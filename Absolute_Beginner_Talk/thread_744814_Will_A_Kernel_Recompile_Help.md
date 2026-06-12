---
title: "Will A Kernel Recompile Help?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-04-04
I got an Emachines computer and for some reason none of my USB mice work with it.  They all worked with my old dell.  But what i was thinking is maybe the onboard USB isn't supported or something.  So would it be a good idea to recompile the kernel, i heard it sometimes helps with unsupported hardware.... If you can't tell this entire process and concept is really foriegn to me.  Thanks

---

### Post by Whiffle on 2008-04-04
I very strongly doubt it.  Unplug your mouse, wait a bit, then plug it back in.  Run "dmesg" in a terminal.  Does anything come up?  Also, are these mice plugged into a hub?

---

### Post by The Titan on 2008-04-04
```


[    0.000000] Linux version 2.6.24-12-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 23:01:54 UTC 2008 (Ubuntu 2.6.24-12.22-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4840
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6670 checksum 0
[    0.000000] ACPI: RSDP 000F6670, 0014 (r0 FIC   )
[    0.000000] ACPI: RSDT 1FFF3000, 0030 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 3918 (r1 FIC    AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: DBGP 1FFF6A80, 0034 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: APIC 1FFF6A00, 0054 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=0493b21b-65ec-4149-b207-45259a155d9a ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1992.686 MHz processor.
[   16.217888] Console: colour VGA+ 80x25
[   16.217893] console [tty0] enabled
[   16.218400] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.218873] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.235603] Memory: 507284k/524224k available (2164k kernel code, 16320k reserved, 1007k data, 364k init, 0k highmem)
[   16.235615] virtual kernel memory layout:
[   16.235616]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.235618]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.235619]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   16.235621]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   16.235623]       .init : 0xc041f000 - 0xc047a000   ( 364 kB)
[   16.235624]       .data : 0xc031d1bd - 0xc0418dc4   (1007 kB)
[   16.235626]       .text : 0xc0100000 - 0xc031d1bd   (2164 kB)
[   16.235630] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.235679] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.315571] Calibrating delay using timer specific routine.. 3989.55 BogoMIPS (lpj=7979102)
[   16.315602] Security Framework initialized
[   16.315611] SELinux:  Disabled at boot.
[   16.315629] AppArmor: AppArmor initialized
[   16.315635] Failure registering capabilities with primary security module.
[   16.315647] Mount-cache hash table entries: 512
[   16.315827] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   16.315845] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.315849] CPU: L2 cache: 512K
[   16.315852] CPU: Hyper-Threading is disabled
[   16.315855] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[   16.315871] Compat vDSO mapped to ffffe000.
[   16.315888] Checking 'hlt' instruction... OK.
[   16.332077] SMP alternatives: switching to UP code
[   16.334239] Freeing SMP alternatives: 11k freed
[   16.334427] Early unpacking initramfs... done
[   16.802751] ACPI: Core revision 20070126
[   16.802826] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.857954] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[   16.858003] Total of 1 processors activated (3989.55 BogoMIPS).
[   16.858150] ENABLING IO-APIC IRQs
[   16.858339] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.002483] Brought up 1 CPUs
[   17.002516] CPU0 attaching sched-domain:
[   17.002521]  domain 0: span 01
[   17.002523]   groups: 01
[   17.002785] net_namespace: 64 bytes
[   17.002798] Booting paravirtualized kernel on bare hardware
[   17.003754] Time:  1:48:25  Date: 04/03/08
[   17.003835] NET: Registered protocol family 16
[   17.004146] EISA bus registered
[   17.004178] ACPI: bus type pci registered
[   17.029669] PCI: PCI BIOS revision 2.10 entry at 0xfb180, last bus=2
[   17.029672] PCI: Using configuration type 1
[   17.029675] Setting up standard PCI resources
[   17.039483] ACPI: EC: Look up EC in DSDT
[   17.043859] ACPI: Interpreter enabled
[   17.043864] ACPI: (supports S0 S3 S4 S5)
[   17.043885] ACPI: Using IOAPIC for interrupt routing
[   17.049632] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.050149] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   17.050151] * this clock source is slow. If you are sure your timer does not have
[   17.050153] * this bug, please use "acpi_pm_good" to disable the workaround
[   17.050208] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   17.050212] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   17.050786] PCI: Transparent bridge - 0000:00:1e.0
[   17.050822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.051039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   17.069264] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 9 11 12 14 15)
[   17.069412] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 11 12 14 15)
[   17.069554] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 11 12 14 15)
[   17.069696] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *11 12 14 15)
[   17.069837] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.069981] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.070124] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.070270] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 *11 12 14 15)
[   17.070447] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.070496] pnp: PnP ACPI init
[   17.070508] ACPI: bus type pnp registered
[   17.074057] pnp: PnP ACPI: found 14 devices
[   17.074060] ACPI: ACPI bus type pnp unregistered
[   17.074068] PnPBIOS: Disabled by ACPI PNP
[   17.074455] PCI: Using ACPI for IRQ routing
[   17.074459] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.102267] NET: Registered protocol family 8
[   17.102270] NET: Registered protocol family 20
[   17.102378] AppArmor: AppArmor Filesystem Enabled
[   17.106248] Time: tsc clocksource has been installed.
[   17.114292] system 00:00: ioport range 0x280-0x287 has been reserved
[   17.114304] system 00:01: iomem range 0xd0000-0xd3fff has been reserved
[   17.114308] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
[   17.114312] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[   17.114316] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
[   17.114320] system 00:01: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   17.114324] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[   17.114327] system 00:01: iomem range 0x100000-0x1ffeffff could not be reserved
[   17.114332] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.114336] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.114340] system 00:01: iomem range 0xffb00000-0xffbfffff could not be reserved
[   17.114344] system 00:01: iomem range 0xfff00000-0xffffffff could not be reserved
[   17.114348] system 00:01: iomem range 0xe0000-0xeffff has been reserved
[   17.114358] system 00:03: ioport range 0x400-0x4bf could not be reserved
[   17.114366] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   17.114370] system 00:04: ioport range 0x800-0x87f has been reserved
[   17.144982] PCI: Bridge: 0000:00:01.0
[   17.144985]   IO window: disabled.
[   17.144992]   MEM window: e0000000-e1ffffff
[   17.144997]   PREFETCH window: d8000000-dfffffff
[   17.145005] PCI: Bridge: 0000:00:1e.0
[   17.145010]   IO window: c000-cfff
[   17.145017]   MEM window: e2000000-e3ffffff
[   17.145021]   PREFETCH window: disabled.
[   17.145045] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.145061] NET: Registered protocol family 2
[   17.182253] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   17.182667] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   17.182789] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   17.182909] TCP: Hash tables configured (established 16384 bind 16384)
[   17.182912] TCP reno registered
[   17.194299] checking if image is initramfs... it is
[   17.645349] Switched to high resolution mode on CPU 0
[   18.112690] Freeing initrd memory: 7697k freed
[   18.113532] audit: initializing netlink socket (disabled)
[   18.113554] audit(1207187305.728:1): initialized
[   18.116644] VFS: Disk quotas dquot_6.5.1
[   18.116772] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.116989] io scheduler noop registered
[   18.116993] io scheduler anticipatory registered
[   18.116996] io scheduler deadline registered
[   18.117013] io scheduler cfq registered (default)
[   18.117098] Boot video device is 0000:01:00.0
[   18.117500] isapnp: Scanning for PnP cards...
[   18.471123] isapnp: No Plug & Play device found
[   18.515270] Real Time Clock Driver v1.12ac
[   18.515408] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.515566] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.516644] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.517845] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.517951] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.518114] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.521159] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.521166] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.527967] mice: PS/2 mouse device common for all mice
[   18.528155] EISA: Probing bus 0 at eisa.0
[   18.528197] EISA: Detected 0 cards.
[   18.528202] cpuidle: using governor ladder
[   18.528204] cpuidle: using governor menu
[   18.528339] NET: Registered protocol family 1
[   18.528385] Using IPI No-Shortcut mode
[   18.528429] registered taskstats version 1
[   18.528547]   Magic number: 4:102:811
[   18.528645]   hash matches device ptys5
[   18.528692] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.528694] EDD information not available.
[   18.529242] Freeing unused kernel memory: 364k freed
[   18.555741] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.848317] fuse init (API version 7.9)
[   19.881499] ACPI: Processor [CPU0] (supports 2 throttling states)
[   19.909433] ACPI: Thermal Zone [THRM] (40 C)
[   20.727951] usbcore: registered new interface driver usbfs
[   20.727987] usbcore: registered new interface driver hub
[   20.739918] usbcore: registered new device driver usb
[   20.759846] USB Universal Host Controller Interface driver v3.0
[   20.759948] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.759966] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.759971] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.760391] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.760427] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   20.760631] usb usb1: configuration #1 chosen from 1 choice
[   20.760665] hub 1-0:1.0: USB hub found
[   20.760675] hub 1-0:1.0: 2 ports detected
[   20.840398] SCSI subsystem initialized
[   20.863753] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 17
[   20.863771] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.863776] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.863811] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.863844] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   20.864017] usb usb2: configuration #1 chosen from 1 choice
[   20.864051] hub 2-0:1.0: USB hub found
[   20.864060] hub 2-0:1.0: 2 ports detected
[   20.917013] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.918757] libata version 3.00 loaded.
[   20.967581] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.967599] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.967604] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.967649] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.967682] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   20.967856] usb usb3: configuration #1 chosen from 1 choice
[   20.967890] hub 3-0:1.0: USB hub found
[   20.967899] hub 3-0:1.0: 2 ports detected
[   21.070474] FDC 0 is a post-1991 82077
[   21.071707] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   21.071728] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.071733] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.071776] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   21.075700] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   21.075716] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe4000000
[   21.091205] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.091394] usb usb4: configuration #1 chosen from 1 choice
[   21.091430] hub 4-0:1.0: USB hub found
[   21.091441] hub 4-0:1.0: 6 ports detected
[   21.195323] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   21.195334] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[   21.199081] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.199159] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.199178] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   21.201303] 8139too Fast Ethernet driver 0.9.28
[   21.201385] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   21.202206] eth0: RealTek RTL8139 at 0xc000, 00:40:ca:34:2a:53, IRQ 17
[   21.202213] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.209528] ata_piix 0000:00:1f.1: version 2.12
[   21.209556] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.209628] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.210919] scsi0 : ata_piix
[   21.212157] scsi1 : ata_piix
[   21.213032] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   21.213037] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   21.530884] ata1.00: ATAPI: MAD DOG MD-16XDVD9, 2.FA, max UDMA/33
[   21.694495] ata1.00: configured for UDMA/33
[   21.858304] ata2.00: ATA-6: WDC WD400BB-00LNA0, 05.01C05, max UDMA/100
[   21.858311] ata2.00: 78165360 sectors, multi 16: LBA
[   21.858332] ata2.00: limited to UDMA/33 due to 40-wire cable
[   21.866263] ata2.00: configured for UDMA/33
[   21.867636] scsi 0:0:0:0: CD-ROM            MAD DOG  MD-16XDVD9       2.FA PQ: 0 ANSI: 5
[   21.867860] scsi 1:0:0:0: Direct-Access     ATA      WDC WD400BB-00LN 05.0 PQ: 0 ANSI: 5
[   21.946286] Driver 'sd' needs updating - please use bus_type methods
[   21.949710] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.949732] sd 1:0:0:0: [sda] Write Protect is off
[   21.949736] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.949766] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.949847] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.949864] sd 1:0:0:0: [sda] Write Protect is off
[   21.949868] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.949895] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.949899]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.953340] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   21.953348] Uniform CD-ROM driver Revision: 3.20
[   21.953429] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.960935]  sda1 sda2 < sda5 >
[   21.980983] sd 1:0:0:0: [sda] Attached SCSI disk
[   21.994137] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   21.994169] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   22.212645] Attempting manual resume
[   22.212651] swsusp: Resume From Partition 8:5
[   22.212654] PM: Checking swsusp image.
[   22.212970] PM: Resume from disk failed.
[   22.257885] kjournald starting.  Commit interval 5 seconds
[   22.257907] EXT3-fs: mounted filesystem with ordered data mode.
[   31.129479] Linux agpgart interface v0.102
[   31.193845] agpgart: Detected an Intel 830M Chipset.
[   31.233240] agpgart: AGP aperture is 128M @ 0xd0000000
[   31.250364] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.301419] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.349376] iTCO_vendor_support: vendor-support=0
[   31.389688] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.390250] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   31.390316] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.624563] intel_rng: FWH not detected
[   31.672704] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.956219] input: Power Button (FF) as /devices/virtual/input/input3
[   31.967946] ACPI: Power Button (FF) [PWRF]
[   31.968099] input: Power Button (CM) as /devices/virtual/input/input4
[   31.979905] ACPI: Power Button (CM) [PWRB]
[   33.795614] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[   33.808065] parport_pc 00:0b: reported by Plug and Play ACPI
[   33.808124] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.816361] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   35.287420] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   35.550028] NET: Registered protocol family 10
[   35.550420] lo: Disabled Privacy Extensions
[   37.769007] loop: module loaded
[   37.814187] lp0: using parport0 (interrupt-driven).
[   38.025371] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   38.737302] EXT3 FS on sda1, internal journal
[   38.910753] device-mapper: uevent: version 1.0.3
[   38.910798] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   40.160917] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.668997] No dock devices found.
[   43.864973] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   43.864981] apm: overridden by ACPI.
[   44.232755] ppdev: user-space parallel port driver
[   45.967134] eth0: no IPv6 routers present
[   47.846721] Bluetooth: Core ver 2.11
[   47.848280] NET: Registered protocol family 31
[   47.848287] Bluetooth: HCI device and connection manager initialized
[   47.848293] Bluetooth: HCI socket layer initialized
[   47.916057] Bluetooth: L2CAP ver 2.9
[   47.916064] Bluetooth: L2CAP socket layer initialized
[   48.016085] Bluetooth: RFCOMM socket layer initialized
[   48.016110] Bluetooth: RFCOMM TTY layer initialized
[   48.016113] Bluetooth: RFCOMM ver 1.8
[ 1415.468010] nvidia: module license 'NVIDIA' taints kernel.
[ 1415.727410] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 1415.728975] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[ 1415.800324] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 1415.801435] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 1415.802356] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 1493.750752] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 1493.751864] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 1493.752778] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 2711.806504] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 2711.807656] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 2711.808532] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 4065.860899] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 4065.862108] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 4065.862979] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 4354.425053] compiz.real[7606]: segfault at 02470002 eip 08055a60 esp bf842e10 error 4
[ 4354.760805] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 4354.770254] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 4354.771308] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 4450.076948] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 4450.078021] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 4450.078935] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 4856.142936] compiz.real[8354]: segfault at 61745f70 eip 08055a60 esp bfc57220 error 4
[ 4856.500382] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 4856.501496] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 4856.502410] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[40168.145591] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40168.145972] NVRM: Xid (0001:00): 29,  L1 -> L0
[40168.747045] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40168.747425] NVRM: Xid (0001:00): 29,  L0 -> L0
[40168.798945] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40168.850484] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40168.899494] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40168.949763] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.000483] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.050836] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.109055] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.161183] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.211462] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.262372] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.313486] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[40169.362984] NVRM: Xid (0001:00): 13, 0003 beef3097 00003497 00001a04 fffffffd 00000002
[63934.808369] RPC: Registered udp transport module.
[63934.808377] RPC: Registered tcp transport module.
titan@dungeon:~$       

```I would have cropped that a bit but i don't know what im looking for so sorry it is so long.  They are not on a hub, its all onboard.  But the light on the mouse is on so i know it's hooked up right and i know that is enabled in the bios too.... I really wish i could get this working because i am using this ANCIENT mouse (tandy 25-1042) and it is really horrible.

EDIT: Also the onboard sound dosent work either but the onboard lan works.. if that matters

---

### Post by Whiffle on 2008-04-04
hmm thsi is what I get when I connect my mouse:
```

usb 4-3.4: new low speed USB device using ehci_hcd and address 6
usb 4-3.4: configuration #1 chosen from 1 choice
input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:03.3/usb4/4-3/4-3.4/4-3.4:1.0/input/input8
input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.3-3.4

```

what does the output of "lsusb"  show while the mouse is plugged in?

---

### Post by The Titan on 2008-04-04
```

titan@dungeon:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
titan@dungeon:~$

```

hmm, does this mean that it dosent see anything connected?

---

### Post by Crafty Kisses on 2008-04-04
I doubt recompiling the kernel will help in this situation, post the following output:
```
lspci
```
After that you can try this:
```
lsub
```

---

### Post by The Titan on 2008-04-04
> **Codename said:**
> I doubt recompiling the kernel will help in this situation, post the following output:
```
lspci
```
After that you can try this:
```
lsub
```
lspci:
```


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
titan@dungeon:~$ 

```
lsub isn't a command.

---

### Post by Whiffle on 2008-04-04
Thats pretty weird.  It sees the USB hardware in the computer, but no mice.  Have you tried all the USB ports?  You might also poke around in the BIOS a bit and see if theres any suspicious usb settings.

---

### Post by Crafty Kisses on 2008-04-04
Sorry the command was the following:
```
lsusb
```

---

### Post by The Titan on 2008-04-04
i already posted the output of that in post #5 :).  After i post that is when people usually stop responding so there must be something really strange about it and nobody will tell me....

---

### Post by ajmorris on 2008-04-04
hi there,
could you please post your /etc/X11/xorg.conf file, sometimes the mouse driver that you have set in there, conflicts with the usb mouse.

and please post your /var/log/Xorg.0.log file

AJ

---

### Post by The Titan on 2008-04-04
> **ajmorris said:**
> hi there,
could you please post your /etc/X11/xorg.conf file, sometimes the mouse driver that you have set in there, conflicts with the usb mouse.

and please post your /var/log/Xorg.0.log file

AJ
xorg.conf:
```


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMA eView 17f3"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: 1280x1024 +0+0; CRT-0: 1024x768 +800+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 800x600 +800+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 640x480 +800+0, CRT-1: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

titan@dungeon:~$    

```

And zee log file:
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu6)
Current Operating System: Linux dungeon 2.6.24-12-generic #1 SMP Wed Mar 12 23:01:54 UTC 2008 i686
Build Date: 30 March 2008  04:42:53PM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  4 00:11:49 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 2.0
        X.Org XInput driver : 2.0
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 1509,9050 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1509,9050 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1509,9050 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1509,9050 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1509,9050 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1509,9050 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1509,9050 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 1509,9050 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:05:0: chip 1274,5000 card 4942,4c4c rev 00 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0406 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [1] -1  0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [2] -1  0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [3] -1  0       0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xe2000000 - 0xe3ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xe0000000/24, 0xd8000000/27
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [1] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [2] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [3] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [4] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [5] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [6] -1  0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [7] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [8] -1  0       0x00000500 - 0x0000051f (0x20) IX[B]
        [9] -1  0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [10] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [11] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [12] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [13] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [15] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [16] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [1] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [2] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [3] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [4] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [5] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [6] -1  0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [7] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [8] -1  0       0x00000500 - 0x0000051f (0x20) IX[B]
        [9] -1  0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [10] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [11] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [12] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [13] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [15] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [16] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [5] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [6] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [7] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [13] -1 0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [14] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [15] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [16] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [21] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.4.0.90, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.2.0
        ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [5] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [6] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [7] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [13] -1 0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [14] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [15] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [16] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [21] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [5] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [6] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [7] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [11] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [12] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [16] -1 0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [17] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [20] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [21] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [22] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [23] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [24] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [25] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024 +1280+0, CRT-1: 1280x1024 +0+0; CRT-0: 1024x768 +800+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 800x600 +800+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 640x480 +800+0, CRT-1: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     EMA eView 17f3 (CRT-0)
(--) NVIDIA(0):     Mag InnoVision (CRT-1)
(--) NVIDIA(0): EMA eView 17f3 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Mag InnoVision (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1280x1024+1280+0,CRT-1:1280x1024+0+0"
(II) NVIDIA(0):     "CRT-0:1024x768+800+0,CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "CRT-0:800x600+800+0,CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "CRT-0:640x480+800+0,CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
        [1] 0   0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
        [2] -1  0       0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xe3000000 - 0xe30000ff (0x100) MX[B]
        [7] -1  0       0x30000000 - 0x300003ff (0x400) MX[B]
        [8] -1  0       0xe4000000 - 0xe40003ff (0x400) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000c400 - 0x0000c43f (0x40) IX[B]
        [18] -1 0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [19] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [20] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [21] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [22] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [26] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [27] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [28] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [29] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024+1280+0,CRT-1:1280x1024+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
titan@dungeon:~$                                                   

```

thanks for the reply :)

---

### Post by ajmorris on 2008-04-04
> **The Titan said:**
>   So would it be a good idea to recompile the kernel, i heard it sometimes helps with unsupported hardware.

Did you compile your kernel yourself? if not, this will not be needed, ubuntu kernels, and even if you download the source and compile it yourself from kernel.org, has usb mice capabilities built into it, so unless you explicitley removed the capability in the kernel to run usb mice, this will not be an issue :)

AJ

---

### Post by Crafty Kisses on 2008-04-04
You might want to look at **Restricted Drivers Manager**, and see if there is any drivers in there you haven't installed.

---

### Post by ajmorris on 2008-04-04
hmm, xorg initialised the usb mouse according to the xorg log, there should be no reason why the mouse is not working... this is very strange...

this might be a long shot, however, in your /etc/X11/xorg.conf file, where it says      Option         "Device" "/dev/psaux"  for the mouse, could you please change that to      Option         "Device" "/dev/input/mice"  and restart X if its a no go, you can just change it back :)

---

### Post by The Titan on 2008-04-04
im using KDE and in the hardware drivers manager it has only the Nvidia driver in there, and says it's not in use.... but that has to be incorrect because im using compiz and play 3d games often

---

### Post by Whiffle on 2008-04-04
Another way you can test mice is to look in the directory

/dev/input

Looks like this on my computer:
```

[root@whiffle input]# ls
by-id    event0  event2  event4  event6  js0   mouse0  mouse2
by-path  event1  event3  event5  event7  mice  mouse1

```

If you do 
```

[root@whiffle input]# sudo cat mouse1

```

and then wiggle the mouse, you should get some fun characters like this:
```

&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;8&#65533;&#65533;(&#65533;(&#65533;(&#65533;(&#65533;(&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;&#9618;&#65533;(&#65533;(&#65533;(
&#65533;(&#65533;(&#65533;(  &#65533;(

```

You'll have to try it with all the mouse related ones there.  Hopefully it works with sudo, I'm not certain of that.  Use ctrl+c to stop it.

---

### Post by The Titan on 2008-04-04
i did that, and when i did "mice" and moved my PS2 mouse it worked but not the USb mouse.  mouse0 did nothing with either mouse and mouse1 worked with my ps2 mouse.  This is really strange... (and that was pretty cool :) ) i appreciate you sticking around with me trying to figure this out.

---

### Post by Whiffle on 2008-04-04
I'm running out of ideas here... do other usb devices work? (USB 1.1 in particular, USB 2 does other things)

---

### Post by The Titan on 2008-04-04
> **Whiffle said:**
> I'm running out of ideas here... do other usb devices work? (USB 1.1 in particular, USB 2 does other things)
i only have 2 usb mice so i dont know... neither one of them work... is it possible to use USB over a network lol, that would be a little strange but im willing to do that....

---

### Post by Crafty Kisses on 2008-04-04
> **The Titan said:**
> i only have 2 usb mice so i dont know... neither one of them work... is it possible to use USB over a network lol, that would be a little strange but im willing to do that....

You should try a USB keyboard and see if that works.

---

### Post by The Titan on 2008-04-04
i don't have one or i would try =/ im gonna go search my room for some usb device..

---

### Post by Crafty Kisses on 2008-04-04
> **The Titan said:**
> i don't have one or i would try =/ im gonna go search my room for some usb device..

Yeah, try an iPod.

---

### Post by The Titan on 2008-04-04
> **Codename said:**
> Yeah, try an iPod.
lmfao, if i could afford an ipod i would go buy a PCI usb card.  I cant find anything but an XBOX controller that i modified to use USB and linux dosent have drivers for it but nothing happened when i plugged it in and lsusb was the same

---

### Post by Whiffle on 2008-04-04
KEep in mind that your mouse is going to be USB1.1ish, which uses a different driver and different controller than USB2.0.  So a USB2.0 device may work, but a USB1 might not.

My current theory is that there is something up with your USB1.1 hardware, your bios, or driver.  I havn't come up with any real good ways to test that though.

---

### Post by Crafty Kisses on 2008-04-04
> **The Titan said:**
> lmfao, if i could afford an ipod i would go buy a PCI usb card.  I cant find anything but an XBOX controller that i modified to use USB and linux dosent have drivers for it but nothing happened when i plugged it in and lsusb was the same

You have any other USB device?

---

### Post by The Titan on 2008-04-04
im gonna go search my bios again for some "legacy" option or something stupid like that... see ya in like 5 mins

---

### Post by ajmorris on 2008-04-04
sorry, dunno if you did try it or not, you may have missed it since i posted it at the same time you posted something, but did you try my replacment of /dev/psaux with /dev/input/mice ?

AJ

---

### Post by The Titan on 2008-04-04
> **ajmorris said:**
> sorry, dunno if you did try it or not, you may have missed it since i posted it at the same time you posted something, but did you try my replacment of /dev/psaux with /dev/input/mice ?

AJ
no i missed that im gonna try it now

---

### Post by The Titan on 2008-04-04
no go :'( just the PS2 mouse works.... i understand if your out of ideas... thanks for your help

---

### Post by Crafty Kisses on 2008-04-04
> **The Titan said:**
> no go :'( just the PS2 mouse works.... i understand if your out of ideas... thanks for your help

You might want to try a Logitech USB mouse, I have one of those, and it works flawlessly with Ubuntu.

---

### Post by ajmorris on 2008-04-04
yeah, im out of ideas also... i have one of these mice, works out of the box.

Your problem is strange...

---

### Post by The Titan on 2008-04-04
i know the mouse works with ubuntu, i used it on my dell before i got this computer...

---

### Post by ajmorris on 2008-04-04
> **The Titan said:**
> i know the mouse works with ubuntu, i used it on my dell before i got this computer...

Oh, kk, even weider :P  There is nothing wrong with the PCI bus you have in your machine either, it works on ubuntu....

---

