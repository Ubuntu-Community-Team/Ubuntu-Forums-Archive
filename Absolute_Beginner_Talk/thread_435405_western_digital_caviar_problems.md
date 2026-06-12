---
title: "western digital caviar problems"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-05-06
so i have this western digital caviar sata hd. it's pretty sweet. it'd be alot sweeter if i could get ubuntu to find it.help please  and thank you!

---

### Post by phidia on 2007-05-06
Open a terminal from the livecd and type > fdisk -l
See if your drive is listed, or post the output.

---

### Post by rickycodie on 2007-05-06
i kind of lost it. any other way?

---

### Post by phidia on 2007-05-06
You lost the install cd? So how exactly are you trying to install? If you're trying a net install and ubuntu isn't seeing the hard drive you might be able to open a terminal i.e Alt+Ctrl+F1 and type the fdisk command.

---

### Post by rickycodie on 2007-05-06
sorry we had a miscommunication. i am not trying to install ubuntu, i am just trying to install the new hard drive. 
i already have ubuntu installed.

---

### Post by phidia on 2007-05-06
From ubuntu open a terminal i.e Applications>Acessories>Terminal.
Type fdisk -l <enter>
Do you see your disk listed there? You could also type dmesg and look at the output of that.
And you can browse this [https://wiki.ubuntu.com/HardwareDetection](https://wiki.ubuntu.com/HardwareDetection) for more info.

---

### Post by rickycodie on 2007-05-06
here's the output from dmesg

[   28.093522]   MEM window: 50000000-51ffffff
[   28.093526]   PREFETCH window: 40000000-4fffffff
[   28.093530] PCI: Bridge: 0000:00:1c.0
[   28.093533]   IO window: 1000-1fff
[   28.093539]   MEM window: 52100000-521fffff
[   28.093543]   PREFETCH window: disabled.
[   28.093548] PCI: Bridge: 0000:00:1c.2
[   28.093549]   IO window: disabled.
[   28.093554]   MEM window: disabled.
[   28.093558]   PREFETCH window: disabled.
[   28.093563] PCI: Bridge: 0000:00:1c.3
[   28.093564]   IO window: disabled.
[   28.093569]   MEM window: disabled.
[   28.093573]   PREFETCH window: disabled.

---

### Post by rickycodie on 2007-05-06
[   28.093578] PCI: Bridge: 0000:00:1c.4
[   28.093579]   IO window: disabled.
[   28.093584]   MEM window: disabled.
[   28.093587]   PREFETCH window: disabled.
[   28.093592] PCI: Bridge: 0000:00:1c.5
[   28.093594]   IO window: disabled.
[   28.093599]   MEM window: disabled.
[   28.093602]   PREFETCH window: disabled.
[   28.093608] PCI: Bridge: 0000:00:1e.0
[   28.093609]   IO window: disabled.
[   28.093614]   MEM window: 52000000-520fffff
[   28.093618]   PREFETCH window: disabled.
[   28.093637] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.093644] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.093665] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.093671] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.093691] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.093696] PCI: Setting latency timer of device 0000:00:1c.2 to 64

---

### Post by rickycodie on 2007-05-06
[   28.093717] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   28.093722] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   28.093741] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   28.093747] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.093766] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   28.093771] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   28.093783] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   28.093806] NET: Registered protocol family 2
[   28.132617] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.132752] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.133368] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.133711] TCP: Hash tables configured (established 131072 bind 65536)
[   28.133714] TCP reno registered
[   28.144694] checking if image is initramfs... it is
[   28.713540] Freeing initrd memory: 6751k freed
[   28.714001] audit: initializing netlink socket (disabled)
[   28.714015] audit(1178488774.304:1): initialized
[   28.714090] highmem bounce pool size: 64 pages
[   28.714145] VFS: Disk quotas dquot_6.5.1
[   28.714167] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.714214] io scheduler noop registered
[   28.714218] io scheduler anticipatory registered
[   28.714220] io scheduler deadline registered
[   28.714228] io scheduler cfq registered (default)
[   28.714557] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.714605] assign_interrupt_mode Found MSI capability
[   28.714608] Allocate Port Service[0000:00:01.0:pcie00]
[   28.714713] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.714762] assign_interrupt_mode Found MSI capability
[   28.714765] Allocate Port Service[0000:00:1c.0:pcie00]

---

### Post by rickycodie on 2007-05-06
[   28.714801] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.714910] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   28.714959] assign_interrupt_mode Found MSI capability
[   28.714961] Allocate Port Service[0000:00:1c.2:pcie00]
[   28.714995] Allocate Port Service[0000:00:1c.2:pcie02]
[   28.715105] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   28.715154] assign_interrupt_mode Found MSI capability
[   28.715156] Allocate Port Service[0000:00:1c.3:pcie00]
[   28.715192] Allocate Port Service[0000:00:1c.3:pcie02]
[   28.715301] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.715349] assign_interrupt_mode Found MSI capability
[   28.715352] Allocate Port Service[0000:00:1c.4:pcie00]
[   28.715389] Allocate Port Service[0000:00:1c.4:pcie02]
[   28.715512] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   28.715561] assign_interrupt_mode Found MSI capability
[   28.715563] Allocate Port Service[0000:00:1c.5:pcie00]
[   28.715597] Allocate Port Service[0000:00:1c.5:pcie02]
[   28.715771] isapnp: Scanning for PnP cards...
[   29.067137] isapnp: No Plug & Play device found
[   29.093031] Real Time Clock Driver v1.12ac
[   29.093086] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.093213] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.093955] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.094157] mice: PS/2 mouse device common for all mice
[   29.094818] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.095055] input: Macintosh mouse button emulation as /class/input/input0
[   29.095094] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.095099] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.095310] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   29.098817] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.098824] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.098961] EISA: Probing bus 0 at eisa.0
[   29.098968] Cannot allocate resource for EISA slot 1
[   29.098971] Cannot allocate resource for EISA slot 2
[   29.098992] EISA: Detected 0 cards.
[   29.129018] TCP cubic registered
[   29.129025] NET: Registered protocol family 1
[   29.129047] Using IPI No-Shortcut mode
[   29.129114] ACPI: (supports S0 S1 S3 S4 S5)
[   29.129159]   Magic number: 7:115:1005
[   29.129166]   hash matches device ttye4
[   29.129297]   hash matches device 00:07
[   29.129484] Freeing unused kernel memory: 328k freed
[   29.130654] Time: tsc clocksource has been installed.
[   29.149944] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.352140] Capability LSM initialized
[   30.393268] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   30.393279] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   30.393287] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   30.881142] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   30.881146] Copyright (c) 1999-2006 Intel Corporation.
[   30.881203] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.881218] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   30.907719] usbcore: registered new interface driver usbfs
[   30.907745] usbcore: registered new interface driver hub
[   30.907769] usbcore: registered new device driver usb
[   30.908655] USB Universal Host Controller Interface driver v3.0
[   30.989056] ieee1394: Initialized config rom entry `ip1394'
[   31.053741] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:13:20:b1:cd:4b
[   31.112258] Floppy drive(s): fd0 is 1.44M
[   31.132980] FDC 0 is a post-1991 82077
[   31.159307] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   31.159342] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   31.159354] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   31.159359] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   31.159507] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   31.159537] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002080
[   31.159651] usb usb1: configuration #1 chosen from 1 choice
[   31.159680] hub 1-0:1.0: USB hub found
[   31.159688] hub 1-0:1.0: 2 ports detected
[   31.262904] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   31.262917] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   31.262921] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   31.262946] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   31.262977] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[   31.263066] usb usb2: configuration #1 chosen from 1 choice
[   31.263092] hub 2-0:1.0: USB hub found
[   31.263100] hub 2-0:1.0: 2 ports detected
[   31.366710] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.366722] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.366726] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.366750] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   31.366781] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[   31.366873] usb usb3: configuration #1 chosen from 1 choice
[   31.366900] hub 3-0:1.0: USB hub found
[   31.366908] hub 3-0:1.0: 2 ports detected
[   31.470519] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   31.470531] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   31.470536] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   31.470559] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   31.470591] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020
[   31.470679] usb usb4: configuration #1 chosen from 1 choice
[   31.470707] hub 4-0:1.0: USB hub found
[   31.470715] hub 4-0:1.0: 2 ports detected
[   31.574420] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   31.574435] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   31.574439] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   31.574464] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   31.574498] ehci_hcd 0000:00:1d.7: debug port 1
[   31.574505] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   31.574512] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x52204400
[   31.578379] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.578450] usb usb5: configuration #1 chosen from 1 choice
[   31.578479] hub 5-0:1.0: USB hub found
[   31.578486] hub 5-0:1.0: 8 ports detected
[   31.688513] SCSI subsystem initialized
[   31.694314] libata version 2.20 loaded.
[   31.698027] ACPI: PCI Interrupt 0000:07:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.747820] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[52004000-520047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.753789] ata_piix 0000:00:1f.1: version 2.10ac1
[   31.753810] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   31.753831] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.754021] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000120b0 irq 14
[   31.754052] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x000120b8 irq 15
[   31.754073] scsi0 : ata_piix
[   31.953508] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   32.153868] usb 5-2: configuration #1 chosen from 1 choice
[   32.265391] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   32.265396] ata1.00: ATA-6: ST3120026A, 8.01, max UDMA/100
[   32.265400] ata1.00: 234441648 sectors, multi 16: LBA48 
[   32.265402] ata1.01: ATAPI, max UDMA/33
[   32.273373] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   32.273376] ata1.00: configured for UDMA/100
[   32.280945] usbcore: registered new interface driver libusual
[   32.284490] Initializing USB Mass Storage driver...
[   32.284552] scsi2 : SCSI emulation for USB Mass Storage devices
[   32.284606] usbcore: registered new interface driver usb-storage
[   32.284609] USB Mass Storage support registered.
[   32.284693] usb-storage: device found at 2
[   32.284696] usb-storage: waiting for device to settle before scanning
[   32.452856] ata1.01: configured for UDMA/33
[   32.452871] scsi1 : ata_piix
[   32.452941] ata2: port disabled. ignoring.
[   32.453191] scsi 0:0:0:0: Direct-Access     ATA      ST3120026A       8.01 PQ: 0 ANSI: 5
[   32.454401] scsi 0:0:1:0: CD-ROM            LITE-ON  COMBO SOHC-5236V R$06 PQ: 0 ANSI: 5
[   32.454552] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   32.454579] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   32.454599] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   32.454634] ata3: SATA max UDMA/133 cmd 0x000120c8 ctl 0x000120e6 bmdma 0x000120a0 irq 19
[   32.454660] ata4: SATA max UDMA/133 cmd 0x000120c0 ctl 0x000120e2 bmdma 0x000120a8 irq 19
[   32.454669] scsi3 : ata_piix
[   32.618443] ATA: abnormal status 0x7F on port 0x000120cf
[   32.618461] scsi4 : ata_piix
[   32.943891] ata4.00: ATA-7: WDC WD2500JS-60MHB5, 10.02E04, max UDMA/100
[   32.943895] ata4.00: 488397168 sectors, multi 16: LBA48 
[   32.943898] ata4.01: ATAPI, max UDMA/33
[   32.943900] ata4.01: applying bridge limits
[   32.951863] ata4.00: configured for UDMA/100
[   33.027656] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00902700019ab412]
[   33.115567] ata4.01: configured for UDMA/33
[   33.115756] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
[   33.116673] scsi 4:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S183L SB00 PQ: 0 ANSI: 5
[   33.128333] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   33.128349] sda: Write Protect is off
[   33.128352] sda: Mode Sense: 00 3a 00 00
[   33.128371] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   33.128431] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   33.128443] sda: Write Protect is off
[   33.128445] sda: Mode Sense: 00 3a 00 00
[   33.128462] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.128465]  sda: sda1 sda2 
[   33.159908] sd 0:0:0:0: Attached scsi disk sda
[   33.160151] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   33.160164] sdb: Write Protect is off
[   33.160167] sdb: Mode Sense: 00 3a 00 00
[   33.160187] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.160232] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   33.160243] sdb: Write Protect is off
[   33.160245] sdb: Mode Sense: 00 3a 00 00
[   33.160263] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.160266]  sdb: unknown partition table
[   33.161938] sd 4:0:0:0: Attached scsi disk sdb
[   33.166583] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.166691] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   33.166798] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   33.166905] scsi 4:0:1:0: Attached scsi generic sg3 type 5
[   33.203251] sr0: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[   33.203257] Uniform CD-ROM driver Revision: 3.20
[   33.203453] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   33.233375] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.233549] sr 4:0:1:0: Attached scsi CD-ROM sr1
[   33.391442] Attempting manual resume
[   33.391446] swsusp: Resume From Partition 8:5
[   33.391448] PM: Checking swsusp image.
[   33.391929] PM: Resume from disk failed.
[   33.431469] kjournald starting.  Commit interval 5 seconds
[   33.431480] EXT3-fs: mounted filesystem with ordered data mode.
[   37.285262] usb-storage: device scan complete
[   37.289127] scsi 2:0:0:0: Direct-Access     Y-E DATA CF Card Reader   3.10 PQ: 0 ANSI: 0
[   37.292741] scsi 2:0:0:1: Direct-Access     Y-E DATA SM Card Reader   3.10 PQ: 0 ANSI: 0
[   37.296482] scsi 2:0:0:2: Direct-Access     Y-E DATA MS Card Reader   3.10 PQ: 0 ANSI: 0
[   37.299601] scsi 2:0:0:3: Direct-Access     Y-E DATA SD Card Reader   3.10 PQ: 0 ANSI: 0
[   37.303992] sd 2:0:0:0: Attached scsi removable disk sdc
[   37.304034] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   37.308880] sd 2:0:0:1: Attached scsi removable disk sdd
[   37.308914] sd 2:0:0:1: Attached scsi generic sg5 type 0
[   37.313710] sd 2:0:0:2: Attached scsi removable disk sde
[   37.313745] sd 2:0:0:2: Attached scsi generic sg6 type 0
[   37.628420] sd 2:0:0:3: Attached scsi removable disk sdf
[   37.628459] sd 2:0:0:3: Attached scsi generic sg7 type 0
[   42.478907] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   42.483172] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   42.483176] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   43.748730] NET: Registered protocol family 17
[   44.102909] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.124757] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.262838] Linux agpgart interface v0.102 (c) Dave Jones
[   44.337029] agpgart: Detected an Intel 945G Chipset.
[   44.356294] agpgart: AGP aperture is 256M @ 0x0
[   44.691000] iTCO_vendor_support: vendor-support=0
[   44.706937] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   44.707038] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   44.707081] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   44.725726] intel_rng: Firmware space is locked read-only. If you can't or
[   44.725729] intel_rng: don't want to disable this in firmware setup, and if
[   44.725731] intel_rng: you are certain that your system has a functional
[   44.725732] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   45.177985] input: PC Speaker as /class/input/input2
[   45.306264] parport: PnPBIOS parport detected.
[   45.306324] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   45.411182] nvidia: module license 'NVIDIA' taints kernel.
[   45.732511] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.732523] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   45.732690] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   45.831701] input: ImExPS/2 Logitech MX Mouse as /class/input/input3
[   45.990088] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   45.990110] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   46.522451] lp0: using parport0 (interrupt-driven).
[   46.726954] fuse init (API version 7.8)
[   46.761550] Adding 3028212k swap on /dev/disk/by-uuid/a725a054-9ebd-45e2-a29f-8617ad182cc7.  Priority:-1 extents:1 across:3028212k
[   46.824329] EXT3 FS on sda1, internal journal
[   46.980517] NET: Registered protocol family 10
[   46.980603] lo: Disabled Privacy Extensions
[   52.462727] input: Power Button (FF) as /class/input/input4
[   52.467289] ACPI: Power Button (FF) [PWRF]
[   52.501974] input: Sleep Button (CM) as /class/input/input5
[   52.506293] ACPI: Sleep Button (CM) [SLPB]
[   52.523726] Using specific hotkey driver
[   52.556055] No dock devices found.
[   52.596480] ibm_acpi: ec object not found
[   52.711775] pcc_acpi: loading...
[   58.625823] ppdev: user-space parallel port driver
[   59.820568] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.820573] apm: overridden by ACPI.
[   59.961480] /dev/vmmon[5294]: Module vmmon: registered with major=10 minor=165
[   59.961794] /dev/vmmon[5294]: Module vmmon: initialized
[   60.074853] /dev/vmnet: open called by PID 5320 (vmnet-bridge)
[   60.075122] /dev/vmnet: hub 0 does not exist, allocating memory.
[   60.075307] /dev/vmnet: port on hub 0 successfully opened
[   60.075478] bridge-eth0: enabling the bridge
[   60.075621] bridge-eth0: up
[   60.075737] bridge-eth0: already up
[   60.075873] bridge-eth0: attached
[   60.098994] /dev/vmnet: open called by PID 5334 (vmnet-natd)
[   60.099252] /dev/vmnet: hub 8 does not exist, allocating memory.
[   60.099437] /dev/vmnet: port on hub 8 successfully opened
[   60.144194] /dev/vmnet: open called by PID 5335 (vmnet-netifup)
[   60.144451] /dev/vmnet: hub 1 does not exist, allocating memory.
[   60.144638] /dev/vmnet: port on hub 1 successfully opened
[   60.148721] /dev/vmnet: open called by PID 5336 (vmnet-netifup)
[   60.148977] /dev/vmnet: port on hub 8 successfully opened
[   60.301075] Bluetooth: Core ver 2.11
[   60.301132] NET: Registered protocol family 31
[   60.301134] Bluetooth: HCI device and connection manager initialized
[   60.301137] Bluetooth: HCI socket layer initialized
[   60.332281] Bluetooth: L2CAP ver 2.8
[   60.332286] Bluetooth: L2CAP socket layer initialized
[   60.344333] /dev/vmnet: open called by PID 5399 (vmnet-dhcpd)
[   60.344538] /dev/vmnet: port on hub 8 successfully opened
[   60.345493] /dev/vmnet: open called by PID 5401 (vmnet-dhcpd)
[   60.345709] /dev/vmnet: port on hub 1 successfully opened
[   60.450459] Bluetooth: RFCOMM socket layer initialized
[   60.450472] Bluetooth: RFCOMM TTY layer initialized
[   60.450474] Bluetooth: RFCOMM ver 1.8
[   70.174917] vmnet1: no IPv6 routers present
[   71.141138] vmnet8: no IPv6 routers present
[   74.091689] eth0: no IPv6 routers present
[14215.240618] usb 5-7: new high speed USB device using ehci_hcd and address 3
[14215.373411] usb 5-7: configuration #1 chosen from 1 choice
[14215.373653] scsi5 : SCSI emulation for USB Mass Storage devices
[14215.373774] usb-storage: device found at 3
[14215.373777] usb-storage: waiting for device to settle before scanning
[14220.363183] usb-storage: device scan complete
[14220.363767] scsi 5:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[14220.366177] SCSI device sdg: 1994385 512-byte hdwr sectors (1021 MB)
[14220.366799] sdg: Write Protect is off
[14220.366803] sdg: Mode Sense: 03 00 00 00
[14220.366805] sdg: assuming drive cache: write through
[14220.369043] SCSI device sdg: 1994385 512-byte hdwr sectors (1021 MB)
[14220.369667] sdg: Write Protect is off
[14220.369671] sdg: Mode Sense: 03 00 00 00
[14220.369673] sdg: assuming drive cache: write through
[14220.369676]  sdg: sdg1
[14220.373644] sd 5:0:0:0: Attached scsi removable disk sdg
[14220.373696] sd 5:0:0:0: Attached scsi generic sg8 type 0
[14368.932803] usb 5-7: USB disconnect, address 3
[14399.427672] cdrom: This disc doesn't have any tracks I recognize!
[14405.156713] cdrom: This disc doesn't have any tracks I recognize!
[15522.395211] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15522.395214]   Tx Queue           
[15522.395215]   TDH                 
[15522.395217]   TDT                
[15522.395218]   next_to_use         
[15522.395219]   next_to_clean       
[15522.395220] buffer_info[next_to_clean]
[15522.395221]   time_stamp        
[15522.395222]   next_to_watch       
[15522.395223]   jiffies              
[15522.395224]   next_to_watch.status
[15524.391188] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15524.391191]   Tx Queue            
[15524.391192]   TDH                 
[15524.391193]   TDT               
[15524.391194]   next_to_use          
[15524.391195]   next_to_clean        
[15524.391196] buffer_info[next_to_clean]
[15524.391197]   time_stamp           
[15524.391198]   next_to_watch        
[15524.391199]   jiffies              
[15524.391200]   next_to_watch.status 
[15526.388171] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15526.388174]   Tx Queue             
[15526.388175]   TDH                  
[15526.388177]   TDT                  
[15526.388178]   next_to_use          
[15526.388179]   next_to_clean        
[15526.388180] buffer_info[next_to_clean]
[15526.388181]   time_stamp          
[15526.388182]   next_to_watch        
[15526.388183]   jiffies              
[15526.388184]   next_to_watch.status 
[15528.048185] NETDEV WATCHDOG: eth0: transmit timed out
[15529.814053] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[15529.814059] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[15529.814262] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15557.389998] eth0: no IPv6 routers present
[15559.758202] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15559.758205]   Tx Queue             
[15559.758206]   TDH                  
[15559.758207]   TDT                  
[15559.758208]   next_to_use         
[15559.758209]   next_to_clean       
[15559.758210] buffer_info[next_to_clean]
[15559.758211]   time_stamp          
[15559.758213]   next_to_watch        
[15559.758214]   jiffies              
[15559.758215]   next_to_watch.status 
[15561.754205] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15561.754207]   Tx Queue             
[15561.754209]   TDH                  
[15561.754210]   TDT                  
[15561.754211]   next_to_use          
[15561.754212]   next_to_clean        
[15561.754213] buffer_info[next_to_clean]
[15561.754214]   time_stamp          
[15561.754215]   next_to_watch        
[15561.754216]   jiffies              
[15561.754217]   next_to_watch.status 
[15563.751172] e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang
[15563.751175]   Tx Queue             
[15563.751176]   TDH                  
[15563.751177]   TDT                  
[15563.751178]   next_to_use          
[15563.751179]   next_to_clean        
[15563.751180] buffer_info[next_to_clean]
[15563.751181]   time_stamp          
[15563.751182]   next_to_watch    
[15563.751183]   jiffies          
[15563.751184]   next_to_watch.status
[15564.748408] NETDEV WATCHDOG: eth0: transmit timed out
[15566.582136] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[15566.582143] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[15566.582325] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15591.530949] eth0: no IPv6 routers present
[16749.098671] cdrom: This disc doesn't have any tracks I recognize!
[17958.237710] cdrom: This disc doesn't have any tracks I recognize!
[19689.621072] cdrom: This disc doesn't have any tracks I recognize!
fdisk -l didn't do anything.
 ijust fugured out how to disable smiles

---

### Post by phidia on 2007-05-07
From the output you provided it looks like you have two hard drives. sda has two partitions.
sdb isn't partitioned yet.  I think if you partition the drive ubuntu will recognize the newly created partitions. You could install gparted to help with partitioning if you want-it's a gui partioner.

---

### Post by rickycodie on 2007-05-07
awesome, thanks i found and partitioned it. but how do i mount it?

---

### Post by phidia on 2007-05-07
Restart the computer or maybe you can just logout and back in again to see if ubuntu will put a drive icon on your desktop. If the drive doesn't show up then you may have to create a mountpoint i.e a directory and mount it.
e.g (from terminal) sudo mkdir /mnt/mynewpartition (choose whatever name you want there obviously) To mount it sudo mount /dev/sdb1 /mnt/mynewpartition

If the partition is a different number then what I typed then change it to what it actually is.
I've given you an example but that should get you started. Sometimes the terminal will balk if you don't provide the filesystem of what you're trying to mount. if that happens use mount -t  and add the filesystem type for the partition. Type man mount at terminal.

---

