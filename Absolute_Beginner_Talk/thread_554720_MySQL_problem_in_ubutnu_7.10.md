---
title: "MySQL problem in ubutnu 7.10"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by lohchab on 2007-09-19
i am trying to install music server(kplaylist) on my ubuntu 7.10.

It shows some error msg. for connecting to MySQL :

Could not login with the supplied user name and password! MySQL said: Access denied for user 'MySQL'@'localhost' (using password: YES)
with username MySQL
same for mysql and root 


 as i dont knows the username and password for sql.
and also i am not able to change it and not able to reinstall it.

when i type comman :  mysql -u root -p 
it shows
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
 same for mysql and MySQL

out put of : mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

output of :  mysqladmin -u root password 'mynewpassword'
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


Need Help

---

### Post by jamvegan on 2007-09-19
Have you installed mysql-server?  If so, is it running?  To make sure, go to System->Administration->Services and make sure that Database server (mysql), Database server (mysql-ndb) and Database server (mysql-ndb-mgm) are checked.

---

### Post by lohchab on 2007-09-19
yaa all are checked

waitin.......

---

### Post by hyper_ch on 2007-09-19
```

sudo apt-get install mysql-server mysql-client libmysqlclient15-dev

```

---

### Post by lohchab on 2007-09-19
Re : sudo apt-get install mysql-server mysql-client libmysqlclient15-dev


all things are allready installed ......

---

### Post by hyper_ch on 2007-09-19
is mysql running?

---

### Post by lohchab on 2007-09-20
ya all things are working correctly.....

thanks for everything to you all.

Regards

---

