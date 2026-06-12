---
title: "Help setting up Apache2"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by dan1928 on 2007-04-15
I've got an Ubuntu box running as a network server. On it is all my media files (movies, music, etc.). I recently read an article ([see here]("http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php#b3")) that details how to setup Apache2 such that you can login to your computer and access files with a user and password for protection from anywhere on the internet. I followed the guide linked to above on my windows computer and got it working just as advertised, but apparently I can't put the equivalent of a symlink to my ubuntu media server as windows doesn't support symlinks. My next option was to set up Apache2 on my ubuntu box. I installed it and got it running just fine. I even put a symlink in my /var/www/ folder to my media folder. The probem is, I can't get the password authentication thing to work. Each time I log in to my IP it lists the file in /var/www/ without asking for a user and password (which is no good as I can't have all that open to the world). I tried to follow the site linked above as much as possible, but it's written for windows, and obviously I'm doing something wrong in ubuntu.

Anyone have any recommendations for me? 

I used htpasswd to create a password file in /usr/local/password. 
I've got a .htaccess file in my /var/www/ folder that reads as:

AuthType Basic
AuthName "This is a private area, please log in"

AuthUserFile /usr/local/passwords

require valid-user

And my httpd.conf located in /etc/apache2/ reads as:

<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Order allow,deny
	Allow from all
</Directory>

Also, I'm definitely still a beginner with ubuntu (linux in general).

Thanks
-Dan

---

### Post by Bachstelze on 2007-04-15
You definitely shouldn't have /var/www as a symlink. If you want the root of your server to be somewhere else, change it in the Apache config.

---

### Post by bloodniece on 2007-04-15
I always use this guide when setting up new Apache2 servers.  Ignore the Ruby and RoR stuff if you don't plan on using it.  Agreed on the symlink.  Just make a www directory in your home folder, that way all you have to do is backup your home folder.  I recommend Webmin too.

[http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to/]("http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to/")

---

### Post by dan1928 on 2007-04-15
Ok, thanks for the replies. I'll think about reworking the symlink thing. Can anyone help with my main problem of having my webserver protected with a user and password when access from the web? It works just fine in windows, but I can't make it work in Ubuntu.
Thanks

---

### Post by bloodniece on 2007-04-18
Are you setting a password for a directory or file using .htaccess?

All the .htaccess tricks you'd ever want
[http://perishablepress.com/press/2006/01/10/stupid-htaccess-tricks/](http://perishablepress.com/press/2006/01/10/stupid-htaccess-tricks/)

---

