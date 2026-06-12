---
title: "How to  install PHP5"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2008-04-02
Having installed PHP5 from Synaptic could someone tell me how i might get it up and running so that i can start learning please

---

### Post by cozmicharlie on 2008-04-02
Not sure if you are just using php or have a Lamp set up but the instructions below should help get you started - it is from here [http://ubuntuforums.org/showthread.php?t=268985](http://ubuntuforums.org/showthread.php?t=268985).

Also, if you mean how to use php then this will help [http://twomadgeeks.com/tech/2007/08/29/php-for-the-absolute-beginner/](http://twomadgeeks.com/tech/2007/08/29/php-for-the-absolute-beginner/)

Enjoy!


[COLOR="RoyalBlue"]Step 1: Get a functional LAMP stack.

To get a 'LAMP' stack running (Linux Apache Mysql Php), you just install the packages "apache2", "php5" and "mysql-server". You can do this using Synaptic (Ubuntu) or Adept (Kubuntu), or on the command line:
Code:

$ sudo aptitude install apache2
$ sudo aptitude install php5
$ sudo aptitude install mysql-server
$ sudo aptitude install php5-mysql

Once these are installed, you should be able to test it by pointing your web-browser to:
[http://localhost/](http://localhost/)

You should see a web-page, not an error message. (You may see a simple web-dir listing with "apache2-default" in it... that's normal.) To test if PHP is working properly, just create a simple test page. For instance, create a file:
Code:

$ sudo nano /var/www/test.php

And put in this text:
Code:

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php 
	echo 'If you can see this text, then PHP is working.';
?>
</body>
</html>

Then go to [http://localhost/test.php](http://localhost/test.php)
If you see the "...then PHP is working" message then all is well.

Since your PHP/MySQL interface will eventually be world-accessible, it makes sense to put some security in place. By default MySQL starts with no password, so you should certainly set one:[/COLOR]

---

### Post by twp_twm on 2008-04-03
Thanks for all the help cozmicharlie

---

### Post by Xiong Chiamiov on 2008-04-03
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is also a very good guide to installing a LAMP stack.  XAMPP is very easy aswell, though I had some problems with MySQL when I used it.  Thankfully installing all this is nowhere near as difficult as on Windows.

---

### Post by twp_twm on 2008-04-03
Solved

---

