---
title: "imac g4 and my wacom tablet"
date: 2010-08-26
forum: Apple Hardware Users
---

### Post by seconteen on 2010-08-26
Hey guys. 

I need some major help. I have this imac g4 that I put Ubuntu 10.04 on in hopes that i could make my devices work with it. internet doesn't work on it (cus it's apparently not compatible with my dlink)

But my issue is, i'd like my graphire 4 to work. I plug it in and when i move the pen, nothing happens. It has the stuff installed to make it work apparently but it's like it hates my tablet and ignores it.

I lsusb'd and it shows the tablet sitting there. any ideas? I looked everywhere for help but i couldn't find anything to help it.

---

### Post by linuxopjemac on 2010-08-26
I think you have to make an entry in the xorg.conf file for this one. Have a look [here]("http://mac.linux.be/content/powerbook-g4-radeon-ly-xorgconf").

---

### Post by seconteen on 2010-08-26
for some reason though i get an error when i try to edit xorg.conf

i do the gksudo gedit thing then it comes up, i make my changes but it wont let me save it.

---

### Post by linuxopjemac on 2010-08-26
in the terminal:

```
sudo nano /etc/X11/xorg.conf
```

then make your changes
CTRL-X and "y" to save

---

### Post by seconteen on 2010-08-26
when i do that, it doesnt boot up right it'll flash something about "Ubuntu 10.04" then flicker then go to black never going to anything else

---

### Post by linuxopjemac on 2010-08-27
```
sudo cat /var/log/Xorg.0.log
sudo cat /etc/X11/xorg.conf
```


paste them here please

---

