---
title: "mysql-server 5.0.45 problems"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by ZeddZull on 2008-02-11
I have been fighting all day with trying to install mysql-server-5.0 onto my Ubuntu gutsy machine (x86).  When I start mysql using "/etc/init.d/mysql start", the syslog shows the following errors:

```
Feb 11 14:34:19 ubuntu1 mysqld_safe[16184]: started
Feb 11 14:34:19 ubuntu1 mysqld[16187]: 080211 14:34:19  InnoDB: Operating system error number 13 in a file operation.
Feb 11 14:34:19 ubuntu1 mysqld[16187]: InnoDB: The error means mysqld does not have the access rights to
Feb 11 14:34:19 ubuntu1 mysqld[16187]: InnoDB: the directory.
Feb 11 14:34:19 ubuntu1 mysqld[16187]: InnoDB: File name ./ibdata1
Feb 11 14:34:19 ubuntu1 mysqld[16187]: InnoDB: File operation call: 'open'.
Feb 11 14:34:19 ubuntu1 mysqld[16187]: InnoDB: Cannot continue operation.
Feb 11 14:34:19 ubuntu1 mysqld_safe[16193]: ended
Feb 11 14:34:34 ubuntu1 /etc/init.d/mysql[16328]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 11 14:34:34 ubuntu1 /etc/init.d/mysql[16328]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 11 14:34:34 ubuntu1 /etc/init.d/mysql[16328]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 11 14:34:34 ubuntu1 /etc/init.d/mysql[16328]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 11 14:34:34 ubuntu1 /etc/init.d/mysql[16328]:
```

I am desparate to get this running.  Any help is greatly appreciated.

---

### Post by drtre on 2008-02-11
have you started the server? if not try: mysqld
when the server is up, try typing 
>  mysql -u root -p <your password

---

### Post by Rogers on 2008-02-11
Looks like it's running as the wrong user.  Did you configure this yourself?  Try dpkg-reconfigure my-sql_server

---

### Post by drtre on 2008-02-11
i dont remeber how i configured this. but it must be sometime while you're installing. the user is root.
and the password is the one you've considered. if you cant remeber try reinstalling mysql from synaptic.

---

### Post by ZeddZull on 2008-02-11
Ok - I figured out.  I had a stray MYSQL_HOME variable set that I had used to point to a different config file.  This was causing the reinstall to be wrong.

---

### Post by drtre on 2008-02-11
good to know that.:popcorn:

---

