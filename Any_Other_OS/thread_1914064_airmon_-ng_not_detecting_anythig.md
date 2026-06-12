---
title: "airmon -ng not detecting anythig"
date: 2012-01-23
forum: Any Other OS
---

### Post by mrughindersingh on 2012-01-23
hello 
im using a dell xps 15 l502x laptop with win 7 x64 home premium.I have installed vmware workstation 8 and created a virtual machine for Backtrack 5R1 gnome..i am having trouble with the wireless card.
when i run command airmon-ng it does not shows anything other than this:->
```
Interface	Chipset		Driver
```
The wireless is built in Intel Centrino wireless N-1030.
i downloaded some drivers from the intel site:
[url*[I]**]http://www.intellinuxwireless.org/?n=Downloads***[/I][/url]
(find 1030 ther is only 1..i downloaded that)
but i am not able to install them(not able to find how to install stuff)

here are outputs of some commands that might help u guys figure my problem:

1)
```
**root@bt:~# lspci**

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB Controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware USB2 EHCI Controller

```

2)
```
root@bt:~# lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
	Subsystem: VMware Device 1976
	Flags: bus master, medium devsel, latency 0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
	Subsystem: VMware Device 1976
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: VMware Device 1976
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 10c0 [size=16]
	Kernel driver in use: ata_piix

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
	Subsystem: VMware Device 1976
	Flags: medium devsel, IRQ 9
	Kernel modules: i2c-piix4

00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
	Subsystem: VMware Virtual Machine Communication Interface
	Flags: medium devsel, IRQ 9
	I/O ports at 1080 [size=64]
	Memory at c8000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [58] MSI-X: Enable- Mask- TabSize=2

00:0f.0 VGA compatible controller: VMware SVGA II Adapter
	Subsystem: VMware SVGA II Adapter
	Flags: medium devsel, IRQ 9
	I/O ports at 10d0 [size=16]
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at c8800000 (32-bit, non-prefetchable) [size=8M]
	[virtual] Expansion ROM at c0000000 [disabled] [size=32K]
	Capabilities: [40] Vendor Specific Information <?>

00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
	Subsystem: VMware Device 1976
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 1400 [size=256]
	Memory at c8040000 (64-bit, non-prefetchable) [size=128K]
	Memory at c8020000 (64-bit, non-prefetchable) [size=128K]
	[virtual] Expansion ROM at c0008000 [disabled] [size=16K]
	Kernel driver in use: mptspi
	Kernel modules: mptspi

00:11.0 PCI bridge: VMware PCI bridge (rev 02) (prog-if 01)
	Flags: bus master, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=68
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: c9000000-ca3fffff
	Prefetchable memory behind bridge: 00000000d8400000-00000000d89fffff
	Capabilities: [40] Subsystem: VMware PCI bridge

00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: ca400000-ca4fffff
	Prefetchable memory behind bridge: 00000000d8a00000-00000000d8afffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: ca800000-ca8fffff
	Prefetchable memory behind bridge: 00000000d8e00000-00000000d8efffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: cac00000-cacfffff
	Prefetchable memory behind bridge: 00000000d9200000-00000000d92fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: cb000000-cb0fffff
	Prefetchable memory behind bridge: 00000000d9600000-00000000d96fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: cb400000-cb4fffff
	Prefetchable memory behind bridge: 00000000d9a00000-00000000d9afffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: cb800000-cb8fffff
	Prefetchable memory behind bridge: 00000000d9e00000-00000000d9efffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: cbc00000-cbcfffff
	Prefetchable memory behind bridge: 00000000da200000-00000000da2fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Memory behind bridge: cc000000-cc0fffff
	Prefetchable memory behind bridge: 00000000da600000-00000000da6fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: ca500000-ca5fffff
	Prefetchable memory behind bridge: 00000000d8b00000-00000000d8bfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: ca900000-ca9fffff
	Prefetchable memory behind bridge: 00000000d8f00000-00000000d8ffffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: cad00000-cadfffff
	Prefetchable memory behind bridge: 00000000d9300000-00000000d93fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
	Memory behind bridge: cb100000-cb1fffff
	Prefetchable memory behind bridge: 00000000d9700000-00000000d97fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0f, subordinate=0f, sec-latency=0
	Memory behind bridge: cb500000-cb5fffff
	Prefetchable memory behind bridge: 00000000d9b00000-00000000d9bfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	Memory behind bridge: cb900000-cb9fffff
	Prefetchable memory behind bridge: 00000000d9f00000-00000000d9ffffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=11, subordinate=11, sec-latency=0
	Memory behind bridge: cbd00000-cbdfffff
	Prefetchable memory behind bridge: 00000000da300000-00000000da3fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=12, subordinate=12, sec-latency=0
	Memory behind bridge: cc100000-cc1fffff
	Prefetchable memory behind bridge: 00000000da700000-00000000da7fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=13, subordinate=13, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: ca600000-ca6fffff
	Prefetchable memory behind bridge: 00000000d8c00000-00000000d8cfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: caa00000-caafffff
	Prefetchable memory behind bridge: 00000000d9000000-00000000d90fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=15, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: cae00000-caefffff
	Prefetchable memory behind bridge: 00000000d9400000-00000000d94fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=16, subordinate=16, sec-latency=0
	Memory behind bridge: cb200000-cb2fffff
	Prefetchable memory behind bridge: 00000000d9800000-00000000d98fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=17, subordinate=17, sec-latency=0
	Memory behind bridge: cb600000-cb6fffff
	Prefetchable memory behind bridge: 00000000d9c00000-00000000d9cfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=18, subordinate=18, sec-latency=0
	Memory behind bridge: cba00000-cbafffff
	Prefetchable memory behind bridge: 00000000da000000-00000000da0fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=19, subordinate=19, sec-latency=0
	Memory behind bridge: cbe00000-cbefffff
	Prefetchable memory behind bridge: 00000000da400000-00000000da4fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1a, subordinate=1a, sec-latency=0
	Memory behind bridge: cc200000-cc2fffff
	Prefetchable memory behind bridge: 00000000da800000-00000000da8fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1b, subordinate=1b, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: ca700000-ca7fffff
	Prefetchable memory behind bridge: 00000000d8d00000-00000000d8dfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1c, subordinate=1c, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: cab00000-cabfffff
	Prefetchable memory behind bridge: 00000000d9100000-00000000d91fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1d, subordinate=1d, sec-latency=0
	Memory behind bridge: caf00000-caffffff
	Prefetchable memory behind bridge: 00000000d9500000-00000000d95fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1e, subordinate=1e, sec-latency=0
	Memory behind bridge: cb300000-cb3fffff
	Prefetchable memory behind bridge: 00000000d9900000-00000000d99fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1f, subordinate=1f, sec-latency=0
	Memory behind bridge: cb700000-cb7fffff
	Prefetchable memory behind bridge: 00000000d9d00000-00000000d9dfffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
	Memory behind bridge: cbb00000-cbbfffff
	Prefetchable memory behind bridge: 00000000da100000-00000000da1fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=21, subordinate=21, sec-latency=0
	Memory behind bridge: cbf00000-cbffffff
	Prefetchable memory behind bridge: 00000000da500000-00000000da5fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=22, subordinate=22, sec-latency=0
	Memory behind bridge: cc300000-cc3fffff
	Prefetchable memory behind bridge: 00000000da900000-00000000da9fffff
	Capabilities: [40] Subsystem: VMware PCI Express Root Port
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Express Root Port (Slot+), MSI 00
	Capabilities: [8c] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

02:00.0 USB Controller: VMware USB1.1 UHCI Controller
	Subsystem: VMware Device 1976
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

02:01.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
	Subsystem: VMware Device 0750
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	Memory at c9020000 (64-bit, non-prefetchable) [size=128K]
	Memory at c9000000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 2000 [size=64]
	[virtual] Expansion ROM at d8400000 [disabled] [size=64K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [e4] PCI-X non-bridge device
	Kernel driver in use: e1000
	Kernel modules: e1000

02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 2040 [size=64]
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

02:03.0 USB Controller: VMware USB2 EHCI Controller (prog-if 20)
	Subsystem: VMware USB2 EHCI Controller
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at c9010000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ehci_hcd


```


3)
```
root@bt:~# lsusb
Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

4)```
root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:17:17:85  
          inet addr:192.168.111.128  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe17:1785/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73731 (73.7 KB)  TX bytes:8758 (8.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110909 (110.9 KB)  TX bytes:110909 (110.9 KB)

```


5)
```
root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

6
```
root@bt:~# lsmod
Module                  Size  Used by
mac80211              277511  0 
cfg80211              165732  1 mac80211
nls_iso8859_1           4665  0 
nls_cp437               6383  0 
vfat                   10835  0 
fat                    53931  1 vfat
usb_storage            48582  0 
uas                     8820  0 
btusb                  13027  2 
bluetooth              83163  5 btusb
rfkill                 18476  3 cfg80211,bluetooth
dm_crypt               16476  0 
snd_ens1371            22759  0 
gameport                9367  1 snd_ens1371
snd_ac97_codec        124117  1 snd_ens1371
ac97_bus                1434  1 snd_ac97_codec
snd_pcm_oss            39737  0 
snd_mixer_oss          15609  1 snd_pcm_oss
snd_pcm                83135  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            29952  0 
snd_seq_midi            5676  0 
snd_rawmidi            21765  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      6708  2 snd_seq_oss,snd_seq_midi
snd_seq                54693  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 10865  0 
snd_timer              21958  2 snd_pcm,snd_seq
snd_seq_device          6265  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                 3869  0 
psmouse                60384  0 
vmw_balloon             4638  0 
serio_raw               4784  0 
ppdev                   6120  0 
lp                      9893  0 
snd                    65738  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             29795  1 
shpchp                 28154  0 
i2c_piix4               8943  0 
soundcore               7240  1 snd
snd_page_alloc          8149  1 snd_pcm
parport                34080  3 ppdev,lp,parport_pc
vmw_pvscsi             15429  0 
vmxnet3                39339  0 
usbhid                 38699  0 
hid                    83826  1 usbhid
e1000                 104456  0 
floppy                 63573  0 
intel_agp              11862  1 
mptspi                 16313  2 
mptscsih               33465  1 mptspi
mptbase                91852  2 mptspi,mptscsih
intel_gtt              16156  1 intel_agp

```

what i want to know is (if u ca check the drivers i downloaded r the right one n will solve my problem) how to install these drivers if they will make my card detect-able...if not then how can i make my card detectabe??

---

### Post by Basher101 on 2012-01-23
really? you install in a **_[COLOR="Red"]virtual[/COLOR]_** machine and wonder why the **_[COLOR="red"]virtual[/COLOR]_** hardware does not work? After all, its just **_[COLOR="red"]virtual[/COLOR]_**..

---

### Post by Dangertux on 2012-01-23
> **Basher101 said:**
> really? you install in a **_[COLOR=Red]virtual[/COLOR]_** machine and wonder why the **_[COLOR=red]virtual[/COLOR]_** hardware does not work? After all, its just **_[COLOR=red]virtual[/COLOR]_**..

This, get a USB wifi interface if you're going to do it that way ;-)

---

### Post by mrughindersingh on 2012-01-23
i do have a Micromaxx 310 USB modem which uses sim card for internet and works in backtrack but its slow very slow.
The problem is catching the wifi..n for that i need my wifi working in Backtrack how i do that?
here is something..i plug the USB modem in the laptop n connect it from win 7 n not from backtrack but still the internet works in backtrack..
cant something similar be done in case of wifi..like turn it on in win 7 n use it alos in backtrack5??

---

### Post by mrughindersingh on 2012-01-23
i also have tried patching from here:
[http://trac.aircrack-ng.org/ticket/934](http://trac.aircrack-ng.org/ticket/934)
tried both paths fr patching..patching goes perfectly but nothing is detected even then.

---

### Post by sffvba[e0rt on 2012-01-23
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by Dangertux on 2012-01-23
I said wifi , not CDMA/3g/4g . Different frequencies. You need a WIFI usb interface. Hope this helps.

---

### Post by mrughindersingh on 2012-01-24
ok..i get it the problem is using backtrack with virtual machine but what if i boot backtrack from live cd or pendrive (but not install it, only boot) will the problem still remain or i can work with the wifi card then?

---

### Post by haqking on 2012-01-24
> **mrughindersingh said:**
> ok..i get it the problem is using backtrack with virtual machine but what if i boot backtrack from live cd or pendrive (but not install it, only boot) will the problem still remain or i can work with the wifi card then?

If you use a virtual machine then you can only use USB wifi devices and not built in.

If you boot directly to a Backtrack or similar then as long as the hardware is supported then you can you use it.

You are better off in the backtrack forums or aircrack forums to help on your device and chipset for support for whether it works, though backtrack may be based on Ubuntu the kernel is a specialised build around certain chipsets especially where wireless is concerned etc.

I have got a feeling but not 100% that aircrack will be need to be recompiled from source for use with that chipset but im not positive on that one but i dont think it will be supported out of the box and the same in backtrack in general, you will need to verify that as i cant be bothered right now ;-), and of course if you are using a Live CD then any changes will be lost when you reboot unless you use a persistent USB for example.

Cheers

---

### Post by mrughindersingh on 2012-01-25
ok now i need help with the wifi usb device..which one to buy?? they are ranging from 5$ to $50 n more.
Any suggestions..i heard about the netgear one still i need more suggestions..meanwhile i amt rying the USB boot of backtrack 5 n see if anything changes.

---

### Post by haqking on 2012-01-25
> **mrughindersingh said:**
> ok now i need help with the wifi usb device..which one to buy?? they are ranging from 5$ to $50 n more.
Any suggestions..i heard about the netgear one still i need more suggestions..meanwhile i amt rying the USB boot of backtrack 5 n see if anything changes.

chipsets and drivers supported in BT are here [http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

Like i said before, you are better off in the BT or Aircrack forums.

The aircrack suite and use of most of the BT tools are not supported here.

Cheers

---

### Post by mrughindersingh on 2012-01-26
thanks for all the help guys..moving to the backtrack forum.
This thread can be closed

---

### Post by nothingspecial on 2012-01-26
Done.

---

