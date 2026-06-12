---
title: "No sound on IBM T41"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by swoopdk on 2007-04-28
Hi

I'm new to Ubuntu - just installed it yesterday.

There were no problems to install Ubuntu but somehow I don't have any sound now. At the first boot (and perhaps the second too) I had sound on but now it's gone.
It's a bit strange but now I don't have any sound on my Windows XP too (I'm using dual boot option).

Any ideas where to look? I have only updated to latest packages - no configuration changes.
It's my pc for work and I love to have some music on when I work. The PC is an IBM T41 laptop.

Thanks for your help.
Allan

---

### Post by swoopdk on 2007-04-28
Some more input.

I've been reading a bit on this  this help page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
Since it's a laptop I guess my soundcard is onboard? I can't find any places in my BIOS to turn on/off my onboard soundcard.

'aplay -l' shows:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

'lspci -v' shows:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: IBM Unknown device 0529
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=168
        I/O behind bridge: 00004000-00008fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1860 [size=16]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Unknown device 0537
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: IBM Unknown device 0525
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0531
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: e8000000-ebfff000 (prefetchable)
        Memory window 1: c4000000-c7fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: ec000000-effff000 (prefetchable)
        Memory window 1: c8000000-cbfff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
        Subsystem: IBM PRO/1000 MT Mobile Connection
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0220000 (32-bit, non-prefetchable) [size=128K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 8000 [size=64]
        [virtual] Expansion ROM at c0240000 [disabled] [size=64K]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Unknown device 17ab:8331
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at c0210000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by moeFinley on 2007-06-06
Ditto :)

I've just bought a T41 from eBay.  I installed Fiesty and I'm sure I had sound to start with??  Now the only sound I can get is a weird crackling beep when I push the volume buttons.

I've fixed some sound issues on other machines so I'm going to have a look into it and I'll post any findings.

Fingers crossed ;)

---

### Post by webjames on 2007-07-20
Hi Thinkpadders,
I've just bought a T41 of ebay should be coming today/tomorrow i'll post what happens to my sound with a feisty install; but if someone is looking at this thread and knows the answer feel free to save me the hassle.
Best wishes, 

James

---

### Post by zeta on 2007-07-20
Hi Allan, 
I had the same problems on my T42 with the upgrade to Feisty. I tried and tweaked a lot to get it work - and it finaly did (9 out of 10 times)  - but I honestly don`t know why. A quick hibernate usually works for my system when it gets quit again. Other than that, I suggest you make sure you have all the updates. Or you switch to Edgy or Dapper. :confused:

---

### Post by moeFinley on 2007-07-21
It seems that the audio goes when the laptop is put into hibernation.  Is this what everyone is experiencing?

---

