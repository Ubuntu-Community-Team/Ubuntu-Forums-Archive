---
title: "DBDesigner 4 and MySQL - Invalid Username/Password"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by cdecarlo on 2007-08-16
Hello,

I'm having difficulty logging into MySQL using DBDesigner 4.  To install DBDesigner4 I followed the handy instructions from this forum, thank you. Also, I've seen that others have had a similar problem with logging in, I've tried the posted solution but I still haven't been able to log in. In MySQL, I've got 'old passwords' turned on, and all my passwords are less than 16 characters, has anyone else faced this problem as well? Some guidance would be appreciated.

Here is some info that may (or may not) help:

```

colin@thedecarlos:~$ mysql --version
mysql  Ver 14.12 Distrib 5.0.38, for pc-linux-gnu (i486) using readline 5.2

colin@thedecarlos:~$ mysql -u root -p mysql
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 5.0.38-Ubuntu_0ubuntu1-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show variables
    -> ;
+---------------------------------+-----------------------------+
| Variable_name                   | Value                       |
+---------------------------------+-----------------------------+
| auto_increment_increment        | 1                           | 
.
.
.
| old_passwords                   | ON                          | 
.
.
.
+---------------------------------+-----------------------------+
228 rows in set (0.00 sec)

mysql> select user, length(password)
    -> from mysql.user
    -> order by user;
+------------------+------------------+
| user             | length(password) |
+------------------+------------------+
| colin            |               16 | 
| colin            |               16 | 
| debian-sys-maint |               41 | 
| root             |               16 | 
| root             |               16 | 
| root             |               16 | 
+------------------+------------------+
6 rows in set (0.39 sec)


```

I've installed DBDesigner4 Ver. 4.0.5.4 Beta.

Thanks,

Colin

---

### Post by db163404 on 2007-08-24
You need to reset your password. I dont know the exact syntax but its like password = OLD_PASSWORD('passwordhere')

---

### Post by Golyadkin on 2007-08-24
I can't help you with your problem here but have another remark: DBDesigner has been discontinued at last 1.5 years ago and it is replaced with [MySQL Workbench]("http://www.mysql.com/products/tools/workbench/"). 
This is the official message:
> 

Dear DBDesigner4 users,

Due to several attacks against the DBDesigner4 forum it has now been closed down.
We simply cannot understand the sick motivation of people to attack Open Source projects.
So please understand that we will not provide any support from now on.

We will continue to host the DBD4 download till the release of the MySQL Workbench,
its successor application that will be an official MySQL product. Then this project will rest in peace.

Best regards,
fabFORCE.net team


---

### Post by db163404 on 2007-08-24
I don't think the current alpha build counts as a release. I think they'll keep the site up and chugging along until a stable build comes out... or at least a RC.

---

### Post by Golyadkin on 2007-08-25
Well yes, but the product DBDesigner will never be updated or fixed again. It is just that you can still download it, but it is unsupported and discontinued.

---

### Post by db163404 on 2007-08-26
That's correct, but I feel much better using a stable product than an alpha build.

---

