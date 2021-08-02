---
id: install_standalone-docker.md
title: 安装单机版 Milvus
label: 使用 Docker Compose 安装
order: 0
group: standalone
---

# 安装 Milvus 单机版

你可以使用 Docker Compose 或 Kubernetes 安装 Milvus 单机版。

你也可以[从源代码编译 Milvus](https://github.com/milvus-io/milvus#to-start-developing-milvus)。


<div class="alert note">
Docker Compose 部署方式只用作测试使用，不能用于生产环境。
</div>

{{tab}}


## 安装 Milvus 单机版


1. 下载 **docker-compose.standalone.yml** 配置文件并保存为 **docker-compose.yml**
```
wget https://raw.githubusercontent.com/milvus-io/milvus/master/deployments/docker/standalone/docker-compose.yml -O docker-compose.yml
```
2. 启动 Milvus 单机版：

```shell
$ docker-compose up -d
```

```text
Docker Compose is now in the Docker CLI, try `docker compose up`
Creating milvus-etcd  ... done
Creating milvus-minio ... done
Creating milvus-standalone ... done
```

*如果 Milvus 单机版启动正常，可以看到有 3 个 Docker 容器在运行（2 个为基础服务，1 个为 Milvus 服务）：*

```
$ sudo docker-compose ps
      Name                     Command                  State                          Ports
----------------------------------------------------------------------------------------------------------------
milvus-etcd         etcd -listen-peer-urls=htt ...   Up (healthy)   2379/tcp, 2380/tcp
milvus-minio        /usr/bin/docker-entrypoint ...   Up (healthy)   9000/tcp
milvus-standalone   /tini -- milvus run standalone   Up             0.0.0.0:19530->19530/tcp,:::19530->19530/tcp
```

<div class="alert note">
运行 <code>$ sudo docker-compose down</code> 停止 Milvus 单机版。
</div>