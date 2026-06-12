---
title: "Allow remote connections in mysql? VSFTPD Users? Help Please"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by uberamd on 2007-02-23
First:

I have set on my router to have port 44473 forwarded to mysql on local machine IP 10.4.1.100. It works in Windows fine. However when I change the BIND_IP in my my.conf file from localhost to my outside domain (example.com for example) and the ports to 44473 I get this error:
```

steve@ubuntuserv:/usr/bin$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
steve@ubuntuserv:/usr/bin$

```
So I am unable to connect remotely to my server (such as remote applications to manage databases etc). Also, do I need to change my root mysql user to connect from a remote host? If so, how. (and note when mysql is set to localhost it runs just fine but I can not connect with remote apps)

Second:
How do I create ftp users for my vsftpd install? I will do something like:
**sudo useradd test -m -p testpass**
Then I restart vsftpd (which I probably don't even need to do) I get error 530: login incorrect when trying to login. Why is this? What needs to be done to allow a user account to login to ftp.

Thanks!

---

