---
title: "Installing Proprietary ATI Drivers (fglrx)... Help?"
date: 2006-06-25
forum: Apple PPC Users
---

### Post by zachws on 2006-06-25
I have a radeon mobility 9550 i think (part of an ibook g4)... i would like to install ATIs drivers so that I can then install xgl/compriz. i found the official how-to and follow the steps until I got > Couldn't find package xorg-driver-fglrx

I searched around but ultimately I am a novice and I do need help. please assist. dapper is such a pain but i am such an addict.

---

### Post by zachws on 2006-06-25
my source for my attempt was 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

and i got that error in the terminal.

---

### Post by EReckase on 2006-06-25
[QUOTE=zachws]I have a radeon mobility 9550 i think (part of an ibook g4)... i would like to install ATIs drivers so that I can then install xgl/compriz. i found the official how-to and follow the steps until I got 

I searched around but ultimately I am a novice and I do need help. please assist. dapper is such a pain but i am such an addict.[/QUOTE]


Which step was this on?  It might mean a typo, might mean something else, depending on when it failed.

---

### Post by zachws on 2006-06-25
> Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv



ok, well im not sure if my restricted repository is enabled. i tried to enable it but maybe i screwed up. after i type in 'sudo apt-get install xorg-driver-fglrx' i get:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx

```

thanks

---

### Post by EReckase on 2006-06-25
Try opening up synaptic and reloading the packages (the reload button in the upper left).  You may have updated the repositories, but the cached contents may not have been updated.

Hope this helps.

---

### Post by zachws on 2006-06-25
all synaptic shows is "xserver-xorg-driver-ati" which is installed.

---

### Post by Peter76 on 2006-06-25
The fglrx driver is proprietary ATI driver only released for the x86 architecture, so unfortunately it doesn't run on ppc Macs... We should all start writing emails to ATI to release the driver for ppc as well

---

### Post by zachws on 2006-06-25
[QUOTE=Peter76]The fglrx driver is proprietary ATI driver only released for the x86 architecture, so unfortunately it doesn't run on ppc Macs... We should all start writing emails to ATI to release the driver for ppc as well[/QUOTE]

ai, my heart is broken. but thanks for the info. i will email right now.

---

### Post by DJ_Max on 2006-06-25
[QUOTE=Peter76]The fglrx driver is proprietary ATI driver only released for the x86 architecture, so unfortunately it doesn't run on ppc Macs... We should all start writing emails to ATI to release the driver for ppc as well[/QUOTE]
I doubt that is ever going to happen, there may have been a chance, but that was before Apple switched to Intel chips.

---

### Post by slux on 2006-06-26
What proprietary means is "you'll only use it the way we want you to" unlike the rest of the GNU/Linux OS...

---

### Post by kellogs on 2006-06-26
the only hope for 9250 and up in Mac is to wait for proper Xorg support. in 7.0 they've support for those newer ati cards, but its not enabled by default(experimental).

Let's wait for xorg people to fix it in the ati open source drivers, Ati won't release fglrx for mac.

I've been two months without opengl. I can wait 8).

---

### Post by 3rdalbum on 2006-06-27
No, ATI should fix all the problems with their Radeon Xpress 200 cards on x86 Linux before working on PPC drivers. I'd much prefer to be able to log out of/shut down my PC than get wobbly windows on my iMac!

---

### Post by zachws on 2006-06-27
do you think 'edgy eft' will have support for graphics acceleration for the new ATI cards (ppc). i assume it will as you say it is availible now experimentally... that is good news. I hope edge eft can just support an ibook 'out of the box'. with the present version of ubuntu, an ibook user must tweak the mouse setting, tweak the wireless settings and go w/o xgl/compiz (one of the most attractive aspects of this whole shabang). just thinking on paper... (e-paper)

---

