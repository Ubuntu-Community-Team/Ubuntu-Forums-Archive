---
title: "wifi not working in joli os 1.2"
date: 2012-06-28
forum: Any Other OS
---

### Post by chq on 2012-06-28
I'm running a fresh install of joli os 1.2 after spending about 6 hours trying to get the wifi to work (even going as far as installing a new kernel). I figured it would be best to start with the a fresh install when asking for help.
I'm using an acer aspire one d257, the wifi card is an intel centrino wireless n-100.

according to their own website, it should be compatible with my laptop ([http://help.jolicloud.com/entries/20055102-initial-list-of-devices-compatible-with-joli-os#acer](http://help.jolicloud.com/entries/20055102-initial-list-of-devices-compatible-with-joli-os#acer))

output of lspci:
```
chad@farts:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Device 08ae
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
chad@farts:~$ sudo lspci -v -nn
[sudo] password for chad: 
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 56180000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 40a0 [size=8]
	Memory at 40000000 (32-bit, prefetchable) [size=256M]
	Memory at 56000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0
	Memory at 56100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at 56200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 55000000-55ffffff
	Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 54000000-54ffffff
	Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 53000000-53ffffff
	Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 4040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at 56205000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device [1025:0590]

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 4098 [size=8]
	I/O ports at 40ac [size=4]
	I/O ports at 4090 [size=8]
	I/O ports at 40a8 [size=4]
	I/O ports at 4080 [size=16]
	Memory at 56204000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: medium devsel, IRQ 10
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 3000 [size=256]
	Memory at 50004000 (64-bit, prefetchable) [size=4K]
	Memory at 50000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=4
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-e0-4c-36-00-00-00-06
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
	Subsystem: Intel Corporation Device [8086:1005]
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at 54000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 4c-3e-06-ff-ff-9c-92-78

03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 53000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 00-e0-4c-00-01-00-00-00

```
any and all help is much appreciated, i'd really like to get this working.
thanks

---

