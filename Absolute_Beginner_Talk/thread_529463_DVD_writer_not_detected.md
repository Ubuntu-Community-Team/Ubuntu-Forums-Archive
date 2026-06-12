---
title: "DVD writer not detected"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-08-19
Hi,


Ubuntu 7.04 is not detecting my LG external USB DVD Writer with casing though its detecting the rest of my internal drives and usb drives too. Please help me in getting this.

---

### Post by intel on 2007-08-19
attach the output of the following commands as root

[LIST=1]
[*]lsusb
[*]dmesg
[*]uname -a[/LIST]okie

---

### Post by sankarv on 2007-08-19
root@ubuntu:/home/ubuntu# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@ubuntu:/home/ubuntu# 








root@ubuntu:/home/ubuntu# dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001bea0000 end: 000000001bfa0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001bfa0000 size: 0000000000010000 end: 000000001bfb0000 type: 3
[    0.000000] copy_e820_map() start: 000000001bfb0000 size: 0000000000040000 end: 000000001bff0000 type: 4
[    0.000000] copy_e820_map() start: 000000001bff0000 size: 0000000000010000 end: 000000001c000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bfa0000 (usable)
[    0.000000]  BIOS-e820: 000000001bfa0000 - 000000001bfb0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bfb0000 - 000000001bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 114592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114592
[    0.000000]   HighMem    114592 ->   114592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114592
[    0.000000] On node 0 totalpages: 114592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109633 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000fa9f0
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x11000523 MSFT 0x00000097) @ 0x1bfa0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x11000523 MSFT 0x00000097) @ 0x1bfa0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000523 MSFT 0x00000097) @ 0x1bfa0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000523 MSFT 0x00000097) @ 0x1bfb0040
[    0.000000] ACPI: DSDT (v001  A0310 A0310001 0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3780000)
[    0.000000] Detected 1600.250 MHz processor.
[   95.138841] Built 1 zonelists.  Total pages: 113697
[   95.138845] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[   95.139030] mapped APIC to ffffd000 (fee00000)
[   95.139032] mapped IOAPIC to ffffc000 (fec00000)
[   95.139035] Enabling fast FPU save and restore... done.
[   95.139038] Enabling unmasked SIMD FPU exception support... done.
[   95.139047] Initializing CPU#0
[   95.139118] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   95.140837] Console: colour VGA+ 80x25
[   95.141054] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   95.141464] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   95.149942] Memory: 443200k/458368k available (1992k kernel code, 14644k reserved, 893k data, 328k init, 0k highmem)
[   95.149953] virtual kernel memory layout:
[   95.149955]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   95.149956]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   95.149958]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   95.149959]     lowmem  : 0xc0000000 - 0xdbfa0000   ( 447 MB)
[   95.149961]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   95.149962]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   95.149964]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   95.149967] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   95.226998] Calibrating delay using timer specific routine.. 3204.14 BogoMIPS (lpj=6408292)
[   95.227037] Security Framework v1.0.0 initialized
[   95.227043] SELinux:  Disabled at boot.
[   95.227058] Mount-cache hash table entries: 512
[   95.227180] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   95.227190] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   95.227192] CPU: L2 Cache: 128K (64 bytes/line)
[   95.227195] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   95.227205] Compat vDSO mapped to ffffe000.
[   95.227209] Remapping vsyscall page to ffffe000
[   95.227218] Checking 'hlt' instruction... OK.
[   95.243096] SMP alternatives: switching to UP code
[   95.243322] Freeing SMP alternatives: 11k freed
[   95.243551] Early unpacking initramfs... done
[   95.596489] ACPI: Core revision 20060707
[   95.596971] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   95.599242] CPU0: AMD Sempron(tm) Processor 2600+ stepping 02
[   95.599264] Total of 1 processors activated (3204.14 BogoMIPS).
[   95.599767] ENABLING IO-APIC IRQs
[   95.600087] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   95.746278] Brought up 1 CPUs
[   95.746527] Booting paravirtualized kernel on bare hardware
[   95.746629] Time: 19:35:05  Date: 07/19/107
[   95.746662] NET: Registered protocol family 16
[   95.746753] EISA bus registered
[   95.746757] ACPI: bus type pci registered
[   95.747437] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   95.747439] PCI: Using configuration type 1
[   95.747441] Setting up standard PCI resources
[   95.755460] ACPI: Interpreter enabled
[   95.755465] ACPI: Using IOAPIC for interrupt routing
[   95.756589] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   95.756596] PCI: Probing PCI hardware (bus 00)
[   95.757346] PCI: enabled onboard AC97/MC97 devices
[   95.757603] Boot video device is 0000:01:00.0
[   95.757644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   95.770314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   95.776982] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   95.777230] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   95.777474] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   95.777719] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   95.777978] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   95.778258] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   95.778508] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   95.778755] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   95.778835] Linux Plug and Play Support v0.97 (c) Adam Belay
[   95.778846] pnp: PnP ACPI init
[   95.783184] pnp: PnP ACPI: found 14 devices
[   95.783190] PnPBIOS: Disabled by ACPI PNP
[   95.783241] PCI: Using ACPI for IRQ routing
[   95.783244] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   95.787520] NET: Registered protocol family 8
[   95.787522] NET: Registered protocol family 20
[   95.788270] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   95.788527] PCI: Bridge: 0000:00:01.0
[   95.788530]   IO window: disabled.
[   95.788534]   MEM window: faf00000-fbffffff
[   95.788538]   PREFETCH window: f4000000-f9ffffff
[   95.788556] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   95.788591] NET: Registered protocol family 2
[   95.826201] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   95.826288] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   95.826399] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   95.826465] TCP: Hash tables configured (established 16384 bind 8192)
[   95.826468] TCP reno registered
[   95.838239] checking if image is initramfs... it is
[   96.539382] Freeing initrd memory: 6966k freed
[   96.539789] audit: initializing netlink socket (disabled)
[   96.539802] audit(1187552105.480:1): initialized
[   96.539928] VFS: Disk quotas dquot_6.5.1
[   96.539950] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   96.540000] io scheduler noop registered
[   96.540003] io scheduler anticipatory registered
[   96.540005] io scheduler deadline registered
[   96.540017] io scheduler cfq registered (default)
[   96.540327] isapnp: Scanning for PnP cards...
[   96.894056] isapnp: No Plug & Play device found
[   96.931506] Real Time Clock Driver v1.12ac
[   96.931549] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   96.931856] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   96.932641] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   96.932936] mice: PS/2 mouse device common for all mice
[   96.933396] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   96.933616] input: Macintosh mouse button emulation as /class/input/input0
[   96.933646] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   96.933650] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   96.933915] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   96.934206] serio: i8042 KBD port at 0x60,0x64 irq 1
[   96.934210] serio: i8042 AUX port at 0x60,0x64 irq 12
[   96.934318] EISA: Probing bus 0 at eisa.0
[   96.934327] Cannot allocate resource for EISA slot 1
[   96.934358] EISA: Detected 0 cards.
[   96.964522] TCP cubic registered
[   96.964534] NET: Registered protocol family 1
[   96.964560] Using IPI No-Shortcut mode
[   96.964654] ACPI: (supports S0 S1 S3 S4 S5)
[   96.964695]   Magic number: 3:485:597
[   96.964751]   hash matches device ptyd1
[   96.965086] Freeing unused kernel memory: 328k freed
[   96.968435] Time: tsc clocksource has been installed.
[   96.974427] input: AT Translated Set 2 keyboard as /class/input/input1
[   98.222426] Capability LSM initialized
[   98.858597] SCSI subsystem initialized
[   98.863483] libata version 2.20 loaded.
[   98.867010] sata_via 0000:00:0f.0: version 2.1
[   98.867036] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   98.867054] sata_via 0000:00:0f.0: routed to hard irq line 10
[   98.867103] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e402 bmdma 0x0001d400 irq 16
[   98.867128] ata2: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001d802 bmdma 0x0001d408 irq 16
[   98.867146] scsi0 : sata_via
[   98.880007] usbcore: registered new interface driver usbfs
[   98.880027] usbcore: registered new interface driver hub
[   98.880048] usbcore: registered new device driver usb
[   98.932600] USB Universal Host Controller Interface driver v3.0
[   98.959345] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   99.070160] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   99.086028] Floppy drive(s): fd0 is 1.44M
[   99.146192] FDC 0 is a post-1991 82077
[   99.235730] ATA: abnormal status 0x7F on port 0x0001e807
[   99.246370] ATA: abnormal status 0x7F on port 0x0001e807
[   99.279843] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   99.279849] ata1.00: ATA-7: ST380211AS, 3.AAB, max UDMA/133
[   99.279852] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   99.338059] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   99.338064] ata1.00: configured for UDMA/133
[   99.338073] scsi1 : sata_via
[   99.464821] end_request: I/O error, dev fd0, sector 0
[   99.540697] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   99.551250] ATA: abnormal status 0x7F on port 0x0001e007
[   99.552094] scsi 0:0:0:0: Direct-Access     ATA      ST380211AS       3.AA PQ: 0 ANSI: 5
[   99.552949] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   99.552961] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   99.553106] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   99.553140] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000b800
[   99.553261] usb usb1: configuration #1 chosen from 1 choice
[   99.553285] hub 1-0:1.0: USB hub found
[   99.553293] hub 1-0:1.0: 2 ports detected
[   99.562890] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   99.562903] sda: Write Protect is off
[   99.562906] sda: Mode Sense: 00 3a 00 00
[   99.562919] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   99.562975] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   99.562983] sda: Write Protect is off
[   99.562985] sda: Mode Sense: 00 3a 00 00
[   99.562998] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   99.563002]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   99.640743] sd 0:0:0:0: Attached scsi disk sda
[   99.645316] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   99.656683] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   99.656695] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   99.656716] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   99.656739] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000c000
[   99.656827] usb usb2: configuration #1 chosen from 1 choice
[   99.656854] hub 2-0:1.0: USB hub found
[   99.656861] hub 2-0:1.0: 2 ports detected
[   99.760483] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   99.760495] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   99.760523] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   99.760545] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000c400
[   99.760636] usb usb3: configuration #1 chosen from 1 choice
[   99.760660] hub 3-0:1.0: USB hub found
[   99.760667] hub 3-0:1.0: 2 ports detected
[   99.864330] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   99.864342] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   99.864368] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   99.864391] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000c800
[   99.864483] usb usb4: configuration #1 chosen from 1 choice
[   99.864507] hub 4-0:1.0: USB hub found
[   99.864514] hub 4-0:1.0: 2 ports detected
[   99.968297] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
[   99.968384] eth0: VIA Rhine II at 0x1b000, 00:15:f2:c7:1b:2d, IRQ 18.
[   99.969098] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   99.969179] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   99.969189] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   99.969215] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   99.969254] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfad00000
[   99.969261] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   99.969339] usb usb5: configuration #1 chosen from 1 choice
[   99.969363] hub 5-0:1.0: USB hub found
[   99.969371] hub 5-0:1.0: 8 ports detected
[  100.072112] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[  100.072131] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[  100.072143] VP_IDE: chipset revision 6
[  100.072145] VP_IDE: not 100% native mode: will probe irqs later
[  100.072156] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[  100.072164]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[  100.072177]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[  100.072184] Probing IDE interface ide0...
[  100.507302] end_request: I/O error, dev fd0, sector 0
[  100.639103] Probing IDE interface ide1...
[  100.918689] usb 5-8: new high speed USB device using ehci_hcd and address 2
[  101.030542] usb 5-8: device descriptor read/64, error -71
[  101.067955] kjournald starting.  Commit interval 5 seconds
[  101.067969] EXT3-fs: mounted filesystem with ordered data mode.
[  101.246202] usb 5-8: device descriptor read/64, error -71
[  101.461884] usb 5-8: new high speed USB device using ehci_hcd and address 3
[  101.501916] hdc: HL-DT-ST RW/DVD GCC-4522B, ATAPI CD/DVD-ROM drive
[  102.104967] end_request: I/O error, dev fd0, sector 0
[  102.284777] hdd: SAMSUNG CD-R/RW DRIVE SW-252F, ATAPI CD/DVD-ROM drive
[  102.332952] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  102.343438] ide1 at 0x170-0x177,0x376 on irq 15
[  102.377179] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[  102.377188] Uniform CD-ROM driver Revision: 3.20
[  102.396195] hdd: ATAPI 1X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[  102.444463] usb 5-8: new high speed USB device using ehci_hcd and address 4
[  102.673142] kjournald starting.  Commit interval 5 seconds
[  102.673155] EXT3-fs: mounted filesystem with ordered data mode.
[  102.851854] usb 5-8: device not accepting address 4, error -71
[  102.963689] usb 5-8: new high speed USB device using ehci_hcd and address 5
[  103.371091] usb 5-8: device not accepting address 5, error -71
[  103.710615] end_request: I/O error, dev fd0, sector 0
[  104.652242] ISO 9660 Extensions: Microsoft Joliet Level 3
[  104.689150] ISO 9660 Extensions: RRIP_1991A
[  104.716612] Registering unionfs 20060916-2203
[  104.716617] unionfs: debugging is not enabled
[  104.731275] loop: loaded (max 8 devices)
[  104.817684] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher
[  163.389846] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  164.854967] Linux agpgart interface v0.102 (c) Dave Jones
[  165.103157] agpgart: Detected AGP bridge 0
[  165.107423] agpgart: AGP aperture is 128M @ 0xe8000000
[  165.347252] NET: Registered protocol family 17
[  165.479129] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  166.365852] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  166.488425] input: PC Speaker as /class/input/input2
[  166.682915] parport: PnPBIOS parport detected.
[  166.682959] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  167.014159] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[  167.014170] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 19
[  167.129420] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  167.768700] PCI: Setting latency timer of device 0000:00:11.6 to 64
[  168.272168] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[  168.272178] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[  168.272409] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[  168.272546] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  168.785986] codec_read: codec 0 is not valid [0xfe0000]
[  168.792566] codec_read: codec 0 is not valid [0xfe0000]
[  168.799194] codec_read: codec 0 is not valid [0xfe0000]
[  168.805766] codec_read: codec 0 is not valid [0xfe0000]
[  170.665512] NET: Registered protocol family 10
[  170.665616] lo: Disabled Privacy Extensions
[  170.674237] fuse init (API version 7.8)
[  171.170977] Adding 1044184k swap on /dev/sda7.  Priority:-1 extents:1 across:1044184k
[  178.781214] input: Power Button (FF) as /class/input/input4
[  178.785909] ACPI: Power Button (FF) [PWRF]
[  178.827283] input: Power Button (CM) as /class/input/input5
[  178.831905] ACPI: Power Button (CM) [PWRB]
[  178.874198] No dock devices found.
[  178.898456] Using specific hotkey driver
[  178.951438] ibm_acpi: ec object not found
[  179.130515] pcc_acpi: loading...
[  179.877171] powernow-k8: Power state transitions not supported
[  180.657815] eth0: no IPv6 routers present
[  192.209511] [drm] Initialized drm 1.1.0 20060810
[  192.262531] [drm] Initialized via 2.11.0 20061227 on minor 0
[  192.262681] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[  192.263538] [drm] Initialized via 2.11.0 20061227 on minor 1
[  192.273142] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  192.273159] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[  192.273166] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  192.273228] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  192.277244] [drm:via_mem_alloc] *ERROR* Attempt to allocate from uninitialized memory manager.
[  193.333479] lp0: using parport0 (interrupt-driven).
[  193.673778] ppdev: user-space parallel port driver
[  203.975624] eth0: no IPv6 routers present
[  206.187100] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  206.187106] apm: overridden by ACPI.
[  208.573894] Bluetooth: Core ver 2.11
[  208.573950] NET: Registered protocol family 31
[  208.573953] Bluetooth: HCI device and connection manager initialized
[  208.573957] Bluetooth: HCI socket layer initialized
[  208.732666] usb 5-8: new high speed USB device using ehci_hcd and address 6
[  208.844502] usb 5-8: device descriptor read/64, error -71
[  208.891620] Bluetooth: L2CAP ver 2.8
[  208.891624] Bluetooth: L2CAP socket layer initialized
[  209.819393] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  209.930921] usb 5-8: new high speed USB device using ehci_hcd and address 7
[  210.042753] usb 5-8: device descriptor read/64, error -71
[  210.258435] usb 5-8: device descriptor read/64, error -71
[  210.474129] usb 5-8: new high speed USB device using ehci_hcd and address 8
[  210.881534] usb 5-8: device not accepting address 8, error -71
[  210.993377] usb 5-8: new high speed USB device using ehci_hcd and address 9
[  211.400772] usb 5-8: device not accepting address 9, error -71
[  212.184691] Bluetooth: RFCOMM socket layer initialized
[  212.184705] Bluetooth: RFCOMM TTY layer initialized
[  212.184707] Bluetooth: RFCOMM ver 1.8
[  430.120508] usb 5-8: new high speed USB device using ehci_hcd and address 10
[  430.232353] usb 5-8: device descriptor read/64, error -71
[  431.207215] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  431.318772] usb 5-8: new high speed USB device using ehci_hcd and address 11
[  432.189812] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  432.301335] usb 5-8: new high speed USB device using ehci_hcd and address 12
[  432.708737] usb 5-8: device not accepting address 12, error -71
[  432.820590] usb 5-8: new high speed USB device using ehci_hcd and address 13
[  433.227984] usb 5-8: device not accepting address 13, error -71








root@ubuntu:/home/ubuntu# uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
root@ubuntu:/home/ubuntu#







*Hi pls let me know if tats ok.*

---

### Post by sankarv on 2007-08-20
hi got rectified the problem. actually i was connecting the writer in usb port at the front of my machine. now i tried with the back side port of machine and now it works fine.

---

### Post by liam1988 on 2007-09-06
hi there my internal dvd writer is not being detected by ubuntu, and im almost a complete n00b when it comes to this. help please?

---

