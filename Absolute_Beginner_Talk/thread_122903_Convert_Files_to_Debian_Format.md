---
title: "Convert Files to Debian Format"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-01-28
How do you convert .rpm, .tar.gz, or .tar.b2z to .deb (Debian Format) ? I know that Alien let's you convert .rpm but what is the command to use it ? I am trying to install xlink and a driver for a lexmark printer.

---

### Post by kingsidy on 2006-01-28
all you have to do is cd into the directory w\here the debian package is located and type in > sudo alien *name of rpm package* this will generate a .deb package which you install by the usual dpkg -i *package name*. 

As far a tar.gz there is not a way that i know of that allows you to convert to deb like you can with rpms. you have to do the untar, make and whatever for that package

---

### Post by hen3rz on 2006-01-28
Just expanding on Kingsidy this webpage has all of that information and a little bit more in detail.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

