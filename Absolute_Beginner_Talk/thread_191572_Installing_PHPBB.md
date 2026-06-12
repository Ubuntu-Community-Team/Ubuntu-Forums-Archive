---
title: "Installing PHPBB"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by cconk01 on 2006-06-07
Im trying to instal PHPBB on my Ubuntu LAMP server, and I have installed all the needed things i believe, from mysqladmin to phpmyadmin. I have uploaded all the files from the phpbb download to /var/www/forums. I load up [http://10.0.5.10/forums/](http://10.0.5.10/forums/) and it takes me to the instal point, i change the following to:
> 
Database Type:      MySQL 4.x/5.x

Database Server Hostname / DSN:  mydomain.com	
Your Database Name: 	test (a database i made using phpmyadmin)
Database Username: 	root
Database Password:       root password

Admin Email Address:  	[email]none@none.net[/email]
Domain Name: 	mydomain.com
Server Port: 	80
Script path: 	/forums/
Administrator Username: 	test
Administrator Password: 	test password
Administrator Password [ Confirm ]:     test password


then i click install and i get the error
> 
Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www/forums/db/mysql4.php on line 48

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /var/www/forums/db/mysql4.php on line 330

Warning: mysql_errno(): supplied argument is not a valid MySQL-Link resource in /var/www/forums/db/mysql4.php on line 331
phpBB : Critical Error

Could not connect to the database 


Is this something you guys could help me with?

---

### Post by Horizon on 2006-06-07
That error message basically means that it can't connect to the database. Make sure that all the info is correct and by default doesn't root only have local access? In your settings you say you put "yourdomain.com" for the database hostname. Is the database also running on the same computer as apache? If so, replace that with "localhost" and see if that helps.

If the database isn't local then you'll need to go into phpmyadmin and allow your apache server's domain/hostname access to root.

That's all I can think of right now, sorry if I wasn't any help :/

---

### Post by cconk01 on 2006-06-07
I got, with your help. Thank you!

---

