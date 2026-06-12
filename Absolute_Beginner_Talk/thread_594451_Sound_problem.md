---
title: "Sound problem"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Frogsmasher on 2007-10-28
Hey guys I am brand new to Ubuntu and through help on various forums I have managed to explore somethings, but the one thing no one seems able to answer is my sound problem. My speakers just do not work. They are plugged in and all the system volumes are at max. I do not know how to go about exploring what might be wrong any ideas? Help is much appreciated

-Frogsmasher

---

### Post by Crafty Kisses on 2007-10-28
> **Frogsmasher said:**
> Hey guys I am brand new to Ubuntu and through help on various forums I have managed to explore somethings, but the one thing no one seems able to answer is my sound problem. My speakers just do not work. They are plugged in and all the system volumes are at max. I do not know how to go about exploring what might be wrong any ideas? Help is much appreciated

-Frogsmasher

Post the following output:
```
lspci
```

---

### Post by Frogsmasher on 2007-10-28
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

---

### Post by Frogsmasher on 2007-10-28
Did I do that right?

---

### Post by gobuntu on 2007-10-28
Frogmasher,

Some facts would be needed:

1. What sound card is at use? Laptop, does sound work in Windows, if dual-booting?

2. What version of Ubuntu, does sound play the boot-music?

3. What player(s) have you installed? Have you downloaded the 'restricted' drivers for them?

---

### Post by Frogsmasher on 2007-10-28
I think it is a soundblaster pro. I do not dual boot, but my sound three days ago when i had Xp on my computer. I have Ubuntu 7.10. I checked and Ubuntu says that there are no restricted drivers that I need.

---

### Post by The O'Really Factor on 2007-10-28
Hmm, It shows that you have integrated sound and PCI sound. I assume you're using the actual sound card and not the integrated. I'll go dig up a tutorial real quick.

---

### Post by The O'Really Factor on 2007-10-28
Alright, well here the specific tutorial for the card you have (Ensoniq ENS1370) as shown in your output to lspci can be found here: [http://www.alsa-project.org/main/index.php/Matrix:Module-ens1370](http://www.alsa-project.org/main/index.php/Matrix:Module-ens1370). If you have any questions about the tutorial just ask here.

---

