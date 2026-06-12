---
title: "lspci"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by ism. on 2008-04-20
hey all!  i have a question.  When i use the command lspci i get the following results 


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)


i was wondering why my network controller doesn't show up like it does for the other people who have posted these results like in this example 

> 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

or is it there listed under something different and im missing it:confused:.....


Thanks

-ism.

---

### Post by wolfen69 on 2008-04-20
> 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
those are 2 of yours right there. ethernet controller and network controller are the same thing.

---

### Post by SOULRiDER on 2008-04-20
> 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
there you go. the broadcome one is your wireless device.

---

### Post by ism. on 2008-04-20
ok so if im trying to see if my network card is capatible i see if the Atheros card is on the list?

---

### Post by joshrobinson on 2008-04-20
> **ism. said:**
> ok so if im trying to see if my network card is capatible i see if the Atheros card is on the list?

correct, even if it isnt supported, do a search or 2 around these forums, you should find a howto on getting it up and running

---

### Post by ism. on 2008-04-20
ok thankyou very much

---

### Post by jimrz on 2008-04-20
> **ism. said:**
> 
00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol 


this is your wifi card. the atheros 5212 is supported "out of the box" in ubuntu. I have 2 of them and both work as well as they did using windows.

---

