---
title: "i don't know which video card i have, how do i find out?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by adam.white on 2007-03-31
Ive just installed ubuntu edgy, and my screen resolution is only 800x600, i don't know what video card i have and how to find out! im really stuck :(  please help!

adam x

---

### Post by teaker1s on 2007-03-31
```
lspci | grep VGA
```
to change it's settings so gnome can then use the settings

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by adam.white on 2007-03-31
Thanks! it says 'ATI Technologies Inc RS480 [Radeon Xpress 200G Series]' so how do i install that and get my screen to a better resolution, something like 1024x1280 or something, im completely new to this! thanks for your help

adam x

---

### Post by taurus on 2007-03-31
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by wpshooter on 2007-03-31
Adam:

You need to go to Synaptic and search by **NAME** for **fglrx** driver and then install it.

You then need to edit the video driver section of your /etc/X11/xorg.conf file and change the driver specification from "ATI" to "fglrx".  Make sure you make a backup of the xorg.conf file under a different name BEFORE you edit/change it.

Then reboot.

Good luck.

---

