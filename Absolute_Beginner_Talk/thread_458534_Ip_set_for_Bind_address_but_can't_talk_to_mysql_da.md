---
title: "Ip set for Bind address but can't talk to mysql database"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by boardtc on 2007-05-29
I've installed lamp and restored some databases. As described in
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
I've set the bind address for the server

I've done this:
At the mysql console type:

> mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
substituating mt root password.

But I am still not able to access the databases from my amp on another machine, it's test page says no database installed. I can see them in phpmyadmin thought.

After reading the forums I tried adding this file testdb to the server:
> <?php

mysql_connect("server_ip","root","root_password") or die(mysql_error());

mysql_select_db("dbname") or die(mysql_error());

?>
but this gives a lost connection to mysql system error 111. How can I get this working?

Thanks, Tom.

---

### Post by sandwitch on 2007-06-01
Isn't Mysql default configured with only local access ?

---

