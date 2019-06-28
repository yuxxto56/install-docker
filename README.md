![docker_logo](https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3534957911,2629491814&fm=27&gp=0.jpg)
## windows上安装docker及应用

### 安装
* 下载：[http://mirrors.aliyun.com/docker-toolbox/windows/docker-toolbox/DockerToolbox-18.03.0-ce.exe](http://mirrors.aliyun.com/docker-toolbox/windows/docker-toolbox/DockerToolbox-18.03.0-ce.exe)
*  一路确认安装成功后，会有Docker Quickstart Terminal,Kitematic (Alpha),Oracle VM VirtualBox三个工具出现则安装成功
* 打开 Docker Quickstart Terminal 工具,一开始打开会有点慢,请耐心等待,出现以下界面说明docker环境已经启动
```
                  ##         .
                  ## ## ##        ==
               ## ## ## ## ##    ===
           /"""""""""""""""""\___/ ===
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
           \______ o           __/
             \    \         __/
              \____\_______/

docker is configured to use the default machine with IP 172.16.0.100
For help getting started, check out the docs at https://docs.docker.com
```
* 前提：这里的容器应用以php swoft微服务框架为条件

### docker 镜像
```
 1、下载镜像
 docker pull swoft/swoft
 2、查看镜像
 docker images
 3、删除镜像
 docker rmi swoft/swoft:latest  #删除镜像名称是：REPOSITORY:TAG 
```
### docker容器
* 创建并启动swoft容器
```swoft doctor
  docker run -p 18307:18306 --name swofts -v /d/wamp/www/swoft/:/var/www/swoft swoft/swoft
  # -p 18307:18306 指定虚拟机与容器的端口映射,前者代表虚拟机(virtualbox)端口,后者是容器服务端口。
  # -name swofts   指定容器名称
  #  -v /d/wamp/www/swoft/:/var/www/swoft 虚拟机目录与容器目录的映射。
  # swoft/swoft swoft项目在docker上的镜像（映像）
```
* 关闭swoft容器
``` swoft close
  docker stop swofts
```
* 启动swoft容器
``` swoft start
   docker start swofts
```
* 查看容器
```
  1、docker ps -a  #查看docker环境下的全部容器
  2、docker ps     #查看docker环境下正在运行的容器
```
* 删除容器
```
  docker rm swofts #删除前提请先关闭该容器，docker stop swofts
```


### 说明
* docker start swofts //在后台启动运行容器
* docker run swofts //如果本地没有改镜像,则远程docker_hub上下载，在前台启动运行容器
* docker与windows的结构关系
``` relation
  windows->virtualbox->docker环境->docker容器
```
* 文档参考：[https://docs.docker.com/](https://docs.docker.com/)
