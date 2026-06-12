---
title: "Mysql"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2006-12-15
Hi,
I recently install apache2, php and mysql. Concerning mysql I have the following questions:

ASSUMPTIONS
1) It is fresh install and I didnt create anything yet, nor user or database.
2) From what I read, inside mysql I have to create users and set their privileges.
However I have the following questions:

QUESTIONS
1) User and databases
  i) Shall I create different users for each db? 
  ii) How do I create a user? 
  iii) How can I create a database
  iv) How can I associate a database to a user
  v) Which one should I create first?

2) Privileges
  i) How can I change/set the user privileges
  ii) Which privileges should I give to that user in order to have maximum security
  iii) I think I should create an administrator to CREATE and DROP databases, and other user to query the database. Is this correct?
  iv) Which user should I create to query the database (from apache) in order to have maximum security? www-data? apache2?

3) Console access to database
  i) How do I have access to the database from a console, either to query or to create/drop?
  ii) I want to allow all databases admin privileges to the login 'A', but only allow login 'B' to query a specific database. How can I do it?
  iii) How do I make a database backup using mysqldump?

If possible please give me the console commands. Please notice that I am a total newbie concerning mysql. 

Thank you in advance.

Carlos

---

### Post by Paul41 on 2006-12-15
This should be useful to you.

[http://dev.mysql.com/doc/refman/5.0/en/preface.html](http://dev.mysql.com/doc/refman/5.0/en/preface.html)

---

### Post by tocleora on 2006-12-15
I use a package called Webmin to administer my server in general.  If you too want to install Webmin, You can get it from webmin.com or you might try:

```
sudo apt-get install webmin
```

Once installed you can go to [http://your.server.ip:10000](http://your.server.ip:10000) (or what you set that number to in setup, notice it's a : not a /) login, go to "Servers" and then you'll see "MySQL Database Server".  Select that.

Go ahead and create your database first.  Then click on "User Permissions", "Create New User".  What I do (and hopefully someone will correct me if I'm wrong so you and I both can correct this since we're talking about Security) is create a user with NO privileges here.  So in the Permissions box you won't select anything.  This overall gives the user no privileges which we'll give to them later.  Save the User and return to database list.

Now click on "Database Permissions".  create a new database permission, Set "Databases" to the database you just created, "Username" to the Username you just created, and then I give my user "Select", "Insert", "Update" and "Delete" privileges, that's all.  this will allow them to run those type of queries but nothing else.  Depending on your purpose you may even want to take update and/or Delete away from them.  Save and return to database list.  You can create a new record in database privileges for every database and/or user you want set up, so if "user01" will have access to "database01" and "database02" but "user02" will only have access to "database02" then you'll have three records: user01/database01, user01/database02, user02/database02.  Hope that makes sense. :)

Your "root" user has privileges to do everything.  I believe the root user has no password when MySQL is first installed, so you'll want to give it a password.

If you plan on just using MySQL with PHP you will more than likely use one username per domain (or that's what I do).  If you're running MySQL and PHP on the same server then in the user creation and permission setups you'll set your Hosts to "localhost".  

If you are planning on selling hosting then with each domain the customer has (domain.com) you can set up a mysql database for them (domain_com) and a user account with full privileges for *that domain*.  

Hope that helps a little... ;)

---

### Post by az on 2006-12-15
> **Carlos Santiago said:**
> Hi,
I recently install apache2, php and mysql. Concerning mysql I have the following questions:

ASSUMPTIONS
1) It is fresh install and I didnt create anything yet, nor user or database.
2) From what I read, inside mysql I have to create users and set their privileges.
However I have the following questions:

Mysql users are not the same as system users.  We are not talking about a user who can log into your computer.  It is a user within mysql.

> **Carlos Santiago said:**
> 
QUESTIONS
1) User and databases
  i) Shall I create different users for each db? 
  ii) How do I create a user? 
  iii) How can I create a database
  iv) How can I associate a database to a user
  v) Which one should I create first?

That depends.  Usually, your web application will only need to use one database.  If your web application needs to use more databases, I guess the mysql user used by your web application would have to have pridiledges to them.


> **Carlos Santiago said:**
> 
2) Privileges
  i) How can I change/set the user privileges
  ii) Which privileges should I give to that user in order to have maximum security
  iii) I think I should create an administrator to CREATE and DROP databases, and other user to query the database. Is this correct?
  iv) Which user should I create to query the database (from apache) in order to have maximum security? www-data? apache2?

3) Console access to database
  i) How do I have access to the database from a console, either to query or to create/drop?
  ii) I want to allow all databases admin privileges to the login 'A', but only allow login 'B' to query a specific database. How can I do it?
  iii) How do I make a database backup using mysqldump?

If possible please give me the console commands. Please notice that I am a total newbie concerning mysql. 

Thank you in advance.

Carlos

To have maximum security, do not allow anyone to use the root user (mysql root user, not the system root user - two different things)  Also, create a user with minimal privs - just enough to use the database functions that your web application needs.

See here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Ben Sprinkle on 2006-12-15
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) 
Use this as I do, it requires no config and comes with PHP, Apache, AND MySQL + phpMyAdmin for your database and user needs:

---

### Post by Carlos Santiago on 2006-12-15
Paul41, tx for the manual link.

Tocleora, I was searching for administration commands on console. However if I choose to use a WEB interface to admin my server, I will certainly use webmin. Moreover, your tips concerning users and databases were all well detailed and concise. ;-) They will be very usefull, no matter if I admin my server via console or via WEB. Thank you so much!

Azz, thanx for your tips, I already knew that login users are different from mysql users. Thanx anyway.

Goat Spirit, thanks for your reply but as I already have PHP Apache and MySQL installed, I will give a try to XAMPP on other opportunity. Thanx anyway.



Some question remain concerning web admin:

1) I feel that WEB admin is another door to access administration privileges. 
   How is the authentication process in a WEB admin interface? Who can have access to it?

2) I also feel that if we don't be cautious we might let a door open to anyone with access to the browser. Or even to anyone on the web.

---

### Post by tocleora on 2006-12-16
Giving it a unique port number (besides 10000, the default) will assist with having access to webmin as they will need to know the port number to know where to find it.  You could also get a secured certificate if you'd feel better about it.  You can set up multiple accounts for webmin but I would suggest keeping that to a minimum.  My commercial servers have Plesk on them:

[http://www.swsoft.com/en/products/plesk/](http://www.swsoft.com/en/products/plesk/)

It seems to be a little more multi user friendly (customers have access to all of their needs) and secure but there's a one-time or monthly fee for it.    You might check it out as well.

---

