---
title: "Boot problem- comp freezes after login (dmesg posted)"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by tomsa on 2007-11-17
I don't know why this happens, but if I shut off my computer- when I restart it it hangs up after the login screen.  It makes it to the plain tan screen before loading the desktop, my mouse pointer freezes, and the lights on my keyboard begin to flash.  I seem to be able to log in and use my machine after I restart it 7 or 8 times though.  The last time I attempted to login before the one that worked (the session that I am in now writing this post) my screen went from the blank tan screen  to what looked like the terminal, but I couldn't type anything in it or move the cursor at all.  The last line of text in that terminal-looking screen was:

[  216.136000]Fixing recursive fault but reboot is needed!

    That gave me some hope, so I kept restarting to try and get it to boot!  Now granted, this is an ooooold 8oo Mhz Athlon processor with about 384 mb RAM, but it should not be doing this, right? This is the second time I have tried to install Ubuntu (gutsy)on this machine and I am having the same problem I had the last time!  It's kind of annoying, because once it's up and running- it's great!  I really just want to be able to leave the microsoft stuff behind!  I have posted the results from a dmesg command below.  If you can help it would be greatly appreciated since I'm a pretty serious linux Noob and I have absolutely no idea what to do about this!!!

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
[    0.000000] Kernel command line: root=UUID=d99e676c-3dc2-44ea-adc4-fb9e2d7de764 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0130d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 800.064 MHz processor.
[   19.063575] Console: colour VGA+ 80x25
[   19.064458] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.065278] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.094365] Memory: 377868k/393200k available (2015k kernel code, 14704k reserved, 916k data, 364k init, 0k highmem)
[   19.094392] virtual kernel memory layout:
[   19.094395]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   19.094398]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.094402]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   19.094405]     lowmem  : 0xc0000000 - 0xd7ffc000   ( 383 MB)
[   19.094409]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   19.094412]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   19.094415]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   19.094424] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.094530] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.174511] Calibrating delay using timer specific routine.. 1602.02 BogoMIPS (lpj=3204054)
[   19.174583] Security Framework v1.0.0 initialized
[   19.174599] SELinux:  Disabled at boot.
[   19.174645] Mount-cache hash table entries: 512
[   19.174980] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   19.175004] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.175011] CPU: L2 Cache: 512K (64 bytes/line)
[   19.175019] CPU: After all inits, caps: 0183f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   19.175044] Compat vDSO mapped to ffffe000.
[   19.175075] Checking 'hlt' instruction... OK.
[   19.190580] SMP alternatives: switching to UP code
[   19.191146] Freeing SMP alternatives: 11k freed
[   19.191923] Early unpacking initramfs... done
[   20.035901] ACPI: Core revision 20070126
[   20.036115] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.038388] ACPI: setting ELCR to 0200 (from 0c20)
[   20.038595] CPU0: AMD Athlon(tm) Processor stepping 02
[   20.038608] SMP motherboard not detected.
[   20.038615] Local APIC not detected. Using dummy APIC emulation.
[   20.038728] Brought up 1 CPUs
[   20.039084] Booting paravirtualized kernel on bare hardware
[   20.039219] Time: 20:36:29  Date: 10/17/107
[   20.039297] NET: Registered protocol family 16
[   20.039586] EISA bus registered
[   20.039614] ACPI: bus type pci registered
[   20.040725] PCI: PCI BIOS revision 2.10 entry at 0xf0880, last bus=1
[   20.040732] PCI: Using configuration type 1
[   20.040736] Setting up standard PCI resources
[   20.053696] ACPI: EC: Look up EC in DSDT
[   20.058309] ACPI: Interpreter enabled
[   20.058320] ACPI: (supports S0 S1 S4 S5)
[   20.058359] ACPI: Using PIC for interrupt routing
[   20.069189] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.069215] PCI: Probing PCI hardware (bus 00)
[   20.069680] PCI quirk: region e400-e4ff claimed by vt82c586 ACPI
[   20.069690] PCI quirk: region e800-e80f claimed by vt82c686 SMB
[   20.070028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.074434] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   20.074633] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   20.074801] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.074984] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   20.075222] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.075252] pnp: PnP ACPI init
[   20.075278] ACPI: bus type pnp registered
[   20.082057] pnp: PnP ACPI: found 14 devices
[   20.082065] ACPI: ACPI bus type pnp unregistered
[   20.082076] PnPBIOS: Disabled by ACPI PNP
[   20.082227] PCI: Using ACPI for IRQ routing
[   20.082237] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.084172] NET: Registered protocol family 8
[   20.084178] NET: Registered protocol family 20
[   20.084375] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   20.084385] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   20.084393] pnp: 00:00: iomem range 0x100000-0x17ffffff could not be reserved
[   20.084401] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   20.084425] pnp: 00:03: ioport range 0xe400-0xe47f has been reserved
[   20.084433] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   20.085892] Time: tsc clocksource has been installed.
[   20.115353] PCI: Bridge: 0000:00:01.0
[   20.115361]   IO window: d000-dfff
[   20.115371]   MEM window: df000000-dfefffff
[   20.115379]   PREFETCH window: dff00000-e3ffffff
[   20.115404] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.115442] NET: Registered protocol family 2
[   20.153998] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.154140] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   20.154866] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.155485] TCP: Hash tables configured (established 16384 bind 16384)
[   20.155493] TCP reno registered
[   20.166203] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   20.889017]  it is
[   21.765983] Freeing initrd memory: 7351k freed
[   21.766272] Simple Boot Flag at 0x3a set to 0x1
[   21.767164] audit: initializing netlink socket (disabled)
[   21.767201] audit(1195331790.496:1): initialized
[   21.772828] VFS: Disk quotas dquot_6.5.1
[   21.773027] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.773316] io scheduler noop registered
[   21.773323] io scheduler anticipatory registered
[   21.773329] io scheduler deadline registered
[   21.773375] io scheduler cfq registered (default)
[   21.773409] PCI: VIA PCI bridge detected. Disabling DAC.
[   21.773418] PCI: Disabling Via external APIC routing
[   21.773464] Boot video device is 0000:01:00.0
[   21.773903] isapnp: Scanning for PnP cards...
[   22.128442] isapnp: No Plug & Play device found
[   22.223470] Real Time Clock Driver v1.12ac
[   22.223721] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.223890] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.224497] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.226105] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.226767] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.229086] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.229699] input: Macintosh mouse button emulation as /class/input/input0
[   22.229948] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.230429] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.230444] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.230974] mice: PS/2 mouse device common for all mice
[   22.231293] EISA: Probing bus 0 at eisa.0
[   22.231358] EISA: Detected 0 cards.
[   22.231807] TCP cubic registered
[   22.231847] NET: Registered protocol family 1
[   22.231903] Using IPI No-Shortcut mode
[   22.232443]   Magic number: 15:12:650
[   22.232595]   hash matches device ptydf
[   22.233860] Freeing unused kernel memory: 364k freed
[   22.256333] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.818509] AppArmor: AppArmor initialized<5>audit(1195331792.496:2):  type=1505 info="AppArmor initialized" pid=1169
[   23.842302] fuse init (API version 7.8)
[   23.856383] Failure registering capabilities with primary security module.
[   23.897767] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   23.897782] ACPI: Processor [CPU0] (supports 16 throttling states)
[   25.491295] usbcore: registered new interface driver usbfs
[   25.491360] usbcore: registered new interface driver hub
[   25.491426] usbcore: registered new device driver usb
[   25.493905] USB Universal Host Controller Interface driver v3.0
[   25.494635] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   25.494645] PCI: setting IRQ 5 as level-triggered
[   25.494654] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   25.494682] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   25.495115] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   25.495159] uhci_hcd 0000:00:04.2: irq 5, io base 0x0000b400
[   25.495474] usb usb1: configuration #1 chosen from 1 choice
[   25.495550] hub 1-0:1.0: USB hub found
[   25.495571] hub 1-0:1.0: 2 ports detected
[   25.560730] SCSI subsystem initialized
[   25.575825] libata version 2.21 loaded.
[   25.598111] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   25.598144] uhci_hcd 0000:00:04.3: UHCI Host Controller
[   25.598212] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[   25.598257] uhci_hcd 0000:00:04.3: irq 5, io base 0x0000b000
[   25.598579] usb usb2: configuration #1 chosen from 1 choice
[   25.598648] hub 2-0:1.0: USB hub found
[   25.598671] hub 2-0:1.0: 2 ports detected
[   25.744158] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.744172] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.745885] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   25.745935] VP_IDE: chipset revision 16
[   25.745941] VP_IDE: not 100% native mode: will probe irqs later
[   25.745962] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:04.1
[   25.745977]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:pio
[   25.746001]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:pio
[   25.746016] Probing IDE interface ide0...
[   25.837602] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   25.984080] usb 1-1: configuration #1 chosen from 1 choice
[   25.985942] hub 1-1:1.0: USB hub found
[   25.988842] hub 1-1:1.0: 4 ports detected
[   26.079399] Floppy drive(s): fd0 is 1.44M
[   26.133163] FDC 0 is a post-1991 82077
[   26.161442] hda: WDC WD800JB-00CRA1, ATA DISK drive
[    7.240000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.244000] Time: acpi_pm clocksource has been installed.
[    7.252000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    7.412000] usb 1-2: configuration #1 chosen from 1 choice
[    7.748000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.768000] Probing IDE interface ide1...
[    7.880000] usb 1-1.4: new full speed USB device using uhci_hcd and address 4
[    8.072000] usb 1-1.4: configuration #1 chosen from 1 choice
[    8.112000] usbcore: registered new interface driver libusual
[    8.124000] Initializing USB Mass Storage driver...
[    8.136000] scsi0 : SCSI emulation for USB Mass Storage devices
[    8.140000] usbcore: registered new interface driver usb-storage
[    8.140000] USB Mass Storage support registered.
[    8.140000] usb-storage: device found at 4
[    8.140000] usb-storage: waiting for device to settle before scanning
[    8.632000] hdc: PLEXTOR CD-R PX-W4824A, ATAPI CD/DVD-ROM drive
[    8.968000] ide1 at 0x170-0x177,0x376 on irq 15
[    8.988000] hda: max request size: 128KiB
[    9.012000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(66)
[    9.012000] hda: cache flushes not supported
[    9.012000]  hda: hda1 hda2 < hda5 hda6 >
[    9.084000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[    9.084000] Uniform CD-ROM driver Revision: 3.20
[    9.480000] Attempting manual resume
[    9.480000] swsusp: Resume From Partition 3:5
[    9.480000] PM: Checking swsusp image.
[    9.480000] PM: Resume from disk failed.
[    9.528000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    9.528000] EXT3-fs: write access will be enabled during recovery.
[   10.172000] kjournald starting.  Commit interval 5 seconds
[   10.172000] EXT3-fs: recovery complete.
[   10.172000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.144000] usb-storage: device scan complete
[   13.148000] scsi 0:0:0:0: Direct-Access     WD       CR    HS-CF      3.04 PQ: 0 ANSI: 0
[   13.152000] scsi 0:0:0:1: Direct-Access     WD       CR    HS-5-IN-1  3.04 PQ: 0 ANSI: 0
[   21.768000] parport_pc: VIA 686A/8231 detected
[   21.768000] parport_pc: probing current configuration
[   21.768000] parport_pc: Current parallel port base: 0x378
[   21.768000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   21.788000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.792000] agpgart: Detected VIA Apollo Pro 133 chipset
[   21.800000] agpgart: AGP aperture is 64M @ 0xe4000000
[   21.812000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.260000] via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   22.304000] parport0: Printer, HEWLETT-PACKARD DESKJET 670C
[   22.304000] parport_pc: VIA parallel port: io=0x378, irq=7
[   23.300000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   24.140000] input: PC Speaker as /class/input/input3
[   24.740000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   24.740000] PCI: setting IRQ 10 as level-triggered
[   24.740000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.132000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   25.224000] sd 0:0:0:1: [sdb] Attached SCSI removable disk
[   25.256000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.256000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   25.412000] eth0: register 'cdc_ether' at usb-0000:00:04.2-2, CDC Ethernet Device, 00:10:95:d5:00:ce
[   25.412000] usbcore: registered new interface driver cdc_ether
[   26.284000] lp0: using parport0 (interrupt-driven).
[   26.400000] Adding 1124508k swap on /dev/hda5.  Priority:-1 extents:1 across:1124508k
[   26.844000] EXT3 FS on hda6, internal journal
[   28.924000] No dock devices found.
[   29.256000] input: Power Button (FF) as /class/input/input4
[   29.256000] ACPI: Power Button (FF) [PWRF]
[   29.296000] input: Power Button (CM) as /class/input/input5
[   29.296000] ACPI: Power Button (CM) [PWRB]
[   29.832000] powernow: No powernow capabilities detected
[   32.180000] ppdev: user-space parallel port driver
[   32.676000] audit(1195349821.153:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4608 profile="/usr/sbin/cupsd"
[   32.792000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   32.792000] apm: overridden by ACPI.
[   33.596000] Failure registering capabilities with primary security module.
[   37.888000] [drm] Initialized drm 1.1.0 20060810
[   37.900000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   37.900000] PCI: setting IRQ 11 as level-triggered
[   37.900000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   37.908000] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   37.912000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   37.912000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   37.912000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   38.292000] NET: Registered protocol family 17
[   44.256000] NET: Registered protocol family 10
[   44.256000] lo: Disabled Privacy Extensions
[   55.024000] eth0: no IPv6 routers present

---

### Post by oilchangeguy on 2007-11-17
this forum is users, helping users.  most do it on their free time. if you're needing help with your dmesg file, i'd suggest using paid support:
[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by llamakc on 2007-11-17
> **oilchangeguy said:**
> this forum is users, helping users.  most do it on their free time. if you're needing help with your dmesg file, i'd suggest using paid support:
[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

Exactly what was wrong with the OP? It was informative, included system specs, and even cut/pasted their dmesg output.

OP: you could have some bad ram. Run the memtest option from the Grub menu. When booting hit the escape key to get the Grub menu and choose 'memtest'.

---

### Post by srt4play on 2007-11-17
> **oilchangeguy said:**
> this forum is users, helping users.  most do it on their free time. if you're needing help with your dmesg file, i'd suggest using paid support:
[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)


What was the point of this post? He posted output from dmesg thinking there's a clue somewhere in there that someone may spot and offer advice from.

On topic -  nothing stands out to me but if it's a desktop I would turn off ACPI and see what happens.

---

### Post by oilchangeguy on 2007-11-17
> **llamakc said:**
> Exactly what was wrong with the OP? It was informative, included system specs, and even cut/pasted their dmesg output.

OP: you could have some bad ram. Run the memtest option from the Grub menu. When booting hit the escape key to get the Grub menu and choose 'memtest'.

nothing wrong with the post. just way to much information for non-paid support. not opposed to helping someone. but reading lines and lines of a file is a bit much to ask of non-paid support.

---

### Post by llamakc on 2007-11-17
> **oilchangeguy said:**
> nothing wrong with the post. just way to much information for non-paid support. not opposed to helping someone. but reading lines and lines of a file is a bit much to ask of non-paid support.

The forum doesn't belong to you alone, or your singular opinion.  Cut the OP some slack. They did the right thing.

I applaud the OP for being informative.

---

### Post by tomsa on 2007-11-17
> **srt4play said:**
> What was the point of this post? He posted output from dmesg thinking there's a clue somewhere in there that someone may spot and offer advice from.

On topic -  nothing stands out to me but if it's a desktop I would turn off ACPI and see what happens.
> On topic - nothing stands out to me but if it's a desktop I would turn off ACPI and see what happens.

What is ACPI?  I'm not sure about a lot of things in linux yet.  I have found something called acpid (power management) in the services settings, but I'm not sure if that is by any chance what I need to do.  I am using a desktop, btw.  If it is something I have to do at the command line, I'm going to need some guidance.  I really am pretty clueless there.  The only reason I knew posting a dmesg (thanks for your patience with that) is because I came across the info on that command and what it did by accident.  
 
I am reluctant to reboot and do the memtest in grub thing right away, because I figure that I might have to do that whole reboot my computer 7 or 8 times to log back in again.  

Oilchangeguy- sorry I overdid it, I just really was not sure what to do and I wanted to make sure I provided enough information to be useful in getting help.  I'm really clueless here.

srt4play & llmakc- thanks for the help!

Perhaps after a while I'll learn enough about this to be able to help others out as well!

---

### Post by peaceforall on 2007-11-17
Are you upgrading?  I had the same problem with an upgrade.  As soon as I did a clean install with the upgrade the problem you are talking about disappeared into dreamland.

---

### Post by niteshifter on 2007-11-18
Hi tomsa,

Ignore the noise - you did the right thing by posting dmesg, we would of asked you to, saves us *all* a step. And it's no problem to scan kernel messages (for some of us).

Now on to working toward a solution. You're going to have to restart - a few more times - no way around that. 

First off, shutdown the OS and power-off the computer and give it's insides a visual check. Check anything socket mounted, give it a gentle push to see if it's seated properly. Unplug and re-insert ribbon cables - one at a time. Do the same unplug / plug with your RAM.

Running memtest is an excellent idea as another poster suggested. I recommend more than one pass testing, let it run for a few hours - RAM failures can be sneaky.

From examining the dmesg output: There's a minor hitch in filesystem mounting (hence the cable check and RAM test requests). Another is try booting without whatever external USB storage device(s) you're using connected.

---

### Post by tomsa on 2007-11-19
Well, I eventually accepted the fact that I was going to have to restart multiple times to get what I wanted.  I disabled both acpid, and apmd as srt4ply suggested, once I found out that those are geared towards laptop power management- I figured I really didn't need them on.  So far, I have rebooted my computer 4 or 5 times with out any difficulty, barring a random screen resolution issue that seems to have fixed itself with a logout/login.  

I also did what you suggested and checked out the insides of my computer and ran memtest.  The insides looked to be intact- so no worries there.  memtest however showed something I was sort of expecting, but I don't understand.  It spit his out:

#8 modulo 20, ones & zeros 156 errors

   I suppose that means I have some RAM problems, which doesn't surprise me.  Honestly, this box is sort of a Frankenstein box I built with almost all used components about four years ago when I was less gainfuly employed than I am now- so I'm not surprised to see something wrong there.  I'm really just trying to extend it's life as long as I can to meet a few financial goals my wife and I have before I build a new machine (and I have all sorts of questions about that too, but that's for another thread).  My question is, shoud I replace my RAM, or will my computer keep running okay without a change?  and if I have to change it, how do I find out what kind it will need? (Even though this was a self- build, it was really just there while two friends helped me, so I really know nothing about what to do).  My instincts tell me that I should just go drop fifty bucks an a gig of RAM and figure out what I want to build next.  

I really should thank you all for the help- before I tried Ubuntu, I worked with Mandriva 2007 for about two months, and it was a lot more difficult getting help with that OS.  The Ubuntu community is really something impressive.  I  hope more people find it!

---

