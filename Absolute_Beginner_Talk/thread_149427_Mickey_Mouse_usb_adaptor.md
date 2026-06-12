---
title: "Mickey Mouse usb adaptor??"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-03-23
I've been trying to find a driver for my inventel usb wireless adaptor but I can't find inventel listed in any of the resources posted on these forums. Does it come under another name? I can't find the chipset either when I run lspci -v I get:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 10000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: medium devsel, IRQ 5
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: medium devsel, IRQ 5
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 3000 [size=256]
        Memory at e0200000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 3084
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 10001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

There's no chipset there is there? I'd really appreciate any help, I'm going to conquer this... I think :-?

---

