---
title: "Laptop &amp; External Monitor"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-05-31
I have a laptop running ubuntu, with both kde and gnome installed, and I would like to be able to use my external monitor to extend the desktop, not to clone it. How do I go about doing this?

Thanks :)
Ajeffreys

---

### Post by kernel tom on 2007-05-31
you'll need to edit your xorg.conf file

sudo nano /etc/X11/xorg.conf

take a look here before doing so

[http://ubuntuforums.org/showthread.php?t=455852&highlight=multiple+monitors](http://ubuntuforums.org/showthread.php?t=455852&highlight=multiple+monitors)

look-a-like xorg.conf file, with some fix to it

---

### Post by Sparkster185 on 2007-05-31
In KDE if you go to the section where you can adjust monitor settings, there's an option for "Display 2".  Find the corresponding menu in GNOME and see if you can enable Display/Device 2.

You might have to reconfigure Xorg, but I'm not sure.

---

### Post by ajeffreys on 2007-05-31
Thanks a lot guys, I'll try that and see what happens.

---

