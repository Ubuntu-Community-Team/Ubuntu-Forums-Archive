---
title: "ATI Radeon 9800 &amp; ATI Accelerated Driver = black screen"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ostekongen on 2007-10-22
As a noob Linux-user I am experiencing a few problems with my new Ubuntu 7.10 installation. I have absolutely no prior knowledge with Linux so any step by step help would be the most useful. 

I'm dual booting with Windows XP, but I'm having some trouble. After installation the first reboot went well and Ubuntu opened. The only problem I experienced was that 3D effects didn’t look all that great. Then I got a popup telling me that a ATI Accelerated graphics driver was available in Restricted Drivers for my ATI Radeon 9800 and I thought lucky me, now I can get the 3D effects working properly.

I installed the driver and rebooted. Now everything seems to go pretty well, the Ubuntu logo appears. The status bar reaches full and then the system just stops on a totally blank black screen. Nothing happens.

Thank you for any help you can offer!

---

### Post by Pumalite on 2007-10-22
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Once IN the system, you might want to try ENVY or download and install from ATI.

---

### Post by ostekongen on 2007-10-22
> **Pumalite said:**
> Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Once IN the system, you might want to try ENVY or download and install from ATI.

Thanks.

What is ENVY and how do I try it and why? If I choose to download the driver from ATI, is it just at matter of click and install?

---

### Post by Fanin on 2007-10-22
i had the same problem once in feisty, things just got worse and worse, until at last i had to reinstall ubuntu, because nothing was working..

oh and btw, er du dansker?

---

### Post by Pumalite on 2007-10-22
If you want my honest opinion, your ATI card is a problem in Linux because ATI does not support it. Nevertheless, they are workarounds. One of them ENVY:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
You will find here all you need to know about ENVY.
This is ATI:[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
You can download from here and follow their instructions, but is iffy.
If I were you I'd get an Nvidia Card and your problems would be over. Nvidia supports Linux.

---

### Post by ostekongen on 2007-10-23
> **Fanin said:**
> i had the same problem once in feisty, things just got worse and worse, until at last i had to reinstall ubuntu, because nothing was working..

Are you also using a Radeon 9800 card and how did you eventually solve installing a driver and getting it working?

> **Fanin said:**
> oh and btw, er du dansker?

Yessir

> **Pumalite said:**
> If you want my honest opinion, your ATI card is a problem in Linux because ATI does not support it. Nevertheless, they are workarounds. One of them ENVY:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
You will find here all you need to know about ENVY.
This is ATI:[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
You can download from here and follow their instructions, but is iffy

Thank you for the links. It sounds like you are suggesting using ENVY over a direct download from ATI? One thing I don’t understand is why Ubuntu is prompting me to install a non working driver via Restricted Drivers. Isn’t the download just coming from ATI themselves?

> **Pumalite said:**
> If I were you I'd get an Nvidia Card and your problems would be over. Nvidia supports Linux.

I hear you, but for now that isn’t an option. I just want to try out Ubuntu, to see if this can be a reliable alternative to Windows.  Maybe down the road I will get a Nvidia card.

---

### Post by fulmitz on 2008-02-21
Any luck with this?  I tried Envy as well as a manual install and still get a blank screen every time.  I'm using an ATI 1650X AGP card using DVI out to a Sony LCD.  Thanks,

fulmitz

---

