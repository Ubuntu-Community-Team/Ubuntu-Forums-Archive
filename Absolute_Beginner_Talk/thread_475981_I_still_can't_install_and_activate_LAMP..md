---
title: "I still can't install and activate LAMP."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-06-16
I installed LAMP with this method which seems to have installed with no errors.
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
```
I'm following this guide and are about to set a MySQL root password but it doesn't work:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> All of those packages are in the Ubuntu 6.06 LTS (Dapper Drake) main repository. Once LAMP is installed, you need to **set a mysql root password** and then, depending on your web application, create a database, user and password. That's it!

```
mike@sanka:~$ **mysql -u root**
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: N O)
mike@sanka:~$ **sudo mysql -u root**
Password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mike@sanka:~$** mysql -u root -p**
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mike@sanka:~$ **mysql -u root -p**
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mike@sanka:~$
mike@sanka:~$

```

What should I type in as **"Enter password:"** I tried NO but no nothing happens.  Help me plz!

---

### Post by skymera on 2007-06-16
how bout 

```
 sudo -s 
```

then 

```
 mysql -u root 
``` or whatever

---

