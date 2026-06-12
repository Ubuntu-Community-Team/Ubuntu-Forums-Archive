---
title: "Can't Figure Out LAMP"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by walesmd on 2006-10-02
Hey everyone - I don't know why, but I am having major issues with getting a LAMP stack setup.

At first, I tried XAMPP - following this tutorial: [http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

I soon gave up on this because XAMPP kept forwarding requests for [http://localhost/](http://localhost/) to [http://localhost/xampp/](http://localhost/xampp/) and I couldn't figure out why.

I decided to follow the Ubuntu package method, following this tutorial: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Here's where I sit currently:
[LIST]
[*]XAMPP is still responding to [http://localhost/](http://localhost/) even though it has been completed deleted off of the system. Requests for [http://localhost/](http://localhost/) go to [http://localhost/xampp/](http://localhost/xampp/)
[*]Apache2, setup via the Ubuntu package system, responds on [http://127.0.0.1/](http://127.0.0.1/) but doesn't seem to offer PHP support (it's asking me if I want to download a .phtml file when attempting to access phpMyAdmin
[*]I've created a symlink between /home/mike/public_html and /var/www but I can't seem to figure out how to access the files. Visiting [http://127.0.0.1/omg.html](http://127.0.0.1/omg.html) gives me a 404 and [http://127.0.0.1/public_html/omg.html](http://127.0.0.1/public_html/omg.html) gives me a 403.
[/LIST]

My biggest concern right now is accessing my www documents - if I can get this figured out I'm sure I can get Apache, PHP, and MySQL talking back and forth easily enough (I've done it on Windows machines before).

I would honestly prefer to work in /var/www under my current username - can someone tell me how to give this user full permissions to that folder?

Finally - why would xampp still be responding on [http://localhost/](http://localhost/) if it's gone?

---

### Post by llamakc on 2006-10-02
bump to somebody less drunk than I am.

---

### Post by walesmd on 2006-10-02
So I managed to give myself permissions to the /var/www folder - in a very sloppy way I imagine though. I just ran nautilus via gksudo and gave full permissions to others. I'm sure there is a way to do this for "mike" only.

Apache still doesn't process PHP scripts, but I believe I saw the culprit earlier. Now that I can create scripts the server can see I'll go about trying to correct this.

If anyone can help me with the xampp issue (still resolving localhost requests), please do.

---

### Post by llamakc on 2006-10-02
Have you restarted apache2?

apache2ctl restart

Also, in your /etc/apache2/ configuration files there will be a DocRoot declaration.

I'm unfamiliar with xampp but you'd want to restart apache2 after enabling php support.

Is there an index.html in /var/www and if so, is that where the forwarding occurs? 

Or, is /var/www/ empty?

---

### Post by Eigenwert on 2006-10-03
Were you able to fix the apache and php problem? I'm getting the same thing.  After changing the memory limit in the php.ini file apache doesn't want to run the php scripts anymore, it just prompts me to download them.

I'm running XAMPP by the way, and by going to localhost I also get redirected to localhost/xampp. Doesn't really bother me, though.

EW

---

### Post by JerryHobby on 2006-10-03
I've had this type of problem twice now -- once with Debian box and once with Ubuntu.  I noticed that there were permissions problems with /var/run/mysql and /var/log/mysql and other files.

To fix it, I removed all apache, mysql, and PHP packages.  Then added them back. My databases were STILL THERE and all was good. I check and the permissions were correct after the second install.

The only difference between first installation (that failed) and second installation might be the order of installs.  I did the packages one at a time the first time.  The second time I did:

To Remove:
apt-get remove mysql-common mysql-server mysql-client php5 apache2 php5-mysql php5-cli apache

To Install:
adduser mysql
apt-get install mysql-server mysql-client 
apt-get install apache2 php5-mysql libapache2-mod-php5 php5-cli


The APT system is new to me so I don't know all the quirks, dependency issues, but this is what I did and it worked.

Here are the permissions of my key files:

drwxr-s--- 2 mysql adm  /var/log/mysql
drwxr-xr-x 2 mysql root /var/run/mysqld



I'm not claiming that I'm the guru at this or whatever.  But since it worked for me it might work for you.  My theory is that a package conflict caused the permissions problem and reloading the packages might be the fastest way to correct the problem.](*,) 

Jerry

---

### Post by walesmd on 2006-10-03
Yeah - I am completely new to Ubuntu and Linux in general myself. So last night, I decided to just reformat and start it all over again.

I'm really anal about my system being clean and knowing everything that is going on and since I first got Ubuntu running I've done a lot of "playing around."

I haven't given the LAMP stack a try again but I will be doing so this afternoon for sure. I'll let you know how it goes. One thing is for certain - I'll be sure to stay far away from XAMPP this time.

---

