---
title: "ATI AIW Radeon X800XT Need Help"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by cyphin6 on 2005-12-03
:confused: Well I know absolutely nothing about Linux coding and I'm very lost when it comes to making a driver out of nothing I went to the ATI website and downlaoded the Linux file but when I get to the Xfree86 download I have no idea what to get or what to download or what to do with the files after I downlaod.  Anways I am completely lost and need extreme help.  If anyone can other a few words of wisdom that would be great.  Thanks again!

---

### Post by tokyovigilante on 2005-12-03
All you need to do to get 3D acceleration in Ubuntu with ATI cards is:

Open a terminal and type:

```
sudo apt-get xorg-driver-fglrx fglrx-control
sudo dpkg-reconfigure xserver-xorg
```

This will present you with the X config utility. Choose fglrx (the Radeon accelerated driver) as your video driver, and accept the defaults for the other questions. 

Then hit <Ctrl>-<Alt>-<Backspace> to restart the X server. If it doesnt start straight back up then type startx at the command prompt. 3D acceleration should now be running.

---

### Post by steviecee on 2005-12-03
I have found it a bit trcky setting up fglrx but found the following thread a great help.

[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)

all the posts make intersesting reading but if you click on "THE HOW TO" link on the first post, it gives you a comprehensive guide on installing the driver.

If you need to modify XORG.CONF, again its a bit tricky and dangerous to do a manual edit for us newbies.

Please therefore see my post at:

[http://ubuntuforums.org/showpost.php?p=540063&postcount=392](http://ubuntuforums.org/showpost.php?p=540063&postcount=392)

Hope this helps:p

---

