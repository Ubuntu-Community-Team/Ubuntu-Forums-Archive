---
title: "Basic Video Setup question for VIA chipset"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by tlg2007 on 2007-06-03
Hi
I have a MSI motherboard with a VIA chipset P4M890 and 8237A and I am attempting to use Ubuntu 7.04

The integrated video is not recognised as VIA during the install so the vesa driver is used. This gives me a 1024X768 screen resolution which is OK, but the refresh rate is 60Hz which has too much flicker. I would like to set the refresh rate of 72Hz.

I have trawled through many threads and tried lots of different ways to modify the xorg.conf file including:
-  setting the Device Driver line to via instead of vesa - this results in X not starting
-  setting modelines from the online modeline generator  for 1024x768 72Hz - this seems to be ignored.

So I have two questions - 
1. Is it possible to make the basic vesa driver refresh at more than 60Hz?

2. Has anyone successfully got Ubuntu to work with this chipset and recognised the video properly?

Many thanks in advance for any help.

---

### Post by overdrank on 2007-06-03
> **tlg2007 said:**
> Hi
I have a MSI motherboard with a VIA chipset P4M890 and 8237A and I am attempting to use Ubuntu 7.04

The integrated video is not recognised as VIA during the install so the vesa driver is used. This gives me a 1024X768 screen resolution which is OK, but the refresh rate is 60Hz which has too much flicker. I would like to set the refresh rate of 72Hz.

I have trawled through many threads and tried lots of different ways to modify the xorg.conf file including:
-  setting the Device Driver line to via instead of vesa - this results in X not starting
-  setting modelines from the online modeline generator  for 1024x768 72Hz - this seems to be ignored.

So I have two questions - 
1. Is it possible to make the basic vesa driver refresh at more than 60Hz?

2. Has anyone successfully got Ubuntu to work with this chipset and recognised the video properly?

Many thanks in advance for any help.

Hi and welcome could you post the output of the command _lspci _ in the terminal located under applications, accessories. Thanks

---

### Post by tlg2007 on 2007-06-03
Hi
Here is the lspci output:

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3343 (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

