---
title: "ATI with 3d Desktop Effects, 7.10  running smoothly"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-10-21
i would like to share this with ATI graphic card users, where am running now the 3d Desktop effects on my ATI Radeon Mobility X1400 successfully without any problem on Gusty Gibbon, here are some simple steps without any complicated configurations :

1- start with fresh new installation of Gusty Gibbon

2- System > Administration > Restricted Drivers Manager : enable the check box for the ATI driver, this will ask for installing new drivers, proceed with the wizard.

3- System > Administration > Synaptic Package Manager :  install the package xserver-xgl

4- log out and then log in again

5- Preferences > Appearance >>> tab Visual Effects  : select extra effects

6- System > Administration > Synaptic Package Manager :  install the package compizconfig-settings-manager , this package is the configuration section for the Desktop effects.

7- in terminal run ccsm to configure ur desktop effects.


so thats all, its working 100% with my ATIi hope it works with u too.

---

### Post by Klargodut on 2007-10-21
Used the same procedure some days ago to get it working with the 200m card as well. Works like a charm.

---

### Post by macvr on 2007-10-21
I too hav d same X1400 card, but i have not installed UBUNTU in my PC. Is there any way tht i could check out d visual effects B4 I INSTALL UBUNTU? thanx in advance

---

### Post by akkad on 2007-10-21
there is the Live CD where u can run ubuntu from the cd without affecting ur harddisks, but am not sure if the effects can be enabled using the live cd, i will try it and give u my feed back.

---

### Post by gcrussell1 on 2007-10-21
I'm brand new to Ubuntu and to Linux in general. I stumbled upon this post, and since I'm running a Radeon Mobility 9600, I thought I'd try to get this running. However, when I ask Ubuntu to enable the ATI accelerated graphics driver, I get this error:

The software source for the package

   xorg-driver-fglrx

 is not enabled.

Incidentally, the same error occurs when I try to run the Broadcom 43xx firmware driver from the same menu, except that the software source is "  bcm43xx-fwcutter". I'm probably just too ignorant to do something obvious here, but if anybody could help me get these drivers up and running (particularly the ATI one), I'd appreciate it greatly.

Edit: Nevermind - I found the solution in another thread: I didn't have downloading enabled for universe and multiverse software. I'ts moving along fine now.

---

### Post by William S on 2007-10-21
I followed this guide and now have to use KDE (running ATI) now because that x-org package screwed up GNOME. 
Maybe remove it to get GNOME back?

---

### Post by akkad on 2007-10-21
gcrussell1,  System > Administration > Software Sources , check the restricted drivers option then try again.

---

### Post by akkad on 2007-10-21
William S, what happened with ur gnome, can u log in into the desktop ?

---

### Post by pertti on 2007-10-21
> **William S said:**
> I followed this guide and now have to use KDE (running ATI) now because that x-org package screwed up GNOME. 
Maybe remove it to get GNOME back?

If your Gnome went kaboom after installing xorg-xgl, try this in a terminal:

```
touch ~/.config/xserver-xgl/disable
```

This will create an empty file which will cause XGL not to load the next time you log into Gnome and switch back to regular Xorg. If this works, perhaps you'd want to remove xorg-xgl alltogheter.

---

### Post by William S on 2007-10-21
Well removing that package wasn't really a good thing. Now I cant use any form for GUI. 

I used:  
```

sudo apt-get remove-purge xserver-xgl

```

And using the normal boot wouldn't work, I have to use recovery mode just to get into a terminal.

---

### Post by akkad on 2007-10-21
actually for removal i used to use synaptic cuz it offers u to remove the refenced packages too, any way why dont u try to install xserver-xgl again from the terminal which u r stuck on.

sudo apt-get install xserver-xgl

---

### Post by CheshireMac on 2007-10-30
I'm also running on Gutsy, and I went through the steps provided. It worked like a miracle after much frustration with the drivers and such. I like the whole package, and how neat and tidy the config-gui is. I also noticed that the whole change left me with a much larger resolution than before. I forgot that Compiz does that. Anyhow, thanks for the HowTo. It's a lot off my mind now. :)

---

### Post by stillingen on 2007-10-30
Thank you for posting this. I have IBM T42 with ATI Technologies Inc RV350 [Mobility Radeon 9600 M10], and can confirm that this procedure worked for me. 

After the installation of the ATI restricted driver restarting X was apparently not good enough so I had to reboot. Compiz benchmark is showing 50 frames/sec, this was around 75 frames/sec using the Open Source driver, but than again this was not stable...

---

### Post by GurneyHalleck on 2007-11-04
It did work for me for a few days. All the compiz effects working very nicely.

Then, yesterday, graphics started to drag like a corpse chained to a pickup truck. Looking at system monitor, xgl was using 100% CPU time for minutes at a go every time I caused any graphic update. Disabling compiz didn't help, so I removed the xgl package. Now everything is back to a usable speed again.

Given that problem and the fact that compiz effects seemed to disable access keys using the Alt key (but not the AltGr key, bizarrely), I'm going to steer clear of compiz and fancy effects for the time being.

---

### Post by hiddensphinx on 2007-11-05
> **Klargodut said:**
> Used the same procedure some days ago to get it working with the 200m card as well. Works like a charm.

Same here :)

never could get my ATI Xpress 200M to work with Fiesty but now things looks awesome with Gutsy Gibson :guitar:

---

### Post by yatesl on 2008-01-13
I've avoided Ubuntu Linux until now, due to this very problem.  With my X1400, it never went to the full 1200x800 setting (only 1024x768), and I always got 

The software source for the package
xorg-driver-fglrx
is not enabled.

Whenever I tried.  However, if this works when I install Linux in a couple of hours, I think I'll stay on for good.  And, if so, I cannot thank you enough.

---

