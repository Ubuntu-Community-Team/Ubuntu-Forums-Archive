---
title: "Counter restarting during boot"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by leo_br on 2008-01-12
Hello,

I just noticed that the time counter of the system is restarting during the boot, is it normal or something is going wrong?


```

:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffdf000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62D0 checksum 0
[    0.000000] ACPI: RSDP 000F62D0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FFD0000, 002C (r1 A M I  OEMRSDT   2000525 MSFT       97)
[    0.000000] ACPI: FACP 1FFD0200, 0081 (r2 A M I  OEMFACP   2000525 MSFT       97)
[    0.000000] ACPI: DSDT 1FFD0390, 5C07 (r1  1ABSU 1ABSU001        1 INTL  2002026)
[    0.000000] ACPI: FACS 1FFDF000, 0040
[    0.000000] ACPI: OEMB 1FFDF040, 0125 (r1 A M I  AMI_OEM   2000525 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] Built 1 zonelists.  Total pages: 130001
[    0.000000] Kernel command line: root=UUID=78e457cb-afee-47d5-b520-920f25a8d2f2 ro irqpool
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2133.487 MHz processor.
[   45.369276] Console: colour VGA+ 80x25
[   45.371116] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   45.371484] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   45.390412] Memory: 508044k/524096k available (2015k kernel code, 15436k reserved, 916k data, 364k init, 0k highmem)
[   45.390478] virtual kernel memory layout:
[   45.390479]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   45.390481]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   45.390482]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   45.390483]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   45.390484]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   45.390485]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   45.390487]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   45.390809] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   45.390942] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   45.470852] Calibrating delay using timer specific routine.. 4269.13 BogoMIPS (lpj=8538270)
[   45.470974] Security Framework v1.0.0 initialized
[   45.471023] SELinux:  Disabled at boot.
[   45.471083] Mount-cache hash table entries: 512
[   45.471308] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[   45.471318] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   45.471364] CPU: L2 Cache: 512K (64 bytes/line)
[   45.471406] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[   45.471419] Compat vDSO mapped to ffffe000.
[   45.471474] Checking 'hlt' instruction... OK.
[   45.487039] SMP alternatives: switching to UP code
[   45.487404] Freeing SMP alternatives: 11k freed
[   45.487836] Early unpacking initramfs... done
[   45.798315] ACPI: Core revision 20070126
[   45.798510] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   45.800900] ACPI: setting ELCR to 0200 (from 8410)
[   46.114855] CPU0: AMD mobile AMD Athlon(tm) XP-M 2800+ stepping 00
[   46.114985] SMP motherboard not detected.
[   46.115027] Local APIC not detected. Using dummy APIC emulation.
[   46.115130] Brought up 1 CPUs
[   46.115359] Booting paravirtualized kernel on bare hardware
[   46.115480] Time:  1:31:35  Date: 00/13/108
[   46.115554] NET: Registered protocol family 16
[   46.115733] EISA bus registered
[   46.115785] ACPI: bus type pci registered
[   46.117320] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   46.117364] PCI: Using configuration type 1
[   46.117404] Setting up standard PCI resources
[   46.131372] ACPI: EC: Look up EC in DSDT
[   46.133163] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   46.135215] ACPI: Interpreter enabled
[   46.135256] ACPI: (supports S0 S1 S3 S4 S5)
[   46.135476] ACPI: Using PIC for interrupt routing
[   46.144293] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   46.144442] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   46.144492] PCI: Probing PCI hardware (bus 00)
[   46.144670] Enabling SiS 96x SMBus.
[   46.145439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   46.145684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   46.153631] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14)
[   46.154059] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14)
[   46.154483] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14)
[   46.154906] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14)
[   46.155329] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 11 12 14 *15)
[   46.155752] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 11 12 14 *15)
[   46.156174] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 11 12 14 15) *0, disabled.
[   46.156658] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 11 12 14 *15)
[   46.157057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   46.157112] pnp: PnP ACPI init
[   46.157165] ACPI: bus type pnp registered
[   46.161516] pnp: PnP ACPI: found 13 devices
[   46.161557] ACPI: ACPI bus type pnp unregistered
[   46.161602] PnPBIOS: Disabled by ACPI PNP
[   46.161706] PCI: Using ACPI for IRQ routing
[   46.161749] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   46.174960] NET: Registered protocol family 8
[   46.175002] NET: Registered protocol family 20
[   46.175126] pnp: 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[   46.175172] pnp: 00:06: iomem range 0xfff80000-0xffffffff could not be reserved
[   46.175224] pnp: 00:06: iomem range 0xffe80000-0xffefffff has been reserved
[   46.175270] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   46.175313] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   46.175359] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   46.175403] pnp: 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   46.175447] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   46.175691] pnp: 00:0c: iomem range 0x100000-0x1fffffff could not be reserved
[   46.177444] Time: tsc clocksource has been installed.
[   46.205987] PCI: Bridge: 0000:00:01.0
[   46.206028]   IO window: d000-dfff
[   46.206072]   MEM window: fea00000-feafffff
[   46.206115]   PREFETCH window: bff00000-cfefffff
[   46.206159] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   46.206200]   IO window: 00001000-000010ff
[   46.206242]   IO window: 00001400-000014ff
[   46.206285]   PREFETCH window: 30000000-33ffffff
[   46.206327]   MEM window: 34000000-37ffffff
[   46.206531] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   46.206576] PCI: setting IRQ 10 as level-triggered
[   46.206579] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   46.206691] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   46.206704] NET: Registered protocol family 2
[   46.245387] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   46.245519] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   46.246023] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   46.246365] TCP: Hash tables configured (established 16384 bind 16384)
[   46.246410] TCP reno registered
[   46.257437] checking if image is initramfs... it is
[   46.708419] Switched to high resolution mode on CPU 0
[   46.834860] Freeing initrd memory: 7060k freed
[   46.835425] audit: initializing netlink socket (disabled)
[   46.835487] audit(1200187894.980:1): initialized
[   46.837417] VFS: Disk quotas dquot_6.5.1
[   46.837508] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   46.837660] io scheduler noop registered
[   46.837701] io scheduler anticipatory registered
[   46.837742] io scheduler deadline registered
[   46.837794] io scheduler cfq registered (default)
[   46.891993] Boot video device is 0000:01:00.0
[   46.892177] isapnp: Scanning for PnP cards...
[   47.244994] isapnp: No Plug & Play device found
[   47.270435] Real Time Clock Driver v1.12ac
[   47.270614] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   47.270876] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   47.271707] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   47.271753] PCI: setting IRQ 4 as level-triggered
[   47.271757] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
[   47.271871] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   47.272600] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   47.272925] input: Macintosh mouse button emulation as /class/input/input0
[   47.273051] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   47.273096] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   47.276135] i8042.c: Detected active multiplexing controller, rev 1.1.
[   47.277546] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.277593] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   47.277635] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   47.277677] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   47.277718] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   47.278002] mice: PS/2 mouse device common for all mice
[   47.278272] EISA: Probing bus 0 at eisa.0
[   47.278324] Cannot allocate resource for EISA slot 1
[   47.278389] EISA: Detected 0 cards.
[   47.278554] TCP cubic registered
[   47.278601] NET: Registered protocol family 1
[   47.278664] Using IPI No-Shortcut mode
[   47.278925]   Magic number: 8:524:508
[   47.279236]   hash matches device 0000:00:01.0
[   47.279919] Freeing unused kernel memory: 364k freed
[   47.394300] input: AT Translated Set 2 keyboard as /class/input/input1
[   47.467823] AppArmor: AppArmor initialized<5>audit(1200187895.480:2):  type=1505 info="AppArmor initialized" pid=1178
[   47.477217] fuse init (API version 7.8)
[   47.483528] Failure registering capabilities with primary security module.
[   47.495395] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   47.518847] ACPI: Thermal Zone [THRM] (62 C)
[   48.120713] SCSI subsystem initialized
[   48.125675] libata version 2.21 loaded.
[   48.128986] pata_sis 0000:00:02.5: version 0.5.1
[   48.129241] scsi0 : pata_sis
[   48.129345] scsi1 : pata_sis
[   48.129535] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   48.129588] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   48.176674] usbcore: registered new interface driver usbfs
[   48.176758] usbcore: registered new interface driver hub
[   48.176827] usbcore: registered new device driver usb
[   48.181382] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   48.223191] sis900.c: v1.08.10 Apr. 2 2006
[    2.780000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.780000] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[    2.780000] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.780000] ata1.01: ATAPI: TOSHIBA ODD-DVD SD-R6372, 1732, max UDMA/33
[    2.784000] Time: acpi_pm clocksource has been installed.
[    2.796000] ata1.00: configured for UDMA/100
[    2.992000] ata1.01: configured for UDMA/33
[    2.992000] ata2: port disabled. ignoring.
[    2.992000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    2.996000] scsi 0:0:1:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1732 PQ: 0 ANSI: 5
[    2.996000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 15
[    2.996000] PCI: setting IRQ 15 as level-triggered
[    2.996000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 15 (level, low) -> IRQ 15
[    2.996000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.996000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    2.996000] ohci_hcd 0000:00:03.0: irq 15, io mem 0xfebfd000
[    3.016000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    3.016000] sd 0:0:0:0: [sda] Write Protect is off
[    3.016000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.016000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.016000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    3.016000] sd 0:0:0:0: [sda] Write Protect is off
[    3.016000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.016000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.016000]  sda: sda1 sda2 sda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[    3.052000] hub 1-0:1.0: USB hub found
[    3.052000] hub 1-0:1.0: 3 ports detected
[    3.068000]  sda5 sda6 > sda4
[    3.072000] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.076000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.076000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    3.096000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.096000] Uniform CD-ROM driver Revision: 3.20
[    3.100000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.156000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 15
[    3.156000] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 15 (level, low) -> IRQ 15
[    3.156000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.156000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.156000] ohci_hcd 0000:00:03.1: irq 15, io mem 0xfebfe000
[    3.212000] usb usb2: configuration #1 chosen from 1 choice
[    3.212000] hub 2-0:1.0: USB hub found
[    3.212000] hub 2-0:1.0: 3 ports detected
[    3.316000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.316000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.316000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.324000] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.328000] eth0: SiS 900 PCI Fast Ethernet at 0xee00, IRQ 10, 00:11:2f:f5:6a:c0.
[    3.328000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.328000] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.380000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[febfb800-febfbfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.388000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 15
[    3.388000] ACPI: PCI Interrupt 0000:00:03.3[D] -> Link [LNKH] -> GSI 15 (level, low) -> IRQ 15
[    3.388000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.388000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[    3.388000] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[    3.388000] ehci_hcd 0000:00:03.3: irq 15, io mem 0xfebff000
[    3.388000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.388000] usb usb3: configuration #1 chosen from 1 choice
[    3.388000] hub 3-0:1.0: USB hub found
[    3.388000] hub 3-0:1.0: 6 ports detected
[    3.448000] Attempting manual resume
[    3.448000] swsusp: Resume From Partition 8:6
[    3.448000] PM: Checking swsusp image.
[    3.452000] PM: Resume from disk failed.
[    3.520000] kjournald starting.  Commit interval 5 seconds
[    3.520000] EXT3-fs: mounted filesystem with ordered data mode.
[    3.908000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[    4.052000] usb 3-2: configuration #1 chosen from 1 choice
[    4.540000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    4.660000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800032447a2]
[    4.752000] usb 2-3: configuration #1 chosen from 1 choice
[   15.536000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.032000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   16.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.088000] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1814]
[   16.184000] ieee80211_crypt: registered algorithm 'NULL'
[   16.188000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.188000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.204000] input: PC Speaker as /class/input/input2
[   16.216000] Yenta: ISA IRQ mask 0x0088, PCI irq 10
[   16.216000] Socket status: 30000006
[   16.216000] agpgart: Detected SiS chipset - id:1862
[   16.220000] agpgart: AGP aperture is 64M @ 0xd0000000
[   16.244000] parport_pc 00:05: reported by Plug and Play ACPI
[   16.244000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.340000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   16.340000] wbsd: Copyright(c) Pierre Ossman
[   16.348000] mmc0: W83L51xD id 7112 at 0x520 irq 5 dma 3 PnP
[   16.684000] irda_init()
[   16.684000] NET: Registered protocol family 23
[   16.716000] bcm43xx driver
[   16.716000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   16.876000] usbcore: registered new interface driver hiddev
[   16.916000] input: Logitech Optical USB Mouse as /class/input/input3
[   16.916000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.1-3
[   16.916000] usbcore: registered new interface driver usbhid
[   16.916000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.256000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.276000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   17.276000] [fglrx] ASYNCIO init succeed!
[   17.276000] [fglrx] PAT is enabled successfully!
[   17.276000] [fglrx] module loaded - fglrx 8.44.3 [Dec 19 2007] on minor 0
[   17.352000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
[   17.620000] cs: IO port probe 0x100-0x3af: clean.
[   17.624000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[   17.624000] cs: IO port probe 0x820-0x8ff: excluding 0x828-0x84f 0x858-0x86f 0x878-0x87f
[   17.624000] cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xc87
[   17.624000] cs: IO port probe 0xa00-0xaff: clean.
[   17.772000] NET: Registered protocol family 17
[   18.016000] NET: Registered protocol family 10
[   18.016000] lo: Disabled Privacy Extensions
[   18.016000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.180000] intel8x0_measure_ac97_clock: measured 55345 usecs
[   18.180000] intel8x0: clocking to 48000
[   18.980000] lp0: using parport0 (interrupt-driven).
[   19.048000] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[   19.052000] usbcore: registered new interface driver pegasus
[   19.104000] Adding 1220868k swap on /dev/sda6.  Priority:-1 extents:1 across:1220868k
[   19.764000] EXT3 FS on sda4, internal journal
[   23.916000] Asus Laptop ACPI Extras version 0.30
[   23.916000]   Error calling BSTS
[   23.916000]   A2D model detected, supported
[   23.968000] No dock devices found.
[   24.104000] input: Power Button (FF) as /class/input/input4
[   24.104000] ACPI: Power Button (FF) [PWRF]
[   24.120000] input: Sleep Button (CM) as /class/input/input5
[   24.120000] ACPI: Sleep Button (CM) [SLPB]
[   24.128000] input: Lid Switch as /class/input/input6
[   24.128000] ACPI: Lid Switch [LIDD]
[   24.132000] input: Power Button (CM) as /class/input/input7
[   24.132000] ACPI: Power Button (CM) [PWRB]
[   24.256000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.300000] ACPI: AC Adapter [AC] (on-line)
[   24.704000] ACPI: Battery Slot [BAT0] (battery present)
[   25.088000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   25.092000] powernow: SGTC: 13333
[   25.092000] powernow: Minimum speed 400 MHz. Maximum speed 2133 MHz.
[   26.304000] Failure registering capabilities with primary security module.
[   26.456000] eth0: Media Link Off
[   26.456000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.808000] ppdev: user-space parallel port driver
[   27.456000] audit(1200177122.446:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5005 profile="/usr/sbin/cupsd"
[   27.504000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   27.504000] apm: overridden by ACPI.
[   28.524000] Bluetooth: Core ver 2.11
[   28.524000] NET: Registered protocol family 31
[   28.524000] Bluetooth: HCI device and connection manager initialized
[   28.524000] Bluetooth: HCI socket layer initialized
[   28.540000] Bluetooth: L2CAP ver 2.8
[   28.540000] Bluetooth: L2CAP socket layer initialized
[   28.600000] Bluetooth: RFCOMM socket layer initialized
[   28.600000] Bluetooth: RFCOMM TTY layer initialized
[   28.600000] Bluetooth: RFCOMM ver 1.8
[   29.008000] Clocksource tsc unstable (delta = -97249150 ns)
[   30.888000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   33.352000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   33.352000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   33.352000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[   33.352000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   33.356000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   33.356000] agpgart: SiS delay workaround: giving bridge time to recover.
[   33.372000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   33.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   33.376000] [fglrx] GART Table is not in FRAME_BUFFER range 
[   33.376000] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   33.376000] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000



```

---

### Post by nikoPSK on 2008-01-12
> **leo_br said:**
> Hello,

I just noticed that the time counter of the system is restarting during the boot, is it normal or something is going wrong?


```

:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffdf000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62D0 checksum 0
[    0.000000] ACPI: RSDP 000F62D0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FFD0000, 002C (r1 A M I  OEMRSDT   2000525 MSFT       97)
[    0.000000] ACPI: FACP 1FFD0200, 0081 (r2 A M I  OEMFACP   2000525 MSFT       97)
[    0.000000] ACPI: DSDT 1FFD0390, 5C07 (r1  1ABSU 1ABSU001        1 INTL  2002026)
[    0.000000] ACPI: FACS 1FFDF000, 0040
[    0.000000] ACPI: OEMB 1FFDF040, 0125 (r1 A M I  AMI_OEM   2000525 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] Built 1 zonelists.  Total pages: 130001
[    0.000000] Kernel command line: root=UUID=78e457cb-afee-47d5-b520-920f25a8d2f2 ro irqpool
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2133.487 MHz processor.
[   45.369276] Console: colour VGA+ 80x25
[   45.371116] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   45.371484] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   45.390412] Memory: 508044k/524096k available (2015k kernel code, 15436k reserved, 916k data, 364k init, 0k highmem)
[   45.390478] virtual kernel memory layout:
[   45.390479]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   45.390481]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   45.390482]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   45.390483]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   45.390484]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   45.390485]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   45.390487]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   45.390809] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   45.390942] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   45.470852] Calibrating delay using timer specific routine.. 4269.13 BogoMIPS (lpj=8538270)
[   45.470974] Security Framework v1.0.0 initialized
[   45.471023] SELinux:  Disabled at boot.
[   45.471083] Mount-cache hash table entries: 512
[   45.471308] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[   45.471318] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   45.471364] CPU: L2 Cache: 512K (64 bytes/line)
[   45.471406] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[   45.471419] Compat vDSO mapped to ffffe000.
[   45.471474] Checking 'hlt' instruction... OK.
[   45.487039] SMP alternatives: switching to UP code
[   45.487404] Freeing SMP alternatives: 11k freed
[   45.487836] Early unpacking initramfs... done
[   45.798315] ACPI: Core revision 20070126
[   45.798510] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   45.800900] ACPI: setting ELCR to 0200 (from 8410)
[   46.114855] CPU0: AMD mobile AMD Athlon(tm) XP-M 2800+ stepping 00
[   46.114985] SMP motherboard not detected.
[   46.115027] Local APIC not detected. Using dummy APIC emulation.
[   46.115130] Brought up 1 CPUs
[   46.115359] Booting paravirtualized kernel on bare hardware
[   46.115480] Time:  1:31:35  Date: 00/13/108
[   46.115554] NET: Registered protocol family 16
[   46.115733] EISA bus registered
[   46.115785] ACPI: bus type pci registered
[   46.117320] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   46.117364] PCI: Using configuration type 1
[   46.117404] Setting up standard PCI resources
[   46.131372] ACPI: EC: Look up EC in DSDT
[   46.133163] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   46.135215] ACPI: Interpreter enabled
[   46.135256] ACPI: (supports S0 S1 S3 S4 S5)
[   46.135476] ACPI: Using PIC for interrupt routing
[   46.144293] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   46.144442] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   46.144492] PCI: Probing PCI hardware (bus 00)
[   46.144670] Enabling SiS 96x SMBus.
[   46.145439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   46.145684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   46.153631] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14)
[   46.154059] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14)
[   46.154483] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14)
[   46.154906] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14)
[   46.155329] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 11 12 14 *15)
[   46.155752] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 11 12 14 *15)
[   46.156174] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 11 12 14 15) *0, disabled.
[   46.156658] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 11 12 14 *15)
[   46.157057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   46.157112] pnp: PnP ACPI init
[   46.157165] ACPI: bus type pnp registered
[   46.161516] pnp: PnP ACPI: found 13 devices
[   46.161557] ACPI: ACPI bus type pnp unregistered
[   46.161602] PnPBIOS: Disabled by ACPI PNP
[   46.161706] PCI: Using ACPI for IRQ routing
[   46.161749] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   46.174960] NET: Registered protocol family 8
[   46.175002] NET: Registered protocol family 20
[   46.175126] pnp: 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[   46.175172] pnp: 00:06: iomem range 0xfff80000-0xffffffff could not be reserved
[   46.175224] pnp: 00:06: iomem range 0xffe80000-0xffefffff has been reserved
[   46.175270] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   46.175313] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   46.175359] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   46.175403] pnp: 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   46.175447] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   46.175691] pnp: 00:0c: iomem range 0x100000-0x1fffffff could not be reserved
[   46.177444] Time: tsc clocksource has been installed.
[   46.205987] PCI: Bridge: 0000:00:01.0
[   46.206028]   IO window: d000-dfff
[   46.206072]   MEM window: fea00000-feafffff
[   46.206115]   PREFETCH window: bff00000-cfefffff
[   46.206159] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   46.206200]   IO window: 00001000-000010ff
[   46.206242]   IO window: 00001400-000014ff
[   46.206285]   PREFETCH window: 30000000-33ffffff
[   46.206327]   MEM window: 34000000-37ffffff
[   46.206531] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   46.206576] PCI: setting IRQ 10 as level-triggered
[   46.206579] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   46.206691] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   46.206704] NET: Registered protocol family 2
[   46.245387] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   46.245519] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   46.246023] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   46.246365] TCP: Hash tables configured (established 16384 bind 16384)
[   46.246410] TCP reno registered
[   46.257437] checking if image is initramfs... it is
[   46.708419] Switched to high resolution mode on CPU 0
[   46.834860] Freeing initrd memory: 7060k freed
[   46.835425] audit: initializing netlink socket (disabled)
[   46.835487] audit(1200187894.980:1): initialized
[   46.837417] VFS: Disk quotas dquot_6.5.1
[   46.837508] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   46.837660] io scheduler noop registered
[   46.837701] io scheduler anticipatory registered
[   46.837742] io scheduler deadline registered
[   46.837794] io scheduler cfq registered (default)
[   46.891993] Boot video device is 0000:01:00.0
[   46.892177] isapnp: Scanning for PnP cards...
[   47.244994] isapnp: No Plug & Play device found
[   47.270435] Real Time Clock Driver v1.12ac
[   47.270614] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   47.270876] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   47.271707] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   47.271753] PCI: setting IRQ 4 as level-triggered
[   47.271757] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
[   47.271871] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   47.272600] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   47.272925] input: Macintosh mouse button emulation as /class/input/input0
[   47.273051] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   47.273096] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   47.276135] i8042.c: Detected active multiplexing controller, rev 1.1.
[   47.277546] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.277593] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   47.277635] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   47.277677] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   47.277718] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   47.278002] mice: PS/2 mouse device common for all mice
[   47.278272] EISA: Probing bus 0 at eisa.0
[   47.278324] Cannot allocate resource for EISA slot 1
[   47.278389] EISA: Detected 0 cards.
[   47.278554] TCP cubic registered
[   47.278601] NET: Registered protocol family 1
[   47.278664] Using IPI No-Shortcut mode
[   47.278925]   Magic number: 8:524:508
[   47.279236]   hash matches device 0000:00:01.0
[   47.279919] Freeing unused kernel memory: 364k freed
[   47.394300] input: AT Translated Set 2 keyboard as /class/input/input1
[   47.467823] AppArmor: AppArmor initialized<5>audit(1200187895.480:2):  type=1505 info="AppArmor initialized" pid=1178
[   47.477217] fuse init (API version 7.8)
[   47.483528] Failure registering capabilities with primary security module.
[   47.495395] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   47.518847] ACPI: Thermal Zone [THRM] (62 C)
[   48.120713] SCSI subsystem initialized
[   48.125675] libata version 2.21 loaded.
[   48.128986] pata_sis 0000:00:02.5: version 0.5.1
[   48.129241] scsi0 : pata_sis
[   48.129345] scsi1 : pata_sis
[   48.129535] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   48.129588] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   48.176674] usbcore: registered new interface driver usbfs
[   48.176758] usbcore: registered new interface driver hub
[   48.176827] usbcore: registered new device driver usb
[   48.181382] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   48.223191] sis900.c: v1.08.10 Apr. 2 2006
[    2.780000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.780000] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[    2.780000] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.780000] ata1.01: ATAPI: TOSHIBA ODD-DVD SD-R6372, 1732, max UDMA/33
[    2.784000] Time: acpi_pm clocksource has been installed.
[    2.796000] ata1.00: configured for UDMA/100
[    2.992000] ata1.01: configured for UDMA/33
[    2.992000] ata2: port disabled. ignoring.
[    2.992000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    2.996000] scsi 0:0:1:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1732 PQ: 0 ANSI: 5
[    2.996000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 15
[    2.996000] PCI: setting IRQ 15 as level-triggered
[    2.996000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 15 (level, low) -> IRQ 15
[    2.996000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.996000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    2.996000] ohci_hcd 0000:00:03.0: irq 15, io mem 0xfebfd000
[    3.016000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    3.016000] sd 0:0:0:0: [sda] Write Protect is off
[    3.016000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.016000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.016000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    3.016000] sd 0:0:0:0: [sda] Write Protect is off
[    3.016000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.016000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.016000]  sda: sda1 sda2 sda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[    3.052000] hub 1-0:1.0: USB hub found
[    3.052000] hub 1-0:1.0: 3 ports detected
[    3.068000]  sda5 sda6 > sda4
[    3.072000] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.076000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.076000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    3.096000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.096000] Uniform CD-ROM driver Revision: 3.20
[    3.100000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.156000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 15
[    3.156000] ACPI: PCI Interrupt 0000:00:03.1[b] -> Link [LNKF] -> GSI 15 (level, low) -> IRQ 15
[    3.156000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.156000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.156000] ohci_hcd 0000:00:03.1: irq 15, io mem 0xfebfe000
[    3.212000] usb usb2: configuration #1 chosen from 1 choice
[    3.212000] hub 2-0:1.0: USB hub found
[    3.212000] hub 2-0:1.0: 3 ports detected
[    3.316000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.316000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.316000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.324000] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.328000] eth0: SiS 900 PCI Fast Ethernet at 0xee00, IRQ 10, 00:11:2f:f5:6a:c0.
[    3.328000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.328000] ACPI: PCI Interrupt 0000:00:0a.1[b] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.380000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[febfb800-febfbfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.388000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 15
[    3.388000] ACPI: PCI Interrupt 0000:00:03.3[D] -> Link [LNKH] -> GSI 15 (level, low) -> IRQ 15
[    3.388000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.388000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[    3.388000] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[    3.388000] ehci_hcd 0000:00:03.3: irq 15, io mem 0xfebff000
[    3.388000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.388000] usb usb3: configuration #1 chosen from 1 choice
[    3.388000] hub 3-0:1.0: USB hub found
[    3.388000] hub 3-0:1.0: 6 ports detected
[    3.448000] Attempting manual resume
[    3.448000] swsusp: Resume From Partition 8:6
[    3.448000] PM: Checking swsusp image.
[    3.452000] PM: Resume from disk failed.
[    3.520000] kjournald starting.  Commit interval 5 seconds
[    3.520000] EXT3-fs: mounted filesystem with ordered data mode.
[    3.908000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[    4.052000] usb 3-2: configuration #1 chosen from 1 choice
[    4.540000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    4.660000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800032447a2]
[    4.752000] usb 2-3: configuration #1 chosen from 1 choice
[   15.536000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.032000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   16.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.088000] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1814]
[   16.184000] ieee80211_crypt: registered algorithm 'NULL'
[   16.188000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.188000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.204000] input: PC Speaker as /class/input/input2
[   16.216000] Yenta: ISA IRQ mask 0x0088, PCI irq 10
[   16.216000] Socket status: 30000006
[   16.216000] agpgart: Detected SiS chipset - id:1862
[   16.220000] agpgart: AGP aperture is 64M @ 0xd0000000
[   16.244000] parport_pc 00:05: reported by Plug and Play ACPI
[   16.244000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.340000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   16.340000] wbsd: Copyright(c) Pierre Ossman
[   16.348000] mmc0: W83L51xD id 7112 at 0x520 irq 5 dma 3 PnP
[   16.684000] irda_init()
[   16.684000] NET: Registered protocol family 23
[   16.716000] bcm43xx driver
[   16.716000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   16.876000] usbcore: registered new interface driver hiddev
[   16.916000] input: Logitech Optical USB Mouse as /class/input/input3
[   16.916000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.1-3
[   16.916000] usbcore: registered new interface driver usbhid
[   16.916000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.256000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.276000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   17.276000] [fglrx] ASYNCIO init succeed!
[   17.276000] [fglrx] PAT is enabled successfully!
[   17.276000] [fglrx] module loaded - fglrx 8.44.3 [Dec 19 2007] on minor 0
[   17.352000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
[   17.620000] cs: IO port probe 0x100-0x3af: clean.
[   17.624000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[   17.624000] cs: IO port probe 0x820-0x8ff: excluding 0x828-0x84f 0x858-0x86f 0x878-0x87f
[   17.624000] cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xc87
[   17.624000] cs: IO port probe 0xa00-0xaff: clean.
[   17.772000] NET: Registered protocol family 17
[   18.016000] NET: Registered protocol family 10
[   18.016000] lo: Disabled Privacy Extensions
[   18.016000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.180000] intel8x0_measure_ac97_clock: measured 55345 usecs
[   18.180000] intel8x0: clocking to 48000
[   18.980000] lp0: using parport0 (interrupt-driven).
[   19.048000] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[   19.052000] usbcore: registered new interface driver pegasus
[   19.104000] Adding 1220868k swap on /dev/sda6.  Priority:-1 extents:1 across:1220868k
[   19.764000] EXT3 FS on sda4, internal journal
[   23.916000] Asus Laptop ACPI Extras version 0.30
[   23.916000]   Error calling BSTS
[   23.916000]   A2D model detected, supported
[   23.968000] No dock devices found.
[   24.104000] input: Power Button (FF) as /class/input/input4
[   24.104000] ACPI: Power Button (FF) [PWRF]
[   24.120000] input: Sleep Button (CM) as /class/input/input5
[   24.120000] ACPI: Sleep Button (CM) [SLPB]
[   24.128000] input: Lid Switch as /class/input/input6
[   24.128000] ACPI: Lid Switch [LIDD]
[   24.132000] input: Power Button (CM) as /class/input/input7
[   24.132000] ACPI: Power Button (CM) [PWRB]
[   24.256000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.300000] ACPI: AC Adapter [AC] (on-line)
[   24.704000] ACPI: Battery Slot [BAT0] (battery present)
[   25.088000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   25.092000] powernow: SGTC: 13333
[   25.092000] powernow: Minimum speed 400 MHz. Maximum speed 2133 MHz.
[   26.304000] Failure registering capabilities with primary security module.
[   26.456000] eth0: Media Link Off
[   26.456000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.808000] ppdev: user-space parallel port driver
[   27.456000] audit(1200177122.446:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5005 profile="/usr/sbin/cupsd"
[   27.504000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   27.504000] apm: overridden by ACPI.
[   28.524000] Bluetooth: Core ver 2.11
[   28.524000] NET: Registered protocol family 31
[   28.524000] Bluetooth: HCI device and connection manager initialized
[   28.524000] Bluetooth: HCI socket layer initialized
[   28.540000] Bluetooth: L2CAP ver 2.8
[   28.540000] Bluetooth: L2CAP socket layer initialized
[   28.600000] Bluetooth: RFCOMM socket layer initialized
[   28.600000] Bluetooth: RFCOMM TTY layer initialized
[   28.600000] Bluetooth: RFCOMM ver 1.8
[   29.008000] Clocksource tsc unstable (delta = -97249150 ns)
[   30.888000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   33.352000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   33.352000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   33.352000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[   33.352000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   33.356000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   33.356000] agpgart: SiS delay workaround: giving bridge time to recover.
[   33.372000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   33.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   33.376000] [fglrx] GART Table is not in FRAME_BUFFER range 
[   33.376000] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   33.376000] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000



```

I'd say don't worry :)

---

