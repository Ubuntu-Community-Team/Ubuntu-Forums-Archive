---
title: "Wireless card not working in Ubuntu - Feisty"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by mabersold on 2007-05-05
System:  Dell Inspiron 1100 laptop
Wireless card:  D-Link Air DWL-650

Simply put, Ubuntu does not give me an option to use my wireless card.  When I look at Network settings, it only lists the wired connection and modem connection.  The "Link" light on my card never turns on when i have it plugged in.

I have confirmed that it does, in fact, record the event of the wireless card being plugged into and out of the PCMCIA slot.  The text from the log message is the following:

May  5 19:59:54 Paiway kernel: [ 9303.507553] pccard: PCMCIA card inserted into slot 0
May  5 19:59:54 Paiway kernel: [ 9303.507933] pcmcia: registering new device pcmcia0.0

It stops there after I plug it in.

Here's the output of what happens when I run lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

Output when I run iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

I can't figure out what to do to get it running, so I'd appreciate some help.  If there's any more information that's needed, please let me know.

---

### Post by e_james on 2007-05-06
I don't know enough about linux hardware issues to give you detailed advice but I just did a search of the hardware forum for "DWL-650" and it looks like many people have been there before you. If you try the same search you will probably find enough information to fix your problem. I think it's an "ndiswrapper" solution.

---

