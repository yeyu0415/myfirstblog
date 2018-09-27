---
title: 操作linux系统配置
---
Welcome to [Hexo](https://hexo.io/)! This is MY first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

## 1.配置repo,cd /etc/yum.repos.d
### Create a new post

``` bash
baseurl=http://10.35.28.5/repos/rhel-x86_64-server-6.7.z/

2.yum update ,更新所有缺失的包或者命令 



```

More info: [Writing](https://hexo.io/docs/writing.html)

### 3.安装wget命令

``` bash
yum install wget
4.如果遇到下面的问题
./libtool: line 990: g++: command not foun
执行下面的语句：
yum -y install gcc+ gcc-c++

5.如果遇到一下问题
libs/pcrecpp.o:could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libpcrecpp.la] 错误 1
make[1]: Leaving directory `/usr/app/pcre-8.00'
make: *** [all] 错误 2

解决办法：./configure --disable-shared --with-pic   
```

More info: [Server](https://hexo.io/docs/server.html)

### 6.安装httpd

``` bash
 [参考网页](http://www.linuxidc.com/Linux/2012-06/62289.htm)

./configure --prefix=/usr/local/httpd/ --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util/ -with-pcre=/usr/local/pcre/
```

More info: [Generating](https://hexo.io/docs/generating.html)

### 7.设置linux 网络代理

``` bash
http_proxy=http://10.175.250.81:8080
https_proxy=http://10.175.250.81:8080
export http_proxy
export https_proxy
export|grep http

要取消该设置：
unset http_proxy
unset https_proxy
```
More info: [Deployment](https://hexo.io/docs/deployment.html)

### 删除yum包

``` bash
8.删除yum包
rpm -qa|grep yum|xargs rpm -e --nodeps
强制收删除
rpm -qa |grep CDM|xargs rpm -e --noscripts --allmatches --nodeps
```



### 9.查询yum包是否安装
``` bash
rpm -qa|grep yum
```
### 10.安装yum,参考一下地址
``` bash
http://www.mamicode.com/info-detail-1176717.html
```

### 11.Linux修改profile文件改错了，恢复的方法
``` bash
在改profile的时候，改出问题了，除了cd以外的命令基本都不能用了，
连vi都不能用了，上网查了下，用export PATH=/usr/bin:/usr/sbin:/bin:/sbin:/usr/X11R6/bin

12.
 could not map anonymous shared memory: Cannot allocate memory
postgressql.conf，将如下属性调小
shared_buffers=256MB
     
13.psql: FATAL:  database "pg" does not exist
参考如下：http://blog.csdn.net/wangyezi19930928/article/details/20358369
```
###  14.cassandra创建keyspace
``` bash
http://www.cnblogs.com/feiyun126/p/6144294.html
cassandra本地配置
http://www.cnblogs.com/maheng/p/4989582.html

http://blog.csdn.net/nangongyanya/article/details/54286540

http://www.cnblogs.com/gaopeng527/p/4755298.html
报如下错误：
Java HotSpot(TM) 64-Bit Server VM warning: INFO: os::commit_memory(0x00000000cba00000, 878706688, 0) failed; error='Cannot allocate memory' (errno=12)
编辑 /etc/sysctl.conf，修改参数 vm.overcommit_memory = 1，重启服务器或者用户重新登录
```
### 15，卸载rpm  
``` bash
即卸载命令变为：
$rpm -e --noscripts wine-20050310-1fc1winehq

若要查看与RPM关联的scripts，使用--script查询RPM包。
＄rpm -q --scripts package

卸载时，若系统里有同一程序的多个安装版本要一起删除，可使用--allmatches标记，如
＄ rpm -e --noscripts --allmatches wine
```






