---
title: "apache php mysql on ubuntu"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by nicolino101 on 2007-03-09
Hi,
  I'm new to this forum and ubuntu and linux. How do I install a lamp stack on ubuntu when I don't have internet. I also do not have 'make'. You see, I can't get my wireless card working on linux  so I can't use apt-get install, right?
Please help!
                     Nicolino101

---

### Post by halitech on 2007-03-09
I would recommend getting your wireless working first before worrying about LAMP. do you know the make/model of your card?

---

### Post by nicolino101 on 2007-03-09
belkin  wireless g f5d7010
works on win 2000 pro

---

### Post by nicolino101 on 2007-03-09
I would love to get this wireless working on my notebook, but after 6 hours of screwing around with it and finding no good news, I thought I would put it off and try to work on the lamp stack.
That's really the only reason for linux for me.
Everything that I've read about this IBM Notebook in combo with the belkin wireless card and ubuntu says that it won't work.

---

### Post by halitech on 2007-03-09
looks like it will depend on what version of the firmware and chipsets you have, some work good, others don't at all.

open a terminal and type in

```

sudo lspci 

```

and see if it even sees  your card

---

### Post by nicolino101 on 2007-03-09
I have to restart. Ubuntu is on another partition. Dual boot.

---

### Post by invalid on 2007-03-09
> **nicolino101 said:**
> How do I install a lamp stack on ubuntu when I don't have internet.

You can follow the following guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Simply download the packages on an internet connected machine, and transfer them over. If you can fix the wireless, however, it would be a lot easier.

---

### Post by nicolino101 on 2007-03-09
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f0000000-f7ffffff
        Prefetchable memory behind bridge: 28000000-280fffff

0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM Thinkpad T20
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM Thinkpad T20
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
        Subsystem: Intel Corporation EtherExpress PRO/100 SP Mobile Combo Adapter
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at e8120000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1800 [size=64]
        Memory at e8100000 (32-bit, non-prefetchable) [size=128K]
        Expansion ROM at 28100000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2

0000:00:03.1 Serial controller: Agere Systems LT WinModem (rev 01) (prog-if 00 [8250])
        Subsystem: Intel Corporation: Unknown device 2205
        Flags: medium devsel, IRQ 11
        I/O ports at 1840 [size=8]
        Memory at e8121000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM: Unknown device 0153
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at e8122000 (32-bit, non-prefetchable) [size=4K]
        Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2

0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
:

---

### Post by nicolino101 on 2007-03-10
that was what the response was from ubuntu. Apparently, ubuntu recognizes my wireless card, but still no drivers for it.
By the way, thank you for the help.

---

### Post by halitech on 2007-03-10
when you boot, do you have any errors related to hotplug?

---

### Post by nicolino101 on 2007-03-10
no errors

---

### Post by halitech on 2007-03-10
from what I can find, it should work using the e100 module which is included in the 2.6 kernel

can't find any info on how to get it to work though. hopefully someone else will have an idea

---

### Post by nicolino101 on 2007-03-10
sorry, no errors. I thought I already replied.

---

### Post by nicolino101 on 2007-03-10
Well at least that's not bad news! I really have no clue how that would work, but I'm looking.

---

### Post by halitech on 2007-03-10
I think my brain went to sleep, considering it 1:38am for me, no surprise. good luck and I'll check tomorow and se if there was any progress

---

### Post by nicolino101 on 2007-03-10
thanks again... good night.

---

