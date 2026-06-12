---
title: "No sound from laptop with Ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-01-20
Hi

I have just installed Ubuntu 6.10 with dualboot. It works :D

But now I have no sound from my laptop. I have tried to set the sound volume in many ways, but no sound is comming.

I've got an Acer Aspire 3680. Dunno which sound card :S

Is there any way to find out, how I got sound back - maybe a program or driver?

---

### Post by ComplexNumber on 2007-01-20
[this ]("http://ubuntuforums.org/showthread.php?t=205449")may help. let us know how you get on.

---

### Post by Wikzo on 2007-01-20
Thanks, but can't get it working. I have typed aplay -l and set all the bars to maximum, but it doesn't work.
> 
wikzo@wikzo-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wikzo@wikzo-laptop:~$ alsamixer

wikzo@wikzo-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 32000000-320fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 58
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031f00000
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at 32000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>

0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. TravelMate 2410
        Flags: bus master, fast devsel, latency 96, IRQ 185
        Memory at d0100000 (32-bit, non-prefetchable) [size=8K]

0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at d0102000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, medium devsel, latency 57, IRQ 201
        Memory at d0103000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>


---

### Post by Wikzo on 2007-01-21
Ok, now I got sounds :D

I just hit the M button in Alsamixer ... some of the things were muted :P

---

