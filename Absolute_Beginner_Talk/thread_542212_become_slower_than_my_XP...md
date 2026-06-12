---
title: "become slower than my XP.."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-03
recently, in last few weeks, my boot of ubuntu takes a LOT longer and longer to load.
it used to be few secomnds, but it now slower than my XP!?

programs freeze more often, and startup slower.
amarok starts slow and freezes.
FF freezes.

any ideas why!?

im bafled!

---

### Post by Steveway on 2007-09-03
Tell us your Hardware-specs and post the output of dmesg.

---

### Post by medya on 2007-09-03
have u installed right graphic card driver ?
make sure  the partition which ubuntu is on it , is not FULL.

---

### Post by skymera on 2007-09-03
Intel core 2 duo - 1.86ghz
1gb RAM
Dual Boot
160GB HD

dmesg...long

```

[   20.747086] SMP alternatives: switching to SMP code
[   20.747150] Booting processor 1/1 eip 3000
[   20.757499] Initializing CPU#1
[   20.835617] Calibrating delay using timer specific routine.. 3724.10 BogoMIPS (lpj=7448209)
[   20.835622] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   20.835627] monitor/mwait feature present.
[   20.835630] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.835631] CPU: L2 cache: 2048K
[   20.835633] CPU: Physical Processor ID: 0
[   20.835634] CPU: Processor Core ID: 1
[   20.835636] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   20.836039] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   20.836067] Total of 2 processors activated (7450.94 BogoMIPS).
[   20.836210] ENABLING IO-APIC IRQs
[   20.836379] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.983364] checking TSC synchronization across 2 CPUs: passed.
[    0.003993] Brought up 2 CPUs
[    0.143762] migration_cost=62
[    0.143998] Dell E520 series board detected. Selecting BIOS-method for reboots.
[    0.144008] Booting paravirtualized kernel on bare hardware
[    0.144072] Time: 21:19:06  Date: 08/03/107
[    0.144097] NET: Registered protocol family 16
[    0.144168] EISA bus registered
[    0.144176] ACPI: bus type pci registered
[    0.178261] PCI: PCI BIOS revision 2.10 entry at 0xfb7fd, last bus=3
[    0.178265] PCI: Using configuration type 1
[    0.178268] Setting up standard PCI resources
[    0.263032] ACPI: Interpreter enabled
[    0.263036] ACPI: Using IOAPIC for interrupt routing
[    0.268786] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.268796] PCI: Probing PCI hardware (bus 00)
[    0.268811] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.279006] Boot video device is 0000:00:02.0
[    0.279557] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.279563] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.279890] PCI: Transparent bridge - 0000:00:1e.0
[    0.279931] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.078104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    2.089507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    2.111374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    2.194825] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    2.196568] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    2.198309] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    2.200057] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    2.201796] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    2.203558] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    2.205298] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    2.207039] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    2.209527] Linux Plug and Play Support v0.97 (c) Adam Belay
[    2.209540] pnp: PnP ACPI init
[    2.268039] pnp: PnP ACPI: found 9 devices
[    2.268045] PnPBIOS: Disabled by ACPI PNP
[    2.268084] PCI: Using ACPI for IRQ routing
[    2.268089] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    2.277304] NET: Registered protocol family 8
[    2.277307] NET: Registered protocol family 20
[    2.296119] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[    2.296124] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[    2.296128] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[    2.296138] pnp: 00:07: ioport range 0x100-0x1fe has been reserved
[    2.296142] pnp: 00:07: ioport range 0x200-0x277 has been reserved
[    2.296146] pnp: 00:07: ioport range 0x280-0x2e7 has been reserved
[    2.296149] pnp: 00:07: ioport range 0x2e8-0x2ef has been reserved
[    2.296153] pnp: 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    2.296156] pnp: 00:07: ioport range 0x2f8-0x2ff has been reserved
[    2.296160] pnp: 00:07: ioport range 0x300-0x377 has been reserved
[    2.296164] pnp: 00:07: ioport range 0x380-0x3bb has been reserved
[    2.296407] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    2.296412] PCI: Bridge: 0000:00:01.0
[    2.296415]   IO window: disabled.
[    2.296419]   MEM window: dfc00000-dfcfffff
[    2.296423]   PREFETCH window: disabled.
[    2.296427] PCI: Bridge: 0000:00:1c.0
[    2.296429]   IO window: disabled.
[    2.296435]   MEM window: dfb00000-dfbfffff
[    2.296439]   PREFETCH window: disabled.
[    2.296444] PCI: Bridge: 0000:00:1e.0
[    2.296446]   IO window: disabled.
[    2.296452]   MEM window: dfa00000-dfafffff
[    2.296456]   PREFETCH window: disabled.
[    2.296470] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.296477] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    2.296491] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.296498] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.296507] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    2.296529] NET: Registered protocol family 2
[    2.344239] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.344335] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.344739] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.344940] TCP: Hash tables configured (established 131072 bind 65536)
[    2.344944] TCP reno registered
[    2.360377] checking if image is initramfs... it is
[    2.921307] Freeing initrd memory: 6779k freed
[    2.921466] Simple Boot Flag at 0x7a set to 0x1
[    2.921872] audit: initializing netlink socket (disabled)
[    2.921890] audit(1188854348.744:1): initialized
[    2.921976] highmem bounce pool size: 64 pages
[    2.922049] VFS: Disk quotas dquot_6.5.1
[    2.922067] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.922112] io scheduler noop registered
[    2.922116] io scheduler anticipatory registered
[    2.922119] io scheduler deadline registered
[    2.922130] io scheduler cfq registered (default)
[    2.935563] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    2.935597] assign_interrupt_mode Found MSI capability
[    2.935603] Allocate Port Service[0000:00:01.0:pcie00]
[    2.935687] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.935735] assign_interrupt_mode Found MSI capability
[    2.935739] Allocate Port Service[0000:00:1c.0:pcie00]
[    2.935769] Allocate Port Service[0000:00:1c.0:pcie02]
[    2.935895] isapnp: Scanning for PnP cards...
[    3.288173] isapnp: No Plug & Play device found
[    3.306500] Real Time Clock Driver v1.12ac
[    3.306856] hpet_resources: 0xfed00000 is busy
[    3.306864] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    3.307351] mice: PS/2 mouse device common for all mice
[    3.307829] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    3.308024] input: Macintosh mouse button emulation as /class/input/input0
[    3.308056] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.308061] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.308266] PNP: No PS/2 controller found. Probing ports directly.
[    3.310846] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.310851] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.310951] EISA: Probing bus 0 at eisa.0
[    3.310962] Cannot allocate resource for EISA slot 2
[    3.310972] Cannot allocate resource for EISA slot 5
[    3.310975] Cannot allocate resource for EISA slot 6
[    3.310985] EISA: Detected 0 cards.
[    3.341086] TCP cubic registered
[    3.341095] NET: Registered protocol family 1
[    3.341115] Starting balanced_irq
[    3.341122] Using IPI No-Shortcut mode
[    3.341215] ACPI: (supports S0 S1 S3 S4 S5)
[    3.341257]   Magic number: 7:741:347
[    3.341332]   hash matches device pci0000:00
[    3.341505] Freeing unused kernel memory: 328k freed
[    3.342252] Time: tsc clocksource has been installed.
[    3.419333] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 7616k, total 7616k
[    3.419342] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    3.419346] vesafb: protected mode interface info at 00ff:44f0
[    3.419349] vesafb: scrolling: redraw
[    3.419352] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.464346] Console: switching to colour frame buffer device 160x64
[    3.509571] fb0: VESA VGA frame buffer device
[    4.674404] Capability LSM initialized
[    4.711350] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.711358] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    5.027117] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    5.027122] Copyright (c) 1999-2006 Intel Corporation.
[    5.027159] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 21 (level, low) -> IRQ 17
[    5.027171] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    5.037750] usbcore: registered new interface driver usbfs
[    5.037773] usbcore: registered new interface driver hub
[    5.037793] usbcore: registered new device driver usb
[    5.038464] USB Universal Host Controller Interface driver v3.0
[    5.083401] SCSI subsystem initialized
[    5.087669] libata version 2.20 loaded.
[    5.090245] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:27:14:ca
[    5.156847] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    5.156876] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.156889] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    5.156893] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.157003] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.157030] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    5.157126] usb usb1: configuration #1 chosen from 1 choice
[    5.157151] hub 1-0:1.0: USB hub found
[    5.157157] hub 1-0:1.0: 2 ports detected
[    5.259702] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[    5.259712] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    5.259715] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.259736] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.259760] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000ff00
[    5.259846] usb usb2: configuration #1 chosen from 1 choice
[    5.259878] hub 2-0:1.0: USB hub found
[    5.259884] hub 2-0:1.0: 2 ports detected
[    5.364581] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    5.364590] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.364594] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.364615] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    5.364640] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ff80
[    5.364725] usb usb3: configuration #1 chosen from 1 choice
[    5.364756] hub 3-0:1.0: USB hub found
[    5.364762] hub 3-0:1.0: 2 ports detected
[    5.469429] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[    5.469438] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.469442] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.469464] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    5.469486] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[    5.469565] usb usb4: configuration #1 chosen from 1 choice
[    5.469591] hub 4-0:1.0: USB hub found
[    5.469597] hub 4-0:1.0: 2 ports detected
[    5.574124] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    5.574133] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.574137] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.574157] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    5.574183] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[    5.574263] usb usb5: configuration #1 chosen from 1 choice
[    5.574289] hub 5-0:1.0: USB hub found
[    5.574306] hub 5-0:1.0: 2 ports detected
[    5.606159] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    5.674592] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[    5.674602] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    5.674606] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.674624] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    5.674651] ehci_hcd 0000:00:1a.7: debug port 1
[    5.674656] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    5.674663] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xdfddac00
[    5.678547] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.678622] usb usb6: configuration #1 chosen from 1 choice
[    5.678646] hub 6-0:1.0: USB hub found
[    5.678652] hub 6-0:1.0: 4 ports detected
[    5.782843] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    5.782860] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.782863] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.782887] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    5.782918] ehci_hcd 0000:00:1d.7: debug port 1
[    5.782924] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.782930] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xff980800
[    5.786819] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.786890] usb usb7: configuration #1 chosen from 1 choice
[    5.786912] hub 7-0:1.0: USB hub found
[    5.786918] hub 7-0:1.0: 6 ports detected
[    5.891758] ahci 0000:00:1f.2: version 2.1
[    5.891776] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[    6.133223] usb 2-1: device not accepting address 2, error -71
[    6.893985] ahci 0000:00:1f.2: nr_ports (6) and implemented port map (0x33) don't match
[    6.894001] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    6.894007] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x33 impl RAID mode
[    6.894011] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    6.894105] ata1: SATA max UDMA/133 cmd 0xf884c100 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.894176] ata2: SATA max UDMA/133 cmd 0xf884c180 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.894193] ata3: DUMMY
[    6.894207] ata4: DUMMY
[    6.894282] ata5: SATA max UDMA/133 cmd 0xf884c300 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.894351] ata6: SATA max UDMA/133 cmd 0xf884c380 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.894361] scsi0 : ahci
[    6.994815] usb 7-4: new high speed USB device using ehci_hcd and address 2
[    7.130229] usb 7-4: configuration #1 chosen from 1 choice
[    7.381100] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.381653] ata1.00: ata_hpa_resize 1: sectors = 312500000, hpa_sectors = 312500000
[    7.381659] ata1.00: ATA-7: WDC WD1600JS-75NCB3, 10.02E04, max UDMA/133
[    7.381662] ata1.00: 312500000 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    7.382253] ata1.00: ata_hpa_resize 1: sectors = 312500000, hpa_sectors = 312500000
[    7.382256] ata1.00: configured for UDMA/133
[    7.382265] scsi1 : ahci
[    7.498154] usbcore: registered new interface driver libusual
[    7.501683] Initializing USB Mass Storage driver...
[    7.735133] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    7.864219] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.911258] usb 5-1: configuration #1 chosen from 1 choice
[    8.023547] ata2.00: ATAPI, max UDMA/100
[    8.150087] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    8.180155] ata2.00: configured for UDMA/100
[    8.180164] scsi2 : ahci
[    8.180215] scsi3 : ahci
[    8.180246] scsi4 : ahci
[    8.318550] usb 5-2: configuration #1 chosen from 1 choice
[    8.321625] scsi6 : SCSI emulation for USB Mass Storage devices
[    8.321667] usb-storage: device found at 2
[    8.321669] usb-storage: waiting for device to settle before scanning
[    8.321691] usbcore: registered new interface driver usb-storage
[    8.321695] USB Mass Storage support registered.
[    8.321697] usbcore: registered new interface driver hiddev
[    8.492824] ata5: SATA link down (SStatus 4 SControl 300)
[    8.492843] scsi5 : ahci
[    8.561087] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    8.731885] usb 2-1: configuration #1 chosen from 1 choice
[    8.749873] input: DELL DELL USB Keyboard as /class/input/input1
[    8.749886] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.2-1
[    8.764781] input: PS/2+USB Mouse as /class/input/input2
[    8.764800] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.2-2
[    8.764811] usbcore: registered new interface driver usbhid
[    8.764814] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    8.802498] ata6: SATA link down (SStatus 4 SControl 300)
[    8.802619] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-75N 10.0 PQ: 0 ANSI: 5
[    8.817143] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H31N B109 PQ: 0 ANSI: 5
[    8.888508] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    8.888520] sda: Write Protect is off
[    8.888522] sda: Mode Sense: 00 3a 00 00
[    8.888534] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.888574] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    8.888582] sda: Write Protect is off
[    8.888583] sda: Mode Sense: 00 3a 00 00
[    8.888596] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.888599]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    8.926342] sd 0:0:0:0: Attached scsi disk sda
[    8.929421] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.929439] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    8.936857] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    8.936861] Uniform CD-ROM driver Revision: 3.20
[    8.936901] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    9.201866] Attempting manual resume
[    9.201869] swsusp: Resume From Partition 8:5
[    9.201871] PM: Checking swsusp image.
[    9.201961] PM: Resume from disk failed.
[    9.229756] kjournald starting.  Commit interval 5 seconds
[    9.229765] EXT3-fs: mounted filesystem with writeback data mode.
[   13.312535] usb-storage: device scan complete
[   13.314652] scsi 6:0:0:0: Direct-Access     HDS72808 0PLAT20          0000 PQ: 0 ANSI: 0
[   13.315753] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
[   13.316625] sdb: Write Protect is off
[   13.316627] sdb: Mode Sense: 27 00 00 00
[   13.316629] sdb: assuming drive cache: write through
[   13.317499] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
[   13.318372] sdb: Write Protect is off
[   13.318374] sdb: Mode Sense: 27 00 00 00
[   13.318376] sdb: assuming drive cache: write through
[   13.318378]  sdb: sdb1
[   13.326412] sd 6:0:0:0: Attached scsi disk sdb
[   13.326449] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   46.091736] Linux agpgart interface v0.102 (c) Dave Jones
[   46.211114] iTCO_vendor_support: vendor-support=0
[   46.269856] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   46.269922] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   46.269929] iTCO_wdt: No card detected
[   46.466480] input: PC Speaker as /class/input/input3
[   46.504634] agpgart: Detected an Intel 965G Chipset.
[   46.505119] agpgart: Detected 7676K stolen memory.
[   46.517993] agpgart: AGP aperture is 256M @ 0xc0000000
[   46.557208] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.559011] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.584340] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 23
[   46.584347] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   46.584352] RT61: Vendor = 0x1814, Product = 0x0301 
[   46.792621] Linux video capture interface: v2.00
[   46.862371] RT61: RfIcType= 3
[   46.925049] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   47.464258] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   47.464272] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   47.607116] usbcore: registered new interface driver gspca
[   47.607121] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   48.254929] fuse init (API version 7.8)
[   48.356530] lp: driver loaded but no devices found
[   48.600879] Adding 2048248k swap on /dev/disk/by-uuid/a5fe7f21-7175-487e-a32e-575469a9dbaf.  Priority:-1 extents:1 across:2048248k
[   48.704849] NET: Registered protocol family 17
[  137.125713] EXT3 FS on sda2, internal journal
[  138.024778] kjournald starting.  Commit interval 5 seconds
[  138.024937] EXT3 FS on sda6, internal journal
[  138.024941] EXT3-fs: mounted filesystem with ordered data mode.
[  138.567233] NET: Registered protocol family 10
[  138.567330] lo: Disabled Privacy Extensions
[  143.967552] Netfilter messages via NETLINK v0.30.
[  143.973644] nf_conntrack version 0.5.0 (8114 buckets, 64912 max)
[  144.113121] ip_tables: (C) 2000-2006 Netfilter Core Team
[  146.935037] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  146.935824] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  147.116819] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=266 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=246 
[  147.370709] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=266 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=246 
[  147.625066] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=266 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=246 
[  147.823038] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=248 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=228 
[  147.903063] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=189 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=169 
[  148.157294] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=189 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=169 
[  148.410766] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=189 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=169 
[  148.611774] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=278 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=258 
[  148.847494] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[  149.497923] [drm] Initialized drm 1.1.0 20060810
[  149.524512] ra1: no IPv6 routers present
[  149.531064] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  149.531250] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  149.532395] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[  149.637304] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=278 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=258 
[  150.870194] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=248 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=228 
[  151.660032] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=278 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=258 
[  156.412303] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[  156.662723] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[  156.912963] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[  157.110860] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[  158.323660] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[  160.536055] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[  288.970807] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[  289.966363] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[  291.966016] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[ 1363.882614] usb 6-4: new high speed USB device using ehci_hcd and address 3
[ 1364.016492] usb 6-4: configuration #1 chosen from 1 choice
[ 1364.017316] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1364.017368] usb-storage: device found at 3
[ 1364.017369] usb-storage: waiting for device to settle before scanning
[ 1369.007075] usb-storage: device scan complete
[ 1369.007577] scsi 7:0:0:0: Direct-Access     Samsung  YP-U2            0100 PQ: 0 ANSI: 4
[ 1369.009051] SCSI device sdc: 254592 2048-byte hdwr sectors (521 MB)
[ 1369.009675] sdc: Write Protect is off
[ 1369.009677] sdc: Mode Sense: 3e 00 00 00
[ 1369.009679] sdc: assuming drive cache: write through
[ 1369.011297] SCSI device sdc: 254592 2048-byte hdwr sectors (521 MB)
[ 1369.011920] sdc: Write Protect is off
[ 1369.011923] sdc: Mode Sense: 3e 00 00 00
[ 1369.011925] sdc: assuming drive cache: write through
[ 1369.011929]  sdc: sdc1
[ 1369.013321] sd 7:0:0:0: Attached scsi removable disk sdc
[ 1369.013361] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 1383.000826] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1385.099640] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=62 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=42 
[ 1386.101135] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=62 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=42 
[ 1509.835411] usb 6-4: USB disconnect, address 3
[ 3829.778986] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[ 3832.469450] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[ 3842.861960] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[ 3843.111725] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[ 3843.361563] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=170 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=150 
[ 3843.562261] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[ 3844.766930] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[ 3846.971554] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=259 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=239 
[ 4559.169911] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[ 4560.169858] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[ 4562.169541] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
scott@scott-desktop:~$ 

```

i have the standard intel driver..
xorg-video-intel

and its no where near full

---

### Post by Steveway on 2007-09-03
> [   48.704849] NET: Registered protocol family 17
[  137.125713] EXT3 FS on sda2, internal journal
That is a big jump.
Something seems to be wrong with your disk.
Maybe someone more knowledgeable in this kind of things can help you.
> [  291.966016] IN=ra1 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=72 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=52 
[ 1363.882614] usb 6-4: new high speed USB device using ehci_hcd and address 3
I assume that you plugged in some usb-device some time after booting.

---

### Post by skymera on 2007-09-03
probably, i had my USB in before booting.

so what is wrong?
can it be fixed!?

---

### Post by skymera on 2007-09-03
this awqward silence isnt very reassuring =P

---

### Post by skymera on 2007-09-03
anyone tell me if something is actually wrong?
so i can at least google it...

---

