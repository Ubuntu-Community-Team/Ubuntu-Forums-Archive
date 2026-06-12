---
title: "Mouse playing up?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by dink1000 on 2007-06-27
i was having trouble with my pc that it was only displaying 640x480.

fixed that but i've now got a problem with my mouse

i used the dpkg-reconfigure xserver-xorg command to alter the resolution and some how get the desktop effects to work:-? 

the mouse is a genius netscroll ps/2 wireless.

what happens is either the left button does nothing or it zooms in and out with the movement:confused:

i've tried all the options in the xserver? screen that i think might work but nothing.

all i'm after is the buttons to work with the scroll wheel. 

i also don't know how to open the xorg.conf file?

---

### Post by ukripper on 2007-06-28
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by dink1000 on 2007-06-29
right i tried booting off the live cd and the mouse works perfect.

is there any way of finding out when running the live cd what drivers it's using for the mouse?

---

### Post by dink1000 on 2007-07-02
this is what i got from the live hardware info screen when i booted from the live cd.

is there any way i can get this info into xserver/xorg ?:confused:

---

