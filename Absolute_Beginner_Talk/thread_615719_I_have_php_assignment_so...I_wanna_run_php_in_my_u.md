---
title: "I have php assignment so...I wanna run php in my ubuntu"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by kokophone on 2007-11-17
hello everybody,
I want to run php in my ubuntu,,,is it possible
if yes 
give me hints...how can I use it??
best regards
:(

---

### Post by 505 on 2007-11-17
just load Synaptic and install the package 'php5' If you want to see php pages in you web browser, you also need a server. You can use the package 'apache2' for that.

---

### Post by Harpoon on 2007-11-17
Yes, it is possible.

Do a quick search for howtos on installing LAMP - - Linux (you have this already) - Apache (web server) MySQL (if you don't need it, don't install it) - - PHP.

As for using it, sorry to say you are on your own.

Installation is, BTW, a snap

---

### Post by LaRoza on 2007-11-17
The easiest way is to use "sudo tasksel" and select lampp.

---

### Post by kokophone on 2007-11-17
yes..
now i install php5 and
I can find page that when i type [http://localhost](http://localhost)
I can find that Index of and in this page...apache2-default...and my test php testphp.php,,
but i can't run it????If i want to build how can i do it????
And also in my desktop..I create php file...but i can't terminate it.....why???
pls...:(

---

### Post by kokophone on 2007-11-17
where can i write down .php??
and how can i show for it in index of....to run .php
kindly regards
kokophone

---

### Post by defrex on 2007-11-17
You need to put your php files into the right directory. It'll be /var/www. Anything in there will be viewable from the browser. So, for example, if you put testphp.php in /var/www you'll need to go to [http://localhost/testphp.php](http://localhost/testphp.php).

---

### Post by kokophone on 2007-11-17
/var/www file...
in there I can't write in outside and can't copy it...:(
and also when i openn my php...it show openwith box,,
but i dunna know why??:(
my code of testphp.php is
<html>
<head>
<title>php testing</title>
</head>
<body>
<?php
echo="if this workds we<i>really</i>did it!";
?>
</body>

</html>
is it wrong???or 
how can i write and copy to this path /var/www/file
and also...other ideas to run it???
yours faithfully
kokophone

---

### Post by kokophone on 2007-11-17
sudo gedit /var/www/testphp.php


I always write this when i running it???
i don't know it
:(:(

---

### Post by kokophone on 2007-11-17
when i type other code and change name
[B]examp.htm
[/B][/B]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML … >       
<html xmlns="http://www.w3.org/1999/xhtml" … >
<head>
   <meta http-equiv="Content-Type" content= … />
   <title>PHP generating text and XHTML</title>
</head>
<body>
   <h1>PHP generating some text and XHTML tags</h1>
   <?php
	echo "<em>Hello everyone!</em>";
	echo "<i>hay...</i>"
   ?>
</body>
</html> 

out put is 
PHP generating some text and XHTML tags
Hello everyone!"; echo "hay..." ?> 

what is that??
not sure php??

---

### Post by kokophone on 2007-11-17
any idea for it??
what is??php??

---

### Post by kokophone on 2007-11-17
Is it need run apache for first?????
Like in windows????
I unable to run php file...
please help me..
:(

---

### Post by kokophone on 2007-11-17
help me for 
my php.....
it can get only html...
not running php.................php!!!
please help me...

---

