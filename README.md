# xb_backup
xtrabackup simple scripts
支持：
1. 记录备份信息，通过xtrabackup --history获取
2. 支持备份后，发送邮件
a. 备份成功，发送统计状态信息
b. 备份失败，发送xtrabackup输出的日志信息

环境部署：
1. 安装python3.5+
   yum -y install openssl
   ./configure --prefix=/usr/local/python3.6 && make -j4 && make install
   ln -s /usr/local/python3.6/bin/python3.6 /usr/local/bin
2. 安装mysql-connector-python-2.1.6
  wget https://dev.mysql.com/get/Downloads/Connector-Python/mysql-connector-python-2.1.6.zip
  tar -zxf mysql-connector-python-2.1.6.zip
  python3.6 setup.py install

3. 安装xtrabackup最新版

使用方法：
1. 编辑配置文件
vim /etc/xtrabackup.cnf

2. 命令
python3.6 xb_backup.py -f/etc/xtrabackup.cnf

最后邮件收到的内容：
[xtrabackup history]
uuid: 05c03608-6d29-11e7-9cd9-067a70000eaf
name: None
tool_name: xtrabackup
tool_command: --defaults-file=/etc/xtrabackup.cnf --target-dir=/data/xtrabackup/2017-07-20_16:54:15/data
tool_version: 2.4.7
ibbackup_version: 2.4.7
server_version: 5.7.18-15-log
start_time: 2017-07-20 16:54:15
end_time: 2017-07-20 16:54:21
lock_time: 0
binlog_pos: filename 'binlog.000020', position '35637'
innodb_from_lsn: 0
innodb_to_lsn: 2778551
partial: N
incremental: N
format: file
compact: N
compressed: Y
encrypted: Y

[backup space]
free size:   457.03GB
total size:  499.75GB

xtrabackup size:    42.68 MB
