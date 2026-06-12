---
title: "Cannot get Apache2 to do a basic location change"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by gingerj on 2007-08-17
Hi all,

I'm just trying to run apache2 locally so i can do some light programming at home it's installed correctly. BUt I want to change it's url path so that it points to /home/james/WebDev/. So I've used the following cmd:

gksudo gedit /etc/apache2/conf.d/alias

then pasted this into the empty file and saved it:

Alias /home/james/WebDev/

<Directory /home/james/WebDev/>
  Options Indexes FollowSymLinks
  AllowOverride All
  Order allow,deny
  Allow from all
</Directory>

then i tried to restart apache2 but i'm getting this error message:

gingerj@gingerj-laptop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    Syntax error on line 1 of /etc/apache2/conf.d/alias:
Alias takes two arguments, a fakename and a realname


what have I done wrong and can this be fixed?

cheers!

---

### Post by nemequ on 2007-08-17
Don't use mod_alias for this--use the DocumentRoot directive.

In /etc/apache2/sites-available/default, change 'DocumentRoot /var/www/' to 'DocumentRoot /home/james/WebDev/'.

---

### Post by gingerj on 2007-08-20
Thanks! It worked first time cheers for the help!

---

