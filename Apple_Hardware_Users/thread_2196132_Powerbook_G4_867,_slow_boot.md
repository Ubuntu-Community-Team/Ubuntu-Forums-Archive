---
title: "Powerbook G4 867, slow boot"
date: 2013-12-28
forum: Apple Hardware Users
---

### Post by theodore-r on 2013-12-28
I'm trying to find the cause of slow booting on a 12" powerbook 867.

I've recently installed 12.04 standard, though I'm currently running the lubuntu package. 
The computer seems to run fine once booted, but the boot process takes almost 10 minutes. It is a similar long delay when shutting down, or logging out.

Here is my dmsg
```

[    0.000000] Using PowerMac machine description
[    0.000000] Cannot reserve gpages without hugetlb enabled
[    0.000000] Total memory = 1152MB; using 4096kB for hash table (at c7c00000)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-57-powerpc-smp (buildd@sagari) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:35:43 UTC 2013 (Ubuntu 3.2.0-57.87-powerpc-smp 3.2.52)
[    0.000000] Found initrd at 0xc1800000:0xc2628000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerBook G4 12"
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] CPU maps initialized for 1 thread per core
[    0.000000]  (thread shift is 0)
[    0.000000] bootconsole [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=950, gen1=951
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x48000000, Total RAM: 0x48000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00030000
[    0.000000]   Normal   empty
[    0.000000]   HighMem  0x00030000 -> 0x00048000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00048000
[    0.000000] On node 0 totalpages: 294912
[    0.000000] free_area_init_node: node 0, pgdat c093ff40, node_mem_map c0adb000
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   HighMem zone: 768 pages used for memmap
[    0.000000]   HighMem zone: 97536 pages, LIFO batch:31
[    0.000000] PERCPU: Embedded 8 pages/cpu @c13e2000 s11424 r8192 d13152 u32768
[    0.000000] pcpu-alloc: s11424 r8192 d13152 u32768 alloc=8*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 292608
[    0.000000] Kernel command line: root=UUID=d99e8159-529c-4282-89a3-a7518c05bf7d ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] allocated 4718592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] High memory: 393216k
[    0.000000] Memory: 1134908k/1179648k available (9192k kernel code, 44740k reserved, 348k data, 1522k bss, 408k init)
[    0.000000] Kernel virtual memory layout:
[    0.000000]   * 0xfff9f000..0xfffff000  : fixmap
[    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
[    0.000000]   * 0xfdf32000..0xff800000  : early ioremap
[    0.000000]   * 0xf1000000..0xfdf32000  : vmalloc & ioremap
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:512 nr_irqs:512 16
[    0.000000] mpic: Resetting
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 1 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 33.280357 MHz
[    0.000000] time_init: processor frequency   = 533.333332 MHz
[    0.000000] clocksource: timebase mult[7830e69] shift[22] registered
[    0.000000] clockevent: decrementer mult[8850fbc] shift[32] cpu[0]
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled, bootconsole disabled
[    0.000501] pid_max: default: 32768 minimum: 301
[    0.000637] Security Framework initialized
[    0.000770] AppArmor: AppArmor initialized
[    0.000783] Yama: becoming mindful.
[    0.000892] Mount-cache hash table entries: 512
[    0.001769] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.008200] Initializing cgroup subsys cpuacct
[    0.008263] Initializing cgroup subsys memory
[    0.008311] Initializing cgroup subsys devices
[    0.008326] Initializing cgroup subsys freezer
[    0.008340] Initializing cgroup subsys blkio
[    0.008378] Initializing cgroup subsys perf_event
[    0.008510] ftrace: allocating 22901 entries in 68 pages
[    0.030806] PowerMac SMP probe found 1 cpus
[    0.030829] MPC7450 family performance monitor hardware support registered
[    0.031823] Brought up 1 CPUs
[    0.032813] devtmpfs: initialized
[    0.033193] EVM: security.selinux
[    0.033203] EVM: security.SMACK64
[    0.033212] EVM: security.capability
[    0.037845] print_constraints: dummy: 
[    0.038138] NET: Registered protocol family 16
[    0.039532] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.039554]  channel 0 bus <multibus>
[    0.039578]  channel 1 bus <multibus>
[    0.039720] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.039740]  channel 0 bus <multibus>
[    0.039769] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[    0.039783]  channel 1 bus <multibus>
[    0.039794]  channel 2 bus <multibus>
[    0.040375] PCI: Probing PCI hardware
[    0.040635] pci 0000:00:0b.0: [106b:0034] type 0 class 0x000600
[    0.040794] pci 0000:00:10.0: [10de:0179] type 0 class 0x000300
[    0.040834] pci 0000:00:10.0: reg 10: [mem 0x91000000-0x91ffffff]
[    0.040858] pci 0000:00:10.0: reg 14: [mem 0x94000000-0x97ffffff pref]
[    0.040882] pci 0000:00:10.0: reg 18: [mem 0x00000000-0x0007ffff pref]
[    0.040931] pci 0000:00:10.0: reg 30: [mem 0x90000000-0x9001ffff pref]
[    0.041584] pci 0001:10:0b.0: [106b:0035] type 0 class 0x000600
[    0.041713] pci 0001:10:12.0: [14e4:4320] type 0 class 0x000280
[    0.041749] pci 0001:10:12.0: reg 10: [mem 0x80084000-0x80085fff]
[    0.041858] pci 0001:10:12.0: supports D1 D2
[    0.041872] pci 0001:10:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.041891] pci 0001:10:12.0: PME# disabled
[    0.041942] pci 0001:10:17.0: [106b:003e] type 0 class 0x00ff00
[    0.041971] pci 0001:10:17.0: reg 10: [mem 0x80000000-0x8007ffff]
[    0.042086] pci 0001:10:18.0: [106b:003f] type 0 class 0x000c03
[    0.042116] pci 0001:10:18.0: reg 10: [mem 0x80082000-0x80082fff]
[    0.042250] pci 0001:10:19.0: [106b:003f] type 0 class 0x000c03
[    0.042281] pci 0001:10:19.0: reg 10: [mem 0x80081000-0x80081fff]
[    0.042400] pci 0001:10:1a.0: [106b:003f] type 0 class 0x000c03
[    0.042431] pci 0001:10:1a.0: reg 10: [mem 0x80080000-0x80080fff]
[    0.043832] pci 0002:20:0b.0: [106b:0036] type 0 class 0x000600
[    0.043933] pci 0002:20:0d.0: [106b:003b] type 0 class 0x00ff00
[    0.043961] pci 0002:20:0d.0: reg 10: [mem 0xf5004000-0xf5007fff]
[    0.044067] pci 0002:20:0e.0: [106b:0031] type 0 class 0x000c00
[    0.044099] pci 0002:20:0e.0: reg 10: [mem 0xf5000000-0xf5000fff]
[    0.044196] pci 0002:20:0e.0: supports D1 D2
[    0.044209] pci 0002:20:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.044226] pci 0002:20:0e.0: PME# disabled
[    0.044269] pci 0002:20:0f.0: [106b:0032] type 0 class 0x000200
[    0.044297] pci 0002:20:0f.0: reg 10: [mem 0xf5200000-0xf53fffff]
[    0.044362] pci 0002:20:0f.0: reg 30: [mem 0xf5100000-0xf51fffff pref]
[    0.045393] PCI: max bus depth: 0 pci_try_num: 1
[    0.045425] pci 0000:00:10.0: BAR 2: assigned [mem 0xf1000000-0xf107ffff pref]
[    0.045451] pci 0000:00:10.0: BAR 2: set to [mem 0xf1000000-0xf107ffff pref] (PCI address [0xf1000000-0xf107ffff])
[    0.045481] pci_bus 0000:00: resource 0 [io  0x802000-0x1001fff]
[    0.045496] pci_bus 0000:00: resource 1 [mem 0xf1000000-0xf1ffffff]
[    0.045512] pci_bus 0000:00: resource 2 [mem 0x90000000-0x9fffffff]
[    0.045527] pci_bus 0001:10: resource 0 [io  0x0000-0x7fffff]
[    0.045542] pci_bus 0001:10: resource 1 [mem 0xf3000000-0xf3ffffff]
[    0.045557] pci_bus 0001:10: resource 2 [mem 0x80000000-0x8fffffff]
[    0.045573] pci_bus 0002:20: resource 0 [io  0xff7fe000-0xffffdfff]
[    0.045588] pci_bus 0002:20: resource 1 [mem 0xf5000000-0xf5ffffff]
[    0.051926] bio: create slab <bio-0> at 0
[    0.053093] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
[    0.053163] vgaarb: loaded
[    0.053172] vgaarb: bridge control possible 0000:00:10.0
[    0.053956] i2c-core: driver [aat2870] using legacy suspend method
[    0.053970] i2c-core: driver [aat2870] using legacy resume method
[    0.054473] SCSI subsystem initialized
[    0.054841] libata version 3.00 loaded.
[    0.055153] usbcore: registered new interface driver usbfs
[    0.055226] usbcore: registered new interface driver hub
[    0.055412] usbcore: registered new device driver usb
[    0.056603] NetLabel: Initializing
[    0.056619] NetLabel:  domain hash size = 128
[    0.056629] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.056694] NetLabel:  unlabeled traffic allowed by default
[    0.057012] Switching to clocksource timebase
[    0.078179] AppArmor: AppArmor Filesystem Enabled
[    0.089584] NET: Registered protocol family 2
[    0.089964] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.091565] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.094814] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.096371] TCP: Hash tables configured (established 131072 bind 65536)
[    0.096386] TCP reno registered
[    0.096406] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.096494] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.097051] NET: Registered protocol family 1
[    0.097319] pci 0001:10:18.0: enabling device (0000 -> 0002)
[    0.153169] pci 0001:10:19.0: enabling device (0000 -> 0002)
[    0.209117] pci 0001:10:1a.0: enabling device (0000 -> 0002)
[    0.265131] PCI: CLS mismatch (32 != 1020), using 32 bytes
[    0.265725] Thermal assist unit not available
[    0.265924] Registering PowerMac CPU frequency driver
[    0.265938] Low: 533 Mhz, High: 867 Mhz, Boot: 533 Mhz
[    0.267346] audit: initializing netlink socket (disabled)
[    0.267396] type=2000 audit(1388052248.243:1): initialized
[    0.359454] Trying to unpack rootfs image as initramfs...
[    0.459891] highmem bounce pool size: 64 pages
[    0.477848] VFS: Disk quotas dquot_6.5.2
[    0.478155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.480339] fuse init (API version 7.17)
[    0.480786] msgmni has been set to 1450
[    0.497456] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.497681] io scheduler noop registered
[    0.497690] io scheduler deadline registered
[    0.497749] io scheduler cfq registered (default)
[    0.498135] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.498168] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.498761] Using unsupported 1024x768 NVDA,Display-A at 94004000, depth=8, pitch=1024
[    0.511810] Console: switching to colour frame buffer device 128x48
[    0.524174] fb0: Open Firmware frame buffer device on /pci@f0000000/NVDA,Parent@10/NVDA,Display-A@0
[    0.550948] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[    0.550986] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[    0.551126] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[    0.551456] Generic non-volatile memory driver v1.1
[    0.551560] Linux agpgart interface v0.103
[    0.560455] brd: module loaded
[    0.568302] loop: module loaded
[    0.568643] MacIO PCI driver attached to Intrepid chipset
[    0.578736] pata-pci-macio 0002:20:0d.0: enabling device (0000 -> 0002)
[    0.579110] adb: starting probe task...
[    0.593637] pata-pci-macio 0002:20:0d.0: Activating pata-macio chipset UniNorth ATA-6, Apple bus ID 3
[    0.601909] scsi0 : pata_macio
[    0.602264] ata1: PATA max UDMA/100 irq 39
[    0.766017] ata1.00: ATA-6: WDC WD800VE-00HDT0, 09.07D09, max UDMA/100
[    0.766035] ata1.00: 156301488 sectors, multi 16: LBA 
[    0.774177] ata1.00: configured for UDMA/100
[    0.774787] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800VE-00HD 09.0 PQ: 0 ANSI: 5
[    0.775643] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.776060] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.776278] sd 0:0:0:0: [sda] Write Protect is off
[    0.776289] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.776375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.835595] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[    0.842286] ADB keyboard at 2, handler 1
[    0.842321] Detected ADB keyboard, type ANSI.
[    0.842561] input: ADB keyboard as /devices/virtual/input/input0
[    0.842753] input: ADB Powerbook buttons as /devices/virtual/input/input1
[    0.858357] ADB mouse at 3, handler set to 4 (trackpad)
[    0.917910] input: ADB mouse as /devices/virtual/input/input2
[    0.917937] adb: finished probe task...
[    1.302554] Freeing initrd memory: 14496k freed
[    1.621104] pata-macio 0.00020000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 0
[    1.621916] scsi1 : pata_macio
[    1.622102] ata2: PATA max MWDMA2 irq 24
[    1.623364] Fixed MDIO Bus: probed
[    1.623404] tun: Universal TUN/TAP device driver, 1.6
[    1.623411] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.623688] PPP generic driver version 2.4.2
[    1.624133] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.624301] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.624422] ohci_hcd 0001:10:18.0: OHCI Host Controller
[    1.624683] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[    1.624784] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80082000
[    1.697624] hub 1-0:1.0: USB hub found
[    1.697648] hub 1-0:1.0: 2 ports detected
[    1.697930] ohci_hcd 0001:10:19.0: OHCI Host Controller
[    1.698148] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[    1.698227] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80081000
[    1.773484] hub 2-0:1.0: USB hub found
[    1.773507] hub 2-0:1.0: 2 ports detected
[    1.773797] ohci_hcd 0001:10:1a.0: OHCI Host Controller
[    1.773998] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 3
[    1.774071] ohci_hcd 0001:10:1a.0: irq 29, io mem 0x80080000
[    1.785389] ata2.00: ATAPI: MATSHITACD-RW  CW-8122, BA21, max UDMA/33
[    1.801366] ata2.00: configured for MWDMA2
[    1.849547] hub 3-0:1.0: USB hub found
[    1.849573] hub 3-0:1.0: 2 ports detected
[    1.849838] uhci_hcd: USB Universal Host Controller Interface driver
[    1.850162] usbcore: registered new interface driver libusual
[    1.850831] mousedev: PS/2 mouse device common for all mice
[    1.851461] PowerMac i2c bus pmu 2 registered
[    1.851583] PowerMac i2c bus pmu 1 registered
[    1.851685] PowerMac i2c bus mac-io 0 registered
[    1.851782] PowerMac i2c bus uni-n 1 registered
[    1.851941] PowerMac i2c bus uni-n 0 registered
[    1.852313] device-mapper: uevent: version 1.0.3
[    1.852646] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.853761] TCP cubic registered
[    1.854234] NET: Registered protocol family 10
[    1.856463] NET: Registered protocol family 17
[    1.856488] Registering the dns_resolver key type
[    1.857139] registered taskstats version 1
[    1.894945] input: PMU as /devices/virtual/input/input3
[    1.895235] Registered led device: pmu-led::front
[    1.895249] /build/buildd/linux-3.2.0/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    2.033091] usb 1-2: new full-speed USB device number 2 using ohci_hcd
[    6.000010]  sda: [mac] sda1 sda2 sda3 sda4 sda5
[    6.001795] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.004035] scsi 1:0:0:0: CD-ROM            MATSHITA CD-RW  CW-8122   BA21 PQ: 0 ANSI: 5
[    6.005698] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.005713] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.006217] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.006649] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.007777] Freeing unused kernel memory: 408k freed
[    6.124286] udevd[84]: starting version 175
[    6.685742] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
[    6.685811] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    6.685825] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    6.685838] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    6.685851] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    6.685863] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    6.741497] ssb: Sonics Silicon Backplane found on PCI device 0001:10:12.0
[    6.815369] input: HID 05ac:1000 as /devices/pci0001:10/0001:10:18.0/usb1/1-2/1-2:1.0/input/input4
[    6.823033] generic-usb 0003:05AC:1000.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0001:10:18.0-2/input0
[    6.846425] input: HID 05ac:1000 as /devices/pci0001:10/0001:10:18.0/usb1/1-2/1-2:1.1/input/input5
[    6.846987] generic-usb 0003:05AC:1000.0002: input,hidraw1: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0001:10:18.0-2/input1
[    6.847071] usbcore: registered new interface driver usbhid
[    6.847079] usbhid: USB HID core driver
[    6.854381] sungem.c:v1.0 David S. Miller <davem@redhat.com>
[    6.856587] gem 0002:20:0f.0: eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:9b:3f:1a
[    6.874930] firewire_ohci 0002:20:0e.0: enabling device (0000 -> 0002)
[    6.929322] firewire_ohci: Added fw-ohci device 0002:20:0e.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
[    7.429484] firewire_core: created device fw0: GUID 000a95fffe9b3f1a, S400
[   12.215152] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   30.385319] Adding 3228808k swap on /dev/sda4.  Priority:-1 extents:1 across:3228808k 
[   30.490589] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.585734] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   30.607532] udevd[288]: starting version 175
[   30.897314] apm_emu: PMU APM Emulation initialized.
[   31.638099] agpgart-uninorth 0000:00:0b.0: Apple UniNorth 2 chipset
[   31.639506] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[   31.742227] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
[   32.453402] i2c i2c-0: PMac Keywest Audio: attach_adapter method is deprecated
[   32.453418] i2c i2c-0: Please use another way to instantiate your i2c_client
[   32.453430] i2c i2c-1: PMac Keywest Audio: attach_adapter method is deprecated
[   32.453439] i2c i2c-1: Please use another way to instantiate your i2c_client
[   32.453449] i2c i2c-2: PMac Keywest Audio: attach_adapter method is deprecated
[   32.453458] i2c i2c-2: Please use another way to instantiate your i2c_client
[   32.453611] i2c i2c-3: PMac Keywest Audio: attach_adapter method is deprecated
[   32.453622] i2c i2c-3: Please use another way to instantiate your i2c_client
[   32.453632] i2c i2c-4: PMac Keywest Audio: attach_adapter method is deprecated
[   32.453641] i2c i2c-4: Please use another way to instantiate your i2c_client
[   32.504202] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input6
[   32.550548] lp: driver loaded but no devices found
[   32.597653] Bluetooth: Core ver 2.16
[   32.605183] NET: Registered protocol family 31
[   32.605202] Bluetooth: HCI device and connection manager initialized
[   32.605216] Bluetooth: HCI socket layer initialized
[   32.605225] Bluetooth: L2CAP socket layer initialized
[   32.605278] Bluetooth: SCO socket layer initialized
[   32.683150] ppdev: user-space parallel port driver
[   32.737460] Bluetooth: RFCOMM TTY layer initialized
[   32.737489] Bluetooth: RFCOMM socket layer initialized
[   32.737497] Bluetooth: RFCOMM ver 1.11
[   33.053183] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.053198] Bluetooth: BNEP filters: protocol multicast
[   33.067202] cfg80211: Calling CRDA to update world regulatory domain
[   33.096715] type=1400 audit(1388052281.068:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=482 comm="apparmor_parser"
[   33.122954] type=1400 audit(1388052281.096:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=482 comm="apparmor_parser"
[   33.656247] [drm] Initialized drm 1.1.0 20060810
[   34.084420] usb 1-2: USB disconnect, device number 2
[   34.100322] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -62
[   34.147681] type=1400 audit(1388052282.120:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=557 comm="apparmor_parser"
[   34.151650] type=1400 audit(1388052282.124:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=557 comm="apparmor_parser"
[   34.152508] type=1400 audit(1388052282.124:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=557 comm="apparmor_parser"
[   34.209736] type=1400 audit(1388052282.184:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=560 comm="apparmor_parser"
[   34.348192] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[   34.489223] usb 1-2: new full-speed USB device number 3 using ohci_hcd
[   34.959636] [drm] nouveau 0000:00:10.0: Detected an NV10 generation card (0x017900a5)
[   34.959664] checking generic (94004000 c0000) vs hw (94000000 4000000)
[   34.959673] fb: conflicting fb hw usage nouveaufb vs OFfb NVDA,Displ - removing generic driver
[   34.959813] Console: switching to colour dummy device 80x25
[   34.997839] b43-phy0: Broadcom 4306 WLAN found (core revision 5)

[   35.025949] [drm] nouveau 0000:00:10.0: OF bios successfully copied (5017 bytes)
[   35.026094] [drm] nouveau 0000:00:10.0: Attempting to load BIOS image from PRAMIN
[   35.098508] [drm] nouveau 0000:00:10.0: ... BIOS checksum invalid
[   35.098522] [drm] nouveau 0000:00:10.0: Attempting to load BIOS image from PROM
[   35.098536] [drm] nouveau 0000:00:10.0: ... BIOS signature not found
[   35.098543] [drm] nouveau 0000:00:10.0: Attempting to load BIOS image from PCIROM

[   35.113684] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   35.113703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113714] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   35.113725] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113735] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   35.113747] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113757] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   35.113768] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113778] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   35.113789] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113799] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   35.113811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113820] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   35.113832] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113842] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   35.113853] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113863] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   35.113874] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113884] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   35.113896] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113905] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   35.113917] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113927] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   35.113938] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113948] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   35.113959] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   35.113969] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   35.113981] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   35.183930] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'

[   35.205923] [drm] nouveau 0000:00:10.0: ... BIOS signature not found
[   35.205944] [drm] nouveau 0000:00:10.0: Attempting to load BIOS image from ACPI
[   35.205952] [drm] nouveau 0000:00:10.0: ... BIOS signature not found
[   35.205961] [drm] nouveau 0000:00:10.0: Using BIOS image from PRAMIN
[   35.278984] [drm] nouveau 0000:00:10.0: BMP BIOS found
[   35.278999] [drm] nouveau 0000:00:10.0: BMP version 5.21
[   35.279011] [drm] nouveau 0000:00:10.0: Bios version 04.17.00.55
[   35.279024] [drm] nouveau 0000:00:10.0: Found Display Configuration Block version 2.0
[   35.279037] [drm] nouveau 0000:00:10.0: Raw DCB entry 0: 04000223 00000004
[   35.279050] [drm] nouveau 0000:00:10.0: Raw DCB entry 1: 02010100 11b04fb0
[   35.279060] [drm] nouveau 0000:00:10.0: Raw DCB entry 2: 02010101 11b00703
[   35.279130] [drm] nouveau 0000:00:10.0: Loading NV17 power sequencing microcode
[   35.279145] [drm] nouveau 0000:00:10.0: Parsing VBIOS init table 0 at offset 0x060F
[   35.279228] [drm] nouveau 0000:00:10.0: Parsing VBIOS init table 1 at offset 0x0737
[   35.293391] [drm] nouveau 0000:00:10.0: Parsing VBIOS init table 2 at offset 0x0CC6
[   35.298599] Registered led device: b43-phy0::tx
[   35.309247] Registered led device: b43-phy0::rx
[   35.312036] Registered led device: b43-phy0::radio
[   35.312262] Broadcom 43xx driver loaded [ Features: PNL ]
[   35.489501] [drm] nouveau 0000:00:10.0: Parsing VBIOS init table 3 at offset 0x0E4D
[   35.489539] [drm] nouveau 0000:00:10.0: Parsing VBIOS init table 4 at offset 0x0EA6
[   35.553046] [drm] nouveau 0000:00:10.0: BIOS FP mode: 1280x1024 (108000kHz pixel clock)
[   36.763857] input: Macintosh mouse button emulation as /devices/virtual/input/input7
[   36.917825] init: failsafe main process (666) killed by TERM signal
[   38.041235] i2c i2c-5: PMac Keywest Audio: attach_adapter method is deprecated
[   38.041252] i2c i2c-5: Please use another way to instantiate your i2c_client
[   38.326146] [drm] nouveau 0000:00:10.0: 1 available performance level(s)
[   38.326167] [drm] nouveau 0000:00:10.0: 0: memory 400MHz
[   38.326200] [drm] nouveau 0000:00:10.0: c: core 23MHz memory 405MHz
[   38.338673] [TTM] Zone  kernel: Available graphics memory: 378808 kiB.
[   38.338687] [TTM] Zone highmem: Available graphics memory: 575416 kiB.
[   38.338697] [TTM] Initializing pool allocator.
[   38.338769] [drm] nouveau 0000:00:10.0: Detected 32MiB VRAM
[   38.341543] [drm] nouveau 0000:00:10.0: 64 MiB GART (aperture)
[   38.375389] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   38.375408] [drm] No driver support for vblank timestamp query.
[   38.375443] [drm] nouveau 0000:00:10.0: Calling LVDS script 1:
[   38.375457] [drm] nouveau 0000:00:10.0: Calling LVDS script 6:
[   38.375468] [drm] nouveau 0000:00:10.0: 0x1306: Parsing digital output script table
[   38.871321] [drm] nouveau 0000:00:10.0: Setting dpms mode 3 on TV encoder (output 2)
[   39.412084] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   39.412106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412117] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   39.412128] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412138] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   39.412149] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412159] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   39.412171] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412180] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   39.412192] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412202] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   39.412213] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412223] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   39.412235] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412244] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   39.412256] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412266] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   39.412277] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412287] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   39.412299] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412308] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   39.412320] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412330] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   39.412341] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.412351] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   39.412363] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.412372] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   39.412384] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.412398] cfg80211: World regulatory domain updated:
[   39.412405] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   39.412416] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412426] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.412437] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.412447] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.412457] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.550574] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   39.568916] usbcore: registered new interface driver btusb
[   39.937200] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   39.965943] i2c i2c-6: PMac Keywest Audio: attach_adapter method is deprecated
[   39.965964] i2c i2c-6: Please use another way to instantiate your i2c_client
[   39.997173] [drm] nouveau 0000:00:10.0: Load detected on output B
[   39.997535] [drm] nouveau 0000:00:10.0: allocated 1024x768 fb: 0x49000, bo ed2da000
[   64.033066] BUG: soft lockup - CPU#0 stuck for 22s! [modprobe:335]
[   64.033075] Modules linked in: btusb arc4 b43 nouveau(+) mac_hid rtc_generic mac80211 ttm drm_kms_helper drm bnep cfg80211 parport_pc rfcomm ppdev bluetooth lp parport snd_powermac snd_pcm bcma snd_seq_midi uninorth_agp snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc apm_emu apm_emulation firewire_ohci firewire_core sungem sungem_phy crc_itu_t usbhid hid ssb
[   64.033167] NIP: c0021bc0 LR: f1ddb390 CTR: c0021b98
[   64.033176] REGS: ed34d5b0 TRAP: 0901   Not tainted  (3.2.0-57-powerpc-smp)
[   64.033182] MSR: 00009032 <EE,ME,IR,DR>  CR: 24042442  XER: 20000000
[   64.033200] TASK = ef313250[335] 'modprobe' THREAD: ed34c000 CPU: 0
[   64.033206] GPR00: f1ddb390 ed34d660 ef313250 0d004b04 0a2f6da0 00000000 26be3680 006013da 
[   64.033223] GPR08: 00000008 ecf80000 00000000 0987b3c0 c0021b98 
[   64.033247] NIP [c0021bc0] ioread32be+0x28/0x48
[   64.033388] LR [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[   64.033395] Call Trace:
[   64.033412] [ed34d660] [ecf80000] 0xecf80000 (unreliable)
[   64.033450] [ed34d670] [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[   64.033493] [ed34d6a0] [f1de8b00] nv_load_state_ext+0x8c0/0xf04 [nouveau]
[   64.033535] [ed34d6f0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[   64.033615] [ed34d710] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[   64.033642] [ed34d740] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[   64.033655] [ed34d930] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[   64.033669] [ed34d9b0] [f1bf01c8] drm_fb_helper_set_par+0x8c/0x108 [drm_kms_helper]
[   64.033684] [ed34d9d0] [c038c02c] fbcon_init+0x45c/0x4b8
[   64.033698] [ed34da20] [c03d530c] visual_init+0xf8/0x1b4
[   64.033710] [ed34da50] [c03d89dc] do_bind_con_driver+0x2d8/0x4fc
[   64.033721] [ed34dab0] [c03d8e98] do_take_over_console+0x58/0x74
[   64.033731] [ed34dad0] [c038c118] do_fbcon_takeover+0x90/0xfc
[   64.033742] [ed34daf0] [c038ffa4] fbcon_event_notify+0x440/0x480
[   64.033759] [ed34db20] [c0651210] notifier_call_chain+0x8c/0xcc
[   64.033770] [ed34db50] [c008aa68] __blocking_notifier_call_chain+0x60/0x88
[   64.033780] [ed34db80] [c008aabc] blocking_notifier_call_chain+0x2c/0x44
[   64.033796] [ed34db90] [c037d984] fb_notifier_call_chain+0x38/0x50
[   64.033808] [ed34dba0] [c037fbbc] do_register_framebuffer+0x1c0/0x2a8
[   64.033818] [ed34dc10] [c037fce0] register_framebuffer+0x3c/0x64
[   64.033831] [ed34dc30] [f1bf042c] drm_fb_helper_single_fb_probe+0x1e8/0x314 [drm_kms_helper]
[   64.033845] [ed34dc70] [f1bf07fc] drm_fb_helper_initial_config+0xc0/0xe4 [drm_kms_helper]
[   64.033900] [ed34dca0] [f1e00364] nouveau_fbcon_init+0xb4/0x10c [nouveau]
[   64.033937] [ed34dcc0] [f1dda758] nouveau_card_init+0x620/0x644 [nouveau]
[   64.033973] [ed34dce0] [f1ddac7c] nouveau_load+0x2e4/0x5dc [nouveau]
[   64.034063] [ed34dd00] [f19a7f0c] drm_get_pci_dev+0x188/0x2c0 [drm]
[   64.034113] [ed34dd30] [f1e66e60] nouveau_pci_probe+0x20/0x38 [nouveau]
[   64.034125] [ed34dd40] [c035c720] local_pci_probe+0x6c/0xdc
[   64.034136] [ed34dd60] [c035d9c8] pci_device_probe+0x84/0xc4
[   64.034153] [ed34dd90] [c03f7828] really_probe+0x88/0x1c4
[   64.034163] [ed34ddc0] [c03f7b60] driver_probe_device+0x60/0x8c
[   64.034174] [ed34dde0] [c03f7c38] __driver_attach+0xac/0xc8
[   64.034184] [ed34de00] [c03f66e8] bus_for_each_dev+0x84/0xc4
[   64.034194] [ed34de30] [c03f7580] driver_attach+0x38/0x50
[   64.034204] [ed34de40] [c03f7110] bus_add_driver+0x1b0/0x280
[   64.034215] [ed34de70] [c03f834c] driver_register+0x98/0x16c
[   64.034225] [ed34de90] [c035e32c] __pci_register_driver+0x60/0xe4
[   64.034254] [ed34deb0] [f19a817c] drm_pci_init+0x138/0x150 [drm]
[   64.034295] [ed34dee0] [f1e91068] nouveau_init+0x68/0xb0 [nouveau]
[   64.034310] [ed34def0] [c0003e2c] do_one_initcall+0xbc/0x130
[   64.034328] [ed34df20] [c00a6578] sys_init_module+0xa0/0x1c8
[   64.034341] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38
[   64.034357] --- Exception: c01 at 0xff5ebfc
[   64.034361]     LR = 0x1000500c
[   64.034366] Instruction dump:
[   64.034372] 7d615b78 4e800020 7c0802a6 90010004 60000000 9421fff0 7c0802a6 90010014 
[   64.034387] 93e1000c 7c3f0b78 7c0004ac 80630000 <0c030000> 4c00012c 397f0010 800b0004 
[  137.700401] [drm] nouveau 0000:00:10.0: Setting dpms mode 0 on TV encoder (output 2)
[  137.700423] [drm] nouveau 0000:00:10.0: Output TV-1 is running on CRTC 0 using output B
[  137.700460] sched: RT throttling activated
[  160.033068] BUG: soft lockup - CPU#0 stuck for 21s! [modprobe:335]
[  160.033078] Modules linked in: btusb arc4 b43 nouveau(+) mac_hid rtc_generic mac80211 ttm drm_kms_helper drm bnep cfg80211 parport_pc rfcomm ppdev bluetooth lp parport snd_powermac snd_pcm bcma snd_seq_midi uninorth_agp snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc apm_emu apm_emulation firewire_ohci firewire_core sungem sungem_phy crc_itu_t usbhid hid ssb
[  160.033170] NIP: c0021bc0 LR: f1ddb390 CTR: c0021b98
[  160.033179] REGS: ed34d5b0 TRAP: 0901   Not tainted  (3.2.0-57-powerpc-smp)
[  160.033185] MSR: 00009032 <EE,ME,IR,DR>  CR: 28044442  XER: 20000000
[  160.033203] TASK = ef313250[335] 'modprobe' THREAD: ed34c000 CPU: 0
[  160.033210] GPR00: f1ddb390 ed34d660 ef313250 0d00172c 304293a0 00000000 26be3680 006013da 
[  160.033226] GPR08: 00000008 ecf80000 00000000 08d95ac0 c0021b98 
[  160.033251] NIP [c0021bc0] ioread32be+0x28/0x48
[  160.033383] LR [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[  160.033390] Call Trace:
[  160.033407] [ed34d660] [ecf80000] 0xecf80000 (unreliable)
[  160.033446] [ed34d670] [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[  160.033489] [ed34d6a0] [f1de8b24] nv_load_state_ext+0x8e4/0xf04 [nouveau]
[  160.033531] [ed34d6f0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[  160.033609] [ed34d710] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[  160.033633] [ed34d740] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[  160.033647] [ed34d930] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[  160.033661] [ed34d9b0] [f1bf01c8] drm_fb_helper_set_par+0x8c/0x108 [drm_kms_helper]
[  160.033676] [ed34d9d0] [c038c02c] fbcon_init+0x45c/0x4b8
[  160.033690] [ed34da20] [c03d530c] visual_init+0xf8/0x1b4
[  160.033702] [ed34da50] [c03d89dc] do_bind_con_driver+0x2d8/0x4fc
[  160.033713] [ed34dab0] [c03d8e98] do_take_over_console+0x58/0x74
[  160.033723] [ed34dad0] [c038c118] do_fbcon_takeover+0x90/0xfc
[  160.033734] [ed34daf0] [c038ffa4] fbcon_event_notify+0x440/0x480
[  160.033751] [ed34db20] [c0651210] notifier_call_chain+0x8c/0xcc
[  160.033762] [ed34db50] [c008aa68] __blocking_notifier_call_chain+0x60/0x88
[  160.033772] [ed34db80] [c008aabc] blocking_notifier_call_chain+0x2c/0x44
[  160.033789] [ed34db90] [c037d984] fb_notifier_call_chain+0x38/0x50
[  160.033800] [ed34dba0] [c037fbbc] do_register_framebuffer+0x1c0/0x2a8
[  160.033811] [ed34dc10] [c037fce0] register_framebuffer+0x3c/0x64
[  160.033823] [ed34dc30] [f1bf042c] drm_fb_helper_single_fb_probe+0x1e8/0x314 [drm_kms_helper]
[  160.033837] [ed34dc70] [f1bf07fc] drm_fb_helper_initial_config+0xc0/0xe4 [drm_kms_helper]
[  160.033894] [ed34dca0] [f1e00364] nouveau_fbcon_init+0xb4/0x10c [nouveau]
[  160.033930] [ed34dcc0] [f1dda758] nouveau_card_init+0x620/0x644 [nouveau]
[  160.033966] [ed34dce0] [f1ddac7c] nouveau_load+0x2e4/0x5dc [nouveau]
[  160.034049] [ed34dd00] [f19a7f0c] drm_get_pci_dev+0x188/0x2c0 [drm]
[  160.034098] [ed34dd30] [f1e66e60] nouveau_pci_probe+0x20/0x38 [nouveau]
[  160.034111] [ed34dd40] [c035c720] local_pci_probe+0x6c/0xdc
[  160.034121] [ed34dd60] [c035d9c8] pci_device_probe+0x84/0xc4
[  160.034138] [ed34dd90] [c03f7828] really_probe+0x88/0x1c4
[  160.034148] [ed34ddc0] [c03f7b60] driver_probe_device+0x60/0x8c
[  160.034159] [ed34dde0] [c03f7c38] __driver_attach+0xac/0xc8
[  160.034169] [ed34de00] [c03f66e8] bus_for_each_dev+0x84/0xc4
[  160.034180] [ed34de30] [c03f7580] driver_attach+0x38/0x50
[  160.034190] [ed34de40] [c03f7110] bus_add_driver+0x1b0/0x280
[  160.034201] [ed34de70] [c03f834c] driver_register+0x98/0x16c
[  160.034211] [ed34de90] [c035e32c] __pci_register_driver+0x60/0xe4
[  160.034239] [ed34deb0] [f19a817c] drm_pci_init+0x138/0x150 [drm]
[  160.034280] [ed34dee0] [f1e91068] nouveau_init+0x68/0xb0 [nouveau]
[  160.034294] [ed34def0] [c0003e2c] do_one_initcall+0xbc/0x130
[  160.034312] [ed34df20] [c00a6578] sys_init_module+0xa0/0x1c8
[  160.034325] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38

[  160.034340] --- Exception: c01 at 0xff5ebfc
[  160.034343]     LR = 0x1000500c
[  160.034348] Instruction dump:
[  160.034354] 7d615b78 4e800020 7c0802a6 90010004 60000000 9421fff0 7c0802a6 90010014 
[  160.034370] 93e1000c 7c3f0b78 7c0004ac 80630000 <0c030000> 4c00012c 397f0010 800b0004 
[  235.417358] [drm] nouveau 0000:00:10.0: Calling LVDS script 2:
[  235.417373] [drm] nouveau 0000:00:10.0: 0x1072: Parsing digital output script table
[  235.433302] [drm] nouveau 0000:00:10.0: Calling LVDS script 5:
[  235.433311] [drm] nouveau 0000:00:10.0: 0x1109: Parsing digital output script table

[  235.463780] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  235.465034] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  235.469237] init: udevtrigger post-stop process (315) terminated with status 1
[  235.499460] Console: switching to colour frame buffer device 90x36
[  235.502331] fb0: nouveaufb frame buffer device
[  235.502341] drm: registered panic notifier
[  235.509232] [drm] Initialized nouveau 0.0.16 20090420 for 0000:00:10.0 on minor 0
[  235.677557] sungem_phy: PHY ID: 4061e4, addr: 0
[  235.677894] gem 0002:20:0f.0: eth0: Found BCM5221 PHY

[  235.679027] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  235.685416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  236.073934] type=1400 audit(1388052484.048:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=837 comm="apparmor_parser"
[  236.075127] type=1400 audit(1388052484.048:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=837 comm="apparmor_parser"
[  236.091925] type=1400 audit(1388052484.064:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=838 comm="apparmor_parser"
[  236.094159] type=1400 audit(1388052484.068:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[  236.094994] type=1400 audit(1388052484.068:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=838 comm="apparmor_parser"
[  236.155945] type=1400 audit(1388052484.132:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=839 comm="apparmor_parser"
[  236.174766] type=1400 audit(1388052484.148:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=839 comm="apparmor_parser"
[  236.180441] type=1400 audit(1388052484.152:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=839 comm="apparmor_parser"
[  236.187134] type=1400 audit(1388052484.160:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=839 comm="apparmor_parser"
[  236.198661] type=1400 audit(1388052484.172:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=839 comm="apparmor_parser"
[  238.333256] [drm] nouveau 0000:00:10.0: Load detected on output B
[  238.497212] [drm] nouveau 0000:00:10.0: Load detected on output B
[  238.959766] [drm] nouveau 0000:00:10.0: Setting dpms mode 3 on TV encoder (output 2)

[  264.033064] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:953]
[  264.033074] Modules linked in: btusb arc4 b43 nouveau mac_hid rtc_generic mac80211 ttm drm_kms_helper drm bnep cfg80211 parport_pc rfcomm ppdev bluetooth lp parport snd_powermac snd_pcm bcma snd_seq_midi uninorth_agp snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc apm_emu apm_emulation firewire_ohci firewire_core sungem sungem_phy crc_itu_t usbhid hid ssb
[  264.033239] NIP: c0021bc0 LR: f1ddb390 CTR: c0021b98
[  264.033249] REGS: ed34d990 TRAP: 0901   Not tainted  (3.2.0-57-powerpc-smp)
[  264.033257] MSR: 00009032 <EE,ME,IR,DR>  CR: 24002442  XER: 20000000
[  264.033281] TASK = ef313250[953] 'Xorg' THREAD: ed34c000 CPU: 0
[  264.033290] GPR00: f1ddb390 ed34da40 ef313250 0d004b08 59834800 00000000 26be3680 006013da 
[  264.033314] GPR08: 00000008 ecf80000 00000000 09f0bbc0 c0021b98 
[  264.033345] NIP [c0021bc0] ioread32be+0x28/0x48
[  264.033455] LR [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[  264.033462] Call Trace:
[  264.033479] [ed34da40] [ecf80000] 0xecf80000 (unreliable)
[  264.033511] [ed34da50] [f1ddb390] nouveau_wait_eq+0x80/0xc4 [nouveau]
[  264.033548] [ed34da80] [f1de8b24] nv_load_state_ext+0x8e4/0xf04 [nouveau]
[  264.033582] [ed34dad0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[  264.033654] [ed34daf0] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[  264.033683] [ed34db20] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[  264.033699] [ed34dd10] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[  264.033799] [ed34dd90] [f19af45c] drm_mode_setcrtc+0x2f0/0x38c [drm]
[  264.033825] [ed34de10] [f199e488] drm_ioctl+0x1d4/0x44c [drm]
[  264.033842] [ed34dee0] [c017f454] do_vfs_ioctl+0xac/0x2f4
[  264.033853] [ed34df10] [c017f728] sys_ioctl+0x8c/0xac
[  264.033868] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38

[  264.033885] --- Exception: c01 at 0x1fceb054
[  264.033888]     LR = 0x1fceafbc
[  264.033895] Instruction dump:
[  264.033903] 7d615b78 4e800020 7c0802a6 90010004 60000000 9421fff0 7c0802a6 90010014 
[  264.033927] 93e1000c 7c3f0b78 7c0004ac 80630000 <0c030000> 4c00012c 397f0010 800b0004 
[  298.961061] INFO: rcu_sched detected stall on CPU 0 (t=15000 jiffies)
[  298.961072] Call Trace:
[  298.961087] [ed34d740] [c000c174] show_stack+0x110/0x1c8 (unreliable)
[  298.961102] [ed34d790] [c0655d60] dump_stack+0x2c/0x44
[  298.961122] [ed34d7a0] [c00d44c4] print_cpu_stall+0x50/0xb4
[  298.961135] [ed34d7c0] [c00d52c4] __rcu_pending+0x104/0x264
[  298.961149] [ed34d7e0] [c00d670c] rcu_check_callbacks+0x1f4/0x254
[  298.961167] [ed34d810] [c006ca7c] update_process_times+0x4c/0x84
[  298.961180] [ed34d830] [c00997ec] tick_sched_timer+0x94/0x118
[  298.961200] [ed34d860] [c00879ac] __run_hrtimer+0x84/0x220
[  298.961213] [ed34d890] [c008909c] hrtimer_interrupt+0x1a8/0x47c
[  298.961228] [ed34d930] [c000f2e4] timer_interrupt+0x1e4/0x2f0
[  298.961241] [ed34d960] [c0019dbc] ret_from_except+0x0/0x14

[  298.961316] --- Exception: 901 at ioread32be+0x28/0x48
[  298.961320]     LR = nv04_timer_read+0x50/0x8c [nouveau]
[  298.961338] [ed34da20] [20000000] 0x20000000 (unreliable)
[  298.961376] [ed34da30] [f1e074e8] nv04_timer_read+0x50/0x8c [nouveau]
[  298.961406] [ed34da50] [f1ddb370] nouveau_wait_eq+0x60/0xc4 [nouveau]
[  298.961438] [ed34da80] [f1de8b24] nv_load_state_ext+0x8e4/0xf04 [nouveau]
[  298.961471] [ed34dad0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[  298.961517] [ed34daf0] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[  298.961537] [ed34db20] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[  298.961553] [ed34dd10] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[  298.961605] [ed34dd90] [f19af45c] drm_mode_setcrtc+0x2f0/0x38c [drm]
[  298.961632] [ed34de10] [f199e488] drm_ioctl+0x1d4/0x44c [drm]
[  298.961645] [ed34dee0] [c017f454] do_vfs_ioctl+0xac/0x2f4
[  298.961657] [ed34df10] [c017f728] sys_ioctl+0x8c/0xac
[  298.961669] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38

[  298.961684] --- Exception: c01 at 0x1fceb054
[  298.961687]     LR = 0x1fceafbc
[  336.665867] [drm] nouveau 0000:00:10.0: Setting dpms mode 0 on TV encoder (output 2)
[  336.665888] [drm] nouveau 0000:00:10.0: Output TV-1 is running on CRTC 0 using output B
[  336.687167] input: Mouseemu virtual keyboard as /devices/virtual/input/input8
[  336.691535] input: Mouseemu virtual mouse as /devices/virtual/input/input9
[  336.713524] [drm] nouveau 0000:00:10.0: Calling LVDS script 6:
[  336.713549] [drm] nouveau 0000:00:10.0: 0x116F: Parsing digital output script table
[  360.033065] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:953]
[  360.033076] Modules linked in: btusb arc4 b43 nouveau mac_hid rtc_generic mac80211 ttm drm_kms_helper drm bnep cfg80211 parport_pc rfcomm ppdev bluetooth lp parport snd_powermac snd_pcm bcma snd_seq_midi uninorth_agp snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc apm_emu apm_emulation firewire_ohci firewire_core sungem sungem_phy crc_itu_t usbhid hid ssb
[  360.033204] NIP: c0021bbc LR: f1e074e8 CTR: c0021b98
[  360.033215] REGS: ed34d970 TRAP: 0901   Not tainted  (3.2.0-57-powerpc-smp)
[  360.033223] MSR: 00009032 <EE,ME,IR,DR>  CR: 28004444  XER: 20000000
[  360.033247] TASK = ef313250[953] 'Xorg' THREAD: ed34c000 CPU: 0
[  360.033256] GPR00: f1e074e8 ed34da20 ef313250 f2009400 7f967000 00000000 26be3680 006013da 
[  360.033279] GPR08: 00000008 ecf80000 00000000 ed34da30 c0021b98 
[  360.033310] NIP [c0021bbc] ioread32be+0x24/0x48
[  360.033438] LR [f1e074e8] nv04_timer_read+0x50/0x8c [nouveau]
[  360.033446] Call Trace:
[  360.033463] [ed34da20] [20000000] 0x20000000 (unreliable)
[  360.033504] [ed34da30] [f1e074e8] nv04_timer_read+0x50/0x8c [nouveau]
[  360.033534] [ed34da50] [f1ddb370] nouveau_wait_eq+0x60/0xc4 [nouveau]
[  360.033566] [ed34da80] [f1de8b24] nv_load_state_ext+0x8e4/0xf04 [nouveau]
[  360.033599] [ed34dad0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[  360.033656] [ed34daf0] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[  360.033683] [ed34db20] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[  360.033699] [ed34dd10] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[  360.033788] [ed34dd90] [f19af45c] drm_mode_setcrtc+0x2f0/0x38c [drm]
[  360.033815] [ed34de10] [f199e488] drm_ioctl+0x1d4/0x44c [drm]
[  360.033830] [ed34dee0] [c017f454] do_vfs_ioctl+0xac/0x2f4
[  360.033842] [ed34df10] [c017f728] sys_ioctl+0x8c/0xac
[  360.033857] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38

[  360.033874] --- Exception: c01 at 0x1fceb054
[  360.033877]     LR = 0x1fceafbc
[  360.033883] Instruction dump:
[  360.033891] 83ebfffc 7d615b78 4e800020 7c0802a6 90010004 60000000 9421fff0 7c0802a6 
[  360.033915] 90010014 93e1000c 7c3f0b78 7c0004ac 
[  360.033930]  0c030000 4c00012c 397f0010 
[  396.713061] INFO: rcu_sched detected stall on CPU 0 (t=15000 jiffies)
[  396.713072] Call Trace:
[  396.713085] [ed34d740] [c000c174] show_stack+0x110/0x1c8 (unreliable)
[  396.713100] [ed34d790] [c0655d60] dump_stack+0x2c/0x44
[  396.713120] [ed34d7a0] [c00d44c4] print_cpu_stall+0x50/0xb4
[  396.713133] [ed34d7c0] [c00d52c4] __rcu_pending+0x104/0x264
[  396.713146] [ed34d7e0] [c00d670c] rcu_check_callbacks+0x1f4/0x254
[  396.713165] [ed34d810] [c006ca7c] update_process_times+0x4c/0x84
[  396.713178] [ed34d830] [c00997ec] tick_sched_timer+0x94/0x118
[  396.713197] [ed34d860] [c00879ac] __run_hrtimer+0x84/0x220
[  396.713210] [ed34d890] [c008909c] hrtimer_interrupt+0x1a8/0x47c
[  396.713225] [ed34d930] [c000f2e4] timer_interrupt+0x1e4/0x2f0
[  396.713239] [ed34d960] [c0019dbc] ret_from_except+0x0/0x14

[  396.713315] --- Exception: 901 at ioread32be+0x28/0x48
[  396.713319]     LR = nv04_timer_read+0x68/0x8c [nouveau]
[  396.713337] [ed34da20] [20000000] 0x20000000 (unreliable)
[  396.713376] [ed34da30] [f1e07500] nv04_timer_read+0x68/0x8c [nouveau]
[  396.713406] [ed34da50] [f1ddb370] nouveau_wait_eq+0x60/0xc4 [nouveau]
[  396.713438] [ed34da80] [f1de8b24] nv_load_state_ext+0x8e4/0xf04 [nouveau]
[  396.713470] [ed34dad0] [f1dee5ec] nouveau_hw_load_state+0xb8/0x14c [nouveau]
[  396.713516] [ed34daf0] [f1e4cb1c] nv_crtc_commit+0x44/0x1a8 [nouveau]
[  396.713537] [ed34db20] [f1bf1420] drm_crtc_helper_set_mode+0x238/0x38c [drm_kms_helper]
[  396.713552] [ed34dd10] [f1bf1dcc] drm_crtc_helper_set_config+0x6dc/0x974 [drm_kms_helper]
[  396.713601] [ed34dd90] [f19af45c] drm_mode_setcrtc+0x2f0/0x38c [drm]
[  396.713627] [ed34de10] [f199e488] drm_ioctl+0x1d4/0x44c [drm]
[  396.713640] [ed34dee0] [c017f454] do_vfs_ioctl+0xac/0x2f4
[  396.713651] [ed34df10] [c017f728] sys_ioctl+0x8c/0xac
[  396.713664] [ed34df40] [c001970c] ret_from_syscall+0x0/0x38

[  396.713679] --- Exception: c01 at 0x1fceb054
[  396.713682]     LR = 0x1fceafbc
[  434.915312] [drm] nouveau 0000:00:10.0: Calling LVDS script 2:
[  434.915327] [drm] nouveau 0000:00:10.0: 0x1072: Parsing digital output script table
[  434.931259] [drm] nouveau 0000:00:10.0: Calling LVDS script 5:
[  434.931269] [drm] nouveau 0000:00:10.0: 0x1109: Parsing digital output script table
[  438.337217] [drm] nouveau 0000:00:10.0: Load detected on output B
[  439.413178] [drm] nouveau 0000:00:10.0: Load detected on output B
[  441.880096] wlan0: direct probe to 28:93:fe:2e:c1:21 (try 1/3)
[  442.077216] wlan0: direct probe to 28:93:fe:2e:c1:21 (try 2/3)
[  442.079958] wlan0: direct probe responded
[  442.080023] wlan0: authenticate with 28:93:fe:2e:c1:21 (try 1)
[  442.081879] wlan0: authenticated
[  442.083020] wlan0: associate with 28:93:fe:2e:c1:21 (try 1)
[  442.085451] wlan0: RX AssocResp from 28:93:fe:2e:c1:21 (capab=0x421 status=0 aid=23)
[  442.085468] wlan0: associated
[  442.088863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  442.093028] cfg80211: Calling CRDA for country: US
[  442.169517] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  442.169539] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169549] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  442.169561] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169571] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  442.169583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169593] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  442.169604] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169655] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  442.169667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169677] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  442.169688] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169698] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  442.169710] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169720] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  442.169731] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169741] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  442.169753] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169762] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  442.169774] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169784] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  442.169795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169805] cfg80211: Disabling freq 2467 MHz
[  442.169811] cfg80211: Disabling freq 2472 MHz
[  442.169818] cfg80211: Disabling freq 2484 MHz
[  442.169831] cfg80211: Regulatory domain changed to country: US
[  442.169839] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  442.169850] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  442.169861] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  442.169871] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  442.169882] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  442.169892] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  442.169902] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  445.761184] [drm] nouveau 0000:00:10.0: Load detected on output B
[  452.837139] wlan0: no IPv6 routers present
[  455.857119] usb 2-1: new low-speed USB device number 2 using ohci_hcd
[  456.032092] input: HID 05c7:1001 as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1:1.0/input/input10
[  456.032684] generic-usb 0003:05C7:1001.0003: input,hidraw0: USB HID v1.00 Mouse [HID 05c7:1001] on usb-0001:10:19.0-1/input0
[  465.605189] [drm] nouveau 0000:00:10.0: Load detected on output B
[  465.801435] [drm] nouveau 0000:00:10.0: Load detected on output B
[  495.485820] ondemand governor failed, too long transition latency of HW, fallback to performance governor


```

I addes spaces trying to go through it to mark errors. 

Here is my var log error messages.

```

/var/log/auth.log:Dec 24 13:14:26 ubuntuPB dbus[649]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.28" (uid=104 pid=1371 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1115 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 13:14:29 ubuntuPB dbus[649]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.37" (uid=104 pid=1411 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1115 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 13:16:41 ubuntuPB dbus[649]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=1670 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1115 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 14:46:34 ubuntuPB dbus[587]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.31" (uid=104 pid=1446 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1188 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 14:46:40 ubuntuPB dbus[587]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.41" (uid=104 pid=1499 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1188 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 15:20:59 ubuntuPB dbus[587]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=1726 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1188 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 15:21:03 ubuntuPB dbus[587]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.66" (uid=1000 pid=1796 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1188 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 16:11:23 ubuntuPB dbus[587]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.103" (uid=104 pid=16847 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1188 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 18:42:01 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.31" (uid=104 pid=1504 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1244 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 18:42:06 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.41" (uid=104 pid=1557 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1244 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 18:45:19 ubuntuPB dbus[432]: [system] Rejected send message, 11 matched rules; type="error", sender=":1.50" (uid=1000 pid=1744 comm="nm-applet ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.5" (uid=0 pid=817 comm="NetworkManager ")
/var/log/auth.log:Dec 24 18:54:44 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.67" (uid=104 pid=2032 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1244 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 18:55:28 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.93" (uid=1000 pid=2299 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1244 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 18:55:34 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.99" (uid=1000 pid=2362 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=1244 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 21:47:42 ubuntuPB dbus[423]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=104 pid=1332 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1075 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 21:48:35 ubuntuPB dbus[423]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=445 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1000 pid=1534 comm="bluetooth-applet ")
/var/log/auth.log:Dec 24 22:02:43 ubuntuPB dbus[409]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=104 pid=1315 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1046 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 24 22:03:37 ubuntuPB dbus[409]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=433 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.57" (uid=1000 pid=1674 comm="bluetooth-applet ")
/var/log/auth.log:Dec 24 22:32:29 ubuntuPB dbus[426]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=1331 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=1070 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 25 01:49:58 ubuntuPB dbus[416]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=1337 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=1082 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 26 00:16:01 ubuntuPB dbus[446]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.24" (uid=104 pid=1381 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1062 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 26 00:16:06 ubuntuPB dbus[446]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.35" (uid=104 pid=1430 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1062 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 26 02:27:46 ubuntuPB dbus[446]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.77" (uid=1000 pid=2836 comm="/usr/bin/python /usr/share/apport/apport-gtk ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1062 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 26 02:27:46 ubuntuPB dbus[446]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.77" (uid=1000 pid=2836 comm="/usr/bin/python /usr/share/apport/apport-gtk ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1062 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 26 04:11:31 ubuntuPB dbus[419]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=104 pid=1361 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=1098 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 27 00:34:08 ubuntuPB dbus[432]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=1351 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=1096 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 28 00:46:13 ubuntuPB dbus[438]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.24" (uid=104 pid=1340 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1085 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Dec 28 01:10:12 ubuntuPB sudo:  legolas : TTY=pts/1 ; PWD=/home/legolas ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/mail.log /var/log/pm-powersave.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/wvdialconf.log /var/log/Xorg.0.log
/var/log/dpkg.log:2013-12-24 10:36:57 install libgpg-error0 <none> 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:36:57 status half-installed libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:36:57 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:36:57 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:37:33 configure libgpg-error0 1.10-2ubuntu1 <none>
/var/log/dpkg.log:2013-12-24 10:37:33 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:37:33 status half-configured libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-24 10:37:34 status installed libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2013-12-25 00:18:10 install liberror-perl <none> 0.17-1
/var/log/dpkg.log:2013-12-25 00:18:10 status half-installed liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:18:10 status half-installed liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:18:11 status unpacked liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:18:11 status unpacked liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:20:37 configure liberror-perl 0.17-1 <none>
/var/log/dpkg.log:2013-12-25 00:20:37 status unpacked liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:20:37 status half-configured liberror-perl 0.17-1
/var/log/dpkg.log:2013-12-25 00:20:37 status installed liberror-perl 0.17-1
/var/log/kern.log:Dec 24 13:06:01 ubuntuPB kernel: [    8.925367] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 24 13:09:31 ubuntuPB kernel: [  224.783283] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
/var/log/kern.log:Dec 24 13:09:31 ubuntuPB kernel: [  224.783350] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
/var/log/kern.log:Dec 24 13:09:31 ubuntuPB kernel: [  224.783383] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Dec 24 14:07:30 ubuntuPB kernel: [ 3702.680493] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
/var/log/kern.log:Dec 24 14:07:30 ubuntuPB kernel: [ 3702.680511] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
/var/log/kern.log:Dec 24 14:07:30 ubuntuPB kernel: [ 3702.680521] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Dec 24 14:07:36 ubuntuPB kernel: [ 3708.079153] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
/var/log/kern.log:Dec 24 14:07:36 ubuntuPB kernel: [ 3708.079169] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
/var/log/kern.log:Dec 24 14:07:36 ubuntuPB kernel: [ 3708.079179] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Dec 24 14:39:10 ubuntuPB kernel: [    8.557336] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 24 18:34:54 ubuntuPB kernel: [   11.149588] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 24 21:44:09 ubuntuPB kernel: [   27.613614] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 24 21:55:54 ubuntuPB kernel: [   20.553380] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 24 22:24:24 ubuntuPB kernel: [   21.204813] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 25 01:46:23 ubuntuPB kernel: [   25.473843] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 26 00:09:03 ubuntuPB kernel: [   30.759430] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 26 00:12:30 ubuntuPB kernel: [  141.484470] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
/var/log/kern.log:Dec 26 00:12:30 ubuntuPB kernel: [  141.484482] b43-phy0 ERROR: Firmware file "b43-open/b0g0initvals5.fw" not found
/var/log/kern.log:Dec 26 00:12:30 ubuntuPB kernel: [  141.484492] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Dec 26 01:26:02 ubuntuPB kernel: [ 4637.179758] ipheth: probe of 2-1:4.2 failed with error -110
/var/log/kern.log:Dec 26 04:04:40 ubuntuPB kernel: [   30.585734] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 27 00:27:17 ubuntuPB kernel: [   30.714235] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 28 00:39:22 ubuntuPB kernel: [   30.692527] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Dec 28 00:42:45 ubuntuPB kernel: [  235.126136] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
/var/log/kern.log:Dec 28 00:42:45 ubuntuPB kernel: [  235.126148] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
/var/log/kern.log:Dec 28 00:42:45 ubuntuPB kernel: [  235.126158] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.0.log:[   237.872] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.0.log:[   237.883] (WW) Warning, couldn't open module nv
/var/log/Xorg.0.log:[   237.895] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.0.log:[   237.899] (WW) Warning, couldn't open module nv


```

any help would be greatly appreciated.

---

### Post by rsavage on 2013-12-28
Maybe try disabling phantom outputs??? [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics)

The sledge hammer approach would be to disable KMS using the 'nomodeset' boot parameter.

---

### Post by theodore-r on 2013-12-28
Ok, I'll try these and report back. Thank you.

---

### Post by theodore-r on 2013-12-30
Well, nouveau modeset 0 gave me some interesting colors. Just for kicks I also installed an xorg profile from the linux.be site. That didn't help. I haven't tried recompiling xorg with the nv driver yet.
It doesn't make sense that its video driver that is the problem, though, since everything seems to work so well once its running. Even 3D and terminal transparency (in Unity only.)

As an experiment, I installed 10.04, and the performance boost is unworldly. Not only does it boot quickly, but there is no "ambient" processor load. By contrast, in 12.04, there was a constant 35% processor load (according to the menu indicators) that never went away. I'll try a new install of 12.04 from a lubuntu disk and see if its any improvement--but if no, rather than muck around with recompiled xorgs and such, I'll probably just fall back to 10.04, since it works so well.

---

### Post by rsavage on 2013-12-30
> **theodore-r said:**
> Well, nouveau modeset 0 gave me some interesting colors.
Expected.  But did you have a faster boot?

> Just for kicks I also installed an xorg profile from the linux.be site. 
why?

> 
That didn't help.

Expected.

> 
 I'll probably just fall back to 10.04, since it works so well.
Is unsupported on the desktop now.  No latest firefox, Java, so pretty pointless.  You can recreate 10.04 using Mate - see [http://ubuntuforums.org/showthread.php?t=1918246&page=29&p=12573621#post12573621](http://ubuntuforums.org/showthread.php?t=1918246&page=29&p=12573621#post12573621) and [http://ubuntuforums.org/showthread.php?t=1918246&page=30&p=12582145#post12582145](http://ubuntuforums.org/showthread.php?t=1918246&page=30&p=12582145#post12582145) (although Mate 1.6 is quicker).

---

