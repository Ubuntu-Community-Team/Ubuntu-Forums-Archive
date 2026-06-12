---
title: "What video drivers are usually installed with a live cd? (ubuntu or not)"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-16
The "ati" drivers for both Ubuntu Live CD and Knoppix Live CD crash my computer.  Under Ubuntu, its a dead freeze; I'm unable to restart x-server or open a terminal or even move my mouse.  Under Knoppix, it killed x-server and sent me to a terminal and said something about "requiring reboot"; I couldn't restart x-server or otherwise get back to a desktop, just terminal.  

I know it is the "ati" drivers that come with both distributions that is causing the crash.  When I use "vesa" drivers (by booting under the "graphic safe" option of Ubuntu), I never crash.  Likewise, when I had Ubuntu installed on the HDD, "ati" drivers crashed the computer but "vesa" did not.  

Are the "ati" drivers the open-source drivers?  It seems that those won't work at all.  I tried to use the restricted drivers when I still had Ubuntu installed, but I wasn't getting any video acceleration with those (according to glxinfo | grep direct). 

The main thing that is stopping me from using Ubuntu full-time is the constant headache with video drivers.  Do I have any other options?

I'm using a Radeon 9500 Pro (r300 core).

---

### Post by overdrank on 2007-08-16
> **TheOrangePeanut said:**
> The "ati" drivers for both Ubuntu Live CD and Knoppix Live CD crash my computer.  Under Ubuntu, its a dead freeze; I'm unable to restart x-server or open a terminal or even move my mouse.  Under Knoppix, it killed x-server and sent me to a terminal and said something about "requiring reboot"; I couldn't restart x-server or otherwise get back to a desktop, just terminal.  

I know it is the "ati" drivers that come with both distributions that is causing the crash.  When I use "vesa" drivers (by booting under the "graphic safe" option of Ubuntu), I never crash.  Likewise, when I had Ubuntu installed on the HDD, "ati" drivers crashed the computer but "vesa" did not.  

Are the "ati" drivers the open-source drivers?  It seems that those won't work at all.  I tried to use the restricted drivers when I still had Ubuntu installed, but I wasn't getting any video acceleration with those (according to glxinfo | grep direct). 

The main thing that is stopping me from using Ubuntu full-time is the constant headache with video drivers.  Do I have any other options?

I'm using a Radeon 9500 Pro (r300 core).

Hi and I an lucky when it comes to ati, I have had a easy time in setting and use the graphics card and that would include nvidia. If you can get ubuntu installed with the vesa drivers then there is many "how to" to get you going and this is one that has help me and others
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Good luck! :)

---

### Post by TheOrangePeanut on 2007-08-16
Unfortunately, that guide uses the drivers that crash my system.

---

### Post by overdrank on 2007-08-16
> **TheOrangePeanut said:**
> Unfortunately, that guide uses the drivers that crash my system.

Ok sorry, This link has instruction to install the ati latest drivers 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Maybe if you compile it from ATI that will give you the performance that you need.

---

### Post by Hobo Joe on 2007-08-16
Start with whatever drivers work for you, and then follow these instructions:

First download and install Envy:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

```
Just open the file, it will install for you.

Then, press 'install ATi drivers' and let it finish. Make sure to let it configure your xorg.conf for you.

Reboot.

---

