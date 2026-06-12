---
title: "Fresh Feisty Install, USB devices randomly fail"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-05-14
Every so often, my USB mouse stops responding, and the light goes off. My external drive nor mp3 player will mount at this time. Replugging devices in does nothing. I normally use a usb keyboard, but right now I'm using a ps/2 one and it responds and I can navigate with it. My entire system froze up as I typed this, but that hadn't happened before now.

---

### Post by skyhopper88 on 2007-05-14
Well, I kinda solved the problem by using a kernal without USB_suspend from this topic.
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

However, I can't seem to get Nvidia's drivers to work with it. When I loaded this kernal X failed to start so I attempted to uninstall then reinstall the nvidia drivers through the envy script and redo my xorg config. It complained about needing linux-headers-2.6.20-15-124-386, which I was unable to locate and install. Same with linux-restricted-modules-2.6.20-15-124-386. Is there a way to use the restricted driver with this kernal? I'm fond of beryl, and it doesn't seem to work with plain old nvidia-glx. Anybody know of another workaround?

---

### Post by skyhopper88 on 2007-05-14
Bump

---

### Post by skyhopper88 on 2007-05-22
I dumpted that kernal and am still tring to add parameters to menu.lst but I havent had one that worked, almost thought I had it too. Here's my dmsg output.

```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fdf0000 end: 000000005fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000005fef0000 size: 0000000000003000 end: 000000005fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000005fef3000 size: 000000000000d000 end: 000000005ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fef0000 (usable)
[    0.000000]  BIOS-e820: 000000005fef0000 - 000000005fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fef3000 - 000000005ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 638MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3a50
[    0.000000] Entering add_active_range(0, 0, 392944) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   392944
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   392944
[    0.000000] On node 0 totalpages: 392944
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1277 pages used for memmap
[    0.000000]   HighMem zone: 162291 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7b70
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x5fef9680
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef97c0
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef95c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5ff00000:80100000)
[    0.000000] Detected 1004.613 MHz processor.
[   27.279978] Built 1 zonelists.  Total pages: 389875
[   27.279984] Kernel command line: root=UUID=e9fceb2e-df32-4566-bbf2-5571d9aa2bc3 ro quiet splash rootflags=data=writeback pci=noacpi acpi=noirq noapic
[   27.280255] mapped APIC to ffffd000 (fee00000)
[   27.280259] mapped IOAPIC to ffffc000 (fec00000)
[   27.280264] Enabling fast FPU save and restore... done.
[   27.280268] Enabling unmasked SIMD FPU exception support... done.
[   27.280278] Initializing CPU#0
[   27.280338] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   27.281625] Console: colour VGA+ 80x25
[   27.282109] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.282769] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.353712] Memory: 1547108k/1571776k available (1992k kernel code, 23508k reserved, 893k data, 328k init, 654272k highmem)
[   27.353730] virtual kernel memory layout:
[   27.353732]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.353735]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.353737]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.353740]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.353742]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   27.353744]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   27.353747]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   27.353752] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.432303] Calibrating delay using timer specific routine.. 2011.24 BogoMIPS (lpj=4022497)
[   27.432363] Security Framework v1.0.0 initialized
[   27.432372] SELinux:  Disabled at boot.
[   27.432395] Mount-cache hash table entries: 512
[   27.432577] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   27.432591] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.432596] CPU: L2 Cache: 512K (64 bytes/line)
[   27.432600] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   27.432616] Compat vDSO mapped to ffffe000.
[   27.432622] Remapping vsyscall page to ffffe000
[   27.432636] Checking 'hlt' instruction... OK.
[   27.448463] SMP alternatives: switching to UP code
[   27.448712] Freeing SMP alternatives: 11k freed
[   27.448991] Early unpacking initramfs... done
[   27.961739] ACPI: Core revision 20060707
[   27.965282] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   27.970329] ACPI: setting ELCR to 0e20 (from 0c20)
[   27.973292] CPU0: AMD Athlon(tm) 64 Processor 3400+ stepping 02
[   27.973317] Total of 1 processors activated (2011.24 BogoMIPS).
[   28.080175] Brought up 1 CPUs
[   28.080462] Booting paravirtualized kernel on bare hardware
[   28.080546] Time:  0:27:33  Date: 04/22/107
[   28.080587] NET: Registered protocol family 16
[   28.080688] EISA bus registered
[   28.080693] ACPI: bus type pci registered
[   28.087533] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=3
[   28.087536] PCI: Using configuration type 1
[   28.087539] Setting up standard PCI resources
[   28.102898] ACPI: Interpreter enabled
[   28.102903] ACPI: Using PIC for interrupt routing
[   28.123875] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.123888] pnp: PnP ACPI init
[   28.138967] pnp: PnP ACPI: found 14 devices
[   28.138973] PnPBIOS: Disabled by ACPI PNP
[   28.139036] PCI: Probing PCI hardware
[   28.139042] PCI: Probing PCI hardware (bus 00)
[   28.143701] Boot video device is 0000:02:00.0
[   28.143918] PCI: Transparent bridge - 0000:00:10.0
[   28.457670] NET: Registered protocol family 8
[   28.457674] NET: Registered protocol family 20
[   28.458623] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   28.458629] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   28.458634] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   28.458639] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   28.458644] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   28.458648] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   28.458653] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   28.458658] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   28.459022] PCI: Bridge: 0000:00:02.0
[   28.459026]   IO window: a000-afff
[   28.459031]   MEM window: fdb00000-fdbfffff
[   28.459036]   PREFETCH window: fdc00000-fdcfffff
[   28.459044] PCI: Bridge: 0000:00:04.0
[   28.459048]   IO window: b000-bfff
[   28.459053]   MEM window: fa000000-fcffffff
[   28.459058]   PREFETCH window: d0000000-dfffffff
[   28.459063] PCI: Bridge: 0000:00:10.0
[   28.459067]   IO window: 9000-9fff
[   28.459073]   MEM window: fde00000-fdefffff
[   28.459079]   PREFETCH window: fdd00000-fddfffff
[   28.459095] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.459107] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   28.459119] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   28.459162] NET: Registered protocol family 2
[   28.496109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.496310] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.497496] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.498094] TCP: Hash tables configured (established 131072 bind 65536)
[   28.498098] TCP reno registered
[   28.508196] checking if image is initramfs... it is
[   29.518969] Freeing initrd memory: 6719k freed
[   29.519512] audit: initializing netlink socket (disabled)
[   29.519528] audit(1179793654.320:1): initialized
[   29.519612] highmem bounce pool size: 64 pages
[   29.519703] VFS: Disk quotas dquot_6.5.1
[   29.519740] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.519807] io scheduler noop registered
[   29.519811] io scheduler anticipatory registered
[   29.519814] io scheduler deadline registered
[   29.519832] io scheduler cfq registered (default)
[   37.541634] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   37.541883] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   37.541919] assign_interrupt_mode Found MSI capability
[   37.541924] Allocate Port Service[0000:00:02.0:pcie00]
[   37.542014] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   37.542049] assign_interrupt_mode Found MSI capability
[   37.542053] Allocate Port Service[0000:00:04.0:pcie00]
[   37.542183] isapnp: Scanning for PnP cards...
[   37.895426] isapnp: No Plug & Play device found
[   37.932188] Real Time Clock Driver v1.12ac
[   37.932269] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.932410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.932622] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.933321] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.933685] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.934230] 0000:03:09.0: ttyS2 at I/O 0x9c08 (irq = 5) is a 16450
[   37.934444] 0000:03:09.0: ttyS3 at I/O 0x9c10 (irq = 5) is a 8250
[   37.934564] Couldn't register serial port 0000:03:09.0: -28
[   37.934636] mice: PS/2 mouse device common for all mice
[   37.935299] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.935562] input: Macintosh mouse button emulation as /class/input/input0
[   37.935612] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   37.935618] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   37.935830] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   37.935835] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   37.938608] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.938614] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.938765] EISA: Probing bus 0 at eisa.0
[   37.938775] Cannot allocate resource for EISA slot 1
[   37.938779] Cannot allocate resource for EISA slot 2
[   37.938805] EISA: Detected 0 cards.
[   37.968916] TCP cubic registered
[   37.968927] NET: Registered protocol family 1
[   37.968958] Using IPI No-Shortcut mode
[   37.969025] ACPI: (supports S0 S3 S4 S5)
[   37.969094]   Magic number: 7:568:456
[   37.969237]   hash matches device urandom
[   37.969396] Time: tsc clocksource has been installed.
[   37.969543] Freeing unused kernel memory: 328k freed
[   37.997622] input: AT Translated Set 2 keyboard as /class/input/input1
[   39.506064] Capability LSM initialized
[   39.567373] ACPI: Fan [FAN] (on)
[   39.574351] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   39.577252] ACPI: Thermal Zone [THRM] (-11 C)
[   40.613214] usbcore: registered new interface driver usbfs
[   40.613244] usbcore: registered new interface driver hub
[   40.613275] usbcore: registered new device driver usb
[   40.614296] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.614351] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   40.614357] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   40.614516] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   40.614536] ohci_hcd 0000:00:0b.0: irq 5, io mem 0xfe02f000
[   40.675615] usb usb1: configuration #1 chosen from 1 choice
[   40.675651] hub 1-0:1.0: USB hub found
[   40.675664] hub 1-0:1.0: 8 ports detected
[   40.729633] ieee1394: Initialized config rom entry `ip1394'
[   40.777340] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   40.777347] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   40.777380] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   40.777418] ehci_hcd 0000:00:0b.1: debug port 1
[   40.777424] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   40.777436] ehci_hcd 0000:00:0b.1: irq 10, io mem 0xfe02e000
[   40.777446] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.777534] usb usb2: configuration #1 chosen from 1 choice
[   40.777567] hub 2-0:1.0: USB hub found
[   40.777576] hub 2-0:1.0: 8 ports detected
[   40.805604] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   40.889864] SCSI subsystem initialized
[   40.897688] libata version 2.20 loaded.
[   40.903423] sata_nv 0000:00:0e.0: version 3.3
[   40.903467] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   40.903521] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 10
[   40.960766] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 10
[   40.960785] scsi0 : sata_nv
[   41.054493] FDC 0 is a post-1991 82077
[   41.428633] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   41.481463] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   41.481473] ata1.00: ATA-7: ST3200827AS, 3.AAE, max UDMA/133
[   41.481478] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   41.539735] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   41.539742] ata1.00: configured for UDMA/133
[   41.539755] scsi1 : sata_nv
[   41.736531] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   41.848499] ata2: SATA link down (SStatus 0 SControl 300)
[   41.859045] ATA: abnormal status 0x7F on port 0x00010977
[   41.859196] scsi 0:0:0:0: Direct-Access     ATA      ST3200827AS      3.AA PQ: 0 ANSI: 5
[   41.860891] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   41.860942] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 11
[   41.860974] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 11
[   41.860993] scsi2 : sata_nv
[   41.953148] usb 1-2: configuration #1 chosen from 1 choice
[   42.172412] ata3: SATA link down (SStatus 0 SControl 300)
[   42.182958] ATA: abnormal status 0x7F on port 0x000109e7
[   42.182983] scsi3 : sata_nv
[   42.260395] usb 1-5: new full speed USB device using ohci_hcd and address 3
[   42.475979] usb 1-5: configuration #1 chosen from 1 choice
[   42.480700] usbcore: registered new interface driver hiddev
[   42.486010] input: Logitech Optical USB Mouse as /class/input/input2
[   42.486041] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-2
[   42.486061] usbcore: registered new interface driver usbhid
[   42.486066] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   42.492351] ata4: SATA link down (SStatus 0 SControl 300)
[   42.502896] ATA: abnormal status 0x7F on port 0x00010967
[   42.555825] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   42.556007] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   42.556016] forcedeth: using HIGHDMA
[   42.562049] usbcore: registered new interface driver libusual
[   42.567760] Initializing USB Mass Storage driver...
[   42.567841] scsi4 : SCSI emulation for USB Mass Storage devices
[   42.567906] usbcore: registered new interface driver usb-storage
[   42.567910] USB Mass Storage support registered.
[   42.568020] usb-storage: device found at 3
[   42.568023] usb-storage: waiting for device to settle before scanning
[   42.591971] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   42.591994] sda: Write Protect is off
[   42.591998] sda: Mode Sense: 00 3a 00 00
[   42.592018] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.592090] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   42.592102] sda: Write Protect is off
[   42.592106] sda: Mode Sense: 00 3a 00 00
[   42.592137] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.592144]  sda: sda1
[   42.612190] sd 0:0:0:0: Attached scsi disk sda
[   42.618137] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.076458] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
[   43.076598] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   43.076625] NFORCE-MCP51: chipset revision 161
[   43.076628] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   43.076635] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   43.076642] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   43.076654]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[   43.076669]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[   43.076679] Probing IDE interface ide0...
[   43.588143] hdb: Maxtor 4D060H3, ATA DISK drive
[   43.644477] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   43.670422] Probing IDE interface ide1...
[   43.824129] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200014ef7f]
[   44.403927] hdc: HL-DT-ST DVD-RW_GSA-H11N, ATAPI CD/DVD-ROM drive
[   44.740950] ide1 at 0x170-0x177,0x376 on irq 15
[   44.757072] hdb: max request size: 128KiB
[   44.769301] hdb: 120069936 sectors (61475 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   44.769312] hdb: cache flushes not supported
[   44.769355]  hdb: hdb1 hdb2 < hdb5 >
[   44.822452] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   44.822465] Uniform CD-ROM driver Revision: 3.20
[   45.145586] Attempting manual resume
[   45.145591] swsusp: Resume From Partition 3:69
[   45.145594] PM: Checking swsusp image.
[   45.145775] PM: Resume from disk failed.
[   45.167590] EXT3-fs: INFO: recovery required on readonly filesystem.
[   45.167596] EXT3-fs: write access will be enabled during recovery.
[   47.182438] kjournald starting.  Commit interval 5 seconds
[   47.182455] EXT3-fs: recovery complete.
[   47.186879] EXT3-fs: mounted filesystem with writeback data mode.
[   47.564212] usb-storage: device scan complete
[   47.571208] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   47.578201] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   47.585202] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   47.592209] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   47.603225] sd 4:0:0:0: Attached scsi removable disk sdb
[   47.603272] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   47.614206] sd 4:0:0:1: Attached scsi removable disk sdc
[   47.614244] sd 4:0:0:1: Attached scsi generic sg2 type 0
[   47.625206] sd 4:0:0:2: Attached scsi removable disk sdd
[   47.625245] sd 4:0:0:2: Attached scsi generic sg3 type 0
[   47.636202] sd 4:0:0:3: Attached scsi removable disk sde
[   47.636247] sd 4:0:0:3: Attached scsi generic sg4 type 0
[   62.410708] NET: Registered protocol family 17
[   64.022152] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.473362] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   64.607405] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   64.607451] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   65.416858] Linux agpgart interface v0.102 (c) Dave Jones
[   65.993101] nvidia: module license 'NVIDIA' taints kernel.
[   66.273644] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   66.273960] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   66.281284] input: PC Speaker as /class/input/input3
[   66.771223] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   66.900634] parport: PnPBIOS parport detected.
[   66.900693] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   67.089854] intel8x0_measure_ac97_clock: measured 54588 usecs
[   67.089860] intel8x0: clocking to 46929
[  112.143923] fuse init (API version 7.8)
[  112.177216] lp0: using parport0 (interrupt-driven).
[  112.265599] Adding 2498068k swap on /dev/disk/by-uuid/aea71a3d-ebbb-46f0-b411-e2fa8d477458.  Priority:-1 extents:1 across:2498068k
[  112.453030] EXT3 FS on hdb1, internal journal
[  112.684152] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  112.688046] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  112.885778] NTFS volume version 3.1.
[  112.932559] NET: Registered protocol family 10
[  112.932690] lo: Disabled Privacy Extensions
[  113.684437] ibm_acpi: ec object not found
[  113.855596] No dock devices found.
[  113.928559] Using specific hotkey driver
[  114.045653] input: Power Button (FF) as /class/input/input4
[  114.052956] ACPI: Power Button (FF) [PWRF]
[  114.122884] input: Power Button (CM) as /class/input/input5
[  114.130209] ACPI: Power Button (CM) [PWRB]
[  114.180399] pcc_acpi: loading...
[  114.626747] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (version 2.00.00)
[  114.626802] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[  114.626807] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[  114.626811] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[  114.626816] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   87.260000] Time: acpi_pm clocksource has been installed.
[   89.668000] ppdev: user-space parallel port driver
[   92.076000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   92.076000] apm: overridden by ACPI.
[   92.548000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   92.640000] Netfilter messages via NETLINK v0.30.
[   92.656000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   97.592000] Bluetooth: Core ver 2.11
[   97.592000] NET: Registered protocol family 31
[   97.592000] Bluetooth: HCI device and connection manager initialized
[   97.592000] Bluetooth: HCI socket layer initialized
[   97.764000] Bluetooth: L2CAP ver 2.8
[   97.764000] Bluetooth: L2CAP socket layer initialized
[   97.804000] Bluetooth: RFCOMM socket layer initialized
[   97.804000] Bluetooth: RFCOMM TTY layer initialized
[   97.804000] Bluetooth: RFCOMM ver 1.8
[  102.968000] eth0: no IPv6 routers present

```
Right now this is with pci=noacpi acpi=noirq noapic in attempt to stop the freezing.
And lsusb gives
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by skyhopper88 on 2007-05-22
Gah, it was behaving nicely for about a day and the mouse froze again. Running in Windows makes me sad...

---

### Post by skyhopper88 on 2007-06-07
I was hoping the 2.6.20-16 kernal would behave itself, but no luck. Is there anything else I can attempt?

---

### Post by skyhopper88 on 2007-06-09
Disabled USB 2.0 and used 1.1 instead, still froze. Didn't disable it at boot though, not sure if that makes a difference.

---

