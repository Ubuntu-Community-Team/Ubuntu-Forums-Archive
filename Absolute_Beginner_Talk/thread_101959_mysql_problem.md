---
title: "mysql problem"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-12-11
im trying to get LAMP configured on my computer but im having a problem with the mysql database. everytime that i try to run mysql on the command line  i get this message:

@ubuntu:~$ mysql
ERROR 1045: Access denied for user: 'becky@localhost' (Using password: NO)

i installed mysql using: sudo apt-get install msyql-server
i was never asked to enter a password. does anyone know what this error message means

---

### Post by amohanty on 2005-12-11
try:

> mysql -u root -p

HTH

---

### Post by sam hassell on 2005-12-11
Try logging into mysql from the prompt using the new account and see if you can access the database you want.

ie: 
```

$ mysql -l *username* -p
enter your password

mysql > use *databasename*;
```

then run a basic select statement on one of your tables, just to check that you can access the data stored within.

--------------------

If this works, you have set up the user account correctly. If not check:

[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html]("http://dev.mysql.com/doc/refman/5.0/en/adding-users.html")

the code you want to use to add an account is:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost' IDENTIFIED BY 'some_pass' WITH GRANT OPTION;
```

*.* refers to database.table. I'm assuming you understand wildcards.

--------------------

Now you need to get php and mysql working together. I'm assuming you're running Ubuntu. 

Assuming you are using php5 (are you?), from the command line run:

```
sudo apt-get install php5-mysql
```

Got that installed? good, now your php should be able to talk to mysql.

--------------------

If the problem is in your script, try:

[http://www.php-mysql-tutorial.com/connect-to-mysql-using-php.php]("http://www.php-mysql-tutorial.com/connect-to-mysql-using-php.php")

-------------------

Any other problems, let me know and supply more information on your setup. Good luck!

-Sam

---

