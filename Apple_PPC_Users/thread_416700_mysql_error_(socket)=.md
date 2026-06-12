---
title: "mysql error (socket)="
date: 2007-04-21
forum: Apple PPC Users
---

### Post by AllFather on 2007-04-21
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]#
---
 
Any ideas?
It worked fine before, then suddenly: poof.

---

### Post by heimo on 2007-04-21
Make sure that mysql server is running and that the socket file exists.

```
sudo /etc/init.d/mysql start
ls -l /var/run/mysqld/mysqld.sock
```

---

### Post by AllFather on 2007-04-21
I cant get it started, thats the problem.
Its running of a mac cube g4, and everything worked fine, then suddenly :o
 
1
> 
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# /etc/init.d/mysql start
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
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]#

 
 
2
> 
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# ls -l /var/run/mysqld/mysqld.sock
ls: /var/run/mysqld/mysqld.sock: No such file or directory


---

