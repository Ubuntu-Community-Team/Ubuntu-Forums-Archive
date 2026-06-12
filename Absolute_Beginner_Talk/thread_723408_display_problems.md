---
title: "display problems"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by cookbooking it on 2008-03-13
I'm enjoying my new Ubuntu desktop except for a few problems, which I'll post separately.
When I tried the Kubuntu live cd, I got lines across the screen, like vector lines connecting the corner of my screen with points in the desktop. There were additional lines, also, and the window images would not completely disappear after closing the windows. Scrolling the mouse over it would sometimes help it disappear. Also, sometimes the display slips out of place (right side of desktop on the left, bottom edge on the top, etc. like off-center tiled images), and I have to use the mouse to drag it back. I hoped that installing to the hard drive would solve these problems, but it didn't. I later installed ubuntu-desktop and found these display problems almost eliminated under gnome. They still show up quite a bit when using kde and with some applications on the gnome desktop.
I used the 64bit Kubuntu live cd for the initial install. My hardware stats are in my signature line. The onboard chipset is SIS 760/964.
Thanks!

---

### Post by handydan918 on 2008-03-14
This could easily be a video driver issue. If you open a terminal and do ```
lspci
``` and then copy and paste the output back here, someone can tell what your video hardware is, and recommend a fix.

---

### Post by cookbooking it on 2008-03-14
Thanks! I hope this tells you something helpful.

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by cookbooking it on 2008-03-15
While waiting for someone to get back to me, I went into system > administration > screens and graphics, and tried all the sis drivers, the generic vga driver, and the generic vesa driver. They all tested poorly - either a snowy screen or a black one. I also checked the sis support page looking for a driver, but didn't find one.
Does this mean my hardware won't work right under Linux? Or does someone know of a solution besides installing another video card? If I do that, will I need to disable the onboard graphics? If so, how?
Any help would be appreciated.

---

