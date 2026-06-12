---
title: "no sound"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-10
hey,

I have a built in speaker for my laptop, and that's all the info I have about it. When I run the command  "aplay -l" it says no sound cards found. And as ususal I don't have any sound. So some help would be really appreciated. 

So thanks a lot in advance....

---

### Post by FuturePilot on 2007-11-10
Could you post the output of ```
lspci -v
```

---

### Post by limac on 2007-11-11
This is what it says for "lspci -v"

limac@Apple-Macintosh:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000068000000-000000006bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 68000000-6bfff000 (prefetchable)
        Memory window 1: 6c000000-6ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

limac@Apple-Macintosh:~$

---

### Post by jingo811 on 2007-11-11
I followed this guide when I had sound problems.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Pumalite on 2007-11-11
Try this:

[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

---

### Post by limac on 2007-11-11
Thnks for those links. That's exactly what I was pleading!

---

### Post by Pumalite on 2007-11-11
You are welcome. Good luck.

---

