---
title: "mysql connection problem..."
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-12-23
im having a problem connecting to my mySQL database with php, here is my code:

//connect to server and select database
$conn = mysql_connect("server_name","user","password") or die(mysql_error());
mysql_select_db("db_name",$conn) or die(mysql_error());

when i run the script i get an error saying that the connection was lost. does anyone know if permissions also need to be set to connect to the mySQL server.

---

### Post by paddyg on 2005-12-23
I just set the DATADIR chmod 700, and make sure it's chown MySQL server---nothing else.

Please can you post the error msg?

---

### Post by grim918 on 2005-12-23
this is the error that i get when i run the script:

Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www//forums/do_addtopic.php on line 9
Lost connection to MySQL server during query

and how do i do chown MySQL-server.
im new to linux and im still learning how to run the basic commands.
thank you for helping me out.

---

### Post by paddyg on 2005-12-24
What i meant was that the datadir should be owned by MySQL server, and only MySQL server should access it (chmod 700).

Anyway, have you tried doing one of the following?---just to try and understand who to put your issue down to:

1. Connect to the server via mysql client:
from terminal
```
mysql
mysql>status
```
or even
```
mysql>use mysql
mysql>show tables;
```

2. Try another very simple connect php script---something like
```

<?php
$conn = mysql_connect("localhost", "user", "password");
mysql_select_db("anotherdb", $conn);
if ($conn) {
  echo "Connected to Server";
}
else {
  echo mysql_error();
}
?>

```

Also, i think you should take a look at some more specific info like
[http://dev.mysql.com/doc/refman/5.0/en/gone-away.html](http://dev.mysql.com/doc/refman/5.0/en/gone-away.html)

---

### Post by ninotob on 2005-12-24
[QUOTE=grim918]
//connect to server and select database
$conn = mysql_connect("server_name","user","password") or die(mysql_error());
mysql_select_db("db_name",$conn) or die(mysql_error());
[/QUOTE]

My connection looks exactly like yours except for one difference.  You have:

```

mysql_select_db("db_name",$conn) or die(mysql_error());

```

Mine looks like this:

```

mysql_select_db("db_name") or die(mysql_error());

```

Give that a shot. 

Here's the php manual.  It shouldn't make a difference that you have $conn there, but maybe?  Anyway:
[http://us3.php.net/mysql_select_db](http://us3.php.net/mysql_select_db)

EDIT:  the more I think about it, my suggestion won't change anything.  The line in your script should work fine so maybe just ignore this post.

---

### Post by grim918 on 2005-12-24
i used chmod 700 on a directory that i created just to do some testing and now i cant get into it to view its contents. how do you remove permissions. im lost.

---

### Post by grim918 on 2005-12-24
never mind i figured it out. 
i just used sudo chmod 755

im still having problems with figuring out which directory is the one that i need to set to chmod 700.

---

### Post by grim918 on 2005-12-24
ok here is my new problem. i got the permissons set but now i have another problem when the script runs. it tells me that i dont have permission. here is the error:
//-----------------------
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/garbage/mysql/mysql_connect.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
//-----------------------

and here is the script that i am using to try and connect to the database

mysql_connect.php:
<?php
$conn = mysql_connect("localhost","user","password");
mysql_select_db("db_name",$conn);

if($conn){
  echo "connected to mysql";
} else {
  echo mysql_error();
}
?>
//----------------

i added the chmod 700 permission to this file. im really stuck on this installation and i would like to thank everyone that has been helping me out. im new to linux. thank you

---

### Post by ninotob on 2005-12-24
You know, I'm completely mystified why this doesn't work for you -- synaptic always sets things up without any effort.  Are you positive you have the mysql server installed?

Open up your terminal and type this:
```

mysql -u <username> -p

```

Replace <username> with the username you are using.  If a password is NOT set, omit "-p", if it is set, leave it in and you will be prompted for the password.

You should get a "mysql>" prompt.  If you get any kind of error(*), then you don't have the server installed or if it is installed, it isn't running.  If you do get in, type "exit" to quit.

EDIT (*) assuming of course your username has permission to acces mysql's database on itself.

---

### Post by grim918 on 2005-12-24
i know exactly what you mean. i have no idea what is going on. its not a hard installation but i just keep getting that problem. i do have mysql-server installed. i can go into it and create databases and everything else. i already have a database set up and i want to connect to it but i cant get it to connect.
the only thing that i can think of is that i might have the permissions screwed up somewhere. i only added the chmod 700 permission to the mysql_connect.php script. im gonna go do some more reading to see what might be causing the problem. if you get any ideas please let me  know. thank you

---

### Post by ninotob on 2005-12-24
well, just for kicks, chmod 777 <php_script>

Realizing of course that is read/write/executable by everyone and totally insecure.  If that doesn't work, there is something else going on because a file just can't get more permissive than that.  If it does work, then start backing off the permissions and see where it fails.  For example, once you've 777'ed it,

chmod o-w <php_script>

that will subtract write permissions for others.  Then "g-w" will subtract write for groups.

---

### Post by ninotob on 2005-12-25
What I said above but with this caveat -- the error message you got originally says that there is a problem with the DB connection, which you'd only get if the file was being read.   

Maybe it's the install -- make sure you have "libapache[2]-mod-php[4 or 5]" (which one depends on your apache and php versions -- just do a synaptic search for "php" and scroll alot).  Also, you need to have "mysql-php[3/4 or 5]" installed (version depending on your PHP version of course -- just search on mysql and scroll alot again.

If you don't have a lot of time invested in your install of apache/mysql/php, it might be worth it to do a complete removal and reinstall through synaptic.  You shouldn't have these issues at all -- it feels like something got borked somewhere along the way and if it's a new install on a test system, the speediest solution would be to start over.

---

### Post by grim918 on 2005-12-25
never mind i finally got it working. i had to take off the chmod 700 on the file. and it just worked. thanks for the help.

---

