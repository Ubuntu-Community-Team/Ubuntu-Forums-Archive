---
title: "MySQL connection fails"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-12-10
Hi,
I amy trying to test the MySQL using a test program (php script) that works fine when the user is set to "root", but when I select a different user that I created, it fails. I set all the privileges for thi suser in the "user" table exactly the same as as root, but it still fails to connect:

mysql_connect(): Access denied for user:

---

### Post by davmac on 2005-12-10
Does the info at [http://www.phplivesupport.com/documentation/viewarticle.php?uid=1&aid=62&pid=3](http://www.phplivesupport.com/documentation/viewarticle.php?uid=1&aid=62&pid=3) help?

Dave Mac

---

### Post by sam hassell on 2005-12-10
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

### Post by NoBullMan on 2005-12-11
Thanks a lot guys. It is resolved.

---

