---
title: "Qtparted, not root user?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-01
When using Gtparted, it wont show any of my partitions, it says, it might be becouse im not a root user? How do I become this?

---

### Post by raptros-v76 on 2006-07-01
when you run qparted, do kdesu qparted as the command

---

### Post by T700 on 2006-07-01
Open a terminal window (the command line) and preface command to start the program with "kdesu" (without the quote marks).  At the prompt that comes up, enter your normal password.

Paul

---

### Post by aysiu on 2006-07-01
Just to clear up the confusion a bit. If you're using Gnome, you should use the command: ```
gksudo qtparted
``` If you're using KDE, you should use the command: ```
kdesu qtparted
``` Please keep in mind, too, that you cannot use QTParted (or any partitioning program) on a partition that's mounted or in use. You may need to use it off a live CD instead.

---

### Post by MozartlovesUbun2 on 2007-12-16
gksudo qtparted
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:62: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:63: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:64: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

---

### Post by aysiu on 2007-12-16
So switch to a different theme other than Creamy Classic or Clearlooks.

---

