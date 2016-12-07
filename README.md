# Bug in handling .dockerignore x/**/y with docker-compose

## How to recreate

```sh
$ docker-compose build docker-ignore
Successfully built 6f6383c417f3
$ docker run --rm -it docker-ignore find node_modules -name '*.md' | wc -l
       3
$ docker run --rm -it docker-ignore find node_modules -name '*.md'
./1/2/3/A.md
./1/2/A.md
./A.md
```

Without docker-compose it's ok
```sh
$ docker build -t docker-ignore -f docker-ignore/docker/Dockerfile.test docker-ignore
Successfully built cd3ab73e69bf
$ docker run --rm -it docker-ignore find node_modules -name '*.md' | wc -l
       0
```
