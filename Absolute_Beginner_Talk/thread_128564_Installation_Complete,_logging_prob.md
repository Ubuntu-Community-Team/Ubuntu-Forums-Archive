---
title: "Installation Complete, logging prob"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by Tomer on 2006-02-11
Hey there, like most of you, i'm noob to Linux.
I've successfully installed Ubuntu64 (not mentioning the xserver prob), and logged in with my user/pass. 
after that i got a few lines telling that ubuntu takes no warrenties etc, and get a command prompt. from here i'm clueless...
this is where i need your help.
so thanks

---

### Post by taurus on 2006-02-11
I guess you installed a server version instead of a desktop, default.  Now, if you want to have that nicely looking Gnome window manager, then you need to install it as

sudo apt-get install ubuntu-desktop

Or for Xfce4, then

sudo apt-get install xubuntu-desktop

Or for KDE, then

sudo apt-get install kubuntu-desktop

Try one of the above and you will have a window manager to play around with...

---

### Post by Tomer on 2006-02-11
well, tried doing it. 
but i get the following msg: "ubunto-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded."
and then it returns me to the command prompt...

---

### Post by taurus on 2006-02-11
Sounds like you need to configure your X so Gnome would start then.  Run this at the prompt,

sudo dpkg-reconfigure xserver-xorg

---

