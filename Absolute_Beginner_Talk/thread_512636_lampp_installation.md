---
title: "lampp installation"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by witham on 2007-07-29
I have just installed lampp having used it previously in XP which all went well and to plan. Now I want to access the admin page but I cannot seem to access it. Usually I just type in [http://localhost/xampp](http://localhost/xampp) and it appears, all I get now is an apache link. Could anyone please help get to the admin page.

---

### Post by indytim on 2007-07-29
First of all, take a look at the files contained in /var/www .  That is the web server root directory.  If you do not have a /var/www/xampp there is no index page to display.  If you do have a var/www/index.htm then go ahead and [http://localhost/](http://localhost/) .

To test whether everything is up and running, do a small php page in var/www like:

[PHP]
<?PHP
phpinfo();
?>
[/PHP]

That'll bring up a display of phpinfo with decent status and variable values across your LAMP installatiion.

Good Luck,

IndyTim

---

### Post by Frak on 2007-07-29
Have you run
```
/opt/lampp/lampp start
```
yet?

EDIT
and have you gone to
[http://localhost/xampp/index.php](http://localhost/xampp/index.php)

---

### Post by witham on 2007-07-30
Thank you very much for your reply inside var/www is apache2-default which has inside it are the apache graphics and the index.html page. lampp is also started.

---

### Post by edrider on 2007-11-23
Hi, im having the same problem ?

when i go to [http://localhost](http://localhost) i just see a list of the directory ie. apache2-default and its index page just says "it works!"

tried changing it using sudo gedit and put :
<?php
phpinfo();
?>

and it doesnt work, but any changes i make to the html do work, so i take it even though it says my lampp is working fine its not ?

havnt been using ubuntu for long but id really appreciate any help getting lampp to work as i dont want to go back to evil windows!!!!

---

