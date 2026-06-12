---
title: "xorg basics"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by scott_b on 2007-03-14
I need an explanation of video cards and xorg.  

I know that I can do an lspci to figure out what card I have.  When I do it, I get the following: 

> 00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller 
(rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
  

I also know that if gdm doesn't start, then I can run 
> sudo dpkg-reconfigure -phigh xserver-xorg

But what I don't understand is why my laptop only runs when I select vesa on that first screen.  How on earth do I figure that out besides trial and error?

Furthermore, why does the splash screen work but gdm doesn't?  If it can run the splash, surely it can run the gui, right?

---

### Post by Brunellus on 2007-03-14
the clue to the labyrinth is the ATI Radeon Mobility card (it's in your lspci output).  

When Ubuntu attempts to set up xorg on first boot, it will go for the free-software driver for ATI Radeon hardware (can't remember the name off the top of my head). . . but that's a flaky driver at best, and not compatible with all ATI cards.  Presumably, it doesn't work for you.

Thus, Xorg fails until you point it to the VESA driver, which is the bare-minimum 'safe' mode for X.  

The splash screen and Xorg are displayed differently.  It's thus possible for one to work and not the other.  I'm not too up on the fine technical details here, though.

Remember:  all that glitters is not gold.  Pretty colors do not necessarily mean Xorg. . .

---

