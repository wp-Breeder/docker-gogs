### docker-gogs
docker部署gogs

### 用法
1.卸载老版本docker，如果`apt-get` 提醒没有这些安装包就卸载成功。
```shell
sudo apt-get remove docker docker-engine docker.io
```
2.Ubuntu14.04, 安装docker 
```shell
#更新源
sudo apt-get update
#安装 aufs 存储驱动
sudo apt-get install \
    linux-image-extra-$(uname -r) \
    linux-image-extra-virtual
#更新源
sudo apt-get update
#安装https、ca证书、curl、
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
#添加docker 官方 GPL密匙
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# 设置稳定的docker官方源
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
#更新源
sudo apt-get update
#安装最新的docker
 sudo apt-get install docker-ce
####查看有哪些docker 版本
apt-cache madison docker-ce
##安装指定版本docker
sudo apt-get install docker-ce=<VERSION>
```
3.安装docker-compose
```shell
curl -L https://github.com/docker/compose/releases/download/{指定版本}/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
4.安装gogs
 a. 克隆项目
```shell
    git clone https://github.com/wp-Breeder/docker-gogs.git
```
 b. 配置
```shell
###注意修改docker-compose.yml的端口
   #设置gogs物理存储的位置;
   ##把docker-compose.yml文件里的 /path/to/gogs修改为真实的路径 
   #设置mysql root用户的密码;
   ##把docker-compose.yml文件里的 your-mysql-root-password修改为自定义的密码
### 修改nginx 配置
   #打开 nginx.conf ,把http://{host}:3000，设置成真实的ip地址和端口
```
 c.运行
```shell
    #在docker-compose.yml文件目录里运行：
    docker-compose up -d
```





