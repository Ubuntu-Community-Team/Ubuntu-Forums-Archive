---
title: "MySQL connection problem"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by goldenbough on 2008-04-19
I am having some trouble pulling up the database through my PHP application.  These are the error messages:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: YES) in /var/www/header.php on line 4

Warning: mysql_select_db(): supplied argument is not a valid MySQL-Link resource in /var/www/header.php on line 5


Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/index.php on line 30

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/index.php on line 30

Warning: mysql_num_rows(): supplied argument is not a valid MySQL result resource in /var/www/index.php on line 31


I don't understand what it means by using password "yes" and "no". Well I can access the database through MySQL Administrator.  The server is localhost.  Say the username is "X" and the password is "Y".

I have my config.php file set to this:

<?php

$dbhost = "localhost";
$dbhuser = "X";
$dbpassword = "Y";
$dbdatabase = "forum";

$config_basedir = "http://127.0.0.1";
?>

Yet still it does not work.

---

### Post by apjone on 2008-04-21
> **goldenbough said:**
> I am having some trouble pulling up the database through my PHP application.  These are the error messages:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: YES) in /var/www/header.php on line 4

Warning: mysql_select_db(): supplied argument is not a valid MySQL-Link resource in /var/www/header.php on line 5


Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/index.php on line 30

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/index.php on line 30

Warning: mysql_num_rows(): supplied argument is not a valid MySQL result resource in /var/www/index.php on line 31


I don't understand what it means by using password "yes" and "no". Well I can access the database through MySQL Administrator.  The server is localhost.  Say the username is "X" and the password is "Y".

I have my config.php file set to this:

<?php

$dbhost = "localhost";
$dbhuser = "X";
$dbpassword = "Y";
$dbdatabase = "forum";

$config_basedir = "http://127.0.0.1";
?>

Yet still it does not work.


Do you have a line like the following in your code?
mysql_connect($db_host,$db_user,$db_password) or die(mysql_error());

---

