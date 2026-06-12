---
title: "messed up screen resolution"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-05
hi, i was messing around with screen resolutions, i have a 1280x768 widescreen monitor, but i wanted to see how a bigger resolution would work. but now i cant see anthing n my monitor, just a bunch of meshed lines... is there anyway to fix this? or will i have to re-install ubuntu? (i have 7.10) thank you....

~Nate

---

### Post by short3000y on 2007-12-06
can anyone please help? :(

---

### Post by The Tronyx on 2007-12-06
In a terminal please type:

> 
sudo gedit /etc/X11/xorg.conf


Go to pastebin.ca and paste the results there and please post the link.  

You may also want to try to reconfigure xorg by booting to the command line and typing:
> 
sudo dpkg-reconfigure xserver-xorg


---

### Post by nikoPSK on 2007-12-06
if you can't see anything on your monitor can you access the terminal? Or were you typing from windows....:confused:

---

### Post by short3000y on 2007-12-06
how do you check any of the boxes after you select your video driver? i keep going in circles...

---

### Post by short3000y on 2007-12-06
im typing from windows... but i can get a doslooking terminal going, using recoverymode.

---

### Post by -grubby on 2007-12-06
hit spacebar to check the boxes, and hit tab to tab to the enter key and hit enter

---

### Post by nikoPSK on 2007-12-06
Yah, just like when you are installing ubuntu from the alternate.

---

### Post by The Tronyx on 2007-12-06
> **short3000y said:**
> im typing from windows... but i can get a doslooking terminal going, using recoverymode.

And from that terminal have you run

sudo dpkg-reconfigure xserver-xorg

---

### Post by stupidkristina on 2008-03-16
sudo dpkg-reconfigure xserver-xorg

Worked great thanks

---

