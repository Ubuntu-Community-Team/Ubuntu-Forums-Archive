---
title: "Mysql"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-10-05
Hello,

If I run this:
```
<html>

<head>
<title>Listing 13.1 Opening a Connetion to a Database</title>
<link href="" rel="stylesheet" type="text/css">
</head>

<body>
<div>
<?php
$username="****";
$pass= "****";
$db="p24";
$link = @mysql_connect("localhost", $user, $pass);
if (! $link){
 die("Couldn't connect to MYSQL: ".mysql_error());
}
print "<h2>Successfully connected to server</h2>\n\n";
@mysql_select_db($db) or die ("Couldn't open $db: ".mysql_error());
print "Succesdfully selected database \"$db\"<br>\n";
mysql_close($link);
?>
</div>
</body>

</html>
```

then I get this message:
> Couldn't connect to MYSQL: Access denied for user 'www-data'@'localhost' (using password: YES)

Could you help me please?
Thanks,

---

### Post by indytim on 2006-10-05
Whatever represents the variable $user, has it been inserted into the appropriate table in the mysql database?

IndyTim

---

### Post by linux-beginner on 2006-10-05
I don't know what is "appropriate table" in the mysql database!
I've begun yesterday with mysql and database.
Could you tell me easier.

---

### Post by hyper_ch on 2006-10-05
First of:

You declare a variable "username" in the PHP script but then vor the DB connection you make use of the variable "user".

This means that the variable user is empty (="") and hence you can't connect to mysql.

---

