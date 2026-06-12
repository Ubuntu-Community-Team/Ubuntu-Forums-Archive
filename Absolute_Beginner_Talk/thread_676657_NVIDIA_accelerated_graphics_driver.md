---
title: "NVIDIA accelerated graphics driver"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by marenum on 2008-01-24
I'm brand new to ubuntu.

That being said, I'm using a gateway pc from late 2002 and the hardware isn't very good. When I have the NVIDIA accelerated graphics driver from the restricted drivers menu in use,  no text shows up in the terminal. I sometimes loose menu bars as well. Everything seems fine when I turn this driver off. I don't know what graphics card i have, but I'm sure it isn't very good, is that my problem? any suggestions?

---

### Post by kpkeerthi on 2008-01-24
May be you need "legacy" driver. To confirm, open a terminal and type ```
lspci
``` and post the output here.

---

### Post by marenum on 2008-01-24
marenum@marenumNET:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

---

