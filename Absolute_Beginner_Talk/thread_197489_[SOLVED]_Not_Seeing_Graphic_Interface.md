---
title: "[SOLVED] Not Seeing Graphic Interface"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by xHero on 2006-06-15
It says I cannot boot x server (graphic interface).  I believe its because it is not detecting my Video/GFX card.  How would I install the drivers or whatever I need to use.

I have an Intel Extreme Graphics 2 for Mobile

Thanks for helping a noob,

xHero

---

### Post by daller on 2006-06-17
Always happy to help!

Have you tried running:

```
sudo dpkg-reconfigure xserver-xorg
``` (In command-line :D)

The whole process should be kinda self-explanatory, but if you stumble - Simply ask for further help!

---

### Post by xHero on 2006-06-17
Pageage 'xserver-xorg' is not installed and no info is availiable.
Use dpkg --info (= dpkg-deb --info) to examine archive files, and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/spkg-reconfigure: xserver-xorg is not installed.


That's my error.

---

### Post by raptros-v76 on 2006-06-17
wow. this problem seems rampant.
try this:
```
sudo aptitude update&&sudo aptitude install xserver-xorg
```

---

### Post by Dr. Nick on 2006-06-17
[quote=raptros-v76]wow. this problem seems rampant.
try this:
```
sudo aptitude update&&sudo aptitude install xserver-xorg
```[/quote]

That could work, but I might try 

sudo aptitude install ubuntu-desktop

just to make sure you get gnome aswell as xorg.

---

### Post by raptros-v76 on 2006-06-17
yeah i guess. theres something wrong somewhere, thats screwing up many people, especially after new installs, that all of the xserver-xorg stuff suddenly is not there. it happened to my friend, and i;m not going into the details of what happened, but that's when i discovered that aptitude is a much safer way of doing things than apt-get. ever seen a kernel panic thingy?

---

