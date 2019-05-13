build executable jar
```bash
mvn -U -Pprod clean package spring-boot:repackage
```

build docker image
```bash
export version=1.0-SNAPSHOT
docker build --rm \
--build-arg version=$version \
-t msj-zuul:prod .
```

run docker container
```
docker run -d --name msj-zuul --restart=always -p 9003:9003 msj-zuul:prod
```

利用docker compose启动容器
```bash
docker-compose -f docker_zuul.yml up -d
```

停止容器
```bash
docker stop msj-zuul
```

移除容器
```bash
docker rm msj-zuul
```

移除旧的镜像
```bash
docker rmi 旧镜像的IMAGE ID
```