---
title: "Noob trying to run simple PHP/mysql page, tell me my problem"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by realityintrudes on 2005-12-30
Ok, managed to install and get Apache w/php support running, and got through setting up mysql and have that successfully (i believe) running - I can create databases and such with mysqladmin and the mysql monitor.  Im just trying to run a php page on localhost, just to get started playing around.  I'm brand new (like, earlier today) to LAMP, so be gentle - :)

All this is supposed to do is create/access a database, create a table, input one number, and then retrieve and print it.  Tell me what Im stupid with.

<html>
<body>

This page should print 575 below!

<?php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = 'mypassword';

$conn = mysql_connect($dbhost, $dbuser, $dbpass) or die                      ('Error connecting to mysql');

$query  = 'CREATE DATABASE phpcake';
$result = mysql_query($query);

mysql_select_db('phpcake') or die('Cannot select database');

$query = 'CREATE TABLE contact(myNumber INT)' or die('cannot create table');
$result = mysql_query($query);

$query = 'INSERT INTO contact(myNumber) VALUES (575)' or die ('cannot insert value');
$result = mysql_query($query);

$query  = 'SELECT myNumber FROM contact' or die ('cannot retrieve value');
$result = mysql_query($query);

print "$result";
print "<br>done";

?>

</body>
</html>

No error messages print, but there's no output of any number.  The database is created successfully (checked), and it prints 'done' successfully at the bottom.

---

### Post by DeniseDD on 2005-12-30
I am not an expert but it would seem you created a table without specifying it's size which normally in most databases defaults to a size of 1 (one). So if you try to put the number 575 it will not fit-


mysql_query("CREATE TABLE birthdays( id INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(id), _**name VARCHAR(30)**_, **_birthday VARCHAR(7)_**)")or die("Create table Error: ".mysql_error());

I am not sure if this helps but I hope it does-

de

---

