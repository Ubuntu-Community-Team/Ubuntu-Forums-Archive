---
title: "Login Freeze"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Evmax318 on 2007-11-11
When I boot up Gusty after a restart and leave it at login for 10 or more minutes, I come back to have Gusty frozen and my CAPS Lock light blinking on my keyboard. Is this some security setting I dont know about?

---

### Post by tomsa on 2007-11-12
I'm Having the same problem!  I was just looking for a possible solution in here as well.  The only thing that has worked for me so far is to keep logging in, trying different sessions (gnome, kde, failsafe gnome, failsafe terminal) and restarting my computer after it locks over and over until eventually I get it started.  I wish I was more effective at the command line so that I could provide some useful information to someone in here who knows what they are doing!  Please let me know if you find anything out that might help me!

---

### Post by tomsa on 2007-11-12
I just found something else that may help us get the info we need.  If you open a terminal and type "dmesg" you will get a rundown of your computer's boot scripts!  I am attaching mine for anyone to read to see if that helps- you may want to do the same!  The following is what I get when I enter the dmesg command:

> 
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ffc000 (usable)
[    0.000000]  BIOS-e820: 0000000017ffc000 - 0000000017fff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017fff000 - 0000000018000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98300) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98300
[    0.000000]   HighMem     98300 ->    98300
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98300
[    0.000000] On node 0 totalpages: 98300
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 735 pages used for memmap
[    0.000000]   Normal zone: 93469 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5CD0 checksum 0
[    0.000000] ACPI: RSDP 000F5CD0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 17FFC000, 002C (r1 ASUS   K7V      30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 17FFC080, 0074 (r1 ASUS   K7V      30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 17FFC100, 28D8 (r1   ASUS K7V          1000 MSFT  100000B)
[    0.000000] ACPI: FACS 17FFF000, 0040
[    0.000000] ACPI: BOOT 17FFC040, 0028 (r1 ASUS   K7V      30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 97533
[    0.000000] Kernel command line: root=UUID=443f9e1c-94d7-48c9-b81e-1137ab40118a ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0130d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 800.058 MHz processor.
[   19.426603] Console: colour VGA+ 80x25
[   19.427493] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.428316] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.457576] Memory: 377996k/393200k available (2015k kernel code, 14692k reserved, 916k data, 364k init, 0k highmem)
[   19.457603] virtual kernel memory layout:
[   19.457606]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   19.457610]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.457613]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   19.457617]     lowmem  : 0xc0000000 - 0xd7ffc000   ( 383 MB)
[   19.457620]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   19.457623]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   19.457627]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   19.457636] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.457741] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.537720] Calibrating delay using timer specific routine.. 1601.99 BogoMIPS (lpj=3203989)
[   19.537791] Security Framework v1.0.0 initialized
[   19.537808] SELinux:  Disabled at boot.
[   19.537854] Mount-cache hash table entries: 512
[   19.538190] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   19.538214] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.538222] CPU: L2 Cache: 512K (64 bytes/line)
[   19.538229] CPU: After all inits, caps: 0183f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   19.538255] Compat vDSO mapped to ffffe000.
[   19.538285] Checking 'hlt' instruction... OK.
[   19.553788] SMP alternatives: switching to UP code
[   19.554351] Freeing SMP alternatives: 11k freed
[   19.555123] Early unpacking initramfs... done
[   20.399445] ACPI: Core revision 20070126
[   20.399672] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.401940] ACPI: setting ELCR to 0200 (from 0c20)
[   20.402143] CPU0: AMD Athlon(tm) Processor stepping 02
[   20.402157] SMP motherboard not detected.
[   20.402165] Local APIC not detected. Using dummy APIC emulation.
[   20.402277] Brought up 1 CPUs
[   20.402630] Booting paravirtualized kernel on bare hardware
[   20.402768] Time:  0:45:16  Date: 10/13/107
[   20.402845] NET: Registered protocol family 16
[   20.403133] EISA bus registered
[   20.403162] ACPI: bus type pci registered
[   20.404278] PCI: PCI BIOS revision 2.10 entry at 0xf0880, last bus=1
[   20.404285] PCI: Using configuration type 1
[   20.404289] Setting up standard PCI resources
[   20.417356] ACPI: EC: Look up EC in DSDT
[   20.421970] ACPI: Interpreter enabled
[   20.421981] ACPI: (supports S0 S1 S4 S5)
[   20.422020] ACPI: Using PIC for interrupt routing
[   20.432748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.432776] PCI: Probing PCI hardware (bus 00)
[   20.433270] PCI quirk: region e400-e4ff claimed by vt82c586 ACPI
[   20.433281] PCI quirk: region e800-e80f claimed by vt82c686 SMB
[   20.433589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.437974] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   20.438168] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   20.438335] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.438518] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   20.438752] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.438780] pnp: PnP ACPI init
[   20.438807] ACPI: bus type pnp registered
[   20.445494] pnp: PnP ACPI: found 14 devices
[   20.445502] ACPI: ACPI bus type pnp unregistered
[   20.445513] PnPBIOS: Disabled by ACPI PNP
[   20.445664] PCI: Using ACPI for IRQ routing
[   20.445673] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.447606] NET: Registered protocol family 8
[   20.447613] NET: Registered protocol family 20
[   20.447814] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   20.447823] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   20.447831] pnp: 00:00: iomem range 0x100000-0x17ffffff could not be reserved
[   20.447840] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   20.447868] pnp: 00:03: ioport range 0xe400-0xe47f has been reserved
[   20.447876] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   20.449099] Time: tsc clocksource has been installed.
[   20.478781] PCI: Bridge: 0000:00:01.0
[   20.478788]   IO window: d000-dfff
[   20.478798]   MEM window: df000000-dfefffff
[   20.478805]   PREFETCH window: dff00000-e3ffffff
[   20.478832] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.478869] NET: Registered protocol family 2
[   20.517203] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.517351] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   20.518105] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.518766] TCP: Hash tables configured (established 16384 bind 16384)
[   20.518775] TCP reno registered
[   20.529393] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   21.247844]  it is
[   22.122482] Freeing initrd memory: 7337k freed
[   22.122774] Simple Boot Flag at 0x3a set to 0x1
[   22.123661] audit: initializing netlink socket (disabled)
[   22.123697] audit(1194914717.496:1): initialized
[   22.129358] VFS: Disk quotas dquot_6.5.1
[   22.129538] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.129824] io scheduler noop registered
[   22.129831] io scheduler anticipatory registered
[   22.129836] io scheduler deadline registered
[   22.129881] io scheduler cfq registered (default)
[   22.129917] PCI: VIA PCI bridge detected. Disabling DAC.
[   22.129925] PCI: Disabling Via external APIC routing
[   22.129970] Boot video device is 0000:01:00.0
[   22.130419] isapnp: Scanning for PnP cards...
[   22.484993] isapnp: No Plug & Play device found
[   22.578852] Real Time Clock Driver v1.12ac
[   22.579101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.579273] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.579882] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.581456] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.582111] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.584425] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.585046] input: Macintosh mouse button emulation as /class/input/input0
[   22.585295] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.585786] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.585801] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.586303] mice: PS/2 mouse device common for all mice
[   22.586614] EISA: Probing bus 0 at eisa.0
[   22.586677] EISA: Detected 0 cards.
[   22.587131] TCP cubic registered
[   22.587171] NET: Registered protocol family 1
[   22.587225] Using IPI No-Shortcut mode
[   22.587761]   Magic number: 15:239:759
[   22.589195] Freeing unused kernel memory: 364k freed
[   22.623605] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.176837] AppArmor: AppArmor initialized<5>audit(1194914719.496:2):  type=1505 info="AppArmor initialized" pid=1169
[   24.195188] fuse init (API version 7.8)
[   24.209106] Failure registering capabilities with primary security module.
[   24.249701] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   24.249717] ACPI: Processor [CPU0] (supports 16 throttling states)
[   25.878038] SCSI subsystem initialized
[   25.892654] libata version 2.21 loaded.
[   25.908140] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.908155] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.909849] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   25.909898] VP_IDE: chipset revision 16
[   25.909903] VP_IDE: not 100% native mode: will probe irqs later
[   25.909925] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:04.1
[   25.909938]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:pio
[   25.909961]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:pio
[   25.909978] Probing IDE interface ide0...
[   25.986654] usbcore: registered new interface driver usbfs
[   25.986719] usbcore: registered new interface driver hub
[   25.986794] usbcore: registered new device driver usb
[   25.989252] USB Universal Host Controller Interface driver v3.0
[   26.278692] Floppy drive(s): fd0 is 1.44M
[   26.344719] hda: WDC WD800JB-00CRA1, ATA DISK drive
[   26.412830] FDC 0 is a post-1991 82077
[    7.092000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.120000] Time: acpi_pm clocksource has been installed.
[    7.568000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.588000] Probing IDE interface ide1...
[    8.452000] hdc: PLEXTOR CD-R PX-W4824A, ATAPI CD/DVD-ROM drive
[    8.788000] ide1 at 0x170-0x177,0x376 on irq 15
[    8.788000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    8.788000] PCI: setting IRQ 5 as level-triggered
[    8.788000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    8.788000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[    8.792000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[    8.792000] uhci_hcd 0000:00:04.2: irq 5, io base 0x0000b400
[    8.792000] usb usb1: configuration #1 chosen from 1 choice
[    8.792000] hub 1-0:1.0: USB hub found
[    8.792000] hub 1-0:1.0: 2 ports detected
[    8.812000] hda: max request size: 128KiB
[    8.836000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(66)
[    8.836000] hda: cache flushes not supported
[    8.836000]  hda: hda1 hda2 < hda5 >
[    8.896000] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    8.896000] uhci_hcd 0000:00:04.3: UHCI Host Controller
[    8.896000] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[    8.896000] uhci_hcd 0000:00:04.3: irq 5, io base 0x0000b000
[    8.896000] usb usb2: configuration #1 chosen from 1 choice
[    8.896000] hub 2-0:1.0: USB hub found
[    8.896000] hub 2-0:1.0: 2 ports detected
[    8.928000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[    8.928000] Uniform CD-ROM driver Revision: 3.20
[    9.136000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    9.268000] Attempting manual resume
[    9.268000] swsusp: Resume From Partition 3:5
[    9.268000] PM: Checking swsusp image.
[    9.272000] PM: Resume from disk failed.
[    9.276000] usb 1-1: configuration #1 chosen from 1 choice
[    9.280000] hub 1-1:1.0: USB hub found
[    9.280000] hub 1-1:1.0: 4 ports detected
[    9.372000] kjournald starting.  Commit interval 5 seconds
[    9.372000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.632000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    9.792000] usb 1-2: configuration #1 chosen from 1 choice
[   10.264000] usb 1-1.4: new full speed USB device using uhci_hcd and address 4
[   10.460000] usb 1-1.4: configuration #1 chosen from 1 choice
[   16.800000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.888000] Netfilter messages via NETLINK v0.30.
[   16.904000] nf_conntrack version 0.5.0 (3071 buckets, 24568 max)
[   21.632000] parport_pc: VIA 686A/8231 detected
[   21.632000] parport_pc: probing current configuration
[   21.632000] parport_pc: Current parallel port base: 0x378
[   21.632000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   21.660000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.680000] agpgart: Detected VIA Apollo Pro 133 chipset
[   21.688000] agpgart: AGP aperture is 64M @ 0xe4000000
[   21.708000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.712000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.328000] parport0: Printer, HEWLETT-PACKARD DESKJET 670C
[   22.328000] parport_pc: VIA parallel port: io=0x378, irq=7
[   23.564000] via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   23.680000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   24.196000] input: PC Speaker as /class/input/input3
[   24.664000] usbcore: registered new interface driver libusual
[   24.712000] eth0: register 'cdc_ether' at usb-0000:00:04.2-2, CDC Ethernet Device, 00:10:95:d5:00:ce
[   24.712000] usbcore: registered new interface driver cdc_ether
[   24.788000] Initializing USB Mass Storage driver...
[   24.788000] scsi0 : SCSI emulation for USB Mass Storage devices
[   24.792000] usb-storage: device found at 4
[   24.792000] usb-storage: waiting for device to settle before scanning
[   24.792000] usbcore: registered new interface driver usb-storage
[   24.792000] USB Mass Storage support registered.
[   25.512000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   25.512000] PCI: setting IRQ 10 as level-triggered
[   25.512000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   26.464000] lp0: using parport0 (interrupt-driven).
[   26.560000] Adding 1124508k swap on /dev/hda5.  Priority:-1 extents:1 across:1124508k
[   26.908000] EXT3 FS on hda1, internal journal
[   29.204000] No dock devices found.
[   29.444000] input: Power Button (FF) as /class/input/input4
[   29.444000] ACPI: Power Button (FF) [PWRF]
[   29.488000] input: Power Button (CM) as /class/input/input5
[   29.488000] ACPI: Power Button (CM) [PWRB]
[   29.796000] usb-storage: device scan complete
[   29.804000] scsi 0:0:0:0: Direct-Access     WD       CR    HS-CF      3.04 PQ: 0 ANSI: 0
[   29.808000] scsi 0:0:0:1: Direct-Access     WD       CR    HS-5-IN-1  3.04 PQ: 0 ANSI: 0
[   29.888000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   29.940000] sd 0:0:0:1: [sdb] Attached SCSI removable disk
[   29.988000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.988000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   30.444000] powernow: No powernow capabilities detected
[   32.944000] ppdev: user-space parallel port driver
[   33.384000] audit(1194914748.866:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4678 profile="/usr/sbin/cupsd"
[   33.476000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.476000] apm: overridden by ACPI.
[   34.116000] Failure registering capabilities with primary security module.
[   38.308000] [drm] Initialized drm 1.1.0 20060810
[   38.328000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   38.328000] PCI: setting IRQ 11 as level-triggered
[   38.328000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   38.336000] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   38.336000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   38.340000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   38.340000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   38.828000] NET: Registered protocol family 17
[   47.892000] NET: Registered protocol family 10
[   47.892000] lo: Disabled Privacy Extensions
[   58.836000] eth0: no IPv6 routers present
[   63.996000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=39931 DF PROTO=TCP SPT=45508 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[   66.952000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=39944 DF PROTO=TCP SPT=45508 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[   69.776000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=1098 DF PROTO=TCP SPT=3460 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[   72.608000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=1944 DF PROTO=TCP SPT=3460 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[   72.964000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=39969 DF PROTO=TCP SPT=45508 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[   78.748000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=3439 DF PROTO=TCP SPT=3460 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  148.728000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  148.728000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  148.728000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  161.108000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=53958 DF PROTO=TCP SPT=1618 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  164.084000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=54065 DF PROTO=TCP SPT=1618 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  170.160000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=54385 DF PROTO=TCP SPT=1618 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  213.376000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  213.380000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  213.380000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  219.520000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=43366 DF PROTO=TCP SPT=3837 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  222.484000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=44078 DF PROTO=TCP SPT=3837 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  228.420000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=45592 DF PROTO=TCP SPT=3837 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  288.836000] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[  288.956000] usb 1-1.2: configuration #1 chosen from 1 choice
[  288.964000] scsi1 : SCSI emulation for USB Mass Storage devices
[  288.964000] usb-storage: device found at 5
[  288.964000] usb-storage: waiting for device to settle before scanning
[  289.516000] usbcore: registered new interface driver hiddev
[  289.524000] hiddev96: USB HID v1.10 Device [Western Digital External HDD] on usb-0000:00:04.2-1.2
[  289.528000] usbcore: registered new interface driver usbhid
[  289.528000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  289.588000] usbcore: registered new interface driver xpad
[  289.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  293.964000] usb-storage: device scan complete
[  293.968000] scsi 1:0:0:0: Direct-Access     WD       2500JB External  0112 PQ: 0 ANSI: 0
[  293.976000] sd 1:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[  293.984000] sd 1:0:0:0: [sdc] Write Protect is off
[  293.984000] sd 1:0:0:0: [sdc] Mode Sense: 33 00 00 00
[  293.984000] sd 1:0:0:0: [sdc] Assuming drive cache: write through
[  293.992000] sd 1:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[  293.996000] sd 1:0:0:0: [sdc] Write Protect is off
[  293.996000] sd 1:0:0:0: [sdc] Mode Sense: 33 00 00 00
[  293.996000] sd 1:0:0:0: [sdc] Assuming drive cache: write through
[  293.996000]  sdc: sdc1
[  294.008000] sd 1:0:0:0: [sdc] Attached SCSI disk
[  294.008000] sd 1:0:0:0: Attached scsi generic sg2 type 0
[  303.668000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=3458 DF PROTO=TCP SPT=4044 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  306.676000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=4442 DF PROTO=TCP SPT=4044 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  312.612000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=6447 DF PROTO=TCP SPT=4044 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  365.300000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=2676 DF PROTO=TCP SPT=1969 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  368.260000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=2991 DF PROTO=TCP SPT=1969 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  374.136000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=3508 DF PROTO=TCP SPT=1969 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  395.800000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=65.78.213.182 DST=72.195.182.39 LEN=59 TOS=0x00 PREC=0x00 TTL=112 ID=212 PROTO=UDP SPT=43550 DPT=12696 LEN=39
[  450.056000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=42567 DF PROTO=TCP SPT=4402 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  453.128000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=43313 DF PROTO=TCP SPT=4402 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  459.240000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=44903 DF PROTO=TCP SPT=4402 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  485.576000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=16038 DF PROTO=TCP SPT=2211 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  488.304000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=16510 DF PROTO=TCP SPT=2211 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  494.180000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=17609 DF PROTO=TCP SPT=2211 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  587.312000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=31828 DF PROTO=TCP SPT=2398 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  589.980000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=32241 DF PROTO=TCP SPT=2398 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  590.128000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=15235 DF PROTO=TCP SPT=4732 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  593.048000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=15953 DF PROTO=TCP SPT=4732 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  595.812000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=33005 DF PROTO=TCP SPT=2398 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  598.712000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=216.254.156.143 DST=72.195.182.39 LEN=59 TOS=0x00 PREC=0x00 TTL=118 ID=9542 PROTO=UDP SPT=45581 DPT=4054 LEN=39
[  599.128000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=17627 DF PROTO=TCP SPT=4732 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  668.308000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=42677 DF PROTO=TCP SPT=2557 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  671.132000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=42996 DF PROTO=TCP SPT=2557 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  677.168000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=43725 DF PROTO=TCP SPT=2557 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  701.748000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=48306 DF PROTO=TCP SPT=1139 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  704.764000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=49084 DF PROTO=TCP SPT=1139 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  710.636000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=50575 DF PROTO=TCP SPT=1139 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  785.624000] ppdev0: registered pardevice
[  786.588000] audit(1194915489.915:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6340 profile="/usr/sbin/cupsd"
[  786.820000] audit(1194915490.415:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6343 profile="/usr/sbin/cupsd"
[  789.432000] ppdev0: registered pardevice
[  796.140000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.240.80 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=35619 PROTO=UDP SPT=24576 DPT=1027 LEN=492
[  796.140000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.240.80 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=35620 PROTO=UDP SPT=24576 DPT=1028 LEN=492
[  796.140000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.240.80 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=35618 PROTO=UDP SPT=24576 DPT=1026 LEN=492
[  829.116000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=15139 DF PROTO=TCP SPT=1404 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  832.044000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=16046 DF PROTO=TCP SPT=1404 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  832.116000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=58846 DF PROTO=TCP SPT=2864 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  835.084000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=59018 DF PROTO=TCP SPT=2864 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  838.080000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=17735 DF PROTO=TCP SPT=1404 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  841.120000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=59386 DF PROTO=TCP SPT=2864 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  922.356000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=64970 DF PROTO=TCP SPT=3016 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  925.412000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=65194 DF PROTO=TCP SPT=3016 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  931.156000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=29 DF PROTO=TCP SPT=3016 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  986.744000] ppdev0: unregistered pardevice
[  994.060000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=65527 DF PROTO=TCP SPT=1766 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[  997.120000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=861 DF PROTO=TCP SPT=1766 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1003.144000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=2841 DF PROTO=TCP SPT=1766 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1036.432000] ppdev0: unregistered pardevice
[ 1040.184000] ppdev0: registered pardevice
[ 1041.008000] audit(1194915744.430:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6419 profile="/usr/sbin/cupsd"
[ 1041.112000] audit(1194915744.430:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6422 profile="/usr/sbin/cupsd"
[ 1042.524000] ppdev0: registered pardevice
[ 1063.020000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=9800 DF PROTO=TCP SPT=3260 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1065.588000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=10011 DF PROTO=TCP SPT=3260 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1071.676000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=10482 DF PROTO=TCP SPT=3260 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1088.096000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=201.221.26.95 DST=72.195.182.39 LEN=59 TOS=0x00 PREC=0x00 TTL=116 ID=26234 PROTO=UDP SPT=51048 DPT=12696 LEN=39
[ 1094.904000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=28655 DF PROTO=TCP SPT=1971 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1098.016000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=29786 DF PROTO=TCP SPT=1971 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1104.036000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=31914 DF PROTO=TCP SPT=1971 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1150.664000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=16593 DF PROTO=TCP SPT=3411 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1153.188000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=16799 DF PROTO=TCP SPT=3411 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1159.892000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=17294 DF PROTO=TCP SPT=3411 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1179.840000] ppdev0: unregistered pardevice
[ 1193.768000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.50.180 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=34553 PROTO=UDP SPT=13005 DPT=1027 LEN=492
[ 1193.768000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.50.180 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=34554 PROTO=UDP SPT=13005 DPT=1028 LEN=492
[ 1193.768000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.50.180 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=34552 PROTO=UDP SPT=13005 DPT=1026 LEN=492
[ 1210.592000] ppdev0: unregistered pardevice
[ 1213.988000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=218.27.148.78 DST=72.195.182.39 LEN=918 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=35904 DPT=1026 LEN=898
[ 1227.812000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=22516 DF PROTO=TCP SPT=3542 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1230.544000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=22704 DF PROTO=TCP SPT=3542 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1236.712000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=23183 DF PROTO=TCP SPT=3542 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1239.468000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=189.156.251.61 DST=72.195.182.39 LEN=63 TOS=0x00 PREC=0x00 TTL=115 ID=58573 PROTO=UDP SPT=21922 DPT=35701 LEN=43
[ 1305.312000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=28631 DF PROTO=TCP SPT=3673 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1307.892000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=28855 DF PROTO=TCP SPT=3673 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1313.948000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=29319 DF PROTO=TCP SPT=3673 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1319.076000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=222.161.2.24 DST=72.195.182.39 LEN=919 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=52148 DPT=1026 LEN=899
[ 1319.080000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=222.161.2.24 DST=72.195.182.39 LEN=919 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=52148 DPT=1027 LEN=899
[ 1383.988000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=34697 DF PROTO=TCP SPT=3806 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1386.284000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=34893 DF PROTO=TCP SPT=3806 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1392.188000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=35369 DF PROTO=TCP SPT=3806 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1398.972000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=50505 DF PROTO=TCP SPT=2616 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1401.976000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=51514 DF PROTO=TCP SPT=2616 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1408.020000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.158.132 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=26283 PROTO=UDP SPT=17044 DPT=1026 LEN=492
[ 1408.020000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.158.132 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=26284 PROTO=UDP SPT=17044 DPT=1027 LEN=492
[ 1408.020000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.158.132 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=26285 PROTO=UDP SPT=17044 DPT=1028 LEN=492
[ 1408.104000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=53474 DF PROTO=TCP SPT=2616 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1481.812000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=92.112.15.227 DST=72.195.182.39 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=34502 DF PROTO=TCP SPT=17889 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1484.612000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=92.112.15.227 DST=72.195.182.39 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=34539 DF PROTO=TCP SPT=17889 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1558.840000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=212.195.48.129 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=101 ID=16180 DF PROTO=TCP SPT=4936 DPT=5900 WINDOW=64240 RES=0x00 SYN URGP=0
[ 1567.676000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=212.195.48.129 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=101 ID=16442 DF PROTO=TCP SPT=4936 DPT=5900 WINDOW=64240 RES=0x00 SYN URGP=0
[ 1584.800000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=48216 DF PROTO=TCP SPT=4152 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1587.316000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=48449 DF PROTO=TCP SPT=4152 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1587.980000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=40118 DF PROTO=TCP SPT=3005 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1590.980000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=41081 DF PROTO=TCP SPT=3005 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1593.424000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=48969 DF PROTO=TCP SPT=4152 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1597.012000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=42846 DF PROTO=TCP SPT=3005 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1665.404000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=55227 DF PROTO=TCP SPT=4293 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1668.276000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=55459 DF PROTO=TCP SPT=4293 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1673.964000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=55961 DF PROTO=TCP SPT=4293 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1700.940000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=3918 DF PROTO=TCP SPT=3237 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1704.040000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=4881 DF PROTO=TCP SPT=3237 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1710.176000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=6684 DF PROTO=TCP SPT=3237 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1818.664000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=5768 DF PROTO=TCP SPT=4587 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1821.624000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=6110 DF PROTO=TCP SPT=4587 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1827.768000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=6909 DF PROTO=TCP SPT=4587 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1922.260000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=19014 DF PROTO=TCP SPT=4796 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1925.252000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=19411 DF PROTO=TCP SPT=4796 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1931.476000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=20233 DF PROTO=TCP SPT=4796 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1931.984000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=64610 DF PROTO=TCP SPT=3719 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1934.988000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=65415 DF PROTO=TCP SPT=3719 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1941.156000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=1128 DF PROTO=TCP SPT=3719 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 1967.672000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.106.164.70 DST=72.195.182.39 LEN=63 TOS=0x00 PREC=0x00 TTL=122 ID=47987 PROTO=UDP SPT=12219 DPT=4054 LEN=43
[ 1994.984000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.104.49 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=7592 PROTO=UDP SPT=15743 DPT=1026 LEN=492
[ 1994.984000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.104.49 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=7593 PROTO=UDP SPT=15743 DPT=1027 LEN=492
[ 1994.984000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.104.49 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=7594 PROTO=UDP SPT=15743 DPT=1028 LEN=492
[ 2006.616000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=25444 DF PROTO=TCP SPT=4987 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2009.556000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=25596 DF PROTO=TCP SPT=4987 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2015.668000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=25933 DF PROTO=TCP SPT=4987 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2053.960000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=28140 DF PROTO=TCP SPT=3973 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2057.064000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=28964 DF PROTO=TCP SPT=3973 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2063.040000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=30613 DF PROTO=TCP SPT=3973 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2068.232000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=6197 DF PROTO=TCP SPT=47995 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2071.184000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=6230 DF PROTO=TCP SPT=47995 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2077.196000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=76.170.120.110 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=6276 DF PROTO=TCP SPT=47995 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2097.816000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.106.164.70 DST=72.195.182.39 LEN=63 TOS=0x00 PREC=0x00 TTL=122 ID=49548 PROTO=UDP SPT=12219 DPT=4054 LEN=43
[ 2120.912000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=88.43.232.156 DST=72.195.182.39 LEN=388 TOS=0x00 PREC=0x00 TTL=58 ID=41391 PROTO=UDP SPT=30918 DPT=1026 LEN=368
[ 2128.696000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.123.61 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=53428 PROTO=UDP SPT=6061 DPT=1026 LEN=492
[ 2128.696000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.123.61 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=53429 PROTO=UDP SPT=6061 DPT=1027 LEN=492
[ 2128.696000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.123.61 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=53430 PROTO=UDP SPT=6061 DPT=1028 LEN=492
[ 2172.524000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=60644 DF PROTO=TCP SPT=4217 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2175.512000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=61398 DF PROTO=TCP SPT=4217 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2181.624000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=35994 DF PROTO=TCP SPT=1327 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2181.816000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=62991 DF PROTO=TCP SPT=4217 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2184.880000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=36238 DF PROTO=TCP SPT=1327 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2190.584000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=36728 DF PROTO=TCP SPT=1327 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2253.512000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=41431 DF PROTO=TCP SPT=1454 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2256.844000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=41694 DF PROTO=TCP SPT=1454 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2262.172000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=42166 DF PROTO=TCP SPT=1454 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2319.612000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=35859 DF PROTO=TCP SPT=4523 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2322.552000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=36540 DF PROTO=TCP SPT=4523 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2324.824000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=46669 DF PROTO=TCP SPT=1578 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2327.708000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=46872 DF PROTO=TCP SPT=1578 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2328.588000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=211.21.137.190 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=38262 DF PROTO=TCP SPT=4523 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2333.624000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=47299 DF PROTO=TCP SPT=1578 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2433.872000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=54051 DF PROTO=TCP SPT=1761 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2436.636000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=54196 DF PROTO=TCP SPT=1761 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2439.816000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.1.68.152 DST=72.195.182.39 LEN=59 TOS=0x00 PREC=0x00 TTL=116 ID=40292 PROTO=UDP SPT=39663 DPT=19789 LEN=39
[ 2443.140000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=68.6.233.35 DST=72.195.182.39 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=54620 DF PROTO=TCP SPT=1761 DPT=31252 WINDOW=65535 RES=0x00 SYN URGP=0
[ 2503.384000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.118.10 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=33377 PROTO=UDP SPT=27408 DPT=1027 LEN=492
[ 2503.384000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.118.10 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=33378 PROTO=UDP SPT=27408 DPT=1028 LEN=492
[ 2503.388000] Inbound IN=eth0 OUT= MAC=00:10:95:d5:00:ce:00:12:d9:54:9d:37:08:00 SRC=24.64.118.10 DST=72.195.182.39 LEN=512 TOS=0x00 PREC=0x00 TTL=73 ID=33376 PROTO=UDP SPT=27408 DPT=1026 LEN=492

---

