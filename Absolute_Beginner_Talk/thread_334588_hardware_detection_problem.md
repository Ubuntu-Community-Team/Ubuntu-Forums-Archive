---
title: "hardware detection problem"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by dbbd8 on 2007-01-09
I have moved my SATA controller to a different PCI slot on the motherboard, and now
6.10 does not detect my SATA drives.

Here is what I believe are the relevant lines from the dmesg log - note the "Cannot allocate resource region" which I believe causes the problems.

> 
[42949374.630000] ACPI: bus type pci registered
[42949374.650000] PCI: PCI BIOS revision 2.10 entry at 0xfb160, last bus=2
[42949374.650000] PCI: Using configuration type 1
[42949374.650000] Setting up standard PCI resources
[42949374.660000] ACPI: Interpreter enabled
[42949374.660000] ACPI: Using PIC for interrupt routing
[42949374.660000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949374.660000] PCI: Probing PCI hardware (bus 00)
[42949374.660000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[42949374.660000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[42949374.660000] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
[42949374.660000] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[42949374.660000] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[42949374.660000] Boot video device is 0000:01:00.0
[42949374.670000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949374.700000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[42949374.700000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[42949374.700000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[42949374.700000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[42949374.710000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949374.710000] pnp: PnP ACPI init
[42949374.710000] pnp: PnP ACPI: found 11 devices
[42949374.710000] PnPBIOS: Disabled by ACPI PNP
[42949374.710000] PCI: Using ACPI for IRQ routing
[42949374.710000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949374.710000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[42949374.710000] PCI: Cannot allocate resource region 1 of device 0000:02:04.0
[42949374.710000] PCI: Cannot allocate resource region 1 of device 0000:02:05.0
[42949374.710000] PCI: Cannot allocate resource region 1 of device 0000:02:06.0
[42949374.710000] PCI: Cannot allocate resource region 1 of device 0000:02:07.0
[42949374.730000] PCI: Bridge: 0000:00:01.0
[42949374.730000]   IO window: disabled.
[42949374.730000]   MEM window: d9000000-db0fffff
[42949374.730000]   PREFETCH window: d4000000-d5ffffff
[42949374.730000] PCI: Bridge: 0000:00:07.0
[42949374.730000]   IO window: 9000-9fff
[42949374.730000]   MEM window: 20000000-200fffff
[42949374.730000]   PREFETCH window: 20100000-201fffff
[42949374.730000] PCI: Setting latency timer of device 0000:00:01.0 to 64


Also, here is my lspci -v output:
> 
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 02)
        Flags: bus master, medium devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 2.0
        Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d9000000-db0fffff
        Prefetchable memory behind bridge: d4000000-d5ffffff

00:03.0 Class 0080: Silicon Image, Inc. Unknown device 3412 (rev 01)
        Subsystem: Silicon Image, Inc. Unknown device 3412
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        I/O ports at b000 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at a400 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at ac00 [size=16]
        Memory at d8000000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 20200000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2

00:07.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: 20000000-200fffff
        Prefetchable memory behind bridge: 0000000020100000-0000000020100000
        Capabilities: [dc] Power Management version 1

00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
        Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0

00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at b400 [size=16]
        Capabilities: [c0] Power Management version 2

00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at b800 [size=32]
        Capabilities: [80] Power Management version 2

00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at bc00 [size=32]
        Capabilities: [80] Power Management version 2

00:14.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
        Flags: medium devsel, IRQ 3
        Capabilities: [68] Power Management version 2

00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 8905
        Flags: medium devsel, IRQ 10
        I/O ports at c000 [size=256]
        I/O ports at c400 [size=4]
        I/O ports at c800 [size=4]
        Capabilities: [c0] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d9000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d4000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at da000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 1
        Capabilities: [44] AGP version 2.0

02:04.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
        Subsystem: D-Link System Inc DFE-570TX Quad Fast Ethernet
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9000 [size=128]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 20100000 [disabled] [size=256K]

02:05.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
        Subsystem: D-Link System Inc DFE-570TX Quad Fast Ethernet
        Flags: bus master, medium devsel, latency 32, IRQ 12
        I/O ports at 9400 [size=128]
        Memory at 20000400 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 20140000 [disabled] [size=256K]

02:06.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
        Subsystem: D-Link System Inc DFE-570TX Quad Fast Ethernet
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 9800 [size=128]
        Memory at 20000800 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 20180000 [disabled] [size=256K]

02:07.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
        Subsystem: D-Link System Inc DFE-570TX Quad Fast Ethernet
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at 9c00 [size=128]
        Memory at 20000c00 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 201c0000 [disabled] [size=256K]


Any ideas what might be the problem, or better yet, how do I fix it?

Dan

---

### Post by hal10000 on 2007-01-09
Maybe you have a chance to get it work, if you add pci=routeirq to to the boot prompt. 
If it works, then add this option to your grub kernel line.

---

### Post by dbbd8 on 2007-01-09
I tried adding that, but no, it didn't help.
Actually ths situation got only worse - apparently that resource problem happened
only when the BIOS does not recognize the SATA card properly.

I tried switching the card to another port, it is now recognized by the BIOS as "MASS storage controller" but then the BIOS fails to boot - it looks like it does not even try to access the IDE
bus (not CDROM nor HD, when the card is identified properly - so I guess this is not an Ubuntu issue but rather a hardware one.

Dan

---

### Post by hal10000 on 2007-01-09
There's another boot option you might want to try: [COLOR="Red"]pci=noapic[/COLOR] (maybe it's just called [COLOR="Red"]noapic [/COLOR] instead of pci=noapic)
Try it alone and together with the pci=routeirq option.

On some mainboards you can disable APIC in your BIOS too.

---

### Post by Modernity on 2007-01-09
Double check the options in BIOS for your boot devices. I am not sure which mobo you have, so double check that first.

---

### Post by dbbd8 on 2007-01-09
Its a FIC AZ11 MB.

I've checked and rechecked the BISO. Boot order, IRQ mapping, everything.

The BIOS does not know about the SATA disks. Only about the SATA controller.
But, when there are SATA disks attached to the controller, its like the IDE has disappeared.

Dan

---

### Post by Modernity on 2007-01-09
Yes, but becareful using SATA and IDE drives together. Why did you move the SATA to a differnt controller?

---

### Post by dbbd8 on 2007-01-09
The motherboard does not support SATA.
I wanted an IDE boot disk, and 2 SATA disks on a PCI controller to be used as a RAID1 network file server (samba).

When I said I moved - I mean I moved the SATA card from one PCI slot to another.
Dan

---

### Post by hal10000 on 2007-01-09
Before you moved the card to another slot, did it work?
If so, then it's usually a irqrouting and/or apic problem.

---

### Post by dbbd8 on 2007-01-09
No, the card is either not recognized by the BIOS as "mass storage" and then ubuntu boots but has the error in the logs above, or it is recognized by the BIOS, and then the IDE disk (or CDROM) won't be accessed for booting - the system hangs after preparing the DMI.

Dan

---

### Post by hal10000 on 2007-01-09
I have no ideas. Maybe you can fiddle something in your BIOS.
Sorry

---

