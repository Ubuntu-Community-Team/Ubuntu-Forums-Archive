---
title: "LAMP on Ubuntu 7.04 - phpmyadmin works but mysql_connect does not exist"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by cdrw on 2007-06-15
Hi Community,

I have installed 7.04 i386 version and followed the instructions bellow to intall a LAMP

[https://help.ubuntu.com/7.04/server/C/]("https://help.ubuntu.com/7.04/server/C/")

Then I did a "sudo apt-get install phpmyadmin" and everything just works fine. But strangely, the following code says "mysql functions are not available.":

[PHP]

<?php
if (function_exists('mysql_connect')) {
    echo "mysql functions are available.<br />\n";
} else {
    echo "mysql functions are not available.<br />\n";
}
?> 

[/PHP]

I have dug into the PHP script files of phpmyadmin, it boils down to calling mysql_connect as well. I have tried to create some dummy databases by phpmyadmin and i can see the database is created from the mysql cli.

Everything is default and root does not have a password. Any idea about this?

Thanks in advance.

wan yi

---

### Post by cdrw on 2007-06-15
issue resolved.

Adding 
/usr/lib/php5/20060613+lfs/mysqli.so
/usr/lib/php5/20060613+lfs/mysql.so

into
/etc/php5/apache2/php.ini
/etc/php5/cgi/php.ini

---

### Post by fdy on 2007-07-25
Hey,

I have a problem with mysql_connect as well, except that the code you used to try it out works for me, that is to say I get : "mysql functions ARE available."
But if I try to actually use this function, I got an error message :
"Fatal error: Call to undefined function  mysql_connect()"
Here is the code I am trying :
```

<?php
$link = mysql_connect('localhost', 'my_user_name', 'mysql_password');
if (!$link) {
    die('Could not connect: ' . mysql_error());
}
echo 'Connected successfully';
mysql_close($link);
?> 

```

Any idea ?

---

