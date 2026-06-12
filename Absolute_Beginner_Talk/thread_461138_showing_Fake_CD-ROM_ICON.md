---
title: "showing Fake CD-ROM ICON"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-01
when i saw my computer , here ubuntu showing me two Extra CD-ROM ICON which is not added in my system, i have only DVD-RW and CD-RW and only floopy drive. i have added the screenshot of my computer for easy reference, here you can see CD-ROM 1 and CD-ROM 2 which is 100% Fake there is no CD-ROM in my system installed. how to fix this problem ???

---

### Post by rfurman24 on 2007-06-01
My Ubuntu install shows the same. I have one dvd rom and one dvd writer. I am not new to linux but new to Ubuntu. Are these icons normal?

---

### Post by Inxsible on 2007-06-01
Tushar,
 
you must have made the recent updates for the linux kernel. These updates installed the 2.6.20-16 kernel. The older one was 2.6.20-15.
 
The change between the two is that -15 identified the drives as /dev/scd*
whereas -16 identifies them as /dev/hd* -- This is strange since this is reserved for hard disk drives. (or so i think because I too now have devices at /dev/hda whereas in -15 i never had any ! )
 
if you do a dmesg, you will notice this. 
 
You can keep using your older kernel, if you haven't uninstalled it and i think you wont see the phantom drives there. 
I have read somewhere that you can change the fstab files to point to each pand every device of yours i.e if you have a DVD and CD RW then one for each etc. but I havent tried that, so i dont know if it works
 
:(

---

### Post by ferronica on 2007-06-02
If there is no problem having old and new kernal then no problem, and if i wanna to remove old kernel, what the process

---

### Post by ferronica on 2007-06-02
Here is my "DMESG" output --->

[   20.958587] SELinux:  Disabled at boot.
[   20.958604] Mount-cache hash table entries: 512
[   20.958760] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   20.958769] monitor/mwait feature present.
[   20.958771] using mwait in idle threads.
[   20.958778] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.958781] CPU: L2 cache: 1024K
[   20.958784] CPU: Physical Processor ID: 0
[   20.958786] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   20.958799] Compat vDSO mapped to ffffe000.
[   20.958803] Remapping vsyscall page to ffffe000
[   20.958819] Checking 'hlt' instruction... OK.
[   20.974620] SMP alternatives: switching to UP code
[   20.975109] Early unpacking initramfs... done
[   21.245467] ACPI: Core revision 20060707
[   21.250504] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   21.254157] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   21.254178] SMP alternatives: switching to SMP code
[   21.254315] Booting processor 1/1 eip 3000
[   21.264638] Initializing CPU#1
[   21.341524] Calibrating delay using timer specific routine.. 5990.26 BogoMIPS (lpj=11980520)
[   21.341534] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   21.341541] monitor/mwait feature present.
[   21.341547] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   21.341550] CPU: L2 cache: 1024K
[   21.341553] CPU: Physical Processor ID: 0
[   21.341555] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   21.341829] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   21.341871] Total of 2 processors activated (11984.60 BogoMIPS).
[   21.342000] ENABLING IO-APIC IRQs
[   21.342178] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.489147] checking TSC synchronization across 2 CPUs: passed.
[    0.003986] Brought up 2 CPUs
[    0.036736] migration_cost=15
[    0.037024] Booting paravirtualized kernel on bare hardware
[    0.037106] Time: 16:52:59  Date: 05/02/107
[    0.037136] NET: Registered protocol family 16
[    0.037230] EISA bus registered
[    0.037236] ACPI: bus type pci registered
[    0.061072] PCI: PCI BIOS revision 2.10 entry at 0xfb800, last bus=2
[    0.061075] PCI: Using configuration type 1
[    0.061077] Setting up standard PCI resources
[    0.083489] ACPI: Interpreter enabled
[    0.083492] ACPI: Using IOAPIC for interrupt routing
[    0.084144] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.084149] PCI: Probing PCI hardware (bus 00)
[    0.084778] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.084783] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.085000] Boot video device is 0000:01:00.0
[    0.085299] PCI: Transparent bridge - 0000:00:1e.0
[    0.085326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.092347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.096254] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.096516] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.096775] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.097033] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.097296] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.097556] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.097811] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.098070] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.098323] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.098336] pnp: PnP ACPI init
[    0.102062] pnp: PnP ACPI: found 15 devices
[    0.102068] PnPBIOS: Disabled by ACPI PNP
[    0.102124] PCI: Using ACPI for IRQ routing
[    0.102128] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.118052] NET: Registered protocol family 8
[    0.118055] NET: Registered protocol family 20
[    0.118460] pnp: 00:0c: ioport range 0x400-0x4bf could not be reserved
[    0.118798] PCI: Bridge: 0000:00:01.0
[    0.118801]   IO window: disabled.
[    0.118805]   MEM window: f8000000-f9ffffff
[    0.118810]   PREFETCH window: f0000000-f7ffffff
[    0.118816] PCI: Bridge: 0000:00:1e.0
[    0.118820]   IO window: a000-afff
[    0.118825]   MEM window: fa000000-fa0fffff
[    0.118829]   PREFETCH window: disabled.
[    0.118848] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.118881] NET: Registered protocol family 2
[    0.159638] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.159807] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.160425] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.160882] TCP: Hash tables configured (established 131072 bind 65536)
[    0.160886] TCP reno registered
[    0.171718] checking if image is initramfs... it is
[    0.706613] Freeing initrd memory: 6769k freed
[    0.706817] Simple Boot Flag at 0x37 set to 0x1
[    0.707268] audit: initializing netlink socket (disabled)
[    0.707288] audit(1180803179.452:1): initialized
[    0.707393] highmem bounce pool size: 64 pages
[    0.707484] VFS: Disk quotas dquot_6.5.1
[    0.707504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.707561] io scheduler noop registered
[    0.707565] io scheduler anticipatory registered
[    0.707567] io scheduler deadline registered
[    0.707580] io scheduler cfq registered (default)
[    0.707877] isapnp: Scanning for PnP cards...
[    1.058886] isapnp: No Plug & Play device found
[    1.085667] Real Time Clock Driver v1.12ac
[    1.085726] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.085837] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.085974] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.086542] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.086782] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.087041] mice: PS/2 mouse device common for all mice
[    1.087691] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.087853] input: Macintosh mouse button emulation as /class/input/input0
[    1.087893] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.087897] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.088142] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.090401] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.090408] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.090531] EISA: Probing bus 0 at eisa.0
[    1.090570] EISA: Detected 0 cards.
[    1.120580] TCP cubic registered
[    1.120590] NET: Registered protocol family 1
[    1.120615] Starting balanced_irq
[    1.120623] Using IPI No-Shortcut mode
[    1.120700] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.120769] ACPI: (supports S0 S1 S4 S5)
[    1.120822]   Magic number: 11:185:893
[    1.120911]   hash matches device ptyy3
[    1.121044] Time: tsc clocksource has been installed.
[    1.121201] Freeing unused kernel memory: 328k freed
[    2.345857] Capability LSM initialized
[    2.383728] ACPI: Fan [FAN] (on)
[    2.389403] ACPI: Thermal Zone [THRM] (58 C)
[    2.845720] usbcore: registered new interface driver usbfs
[    2.845752] usbcore: registered new interface driver hub
[    2.970865] usbcore: registered new device driver usb
[    2.971178] SCSI subsystem initialized
[    2.979953] libata version 2.20 loaded.
[    2.982255] ata_piix 0000:00:1f.2: version 2.10ac1
[    2.982262] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    2.982293] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16
[    2.982316] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    2.982397] ata1: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001c402 bmdma 0x0001d000 irq 16
[    2.982440] ata2: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001cc02 bmdma 0x0001d008 irq 16
[    2.982459] scsi0 : ata_piix
[    3.055267] USB Universal Host Controller Interface driver v3.0
[    3.064835] ieee1394: Initialized config rom entry `ip1394'
[    3.074127] 8139too Fast Ethernet driver 0.9.28
[    3.091590] FDC 0 is a post-1991 82077
[    3.195268] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.195276] ata1.00: ATA-7: ST3808110AS, 3.AAE, max UDMA/133
[    3.195279] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.261723] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.261728] ata1.00: configured for UDMA/133
[    3.261740] scsi1 : ata_piix
[    3.481618] ata2.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.481624] ata2.00: ATA-7: ST3200827AS, 3.AAE, max UDMA/133
[    3.481627] ata2.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.631140] ata2.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.631146] ata2.00: configured for UDMA/133
[    3.631284] scsi 0:0:0:0: Direct-Access     ATA      ST3808110AS      3.AA PQ: 0 ANSI: 5
[    3.631676] scsi 1:0:0:0: Direct-Access     ATA      ST3200827AS      3.AA PQ: 0 ANSI: 5
[    3.632026] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[    3.632043] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.632049] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.632341] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.632375] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000bc00
[    3.632660] usb usb1: configuration #1 chosen from 1 choice
[    3.632704] hub 1-0:1.0: USB hub found
[    3.632714] hub 1-0:1.0: 2 ports detected
[    3.738250] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    3.738265] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.738270] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.738305] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.738333] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000b000
[    3.738476] usb usb2: configuration #1 chosen from 1 choice
[    3.738521] hub 2-0:1.0: USB hub found
[    3.738533] hub 2-0:1.0: 2 ports detected
[    3.846661] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[    3.846677] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.846683] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.846895] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.846925] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000b400
[    3.847194] usb usb3: configuration #1 chosen from 1 choice
[    3.847236] hub 3-0:1.0: USB hub found
[    3.847247] hub 3-0:1.0: 2 ports detected
[    3.953666] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 17
[    3.953680] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.953686] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.953718] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.953744] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000b800
[    3.953877] usb usb4: configuration #1 chosen from 1 choice
[    3.953926] hub 4-0:1.0: USB hub found
[    3.953937] hub 4-0:1.0: 2 ports detected
[    4.064821] ICH5: IDE controller at PCI slot 0000:00:1f.1
[    4.064837] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 16
[    4.064851] ICH5: chipset revision 2
[    4.064854] ICH5: not 100% native mode: will probe irqs later
[    4.064870]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[    4.064894]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[    4.064909] Probing IDE interface ide0...
[    4.196911] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.356622] hda: ST340014A, ATA DISK drive
[    5.031241] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.034879] Probing IDE interface ide1...
[    5.772882] hdc: SONY DVD RW DW-Q120A, ATAPI CD/DVD-ROM drive
[    6.558805] hdd: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
[    6.618978] ide1 at 0x170-0x177,0x376 on irq 15
[    6.632099] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 19 (level, low) -> IRQ 18
[    6.685066] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fa001000-fa0017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.696346] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 23 (level, low) -> IRQ 19
[    6.696716] eth0: RealTek RTL8139 at 0xf8846000, 00:01:6c:38:f2:e9, IRQ 19
[    6.696721] eth0:  Identified 8139 chip type 'RTL-8101'
[    6.700569] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.700747] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[    6.700766] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.700773] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.700836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.700884] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    6.700902] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfa100000
[    6.704790] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.704938] usb usb5: configuration #1 chosen from 1 choice
[    6.704981] hub 5-0:1.0: USB hub found
[    6.704993] hub 5-0:1.0: 8 ports detected
[    6.711934] usb 3-2: configuration #1 chosen from 1 choice
[    6.715801] usb 3-2: can't set config #1, error -71
[    6.715883] usb 3-2: USB disconnect, address 2
[    6.727670] hda: max request size: 512KiB
[    6.730197] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.730225] Uniform CD-ROM driver Revision: 3.20
[    6.730518] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.730623] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.730702] hda: cache flushes supported
[    6.730748]  hda:<5>sda: Write Protect is off
[    6.731330] sda: Mode Sense: 00 3a 00 00
[    6.731959] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.732039] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.732059] sda: Write Protect is off
[    6.732062] sda: Mode Sense: 00 3a 00 00
[    6.732090] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.732096]  sda:<6>hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.750381]  sda1
[    6.750469] sd 0:0:0:0: Attached scsi disk sda
[    6.751064] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[    6.751084] sdb: Write Protect is off
[    6.751087] sdb: Mode Sense: 00 3a 00 00
[    6.751114] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.751197]  hda1 hda2 <<5>SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[    6.751301] sdb: Write Protect is off
[    6.751305] sdb: Mode Sense: 00 3a 00 00
[    6.751337] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.751342]  sdb: sdb1
[    6.770317] sd 1:0:0:0: Attached scsi disk sdb
[    6.770452]  hda5 >
[    6.777372] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.777854] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    6.982088] Attempting manual resume
[    6.982092] swsusp: Resume From Partition 3:5
[    6.982094] PM: Checking swsusp image.
[    6.982499] PM: Resume from disk failed.
[    6.999649] kjournald starting.  Commit interval 5 seconds
[    6.999682] EXT3-fs: mounted filesystem with ordered data mode.
[    7.464279] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    7.971153] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00601d0000008517]
[   16.905949] eth1: link down
[   17.622789] usb 3-2: configuration #1 chosen from 1 choice
[   18.119741] Linux agpgart interface v0.102 (c) Dave Jones
[   18.122305] agpgart: Detected an Intel 865 Chipset.
[   18.128248] agpgart: AGP aperture is 128M @ 0xe8000000
[   18.467909] input: PC Speaker as /class/input/input2
[   18.506952] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.509465] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.582476] logips2pp: Detected unknown logitech mouse model 20
[   18.597164] NET: Registered protocol family 17
[   18.643031] iTCO_vendor_support: vendor-support=0
[   18.705997] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.780558] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   18.924395] parport: PnPBIOS parport detected.
[   18.924443] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   19.036864] Linux video capture interface: v2.00
[   19.052233] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   19.055039] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   19.055094] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.193106] nvidia: module license 'NVIDIA' taints kernel.
[   19.460307] Bluetooth: Core ver 2.11
[   19.478393] NET: Registered protocol family 31
[   19.478398] Bluetooth: HCI device and connection manager initialized
[   19.478403] Bluetooth: HCI socket layer initialized
[   19.494815] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   19.495052] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   19.545463] saa7130/34: v4l2 driver version 0.2.14 loaded
[   19.545542] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 20
[   19.545552] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xfa000000
[   19.545558] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[   19.545567] saa7134[0]: board init: gpio is 6000
[   19.623001] intel_rng: FWH not detected
[   19.649818] Bluetooth: HCI USB driver ver 2.9
[   19.703969] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   19.704002] saa7134[0]: i2c eeprom 10: 00 f0 00 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.704030] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 1c ff ff ff ff
[   19.704055] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.704080] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[   19.704106] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.704128] saa7134[0]: i2c eeprom 60: 0c 22 17 4d 03 0d 53 b0 ff ff ff ff ff ff ff ff
[   19.704152] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff 74 78 ff ff ff ff ff ff
[   19.730305] usb 3-2: USB disconnect, address 3
[   19.730319] hci_usb: probe of 3-2:1.0 failed with error -84
[   19.731952] usbcore: registered new interface driver hci_usb
[   19.799704] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   19.799777] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   19.823634] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[   19.823641] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   19.843590] usb 3-2: new full speed USB device using uhci_hcd and address 4
[   19.847569] tuner 0-0060: microtune: companycode=3cbf part=42 rev=2f
[   19.895437] tuner 0-0060: microtune MT2050 found, OK
[   19.919385] tuner 0-0060: microtune: companycode=3cbf part=42 rev=2f
[   19.967249] tuner 0-0060: microtune MT2050 found, OK
[   19.979621] saa7134[0]: registered device video0 [v4l2]
[   19.979675] saa7134[0]: registered device vbi0
[   20.002266] saa7134 ALSA driver for DMA sound loaded
[   20.002304] saa7134[0]/alsa: saa7134[0] at 0xfa000000 irq 20 registered as card -2
[   20.096785] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 16
[   20.100462] Audigy2 value: Special config.
[   20.292153] fuse init (API version 7.8)
[   20.327145] lp0: using parport0 (interrupt-driven).
[   20.363314] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 21
[   20.564378] Adding 1646620k swap on /dev/disk/by-uuid/370baa1c-f12d-4126-b663-3143b0ff3fc4.  Priority:-1 extents:1 across:1646620k
[   20.683536] EXT3 FS on hda1, internal journal
[   24.833941] PPP generic driver version 2.4.2
[   24.865758] NET: Registered protocol family 10
[   24.865892] lo: Disabled Privacy Extensions
[   25.523775] input: Power Button (FF) as /class/input/input4
[   25.523815] ACPI: Power Button (FF) [PWRF]
[   25.523868] input: Power Button (CM) as /class/input/input5
[   25.523895] ACPI: Power Button (CM) [PWRB]
[   25.523950] input: Sleep Button (CM) as /class/input/input6
[   25.523983] ACPI: Sleep Button (CM) [SLPB]
[   25.661413] ibm_acpi: ec object not found
[   25.708659] Using specific hotkey driver
[   25.758606] No dock devices found.
[   25.899828] pcc_acpi: loading...
[   30.002450] usb 3-2: configuration #1 chosen from 1 choice
[   31.758886] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   31.758912] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   31.758947] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   32.441763] ppdev: user-space parallel port driver
[   33.249052] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   33.249058] apm: disabled - APM is not SMP safe.
[   33.427059] Bluetooth: L2CAP ver 2.8
[   33.427066] Bluetooth: L2CAP socket layer initialized
[   33.554672] Bluetooth: RFCOMM socket layer initialized
[   33.554690] Bluetooth: RFCOMM TTY layer initialized
[   33.554694] Bluetooth: RFCOMM ver 1.8
[   89.871320] NET: Registered protocol family 24
[   90.480310] ip_tables: (C) 2000-2006 Netfilter Core Team
tushar@tushar-desktop:~$ 
Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587132] Oops: 0002 [#1]

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587134] SMP 

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587285] CPU:    1

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587286] EIP:    0060:[add_wait_queue+35/80]    Tainted: P      VLI

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587288] EFLAGS: 00210046   (2.6.20-16-generic #2)

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587298] EIP is at add_wait_queue+0x23/0x50

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587302] eax: 00200246   ebx: f6d37d10   ecx: ffc7121c   edx: f6d37d1c

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587307] esi: dfc71218   edi: dfc7121c   ebp: f6d37c54   esp: f6d37c08

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587311] ds: 007b   es: 007b   ss: 0068

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587316] Process gnome-power-man (pid: 6002, ti=f6d36000 task=f6d5ba90 task.ti=f6d36000)

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587319] Stack: f6d21c80 f6d37c54 f6d20900 c02e15b4 c0303ee0 f6d37ecc c027772c 00000000 

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587332]        c01831d4 f6d37c54 f6d37fac 081a0b58 081a0ba0 00000000 f6d37e94 f6d37e94 

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587343]        00000009 f6d37ee4 f6d37e94 c0183ed0 00000000 00000000 00000007 f6d1f8c0 

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587354] Call Trace:

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587372]  [unix_poll+20/160] unix_poll+0x14/0xa0

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587390]  [sock_poll+12/16] sock_poll+0xc/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587401]  [do_sys_poll+420/992] do_sys_poll+0x1a4/0x3e0

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587452]  [__pollwait+0/240] __pollwait+0x0/0xf0

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587485]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587511]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587536]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587561]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587585]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587610]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587634]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587680]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587683]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587708]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587742]  [__wake_up+56/80] __wake_up+0x38/0x50

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587775]  [unix_write_space+128/144] unix_write_space+0x80/0x90

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587790]  [sock_wfree+56/64] sock_wfree+0x38/0x40

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587798]  [__kfree_skb+74/288] __kfree_skb+0x4a/0x120

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587824]  [unix_stream_recvmsg+558/1376] unix_stream_recvmsg+0x22e/0x560

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587828]  [__wake_up+56/80] __wake_up+0x38/0x50

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.587939]  [sock_aio_read+287/304] sock_aio_read+0x11f/0x130

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588088]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588120]  [unix_ioctl+151/208] unix_ioctl+0x97/0xd0

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588139]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588146]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588161]  [do_ioctl+43/144] do_ioctl+0x2b/0x90

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588164]  [read_tsc+6/16] read_tsc+0x6/0x10

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588169]  [do_gettimeofday+54/240] do_gettimeofday+0x36/0xf0

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588198]  [copy_to_user+41/80] copy_to_user+0x29/0x50

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588221]  [sys_poll+43/64] sys_poll+0x2b/0x40

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588232]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588268]  [xfrm_state_find+1011/1392] xfrm_state_find+0x3f3/0x570

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588300]  =======================

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588302] Code: 00 8d bc 27 00 00 00 00 83 ec 0c 89 1c 24 89 d3 89 74 24 04 89 c6 89 7c 24 08 8d 7e 04 83 22 fe e8 d3 37 1b 00 8b 4e 04 8d 53 0c <89> 51 04 89 4b 0c 89 7a 04 89 56 04 89 c2 8b 1c 24 89 f0 8b 7c 

Message from syslogd@tushar-desktop at Sat Jun  2 23:02:16 2007 ...
tushar-desktop kernel: [ 2351.588345] EIP: [add_wait_queue+35/80] add_wait_queue+0x23/0x50 SS:ESP 0068:f6d37c08

---

### Post by drowner on 2007-06-02
Rofl

---

### Post by Inxsible on 2007-06-02
> **drowner said:**
> Rofl

Why Rofl ??? :confused:

---

### Post by Inxsible on 2007-06-02
> [ 5.034879] Probing IDE interface ide1...
[ 5.772882] [COLOR="#ff0000"]hdc: SONY DVD RW DW-Q120A, ATAPI CD/DVD-ROM drive[/COLOR]
[ 6.558805] [COLOR="#ff0000"]hdd: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive[/COLOR]
[ 6.618978] ide1 at 0x170-0x177,0x376 on irq 15
[ 6.632099] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 19 (level, low) -> IRQ 18
[ 6.685066] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18] MMIO=[fa001000-fa0017ff] Max Packet=[2048] IR/IT contexts=[8/8]
[ 6.696346] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 23 (level, low) -> IRQ 19
[ 6.696716] eth0: RealTek RTL8139 at 0xf8846000, 00:01:6c:38:f2:e9, IRQ 19
[ 6.696721] eth0: Identified 8139 chip type 'RTL-8101'
[ 6.700569] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 6.700747] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[ 6.700766] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 6.700773] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 6.700836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[ 6.700884] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[ 6.700902] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfa100000
[ 6.704790] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 6.704938] usb usb5: configuration #1 chosen from 1 choice
[ 6.704981] hub 5-0:1.0: USB hub found
[ 6.704993] hub 5-0:1.0: 8 ports detected
[ 6.711934] usb 3-2: configuration #1 chosen from 1 choice
[ 6.715801] usb 3-2: can't set config #1, error -71
[ 6.715883] usb 3-2: USB disconnect, address 2
[ 6.727670] hda: max request size: 512KiB
[ 6.730197][COLOR="#ff0000"] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)[/COLOR]
[ 6.730225] Uniform CD-ROM driver Revision: 3.20
[ 6.730518] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[ 6.730623] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 6.730702] hda: cache flushes supported
[ 6.730748] hda:<5>sda: Write Protect is off
[ 6.731330] sda: Mode Sense: 00 3a 00 00
[ 6.731959] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6.732039] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 6.732059] sda: Write Protect is off
[ 6.732062] sda: Mode Sense: 00 3a 00 00
[ 6.732090] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6.732096] [COLOR="Red"]sda:<6>hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)[/COLOR]

So now because of the -16 kernel update, you are seeing CD Devices at 4 places -- two of which like you said are "fake" or rather phantom devices. Two of them are due to kernel 15 and two are for kernel 16. I do not exactly know what changed in the way the two kernels recognize cd drives.

Just keep using the -15 version and you should be ok. 

OR :
Warning : do this at your own risk
1) Uninstall kernel -15 so you will have only two cd drives -- no phantoms

Yet another OR
1) Uninstall kernel -16 -- same thing again, two drives -- no phantoms 

:)

---

### Post by ferronica on 2007-06-03
which one is more risky, and i dont know how to remove old kernel from system i want to use new not old one :) :)

---

### Post by UrbenLegend on 2007-06-03
Do neither option. CD drives are mounted automatically and not through fstab, but with the new kernel, during setup it puts cd drive entries into fstab. Nautilus sees this and puts two icons on the desktop. Simply remove the cd drive entries and you should be fine.

The way the new kernel update handles drives is quite stupid really. It reverses the new naming convention that the kernel devs have put in place.

---

### Post by rfurman24 on 2007-06-03
Yes. I edited my fstab to get rid of the cdrom entries and a floppy as well  to fix my problem.

---

