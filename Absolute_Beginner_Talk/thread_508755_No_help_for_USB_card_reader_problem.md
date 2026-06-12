---
title: "No help for USB card reader problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by cypah on 2007-07-24
The version is current 7.04 Gnome, all updates made to this date. This card reader was reading just fine I simply put the card in and a dialog would pop asking me what to choose. This past Fri this simply did not happen. I have changed nothing I have used the command line since but not before reading stopped.

here is what I have done and I will post the logged results so that perhaps someone can instruct me what to do and more important please tell me what could have caused this problem to occur. Right now I have some important data on the card and need to get to it so really need to fix this or reinstall the system... shudder .. so please help me out.

here is results of df ... herb@Aelf-FarieForge:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             78415940   4809592  69623036   7% /
varrun                  128064       208    127856   1% /var/run
varlock                 128064         0    128064   0% /var/lock
procbususb              128064        72    127992   1% /proc/bus/usb
udev                    128064        72    127992   1% /dev
devshm                  128064         0    128064   0% /dev/shm
lrm                     128064     33788     94276  27% /lib/modules/2.6.20-16-generic/volatile

Here is dmesg  herb@Aelf-FarieForge:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e7000 size: 0000000000019000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fefdc00 end: 000000000fffdc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fffdc00 size: 0000000000002000 end: 000000000ffffc00 type: 3
[    0.000000] copy_e820_map() start: 000000000ffffc00 size: 0000000000000400 end: 0000000010000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffe7000 size: 0000000000019000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fffdc00 (usable)
[    0.000000]  BIOS-e820: 000000000fffdc00 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65533) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65533
[    0.000000]   HighMem     65533 ->    65533
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65533
[    0.000000] On node 0 totalpages: 65533
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60958 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ad0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001 PTL  0x01000000) @ 0x0fffdd69
[    0.000000] ACPI: FADT (v001 INTEL  SEATTLE2 0x20000817 PTL  0x000f4240) @ 0x0ffffb8c
[    0.000000] ACPI: DSDT (v001  Intel  S2440BX 0x00000001 MSFT 0x01000004) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effe7000)
[    0.000000] Detected 902.854 MHz processor.
[   24.421836] Built 1 zonelists.  Total pages: 65022
[   24.421844] Kernel command line: root=UUID=47f44d7d-3bc6-42eb-9dbb-b8f6ee97788e ro quiet splash
[   24.422277] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   24.422294] mapped APIC to ffffd000 (0120a000)
[   24.422302] Enabling fast FPU save and restore... done.
[   24.422308] Enabling unmasked SIMD FPU exception support... done.
[   24.422329] Initializing CPU#0
[   24.422409] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   24.423268] Console: colour VGA+ 80x25
[   24.423658] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.424019] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   24.443086] Memory: 248888k/262132k available (1992k kernel code, 12724k reserved, 900k data, 328k init, 0k highmem)
[   24.443111] virtual kernel memory layout:
[   24.443114]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   24.443117]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.443120]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   24.443124]     lowmem  : 0xc0000000 - 0xcfffd000   ( 255 MB)
[   24.443127]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   24.443130]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   24.443133]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   24.443141] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.490477] Calibrating delay using timer specific routine.. 1098.68 BogoMIPS (lpj=2197362)
[   24.490572] Security Framework v1.0.0 initialized
[   24.490588] SELinux:  Disabled at boot.
[   24.490628] Mount-cache hash table entries: 512
[   24.490924] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   24.490948] CPU: L1 I cache: 16K, L1 D cache: 16K
[   24.490954] CPU: L2 cache: 512K
[   24.490960] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   24.490984] Compat vDSO mapped to ffffe000.
[   24.490999] Remapping vsyscall page to ffffe000
[   24.491018] Checking 'hlt' instruction... OK.
[   24.500374] SMP alternatives: switching to UP code
[   24.500693] Freeing SMP alternatives: 11k freed
[   24.501060] Early unpacking initramfs... done
[   25.326905] ACPI: Core revision 20060707
[   25.327525] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   25.329191] ACPI: setting ELCR to 0200 (from 0e20)
[   25.330136] CPU0: Intel Pentium III (Katmai) stepping 03
[   25.330147] SMP motherboard not detected.
[   25.330152] Local APIC not detected. Using dummy APIC emulation.
[   25.330251] Brought up 1 CPUs
[   25.330789] Booting paravirtualized kernel on bare hardware
[   25.330922] Time: 18:30:31  Date: 06/23/107
[   25.330991] NET: Registered protocol family 16
[   25.331201] EISA bus registered
[   25.331212] ACPI: bus type pci registered
[   25.331405] PCI: PCI BIOS revision 2.10 entry at 0xfd9b4, last bus=1
[   25.331411] PCI: Using configuration type 1
[   25.331415] Setting up standard PCI resources
[   25.336185] ACPI: Interpreter enabled
[   25.336193] ACPI: Using PIC for interrupt routing
[   25.336898] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.336914] PCI: Probing PCI hardware (bus 00)
[   25.336951] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   25.339877] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   25.339881] * this clock source is slow. Consider trying other clock sources
[   25.339919] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   25.339926] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   25.339997] PCI: Firmware left 0000:00:0e.0 e100 interrupts enabled, disabling
[   25.340209] Boot video device is 0000:01:00.0
[   25.340257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.342808] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   25.343298] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   25.343797] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12)
[   25.344278] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[   25.344536] ACPI: Power Resource [PFAN] (on)
[   25.350252] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.350276] pnp: PnP ACPI init
[   25.359780] pnp: PnP ACPI: found 12 devices
[   25.359790] PnPBIOS: Disabled by ACPI PNP
[   25.359912] PCI: Using ACPI for IRQ routing
[   25.359920] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.361117] NET: Registered protocol family 8
[   25.361123] NET: Registered protocol family 20
[   25.361287] pnp: 00:01: ioport range 0x7000-0x700f has been reserved
[   25.361295] pnp: 00:01: ioport range 0x8000-0x803f could not be reserved
[   25.362162] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:01:00.0
[   25.362202] PCI: Bridge: 0000:00:01.0
[   25.362206]   IO window: disabled.
[   25.362214]   MEM window: e9000000-e9ffffff
[   25.362221]   PREFETCH window: f0000000-f7ffffff
[   25.362285] NET: Registered protocol family 2
[   25.385212] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   25.385395] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   25.385552] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   25.385640] TCP: Hash tables configured (established 8192 bind 4096)
[   25.385646] TCP reno registered
[   25.392581] checking if image is initramfs... it is
[   26.953286] Freeing initrd memory: 6769k freed
[   26.954126] audit: initializing netlink socket (disabled)
[   26.954152] audit(1185215433.848:1): initialized
[   26.954460] VFS: Disk quotas dquot_6.5.1
[   26.954507] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.954625] io scheduler noop registered
[   26.954633] io scheduler anticipatory registered
[   26.954638] io scheduler deadline registered
[   26.954664] io scheduler cfq registered (default)
[   26.954681] Limiting direct PCI/PCI transfers.
[   26.955127] isapnp: Scanning for PnP cards...
[   27.170511] isapnp: No Plug & Play device found
[   27.255528] Real Time Clock Driver v1.12ac
[   27.255660] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.255836] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.256124] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.257411] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.257855] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.258769] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   27.258777] PCI: setting IRQ 9 as level-triggered
[   27.258782] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   27.259378] 0000:00:10.0: ttyS2 at I/O 0x1008 (irq = 9) is a 16450
[   27.259745] 0000:00:10.0: ttyS3 at I/O 0x1010 (irq = 9) is a 8250
[   27.259965] Couldn't register serial port 0000:00:10.0: -28
[   27.260140] mice: PS/2 mouse device common for all mice
[   27.261827] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.262319] input: Macintosh mouse button emulation as /class/input/input0
[   27.262414] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.262423] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.262777] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MICE] at 0x60,0x64 irq 1,12
[   27.264407] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.264418] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.264705] EISA: Probing bus 0 at eisa.0
[   27.264719] Cannot allocate resource for EISA slot 1
[   27.264743] Cannot allocate resource for EISA slot 7
[   27.264748] Cannot allocate resource for EISA slot 8
[   27.264753] EISA: Detected 0 cards.
[   27.283166] TCP cubic registered
[   27.283185] NET: Registered protocol family 1
[   27.283232] Using IPI No-Shortcut mode
[   27.283357] ACPI: (supports S0 S1 S5)
[   27.283439]   Magic number: 15:122:545
[   27.283546] Time: tsc clocksource has been installed.
[   27.284373] Freeing unused kernel memory: 328k freed
[   27.292635] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.791516] Capability LSM initialized
[   28.872276] ACPI: Fan [FAN1] (on)
[   28.883229] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   29.948298] SCSI subsystem initialized
[   29.976632] libata version 2.20 loaded.
[   29.986131] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   29.986154] PIIX4: chipset revision 1
[   29.986159] PIIX4: not 100% native mode: will probe irqs later
[   29.986173]     ide0: BM-DMA at 0x1460-0x1467, BIOS settings: hda:DMA, hdb:pio
[   29.986192]     ide1: BM-DMA at 0x1468-0x146f, BIOS settings: hdc:DMA, hdd:pio
[   29.986207] Probing IDE interface ide0...
[   30.076338] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   30.076346] e100: Copyright(c) 1999-2006 Intel Corporation
[   30.194766] usbcore: registered new interface driver usbfs
[   30.194824] usbcore: registered new interface driver hub
[   30.194884] usbcore: registered new device driver usb
[   30.198892] USB Universal Host Controller Interface driver v3.0
[   30.329584] hda: IC35L080AVVA07-0, ATA DISK drive
[   30.404943] Floppy drive(s): fd0 is 1.44M
[   30.424508] FDC 0 is a post-1991 82077
[    9.436000] Time: acpi_pm clocksource has been installed.
[    9.892000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    9.892000] Probing IDE interface ide1...
[   10.628000] hdc: LG CD-RW CED-8120B, ATAPI CD/DVD-ROM drive
[   11.300000] ide1 at 0x170-0x177,0x376 on irq 15
[   11.308000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   11.308000] PCI: setting IRQ 10 as level-triggered
[   11.308000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   11.332000] e100: eth0: e100_probe: addr 0xe8008000, irq 10, MAC addr 00:D0:B7:BA:85:FE
[   11.332000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   11.332000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   11.332000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   11.332000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001440
[   11.336000] usb usb1: configuration #1 chosen from 1 choice
[   11.336000] hub 1-0:1.0: USB hub found
[   11.336000] hub 1-0:1.0: 2 ports detected
[   11.364000] hda: max request size: 128KiB
[   11.400000] hda: 160836480 sectors (82348 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(33)
[   11.404000] hda: cache flushes supported
[   11.404000]  hda: hda1 hda2 < hda5 >
[   11.460000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 8192kB Cache, DMA
[   11.460000] Uniform CD-ROM driver Revision: 3.20
[   11.680000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   11.800000] usb 1-1: device descriptor read/64, error -71
[   11.880000] Attempting manual resume
[   11.880000] swsusp: Resume From Partition 3:5
[   11.880000] PM: Checking swsusp image.
[   11.900000] PM: Resume from disk failed.
[   12.004000] kjournald starting.  Commit interval 5 seconds
[   12.004000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.024000] usb 1-1: device descriptor read/64, error -71
[   12.240000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   12.360000] usb 1-1: device descriptor read/64, error -71
[   12.584000] usb 1-1: device descriptor read/64, error -71
[   12.800000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   13.208000] usb 1-1: device not accepting address 4, error -71
[   13.320000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   13.736000] usb 1-1: device not accepting address 5, error -71
[   25.864000] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[   27.216000] NET: Registered protocol family 17
[   30.476000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.508000] Linux agpgart interface v0.102 (c) Dave Jones
[   30.516000] agpgart: Detected an Intel 440BX Chipset.
[   30.524000] agpgart: AGP aperture is 64M @ 0xec000000
[   31.204000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.396000] input: PC Speaker as /class/input/input2
[   31.780000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   32.160000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   32.736000] parport: PnPBIOS parport detected.
[   32.736000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   33.452000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   33.452000] PCI: setting IRQ 5 as level-triggered
[   33.452000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   34.744000] fuse init (API version 7.8)
[   34.824000] lp0: using parport0 (interrupt-driven).
[   34.924000] Adding 746980k swap on /dev/disk/by-uuid/3a747e72-03db-4823-aaf9-5ee23451ee9b.  Priority:-1 extents:1 across:746980k
[   35.148000] EXT3 FS on hda1, internal journal
[   35.600000] NET: Registered protocol family 10
[   35.600000] lo: Disabled Privacy Extensions
[   43.676000] input: Power Button (FF) as /class/input/input4
[   43.676000] ACPI: Power Button (FF) [PWRF]
[   44.116000] Using specific hotkey driver
[   44.296000] ibm_acpi: ec object not found
[   44.460000] No dock devices found.
[   44.688000] pcc_acpi: loading...
[   46.252000] eth0: no IPv6 routers present
[   55.344000] ppdev: user-space parallel port driver
[   61.628000] apm: BIOS not found.
[   63.556000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   64.436000] Netfilter messages via NETLINK v0.30.
[   64.492000] nf_conntrack version 0.5.0 (2047 buckets, 16376 max)
[   66.536000] lp0 off-line
[   68.576000] Bluetooth: Core ver 2.11
[   68.576000] NET: Registered protocol family 31
[   68.576000] Bluetooth: HCI device and connection manager initialized
[   68.576000] Bluetooth: HCI socket layer initialized
[   68.640000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   68.696000] Bluetooth: L2CAP ver 2.8
[   68.696000] Bluetooth: L2CAP socket layer initialized
[   68.760000] usb 1-1: device descriptor read/64, error -71
[   68.984000] usb 1-1: device descriptor read/64, error -71
[   69.200000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[   69.320000] usb 1-1: device descriptor read/64, error -71
[   69.544000] usb 1-1: device descriptor read/64, error -71
[   69.760000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[   70.168000] usb 1-1: device not accepting address 8, error -71
[   70.280000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[   70.688000] usb 1-1: device not accepting address 9, error -71
[   70.700000] eth0: no IPv6 routers present
[   70.732000] Bluetooth: RFCOMM socket layer initialized
[   70.732000] Bluetooth: RFCOMM TTY layer initialized
[   70.732000] Bluetooth: RFCOMM ver 1.8

And here is lspci  herb@Aelf-FarieForge:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
00:0e.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:10.0 Modem: Motorola Unknown device 3052 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
herb@Aelf-FarieForge:~$ 

I have tried googling for the uhci_hcd  device descriptor read/64, error -71 but found nothing relevant. 
I can use the command if someone can provide me with what to do I am not sure what the name is for the devise the final 10 lines show what appears to be four devises failing all with same description and I think this reader reads 4 different kinds of flash cards I only have one ... a compact flash 256mb I just took about 30-40 pics and the Camera did not report any problem the .jpg files are there on the card. I can view them with the cam-viewer screen.
Thanks cypah

---

### Post by e_james on 2007-07-25
Based on my own recent experiences, I would want to establish that the memory card, the card reader, the usb lead and the usb socket are all in working order. I appear to have a faulty usb socket on my laptop. I have still to verify if it's the power lines or the data lines or both which have failed. I also replaced a printer recently only to find that the usb adaptor card was also faulty.

---

### Post by cypah on 2007-08-06
This turned out to be the reader itself had crashed replaceing it solved the problem.

---

### Post by e_james on 2007-08-08
Thanks for the update. It's nice to know the outcome of these questions.

---

