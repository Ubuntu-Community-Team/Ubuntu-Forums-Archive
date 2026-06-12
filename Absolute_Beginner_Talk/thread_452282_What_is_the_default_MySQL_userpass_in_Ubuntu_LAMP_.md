---
title: "What is the default MySQL user/pass in Ubuntu LAMP Server?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by pansz on 2007-05-23
Hello,

I installed Ubuntu Server 7.04 with the LAMP option.

It is said that LAMP will setup Apache, MySQL and PHP for me.

But what has is do? how to access MySQL? any user/password?

Now I had installed torrentflux which requires the user/password for MySQL database, what is it?

Thanks in advance.

---

### Post by Viskovitz on 2007-05-23
I think the default user after mysql installation is "root" and the password is set to blank. At least it's like this in a normal Ubuntu install. Try this:

[http://www.howtogeek.com/howto/programming/mysql/set-the-mysql-root-password/](http://www.howtogeek.com/howto/programming/mysql/set-the-mysql-root-password/)

---

### Post by az on 2007-05-23
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Set mysql root password
Before accessing the database by console you need to type: 

mysql -u root
At the mysql console type: 

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
A successful mysql command will show: 

Query OK, 0 rows affected (0.00 sec) 

Mysql commands can span several lines. Do not forget to end your mysql command with a semicolon. 

Note: If you have already set a password for the mysql root, you will need to use: 

mysql -u root -p
(Did you forget the mysql-root password? See MysqlPasswordReset.)

---

