---
title: "debian-sys-maint@localhost errors"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by jrichey on 2006-10-05
Ok, I installed Ubuntu using the LAMP option about 2 months ago and everything has been running fine.

Yesterday I notice my third party db development tool can't connect to Mysql.

So, I ssh into the server and try to restart mysql.

root@avalivetest:/etc/mysql# /etc/init.d/mysql restart
Stopping MySQL database server: mysqld...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Killing MySQL database server by signal: mysqld.

I can start and stop the server, but I always get these weird errors.

I noticed that the debian user was missing out of the mysql->user table so I added him back in using the password from debian.cnf file. Still gives me the errors.

I have uninstalled/reinstalled mysql several times and I still get the errors. 

Anybody got any ideas?

Thanks

---

### Post by martyn.mayfield on 2006-10-28
I have the same problem - any clear answers out there?

Running Ubuntu Edgy AMD64
Mysql 4.1 PHP5 Apache2.2

---

### Post by eldaria on 2006-11-01
I have the same problem.

I had to recover my server after an upgrade to edgy had gone wrong.
And after importing the mysql.sql dump, and restarting the sql server, i also get the error.

```

/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```

---

### Post by meltintosound on 2008-04-09
Try restarting the mysql daemon:

sudo /etc/init.d/mysql restart

If that fails, try restarting the mysql daemon with a bit more force:

sudo pkill -9 mysql
sudo /etc/init.d/mysql start

If that also fails, try reconfiguring mysql (if at all possible, back up all databases first)

sudo dpkg-reconfigure mysql-server-5.0
sudo /etc/init.d/mysql start

---

