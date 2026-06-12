---
title: "php reinstall"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2006-12-25
i havent been able to get php to install to my apache2 webserver. i looked around google/forums/etc, but nothing yet has worked. ive run through the basic install process many times, but to no avail.

background: i was trying to get Gallery2 photo album/organizer set up on my apache2 webserver (currently back at college).  it requires apache, php, and mysql. i had apache and php working, so i installed mysql. i ended up not having mysql set up correctly, so i began to mess with the php (i dont have any experience with php, i just needed it working :-/ )

when visiting my root webserver directory, it would display both my apache and php version. however after i messed w/the php, it ceased functioning. i uninstalled apache, php, mysql - everything, and attempted to reinstall, hoping for a fix. no luck.

currently:
im told php5, apache2, and mysql are installed. but my root webpage only mentioned apache being installed.
```
willi@fileserver:/usr/share$ sudo apt-get install apache2 php5 php5-mysql php5-common libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
apache2 is already the newest version.
php5 is already the newest version.
php5-mysql is already the newest version.
php5-common is already the newest version.
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
willi@fileserver:/usr/share$  sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                            [ ok ] 
willi@fileserver:/usr/share$ 

```

what can i do to get php working?

---

