# SettingBackUp

Original link https://github.com/shadowsocks/shadowsocks-libev/issues/1689

以root权限执行一下命令
echo 3 > /proc/sys/net/ipv4/tcp_fastopen
在/etc/sysctl.conf中添加
net.ipv4.tcp_fastopen = 3
重启，然后查询是否已经打开，运行下面命令，如果 TCPFastOpenPassive 在增长，表示接受到了fast open的tcp连接：
grep '^TcpExt:' /proc/net/netstat | cut -d ' ' -f 91-96 | column -t
