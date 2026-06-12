---
title: "Smokeping help"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by MatsB on 2007-08-03
Hi,

I need some basic help with SmokePing. I've installed Apache2, rrdtool, SpeedyCGI, smokeping on a newly installed Ubuntu 7.0.4 laptop.

I've been trying to follow the documentation on installing Smokeping but i'm stuck at a permission problem when i moved the smokeping.cgi file from /usr/lib/cgi-bin/ to /var/www/smokeping i get **403 forbidden You don't have permission to access /cgi-bin/ on this server.** when i browse to [http://localhost/cgi-bin/](http://localhost/cgi-bin/)
Changing the ownership to www-data doesn't help.

I've also tried to change this in server@admin-laptop:/etc/apache2/sites-available/default

 ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


server@admin-laptop:/var/www$
drwxr-xr-x 2 root     root     4096 2007-08-03 12:14 apache2-default
drwxr-xr-x 2 root     root     4096 2007-08-03 12:54 cgi-bin
drwxr-xr-x 2 www-data www-data 4096 2007-03-19 22:57 smokeping

server@admin-laptop:/var/www/cgi-bin$ 
-rwxr-xr-x 1 root root 2362 2007-08-03 12:28 smokeping.cgi

---

### Post by apswartz on 2007-08-03
You might some help in the servers forum...
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

