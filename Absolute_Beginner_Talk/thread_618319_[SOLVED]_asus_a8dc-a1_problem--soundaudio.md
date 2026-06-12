---
title: "[SOLVED] asus a8dc-a1 problem--sound/audio?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by weirdfrog on 2007-11-20
**Solved 12/06/07** 
[I]--compiled and installed 1.0.15rc3 driver and newest libs and utils
--then added "options snd-hda-intel model=lenovo" to modprobe.conf
...which is kinda odd, since it's Asus and -not- a lenovo--but it worked. Speakers and headphones work just fine. Haven't tried my microphones yet.[/I]

---------------------------------------------------------------------------------
Hi folks. I'm hoping to find some direction here. I recently bought an Asus a8dc-a1 laptop.
(AMD Turion 64x2 tl-58 1.9 ghz, 2g ram, nvidia 8400m) I'm on it right now using  7.10 Gutsy.
I've had it for 2 weeks-- and I've been thru every FAQ and sticky...I've cruised thousands of threads and posts here and many other places...but I find myself at a standstill.
I simply cannot get sound to work on this notebook--although it works just fine in Vista. I have followed and further researched many pieces of advice from here--but nothing seems to work. I have a feeling it's just me being stupid, although I would hope not.
I've been  dual booting w/ vista.
NO SOUND at all in ubuntu....what am I missing?
The frequently mentioned alterations to modprobe.d/alsa-base and modprobe/conf have not worked...I have reinstalled, updated, reconfigured, and patched so many times I'm going nuts...and still no sound.
I'm mostly coming from a windows background, although I have experimented with several linux distros on desktops before...but this is my first laptop.
If anyone can help, I'd be very grateful.

aplay -l gives this:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v gives this:

:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at cc00 [size=64]
        I/O ports at 2d00 [size=64]
        I/O ports at 2e00 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f9e7f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f9e7ec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f9e7d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f9e7e800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f9e78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at c480 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c080 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at bc00 [size=16]
        Memory at f9e76000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1686
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f9e7c000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b880 [size=8]
        Memory at f9e7e400 (32-bit, non-prefetchable) [size=256]
        Memory at f9e7e000 (32-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-fd6fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fd700000-fd7fffff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd800000-febfffff
        Prefetchable memory behind bridge: 00000000f6000000-00000000f8ffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at f9fff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

01:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at f9fff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at f9ffec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1687
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at f9ffe800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1513
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at fd6e0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1026
        Flags: fast devsel, IRQ 20
        Memory at fd7f0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
-------------------------------------------------------------
I'm new here, so I apologize if I have posted this incorrectly, or in the wrong place.
Anyone have any ideas?
Once again, my notebook is:

ASUS A8DC-A1 Turion 64x2 tl-58 1.9 ghz  2 gig ram 
video is NVidia 8400m G dedicated 
from newegg.

Thanks to all y'all for everything I've learned here over the last two or three weeks...even if I can't find an answer to my current problem, I certainly have found an excellent place to wander.

-scott.

---

### Post by weirdfrog on 2007-11-20
*bump*

---

### Post by yagaman on 2008-03-06
hi there,
just got a Asus A8DC
Same specs than above regarding the sound caracteristiks...
Want to know if anybody knows if there any drivers avaliable...
Want to here some music...:guitar:

---

