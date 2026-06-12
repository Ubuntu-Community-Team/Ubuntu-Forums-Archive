---
title: "[SOLVED] 500 Internal Server Error - when trying to open a php"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by GreenB on 2008-04-09
Hi, I am not in any way a experienced Linux user, so i kind of need some help,
so far i have installed libapache2-mod-php5 , apache2-mpm-perfork and a bunch of different php5 packets.(not really sure which one i need so i keep changing )

when i go to [http://localhost](http://localhost) in mozilla i get to the /var/www/ and im able to browse down the directories, but when i try to open a .php file i get a "500 internal server error" 

when i (re)start my apache i get a:
```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                           [ OK ]


```

and in the error.log file i find:
```

[Wed Apr 09 18:18:57 2008] [error] [client 127.0.0.1] SoftException in Application.cpp:297: UID of script "/var/www/ax.p$
[Wed Apr 09 18:18:57 2008] [error] [client 127.0.0.1] Premature end of script headers: ax.php, referer: http://localhost/

```

well, i am not quite sure where to go from here, so any help would be much appreciated

---

### Post by Rocket2DMn on 2008-04-09
Did you try setting up LAMP - [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ?
I think this is the best supported method for getting Apache and PHP to work in Ubuntu.  It's possible that right now Apache doesn't know exactly where to look for PHP, or it is missing some stuff.

---

### Post by GreenB on 2008-04-10
Thx a Bunch-  you just made my dayn a bit brighter.
turns out i needed a 
```

ServerName localhost

```
in the httpd.conf file, then a complete removal and re installation of the php5 made it work like a nice and comfy dream
Thx. again

---

