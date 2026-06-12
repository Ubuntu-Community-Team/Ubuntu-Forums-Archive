---
title: "copy paste as root (Solved)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by spacegypsy on 2006-10-11
Hi;
does someone know how to copy paste as root in Ubuntu to solve [this]("http://www.ubuntuforums.org/showthread.php?t=272919")problem?
thanks

---

### Post by ciscosurfer on 2006-10-11
If you need to copy and paste as root, there are many ways of accomplishing what you need.  You can create a launcher and use 'gksudo nautlius' (without single quotes) as the command, and you'll then have root access via nautilus.  You can also try using Automatix and download Azureus that way.  I had similar problems with permissions after installing and had to modify permissions on the Azureus directories in order to get Azureus to work correctly.

---

### Post by annda on 2006-10-11
use ```
sudo cp something somewhere
``` and type your password at prompt or launch your gui file manager with e.g. ```
gksudo nautilus
``` (if you use gnome)

---

### Post by spacegypsy on 2006-10-11
Works for me.  :)

---

