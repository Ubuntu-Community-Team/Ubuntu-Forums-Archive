---
title: "No Sound Dell Ispirion 1420"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Adolphian on 2008-02-29
I bought my computer from dell, so they were nice enough to install and get all my crap working for me before i opened them damn thing, so not only am i new to ubuntu, i didn't install any of my drivers and im a total newb with terminal as well.  anyways, everything was working fine till tonight.

tonight my internet froze up and i turned my computer on and off to fix this of course. and when i turned my computer back on... the sound doesnt work. ive turned it off and on about 10 times, and its still dead.  i plug headphones into the jack and still nothing.

HELP ME!!!


SOLUTION:

first i right clicked on the sound icon near the date and opened the volume control  from here i simply clicked file, and changed the device.  OSS works for my computer, hopefully this will help other people.

---

### Post by FuturePilot on 2008-02-29
I take it the sound was working before it froze, correct?
Post the output of
```
lspci
```
so we know what sound card you have.

---

### Post by Adolphian on 2008-02-29
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


yes it was working..... now its dead.

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Adolphian on 2008-02-29
ok, now i just wanna break down and cry. lol.

my rhythm musicbox works.

my vlc player doesnt, and my computer doesnt make the log on noises anymore either.  

*dies*

new idea?

the oss music thing worked btw, but int he article it talks about "CS46XX"  and i didn't see that option.  do i have an older version of something?  maybe this could help me?

EDIT: there is no sound online either. youtube only will play video

---

### Post by Adolphian on 2008-02-29
w00t, im awesome. fixed it myself.

---

