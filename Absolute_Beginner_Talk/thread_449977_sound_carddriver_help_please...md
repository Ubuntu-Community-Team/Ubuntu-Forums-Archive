---
title: "sound card/driver help please.."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by lexod on 2007-05-20
Hi All,

I will be the first to say that I am a complete noob.  I'm running Feisty on a pcg-tr2a sony laptop.  The problem I am having is that I cannot get the sound to work.  I've searched for a few hours unsuccessfully to try and find a previous solution post but can't find anything.  It may because I don't know EXACTLY how to word the technical problem that I am having.  To put it in the most simple terms...my sound doesn't work and I don't know why.  Any help would be appreciated, thanks guys.

---

### Post by overdrank on 2007-05-20
> **lexod said:**
> Hi All,

I will be the first to say that I am a complete noob.  I'm running Feisty on a pcg-tr2a sony laptop.  The problem I am having is that I cannot get the sound to work.  I've searched for a few hours unsuccessfully to try and find a previous solution post but can't find anything.  It may because I don't know EXACTLY how to word the technical problem that I am having.  To put it in the most simple terms...my sound doesn't work and I don't know why.  Any help would be appreciated, thanks guys.

Hi can you post the output of this command in the terminal, lspci. Terminal is located in applications,accessories. :popcorn:

---

### Post by lexod on 2007-05-20
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
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
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by overdrank on 2007-05-20
> **lexod said:**
> Hi All,

I will be the first to say that I am a complete noob.  I'm running Feisty on a pcg-tr2a sony laptop.  The problem I am having is that I cannot get the sound to work.  I've searched for a few hours unsuccessfully to try and find a previous solution post but can't find anything.  It may because I don't know EXACTLY how to word the technical problem that I am having.  To put it in the most simple terms...my sound doesn't work and I don't know why.  Any help would be appreciated, thanks guys.

Hi the best I can find for that card is this link
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
Hope this helps good Luck!:p

---

