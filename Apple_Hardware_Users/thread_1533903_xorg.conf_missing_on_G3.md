---
title: "xorg.conf missing on G3?"
date: 2010-07-18
forum: Apple Hardware Users
---

### Post by Muskiet on 2010-07-18
I've installed Ubuntu 10.04 LTS on an IMac G3 with 192 Mb RAM using the alternate PPC disk.
The installation went well and when starting up I hear the "drum" which sounds when showing the login screen but the screen stays blank.
I found a solution to this problem [here]("https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3"), but after typing > sudo nano /etc/X11/xorg.conf it opens up a new file in stead of editing the original.
when going to the directory I also don't find an xorg.conf file.
When typing > locate xorg.conf it only finds a directory called /usr/lib/X11/xorg.conf.d

Please help.

---

### Post by linuxopjemac on 2010-07-18
There is none there. You have to put one there:
[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

