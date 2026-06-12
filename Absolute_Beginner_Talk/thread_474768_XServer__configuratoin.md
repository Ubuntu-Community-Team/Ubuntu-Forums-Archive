---
title: "XServer  configuratoin"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Rufi0h on 2007-06-15
To start off i was trying to install a nvidia driver and when i did i restarted the computer it said it couldnt run xserver

it saids something along the lines of
The X server i now disabled.  Restart GDM when it is configured correctly.

is there a command where i can restore this so i can at least start my computer again. then i will start over.

---

### Post by Rocket2DMn on 2007-06-15
in terminal (which seems to be all you have):
```
sudo dpkg-reconfigure xserver-xorg
```
This will help you setup the Xserver correctly, but please do read through it to get it to work the first time

---

### Post by Rufi0h on 2007-06-15
your my hero, thanks

---

