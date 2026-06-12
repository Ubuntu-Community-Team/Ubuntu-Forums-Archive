---
title: "Wireless on Acer 3630 and ndiswrapper"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by othelios on 2008-01-28
Hi all, I'm new here and new to Ubuntu/Linux.

Anyway, I am trying to sort out the wireless on my Acer Aspire 3630 laptop (it uses the Broadcom chipset).

When trying out Ubuntu using the LiveCD I thought I would see if I could get the wireless to work first (I heard it was quite difficult).

I found this 

[http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

using option 2 (Feisty/Gutsy), which helped tremendously and got the wireless up and running with no problems. So, I decided to install Ubuntu.

Now I am using the same process as before but for some reason when its installing ndiswrapper it just sits there ans says:

Gutsy release detected.
Installing ndiswrapper-1.9...


and thats it. It doesnt do anything else. I've waited ~20 mins.

There is also a setup.log file that appears on the desktop when this happens and if you want I can post its contents here if that would help.

I know there are possibly other methods of getting this to work, but since this method worked before I would like to know why it isnt working now and get it to work.


Thanks

---

### Post by igknighted on 2008-01-28
Can you run the command "lspci" and post the output?  Most broadcom chips will be perfectly initialised to use the bcm43xx driver by the restricted driver manager, but some cannot.  That command will tell which one you have.

---

### Post by othelios on 2008-01-28
Here you go
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

---

### Post by othelios on 2008-02-07
Doesn't matter now. Got it fixed :D

Just had to enable one of the restricted drivers for the software modem, or something like that anyway.

---

