---
title: "Connecting to mySql"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by tgfkarick on 2007-03-31
Hi,

Installed ubuntu LAMP server, as I'm planning to move a current php/mysql based application from shared hosting onto my own linux server.

I've managed to get the web site up and running, but my problem is witht he sections which connect to the mySql database.  I've created the database by restoring a backup from my shared hosting enviroment, but when I try and use the code which access it I get:

Access denied for user 'www-data'@'localhost' 

To me this is saying I need to give user www-data access to my database, so I installed webmin to make life a little easier and then tried assigning a database permission for the user www-data to read/write/delete.  But still the same error.

I'm also getting a similar error when I try and connect to mysql from the command prompt but typing:

sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

So I guess the first question is, have I set up mySql wrong in anyway, and can I get apache to access the database somehow?

Secondly, is this the best way?  Should I use www-data to access the database or should I really create a new user for database connectity?

Many thanks for your help.

Rick

---

### Post by useResa on 2007-03-31
There is a good instruction on how to set up a LAMP server, including setting up access to mySQL, to be found [here]("http://www.mysql-apache-php.com/").

Hope this will help solve your problem.

---

### Post by aGor on 2007-03-31
Try this:
sudo mysql -u root -p
Push enter
Then type your password

This should work.

---

### Post by benetook on 2007-04-04
I have exactly the same problem, I then used
sudo mysqladmin -u root password [I]password here[I]
pressed ENTER
this corrected the password, then I entered the command above and can now access mysql.

but I still cannot get the blog site operating, I get the message;

Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/blog/index.php on line 81

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/blog/index.php on line 81
 Could not CREATE table
 Access denied for user 'www-data'@'localhost' (using password: NO)  

Warning: Missing argument 2 for AE4(), called in /var/www/blog/index.php on line 83 and defined in /var/www/blog/index.php on line 2
 AC2 creating table bloly_User
 Access denied for user 'www-data'@'localhost' (using password: NO)  
 Could not install  

[/I][/I]

---

### Post by benetook on 2007-04-04
In follow up, I followed [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/) as suggested, all works till 
mysql> USE mysql;
same refusal as previous problem.
mysql> UPDATE user SET Password=[I]mypassword[I] WHERE user=[I]rootname[I]
this line above worked!!!
then this line failed with the same refusal of access
mysql> FLUSH PRIVILEGES.

Any help appreciated[/I][/I][/I][/I]

---

