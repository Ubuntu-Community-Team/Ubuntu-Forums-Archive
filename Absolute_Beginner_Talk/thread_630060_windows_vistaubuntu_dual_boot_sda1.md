---
title: "windows vista/ubuntu dual boot sda1?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by aqchat300 on 2007-12-02
:mad: i have a ubuntu 30 gig hd and a fat vista one aka sda1 popping up so whats going on...? is my vista partition messing with ubuntu help me...:confused:


EDIT:god i hate my noobish ness i figured out i had to sudo umount /dev/sda1 im sorry i even posted this i should of google first... please forgive me :(

---

### Post by aqchat300 on 2007-12-03
nevermind... everytime i restart it remounts... :( any help.... i gtg sleep so when someone can post well im gone go ahead gimme some help i would appreciate ok :)

---

### Post by bdtgp on 2008-02-12
if you dont want it to show up on the desktop type this in a terminal:
```
gconf-editor
```
Then go to apps>nautilus>desktop and uncheck volumes visible.  It will still be mounted so you have access but it wont be on your desktop.

---

