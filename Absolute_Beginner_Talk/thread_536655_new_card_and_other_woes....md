---
title: "new card and other woes..."
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-08-28
[COLOR=DarkOrange][B]Well it mostly started when i bought my new 8800 gts.
I had to reinstall xp to not get blue screens, I also installed vista again to get some dx10 action.
anyways i have a couple of problems i've tried reinstalling grub but if i choose vista or xp the next time i boot up it defaults to that os. So i have to boot up g-parted and set the boot partition, its very annoying.

also i've had this problem for awhile now and its now becoming worse to the point that every time i boot up ubuntu i can't connect to the internet.

also i've tried to install compiz-fusion multiple times but it only partially worked the first time. Also the update manager has and update for the compiz core from the latest core to the latest core no matter how many times i install. As well when i try to start compiz from the terminal it says that there is no compiz core.

Much thanks for help.
[/B][/COLOR]

---

### Post by dwhitney67 on 2007-08-28
I'm surprised you didn't mention about any problems with your car or your pet dog.

Seriously, if you need some help it would be nice if you created a post for each problem, and please do try to be specific as to what the problem is.  What error messages are you seeing, what hardware you have, network type (wired or wifi), etc.

Use these commands to help you diagnose what your system is "seeing":

$ dmesg
$ lspci

---

### Post by southernman on 2007-08-28
Please... don't use colored text for your entire post. It's very hard to read for us old people. ;)

I don't see any questions in your post... just comments.

---

### Post by Nigmah on 2007-08-28
@southernman
Sorry about that its just a thing i do but my questions are how do i fix grub so its always shows up?
How do i fix my internet so that it always works
and how do i get compiz-fusion up and running?
dmesg output:
[/b]```
[    1.404000] assign_interrupt_mode Found MSI capability
[    1.404000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.404000] isapnp: Scanning for PnP cards...
[    1.756000] isapnp: No Plug & Play device found
[    1.776000] Real Time Clock Driver v1.12ac
[    1.776000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.776000] mice: PS/2 mouse device common for all mice
[    1.776000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.776000] input: Macintosh mouse button emulation as /class/input/input0
[    1.776000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.776000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.776000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.780000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.780000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.780000] EISA: Probing bus 0 at eisa.0
[    1.780000] Cannot allocate resource for EISA slot 4
[    1.780000] EISA: Detected 0 cards.
[    1.812000] TCP cubic registered
[    1.812000] NET: Registered protocol family 1
[    1.812000] Starting balanced_irq
[    1.812000] Using IPI No-Shortcut mode
[    1.812000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.812000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.812000]   Magic number: 3:956:654
[    1.812000] Freeing unused kernel memory: 328k freed
[    1.816000] Time: acpi_pm clocksource has been installed.
[    3.092000] Capability LSM initialized
[    3.136000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.136000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.548000] usbcore: registered new interface driver usbfs
[    3.548000] usbcore: registered new interface driver hub
[    3.548000] usbcore: registered new device driver usb
[    3.548000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.548000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.548000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    3.548000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02c000
[    3.548000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.548000] usb usb1: configuration #1 chosen from 1 choice
[    3.548000] hub 1-0:1.0: USB hub found
[    3.548000] hub 1-0:1.0: 8 ports detected
[    3.556000] SCSI subsystem initialized
[    3.560000] libata version 2.20 loaded.
[    3.660000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.660000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.660000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.660000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    3.660000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    3.680000] 8139too Fast Ethernet driver 0.9.28
[    3.684000] ieee1394: Initialized config rom entry `ip1394'
[    3.720000] usb usb2: configuration #1 chosen from 1 choice
[    3.720000] hub 2-0:1.0: USB hub found
[    3.720000] hub 2-0:1.0: 4 ports detected
[    3.824000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.824000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.824000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    3.824000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02d000
[    3.884000] usb usb3: configuration #1 chosen from 1 choice
[    3.884000] hub 3-0:1.0: USB hub found
[    3.884000] hub 3-0:1.0: 4 ports detected
[    3.988000] sata_sil 0000:00:12.0: version 2.2
[    3.988000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[    3.988000] ata1: SATA max UDMA/100 cmd 0xf88b8080 ctl 0xf88b808a bmdma 0xf88b8000 irq 17
[    3.988000] ata2: SATA max UDMA/100 cmd 0xf88b80c0 ctl 0xf88b80ca bmdma 0xf88b8008 irq 17
[    3.988000] scsi0 : sata_sil
[    4.076000] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    4.208000] usb 1-3: configuration #1 chosen from 1 choice
[    4.448000] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    4.456000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.464000] ata1.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
[    4.464000] ata1.00: 488397168 sectors, multi 16: LBA48 
[    4.472000] ata1.00: configured for UDMA/100
[    4.472000] scsi1 : sata_sil
[    4.588000] usb 1-4: configuration #1 chosen from 1 choice
[    4.784000] ata2: SATA link down (SStatus 0 SControl 300)
[    4.784000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
[    4.784000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 18
[    4.828000] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    4.836000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.840000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.844000] eth0: RealTek RTL8139 at 0xf8856000, 00:13:d3:db:18:6e, IRQ 19
[    4.844000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.844000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.844000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
[    4.844000] ATIIXP: chipset revision 0
[    4.844000] ATIIXP: not 100% native mode: will probe irqs later
[    4.844000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    4.844000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    4.844000] Probing IDE interface ide0...
[    4.856000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.864000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    4.864000] sda: Write Protect is off
[    4.864000] sda: Mode Sense: 00 3a 00 00
[    4.864000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.864000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    4.864000] sda: Write Protect is off
[    4.864000] sda: Mode Sense: 00 3a 00 00
[    4.864000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.864000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    4.924000] sd 0:0:0:0: Attached scsi disk sda
[    4.928000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.964000] usb 1-5: configuration #1 chosen from 1 choice
[    5.324000] kjournald starting.  Commit interval 5 seconds
[    5.324000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.412000] Probing IDE interface ide1...
[    5.636000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.844000] usb 2-1: configuration #1 chosen from 1 choice
[    6.112000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000db8a9f]
[    6.148000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    6.152000] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    6.360000] usb 3-3: configuration #1 chosen from 1 choice
[    6.664000] usb 3-4: new full speed USB device using ohci_hcd and address 3
[    6.872000] usb 3-4: configuration #1 chosen from 1 choice
[    6.872000] usb 1-4: USB disconnect, address 4
[    6.932000] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[    6.988000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.176000] usb 1-4: new high speed USB device using ehci_hcd and address 8
[    7.312000] usb 1-4: configuration #1 chosen from 1 choice
[    7.364000] usbcore: registered new interface driver libusual
[    7.852000] Initializing USB Mass Storage driver...
[    7.852000] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.852000] usb-storage: device found at 3
[    7.852000] usb-storage: waiting for device to settle before scanning
[    7.852000] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.852000] usb-storage: device found at 5
[    7.852000] usb-storage: waiting for device to settle before scanning
[    7.852000] scsi4 : SCSI emulation for USB Mass Storage devices
[    7.852000] usbcore: registered new interface driver usb-storage
[    7.852000] USB Mass Storage support registered.
[    7.852000] usb-storage: device found at 3
[    7.852000] usb-storage: waiting for device to settle before scanning
[    9.448000] usb 1-4: USB disconnect, address 8
[    9.940000] usb 1-4: new high speed USB device using ehci_hcd and address 9
[   10.076000] usb 1-4: configuration #1 chosen from 1 choice
[   12.220000] usb 1-4: USB disconnect, address 9
[   12.712000] usb 1-4: new high speed USB device using ehci_hcd and address 10
[   12.852000] usb-storage: device scan complete
[   12.852000] usb 1-4: configuration #1 chosen from 1 choice
[   12.852000] usb-storage: device scan complete
[   12.852000] usb-storage: device scan complete
[   12.852000] scsi 2:0:0:0: Direct-Access     Hitachi  HDT725025VLAT80  V5DO PQ: 0 ANSI: 2
[   12.852000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   12.852000] scsi 3:0:0:0: Direct-Access     WDC WD50 00AAKB-00UKA     07.0 PQ: 0 ANSI: 2
[   12.852000] sdb: Write Protect is off
[   12.852000] sdb: Mode Sense: 53 00 00 08
[   12.852000] sdb: assuming drive cache: write through
[   12.852000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   12.856000] sdb: Write Protect is off
[   12.856000] sdb: Mode Sense: 53 00 00 08
[   12.856000] sdb: assuming drive cache: write through
[   12.856000]  sdb:<5>scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   12.864000] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   12.868000]  sdb1
[   12.868000] sd 2:0:0:0: Attached scsi disk sdb
[   12.868000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   12.868000] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   12.868000] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   12.872000] sdc: Write Protect is off
[   12.872000] sdc: Mode Sense: 00 00 00 00
[   12.872000] sdc: assuming drive cache: write through
[   12.872000] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   12.876000] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   12.876000] sdc: Write Protect is off
[   12.876000] sdc: Mode Sense: 00 00 00 00
[   12.876000] sdc: assuming drive cache: write through
[   12.876000]  sdc: sdc1
[   12.888000] sd 3:0:0:0: Attached scsi disk sdc
[   12.888000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   12.900000] sd 4:0:0:0: Attached scsi removable disk sdd
[   12.900000] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   12.908000] sd 4:0:0:1: Attached scsi removable disk sde
[   12.908000] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   12.920000] sd 4:0:0:2: Attached scsi removable disk sdf
[   12.920000] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   12.928000] sd 4:0:0:3: Attached scsi removable disk sdg
[   12.928000] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   13.364000] eth0: link down
[   13.772000] NET: Registered protocol family 10
[   13.772000] lo: Disabled Privacy Extensions
[   13.772000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.564000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.600000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.600000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.736000] input: PC Speaker as /class/input/input2
[   14.816000] Linux video capture interface: v2.00
[   14.884000] parport: PnPBIOS parport detected.
[   14.884000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   14.980000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.992000] usb 1-4: USB disconnect, address 10
[   15.040000] ath_hal: module license 'Proprietary' taints kernel.
[   15.040000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.556000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[   15.556000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.556000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   15.624000] ivtv:  ==================== START INIT IVTV ====================
[   15.624000] ivtv:  version 0.10.1 (tagged release) loading
[   15.624000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   15.624000] ivtv:  In case of problems please include the debug info between
[   15.624000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   15.624000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   15.624000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   15.628000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 18
[   15.632000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   15.648000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   15.648000] Uniform CD-ROM driver Revision: 3.20
[   15.652000] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   15.668000] usb 1-4: new high speed USB device using ehci_hcd and address 11
[   15.720000] wlan: 0.8.4.2 (0.9.3.1)
[   15.780000] ath_pci: 0.9.4.5 (0.9.3.1)
[   15.804000] usb 1-4: configuration #1 chosen from 1 choice
[   15.808000] usbcore: registered new interface driver hiddev
[   15.948000] input: Device USB Device as /class/input/input4
[   15.948000] input: USB HID v1.00 Keyboard [Device USB Device] on usb-0000:00:13.0-1
[   15.956000] input: Device USB Device as /class/input/input5
[   15.956000] input: USB HID v1.00 Mouse [Device USB Device] on usb-0000:00:13.0-1
[   15.956000] usbcore: registered new interface driver usbhid
[   15.956000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   16.292000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   16.508000] ivtv0: Encoder revision: 0x02050032
[   16.508000] ivtv0: Recommended firmware version is 0x02060039.
[   16.576000] tveeprom 1-0050: Hauppauge model 26552, rev B268, serial# 8779184
[   16.576000] tveeprom 1-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   16.576000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   16.576000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   16.576000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   16.576000] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   16.576000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   16.608000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   16.608000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   16.612000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.644000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   18.016000] usb 1-4: USB disconnect, address 11
[   18.384000] usb 1-4: new high speed USB device using ehci_hcd and address 12
[   18.520000] usb 1-4: configuration #1 chosen from 1 choice
[   20.788000] usb 1-4: USB disconnect, address 12
[   21.124000] usb 1-4: new high speed USB device using ehci_hcd and address 13
[   21.264000] usb 1-4: configuration #1 chosen from 1 choice
[   21.456000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   21.584000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   21.652000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   21.652000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   21.652000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   21.652000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   21.652000] ivtv0: Registered device radio0 for encoder radio
[   21.652000] tuner 1-0061: type set to 47 (LG NTSC (TAPE series))
[   22.040000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   22.040000] ivtv:  ====================  END INIT IVTV  ====================
[   22.040000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 19
[   22.040000] wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)
[   22.040000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   22.040000] ACPI: PCI Interrupt 0000:00:14.5[b] -> GSI 17 (level, low) -> IRQ 22
[   22.188000] fuse init (API version 7.8)
[   22.208000] lp0: using parport0 (interrupt-driven).
[   22.456000] EXT3 FS on sda4, internal journal
[   22.764000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   22.812000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   23.308000] usb 1-4: USB disconnect, address 13
[   24.052000] usb 1-4: new high speed USB device using ehci_hcd and address 14
[   24.188000] usb 1-4: configuration #1 chosen from 1 choice
[   24.572000] NET: Registered protocol family 17
[   26.332000] usb 1-4: USB disconnect, address 14
[   26.824000] usb 1-4: new high speed USB device using ehci_hcd and address 15
[   26.964000] usb 1-4: configuration #1 chosen from 1 choice
[   28.644000] Using specific hotkey driver
[   28.680000] input: Power Button (FF) as /class/input/input6
[   28.680000] ACPI: Power Button (FF) [PWRF]
[   28.680000] input: Power Button (CM) as /class/input/input7
[   28.680000] ACPI: Power Button (CM) [PWRB]
[   28.812000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   28.812000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   28.812000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   28.812000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   28.864000] No dock devices found.
[   28.888000] ibm_acpi: ec object not found
[   29.008000] pcc_acpi: loading...
[   29.104000] usb 1-4: USB disconnect, address 15
[   29.596000] usb 1-4: new high speed USB device using ehci_hcd and address 16
[   29.736000] usb 1-4: configuration #1 chosen from 1 choice
[   31.876000] usb 1-4: USB disconnect, address 16
[   32.368000] usb 1-4: new high speed USB device using ehci_hcd and address 17
[   32.504000] usb 1-4: configuration #1 chosen from 1 choice
[   33.116000] ppdev: user-space parallel port driver
[   34.652000] usb 1-4: USB disconnect, address 17
[   34.896000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.896000] apm: disabled - APM is not SMP safe.
[   35.000000] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   35.000000] vboxdrv: Successfully done.
[   35.136000] usb 1-4: new high speed USB device using ehci_hcd and address 18
[   35.272000] usb 1-4: configuration #1 chosen from 1 choice
[   36.024000] Bluetooth: Core ver 2.11
[   36.024000] NET: Registered protocol family 31
[   36.024000] Bluetooth: HCI device and connection manager initialized
[   36.024000] Bluetooth: HCI socket layer initialized
[   36.052000] Bluetooth: L2CAP ver 2.8
[   36.052000] Bluetooth: L2CAP socket layer initialized
[   36.056000] Bluetooth: RFCOMM socket layer initialized
[   36.056000] Bluetooth: RFCOMM TTY layer initialized
[   36.056000] Bluetooth: RFCOMM ver 1.8
[   38.176000] usb 1-4: USB disconnect, address 18
[   38.668000] usb 1-4: new high speed USB device using ehci_hcd and address 19
[   38.804000] usb 1-4: configuration #1 chosen from 1 choice
[   40.948000] usb 1-4: USB disconnect, address 19
[   41.440000] usb 1-4: new high speed USB device using ehci_hcd and address 20
[   41.576000] usb 1-4: configuration #1 chosen from 1 choice
[   43.720000] usb 1-4: USB disconnect, address 20
[   44.212000] usb 1-4: new high speed USB device using ehci_hcd and address 21
[   44.352000] usb 1-4: configuration #1 chosen from 1 choice
[   46.492000] usb 1-4: USB disconnect, address 21
[   46.984000] usb 1-4: new high speed USB device using ehci_hcd and address 22
[   47.120000] usb 1-4: configuration #1 chosen from 1 choice
[   49.264000] usb 1-4: USB disconnect, address 22
[   49.756000] usb 1-4: new high speed USB device using ehci_hcd and address 23
[   49.892000] usb 1-4: configuration #1 chosen from 1 choice
[   52.036000] usb 1-4: USB disconnect, address 23
[   52.528000] usb 1-4: new high speed USB device using ehci_hcd and address 24
[   52.664000] usb 1-4: configuration #1 chosen from 1 choice
[   54.808000] usb 1-4: USB disconnect, address 24
[   55.300000] usb 1-4: new high speed USB device using ehci_hcd and address 25
[   55.436000] usb 1-4: configuration #1 chosen from 1 choice
[   57.580000] usb 1-4: USB disconnect, address 25
[   58.072000] usb 1-4: new high speed USB device using ehci_hcd and address 26
[   58.208000] usb 1-4: configuration #1 chosen from 1 choice
[   60.352000] usb 1-4: USB disconnect, address 26
[   60.844000] usb 1-4: new high speed USB device using ehci_hcd and address 27
[   60.980000] usb 1-4: configuration #1 chosen from 1 choice
[   63.124000] usb 1-4: USB disconnect, address 27
[   63.616000] usb 1-4: new high speed USB device using ehci_hcd and address 28
[   63.752000] usb 1-4: configuration #1 chosen from 1 choice
[   65.896000] usb 1-4: USB disconnect, address 28
[   66.388000] usb 1-4: new high speed USB device using ehci_hcd and address 29
[   66.524000] usb 1-4: configuration #1 chosen from 1 choice
[   68.668000] usb 1-4: USB disconnect, address 29
[   69.160000] usb 1-4: new high speed USB device using ehci_hcd and address 30
[   69.296000] usb 1-4: configuration #1 chosen from 1 choice
[   71.440000] usb 1-4: USB disconnect, address 30
[   71.932000] usb 1-4: new high speed USB device using ehci_hcd and address 31
[   72.068000] usb 1-4: configuration #1 chosen from 1 choice
[   74.212000] usb 1-4: USB disconnect, address 31
[   74.704000] usb 1-4: new high speed USB device using ehci_hcd and address 32
[   74.840000] usb 1-4: configuration #1 chosen from 1 choice
[   76.984000] usb 1-4: USB disconnect, address 32
[   77.476000] usb 1-4: new high speed USB device using ehci_hcd and address 33
[   77.612000] usb 1-4: configuration #1 chosen from 1 choice
[   79.756000] usb 1-4: USB disconnect, address 33
[   80.248000] usb 1-4: new high speed USB device using ehci_hcd and address 34
[   80.384000] usb 1-4: configuration #1 chosen from 1 choice
[   82.528000] usb 1-4: USB disconnect, address 34
[   83.020000] usb 1-4: new high speed USB device using ehci_hcd and address 35
[   83.156000] usb 1-4: configuration #1 chosen from 1 choice
[   85.300000] usb 1-4: USB disconnect, address 35
[   85.792000] usb 1-4: new high speed USB device using ehci_hcd and address 36
[   85.928000] usb 1-4: configuration #1 chosen from 1 choice
[   88.072000] usb 1-4: USB disconnect, address 36
[   88.564000] usb 1-4: new high speed USB device using ehci_hcd and address 37
[   88.704000] usb 1-4: configuration #1 chosen from 1 choice
[   90.844000] usb 1-4: USB disconnect, address 37
[   91.336000] usb 1-4: new high speed USB device using ehci_hcd and address 38
[   91.476000] usb 1-4: configuration #1 chosen from 1 choice
[   93.616000] usb 1-4: USB disconnect, address 38
[   94.108000] usb 1-4: new high speed USB device using ehci_hcd and address 39
[   94.244000] usb 1-4: configuration #1 chosen from 1 choice
[   96.388000] usb 1-4: USB disconnect, address 39
[   96.880000] usb 1-4: new high speed USB device using ehci_hcd and address 40
[   97.016000] usb 1-4: configuration #1 chosen from 1 choice
[   99.160000] usb 1-4: USB disconnect, address 40
[   99.652000] usb 1-4: new high speed USB device using ehci_hcd and address 41
[   99.788000] usb 1-4: configuration #1 chosen from 1 choice
[  101.932000] usb 1-4: USB disconnect, address 41
[  102.424000] usb 1-4: new high speed USB device using ehci_hcd and address 42
[  102.560000] usb 1-4: configuration #1 chosen from 1 choice
[  104.704000] usb 1-4: USB disconnect, address 42
[  105.196000] usb 1-4: new high speed USB device using ehci_hcd and address 43
[  105.336000] usb 1-4: configuration #1 chosen from 1 choice
[  107.476000] usb 1-4: USB disconnect, address 43
[  107.968000] usb 1-4: new high speed USB device using ehci_hcd and address 44
[  108.108000] usb 1-4: configuration #1 chosen from 1 choice
[  110.248000] usb 1-4: USB disconnect, address 44
[  110.740000] usb 1-4: new high speed USB device using ehci_hcd and address 45
[  110.876000] usb 1-4: configuration #1 chosen from 1 choice
[  113.020000] usb 1-4: USB disconnect, address 45
[  113.512000] usb 1-4: new high speed USB device using ehci_hcd and address 46
[  113.648000] usb 1-4: configuration #1 chosen from 1 choice
[  115.792000] usb 1-4: USB disconnect, address 46
[  116.284000] usb 1-4: new high speed USB device using ehci_hcd and address 47
[  116.424000] usb 1-4: configuration #1 chosen from 1 choice
[  118.564000] usb 1-4: USB disconnect, address 47
[  119.056000] usb 1-4: new high speed USB device using ehci_hcd and address 48
[  119.192000] usb 1-4: configuration #1 chosen from 1 choice
[  121.336000] usb 1-4: USB disconnect, address 48
[  121.828000] usb 1-4: new high speed USB device using ehci_hcd and address 49
[  121.968000] usb 1-4: configuration #1 chosen from 1 choice
[  124.108000] usb 1-4: USB disconnect, address 49
[  124.600000] usb 1-4: new high speed USB device using ehci_hcd and address 50
[  124.740000] usb 1-4: configuration #1 chosen from 1 choice
[  126.880000] usb 1-4: USB disconnect, address 50
[  127.372000] usb 1-4: new high speed USB device using ehci_hcd and address 51
[  127.512000] usb 1-4: configuration #1 chosen from 1 choice
[  129.652000] usb 1-4: USB disconnect, address 51
[  130.144000] usb 1-4: new high speed USB device using ehci_hcd and address 52
[  130.280000] usb 1-4: configuration #1 chosen from 1 choice
[  132.424000] usb 1-4: USB disconnect, address 52
[  132.916000] usb 1-4: new high speed USB device using ehci_hcd and address 53
[  133.052000] usb 1-4: configuration #1 chosen from 1 choice
[  135.196000] usb 1-4: USB disconnect, address 53
[  135.688000] usb 1-4: new high speed USB device using ehci_hcd and address 54
[  135.824000] usb 1-4: configuration #1 chosen from 1 choice
[  137.968000] usb 1-4: USB disconnect, address 54
[  138.460000] usb 1-4: new high speed USB device using ehci_hcd and address 55
[  138.596000] usb 1-4: configuration #1 chosen from 1 choice
[  140.740000] usb 1-4: USB disconnect, address 55
[  141.232000] usb 1-4: new high speed USB device using ehci_hcd and address 56
[  141.368000] usb 1-4: configuration #1 chosen from 1 choice
[  143.512000] usb 1-4: USB disconnect, address 56
[  144.004000] usb 1-4: new high speed USB device using ehci_hcd and address 57
[  144.140000] usb 1-4: configuration #1 chosen from 1 choice
[  146.284000] usb 1-4: USB disconnect, address 57
[  146.776000] usb 1-4: new high speed USB device using ehci_hcd and address 58
[  146.916000] usb 1-4: configuration #1 chosen from 1 choice
[  149.056000] usb 1-4: USB disconnect, address 58
[  149.548000] usb 1-4: new high speed USB device using ehci_hcd and address 59
[  149.684000] usb 1-4: configuration #1 chosen from 1 choice
[  151.828000] usb 1-4: USB disconnect, address 59
[  152.320000] usb 1-4: new high speed USB device using ehci_hcd and address 60
[  152.456000] usb 1-4: configuration #1 chosen from 1 choice
[  154.600000] usb 1-4: USB disconnect, address 60
[  155.092000] usb 1-4: new high speed USB device using ehci_hcd and address 61
[  155.228000] usb 1-4: configuration #1 chosen from 1 choice
[  157.372000] usb 1-4: USB disconnect, address 61
[  157.864000] usb 1-4: new high speed USB device using ehci_hcd and address 62
[  158.004000] usb 1-4: configuration #1 chosen from 1 choice
[  160.144000] usb 1-4: USB disconnect, address 62
[  160.636000] usb 1-4: new high speed USB device using ehci_hcd and address 63
[  160.772000] usb 1-4: configuration #1 chosen from 1 choice
[  162.916000] usb 1-4: USB disconnect, address 63
[  163.408000] usb 1-4: new high speed USB device using ehci_hcd and address 64
[  163.544000] usb 1-4: configuration #1 chosen from 1 choice
[  165.688000] usb 1-4: USB disconnect, address 64
[  166.180000] usb 1-4: new high speed USB device using ehci_hcd and address 65
[  166.316000] usb 1-4: configuration #1 chosen from 1 choice
[  168.460000] usb 1-4: USB disconnect, address 65
[  168.952000] usb 1-4: new high speed USB device using ehci_hcd and address 66
[  169.092000] usb 1-4: configuration #1 chosen from 1 choice
[  171.232000] usb 1-4: USB disconnect, address 66
[  171.724000] usb 1-4: new high speed USB device using ehci_hcd and address 67
[  171.860000] usb 1-4: configuration #1 chosen from 1 choice
[  174.004000] usb 1-4: USB disconnect, address 67
[  174.496000] usb 1-4: new high speed USB device using ehci_hcd and address 68
[  174.632000] usb 1-4: configuration #1 chosen from 1 choice
[  176.776000] usb 1-4: USB disconnect, address 68
[  177.268000] usb 1-4: new high speed USB device using ehci_hcd and address 69
[  177.404000] usb 1-4: configuration #1 chosen from 1 choice
[  179.548000] usb 1-4: USB disconnect, address 69
[  180.040000] usb 1-4: new high speed USB device using ehci_hcd and address 70
[  180.176000] usb 1-4: configuration #1 chosen from 1 choice



```lspci output:
```


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
02:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```output from trying to start compiz from terminal
```

compiz (core) - Fatal: No composite extension
```output from updater:
```

From version 1:0.5.2-0ubuntu2~ppal to 1:0.5.2~ubuntu2~ppal

```

---

### Post by southernman on 2007-08-28
Whoaaa. I don't think the guy/lady was trying to be a jerk... that was a bit uncalled for don't you think. It's certainly against the code of conduct for the forum.

None-the-less, I'll refer you to Hermanzone's Grub page found [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by wieman01 on 2007-08-28
Deleted...

---

### Post by Nigmah on 2007-08-28
[B]ah yes i forgot to tell you my system specs heres the page
[/B][http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00586071&lc=en&cc=us&dlc=en&product=1821850](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00586071&lc=en&cc=us&dlc=en&product=1821850)

i've swapped the old crappy 300 watt psu that came with it for a silverstone 500watt psu to power the 8800, which of course i've also added.

---

### Post by bapoumba on 2007-08-28
Thanks for editing your post, Nigmah.

---

