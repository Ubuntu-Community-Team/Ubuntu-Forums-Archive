---
title: "Anything different when running dapper drake on a laptop?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-11-28
This should be brief, I haven't bought a laptop yet so its scary that I could waste over $1000. Are there any differences with laptops? Because they use different technology, I'm mainly worried about the refresh rate. I've got that fixed on my desktop but with a laptop I don't know if the monitor has its own menu button. With my desktop I proved it was running at 61htz because I checked the monitors menu, otherwise I have to trust that the os is telling the truth... which isn't too accurate. And if the screen dies fast then the laptop is almost useless since the monitor is fixed on ](*,) 

I'll cut it short: Questions...

- Do monitors on laptops have their own menu button?
- If the answer to the above question is yes, then please provide a make & model that has reported a 60htz refresh rate or whatever the optimal refresh rate is (bonus points if its dell!)
- Any whack stuff that doesn't happen with desktops?

- Thanks... I'm just a tiny bit paranoid :)

---

### Post by NikoC on 2006-11-28
I have a sony vaio vgn-s4hp myself (widescreen) and I have no trouble at all with refresh rates or screen resolution when running Ubuntu (all autodetected). Hibernate and Suspend do not work though and neither do a 'normal' (by which I mean not pushing the power button for 10s) shutdown or reboot.

---

### Post by redDEADresolve on 2006-11-28
The new AMD powered dells have been working well for me and others, i got one for less then 700 and love it. A little work is needed to install Ubuntu but everything is easy from there.

Screen Resolution, monitor all work well and with the new ATI driver installed the refresh rate is a nice clean 60

[http://ubuntuforums.org/showthread.php?t=299929&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=299929&highlight=dell+1501)

---

### Post by PartisanEntity on 2006-11-28
Dapper is running fine and stable on my Asus laptop (it has an AMD Turion processor).

As far as I know laptop screens do not have their own menus (at least mine doesn't). And LCD's don't have refresh-rates (or configurable one's). Someone correct me if I am wrong. 

There shouldn't be any problems running Dapper on a laptop, my brother managed to install it on his Acer which also as an AMD, Athlon I think it was.

---

### Post by bodhi.zazen on 2006-11-28
I do not have much experience with laptops.

The only problem I have had is with the monitor, although I understand wireless can be problematic as well.

All the monitor needed was manual configuration of xorg.conf (adding refresh rates and such).

I have no advice wireless.

Is there away for you to drive one with a live CD before you buy?

And you should be eligible for a "Rebate" if you purchase with no OS

HTH

---

### Post by kpkeerthi on 2006-11-28
I'm running Dapper Drake on my Dell XPS M170 for over six months. My 1920x1200 screen was detected out-of-the box including my wireless, SD card reader, bluetooth, Audigy 2 ZX PCMCIA sound card etc. As for the refresh rate, do not worry about it if your are going to use a laptop as LCDs don't 'refresh'.

---

### Post by burwaco on 2006-11-28
Medion MD95400

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Seems to work rather well after some tweaks, but I'mjust a beginner...

---

