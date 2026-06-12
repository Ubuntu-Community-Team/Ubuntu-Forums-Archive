---
title: "How to rename files in terminal"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by nisukka on 2005-09-07
Hi!
I was trying to configure the extra buttons for my mouse and edited the /etc/X11/xorg.conf file. Now when I boot up my Ubuntu, the GUI does not load (is it called X or Gnome?). I can log in from non-graphical login.

Fortunately I managed to make a backup copy of the xorg.conf and saved it as xorg.conf_backup.
I would like to know what I need to type to rename the xorg.conf to xorg.conf_backup in terminal. I am not very familiar with using terminal commands in Linux.
Thanks!

---

### Post by mirons on 2005-09-07
$ apropos rename 
will suggest you the solution ;-)

---

### Post by nisukka on 2005-09-07
I managed to rename the file using mv command.
Thanks anyway!

---

### Post by SNo0py on 2005-09-07
move source target

---

