---
title: "xorg.conf help"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by akschnare on 2007-08-01
Hey, I just got an Nvidia 7800 and I installed the drivers with envy and everything seems to work. Except, when I go into the configuration menu that came with the drivers, I set everything how I like it, and it wants you to save it to the x configuration file but it won't let me. It tells me "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup".

Can anyone help me?

---

### Post by splintercellguy on 2007-08-01
sudo rm /etc/X11/xorg.conf.backup

---

### Post by akschnare on 2007-08-01
Well that removed it, but now I get this message. "Unable to create new X config backup file '/etc/X11/xorg.conf.backup".

---

### Post by forestpixie on 2007-08-01
are you using nvidia-settings from terminal - if you are make sure you use 

gksudo nvidia-settings

---

### Post by akschnare on 2007-08-01
No, I'm  using the menu that was installed under Applications>System Tools.

---

### Post by akschnare on 2007-08-01
Does anyone know how to fix this??

---

### Post by fastpakr on 2007-08-01
Sounds like whatever icon you're launching isn't executing with sudo/gksudo access.  Either run it from the shell using sudo (or gksudo if it's graphical) or go into the 'Main Menu' applet and edit the launcher properties so the shortcut uses sudo access.

---

