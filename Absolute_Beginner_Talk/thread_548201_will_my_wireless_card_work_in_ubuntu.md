---
title: "will my wireless card work in ubuntu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by buckety on 2007-09-11
hi there,

I currently run Mepis 2.6.12 on an IBM Thinkpad T23. I want to switch to Ubuntu, but I am concerned I won't be able to get my wireless card to work. I have long since lost the install disk that came with the card. In a previous post, someone suggested I run
 
lspci -v | less

and post the results here, so as to aid in the figuring out of what kind of card I have, and whether I will be able to get it to work on Ubuntu:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 0
2)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-ebffffff

0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
 (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
 (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series


Does anyone draw a conclusion from this info? I have no idea what to make of it. 

Thanks!
Buckety

---

### Post by wolfen69 on 2007-09-11
you should have no problem. intel wireless is pretty good in ubuntu. i know a couple people with similar chipdets. you can always try the live cd and test it.

---

### Post by Chris S. on 2007-09-11
I think there should be more to that output.  When you pipe the output to "less" like that, it makes the output easy to scroll, but you only see part of it at a time.  To see what I mean, retype that command, and then press the down arrow or the enter key.  You'll now be scrolling down through the output.

Instead, just type "lspci -v" and copy and paste everything here.

---

### Post by buckety on 2007-09-11
o.k. here it is:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-ebffffff

0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
        I/O behind bridge: 00002000-00006fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 1860 [size=16]
        Memory at 10000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
        Subsystem: IBM ThinkPad T23 (2647-4MG) or A30/A30p (2652/2653)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]

0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0100000 (32-bit, non-prefetchable) [size=512K]
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <available only to root>

0000:02:00.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:00.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 51000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: AMBIT Microsystem Corp. IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 6440 [size=8]
        I/O ports at 6000 [size=256]
        Capabilities: <available only to root>

0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 6400 [size=64]
        Capabilities: <available only to root>

0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Motorola WN825G
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at 10800000 (32-bit, non-prefetchable) [size=8K]

---

### Post by jamieh on 2007-09-11
This is why we have ndiswrapper (ndisgtk for noobs)

---

