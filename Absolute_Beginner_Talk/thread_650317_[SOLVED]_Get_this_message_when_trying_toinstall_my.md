---
title: "[SOLVED] Get this message when trying toinstall mythtv"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-26
tlc@tlc-desktop:~/Desktop$ sudo aptitude install mythtv-0.20.2
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tlc@tlc-desktop:~/Desktop$

---

### Post by lisati on 2007-12-26
Were you trying to do something else that updated your system at the same time???????

---

### Post by goldencj on 2007-12-26
yes just before this

---

### Post by goldencj on 2007-12-26
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ ./configure
You must have the Lame MP3 encoding library installed to compile Myth.
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$

Just downloading lame now...

---

