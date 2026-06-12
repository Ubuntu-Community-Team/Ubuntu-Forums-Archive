---
title: "MacBook 5-2 early 09 Installing using Mactel Support Docs for MB5-1"
date: 2009-08-02
forum: Apple Hardware Users
---

### Post by CellPhoneDude on 2009-08-02
I'll just cut to the chase, I'm a unix newb and I was wondering if there's anyway I can help do testing for the MB 5-2's. To start here's what dmesg outputs.
What I've done so far, install Nvidia Drivers from their site, I've done what the Mactel support docs outlined to fix the keyboard and touchpad. Not really sure what other info I should post...

```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 (Ubuntu 2.6.28-14.47-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 0000000050000000 - 000000007e83a000 (usable)
[    0.000000]  BIOS-e820: 000000007e83a000 - 000000007e83e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e83e000 - 000000007e859000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007e859000 - 000000007ea5a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ea5a000 - 000000007fec6000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fec6000 - 000000007fec8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fec8000 - 000000007fec9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fec9000 - 000000007fecb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fecb000 - 000000007fecd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fecd000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedf000 - 000000007fef9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef9000 - 000000007feff000 (reserved)
[    0.000000]  BIOS-e820: 000000007feff000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000093400000 - 0000000093401000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7e83a max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000040000000 (usable)
[    0.000000]  modified: 0000000040000000 - 0000000050000000 (reserved)
[    0.000000]  modified: 0000000050000000 - 000000007e83a000 (usable)
[    0.000000]  modified: 000000007e83a000 - 000000007e83e000 (ACPI NVS)
[    0.000000]  modified: 000000007e83e000 - 000000007e859000 (ACPI data)
[    0.000000]  modified: 000000007e859000 - 000000007ea5a000 (ACPI NVS)
[    0.000000]  modified: 000000007ea5a000 - 000000007fec6000 (ACPI data)
[    0.000000]  modified: 000000007fec6000 - 000000007fec8000 (ACPI NVS)
[    0.000000]  modified: 000000007fec8000 - 000000007fec9000 (ACPI data)
[    0.000000]  modified: 000000007fec9000 - 000000007fecb000 (ACPI NVS)
[    0.000000]  modified: 000000007fecb000 - 000000007fecd000 (ACPI data)
[    0.000000]  modified: 000000007fecd000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  modified: 000000007fedf000 - 000000007fef9000 (ACPI data)
[    0.000000]  modified: 000000007fef9000 - 000000007feff000 (reserved)
[    0.000000]  modified: 000000007feff000 - 000000007ff00000 (ACPI data)
[    0.000000]  modified: 0000000093400000 - 0000000093401000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bc000 - 37fef14b
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fae14b
[    0.000000] Move RAMDISK from 00000000378bc000 - 0000000037fef14a to 0087b000 - 00fae14a
[    0.000000] 1140MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fae14b]      NEW RAMDISK ==> [000087b000 - 0000fae14b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007e83a
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x00040000
[    0.000000]     0: 0x00050000 -> 0x0007e83a
[    0.000000] On node 0 totalpages: 452543
[    0.000000] free_area_init_node: node 0, pgdat c06ca500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2281 pages used for memmap
[    0.000000]   HighMem zone: 224083 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 98000000 (gap: 93401000:5cbff000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 448494
[    0.000000] Kernel command line: root=UUID=6dbd5cd5-1bbd-4290-8b3c-18a63ae73dad ro acpi=off quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: No reference (HPET/PMTIMER) available
[    0.000000] Marking TSC unstable due to could not calculate TSC khz
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] allocated 10364040 bytes of page_cgroup
[    0.000000] please try cgroup_disable=memory option if you don't want
[    0.000000] Scanning for low memory corruption every 60 seconds
[    0.000000] Memory: 1767084k/2072808k available (4115k kernel code, 42300k reserved, 2196k data, 532k init, 905456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.000000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.000000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.000000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.000000]       .data : 0xc0504def - 0xc0729e60   (2196 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0504def   (4115 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004000] Calibrating delay loop... 3145.72 BogoMIPS (lpj=6291456)
[    0.112000] Security Framework initialized
[    0.112000] SELinux:  Disabled at boot.
[    0.112000] AppArmor: AppArmor initialized
[    0.112000] Mount-cache hash table entries: 512
[    0.112000] Initializing cgroup subsys ns
[    0.112000] Initializing cgroup subsys cpuacct
[    0.112000] Initializing cgroup subsys memory
[    0.112000] Initializing cgroup subsys freezer
[    0.112000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.112000] CPU: L2 cache: 3072K
[    0.112000] CPU: Physical Processor ID: 0
[    0.112000] CPU: Processor Core ID: 0
[    0.112000] using mwait in idle threads.
[    0.112000] Checking 'hlt' instruction... OK.
[    0.128000] SMP alternatives: switching to UP code
[    0.240001] Freeing SMP alternatives: 18k freed
[    0.240001] weird, boot CPU (#0) not listedby the BIOS.
[    0.240001] SMP motherboard not detected.
[    0.348001] SMP disabled
[    0.348001] Brought up 1 CPUs
[    0.348001] Total of 1 processors activated (3145.72 BogoMIPS).
[    0.348001] CPU0 attaching NULL sched-domain.
[    0.348001] net_namespace: 776 bytes
[    0.348001] Booting paravirtualized kernel on bare hardware
[    0.348001] Time: 21:37:53  Date: 08/01/09
[    0.348001] regulator: core version 0.5
[    0.348001] NET: Registered protocol family 16
[    0.348001] EISA bus registered
[    0.348001] PCI: Using configuration type 1 for base access
[    0.348001] ACPI: Interpreter disabled.
[    0.348001] SCSI subsystem initialized
[    0.352001] libata version 3.00 loaded.
[    0.352001] usbcore: registered new interface driver usbfs
[    0.352001] usbcore: registered new interface driver hub
[    0.352001] usbcore: registered new device driver usb
[    0.352001] PCI: Probing PCI hardware
[    0.352001] PCI: Probing PCI hardware (bus 00)
[    0.352001] pci 0000:00:03.0: reg 10 io port: [0x2000-0x20ff]
[    0.352001] pci 0000:00:03.2: reg 10 io port: [0x2180-0x21bf]
[    0.352001] pci 0000:00:03.2: reg 20 io port: [0x2140-0x217f]
[    0.352001] pci 0000:00:03.2: reg 24 io port: [0x2100-0x213f]
[    0.352001] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.352001] pci 0000:00:03.2: PME# disabled
[    0.352001] pci 0000:00:03.5: reg 10 32bit mmio: [0x93400000-0x9347ffff]
[    0.352001] pci 0000:00:04.0: reg 10 32bit mmio: [0x93488000-0x93488fff]
[    0.352001] pci 0000:00:04.0: supports D1 D2
[    0.352001] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:04.0: PME# disabled
[    0.352001] pci 0000:00:04.1: reg 10 32bit mmio: [0x93489200-0x934892ff]
[    0.352001] pci 0000:00:04.1: supports D1 D2
[    0.352001] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:04.1: PME# disabled
[    0.352001] pci 0000:00:06.0: reg 10 32bit mmio: [0x93487000-0x93487fff]
[    0.352001] pci 0000:00:06.0: supports D1 D2
[    0.352001] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:06.0: PME# disabled
[    0.352001] pci 0000:00:06.1: reg 10 32bit mmio: [0x93489100-0x934891ff]
[    0.352001] pci 0000:00:06.1: supports D1 D2
[    0.352001] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:06.1: PME# disabled
[    0.352001] pci 0000:00:08.0: reg 10 32bit mmio: [0x93480000-0x93483fff]
[    0.352001] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.352001] pci 0000:00:08.0: PME# disabled
[    0.352001] pci 0000:00:0a.0: reg 10 32bit mmio: [0x93486000-0x93486fff]
[    0.352001] pci 0000:00:0a.0: reg 14 io port: [0x21e0-0x21e7]
[    0.352001] pci 0000:00:0a.0: reg 18 32bit mmio: [0x93489000-0x934890ff]
[    0.352001] pci 0000:00:0a.0: reg 1c 32bit mmio: [0x93489300-0x9348930f]
[    0.352001] pci 0000:00:0a.0: supports D1 D2
[    0.352001] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:0a.0: PME# disabled
[    0.352001] pci 0000:00:0b.0: reg 10 io port: [0x21d8-0x21df]
[    0.352001] pci 0000:00:0b.0: reg 14 io port: [0x21ec-0x21ef]
[    0.352001] pci 0000:00:0b.0: reg 18 io port: [0x21d0-0x21d7]
[    0.352001] pci 0000:00:0b.0: reg 1c io port: [0x21e8-0x21eb]
[    0.352001] pci 0000:00:0b.0: reg 20 io port: [0x21c0-0x21cf]
[    0.352001] pci 0000:00:0b.0: reg 24 32bit mmio: [0x93484000-0x93485fff]
[    0.352001] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:10.0: PME# disabled
[    0.352001] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:15.0: PME# disabled
[    0.352001] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:00:16.0: PME# disabled
[    0.352001] pci 0000:00:09.0: transparent bridge
[    0.352001] pci 0000:00:09.0: bridge 32bit mmio: [0x93300000-0x933fffff]
[    0.352001] pci 0000:02:00.0: reg 10 32bit mmio: [0x92000000-0x92ffffff]
[    0.352001] pci 0000:02:00.0: reg 14 64bit mmio: [0x80000000-0x8fffffff]
[    0.352001] pci 0000:02:00.0: reg 1c 64bit mmio: [0x90000000-0x91ffffff]
[    0.352001] pci 0000:02:00.0: reg 24 io port: [0x1000-0x107f]
[    0.352001] pci 0000:02:00.0: reg 30 32bit mmio: [0x93000000-0x9301ffff]
[    0.352001] pci 0000:00:10.0: bridge io port: [0x1000-0x1fff]
[    0.352001] pci 0000:00:10.0: bridge 32bit mmio: [0x92000000-0x930fffff]
[    0.352001] pci 0000:00:10.0: bridge 64bit mmio pref: [0x80000000-0x91ffffff]
[    0.352001] pci 0000:03:00.0: reg 10 64bit mmio: [0x93200000-0x93203fff]
[    0.352001] pci 0000:03:00.0: supports D1 D2
[    0.352001] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.352001] pci 0000:03:00.0: PME# disabled
[    0.352001] pci 0000:00:15.0: bridge 32bit mmio: [0x93200000-0x932fffff]
[    0.352001] pci 0000:04:00.0: reg 10 64bit mmio: [0x93100000-0x93100fff]
[    0.352001] pci 0000:04:00.0: supports D1 D2
[    0.352001] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.352001] pci 0000:04:00.0: PME# disabled
[    0.352001] pci 0000:00:16.0: bridge 32bit mmio: [0x93100000-0x931fffff]
[    0.352001] PCI: Discovered primary peer bus ff [IRQ]
[    0.352001] pci 0000:00:03.1: default IRQ router [10de:0aa4]
[    0.356001] Bluetooth: Core ver 2.13
[    0.356001] NET: Registered protocol family 31
[    0.356001] Bluetooth: HCI device and connection manager initialized
[    0.356001] Bluetooth: HCI socket layer initialized
[    0.356001] NET: Registered protocol family 8
[    0.356001] NET: Registered protocol family 20
[    0.356001] NetLabel: Initializing
[    0.356001] NetLabel:  domain hash size = 128
[    0.356001] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.356001] NetLabel:  unlabeled traffic allowed by default
[    0.356001] AppArmor: AppArmor Filesystem Enabled
[    0.356001] pnp: PnP ACPI: disabled
[    0.356001] PnPBIOS: Scanning system for PnP BIOS support...
[    0.356001] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe0e0
[    0.356001] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbca2, dseg 0x400
[    0.356001] PnPBIOS: 2 nodes reported by PnP BIOS; 2 recorded by driver
[    0.356001] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.356001] pci 0000:00:09.0:   IO window: disabled
[    0.356001] pci 0000:00:09.0:   MEM window: 0x93300000-0x933fffff
[    0.356001] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.356001] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.356001] pci 0000:00:10.0:   IO window: 0x1000-0x1fff
[    0.356001] pci 0000:00:10.0:   MEM window: 0x92000000-0x930fffff
[    0.356001] pci 0000:00:10.0:   PREFETCH window: 0x00000080000000-0x00000091ffffff
[    0.356001] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
[    0.356001] pci 0000:00:15.0:   IO window: disabled
[    0.356001] pci 0000:00:15.0:   MEM window: 0x93200000-0x932fffff
[    0.356001] pci 0000:00:15.0:   PREFETCH window: disabled
[    0.356001] pci 0000:00:16.0: PCI bridge, secondary bus 0000:04
[    0.356001] pci 0000:00:16.0:   IO window: disabled
[    0.356001] pci 0000:00:16.0:   MEM window: 0x93100000-0x931fffff
[    0.356001] pci 0000:00:16.0:   PREFETCH window: disabled
[    0.356001] pci 0000:00:09.0: enabling device (0000 -> 0002)
[    0.356001] pci 0000:00:09.0: setting latency timer to 64
[    0.356001] pci 0000:00:10.0: setting latency timer to 64
[    0.356001] pci 0000:00:15.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    0.356001] pci 0000:00:15.0: setting latency timer to 64
[    0.356001] pci 0000:00:16.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    0.356001] pci 0000:00:16.0: setting latency timer to 64
[    0.356001] bus: 00 index 0 io port: [0x00-0xffff]
[    0.356001] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.356001] bus: 01 index 0 mmio: [0x0-0x0]
[    0.356001] bus: 01 index 1 mmio: [0x93300000-0x933fffff]
[    0.356001] bus: 01 index 2 mmio: [0x0-0x0]
[    0.356001] bus: 01 index 3 io port: [0x00-0xffff]
[    0.356001] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.356001] bus: 02 index 0 io port: [0x1000-0x1fff]
[    0.356001] bus: 02 index 1 mmio: [0x92000000-0x930fffff]
[    0.356001] bus: 02 index 2 mmio: [0x80000000-0x91ffffff]
[    0.356001] bus: 02 index 3 mmio: [0x0-0x0]
[    0.356001] bus: 03 index 0 mmio: [0x0-0x0]
[    0.356001] bus: 03 index 1 mmio: [0x93200000-0x932fffff]
[    0.356001] bus: 03 index 2 mmio: [0x0-0x0]
[    0.356001] bus: 03 index 3 mmio: [0x0-0x0]
[    0.356001] bus: 04 index 0 mmio: [0x0-0x0]
[    0.356001] bus: 04 index 1 mmio: [0x93100000-0x931fffff]
[    0.356001] bus: 04 index 2 mmio: [0x0-0x0]
[    0.356001] bus: 04 index 3 mmio: [0x0-0x0]
[    0.356001] bus: ff index 0 io port: [0x00-0xffff]
[    0.356001] bus: ff index 1 mmio: [0x000000-0xffffffff]
[    0.356001] NET: Registered protocol family 2
[    0.356001] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.356001] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.356001] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.356001] TCP: Hash tables configured (established 131072 bind 65536)
[    0.356001] TCP reno registered
[    0.356001] NET: Registered protocol family 1
[    0.356001] checking if image is initramfs... it is
[    1.132002] Freeing initrd memory: 7372k freed
[    1.132002] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    1.132002] cpufreq: No nForce2 chipset.
[    1.132002] audit: initializing netlink socket (disabled)
[    1.132002] type=2000 audit(1249162673.132:1): initialized
[    1.140003] highmem bounce pool size: 64 pages
[    1.140003] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.144003] VFS: Disk quotas dquot_6.5.1
[    1.144003] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.144003] fuse init (API version 7.10)
[    1.144003] msgmni has been set to 1698
[    1.144003] alg: No test for stdrng (krng)
[    1.144003] io scheduler noop registered
[    1.144003] io scheduler anticipatory registered
[    1.144003] io scheduler deadline registered
[    1.144003] io scheduler cfq registered (default)
[    1.160003] pci 0000:02:00.0: Boot video device
[    1.160003] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    1.160003] pcieport-driver 0000:00:15.0: device [10de:0ac6] has invalid IRQ; check vendor BIOS
[    1.160003] pcieport-driver 0000:00:15.0: found MSI capability
[    1.160003] pcieport-driver 0000:00:15.0: irq 2303 for MSI/MSI-X
[    1.160003] pci_express 0000:00:15.0:pcie00: allocate port service
[    1.160003] pcieport-driver 0000:00:16.0: setting latency timer to 64
[    1.160003] pcieport-driver 0000:00:16.0: device [10de:0ac7] has invalid IRQ; check vendor BIOS
[    1.160003] pcieport-driver 0000:00:16.0: found MSI capability
[    1.160003] pcieport-driver 0000:00:16.0: irq 2302 for MSI/MSI-X
[    1.160003] pci_express 0000:00:16.0:pcie00: allocate port service
[    1.160003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.160003] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.160003] isapnp: Scanning for PnP cards...
[    1.508003] isapnp: No Plug & Play device found
[    1.508003] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.508003] brd: module loaded
[    1.512003] loop: module loaded
[    1.512003] Fixed MDIO Bus: probed
[    1.512003] PPP generic driver version 2.4.2
[    1.512003] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.512003] Driver 'sd' needs updating - please use bus_type methods
[    1.512003] Driver 'sr' needs updating - please use bus_type methods
[    1.512003] ahci 0000:00:0b.0: version 3.0
[    1.512003] ahci 0000:00:0b.0: irq 2301 for MSI/MSI-X
[    1.512003] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    1.512003] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pmp pio slum part 
[    1.512003] ahci 0000:00:0b.0: setting latency timer to 64
[    1.512003] scsi0 : ahci
[    1.512003] scsi1 : ahci
[    1.512003] scsi2 : ahci
[    1.512003] scsi3 : ahci
[    1.512003] scsi4 : ahci
[    1.512003] scsi5 : ahci
[    1.512003] ata1: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484100 irq 2301
[    1.512003] ata2: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484180 irq 2301
[    1.512003] ata3: DUMMY
[    1.512003] ata4: DUMMY
[    1.512003] ata5: DUMMY
[    1.512003] ata6: DUMMY
[    1.996004] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.044004] ata1.00: ATA-8: ST9500325AS, 0001SDM1, max UDMA/133
[    2.044004] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.048004] ata1.00: configured for UDMA/133
[    2.952006] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.952006] ata2.00: ATAPI: MATSHITADVD-R   UJ867A, KK07, max UDMA/66, ATAPI AN
[    2.956006] ata2.00: configured for UDMA/66
[    2.972006] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0001 PQ: 0 ANSI: 5
[    2.972006] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.972006] sd 0:0:0:0: [sda] Write Protect is off
[    2.972006] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.972006] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.972006] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.972006] sd 0:0:0:0: [sda] Write Protect is off
[    2.972006] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.972006] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.972006]  sda: sda1 sda2 sda3 sda4 sda5
[    3.060006] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.060006] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.064006] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-R   UJ867A   KK07 PQ: 0 ANSI: 5
[    3.068006] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.068006] Uniform CD-ROM driver Revision: 3.20
[    3.068006] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.068006] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.068006] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.068006] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.068006] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.068006] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    3.068006] ehci_hcd 0000:00:04.1: debug port 1
[    3.068006] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    3.068006] ehci_hcd 0000:00:04.1: irq 10, io mem 0x93489200
[    3.080006] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.080006] usb usb1: configuration #1 chosen from 1 choice
[    3.080006] hub 1-0:1.0: USB hub found
[    3.080006] hub 1-0:1.0: 7 ports detected
[    3.080006] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    3.080006] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    3.080006] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    3.080006] ehci_hcd 0000:00:06.1: debug port 1
[    3.080006] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    3.080006] ehci_hcd 0000:00:06.1: irq 5, io mem 0x93489100
[    3.092006] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    3.092006] usb usb2: configuration #1 chosen from 1 choice
[    3.092006] hub 2-0:1.0: USB hub found
[    3.092006] hub 2-0:1.0: 5 ports detected
[    3.092006] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.092006] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.092006] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.092006] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    3.092006] ohci_hcd 0000:00:04.0: irq 11, io mem 0x93488000
[    3.148006] usb usb3: configuration #1 chosen from 1 choice
[    3.148006] hub 3-0:1.0: USB hub found
[    3.148006] hub 3-0:1.0: 7 ports detected
[    3.148006] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    3.148006] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    3.148006] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    3.148006] ohci_hcd 0000:00:06.0: irq 7, io mem 0x93487000
[    3.204006] usb usb4: configuration #1 chosen from 1 choice
[    3.204006] hub 4-0:1.0: USB hub found
[    3.204006] hub 4-0:1.0: 5 ports detected
[    3.204006] uhci_hcd: USB Universal Host Controller Interface driver
[    3.204006] PNP: No PS/2 controller found. Probing ports directly.
[    3.204006] i8042.c: No controller found.
[    3.204006] mice: PS/2 mouse device common for all mice
[    3.204006] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    3.204006] rtc0: alarms up to one day, 114 bytes nvram
[    3.204006] device-mapper: uevent: version 1.0.3
[    3.204006] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.204006] device-mapper: multipath: version 1.0.5 loaded
[    3.204006] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.204006] EISA: Probing bus 0 at eisa.0
[    3.204006] Cannot allocate resource for EISA slot 1
[    3.204006] Cannot allocate resource for EISA slot 2
[    3.204006] EISA: Detected 0 cards.
[    3.204006] cpuidle: using governor ladder
[    3.204006] cpuidle: using governor menu
[    3.208006] TCP cubic registered
[    3.208006] NET: Registered protocol family 10
[    3.208006] lo: Disabled Privacy Extensions
[    3.208006] NET: Registered protocol family 17
[    3.208006] Bluetooth: L2CAP ver 2.11
[    3.208006] Bluetooth: L2CAP socket layer initialized
[    3.208006] Bluetooth: SCO (Voice Link) ver 0.6
[    3.208006] Bluetooth: SCO socket layer initialized
[    3.208006] Bluetooth: RFCOMM socket layer initialized
[    3.208006] Bluetooth: RFCOMM TTY layer initialized
[    3.208006] Bluetooth: RFCOMM ver 1.10
[    3.208006] IO APIC resources could be not be allocated.
[    3.208006] Using IPI No-Shortcut mode
[    3.208006] registered taskstats version 1
[    3.208006]   Magic number: 5:894:650
[    3.208006] scsi_host host4: hash matches
[    3.208006] scsi host4: hash matches
[    3.208006] rtc_cmos rtc_cmos: setting system clock to 2009-08-01 21:37:55 UTC (1249162675)
[    3.208006] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.208006] EDD information not available.
[    3.208006] Freeing unused kernel memory: 532k freed
[    3.208006] Write protecting the kernel text: 4116k
[    3.208006] Write protecting the kernel read-only data: 1524k
[    3.392006] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    3.524006] usb 1-4: configuration #1 chosen from 1 choice
[    3.848007] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.848007] forcedeth 0000:00:0a.0: setting latency timer to 64
[    3.848007] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:23:df:95:a1:a2
[    3.848007] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    4.084007] ohci1394 0000:04:00.0: setting latency timer to 64
[    4.136007] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[7]  MMIO=[93100000-931007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.148007] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    4.352007] usb 4-1: configuration #1 chosen from 1 choice
[    4.356007] hub 4-1:1.0: USB hub found
[    4.356007] hub 4-1:1.0: 3 ports detected
[    4.588007] PM: Starting manual resume from disk
[    4.588007] PM: Resume from partition 8:5
[    4.588007] PM: Checking hibernation image.
[    4.588007] PM: Resume from disk failed.
[    4.624007] kjournald starting.  Commit interval 5 seconds
[    4.624007] EXT3-fs: mounted filesystem with ordered data mode.
[    4.692007] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    4.904007] usb 3-5: configuration #1 chosen from 1 choice
[    5.216007] usb 3-6: new full speed USB device using ohci_hcd and address 3
[    5.436007] usb 3-6: configuration #1 chosen from 1 choice
[    5.460007] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0023dffffe95a1a2]
[    5.528007] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
[    5.652007] usb 4-1.1: configuration #1 chosen from 1 choice
[   10.280007] udev: starting version 141
[   10.468007] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.544007] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.544007] usbcore: registered new interface driver btusb
[   10.548007] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   10.568007] appletouch: Geyser mode initialized.
[   10.568007] input: appletouch as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.1/input/input2
[   10.576007] Linux video capture interface: v2.00
[   10.592007] ieee80211_crypt: registered algorithm 'NULL'
[   10.592007] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.596007] usbcore: registered new interface driver appletouch
[   10.596007] wl 0000:03:00.0: setting latency timer to 64
[   10.620007] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8503)
[   10.620007] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   10.624007] input: Built-in iSight as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.0/input/input3
[   10.640007] usbcore: registered new interface driver uvcvideo
[   10.640007] USB Video Class driver (v0.1.0)
[   10.680007] input: Apple Mac mini infrared remote control driver as /devices/pci0000:00/0000:00:04.0/usb3/3-5/3-5:1.0/input/input4
[   10.700007] ieee80211_crypt: registered algorithm 'TKIP'
[   10.704007] usbcore: registered new interface driver appleir
[   10.704007] appleir: v1.1:USB Apple MacMini IR Receiver driver
[   10.704007] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.91.9
[   11.176007] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.568007] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.232007] lp: driver loaded but no devices found
[   12.336007] applesmc: Apple MacBook 5 detected:
[   12.336007] applesmc:  - Model with accelerometer
[   12.336007] applesmc:  - Model with light sensors and backlight
[   12.336007] applesmc:  - Model with 14 temperature sensors
[   12.396007] applesmc: device successfully initialized (0xe0, 0x00).
[   12.396007] applesmc: device successfully initialized.
[   12.396007] applesmc: 1 fans found.
[   12.400007] input: applesmc as /devices/platform/applesmc.768/input/input5
[   12.412007] Registered led device: smc::kbd_backlight
[   12.412007] applesmc: driver successfully loaded.
[   12.420007] usbcore: registered new interface driver bcm5974
[   12.444007] usbcore: registered new interface driver hiddev
[   12.444007] usbcore: registered new interface driver usbhid
[   12.444007] usbhid: v2.6:USB HID core driver
[   12.508007] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input6
[   12.524007] Adding 4195304k swap on /dev/sda5.  Priority:-1 extents:1 across:4195304k
[   12.536007] apple 0003:05AC:0229.0001: input,hidraw0: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[   12.544007] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input7
[   12.560007] apple 0003:05AC:0229.0002: input,hidraw1: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input2
[   13.076007] EXT3 FS on sda4, internal journal
[   14.200007] type=1505 audit(1249162686.492:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1906
[   14.252007] type=1505 audit(1249162686.544:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1910
[   14.252007] type=1505 audit(1249162686.544:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1910
[   14.252007] type=1505 audit(1249162686.544:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1910
[   14.252007] type=1505 audit(1249162686.544:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1910
[   14.396007] type=1505 audit(1249162686.688:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1915
[   14.396007] type=1505 audit(1249162686.688:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1915
[   14.428007] type=1505 audit(1249162686.720:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1919
[   17.580007] input: Mouseemu virtual keyboard as /devices/virtual/input/input8
[   17.608007] input: Mouseemu virtual mouse as /devices/virtual/input/input9
[   17.652007] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.652007] Bluetooth: BNEP filters: protocol multicast
[   17.684007] Bridge firewalling registered
[   19.176007] ppdev: user-space parallel port driver
[   20.600007] Linux agpgart interface v0.103
[   21.124007] nvidia 0000:02:00.0: setting latency timer to 64
[   21.124007] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.29  Thu Jul 23 05:09:54 PDT 2009
[   21.216007] NVRM: failed to register with the ACPI subsystem!
[   21.220007] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread F63C9920 could not acquire Mutex [1] [20080926]
[   23.144007] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   23.144007] eth0: no link during initialization.
[   23.144007] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.060007] eth1: no IPv6 routers present
[   59.816007] Corrupted low memory at c000c194 (c194 phys) = 000000a0
[   59.816007] ------------[ cut here ]------------
[   59.816007] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
[   59.816007] Memory corruption detected in low memory
[   59.816007] Modules linked in: nvidia(P) agpgart binfmt_misc ppdev bridge stp bnep uinput hid_apple usbhid bcm5974 applesmc led_class input_polldev coretemp lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi joydev snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore ieee80211_crypt_tkip snd_page_alloc appleir uvcvideo wl(P) ieee80211_crypt compat_ioctl32 videodev appletouch pcspkr btusb v4l1_compat shpchp ohci1394 ieee1394 forcedeth fbcon tileblit font bitblit softcursor
[   59.816007] Pid: 3124, comm: gconfd-2 Tainted: P           2.6.28-14-generic #47-Ubuntu
[   59.816007] Call Trace:
[   59.816007]  [<c0139aa0>] warn_slowpath+0x60/0x80
[   59.816007]  [<c013a2e9>] ? release_console_sem+0x1c9/0x200
[   59.816007]  [<c04fde46>] ? printk+0x18/0x1a
[   59.816007]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
[   59.816007]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
[   59.816007]  [<c0143af0>] run_timer_softirq+0x130/0x200
[   59.816007]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
[   59.816007]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
[   59.816007]  [<c013f197>] __do_softirq+0x97/0x170
[   59.816007]  [<c0143f64>] ? update_process_times+0x54/0x70
[   59.816007]  [<c013f2cd>] do_softirq+0x5d/0x60
[   59.816007]  [<c013f445>] irq_exit+0x55/0x90
[   59.816007]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
[   59.816007]  [<c013eaa5>] ? sys_time+0x15/0x40
[   59.816007]  [<c0105318>] apic_timer_interrupt+0x28/0x30
[   59.816007] ---[ end trace 4fef7631968915a5 ]---
[  342.136007] NVRM: failed to unregister from the ACPI subsystem!
[  343.280007] NVRM: failed to register with the ACPI subsystem!
[  343.284007] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread F53A3240 could not acquire Mutex [1] [20080926]

```

---

### Post by ebash on 2009-08-09
Is all hardware working for you?

I've installed ubuntu 9.04 on a MacBook 5,2 and it's nothing but troubles. 

The sound card doesn't work, it's detected but muted and playing with all volume controls and switches has no effect.

I can't use the nvidia drivers as they tend to make graphical quirks and freeze the laptop, besides the random freezes they work well and compiz was running quite nice. I'm now using the default drivers but they give me a weird resolution 1280x720.

The laptop won't boot with the default kernel parameters. I had to add maxcpus=1 to the command line. This disables the second code but allows me to use the laptop.

---

### Post by CellPhoneDude on 2009-08-09
> **ebash said:**
> Is all hardware working for you?

I've installed ubuntu 9.04 on a MacBook 5,2 and it's nothing but troubles. 

The sound card doesn't work, it's detected but muted and playing with all volume controls and switches has no effect.

I can't use the nvidia drivers as they tend to make graphical quirks and freeze the laptop, besides the random freezes they work well and compiz was running quite nice. I'm now using the default drivers but they give me a weird resolution 1280x720.

The laptop won't boot with the default kernel parameters. I had to add maxcpus=1 to the command line. This disables the second code but allows me to use the laptop.

Ya you have to do some stuff before sound works (I had it working before then I reinstalled haven't fixed it again) I actually followed a lot of the documentation for installing on a 5-1 macbook. I downloaded and installed drivers from the nvidia site185.xx was the version number I even get the Nvidia splash screen. as well as it extends to my external monitor so thats nice first laptop I've got that to work on.

As far as booting and installing goes all I had to to was turn acpi=off on from the installer menu (F6) and it worked great however because it's off all the power management stuff is still broken. I also noticed that like the 5-1 the 5-2 is susceptible to the ethernet port also drawing a lot of power..

---

### Post by ebash on 2009-08-09
> **CellPhoneDude said:**
> Ya you have to do some stuff before sound works (I had it working before then I reinstalled haven't fixed it again) I actually followed a lot of the documentation for installing on a 5-1 macbook.

Good to know that there's hope for the sound system. If you find out what to do please post it here.

> **CellPhoneDude said:**
> 
I downloaded and installed drivers from the nvidia site185.xx was the version number I even get the Nvidia splash screen. as well as it extends to my external monitor so thats nice first laptop I've got that to work on.

I've also just installed the nvidia 185 drivers that I downloaded from their web site and so far all seems good. X didn't freeze yet and compiz is working like a charm.

> **CellPhoneDude said:**
> 
As far as booting and installing goes all I had to to was turn acpi=off on from the installer menu (F6) and it worked great however because it's off all the power management stuff is still broken.

At first I was also using acpi=off but this turns off a lot of nice functionalities: no battery monitoring, shutdown doesn't halt the computer (need to press the button), can't shutdown the laptop by pressing the hardware button, etc.

I found out that passing maxcpus=1 was a better alternative as it doesn't disable ACPI and allows the macbook to boot. Sure the computer starts with one core but this is not avoidable at the moment.

---

### Post by CellPhoneDude on 2009-08-09
I used the sound fix from here...
[https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)

As far as shutdown and CPU core's theirs a fix in their that works on the 5-1's which are essentially the same as the 5-2's theres a fix for getting both cores to work as well as the REPO to install a power management app (I think) that replaces the built-in ACPI controller with one thats compatible with the mac.

In the link up there theirs a suggestion on how to check what's pulling the most power I'd be intrested to know if using ure install method made any difference as to how much power the ethernet port pulls... 

I really would like to help get a guied together of what works on 5-2 and how to get it to work but like I said before I'm super newb...

---

