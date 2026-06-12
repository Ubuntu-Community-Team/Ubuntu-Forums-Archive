---
title: "Changed my ATI AIW 1950 with a Nvida XXX 8800"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by tcmshow on 2007-12-08
I just changed my video card , I am running triple boot Ubuntu, THE Ubuntu is not starting up because it still looking for my old ati card.
How do I get the ubuntu studio to re dectect hardware and get back in.

Layman here very new to Ubuntu.

Thanks for any help

---

### Post by sloggerkhan on 2007-12-08
first, edit your xorg.conf to use vesa.
then,
try 
sudo dpkg-reconfigure xserver-xorg
from the command line
and choose the correct nvidia driver.

---

### Post by dcstar on 2007-12-08
> **sloggerkhan said:**
> first, edit your xorg.conf to use vesa.
then,
try 
sudo dpkg-reconfigure xserver-xorg
from the command line
and choose the correct nvidia driver.

And you have to install the Nvidia-new package before you do this!

---

### Post by tcmshow on 2007-12-10
I can't get in to ubuntu to the graphic interface, now that the nvida card is in it keeps telling me that it can't load ..

---

### Post by crjackson on 2007-12-10
1) Put the ATI card back in and reboot.
2) Turn Off the restricted driver.
3) Edit the xorg.conf file and replace **fglrx ** or **ati **with **vesa**
4) Reboot and ensure it's running with the vesa driver
5) Shut down
6) Install the Nvidia 88xx card
7) Reboot (fingers crossed)
8 ) If booted okay, install the restricted driver for the Nvidia card
9) Reboot (fingers crossed)
10) You're done...

I think this will do it.  At least I hope so...  Good Luck.

---

