---
title: "card reader is not working"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by kensou on 2007-05-08
Recently I install Feisty on my laptop. compaq presario v3018tu. problem is my integrated card reader is not working.any suggestion in this regard would be of great help.

the output of "lspci -v" is

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d2000000-d3ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: d4000000-d40fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d4544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d4100000-d41fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d4544400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 66, IRQ 22
        Memory at d4100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d4101000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at d4101800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at d4101c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        Memory at d4102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        Memory at d4102400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by mthakur2006 on 2007-05-08
try inserting a card and then rebooting the machine, i've heard it works. card readers are somewhat unsupported on linux, quite contrary to what common sense tells you, and I know this all too well as I suffer from it as well:popcorn:

---

### Post by az_s_za on 2007-05-08
You need to look [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=420721")

---

