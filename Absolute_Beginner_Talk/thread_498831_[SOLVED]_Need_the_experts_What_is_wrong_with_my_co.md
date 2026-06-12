---
title: "[SOLVED] Need the experts: What is wrong with my computer?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2007-07-11
What is wrong with my laptop? I just installed a new hard drive because I was getting "cannot mount drive" errors during computer usage (listening to streamtuner via xmms,web browsing). I thought the problem was simply my hard drive. It wasn't being detected at several startups, it would cause these errors,etc. Now it is replaced and I am getting these "read-only drive" errors! Here's my fresh kern log:

Jul 11 19:44:57 randy-laptop kernel: [  916.100423] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 19:55:26 randy-laptop kernel: [ 1168.143097] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 20:08:20 randy-laptop kernel: [ 1482.711720] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 20:41:45 randy-laptop kernel: [ 2340.138666] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul 11 20:41:45 randy-laptop kernel: [ 2340.138671] ide: failed opcode was: unknown
Jul 11 20:41:45 randy-laptop kernel: [ 2340.138981] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul 11 20:41:45 randy-laptop kernel: [ 2340.138984] ide: failed opcode was: unknown
Jul 11 20:41:45 randy-laptop kernel: [ 2340.139295] hdb: status error: status=0x50 { DriveReady SeekComplete }
Jul 11 20:41:45 randy-laptop kernel: [ 2340.139298] ide: failed opcode was: unknown
Jul 11 21:01:43 randy-laptop kernel: [ 2865.635414] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 21:07:29 randy-laptop kernel: [ 3068.775820] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 21:37:27 randy-laptop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul 11 21:37:27 randy-laptop kernel: Loaded 25649 symbols from /boot/System.map-2.6.20-15-generic.
Jul 11 21:37:27 randy-laptop kernel: Symbols match kernel version 2.6.20.
Jul 11 21:37:27 randy-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Command line: root=UUID=43d52c15-5d17-483d-84c7-55f139781ecf ro quiet splash
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe90000 (usable)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe90000 - 000000002fe9a000 (ACPI data)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002fe9a000 - 000000002ff00000 (ACPI NVS)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 000000002ff00000 - 0000000040000000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] end_pfn_map = 1048576
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] DMI present.
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x00000000000f8040
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x000000002fe91c71
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x000000002fe99c7f
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 LOHR 0x00000000) @ 0x000000002fe99cf3
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x000000002fe99e69
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x000000002fe99eaf
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000002fe99eeb
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: DSDT (v001   Acer  Navarro 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Number of nodes 1
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Node 0 MemBase 0000000000000000 Limit 000000002fe90000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Entering add_active_range(0, 256, 196240) 1 entries of 3200 used
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Using node hash shift of 63
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000002fe90000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Zone PFN ranges:
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]     0:        0 ->      157
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]     0:      256 ->   196240
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] On node 0 totalpages: 196141
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA zone: 1086 pages reserved
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA zone: 2855 pages, LIFO batch:0
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA32 zone: 2626 pages used for memmap
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   DMA32 zone: 189518 pages, LIFO batch:31
Jul 11 21:37:27 randy-laptop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Setting APIC routing to physical flat
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000a0000 - 00000000000d0000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Nosave address range: 00000000000d0000 - 0000000000100000
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 192373
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Kernel command line: root=UUID=43d52c15-5d17-483d-84c7-55f139781ecf ro quiet splash
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] Initializing CPU#0
Jul 11 21:37:27 randy-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   14.349523] Console: colour VGA+ 80x25
Jul 11 21:37:27 randy-laptop kernel: [   14.350009] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   14.350698] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   14.350807] Checking aperture...
Jul 11 21:37:27 randy-laptop kernel: [   14.350811] CPU 0: aperture @ c30e000000 size 32 MB
Jul 11 21:37:27 randy-laptop kernel: [   14.350812] Aperture too small (32 MB)
Jul 11 21:37:27 randy-laptop kernel: [   14.362368] No AGP bridge found
Jul 11 21:37:27 randy-laptop kernel: [   14.368653] Memory: 760524k/784960k available (2217k kernel code, 24040k reserved, 1162k data, 304k init)
Jul 11 21:37:27 randy-laptop kernel: [   14.446609] Calibrating delay using timer specific routine.. 4009.08 BogoMIPS (lpj=8018175)
Jul 11 21:37:27 randy-laptop kernel: [   14.446666] Security Framework v1.0.0 initialized
Jul 11 21:37:27 randy-laptop kernel: [   14.446671] SELinux:  Disabled at boot.
Jul 11 21:37:27 randy-laptop kernel: [   14.446694] Mount-cache hash table entries: 256
Jul 11 21:37:27 randy-laptop kernel: [   14.446836] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 21:37:27 randy-laptop kernel: [   14.446839] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 21:37:27 randy-laptop kernel: [   14.446842] CPU 0/0 -> Node 0
Jul 11 21:37:27 randy-laptop kernel: [   14.446863] SMP alternatives: switching to UP code
Jul 11 21:37:27 randy-laptop kernel: [   14.447015] Freeing SMP alternatives: 24k freed
Jul 11 21:37:27 randy-laptop kernel: [   14.447124] Early unpacking initramfs... done
Jul 11 21:37:27 randy-laptop kernel: [   14.774634] ACPI: Core revision 20060707
Jul 11 21:37:27 randy-laptop kernel: [   14.777397] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 11 21:37:27 randy-laptop kernel: [   15.232360] Using local APIC timer interrupts.
Jul 11 21:37:27 randy-laptop kernel: [   15.282460] result 12469190
Jul 11 21:37:27 randy-laptop kernel: [   15.282462] Detected 12.469 MHz APIC timer.
Jul 11 21:37:27 randy-laptop kernel: [   15.286234] Brought up 1 CPUs
Jul 11 21:37:27 randy-laptop kernel: [   15.286276] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
Jul 11 21:37:27 randy-laptop kernel: [   15.286278] time.c: Detected 1995.068 MHz processor.
Jul 11 21:37:27 randy-laptop kernel: [   15.286574] Time:  1:36:55  Date: 06/12/107
Jul 11 21:37:27 randy-laptop kernel: [   15.286609] NET: Registered protocol family 16
Jul 11 21:37:27 randy-laptop kernel: [   15.286686] ACPI: bus type pci registered
Jul 11 21:37:27 randy-laptop kernel: [   15.286694] PCI: Using configuration type 1
Jul 11 21:37:27 randy-laptop kernel: [   15.310357] ACPI: Interpreter enabled
Jul 11 21:37:27 randy-laptop kernel: [   15.310361] ACPI: Using IOAPIC for interrupt routing
Jul 11 21:37:27 randy-laptop kernel: [   15.310905] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 21:37:27 randy-laptop kernel: [   15.310909] PCI: Probing PCI hardware (bus 00)
Jul 11 21:37:27 randy-laptop kernel: [   15.312498] Boot video device is 0000:01:05.0
Jul 11 21:37:27 randy-laptop kernel: [   15.313281] PCI: Transparent bridge - 0000:00:14.4
Jul 11 21:37:27 randy-laptop kernel: [   15.313384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.318463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.318753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.319102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB4_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.319383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.320909] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.321175] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.321442] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.321707] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.321974] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.322276] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.322542] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.322809] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.323074] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.374285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.375066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul 11 21:37:27 randy-laptop kernel: [   15.375940] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 11 21:37:27 randy-laptop kernel: [   15.375954] pnp: PnP ACPI init
Jul 11 21:37:27 randy-laptop kernel: [   15.402376] pnp: PnP ACPI: found 10 devices
Jul 11 21:37:27 randy-laptop kernel: [   15.402429] PCI: Using ACPI for IRQ routing
Jul 11 21:37:27 randy-laptop kernel: [   15.402432] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 11 21:37:27 randy-laptop kernel: [   15.402440] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
Jul 11 21:37:27 randy-laptop kernel: [   15.402442] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
Jul 11 21:37:27 randy-laptop kernel: [   15.402444] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
Jul 11 21:37:27 randy-laptop kernel: [   15.402447] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
Jul 11 21:37:27 randy-laptop kernel: [   15.402449] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Jul 11 21:37:27 randy-laptop kernel: [   15.402550] NET: Registered protocol family 8
Jul 11 21:37:27 randy-laptop kernel: [   15.402552] NET: Registered protocol family 20
Jul 11 21:37:27 randy-laptop kernel: [   15.402847] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
Jul 11 21:37:27 randy-laptop kernel: [   15.402850] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
Jul 11 21:37:27 randy-laptop kernel: [   15.402853] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 21:37:27 randy-laptop kernel: [   15.402855] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
Jul 11 21:37:27 randy-laptop kernel: [   15.403113] PCI: Bridge: 0000:00:01.0
Jul 11 21:37:27 randy-laptop kernel: [   15.403115]   IO window: 9000-9fff
Jul 11 21:37:27 randy-laptop kernel: [   15.403118]   MEM window: b0100000-b01fffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403121]   PREFETCH window: c0000000-cfffffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403123] PCI: Bridge: 0000:00:04.0
Jul 11 21:37:27 randy-laptop kernel: [   15.403125]   IO window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403127]   MEM window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403129]   PREFETCH window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403131] PCI: Bridge: 0000:00:05.0
Jul 11 21:37:27 randy-laptop kernel: [   15.403133]   IO window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403135]   MEM window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403137]   PREFETCH window: disabled.
Jul 11 21:37:27 randy-laptop kernel: [   15.403149] PCI: Bus 7, cardbus bridge: 0000:06:04.0
Jul 11 21:37:27 randy-laptop kernel: [   15.403151]   IO window: 0000a400-0000a4ff
Jul 11 21:37:27 randy-laptop kernel: [   15.403156]   IO window: 0000a800-0000a8ff
Jul 11 21:37:27 randy-laptop kernel: [   15.403162]   PREFETCH window: 50000000-53ffffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403168]   MEM window: 58000000-5bffffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403174] PCI: Bridge: 0000:00:14.4
Jul 11 21:37:27 randy-laptop kernel: [   15.403177]   IO window: a000-afff
Jul 11 21:37:27 randy-laptop kernel: [   15.403183]   MEM window: b0200000-b02fffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403188]   PREFETCH window: 50000000-53ffffff
Jul 11 21:37:27 randy-laptop kernel: [   15.403205] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jul 11 21:37:27 randy-laptop kernel: [   15.403212] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jul 11 21:37:27 randy-laptop kernel: [   15.403240] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 20
Jul 11 21:37:27 randy-laptop kernel: [   15.403323] NET: Registered protocol family 2
Jul 11 21:37:27 randy-laptop kernel: [   15.438185] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   15.438381] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   15.439375] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   15.439842] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 21:37:27 randy-laptop kernel: [   15.439846] TCP reno registered
Jul 11 21:37:27 randy-laptop kernel: [   15.450238] checking if image is initramfs... it is
Jul 11 21:37:27 randy-laptop kernel: [   16.060476] Freeing initrd memory: 7304k freed
Jul 11 21:37:27 randy-laptop kernel: [   16.064566] audit: initializing netlink socket (disabled)
Jul 11 21:37:27 randy-laptop kernel: [   16.064579] audit(1184204215.260:1): initialized
Jul 11 21:37:27 randy-laptop kernel: [   16.064710] VFS: Disk quotas dquot_6.5.1
Jul 11 21:37:27 randy-laptop kernel: [   16.064727] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 11 21:37:27 randy-laptop kernel: [   16.064771] io scheduler noop registered
Jul 11 21:37:27 randy-laptop kernel: [   16.064773] io scheduler anticipatory registered
Jul 11 21:37:27 randy-laptop kernel: [   16.064775] io scheduler deadline registered
Jul 11 21:37:27 randy-laptop kernel: [   16.064787] io scheduler cfq registered (default)
Jul 11 21:37:27 randy-laptop kernel: [   16.064997] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jul 11 21:37:27 randy-laptop kernel: [   16.065016] assign_interrupt_mode Found MSI capability
Jul 11 21:37:27 randy-laptop kernel: [   16.065019] Allocate Port Service[0000:00:04.0:pcie00]
Jul 11 21:37:27 randy-laptop kernel: [   16.065048] Allocate Port Service[0000:00:04.0:pcie02]
Jul 11 21:37:27 randy-laptop kernel: [   16.065108] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jul 11 21:37:27 randy-laptop kernel: [   16.065126] assign_interrupt_mode Found MSI capability
Jul 11 21:37:27 randy-laptop kernel: [   16.065128] Allocate Port Service[0000:00:05.0:pcie00]
Jul 11 21:37:27 randy-laptop kernel: [   16.065157] Allocate Port Service[0000:00:05.0:pcie02]
Jul 11 21:37:27 randy-laptop kernel: [   16.086435] Real Time Clock Driver v1.12ac
Jul 11 21:37:27 randy-laptop kernel: [   16.086477] Linux agpgart interface v0.102 (c) Dave Jones
Jul 11 21:37:27 randy-laptop kernel: [   16.086479] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 11 21:37:27 randy-laptop kernel: [   16.087016] mice: PS/2 mouse device common for all mice
Jul 11 21:37:27 randy-laptop kernel: [   16.087490] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 11 21:37:27 randy-laptop kernel: [   16.087675] input: Macintosh mouse button emulation as /class/input/input0
Jul 11 21:37:27 randy-laptop kernel: [   16.087706] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 11 21:37:27 randy-laptop kernel: [   16.087711] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 11 21:37:27 randy-laptop kernel: [   16.087965] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Jul 11 21:37:27 randy-laptop kernel: [   16.088942] i8042.c: Detected active multiplexing controller, rev 1.1.
Jul 11 21:37:27 randy-laptop kernel: [   16.089023] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 21:37:27 randy-laptop kernel: [   16.089028] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul 11 21:37:27 randy-laptop kernel: [   16.089030] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul 11 21:37:27 randy-laptop kernel: [   16.089032] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul 11 21:37:27 randy-laptop kernel: [   16.089035] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul 11 21:37:27 randy-laptop kernel: [   16.089120] TCP cubic registered
Jul 11 21:37:27 randy-laptop kernel: [   16.089127] NET: Registered protocol family 1
Jul 11 21:37:27 randy-laptop kernel: [   16.089268] ACPI: (supports S0 S3 S4 S5)
Jul 11 21:37:27 randy-laptop kernel: [   16.089309]   Magic number: 15:589:609
Jul 11 21:37:27 randy-laptop kernel: [   16.089432] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 11 21:37:27 randy-laptop kernel: [   16.089507] Freeing unused kernel memory: 304k freed
Jul 11 21:37:27 randy-laptop kernel: [   16.091803] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 11 21:37:27 randy-laptop kernel: [   17.274677] Capability LSM initialized
Jul 11 21:37:27 randy-laptop kernel: [   17.307237] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jul 11 21:37:27 randy-laptop kernel: [   17.307247] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Jul 11 21:37:27 randy-laptop kernel: [   17.336045] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
Jul 11 21:37:27 randy-laptop kernel: [   17.351495] ACPI: Thermal Zone [THRM] (52 C)
Jul 11 21:37:27 randy-laptop kernel: [   17.801410] usbcore: registered new interface driver usbfs
Jul 11 21:37:27 randy-laptop kernel: [   17.801435] usbcore: registered new interface driver hub
Jul 11 21:37:27 randy-laptop kernel: [   17.801457] usbcore: registered new device driver usb
Jul 11 21:37:27 randy-laptop kernel: [   17.802180] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 21:37:27 randy-laptop kernel: [   17.802213] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
Jul 11 21:37:27 randy-laptop kernel: [   17.802228] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 11 21:37:27 randy-laptop kernel: [   17.802356] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 11 21:37:27 randy-laptop kernel: [   17.802378] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0005000
Jul 11 21:37:27 randy-laptop kernel: [   17.834988] SCSI subsystem initialized
Jul 11 21:37:27 randy-laptop kernel: [   17.839999] libata version 2.20 loaded.
Jul 11 21:37:27 randy-laptop kernel: [   17.861127] usb usb1: configuration #1 chosen from 1 choice
Jul 11 21:37:27 randy-laptop kernel: [   17.861151] hub 1-0:1.0: USB hub found
Jul 11 21:37:27 randy-laptop kernel: [   17.861163] hub 1-0:1.0: 4 ports detected
Jul 11 21:37:27 randy-laptop kernel: [   17.900784] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 11 21:37:27 randy-laptop kernel: [   17.965036] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
Jul 11 21:37:27 randy-laptop kernel: [   17.965054] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 11 21:37:27 randy-laptop kernel: [   17.965076] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 11 21:37:27 randy-laptop kernel: [   17.965093] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0006000
Jul 11 21:37:27 randy-laptop kernel: [   18.020996] usb usb2: configuration #1 chosen from 1 choice
Jul 11 21:37:27 randy-laptop kernel: [   18.021023] hub 2-0:1.0: USB hub found
Jul 11 21:37:27 randy-laptop kernel: [   18.021036] hub 2-0:1.0: 4 ports detected
Jul 11 21:37:27 randy-laptop kernel: [   18.125014] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
Jul 11 21:37:27 randy-laptop kernel: [   18.125029] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 11 21:37:27 randy-laptop kernel: [   18.125050] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 11 21:37:27 randy-laptop kernel: [   18.125101] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0007000
Jul 11 21:37:27 randy-laptop kernel: [   18.125113] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 11 21:37:27 randy-laptop kernel: [   18.125176] usb usb3: configuration #1 chosen from 1 choice
Jul 11 21:37:27 randy-laptop kernel: [   18.125199] hub 3-0:1.0: USB hub found
Jul 11 21:37:27 randy-laptop kernel: [   18.125205] hub 3-0:1.0: 8 ports detected
Jul 11 21:37:27 randy-laptop kernel: [   18.230811] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Jul 11 21:37:27 randy-laptop kernel: [   18.230831] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:37:27 randy-laptop kernel: [   18.230842] ATIIXP: chipset revision 128
Jul 11 21:37:27 randy-laptop kernel: [   18.230844] ATIIXP: not 100%% native mode: will probe irqs later
Jul 11 21:37:27 randy-laptop kernel: [   18.230853]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:DMA
Jul 11 21:37:27 randy-laptop kernel: [   18.230867] ATIIXP: simplex device: DMA disabled
Jul 11 21:37:27 randy-laptop kernel: [   18.230868] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
Jul 11 21:37:27 randy-laptop kernel: [   18.230872] Probing IDE interface ide0...
Jul 11 21:37:27 randy-laptop kernel: [   18.517027] hda: WDC WD800VE-00KWT0, ATA DISK drive
Jul 11 21:37:27 randy-laptop kernel: [   19.300651] hdb: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
Jul 11 21:37:27 randy-laptop kernel: [   19.356648] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 11 21:37:27 randy-laptop kernel: [   19.397073] Probing IDE interface ide1...
Jul 11 21:37:27 randy-laptop kernel: [   19.956025] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 11 21:37:27 randy-laptop kernel: [   19.956029] 8139cp 0000:06:01.0: Try the "8139too" driver instead.
Jul 11 21:37:27 randy-laptop kernel: [   19.958879] 8139too Fast Ethernet driver 0.9.28
Jul 11 21:37:27 randy-laptop kernel: [   19.959602] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Jul 11 21:37:27 randy-laptop kernel: [   19.960396] eth0: RealTek RTL8139 at 0xffffc20000026000, 00:16:d4:1b:28:5e, IRQ 21
Jul 11 21:37:27 randy-laptop kernel: [   19.960399] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jul 11 21:37:27 randy-laptop kernel: [   19.966294] hda: max request size: 512KiB
Jul 11 21:37:27 randy-laptop kernel: [   20.009372] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Jul 11 21:37:27 randy-laptop kernel: [   20.009512] hda: cache flushes supported
Jul 11 21:37:27 randy-laptop kernel: [   20.009552]  hda: hda1 hda2 < hda5 >
Jul 11 21:37:27 randy-laptop kernel: [   20.059206] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jul 11 21:37:27 randy-laptop kernel: [   20.059215] Uniform CD-ROM driver Revision: 3.20
Jul 11 21:37:27 randy-laptop kernel: [   20.259199] Attempting manual resume
Jul 11 21:37:27 randy-laptop kernel: [   20.259203] swsusp: Resume From Partition 3:5
Jul 11 21:37:27 randy-laptop kernel: [   20.259205] PM: Checking swsusp image.
Jul 11 21:37:27 randy-laptop kernel: [   20.259405] PM: Resume from disk failed.
Jul 11 21:37:27 randy-laptop kernel: [   20.274182] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 11 21:37:27 randy-laptop kernel: [   20.274185] EXT3-fs: write access will be enabled during recovery.
Jul 11 21:37:27 randy-laptop kernel: [   25.607070] kjournald starting.  Commit interval 5 seconds
Jul 11 21:37:27 randy-laptop kernel: [   25.607085] EXT3-fs: recovery complete.
Jul 11 21:37:27 randy-laptop kernel: [   25.607440] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 21:37:27 randy-laptop kernel: [   37.238421] eth0: link down
Jul 11 21:37:27 randy-laptop kernel: [   38.559357] NET: Registered protocol family 17
Jul 11 21:37:27 randy-laptop kernel: [   38.632526] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 21:37:27 randy-laptop kernel: [   38.634692] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 11 21:37:27 randy-laptop kernel: [   38.816863] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 11 21:37:27 randy-laptop kernel: [   39.294956] sdhci: Secure Digital Host Controller Interface driver
Jul 11 21:37:27 randy-laptop kernel: [   39.294960] sdhci: Copyright(c) Pierre Ossman
Jul 11 21:37:27 randy-laptop kernel: [   39.295003] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
Jul 11 21:37:27 randy-laptop kernel: [   39.295030] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 23 (level, low) -> IRQ 23
Jul 11 21:37:27 randy-laptop kernel: [   39.295123] mmc0: SDHCI at 0xb0202800 irq 23 DMA
Jul 11 21:37:27 randy-laptop kernel: [   39.326943] Yenta: CardBus bridge found at 0000:06:04.0 [1025:009f]
Jul 11 21:37:27 randy-laptop kernel: [   39.326974] Yenta: Using CSCINT to route CSC interrupts to PCI
Jul 11 21:37:27 randy-laptop kernel: [   39.326976] Yenta: Routing CardBus interrupts to PCI
Jul 11 21:37:27 randy-laptop kernel: [   39.326982] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
Jul 11 21:37:27 randy-laptop kernel: [   39.360173] ieee80211_crypt: registered algorithm 'NULL'
Jul 11 21:37:27 randy-laptop kernel: [   39.372335] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jul 11 21:37:27 randy-laptop kernel: [   39.372339] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jul 11 21:37:27 randy-laptop kernel: [   39.381138] input: PC Speaker as /class/input/input2
Jul 11 21:37:27 randy-laptop kernel: [   39.558800] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
Jul 11 21:37:27 randy-laptop kernel: [   39.558806] Socket status: 30000006
Jul 11 21:37:27 randy-laptop kernel: [   39.558811] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Jul 11 21:37:27 randy-laptop kernel: [   39.558814] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
Jul 11 21:37:27 randy-laptop kernel: [   39.558817] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Jul 11 21:37:27 randy-laptop kernel: [   39.605021] bcm43xx driver
Jul 11 21:37:27 randy-laptop kernel: [   39.605116] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 11 21:37:27 randy-laptop kernel: [   39.924196] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
Jul 11 21:37:27 randy-laptop kernel: [   39.956306] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Jul 11 21:37:27 randy-laptop kernel: [   40.268156] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:37:27 randy-laptop kernel: [   40.563157] SoftMAC: Open Authentication completed with 00:14:6c:78:d2:f4
Jul 11 21:37:27 randy-laptop kernel: [   40.837544] fuse init (API version 7.8)
Jul 11 21:37:27 randy-laptop kernel: [   40.937303] lp: driver loaded but no devices found
Jul 11 21:37:27 randy-laptop kernel: [   41.129112] Adding 2249060k swap on /dev/disk/by-uuid/69e82397-50b0-47d9-be03-78c049fa7b8b.  Priority:-1 extents:1 across:2249060k
Jul 11 21:37:27 randy-laptop kernel: [   41.295674] EXT3 FS on hda1, internal journal
Jul 11 21:37:27 randy-laptop kernel: [   46.262165] NET: Registered protocol family 10
Jul 11 21:37:27 randy-laptop kernel: [   46.262250] lo: Disabled Privacy Extensions
Jul 11 21:37:27 randy-laptop kernel: [   46.262299] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 11 21:37:27 randy-laptop kernel: [   46.613013] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul 11 21:37:27 randy-laptop kernel: [   46.613247] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul 11 21:37:27 randy-laptop kernel: [   46.746496] ACPI: Battery Slot [BAT1] (battery present)
Jul 11 21:37:27 randy-laptop kernel: [   46.830842] ibm_acpi: ec object not found
Jul 11 21:37:27 randy-laptop kernel: [   46.895608] No dock devices found.
Jul 11 21:37:27 randy-laptop kernel: [   46.930407] input: Power Button (FF) as /class/input/input4
Jul 11 21:37:27 randy-laptop kernel: [   46.934481] ACPI: Power Button (FF) [PWRF]
Jul 11 21:37:27 randy-laptop kernel: [   46.957598] input: Lid Switch as /class/input/input5
Jul 11 21:37:27 randy-laptop kernel: [   46.961626] ACPI: Lid Switch [LID]
Jul 11 21:37:27 randy-laptop kernel: [   46.984908] input: Power Button (CM) as /class/input/input6
Jul 11 21:37:27 randy-laptop kernel: [   46.988877] ACPI: Power Button (CM) [PWRB]
Jul 11 21:37:27 randy-laptop kernel: [   47.011848] input: Sleep Button (CM) as /class/input/input7
Jul 11 21:37:27 randy-laptop kernel: [   47.015849] ACPI: Sleep Button (CM) [SLPB]
Jul 11 21:37:27 randy-laptop kernel: [   47.027629] Using specific hotkey driver
Jul 11 21:37:27 randy-laptop kernel: [   47.119032] ACPI: AC Adapter [ACAD] (on-line)
Jul 11 21:37:27 randy-laptop kernel: [   47.127212] pcc_acpi: loading...
Jul 11 21:37:27 randy-laptop kernel: [   47.143365] wmi_add device=ffff81002dc20800
Jul 11 21:37:27 randy-laptop kernel: [   47.143369] calling WQBA
Jul 11 21:37:27 randy-laptop kernel: [   47.330634] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
Jul 11 21:37:27 randy-laptop kernel: [   47.330683] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
Jul 11 21:37:27 randy-laptop kernel: [   47.330686] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
Jul 11 21:37:27 randy-laptop kernel: [   47.330688] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
Jul 11 21:37:27 randy-laptop kernel: [   47.330690] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
Jul 11 21:37:30 randy-laptop kernel: [   50.532696] Losing some ticks... checking if CPU frequency changed.
Jul 11 21:37:32 randy-laptop kernel: [   52.424086] ppdev: user-space parallel port driver
Jul 11 21:37:33 randy-laptop kernel: [   53.333432] Bluetooth: Core ver 2.11
Jul 11 21:37:33 randy-laptop kernel: [   53.333489] NET: Registered protocol family 31
Jul 11 21:37:33 randy-laptop kernel: [   53.333491] Bluetooth: HCI device and connection manager initialized
Jul 11 21:37:33 randy-laptop kernel: [   53.333495] Bluetooth: HCI socket layer initialized
Jul 11 21:37:33 randy-laptop kernel: [   53.368945] Bluetooth: L2CAP ver 2.8
Jul 11 21:37:33 randy-laptop kernel: [   53.368950] Bluetooth: L2CAP socket layer initialized
Jul 11 21:37:33 randy-laptop kernel: [   53.515793] Bluetooth: RFCOMM socket layer initialized
Jul 11 21:37:33 randy-laptop kernel: [   53.515805] Bluetooth: RFCOMM TTY layer initialized
Jul 11 21:37:33 randy-laptop kernel: [   53.515807] Bluetooth: RFCOMM ver 1.8
Jul 11 21:37:35 randy-laptop kernel: [   55.246888] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 11 21:37:36 randy-laptop kernel: [   55.809999] eth1: no IPv6 routers present

Please help! I am really stunned and no one has an answer. It's not memory (according to memtest86)... not the motherboard (doesn't seem like the board would do this one). HELP!!!!

---

### Post by expatCM on 2007-07-11
Is the hdd completely identified in the BIOS?

Does this laptop normally have a hidden partition which holds the BIOS information?

---

### Post by randytuggle on 2007-07-11
The drive has no hidden partitions that I am aware of. The BIOS is only held in the motherboard's memory/battery as far as I know. I just installed this drive tonight to replace a Hitachi Travelstar that showed fixed disk not found errors at most cold startups. The drive is identified in the bios.

---

