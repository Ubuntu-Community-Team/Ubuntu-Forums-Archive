---
title: "PHPMyAdmin weirdness"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by theacoustician on 2006-06-01
Ok, I installed Apache2, mysql-server, and phpmyadmin.

I open up Firefox, go to localhost, and click on phpmyadmin/

I'm greeted with a dialog box that states 

> You have chosen to open


which is a: PHTML file
from: [http://localhost](http://localhost)
and the prompt to tell Firefox what to do with it.

So what have I done wrong?

Many thanks in advance.

---

### Post by indytim on 2006-06-01
I'm away from my server now but it looks like your address is incomplete.  You will need to check the location of phpmyadmin within your server.  If memory serves me correct it should be something like
[http://localhost/phpmyadmin/index.php]("http://localhost/phpmyadmin/index.php")

Someone who has an instance running can chime in with any address corrections.

IndyTim

---

### Post by theacoustician on 2006-06-01
Thanks for the reply.

Doing that only prompts up a similar dialog box with Firefox asking what to do with a php file.  Its like it has no clue how to render it.

And I'm not sure if this matters or not, but this isn't a Ubuntu server install.  Standard Dapper install.  I'm trying to set things up for MythTV and not getting extremely far.

---

### Post by indytim on 2006-06-01
I took mydevelopment box down for a re-format in preparation to migrate to Kubuntu Dapper, so I'm doing this from memory.

1.  Using a text editor, navigate to /etc/var/www
2.  Create a new file with the following
[PHP]<?PHP
echo phpinfo();
?>[/PHP]

3.  Save the file as test.php
4.  From your browser enter the url

[http://localhost/test.php]("http://localhost/test.php")

If Apache, PHP and MySQL are configured and running, you will see it in the output of your link.

Note : I'm not 100% on the path to your root, you might have to poke around with Nautilus.

IndyTim

---

### Post by Daremo on 2006-06-01
Have you installed PHP also? You didn't mention it in your post...

---

### Post by addikt10 on 2006-06-01
Since I am seeing the same problem, I assume that the OP is referencing [http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html](http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html)

The relevant installation commands are:

apt-get install build-essential dialog apache2 mysql-server phpmyadmin gcc-3.4 
apt-get install libapache2-mod-auth-mysql

I checked what was installed with:
```
dpkg --get-selections php*
php5-cgi                                        install
php5-common                                     install
php5-mysql                                      install
php5-mysqli                                     install
phpmyadmin                                      install


/etc/apache2# grep -R php *
apache2.conf:DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
#apache2.conf:AddType application/x-httpd-php .php
#apache2.conf:AddType application/x-httpd-php-source .phps


```
Uncommenting the second 2 lines and restarting apache had no effect.

---

### Post by addikt10 on 2006-06-02
OK.  I'm almost positive this isn't the "correct" answer, but it will get you by.

I checked on breezy, and the main difference seems to be resolved by 

apt-get install libapache2-mod-php5

-- edit --
Even though this works, change password doesn't show up (for me) on the phpmyadmin page.
Instead, do this:

shell> mysql -u root mysql
mysql> SET PASSWORD FOR root@localhost=PASSWORD('new_password');

found at [http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/doc/en/Default_privileges.html](http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/doc/en/Default_privileges.html)

Good Luck.

---

### Post by justfred on 2006-06-03
Hey , I ran ito similar problems.

[history] I seem to broken my apache2 php5 config when trying to look if I could have only the php4 modules and not php5 as php5 seems to break acid-mysql. However it seems it is not possible using the synaptic packet manager to this properly.  So I tried to revert all the changes I did and found that now I could not serve php files anylonger with apache2 : a dialogbox appears asking to save a PHTML file.

[now] so after numerous trials to completely remove apache2 and php related files and reinstall using 

sudo apt-get install apache2 php5

and I did have to uncomment the php related lines in apache2.conf as well as to make the links to php5.conf and php.load in /etc/apache2/mods-enabled/.

The situation is now like :
[http://localhost](http://localhost)    will still ask to download a PHTML type of file

but

 [http://192.168.0.1](http://192.168.0.1)  will correctly display the result of phpinfo() in the index.php

The strange thing is that I am quite sure the [http://localhost](http://localhost) did work correctly before.

Any ideas ?

PS I am rather new to Ubuntu and linux

---

### Post by uglysmurf on 2006-06-04
justfred - 

Try clearing your client browser's cache...I was having similar problems and that cleared it right up...hope it helps

---

### Post by laurens on 2006-06-04
I had the same trouble as the topic starter, the 

sudo apt-get install libapache2-mod-php5 

trick ehm, did the trick :)

THanks!

---

### Post by NT4usB on 2006-06-05
fwiw... clearing cache didn't get it for me after installing php5. Restarting X did though.

---

