---
title: "Installing ATI Drivers from blank screen"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by mikethepirate on 2007-12-18
Hey guys, this is part of my ongoing battle to get CS:S running on my computer :(
OK so, I downloaded the driver for my X600 off of the ATI website and ran the setup in terminal (because it wouldn't allow me to do the GUI installer even though I had logged in as root).  After I did this, I tried to open the ATI Catalyst Control center, but it told me that the drivers where not installed correctly.  Being the noob that I am, I then disabled the Restricted Graphics Accellerated drivers in the Restricted Drivers menu.  I then restarted the computer and it got to the log in screen and logged in but the screen just when black and kicked me back to the log in screen.  I then tried the dpkg-reconfigure xserver-xorg and went through the menu's leaving everything on the default answers and restarted the computer.  Now my screen goes completely black after the Ubuntu loading bar finishes. No log in screen or anything :(.  I think this has everything to do with me disabling the Restricted drivers, so I was wondering how I would get them back in the recovery mode.  Any help would be greatly appreciated and any tips on getting Counter Strike Source to run well on my computer would be greatly appreciated.  I am running the 32-bit version of Gutsy Gibbons and I have a 256mb ATI Radeon X600 video card and a P4 HT running at 3.0ghz.

thanks in advance :)

---

### Post by mikethepirate on 2007-12-18
I've heard that nVidia cards have better luck in ubuntu and I'm getting a 8600GT soon.  Do you think it would be best for me to wait untill then and reinstall the OS?  I don't have anything important on ubuntu, but it will be boring to wait 3 hours for CounterStrike to download through steam again lol.

---

### Post by mikethepirate on 2007-12-18
bump

---

### Post by bumanie on 2007-12-18
Your ati driver should work. What I would try is to reinstall. Are trying to install ubuntu 7.10?
I use a nvidia agp, so have not tried to install ati personally. But my experience was that I had to turn off x server to install the driver with my gutsy install. I can't say whether this is the same with ati cards.
If you look on this link [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) you will find an ati driver installer for your card. You could try that. Alternatively you could follow this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
I would probably try the latter guide first, as I suspect it is aimed at older cards/drivers like your one.

---

### Post by Niniel on 2007-12-18
I've installed 7.10 on a notebook with an ATI mobility 9600 card and on a desktop tower with an nVidia Ti4200... granted, both cards are quite old, but I found I'm not having any problems with the ATI (proprietary drivers), which is more than I can say about the nVidia card (lost all window borders for a while after I installed the proprietary drivers; was relatively easy to fix though).

Anyway, if you are willing to reinstall anyway, just do it. :)

---

