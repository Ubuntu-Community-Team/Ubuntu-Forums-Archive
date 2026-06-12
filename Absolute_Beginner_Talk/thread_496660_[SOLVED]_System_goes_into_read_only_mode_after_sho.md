---
title: "[SOLVED] System goes into read only mode after short time"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2007-07-09
I have had several issues with my hard drive going into read only mode while working on Ubuntu 7.04 64-bit. If I go to restart the system, it doesn't restart until I use ALT+SYSReq+RSEIUB. 

The system runs fine once it restarts - but FSCK doesn't show on bootup when this occurs. I have an Acer Aspire 5100-3583 with a Hitachi Travelstar 80GB drive. I thought the drive could be at fault, but I've struggled with determining the real cause as to why this system is behaving so strangely.

I know several people post log files on these forums to show what is going on. If someone is good at reading system logs, I'd love to know what is happening with this laptop before I go and buy another hard drive. I have FSCK'ed it, (just get contiguous file messages mostly), memtested it, etc. I need some serious help. Thanks!

---

### Post by swoll1980 on 2007-07-09
Open run command (alt F2) type  "gksu nautilus"           This should do the trick

---

### Post by kinematic on 2007-07-09
> **swoll1980 said:**
> Open run command (alt F2) type  "gksu nautilus"           This should do the trick

although i've got no idea what's going on this is NOT the solution!
gksu nautilus lets you run your file manager as root so please stop giving advice like this if you don't know what you're talking about.

please post your dmesg log wich is located in /var/log so we can take a look.

---

### Post by randytuggle on 2007-07-09
Here's the logfile you requested. Thank you for offering your help. I am really trying to figure this one out. I've seen lots of computer issues I could fix in my time - but this one stumps me.

---

### Post by swoll1980 on 2007-07-09
He needs write access to his files. This works for me when I need write access

---

### Post by randytuggle on 2007-07-09
how do I attach or upload the file? It doesn't post when I attach it...I just pasted it below:

[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=648639e2-1369-44b1-9b79-8eefea372a01 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe90000 (usable)
[    0.000000]  BIOS-e820: 000000002fe90000 - 000000002fe9a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fe9a000 - 000000002ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x00000000000f8040
[    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x000000002fe91c71
[    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x000000002fe99c7f
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 LOHR 0x00000000) @ 0x000000002fe99cf3
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x000000002fe99e69
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x000000002fe99eaf
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000002fe99eeb
[    0.000000] ACPI: DSDT (v001   Acer  Navarro 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000002fe90000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000002fe90000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   196240
[    0.000000] On node 0 totalpages: 196141
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2855 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 2626 pages used for memmap
[    0.000000]   DMA32 zone: 189518 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d0000
[    0.000000] Nosave address range: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 192373
[    0.000000] Kernel command line: root=UUID=648639e2-1369-44b1-9b79-8eefea372a01 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   16.353069] Console: colour VGA+ 80x25
[   16.353553] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.354241] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.354349] Checking aperture...
[   16.354354] CPU 0: aperture @ d30c000000 size 32 MB
[   16.354356] Aperture too small (32 MB)
[   16.366009] No AGP bridge found
[   16.372272] Memory: 760528k/784960k available (2217k kernel code, 24036k reserved, 1162k data, 304k init)
[   16.450162] Calibrating delay using timer specific routine.. 3994.26 BogoMIPS (lpj=7988538)
[   16.450218] Security Framework v1.0.0 initialized
[   16.450224] SELinux:  Disabled at boot.
[   16.450248] Mount-cache hash table entries: 256
[   16.450388] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.450390] CPU: L2 Cache: 512K (64 bytes/line)
[   16.450393] CPU 0/0 -> Node 0
[   16.450413] SMP alternatives: switching to UP code
[   16.450567] Freeing SMP alternatives: 24k freed
[   16.450677] Early unpacking initramfs... done
[   16.777194] ACPI: Core revision 20060707
[   16.779928] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.234096] Using local APIC timer interrupts.
[   17.284196] result 12469187
[   17.284198] Detected 12.469 MHz APIC timer.
[   17.285782] Brought up 1 CPUs
[   17.285824] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   17.285826] time.c: Detected 1995.070 MHz processor.
[   17.286119] Time: 17:17:40  Date: 06/09/107
[   17.286152] NET: Registered protocol family 16
[   17.286229] ACPI: bus type pci registered
[   17.286237] PCI: Using configuration type 1
[   17.309905] ACPI: Interpreter enabled
[   17.309909] ACPI: Using IOAPIC for interrupt routing
[   17.310446] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.310451] PCI: Probing PCI hardware (bus 00)
[   17.312043] Boot video device is 0000:01:05.0
[   17.312826] PCI: Transparent bridge - 0000:00:14.4
[   17.312927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.317905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   17.318193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   17.318543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB4_._PRT]
[   17.318824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[   17.320348] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   17.320620] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   17.320888] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   17.321155] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   17.321424] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   17.321690] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   17.321993] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   17.322259] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   17.322529] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   17.373832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   17.374615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   17.375493] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.375508] pnp: PnP ACPI init
[   17.405925] pnp: PnP ACPI: found 10 devices
[   17.405974] PCI: Using ACPI for IRQ routing
[   17.405977] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.405984] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   17.405986] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   17.405988] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
[   17.405991] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   17.405993] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   17.406100] NET: Registered protocol family 8
[   17.406101] NET: Registered protocol family 20
[   17.406395] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   17.406398] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   17.406401] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.406403] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   17.406655] PCI: Bridge: 0000:00:01.0
[   17.406658]   IO window: 9000-9fff
[   17.406661]   MEM window: b0100000-b01fffff
[   17.406664]   PREFETCH window: c0000000-cfffffff
[   17.406666] PCI: Bridge: 0000:00:04.0
[   17.406667]   IO window: disabled.
[   17.406670]   MEM window: disabled.
[   17.406671]   PREFETCH window: disabled.
[   17.406674] PCI: Bridge: 0000:00:05.0
[   17.406675]   IO window: disabled.
[   17.406677]   MEM window: disabled.
[   17.406679]   PREFETCH window: disabled.
[   17.406691] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   17.406692]   IO window: 0000a400-0000a4ff
[   17.406698]   IO window: 0000a800-0000a8ff
[   17.406704]   PREFETCH window: 50000000-53ffffff
[   17.406710]   MEM window: 58000000-5bffffff
[   17.406716] PCI: Bridge: 0000:00:14.4
[   17.406719]   IO window: a000-afff
[   17.406725]   MEM window: b0200000-b02fffff
[   17.406730]   PREFETCH window: 50000000-53ffffff
[   17.406748] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.406754] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   17.406782] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[   17.406863] NET: Registered protocol family 2
[   17.441729] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   17.441927] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   17.442925] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.443393] TCP: Hash tables configured (established 131072 bind 65536)
[   17.443397] TCP reno registered
[   17.453788] checking if image is initramfs... it is
[   18.060250] Freeing initrd memory: 7303k freed
[   18.064354] audit: initializing netlink socket (disabled)
[   18.064368] audit(1184001460.264:1): initialized
[   18.064498] VFS: Disk quotas dquot_6.5.1
[   18.064515] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.064559] io scheduler noop registered
[   18.064561] io scheduler anticipatory registered
[   18.064563] io scheduler deadline registered
[   18.064574] io scheduler cfq registered (default)
[   18.064786] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.064806] assign_interrupt_mode Found MSI capability
[   18.064809] Allocate Port Service[0000:00:04.0:pcie00]
[   18.064838] Allocate Port Service[0000:00:04.0:pcie02]
[   18.064897] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.064915] assign_interrupt_mode Found MSI capability
[   18.064918] Allocate Port Service[0000:00:05.0:pcie00]
[   18.064947] Allocate Port Service[0000:00:05.0:pcie02]
[   18.086070] Real Time Clock Driver v1.12ac
[   18.086113] Linux agpgart interface v0.102 (c) Dave Jones
[   18.086116] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.086647] mice: PS/2 mouse device common for all mice
[   18.087115] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.087301] input: Macintosh mouse button emulation as /class/input/input0
[   18.087332] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.087336] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.087591] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[   18.087810] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.087887] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.087891] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.087894] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.087896] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.087899] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.088040] TCP cubic registered
[   18.088048] NET: Registered protocol family 1
[   18.088163] ACPI: (supports S0 S3 S4 S5)
[   18.088204]   Magic number: 15:204:289
[   18.088226]   hash matches device ttyz3
[   18.088313]   hash matches device tty22
[   18.088332] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.088410] Freeing unused kernel memory: 304k freed
[   18.090723] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.274946] Capability LSM initialized
[   19.309372] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.309383] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   19.338759] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   19.354072] ACPI: Thermal Zone [THRM] (44 C)
[   19.823704] usbcore: registered new interface driver usbfs
[   19.823729] usbcore: registered new interface driver hub
[   19.823749] usbcore: registered new device driver usb
[   19.824468] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.824508] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   19.824523] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   19.824653] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   19.824674] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0005000
[   19.890699] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.912972] usb usb1: configuration #1 chosen from 1 choice
[   19.912999] hub 1-0:1.0: USB hub found
[   19.913011] hub 1-0:1.0: 4 ports detected
[   20.016543] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   20.016560] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   20.016586] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   20.016603] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0006000
[   20.072510] usb usb2: configuration #1 chosen from 1 choice
[   20.072535] hub 2-0:1.0: USB hub found
[   20.072547] hub 2-0:1.0: 4 ports detected
[   20.177031] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   20.177049] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   20.177082] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   20.177135] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0007000
[   20.177147] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.177225] usb usb3: configuration #1 chosen from 1 choice
[   20.177249] hub 3-0:1.0: USB hub found
[   20.177255] hub 3-0:1.0: 8 ports detected
[   20.280480] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   20.280499] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   20.280509] ATIIXP: chipset revision 128
[   20.280511] ATIIXP: not 100% native mode: will probe irqs later
[   20.280520]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:DMA
[   20.280535] ATIIXP: simplex device: DMA disabled
[   20.280536] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   20.280540] Probing IDE interface ide0...
[   20.568552] hda: HTS541080G9AT00, ATA DISK drive
[   21.352180] hdb: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[   21.408373] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   21.429340] Probing IDE interface ide1...
[   22.000273] SCSI subsystem initialized
[   22.006145] libata version 2.20 loaded.
[   22.008350] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   22.008354] 8139cp 0000:06:01.0: Try the "8139too" driver instead.
[   22.010160] 8139too Fast Ethernet driver 0.9.28
[   22.010560] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   22.011394] eth0: RealTek RTL8139 at 0xffffc20000026000, 00:16:d4:1b:28:5e, IRQ 21
[   22.011397] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   22.020918] hda: max request size: 512KiB
[   22.031059] hda: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
[   22.031487] hda: cache flushes supported
[   22.031531]  hda: hda1 hda2 < hda5 >
[   22.076707] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   22.076715] Uniform CD-ROM driver Revision: 3.20
[   22.357055] Attempting manual resume
[   22.357059] swsusp: Resume From Partition 3:5
[   22.357061] PM: Checking swsusp image.
[   22.377930] PM: Resume from disk failed.
[   22.424715] kjournald starting.  Commit interval 5 seconds
[   22.424725] EXT3-fs: mounted filesystem with ordered data mode.
[   33.434512] eth0: link down
[   34.587805] NET: Registered protocol family 17
[   34.608099] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.613945] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.276995] ieee80211_crypt: registered algorithm 'NULL'
[   35.279087] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   35.279090] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   35.291905] Yenta: CardBus bridge found at 0000:06:04.0 [1025:009f]
[   35.291936] Yenta: Using CSCINT to route CSC interrupts to PCI
[   35.291938] Yenta: Routing CardBus interrupts to PCI
[   35.291944] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
[   35.427104] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   35.477962] sdhci: Secure Digital Host Controller Interface driver
[   35.477965] sdhci: Copyright(c) Pierre Ossman
[   35.521402] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[   35.521408] Socket status: 30000006
[   35.521412] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   35.521416] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   35.521419] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   35.527878] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   35.527910] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 23 (level, low) -> IRQ 23
[   35.527998] mmc0: SDHCI at 0xb0202800 irq 23 DMA
[   35.579684] bcm43xx driver
[   35.579793] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[   35.628736] input: PC Speaker as /class/input/input2
[   35.842171] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   36.066384] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   36.098441] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   36.524537] fuse init (API version 7.8)
[   36.581670] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
[   36.622936] lp: driver loaded but no devices found
[   36.672354] Adding 2249060k swap on /dev/disk/by-uuid/08f333e6-95a6-47c7-869b-7cb563bf775f.  Priority:-1 extents:1 across:2249060k
[   36.957062] EXT3 FS on hda1, internal journal
[   40.322699] NET: Registered protocol family 10
[   40.322785] lo: Disabled Privacy Extensions
[   40.322834] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by FleetAdmiral74 on 2007-07-09
> **swoll1980 said:**
> He needs write access to his files. This works for me when I need write access

Just listen, this may work, but it is NOT the best solution by far. He could do anything to **** up his system w/o confirmation. Wonder why you have to type in sudo for commands in the terminal? Same rule applies to your GUI interface.

---

### Post by swoll1980 on 2007-07-09
I probably shouldn't do it that way then. I posted the same question a couple weeks ago and got this the responce I got. No one gave me a better solution

---

### Post by swoll1980 on 2007-07-09
> **kinematic said:**
> although i've got no idea what's going on this is NOT the solution!
gksu nautilus lets you run your file manager as root so please stop giving advice like this if you don't know what you're talking about.



This what I was told to do and it worked. When I posted the answer I thought I did know what I was talking about. I was just trying to help the guy out. You could have been a little less snippy. Don't you think? Were all  
here trying to help each other. That kind of stuff is not nessesary.  :(

---

### Post by Lakefall on 2007-07-09
> **kinematic said:**
> please post your dmesg log wich is located in /var/log so we can take a look.
What he really should look at / post is kern.log, but preferably only the lines around the time when the partition(s) go(es) into read only mode.

EDIT: Of course there might not be such lines, because /var was in read only mode at the time. :-? So maybe he should just wait until it happens and use the dmesg command to see what the exact error is. In any case he should back up all important data *now*. It's always a good idea. :-)

---

### Post by randytuggle on 2007-07-09
The kern log is too large to post. If I knew how to attach it, I would.

---

### Post by Lakefall on 2007-07-09
Look at the timestamps in the beginning of each line and try to see if there are any lines which might be relevant. The read-only mode might have prevented those lines to be written, though...

Anyhow, back up all important data, if any.

EDIT: Did you try adding .txt at the end of the file name before attaching?

---

### Post by randytuggle on 2007-07-09
from the kern file yesterday...this is the start of the file...

Jul  8 17:23:56 randy-laptop kernel: [  490.792479] Losing some ticks... checking if CPU frequency changed.
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308349] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308354] ide: failed opcode was: unknown
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308634] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308637] ide: failed opcode was: unknown
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308910] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308913] ide: failed opcode was: unknown
Jul  8 17:51:53 randy-laptop kernel: [ 1167.309186] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.309189] ide: failed opcode was: unknown
Jul  8 17:51:53 randy-laptop kernel: [ 1167.309456] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.309459] ide: failed opcode was: unknown
Jul  8 18:32:19 randy-laptop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul  8 18:32:19 randy-laptop kernel: Loaded 25649 symbols from /boot/System.map-2.6.20-15-generic.
Jul  8 18:32:19 randy-laptop kernel: Symbols match kernel version 2.6.20.
Jul  8 18:32:19 randy-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Command line: root=UUID=648639e2-1369-44b1-9b79-8eefea372a01 ro quiet splash
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe90000 (usable)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe90000 - 000000002fe9a000 (ACPI data)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe9a000 - 000000002ff00000 (ACPI NVS)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002ff00000 - 0000000040000000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] end_pfn_map = 1048576
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] DMI present.
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x00000000000f8040
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x000000002fe91c71
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x000000002fe99c7f
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 LOHR 0x00000000) @ 0x000000002fe99cf3
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x000000002fe99e69
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x000000002fe99eaf
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000002fe99eeb
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: DSDT (v001   Acer  Navarro 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Number of nodes 1
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Node 0 MemBase 0000000000000000 Limit 000000002fe90000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Using node hash shift of 63
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000002fe90000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Zone PFN ranges:
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]     0:        0 ->      157
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]     0:      256 ->   196240
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] On node 0 totalpages: 196141
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA zone: 1086 pages reserved
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA zone: 2855 pages, LIFO batch:0
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA32 zone: 2626 pages used for memmap
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   DMA32 zone: 189518 pages, LIFO batch:31
Jul  8 18:32:19 randy-laptop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Setting APIC routing to physical flat
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000a0000 - 00000000000d0000
Jul  8 18:32:19 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000d0000 - 0000000000100000

---

### Post by dasunst3r on 2007-07-09
In the time that it is not read-only, I would recommend installing the package *smartmontools*, running *smartctl --all {device}* (replace {device} with your hard drive in question, usually */dev/hda*, and posting the results.  Linux putting itself in read-only mode is the sign of something pretty bad, so you might want to back up your data while you're at it.

---

### Post by randytuggle on 2007-07-09
maybe this will help from the kern log?

Jul  9 00:39:27 randy-laptop kernel: [   19.895689] Attempting manual resume
Jul  9 00:39:27 randy-laptop kernel: [   19.895693] swsusp: Resume From Partition 3:5
Jul  9 00:39:27 randy-laptop kernel: [   19.895695] PM: Checking swsusp image.
Jul  9 00:39:27 randy-laptop kernel: [   19.916553] PM: Resume from disk failed.
Jul  9 00:39:27 randy-laptop kernel: [   19.950490] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul  9 00:39:27 randy-laptop kernel: [   19.950494] EXT3-fs: write access will be enabled during recovery.
Jul  9 00:39:27 randy-laptop kernel: [   25.314582] kjournald starting.  Commit interval 5 seconds
Jul  9 00:39:27 randy-laptop kernel: [   25.314587] EXT3-fs warning (device hda1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
Jul  9 00:39:27 randy-laptop kernel: [   25.314592] EXT3-fs warning (device hda1): ext3_clear_journal_err: Marking fs in need of filesystem check.
Jul  9 00:39:27 randy-laptop kernel: [   25.322516] EXT3-fs: recovery complete.
Jul  9 00:39:27 randy-laptop kernel: [   25.323998] EXT3-fs: mounted filesystem with ordered data mode.
Jul  9 00:39:27 randy-laptop kernel: [   34.887324] eth0: link down
Jul  9 00:39:27 randy-laptop kernel: [   36.180096] NET: Registered protocol family 17
Jul  9 00:39:27 randy-laptop kernel: [   36.222494] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  9 00:39:27 randy-laptop kernel: [   36.228243] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  9 00:39:27 randy-laptop kernel: [   36.643452] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul  9 00:39:27 randy-laptop kernel: [   36.869179] ieee80211_crypt: registered algorithm 'NULL'
Jul  9 00:39:27 randy-laptop kernel: [   36.880545] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jul  9 00:39:27 randy-laptop kernel: [   36.880548] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jul  9 00:39:27 randy-laptop kernel: [   36.991245] input: PC Speaker as /class/input/input2
Jul  9 00:39:27 randy-laptop kernel: [   37.017168] bcm43xx driver
Jul  9 00:39:27 randy-laptop kernel: [   37.017260] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  9 00:39:27 randy-laptop kernel: [   37.079953] sdhci: Secure Digital Host Controller Interface driver
Jul  9 00:39:27 randy-laptop kernel: [   37.079956] sdhci: Copyright(c) Pierre Ossman
Jul  9 00:39:27 randy-laptop kernel: [   37.080000] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
Jul  9 00:39:27 randy-laptop kernel: [   37.080027] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 23 (level, low) -> IRQ 23
Jul  9 00:39:27 randy-laptop kernel: [   37.080124] mmc0: SDHCI at 0xb0202800 irq 23 DMA
Jul  9 00:39:27 randy-laptop kernel: [   37.121428] Yenta: CardBus bridge found at 0000:06:04.0 [1025:009f]
Jul  9 00:39:27 randy-laptop kernel: [   37.121460] Yenta: Using CSCINT to route CSC interrupts to PCI
Jul  9 00:39:27 randy-laptop kernel: [   37.121462] Yenta: Routing CardBus interrupts to PCI
Jul  9 00:39:27 randy-laptop kernel: [   37.121468] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
Jul  9 00:39:27 randy-laptop kernel: [   37.351465] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
Jul  9 00:39:27 randy-laptop kernel: [   37.351471] Socket status: 30000006
Jul  9 00:39:27 randy-laptop kernel: [   37.351476] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Jul  9 00:39:27 randy-laptop kernel: [   37.351480] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
Jul  9 00:39:27 randy-laptop kernel: [   37.351483] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Jul  9 00:39:27 randy-laptop kernel: [   37.356992] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul  9 00:39:27 randy-laptop kernel: [   37.495784] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
Jul  9 00:39:27 randy-laptop kernel: [   37.527950] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Jul  9 00:39:27 randy-laptop kernel: [   37.973017] fuse init (API version 7.8)
Jul  9 00:39:27 randy-laptop kernel: [   38.045101] lp: driver loaded but no devices found
Jul  9 00:39:27 randy-laptop kernel: [   38.084116] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul  9 00:39:27 randy-laptop kernel: [   38.119632] Adding 2249060k swap on /dev/disk/by-uuid/08f333e6-95a6-47c7-869b-7cb563bf775f.  Priority:-1 extents:1 across:2249060k
Jul  9 00:39:27 randy-laptop kernel: [  137.712521] EXT3 FS on hda1, internal journal
Jul  9 00:39:27 randy-laptop kernel: [  138.656943] NET: Registered protocol family 10
Jul  9 00:39:27 randy-laptop kernel: [  138.657040] lo: Disabled Privacy Extensions
Jul  9 00:39:27 randy-laptop kernel: [  138.657093] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  9 00:39:27 randy-laptop kernel: [  144.756150] ACPI: Battery Slot [BAT1] (battery present)
Jul  9 00:39:27 randy-laptop kernel: [  144.822911] ibm_acpi: ec object not found
Jul  9 00:39:27 randy-laptop kernel: [  144.873685] input: Power Button (FF) as /class/input/input4
Jul  9 00:39:27 randy-laptop kernel: [  144.877790] ACPI: Power Button (FF) [PWRF]
Jul  9 00:39:27 randy-laptop kernel: [  144.903941] input: Lid Switch as /class/input/input5
Jul  9 00:39:27 randy-laptop kernel: [  144.907952] ACPI: Lid Switch [LID]
Jul  9 00:39:27 randy-laptop kernel: [  144.933983] input: Power Button (CM) as /class/input/input6
Jul  9 00:39:27 randy-laptop kernel: [  144.938078] ACPI: Power Button (CM) [PWRB]
Jul  9 00:39:27 randy-laptop kernel: [  144.964189] input: Sleep Button (CM) as /class/input/input7
Jul  9 00:39:27 randy-laptop kernel: [  144.968267] ACPI: Sleep Button (CM) [SLPB]
Jul  9 00:39:27 randy-laptop kernel: [  145.000899] ACPI: AC Adapter [ACAD] (on-line)
Jul  9 00:39:27 randy-laptop kernel: [  145.015772] Using specific hotkey driver
Jul  9 00:39:27 randy-laptop kernel: [  145.043658] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul  9 00:39:27 randy-laptop kernel: [  145.043913] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul  9 00:39:27 randy-laptop kernel: [  145.056761] No dock devices found.
Jul  9 00:39:27 randy-laptop kernel: [  145.079363] wmi_add device=ffff81002e3bc800
Jul  9 00:39:27 randy-laptop kernel: [  145.079367] calling WQBA
Jul  9 00:39:27 randy-laptop kernel: [  145.097831] pcc_acpi: loading...
Jul  9 00:39:27 randy-laptop kernel: [  145.451114] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
Jul  9 00:39:27 randy-laptop kernel: [  145.451166] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
Jul  9 00:39:27 randy-laptop kernel: [  145.451168] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
Jul  9 00:39:27 randy-laptop kernel: [  145.451171] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
Jul  9 00:39:27 randy-laptop kernel: [  145.451173] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
Jul  9 00:39:30 randy-laptop kernel: [  148.746177] eth1: no IPv6 routers present
Jul  9 00:39:31 randy-laptop kernel: [  149.321952] Losing some ticks... checking if CPU frequency changed.
Jul  9 00:39:32 randy-laptop kernel: [  150.406708] ppdev: user-space parallel port driver

---

### Post by randytuggle on 2007-07-09
and here's more from kern log:

Jul  9 00:39:40 randy-laptop kernel: [  157.329906] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul  9 00:39:41 randy-laptop kernel: [  157.827626] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.827630] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.827906] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.827909] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.828176] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.828179] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.828438] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.828440] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.828699] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.828702] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.828967] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.828970] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.829240] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.829243] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.829502] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.829505] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.829777] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.829780] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.830041] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.830044] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.830305] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.830308] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.830579] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.830581] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.830856] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.830859] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.835516] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.835521] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.835820] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.835823] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.836081] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.836084] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.836352] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.836354] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.850829] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.850834] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.851105] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.851108] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.851367] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.851370] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.851640] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.851643] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.851911] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.851914] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.852173] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.852175] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.852434] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.852437] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.852703] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.852705] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.852971] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.852974] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.853235] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.853238] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.853497] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.853500] ide: failed opcode was: unknown
Jul  9 00:39:41 randy-laptop kernel: [  157.853767] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  9 00:39:41 randy-laptop kernel: [  157.853770] ide: failed opcode was: unknown
Jul  9 07:55:40 randy-laptop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul  9 07:55:40 randy-laptop kernel: Loaded 25649 symbols from /boot/System.map-2.6.20-15-generic.
Jul  9 07:55:40 randy-laptop kernel: Symbols match kernel version 2.6.20.
Jul  9 07:55:40 randy-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Command line: root=UUID=648639e2-1369-44b1-9b79-8eefea372a01 ro quiet splash
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe90000 (usable)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe90000 - 000000002fe9a000 (ACPI data)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe9a000 - 000000002ff00000 (ACPI NVS)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002ff00000 - 0000000040000000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] end_pfn_map = 1048576
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] DMI present.
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x00000000000f8040
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x000000002fe91c71
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x000000002fe99c7f
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 LOHR 0x00000000) @ 0x000000002fe99cf3
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x000000002fe99e69
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x000000002fe99eaf
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000002fe99eeb
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: DSDT (v001   Acer  Navarro 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Number of nodes 1
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Node 0 MemBase 0000000000000000 Limit 000000002fe90000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Using node hash shift of 63
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000002fe90000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Zone PFN ranges:
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]     0:        0 ->      157
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]     0:      256 ->   196240
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] On node 0 totalpages: 196141
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA zone: 1086 pages reserved
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA zone: 2855 pages, LIFO batch:0
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA32 zone: 2626 pages used for memmap
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   DMA32 zone: 189518 pages, LIFO batch:31
Jul  9 07:55:40 randy-laptop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Setting APIC routing to physical flat
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000a0000 - 00000000000d0000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000d0000 - 0000000000100000
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 192373
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Kernel command line: root=UUID=648639e2-1369-44b1-9b79-8eefea372a01 ro quiet splash
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] Initializing CPU#0
Jul  9 07:55:40 randy-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)

---

### Post by randytuggle on 2007-07-09
> **dasunst3r said:**
> In the time that it is not read-only, I would recommend installing the package *smartmontools*, running *smartctl --all {device}* (replace {device} with your hard drive in question, usually */dev/hda*, and posting the results.  Linux putting itself in read-only mode is the sign of something pretty bad, so you might want to back up your data while you're at it.

Here it is:

smartctl version 5.36 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K100 series
Device Model:     HTS541080G9AT00
Serial Number:    MP28MBXBGV9TBH
Firmware Version: MB4OA60A
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a
Local Time is:    Mon Jul  9 16:33:55 2007 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  56) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   218   218   033    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1109
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       1597
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       965
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       63
193 Load_Cycle_Count        0x0012   093   093   000    Old_age   Always       -       77060
194 Temperature_Celsius     0x0002   152   152   000    Old_age   Always       -       36 (Lifetime Min/Max 11/60)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       124

SMART Error Log Version: 1
ATA Error Count: 85 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 85 occurred at disk power-on lifetime: 1509 hours (62 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 41 7f e8 70 ef

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  70 43 41 7f e8 70 ef 02      00:00:05.400  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.400  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.300  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.300  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.200  SEEK [OBS-7]

Error 84 occurred at disk power-on lifetime: 1509 hours (62 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 41 7f e8 70 ef

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  70 43 41 7f e8 70 ef 02      00:00:05.400  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.300  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.300  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.200  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.200  SEEK [OBS-7]

Error 83 occurred at disk power-on lifetime: 1509 hours (62 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 41 7f e8 70 ef

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  70 43 41 7f e8 70 ef 02      00:00:05.300  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.200  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.200  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]

Error 82 occurred at disk power-on lifetime: 1509 hours (62 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 41 7f e8 70 ef

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  70 43 41 7f e8 70 ef 02      00:00:05.200  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.200  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.000  SEEK [OBS-7]

Error 81 occurred at disk power-on lifetime: 1509 hours (62 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 41 7f e8 70 ef

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.100  SEEK [OBS-7]
  70 43 41 7f e8 70 a0 04      00:00:05.000  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:05.000  SEEK [OBS-7]
  70 43 41 7f e8 70 ef 02      00:00:04.900  SEEK [OBS-7]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1520         -
# 2  Short offline       Completed without error       00%      1497         -
# 3  Short offline       Completed without error       00%      1495         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by Lakefall on 2007-07-09
> **randytuggle said:**
> Jul  8 17:51:53 randy-laptop kernel: [ 1167.308349] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul  8 17:51:53 randy-laptop kernel: [ 1167.308354] ide: failed opcode was: unknown
Well, these lines are definitely related to the problem.

---

### Post by randytuggle on 2007-07-09
So do you think it's a "computer problem" overall (motherboard related) or just that the hard drive is trash?

---

### Post by Lakefall on 2007-07-09
Well, I'm not an expert when it comes to failing hard drives, but the fact that the hard drive itself has logged errors (85 total) and that it looks like even the "SMART Selective Self-Test Log Structure" is broken, I would guess the hard drive is definitely about to break apart.

---

### Post by randytuggle on 2007-07-09
Ok. I'll buy a new hard drive in a few days and see if that's the fix. I'll update this post when done. Thanks!

---

### Post by randytuggle on 2007-07-10
It was running too hot! Run laptops with the slowest speeds and it runs fine. In addition to the overheating issues, I reset the hard drive using hdparm -w. It was a dangerous thing to attempt, but with a seemingly broken drive, I had no choice but to give it a try and it worked excellently! When re-installing Ubuntu, I hadn't partitioned the reset drive beforehand - so the install was very slow without a swap partition in place. BUT it WORKED GREAT!

Update: I have been trying to crash this system for nearly three hours and haven't been able to generate a single error! I love Ubuntu!!!!!! I think I may have fixed this issue to a point where I can actually get by on this drive for awhile longer without worry. Cheers!

---

