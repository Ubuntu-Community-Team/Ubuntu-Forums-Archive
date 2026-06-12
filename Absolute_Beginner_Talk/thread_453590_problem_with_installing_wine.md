---
title: "problem with installing wine"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-24
Hi

thank you for reading my post
I have installed some packages using add/remove application and it returned error in installation.

Now what ever that i want to install return error for example:

```

legolas@personalPC:~$ sudo apt-get install libdvdcss2 w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up msttcorefonts (1.8ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Hobo Joe on 2007-05-24
I'd use this tutorial if I were you:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by eltorodeoro on 2007-05-24
i think prior to installing msttcorefonts, you need to install cabextract.

this is also required for wine.

---

### Post by Sparkster185 on 2007-05-24
> /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

This sounds like you have two things trying to install/update/remove packages at the same time.  If you have Synaptic open while you're trying to install from the command line, it won't work.  Close anything else that might be using the package database, see if that works.

---

