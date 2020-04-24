# tutapnel
A stand-in of pingtunnel

### Docker
server:
```
docker run --name tutapnel -d --privileged --network host --restart=always tutacc/tutapnel ./tutapnel -type server -key 123456
```
client:
```
docker run --name tutapnel -d --restart=always -p 1080:1080 tutacc/tutapnel ./tutapnel -type client -l :1080 -s www.yourserver.com -sock5 1 -key 123456
```

### 参数
    通过伪造ping，把tcp/udp/sock5流量通过远程服务器转发到目的服务器上。用于突破某些运营商封锁TCP/UDP流量。
    
    -type     服务器或者客户端

    服务器参数:

    -key      设置的密码，默认0

    -nolog    不写日志文件，只打印标准输出，默认0

    -noprint  不打印屏幕输出，默认0

    -loglevel 日志文件等级，默认info

    -maxconn  最大连接数，默认0，不受限制

    -maxprt   server最大处理线程数，默认100

    -maxprb   server最大处理线程buffer数，默认1000

    -conntt   server发起连接到目标地址的超时时间，默认1000ms

    客户端参数:

    -l        本地的地址，发到这个端口的流量将转发到服务器

    -s        服务器的地址，流量将通过隧道转发到这个服务器

    -t        远端服务器转发的目的地址，流量将转发到这个地址

    -timeout  本地记录连接超时的时间，单位是秒，默认60s

    -key      设置的密码，默认0

    -tcp      设置是否转发tcp，默认0

    -tcp_bs   tcp的发送接收缓冲区大小，默认1MB

    -tcp_mw   tcp的最大窗口，默认10000

    -tcp_rst  tcp的超时发送时间，默认400ms

    -tcp_gz   当数据包超过这个大小，tcp将压缩数据，0表示不压缩，默认0

    -tcp_stat 打印tcp的监控，默认0

    -nolog    不写日志文件，只打印标准输出，默认0

    -noprint  不打印屏幕输出，默认0

    -loglevel 日志文件等级，默认info

    -sock5    开启sock5转发，默认0

    -profile  在指定端口开启性能检测，默认0不开启

    -s5filter sock5模式设置转发过滤，默认全转发，设置CN代表CN地区的直连不转发

    -s5ftfile sock5模式转发过滤的数据文件，默认读取当前目录的GeoLite2-Country.mmdb

