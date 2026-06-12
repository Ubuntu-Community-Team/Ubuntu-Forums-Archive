---
title: "Lost my GUI"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by strokeboy on 2007-05-25
Okay, well I installed 7.04 and while trying to muddle through and get an Nvidia PCI geforce 5200 driver installed, I mucked around (evidently) with the X something and now I have only the command line.  I am dual booting with xp and even that looks like it is in safe mode now.  I have done something terrible.  Please advise.:(

---

### Post by Nikron on 2007-05-26
Do "sudo nano /etc/X11/xorg.conf" Scroll down, find the driver section, change the driver to 'nv', save it, and 'startx'.

---

### Post by starcraft.man on 2007-05-26
> **strokeboy said:**
> Okay, well I installed 7.04 and while trying to muddle through and get an Nvidia PCI geforce 5200 driver installed, I mucked around (evidently) with the X something and now I have only the command line.  I am dual booting with xp and even that looks like it is in safe mode now.  I have done something terrible.  Please advise.:(

Easy fix. Login to the console with your name and pass. Then run this command:

```
sudo dpgk-reconfigure xserver-xorg
```

keep selecting ok to the default responses till you get to the driver section. Select "nv" instead of "nvidia" that will switch to the 2d default driver. Then reboot after you save. 

Thats it, then use [Envy.]("http://www.albertomilone.com/nvidia_scripts1.html") It will get you intalled with Nvidia drivers and configured right, follow instructions on site and use stable version 0.93.

Edit: Or you nikron's way, he beat me to it. I just think most users prefer the gui configure... I try to avoid using nano >.>.

---

### Post by strokeboy on 2007-05-26
Thank you both for responding.  I have been working on this for some time but, with persistance and a big assist, it is now working!!!  I don't want to go into what I was doing wrong, but Thanks again!!!:D

---

