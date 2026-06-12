---
title: "won't boot up"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by hbence on 2007-10-08
I installed ubuntu 7.04 on a new partition two days ago, I used it all day and it worked well. Then the next day when i've tried to load up it freezed on the login screen, I couldn't type the username. I can enter from the terminal and it says "Failed to initialize HAL" and also i can't change my administrational settings because it says I don't have the right to (I've tried the root and the first user too).

I've tried the live cd to reinstall or something but it loads up a blank black screen. Is there a way to fix the problem or reinstall the system?

---

### Post by jnorthr on 2007-10-08
Good Morning -
Do you have a dual boot system, if so can you boot into windows and does it run normally ? This should confirm your machine is still working correctly.  Have you made any hardware changes ? Have you loaded any new packages and if so did they give a successful completion ? 

When you try to boot your system without the liveCD, does grub give you a menu of operating systems to select from ? I believe there is an option there to boot using safe mode. This will avoid loading most of your device drivers which may be causing you problems as that is what HAL is looking at during boot time. If you can get in that way, look to start a terminal session and issue the dmesg command. This will show you the system log with messages from the kernel. If possible could you please post that ?

When you try the liveCD, what messages do you see ? 

the more you can explain, the more you can tell us, the more we can help you :KS

---

### Post by hbence on 2007-10-08
Yes, it's a dual boot system, and the xp works fine. I didn't make any hardware changes. I've loaded some packages for try (gaim and a library for c), those downloaded succesfully.

I can choose operating systems from grub and i can boot using the recovery mode, if i write "sudo /etc/init.d/gdm start" i can login normally, and then it gives that failed to initialize hal massage. When i try to start the system in normal mode it still doesn't work.

Here's the text from the dmesg command:
```

[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=e62806b7-5141-4dd1-a8fc-a4236a528b1c ro single
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262096) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 M S I                                 ) @ 0x00000000000f82e0
[    0.000000] ACPI: RSDT (v001 MSI_NB MEGABOOK 0x12062006 MSFT 0x00000097) @ 0x000000003ffd0000
[    0.000000] ACPI: FADT (v002 MSI_NB 1633X    0x12062006 MSFT 0x00000097) @ 0x000000003ffd0200
[    0.000000] ACPI: MADT (v001 MSI_NB OEMAPIC  0x12062006 MSFT 0x00000097) @ 0x000000003ffd0390
[    0.000000] ACPI: MCFG (v001 MSI_NB OEMMCFG  0x12062006 MSFT 0x00000097) @ 0x000000003ffd0400
[    0.000000] ACPI: SLIC (v001 MSI_NB MEGABOOK 0x12062006 MSFT 0x00000097) @ 0x000000003ffd0440
[    0.000000] ACPI: OEMB (v001 MSI_NB AMI_OEM  0x12062006 MSFT 0x00000097) @ 0x000000003ffde040
[    0.000000] ACPI: SSDT (v001 A M I  POWERNOW 0x00000001 AMD  0x00000001) @ 0x000000003ffd5030
[    0.000000] ACPI: DSDT (v001 M S I  1633X    0x00000007 INTL 0x20051117) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ffd0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262096) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ffd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262096
[    0.000000] On node 0 totalpages: 261999
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254473 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257331
[    0.000000] Kernel command line: root=UUID=e62806b7-5141-4dd1-a8fc-a4236a528b1c ro single
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   38.317807] Console: colour VGA+ 80x25
[   38.320884] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   38.322182] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   38.322346] Checking aperture...
[   38.322395] CPU 0: aperture @ c22000000 size 32 MB
[   38.322442] Aperture too small (32 MB)
[   38.329413] No AGP bridge found
[   38.342349] Memory: 1020320k/1048384k available (2217k kernel code, 27676k reserved, 1162k data, 304k init)
[   38.420849] Calibrating delay using timer specific routine.. 3619.79 BogoMIPS (lpj=7239587)
[   38.421000] Security Framework v1.0.0 initialized
[   38.421053] SELinux:  Disabled at boot.
[   38.421125] Mount-cache hash table entries: 256
[   38.421330] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.421381] CPU: L2 Cache: 512K (64 bytes/line)
[   38.421430] CPU 0/0 -> Node 0
[   38.421475] CPU: Physical Processor ID: 0
[   38.421521] CPU: Processor Core ID: 0
[   38.421589] SMP alternatives: switching to UP code
[   38.421940] Early unpacking initramfs... done
[   38.787027] ACPI: Core revision 20060707
[   38.787563] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   38.840472] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   39.021054] Using local APIC timer interrupts.
[   39.076376] result 12557340
[   39.076423] Detected 12.557 MHz APIC timer.
[   39.076788] SMP alternatives: switching to SMP code
[   39.076981] Booting processor 1/2 APIC 0x1
[   39.087458] Initializing CPU#1
[   39.164663] Calibrating delay using timer specific routine.. 3621.33 BogoMIPS (lpj=7242669)
[   39.164670] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   39.164673] CPU: L2 Cache: 512K (64 bytes/line)
[   39.164675] CPU 1/1 -> Node 0
[   39.164677] CPU: Physical Processor ID: 0
[   39.164679] CPU: Processor Core ID: 1
[   39.164764] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   39.168675] CPU 1: Syncing TSC to CPU 0.
[   39.168617] CPU 1: synchronized TSC with CPU 0 (last diff -1 cycles, maxerr 519 cycles)
[   39.168631] Brought up 2 CPUs
[   39.169234] Disabling vsyscall due to use of PM timer
[   39.169285] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   39.169333] time.c: Detected 1808.256 MHz processor.
[   39.251860] migration_cost=290
[   39.252345] Time:  9:48:04  Date: 09/08/107
[   39.252438] NET: Registered protocol family 16
[   39.252589] ACPI: bus type pci registered
[   39.252641] PCI: Using configuration type 1
[   39.259931] ACPI: Interpreter enabled
[   39.259981] ACPI: Using IOAPIC for interrupt routing
[   39.260319] Error attaching device data
[   39.260372] Error attaching device data
[   39.260779] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   39.260832] PCI: Probing PCI hardware (bus 00)
[   39.261991] Boot video device is 0000:04:00.0
[   39.262274] PCI: Transparent bridge - 0000:00:10.0
[   39.262373] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#06) (try 'pci=assign-busses')
[   39.262435] Please report the result to linux-kernel to fix this permanently
[   39.262519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   39.277758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[   39.281487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   39.281887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   39.282231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   39.283607] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *10
[   39.284292] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   39.285203] ACPI: PCI Interrupt Link [LNKC] (IRQs 17) *10
[   39.285876] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   39.286682] ACPI: PCI Interrupt Link [LNEA] (IRQs 18) *10
[   39.287352] ACPI: PCI Interrupt Link [LNEB] (IRQs 19) *5
[   39.288023] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   39.288859] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   39.289667] ACPI: PCI Interrupt Link [LUB0] (IRQs 21) *7
[   39.290341] ACPI: PCI Interrupt Link [LUB2] (IRQs 21) *14
[   39.291014] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
[   39.291823] ACPI: PCI Interrupt Link [LAZA] (IRQs 23) *11
[   39.292511] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   39.293322] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   39.294130] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[   39.294912] ACPI: PCI Interrupt Link [LPMU] (IRQs 20) *11
[   39.295587] ACPI: PCI Interrupt Link [LSA0] (IRQs 22) *10
[   39.296265] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[   39.297251] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   39.297708] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.297772] pnp: PnP ACPI init
[   39.301471] pnp: PnP ACPI: found 12 devices
[   39.301588] PCI: Using ACPI for IRQ routing
[   39.301637] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   39.301812] NET: Registered protocol family 8
[   39.301860] NET: Registered protocol family 20
[   39.303486] PCI: Bridge: 0000:00:02.0
[   39.303535]   IO window: a000-afff
[   39.303582]   MEM window: f9800000-f98fffff
[   39.303628]   PREFETCH window: disabled.
[   39.303675] PCI: Bridge: 0000:00:03.0
[   39.303720]   IO window: b000-bfff
[   39.303767]   MEM window: f9900000-fa0fffff
[   39.303813]   PREFETCH window: bbf00000-bdefffff
[   39.303860] PCI: Bridge: 0000:00:04.0
[   39.303905]   IO window: c000-cfff
[   39.303952]   MEM window: fa100000-fe1fffff
[   39.303999]   PREFETCH window: bdf00000-ddefffff
[   39.304053] PCI: Bus 6, cardbus bridge: 0000:05:04.0
[   39.304100]   IO window: 0000d000-0000d0ff
[   39.304148]   IO window: 0000d400-0000d4ff
[   39.304196]   PREFETCH window: 50000000-53ffffff
[   39.304244]   MEM window: 54000000-57ffffff
[   39.304291] PCI: Bridge: 0000:00:10.0
[   39.304337]   IO window: d000-dfff
[   39.304385]   MEM window: fe200000-feafffff
[   39.304451]   PREFETCH window: ddf00000-dfefffff
[   39.304508] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.304514] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   39.304521] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   39.304528] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   39.304978] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
[   39.305035] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 17
[   39.305258] NET: Registered protocol family 2
[   39.344497] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   39.344800] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   39.346527] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   39.347426] TCP: Hash tables configured (established 131072 bind 65536)
[   39.347479] TCP reno registered
[   39.356557] checking if image is initramfs... it is
[   40.041401] Freeing initrd memory: 7301k freed
[   40.047489] audit: initializing netlink socket (disabled)
[   40.047555] audit(1191836884.608:1): initialized
[   40.047837] VFS: Disk quotas dquot_6.5.1
[   40.047911] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   40.048015] io scheduler noop registered
[   40.048113] io scheduler anticipatory registered
[   40.048193] io scheduler deadline registered
[   40.048289] io scheduler cfq registered (default)
[   40.476092] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.476113] assign_interrupt_mode Found MSI capability
[   40.476165] Allocate Port Service[0000:00:02.0:pcie00]
[   40.476239] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   40.476260] assign_interrupt_mode Found MSI capability
[   40.476310] Allocate Port Service[0000:00:03.0:pcie00]
[   40.476379] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   40.476401] assign_interrupt_mode Found MSI capability
[   40.476450] Allocate Port Service[0000:00:04.0:pcie00]
[   40.503621] Real Time Clock Driver v1.12ac
[   40.503720] Linux agpgart interface v0.102 (c) Dave Jones
[   40.503771] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   40.504499] mice: PS/2 mouse device common for all mice
[   40.505138] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   40.505435] input: Macintosh mouse button emulation as /class/input/input0
[   40.505521] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.505574] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.505841] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   40.506372] i8042.c: Detected active multiplexing controller, rev 1.1.
[   40.506498] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.508859] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   40.508911] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   40.508958] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   40.509006] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   40.509237] TCP cubic registered
[   40.509295] NET: Registered protocol family 1
[   40.509458] ACPI: (supports S0 S1 S3 S4 S5)
[   40.509757]   Magic number: 11:365:828
[   40.509896]   hash matches device ptyt8
[   40.509957]   hash matches device ptyqb
[   40.510037] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   40.510172] Freeing unused kernel memory: 304k freed
[   40.512548] input: AT Translated Set 2 keyboard as /class/input/input1
[   40.690229] Capability LSM initialized
[   40.735086] ACPI: Thermal Zone [THRM] (57 C)
[   41.207110] usbcore: registered new interface driver usbfs
[   41.207187] usbcore: registered new interface driver hub
[   41.231257] usbcore: registered new device driver usb
[   41.235002] SCSI subsystem initialized
[   41.240938] libata version 2.20 loaded.
[   41.242819] sata_nv 0000:00:0e.0: version 3.3
[   41.243300] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[   41.243362] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 22
[   41.243516] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   41.243586] ata1: SATA max UDMA/133 cmd 0x000000000001e800 ctl 0x000000000001e482 bmdma 0x000000000001e000 irq 22
[   41.243679] ata2: SATA max UDMA/133 cmd 0x000000000001e400 ctl 0x000000000001e082 bmdma 0x000000000001e008 irq 22
[   41.243754] scsi0 : sata_nv
[   41.280564] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   41.316549] ieee1394: Initialized config rom entry `ip1394'
[   41.715214] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   41.760894] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   41.760964] ata1.00: ATA-7: WDC WD1200BEVS-00LAT0, 01.06M01, max UDMA/133
[   41.761015] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/1)
[   41.771462] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   41.771524] ata1.00: configured for UDMA/133
[   41.771583] scsi1 : sata_nv
[   42.086999] ata2: SATA link down (SStatus 0 SControl 300)
[   42.087192] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[   42.094715] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   42.094791] NFORCE-MCP51: chipset revision 161
[   42.094840] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   42.094895] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   42.094951]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   42.095092] Probing IDE interface ide1...
[   42.108153] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   42.108220] sda: Write Protect is off
[   42.108267] sda: Mode Sense: 00 3a 00 00
[   42.108283] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.108398] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   42.108457] sda: Write Protect is off
[   42.108502] sda: Mode Sense: 00 3a 00 00
[   42.108517] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.108579]  sda: sda1 sda2 sda3
[   42.213632] sd 0:0:0:0: Attached scsi disk sda
[   42.217355] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   42.476061] Attempting manual resume
[   42.476109] swsusp: Resume From Partition 8:3
[   42.476112] PM: Checking swsusp image.
[   42.476320] PM: Resume from disk failed.
[   42.490919] EXT3-fs: INFO: recovery required on readonly filesystem.
[   42.490989] EXT3-fs: write access will be enabled during recovery.
[   42.597768] kjournald starting.  Commit interval 5 seconds
[   42.597776] EXT3-fs: recovery complete.
[   42.598126] EXT3-fs: mounted filesystem with ordered data mode.
[   42.834714] hdc: Optiarc DVD RW AD-7530A, ATAPI CD/DVD-ROM drive
[   43.510993] ide1 at 0x170-0x177,0x376 on irq 15
[   43.512002] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[   43.512062] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 21 (level, low) -> IRQ 21
[   43.512204] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   43.512207] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   43.512417] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   43.512511] ehci_hcd 0000:00:0b.1: debug port 1
[   43.512562] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   43.512573] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfebbfc00
[   43.512628] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.512784] usb usb1: configuration #1 chosen from 1 choice
[   43.512860] hub 1-0:1.0: USB hub found
[   43.512914] hub 1-0:1.0: 8 ports detected
[   43.618484] ACPI: PCI Interrupt 0000:05:04.4[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 17
[   43.633190] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[   43.633246] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 21
[   43.633386] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   43.633390] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   43.633478] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   43.633552] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xfebbe000
[   43.668864] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   43.692251] usb usb2: configuration #1 chosen from 1 choice
[   43.692329] hub 2-0:1.0: USB hub found
[   43.692385] hub 2-0:1.0: 8 ports detected
[   43.798378] r8169 Gigabit Ethernet driver 2.2LK loaded
[   43.798923] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[   43.798981] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNEB] -> GSI 19 (level, low) -> IRQ 19
[   43.799123] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   43.799303] eth0: RTL8168b/8111b at 0xffffc20000048000, 00:19:db:39:a5:06, IRQ 19
[   43.862064] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   44.004619] usb 1-1: configuration #1 chosen from 1 choice
[   44.493733] usb 2-7: new low speed USB device using ohci_hcd and address 2
[   44.716722] usb 2-7: configuration #1 chosen from 1 choice
[   44.941745] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc100035aa1a01]
[   54.188671] r8169: eth0: link down
[   54.970032] NET: Registered protocol family 10
[   54.970206] lo: Disabled Privacy Extensions
[   54.970313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.885613] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.887858] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.331977] input: PC Speaker as /class/input/input2
[   56.362832] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   56.362924] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   56.401092] Yenta: CardBus bridge found at 0000:05:04.0 [1462:3fcc]
[   56.401163] Yenta O2: res at 0x94/0xD4: 00/ea
[   56.401213] Yenta O2: enabling read prefetch/write burst
[   56.412711] sdhci: Secure Digital Host Controller Interface driver
[   56.412768] sdhci: Copyright(c) Pierre Ossman
[   56.532244] Yenta: ISA IRQ mask 0x0c38, PCI irq 17
[   56.532300] Socket status: 30000006
[   56.532347] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   56.532422] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   56.532471] pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfeafffff
[   56.532521] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
[   56.533093] sdhci: SDHCI controller found at 0000:05:04.2 [1217:7120] (rev 1)
[   56.533161] ACPI: PCI Interrupt 0000:05:04.2[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 17
[   56.533310] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   56.533419] mmc0: SDHCI at 0xfeafe400 irq 17 PIO
[   56.534008] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[   56.534070] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 16
[   56.534199] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   56.534252] RT61: Vendor = 0x1814, Product = 0x0302 
[   56.554784] usbcore: registered new interface driver hiddev
[   56.693648] input: Acrox USB & PS/2 Mouse as /class/input/input3
[   56.693765] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:0b.0-7
[   56.693906] usbcore: registered new interface driver usbhid
[   56.693956] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   56.928477] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   56.928542] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 23
[   56.928693] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   56.995894] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   57.182842] hdc: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   57.183178] Uniform CD-ROM driver Revision: 3.20
[   57.560366] fuse init (API version 7.8)
[   57.649236] lp: driver loaded but no devices found
[   57.741807] Adding 1004052k swap on /dev/disk/by-uuid/e7b6793a-c7a5-41e8-91a7-0bfb17259fb0.  Priority:-1 extents:1 across:1004052k
[   57.936280] EXT3 FS on sda2, internal journal
[   58.104215] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   58.176846] NTFS volume version 3.1.
[   59.474515] NET: Registered protocol family 17
[   97.749770] mtrr: type mismatch for c0000000,10000000 old: write-protect new: write-combining
```

Thanks for the help!

---

