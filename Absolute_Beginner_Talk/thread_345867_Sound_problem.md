---
title: "Sound problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by raharris on 2007-01-24
I'm using a Dell Inspiron 700m with a intel 82801DB-ICH4 sound card.  No problem hearing sound through the headphones but I get nothing from the speakers.  I've been through ALSA, have unchecked everything and placed all the center (read that somewhere) and have unchecked external amplifier (read that somewhere else) but no luck.  Any ideas?  Thanks, RAH

---

### Post by McLogic on 2007-01-26
I think we would need to know what version of Ubuntu you are using. I'm using 6.06 and the headphones are assigned to Headphone, and the Speakers are assigned to Master. They can have their volumes changed independantly, and that is really nice for not blowing out your ears when you plug in your headphones.

It can be really loud when you find the right solution, but I put the sliders all UP all the way (not middle) as sound can pass through a few of the values before it gets to the speakers.

The 700m has noisy sound, as they didn't clean the 5v going into the sound system. This is a real problem when using the Mic. It was one of the main reasons that Dell started making the 710m.
[http://www.jumboprawn.net/jesse/projs/inspiron_700m_mic/index.html](http://www.jumboprawn.net/jesse/projs/inspiron_700m_mic/index.html)

I'll use my 700m until it dies, as it rocks: 1280x800 screen, 11", 4.5 hours batt, 5 lb. 
Saddly, Dell no longer makes a 700/710-like computer.

---

### Post by dannyboy79 on 2007-01-26
have you read thru the sound solution thread. I got my laptop working using that. it has something to do with making sure the correct module is loading, whether you sound card is seen by ubuntu etc etc. what does your lspci -v look like?

---

### Post by raharris on 2007-01-27
Hi -- I'm not clear where the sound card thread is but I'll look for it.  Here is my lspci -v  
if that helps --

thanks in advance -- RAH

0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: [40] #09 [8105]

0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: [d0] Power Management version 1

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Dell: Unknown device 018d
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff
        Prefetchable memory behind bridge: 50000000-53ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 54000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Dell: Unknown device 018d
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: [50] Power Management version 2

0000:02:01.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
        Subsystem: Intel Corporation: Unknown device 1020
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0206000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

0000:02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0209000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 56000000-57fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e020a000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 52000000-53fff000 (prefetchable)
        Memory window 1: 58000000-59fff000
        I/O window 0: 00003800-000038ff
        I/O window 1: 00003c00-00003cff
        16-bit legacy interface ports at 0001

0000:02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0208000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:02:04.3 Mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
        Subsystem: Dell: Unknown device 018d
        Flags: medium devsel, IRQ 10
        Memory at e0207000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: [44] Power Management version 2

0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, fast devsel, latency 32, IRQ 10
        Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

---

### Post by raharris on 2007-01-27
I'm using Dapper Drake, 6.06.  I can see the seperate volume bars for master and headphone, and they w=are both set to the middle.

thanks, RAH

---

### Post by dannyboy79 on 2007-01-27
heres the link to the comprehensive sound trouble shooting guide.
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

