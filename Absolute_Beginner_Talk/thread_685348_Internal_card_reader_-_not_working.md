---
title: "Internal card reader - not working"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by itsashame on 2008-02-02
Hi,

Any ideas? 

Fujitsu Siemens M1420, Kubuntu 7.1

lspci - output as follows....

Thanks in advance!


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/
O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP
 Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Co
ntroller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (re                                        v 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 0                                        3)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Cont                                        roller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH                                        4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Mode                                        m Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9                                        600 M10]
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec                                        tion (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139                                        C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01                                        )
02:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (                                        rev 80)

---

### Post by candtalan on 2008-02-03
Not sure if this is your problem but hope it helps in some way.
What cards does it take? Have you tried different card types, and also smaller sizes?
I found that an older (externel usb) card multi reader ignored the larger SD cards but was ok with small ones, and also ok with CF cards. More recent reader I bought is ok with large SD cards too. I think a spec changed at least with SD cards, for larger sizes.

---

### Post by itsashame on 2008-02-04
Unfortunately it seems dead to all cards. The light on the front of my laptop that illuminates when a card is inserted when I boot in windows, shows no sign of life at all in Kubuntu.

I'm wondering if it needs a driver - probably there isn't one for this type of card reader?

Cheers.

---

### Post by SneakPeak on 2008-02-04
I have a similar problem with an external reader.

Sometimes it works and sometimes it doesn't.  Sometimes if I insert a smaller CF card (250MB) while a larger SD card (1Gig) is already inserted it suddenly picks up both.  Sometimes it doesn't pick up either.

The lights (power and card present) come on and stay on for a while and then go out.  I guess if there is no action on a USB port the power drops away???

Cheers

Sneak Peak

---

### Post by SneakPeak on 2008-02-04
I seem to have found a way to get the reader to work consistently if not properly.  When I plug it into a USB port that XP warns me is slow it seems to work provided I plug in the small (256MB) card first.

I guess the port is a USB 1 as apposed to a USB 2 port.  Anyway it works even if it is a little slow.

Sneak Peak

---

### Post by smurphy_it on 2008-02-04
itsashame, What type of card are you trying to read ?

If for example, it is some kind of Sony Memory Stick, it probably won't read it at all (not without a kernel / driver hack) last I heard.  Thus it wouldn't illuminate the LED either.

---

