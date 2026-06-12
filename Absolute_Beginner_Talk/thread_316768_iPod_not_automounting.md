---
title: "iPod not automounting"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by kurisutofuaa on 2006-12-11
Am on Edgy64 and my iPod Video 30gb doesn't want to automount for me anyone have any idea's why? also here is the dmesg
> 
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 0-80000000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fef0000
[    0.000000] On node 0 totalpages: 515403
[    0.000000]   DMA zone: 2591 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 512812 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 8000000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdb2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Disabling vsyscall due to use of PM timer
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[    0.000000] time.c: Detected 1989.839 MHz processor.
[   31.717134] Console: colour VGA+ 80x25
[   31.718223] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   31.719775] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.737681] Memory: 2052684k/2096064k available (2129k kernel code, 42992k reserved, 1424k data, 188k init)
[   31.813850] Calibrating delay using timer specific routine.. 3984.46 BogoMIPS (lpj=7968931)
[   31.813904] Security Framework v1.0.0 initialized
[   31.813910] SELinux:  Disabled at boot.
[   31.813931] Mount-cache hash table entries: 256
[   31.814053] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.814056] CPU: L2 Cache: 512K (64 bytes/line)
[   31.814059] CPU 0/0(2) -> Node 0 -> Core 0
[   31.814073] SMP alternatives: switching to UP code
[   31.814296] checking if image is initramfs... it is
[   32.300576] Freeing initrd memory: 5673k freed
[   32.303578] ACPI: Core revision 20060707
[   32.312544] ACPI: Looking for DSDT ... not found!
[   32.363551] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   32.403551] Using local APIC timer interrupts.
[   32.453750] result 12436511
[   32.453752] Detected 12.436 MHz APIC timer.
[   32.457354] SMP alternatives: switching to SMP code
[   32.457415] Booting processor 1/2 APIC 0x1
[   32.463865] Initializing CPU#1
[   32.541193] Calibrating delay using timer specific routine.. 3983.33 BogoMIPS (lpj=7966678)
[   32.541200] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.541202] CPU: L2 Cache: 512K (64 bytes/line)
[   32.541204] CPU 1/1(2) -> Node 0 -> Core 1
[   32.541277] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   32.545212] CPU 1: Syncing TSC to CPU 0.
[   32.549113] CPU 1: synchronized TSC with CPU 0 (last diff -76 cycles, maxerr 514 cycles)
[   32.549119] Brought up 2 CPUs
[   32.549156] testing NMI watchdog ... OK.
[   33.467967] migration_cost=171
[   33.468246] NET: Registered protocol family 16
[   33.468271] ACPI: bus type pci registered
[   33.471675] PCI: Using MMCONFIG at e0000000
[   33.471720] PCI: No mmconfig possible on device 0:18
[   33.484680] ACPI: Interpreter enabled
[   33.484682] ACPI: Using IOAPIC for interrupt routing
[   33.485247] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.485250] PCI: Probing PCI hardware (bus 00)
[   33.485342] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   33.487132] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   33.487435] Boot video device is 0000:01:00.0
[   33.487899] PCI: Transparent bridge - 0000:00:14.4
[   33.487940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.505665] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.505868] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.506068] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.506267] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.506465] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[   33.506666] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[   33.506865] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[   33.507065] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.507403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   33.509785] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.509797] pnp: PnP ACPI init
[   33.512478] pnp: PnP ACPI: found 12 devices
[   33.512529] PCI: Using ACPI for IRQ routing
[   33.512532] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.512541] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   33.512705] PCI-DMA: Disabling IOMMU.
[   33.513179] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   33.513183] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   33.513186] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   33.513189] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   33.513192] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   33.513195] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   33.513198] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   33.513201] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   33.513407] PCI: Bridge: 0000:00:02.0
[   33.513410]   IO window: e000-efff
[   33.513414]   MEM window: fdd00000-fddfffff
[   33.513417]   PREFETCH window: d0000000-dfffffff
[   33.513420] PCI: Bridge: 0000:00:14.4
[   33.513424]   IO window: d000-dfff
[   33.513430]   MEM window: fdc00000-fdcfffff
[   33.513435]   PREFETCH window: fde00000-fdefffff
[   33.513446] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.513496] NET: Registered protocol family 2
[   33.547874] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   33.548196] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   33.550333] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   33.550866] TCP: Hash tables configured (established 262144 bind 65536)
[   33.550869] TCP reno registered
[   33.551256] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   33.551613] audit: initializing netlink socket (disabled)
[   33.551623] audit(1165546059.260:1): initialized
[   33.551795] VFS: Disk quotas dquot_6.5.1
[   33.551820] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   33.551876] Initializing Cryptographic API
[   33.551880] io scheduler noop registered
[   33.551888] io scheduler anticipatory registered
[   33.551898] io scheduler deadline registered
[   33.551917] io scheduler cfq registered (default)
[   33.552413] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.552417] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[   33.552431] assign_interrupt_mode Found MSI capability
[   33.552466] Allocate Port Service[0000:00:02.0:pcie00]
[   33.552498] Allocate Port Service[0000:00:02.0:pcie01]
[   33.552527] Allocate Port Service[0000:00:02.0:pcie03]
[   33.572980] Real Time Clock Driver v1.12ac
[   33.573016] Linux agpgart interface v0.101 (c) Dave Jones
[   33.573019] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.573511] mice: PS/2 mouse device common for all mice
[   33.573993] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.574094] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.574097] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.574345] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   34.130491] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.131023] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.131586] TCP bic registered
[   34.131596] NET: Registered protocol family 1
[   34.131600] NET: Registered protocol family 8
[   34.131602] NET: Registered protocol family 20
[   34.140944] ACPI: (supports S0 S1 S3 S4 S5)
[   34.140988] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   34.141007] Freeing unused kernel memory: 188k freed
[   34.181118] input: AT Translated Set 2 keyboard as /class/input/input0
[   34.218044] vga16fb: initializing
[   34.218049] vga16fb: mapped to 0xffff8100000a0000
[   34.347672] Console: switching to colour frame buffer device 80x25
[   34.347679] fb0: VGA16 VGA frame buffer device
[   35.375883] Capability LSM initialized
[   35.406726] ACPI: Processor [CPU0] (supports 8 throttling states)
[   35.406739] ACPI: Processor [CPU1] (supports 8 throttling states)
[   35.738254] SCSI subsystem initialized
[   35.741742] libata version 1.20 loaded.
[   35.742763] sata_sil 0000:00:12.0: version 0.9
[   35.742786] GSI 16 sharing vector 0xC1 and IRQ 16
[   35.742790] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 193
[   35.743077] ata1: SATA max UDMA/100 cmd 0xFFFFC2000003A080 ctl 0xFFFFC2000003A08A bmdma 0xFFFFC2000003A000 irq 193
[   35.743104] ata2: SATA max UDMA/100 cmd 0xFFFFC2000003A0C0 ctl 0xFFFFC2000003A0CA bmdma 0xFFFFC2000003A008 irq 193
[   36.104777] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   36.117206] ata1: dev 0 cfg 49:2f00 82:7069 83:7c01 84:4023 85:7069 86:3c01 87:4023 88:203f
[   36.117210] ata1: dev 0 ATA-7, max UDMA/100, 488397168 sectors: LBA48
[   36.129190] ata1: dev 0 configured for UDMA/100
[   36.129196] scsi0 : sata_sil
[   36.492311] ata2: SATA link up 1.5 Gbps (SStatus 113)
[   36.504740] ata2: dev 0 cfg 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3c01 87:4003 88:203f
[   36.504744] ata2: dev 0 ATA-6, max UDMA/100, 625142448 sectors: LBA48
[   36.516723] ata2: dev 0 configured for UDMA/100
[   36.516728] scsi1 : sata_sil
[   36.516820]   Vendor: ATA       Model: WDC WD2500JS-60M  Rev: 10.0
[   36.516828]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   36.516898]   Vendor: ATA       Model: WDC WD3200JD-22K  Rev: 08.0
[   36.516905]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   36.524148] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   36.524159] sda: Write Protect is off
[   36.524162] sda: Mode Sense: 00 3a 00 00
[   36.524174] SCSI device sda: drive cache: write back
[   36.524217] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   36.524225] sda: Write Protect is off
[   36.524227] sda: Mode Sense: 00 3a 00 00
[   36.524248] SCSI device sda: drive cache: write back
[   36.524252]  sda: sda2
[   36.531233] sd 0:0:0:0: Attached scsi disk sda
[   36.531265] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   36.531273] sdb: Write Protect is off
[   36.531275] sdb: Mode Sense: 00 3a 00 00
[   36.531287] SCSI device sdb: drive cache: write back
[   36.531315] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   36.531325] sdb: Write Protect is off
[   36.531327] sdb: Mode Sense: 00 3a 00 00
[   36.531339] SCSI device sdb: drive cache: write back
[   36.531341]  sdb: sdb1 < sdb5 sdb6 > sdb2
[   36.561700] sd 1:0:0:0: Attached scsi disk sdb
[   36.917601] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   36.917620] GSI 17 sharing vector 0xC9 and IRQ 17
[   36.917623] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 201
[   36.917633] ATIIXP: chipset revision 0
[   36.917635] ATIIXP: not 100% native mode: will probe irqs later
[   36.917644]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[   36.917656]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[   36.917664] Probing IDE interface ide0...
[   37.487086] Probing IDE interface ide1...
[   38.226627] hdc: TSSTcorpCD/DVDW TS-H552L, ATAPI CD/DVD-ROM drive
[   39.013680] hdd: TSSTcorpDVD-ROM TS-H352C, ATAPI CD/DVD-ROM drive
[   39.073791] ide1 at 0x170-0x177,0x376 on irq 15
[   39.125041] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   39.125049] Uniform CD-ROM driver Revision: 3.20
[   39.128217] hdd: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
[   39.216382] Probing IDE interface ide0...
[   39.225458] usbcore: registered new driver usbfs
[   39.225478] usbcore: registered new driver hub
[   39.226279] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   39.226310] GSI 18 sharing vector 0xD1 and IRQ 18
[   39.226314] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 209
[   39.226537] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   39.226669] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   39.258171] ohci_hcd 0000:00:13.0: irq 209, io mem 0xfe02e000
[   39.269817] ieee1394: Initialized config rom entry `ip1394'
[   39.320970] usb usb1: configuration #1 chosen from 1 choice
[   39.320992] hub 1-0:1.0: USB hub found
[   39.321003] hub 1-0:1.0: 4 ports detected
[   39.424827] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 209
[   39.425004] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   39.425066] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   39.868504] APIC error on CPU0: 00(40)
[   39.920656] irq 209: nobody cared (try booting with the "irqpoll" option)
[   39.920659] 
[   39.920660] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[   39.920672]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff880c6bb8>{:usbcore:usb_hcd_irq+40}
[   39.920702]        <ffffffff802b6190>{__do_IRQ+224} <ffffffff802737e2>{do_IRQ+66}
[   39.920711]        <ffffffff80271f00>{default_idle+0} <ffffffff80265d08>{ret_from_intr+0} <EOI>
[   39.920721]        <ffffffff80269d9f>{thread_return+0} <ffffffff80271f29>{default_idle+41}
[   39.920732]        <ffffffff8024ecfe>{cpu_idle+158} <ffffffff8060885b>{start_kernel+523}
[   39.920742]        <ffffffff80608293>{_sinittext+659}
[   39.920747] handlers:
[   39.920749] [<ffffffff880c6b90>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   39.920766] Disabling IRQ #209
[   39.920823] ohci_hcd 0000:00:13.1: irq 209, io mem 0xfe02d000
[   39.984201] usb usb2: configuration #1 chosen from 1 choice
[   39.984225] hub 2-0:1.0: USB hub found
[   39.984237] hub 2-0:1.0: 4 ports detected
[   40.088116] GSI 19 sharing vector 0xD9 and IRQ 19
[   40.088121] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 217
[   40.088127] PCI: Via IRQ fixup for 0000:02:04.0, from 255 to 9
[   40.088288] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 209
[   40.088464] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   40.088521] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   40.088577] ehci_hcd 0000:00:13.2: irq 209, io mem 0xfe02c000
[   40.088589] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.088641] usb usb3: configuration #1 chosen from 1 choice
[   40.088660] hub 3-0:1.0: USB hub found
[   40.088666] hub 3-0:1.0: 8 ports detected
[   40.142399] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   40.241897] Attempting manual resume
[   40.252887] EXT3-fs: INFO: recovery required on readonly filesystem.
[   40.252891] EXT3-fs: write access will be enabled during recovery.
[   41.422889] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000bb34af]
[   43.217722] kjournald starting.  Commit interval 5 seconds
[   43.217737] EXT3-fs: recovery complete.
[   43.222097] EXT3-fs: mounted filesystem with ordered data mode.
[   50.909366] input: PC Speaker as /class/input/input1
[   51.193706] 8139too Fast Ethernet driver 0.9.27
[   51.193754] GSI 20 sharing vector 0xE1 and IRQ 20
[   51.193757] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 225
[   51.194576] eth0: RealTek RTL8139 at 0xffffc2001009a000, 00:13:d3:5c:2a:74, IRQ 225
[   51.194579] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   51.200273] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   51.224532] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   51.239880] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.319982] parport: PnPBIOS parport detected.
[   51.320031] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   51.376204] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.674044] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   51.674074] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   51.704866] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   51.731634] ts: Compaq touchscreen protocol output
[   51.854737] GSI 21 sharing vector 0xA9 and IRQ 21
[   51.854741] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 169
[   52.001319] lp0: using parport0 (interrupt-driven).
[   52.032043] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   52.032047] ieee1394: sbp2: Try serialize_io=0 for better performance
[   52.065740] Adding 6032368k swap on /dev/disk/by-uuid/3f593ca1-1539-49af-b531-7337831a09d6.  Priority:-1 extents:1 across:6032368k
[   52.099059] EXT3 FS on sdb2, internal journal
[   52.259439] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   52.449918] NET: Registered protocol family 17
[   54.560140] ACPI: Power Button (FF) [PWRF]
[   54.560150] ACPI: Power Button (CM) [PWRB]
[   54.670933] ibm_acpi: ec object not found
[   54.702061] pcc_acpi: loading...
[   54.972251] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   54.972246] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8 (1350 mV)
[   54.972250] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[   54.972253] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   54.972258] cpu_init done, current fid 0xc, vid 0x8
[   57.856394] NET: Registered protocol family 10
[   57.856488] lo: Disabled Privacy Extensions
[   57.856608] IPv6 over IPv4 tunneling driver
[   57.942142] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   57.945841] [fglrx] Maximum main memory to use for locked dma buffers: 1883 MBytes.
[   57.945927] [fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
[   57.974910] GSI 22 sharing vector 0xE9 and IRQ 22
[   57.974916] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 233
[   59.354366] [fglrx] total      GART = 134217728
[   59.354372] [fglrx] free       GART = 118226944
[   59.354375] [fglrx] max single GART = 118226944
[   59.354377] [fglrx] total      LFB  = 126742528
[   59.354379] [fglrx] free       LFB  = 116256768
[   59.354381] [fglrx] max single LFB  = 116256768
[   59.354383] [fglrx] total      Inv  = 134217728
[   59.354386] [fglrx] free       Inv  = 134217728
[   59.354388] [fglrx] max single Inv  = 134217728
[   59.354389] [fglrx] total      TIM  = 0
[   60.786491] /dev/vmmon[4388]: Module vmmon: registered with major=10 minor=165
[   60.786604] /dev/vmmon[4388]: Module vmmon: initialized
[   60.871677] /dev/vmnet: open called by PID 4414 (vmnet-bridge)
[   60.871714] /dev/vmnet: hub 0 does not exist, allocating memory.
[   60.871737] /dev/vmnet: port on hub 0 successfully opened
[   60.871818] bridge-eth0: enabling the bridge
[   60.871828] bridge-eth0: up
[   60.871835] bridge-eth0: already up
[   60.871844] bridge-eth0: attached
[   60.971853] /dev/vmnet: open called by PID 4429 (vmnet-netifup)
[   60.971864] /dev/vmnet: hub 1 does not exist, allocating memory.
[   60.971878] /dev/vmnet: port on hub 1 successfully opened
[   60.973297] /dev/vmnet: open called by PID 4428 (vmnet-natd)
[   60.973308] /dev/vmnet: hub 8 does not exist, allocating memory.
[   60.973321] /dev/vmnet: port on hub 8 successfully opened
[   60.975379] /dev/vmnet: open called by PID 4430 (vmnet-netifup)
[   60.975503] /dev/vmnet: port on hub 8 successfully opened
[   61.096441] Bluetooth: Core ver 2.8
[   61.096447] NET: Registered protocol family 31
[   61.096449] Bluetooth: HCI device and connection manager initialized
[   61.096463] Bluetooth: HCI socket layer initialized
[   61.156276] Bluetooth: L2CAP ver 2.8
[   61.156281] Bluetooth: L2CAP socket layer initialized
[   61.176745] Bluetooth: RFCOMM socket layer initialized
[   61.176822] Bluetooth: RFCOMM TTY layer initialized
[   61.176824] Bluetooth: RFCOMM ver 1.7
[   61.289327] /dev/vmnet: open called by PID 4452 (vmnet-dhcpd)
[   61.289342] /dev/vmnet: port on hub 1 successfully opened
[   61.290256] /dev/vmnet: open called by PID 4461 (vmnet-dhcpd)
[   61.290269] /dev/vmnet: port on hub 8 successfully opened
[   66.843484] vmnet8: no IPv6 routers present
[   66.845481] vmnet1: no IPv6 routers present
[   69.570203] eth0: no IPv6 routers present
[  262.115467] APIC error on CPU0: 40(40)
[  677.476673] APIC error on CPU0: 40(40)
[  953.854274] ip_tables: (C) 2000-2006 Netfilter Core Team
[  953.918759] Netfilter messages via NETLINK v0.30.
[  953.927203] ip_conntrack version 2.4 (8192 buckets, 65536 max) - 304 bytes per conntrack
[ 1361.080620] APIC error on CPU0: 40(40)
[ 2283.194353] APIC error on CPU0: 40(40)
[ 2414.602604] APIC error on CPU0: 40(40)
[ 2420.234101] APIC error on CPU0: 40(40)
[ 3448.366889] APIC error on CPU0: 40(40)
[ 7384.614910] APIC error on CPU0: 40(40)
[ 8351.256893] APIC error on CPU0: 40(40)
[ 8707.913129] APIC error on CPU0: 40(40)
[ 9003.372755] APIC error on CPU0: 40(40)
[ 9795.929669] APIC error on CPU0: 40(40)
[10306.851757] APIC error on CPU0: 40(40)
[10721.918526] APIC error on CPU0: 40(40)
[11920.260898] APIC error on CPU0: 40(40)
[12613.196863] APIC error on CPU0: 40(40)
[12613.549495] Losing some ticks... checking if CPU frequency changed.
[12750.296593] APIC error on CPU0: 40(40)
[13368.177196] APIC error on CPU0: 40(40)
[14508.777010] APIC error on CPU0: 40(40)
[15237.609531] APIC error on CPU0: 40(40)
[16084.657520] APIC error on CPU0: 40(40)
[16772.139813] APIC error on CPU0: 40(40)
[17200.373387] APIC error on CPU0: 40(40)
[17594.758030] APIC error on CPU0: 40(40)
[18128.126248] APIC error on CPU0: 40(40)
[18364.769039] APIC error on CPU0: 40(40)
[18916.975482] APIC error on CPU0: 40(40)
[19628.867565] APIC error on CPU0: 40(40)
[19752.840432] APIC error on CPU0: 40(40)
[20337.503399] APIC error on CPU0: 40(40)
[20521.423051] APIC error on CPU0: 40(40)
[20968.279117] APIC error on CPU0: 40(40)
[21712.116304] APIC error on CPU0: 40(40)
[21990.103364] APIC error on CPU0: 40(40)
[22399.538653] APIC error on CPU0: 40(40)
[22998.700866] APIC error on CPU0: 40(40)
[23415.953161] APIC error on CPU0: 40(40)
[24024.316759] APIC error on CPU0: 40(40)
[24238.489473] APIC error on CPU0: 40(40)
[25654.698380] APIC error on CPU0: 40(40)
[26378.097196] APIC error on CPU0: 40(40)
[28852.176630] APIC error on CPU0: 40(40)
[28925.028522] APIC error on CPU0: 40(40)
[29356.254650] APIC error on CPU0: 40(40)
[29400.419655] APIC error on CPU0: 40(40)
[29633.112991] APIC error on CPU0: 40(40)
[30720.671342] APIC error on CPU0: 40(40)
[31386.894172] APIC error on CPU0: 40(40)
[31487.074508] APIC error on CPU0: 40(40)
[31723.737258] APIC error on CPU0: 40(40)
[32803.228911] APIC error on CPU0: 40(40)
[32965.549505] APIC error on CPU0: 40(40)
[33271.773966] APIC error on CPU0: 40(40)
[41980.734816] APIC error on CPU0: 40(40)
[44085.506695] APIC error on CPU0: 40(40)
[45687.047791] APIC error on CPU0: 40(40)
[46540.531125] APIC error on CPU0: 40(40)
[47630.653539] /dev/vmmon[24378]: Module vmmon: unloaded
[47630.818009] bridge-eth0: down
[47630.818064] bridge-eth0: detached
[51587.787542] APIC error on CPU0: 40(40)
[52910.492759] APIC error on CPU0: 40(40)
[53923.192019] APIC error on CPU0: 40(40)
[54062.400407] APIC error on CPU0: 40(40)
[54779.370151] APIC error on CPU0: 40(40)
[63841.136183] APIC error on CPU0: 40(40)
[65326.600864] APIC error on CPU0: 40(40)
[65667.035813] APIC error on CPU0: 40(40)
[66815.495732] APIC error on CPU0: 40(40)
[66979.507584] APIC error on CPU0: 40(40)
[68044.527198] APIC error on CPU0: 40(40)
[68082.081303] APIC error on CPU0: 40(40)
[69163.877454] APIC error on CPU0: 40(40)
[70943.470105] APIC error on CPU0: 40(40)
[71350.702721] APIC error on CPU0: 40(40)
[71644.226519] APIC error on CPU0: 40(40)
[71718.594687] APIC error on CPU0: 40(40)
[73355.519574] APIC error on CPU0: 40(40)
[75927.950457] APIC error on CPU0: 40(40)
[81339.319102] APIC error on CPU0: 40(40)
[81793.097742] APIC error on CPU0: 40(40)
[83246.086819] APIC error on CPU0: 40(40)
[91224.091723] APIC error on CPU0: 40(40)
[91638.774951] APIC error on CPU0: 40(40)
[94958.787902] APIC error on CPU0: 40(40)
[95743.813344] APIC error on CPU0: 40(40)
[100919.754005] APIC error on CPU0: 40(40)
[101309.225774] APIC error on CPU0: 40(40)
[101956.285339] APIC error on CPU0: 40(40)
[102877.822003] APIC error on CPU0: 40(40)
[103567.609760] usb 3-7: new high speed USB device using ehci_hcd and address 3
[103568.109179] ehci_hcd 0000:00:13.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[103573.375217] usb 3-7: device not accepting address 3, error -110
[103573.431156] usb 3-7: new high speed USB device using ehci_hcd and address 4
[103579.198599] usb 3-7: device not accepting address 4, error -110
[103579.254553] usb 3-7: new high speed USB device using ehci_hcd and address 5
[103584.460498] usb 3-7: device not accepting address 5, error -110
[103584.516440] usb 3-7: new high speed USB device using ehci_hcd and address 6
[103589.722410] usb 3-7: device not accepting address 6, error -110
[103626.516648] usb 3-5: new high speed USB device using ehci_hcd and address 7
[103632.290112] usb 3-5: device not accepting address 7, error -110
[103632.346059] usb 3-5: new high speed USB device using ehci_hcd and address 8
[103638.113522] usb 3-5: device not accepting address 8, error -110
[103638.169470] usb 3-5: new high speed USB device using ehci_hcd and address 9
[103643.375433] usb 3-5: device not accepting address 9, error -110
[103643.431372] usb 3-5: new high speed USB device using ehci_hcd and address 10
[103648.637344] usb 3-5: device not accepting address 10, error -110
[103722.553443] usb 3-2: new high speed USB device using ehci_hcd and address 11
[103728.318920] usb 3-2: device not accepting address 11, error -110
[103728.374862] usb 3-2: new high speed USB device using ehci_hcd and address 12
[103734.142309] usb 3-2: device not accepting address 12, error -110
[103734.198250] usb 3-2: new high speed USB device using ehci_hcd and address 13
[103739.404211] usb 3-2: device not accepting address 13, error -110
[103739.460142] usb 3-2: new high speed USB device using ehci_hcd and address 14
[103744.666106] usb 3-2: device not accepting address 14, error -110
[105238.022880] usb 3-5: new high speed USB device using ehci_hcd and address 15
[105243.790320] usb 3-5: device not accepting address 15, error -110
[105243.846263] usb 3-5: new high speed USB device using ehci_hcd and address 16
[105249.611685] usb 3-5: device not accepting address 16, error -110
[105249.667623] usb 3-5: new high speed USB device using ehci_hcd and address 17
[105254.873574] usb 3-5: device not accepting address 17, error -110
[105254.929514] usb 3-5: new high speed USB device using ehci_hcd and address 18
[105260.135469] usb 3-5: device not accepting address 18, error -110
[105385.562920] FAT: bogus number of reserved sectors
[105385.562927] VFS: Can't find a valid FAT filesystem on dev sda2.
[105416.375617] usb 3-1: new high speed USB device using ehci_hcd and address 19
[105422.141095] usb 3-1: device not accepting address 19, error -110
[105422.197024] usb 3-1: new high speed USB device using ehci_hcd and address 20
[105427.962482] usb 3-1: device not accepting address 20, error -110
[105428.018422] usb 3-1: new high speed USB device using ehci_hcd and address 21
[105433.224390] usb 3-1: device not accepting address 21, error -110
[105433.280331] usb 3-1: new high speed USB device using ehci_hcd and address 22
[105438.486298] usb 3-1: device not accepting address 22, error -110
[105511.442122] APIC error on CPU0: 40(40)
[105898.091201] NTFS volume version 3.1.
[105951.804856] APIC error on CPU0: 40(40)
[105998.129269] APIC error on CPU0: 40(40)


I hope this helps.

---

### Post by kinematic on 2006-12-11
don't you have to access your ipod with gtkpod or amarok?

---

### Post by kurisutofuaa on 2006-12-12
> **kinematic said:**
> don't you have to access your ipod with gtkpod or amarok?

Nope cant access it with either of them.

---

### Post by ctsdownloads on 2007-01-01
Is it formated for Windows? Did you already sync it with iTunes in Windows/OS X?

---

