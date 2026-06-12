---
title: "installing XAMPP"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by entropy7 on 2006-05-17
Hi.  I am trying to install XAMPP.  The problem is that i already had apache, MySQL, and PHP running on the system.  I went into Synaptic and tried to uninstall them, but  the original version of Apache still seems to persist. When I type:

sudo /opt/lampp/lampp start

the result is:

Starting XAMPP for Linux 1.5.2...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

so when i type [http://localhost/](http://localhost/) into the browser, i get sent to the old directory located at /var/www/apache2-default/

So whatshould i do with the original Apache?  Have i succeeded in totally messing up my system?       Thanx.

---

### Post by add1sun on 2006-06-10
Hm, well I don't really know the answer but did you try stopping apache before uninstalling?

```
sudo /etc/init.d/apache2 stop
```

If you still can't get it uninstalled try making sure your old apache is stopped and then try XAMPP and see if it works.  If it does, then get the old apache out of your startup script.  You can look at something like rcconf (Runlevel configuration tool).

HTH
Addi

---

