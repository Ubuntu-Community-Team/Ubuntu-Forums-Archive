---
title: "usb problems"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by heyjoe on 2006-04-07
hi im posting this in beginners because, well im a beginner, but it seems to be a rather complex problem from what ive been told in the irc pages.

basically, ubuntu doesnt like my usb devices-a usb drive and a teac mp3 player. 
they both work fine on win2000 and winxp, but not on linux. the usb ports on my computer are fully functional and ubuntu can recognize my usb mouse. 

when i type dmesg i get the output listed below.

all help is much appreciated as i try to rid myself of windows and convert over to ubuntu 100%

(here is the output)

frank@ubuntu:~$ dmesg
sa.0
[4294671.256000] Cannot allocate resource for EISA slot 1
[4294671.256000] EISA: Detected 0 cards.
[4294671.256000] NET: Registered protocol family 2
[4294671.265000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294671.265000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.265000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.265000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.265000] NET: Registered protocol family 8
[4294671.265000] NET: Registered protocol family 20
[4294671.265000] ACPI wakeup devices:
[4294671.265000] PCI0 USB0 USB1 USB2 MAC0 AMR0 UAR1 UAR2
[4294671.265000] ACPI: (supports S0 S1 S4 S5)
[4294671.265000] Freeing unused kernel memory: 224k freed
[4294671.278000] vga16fb: initializing
[4294671.279000] vga16fb: mapped to 0xc00a0000
[4294671.363000] Console: switching to colour frame buffer device 80x30
[4294671.363000] fb0: VGA16 VGA frame buffer device
[4294671.682000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.711000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.421000] Capability LSM initialized
[4294672.430000] NET: Registered protocol family 1
[4294672.440000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.440000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.440000] ACPI: bus type ide registered
[4294672.445000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294672.445000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[4294672.445000] SIS5513: chipset revision 1
[4294672.445000] SIS5513: not 100% native mode: will probe irqs later
[4294672.445000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294672.445000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[4294672.445000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294672.445000] Probing IDE interface ide0...
[4294672.709000] hda: QUANTUM FIREBALLP AS20.5, ATA DISK drive
[4294673.321000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.321000] Probing IDE interface ide1...
[4294673.993000] hdc: HL-DT-ST GCE-8520B, ATAPI CD/DVD-ROM drive
[4294674.707000] hdd: GCR-8521B, ATAPI CD/DVD-ROM drive
[4294674.758000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.758000] Probing IDE interface ide2...
[4294675.271000] Probing IDE interface ide3...
[4294675.783000] Probing IDE interface ide4...
[4294676.295000] Probing IDE interface ide5...
[4294676.809000] hda: max request size: 128KiB
[4294676.821000] hda: Host Protected Area detected.
[4294676.821000]        current capacity is 40130390 sectors (20546 MB)
[4294676.821000]        native  capacity is 40132503 sectors (20547 MB)
[4294676.822000] hda: Host Protected Area disabled.
[4294676.822000] hda: 40132503 sectors (20547 MB) w/1902KiB Cache, CHS=39813/16/63, UDMA(100)
[4294676.822000] hda: cache flushes not supported
[4294676.822000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[4294676.855000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
[4294676.855000] Uniform CD-ROM driver Revision: 3.20
[4294676.857000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache
[4294677.163000] Attempting manual resume
[4294677.163000] swsusp: Suspend partition has wrong signature?
[4294677.200000] usbcore: registered new driver usbfs
[4294677.200000] usbcore: registered new driver hub
[4294677.200000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.200000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294677.200000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294677.201000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[4294677.201000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xed104000
[4294677.254000] hub 1-0:1.0: USB hub found
[4294677.254000] hub 1-0:1.0: 3 ports detected
[4294677.257000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294677.257000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294677.257000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[4294677.257000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xed100000
[4294677.310000] hub 2-0:1.0: USB hub found
[4294677.310000] hub 2-0:1.0: 3 ports detected
[4294677.313000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294677.313000] ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
[4294677.313000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[4294677.313000] ohci_hcd 0000:00:03.2: irq 22, io mem 0xed101000
[4294677.366000] hub 3-0:1.0: USB hub found
[4294677.366000] hub 3-0:1.0: 2 ports detected
[4294677.387000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[4294677.387000] ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
[4294677.387000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[4294677.387000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xed102000
[4294677.387000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[4294677.387000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.387000] hub 4-0:1.0: USB hub found
[4294677.387000] hub 4-0:1.0: 8 ports detected
[4294677.415000] sis900.c: v1.08.08 Jan. 22 2005
[4294677.415000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294677.416000] 0000:00:04.0: ICS LAN PHY transceiver found at address 1.
[4294677.426000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294677.427000] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 19, 00:0f:ea:42:2f:96.
[4294677.435000] SCSI subsystem initialized
[4294677.436000] libata version 1.11 loaded.
[4294677.437000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294677.437000] ata1: SATA max UDMA/133 cmd 0xAC00 ctl 0xB002 bmdma 0xBC00 irq 17
[4294677.437000] ata2: SATA max UDMA/133 cmd 0xB400 ctl 0xB802 bmdma 0xBC08 irq 17
[4294677.639000] ata1: no device found (phy stat 00000000)
[4294677.639000] scsi0 : sata_sis
[4294677.840000] ata2: no device found (phy stat 00000000)
[4294677.840000] scsi1 : sata_sis
[4294677.990000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294679.867000] usbcore: registered new driver hiddev
[4294679.879000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical\uffff] on usb-0000:00:03.1-1
[4294679.879000] usbcore: registered new driver usbhid
[4294679.879000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.230000] ACPI: CPU0 (power states: C1[C1])
[4294680.350000] Attempting manual resume
[4294680.350000] swsusp: Suspend partition has wrong signature?
[4294680.361000] kjournald starting.  Commit interval 5 seconds
[4294680.361000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.492000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294701.874000] hda: dma_timer_expiry: dma status == 0x21
[4294711.874000] hda: DMA timeout error
[4294711.874000] hda: dma timeout error: status=0xd0 { Busy }
[4294711.874000]
[4294711.874000] ide: failed opcode was: unknown
[4294711.874000] hda: DMA disabled
[4294711.924000] ide0: reset: success
[4294731.972000] hda: dma_timer_expiry: dma status == 0x21
[4294741.972000] hda: DMA timeout error
[4294741.972000] hda: dma timeout error: status=0xd0 { Busy }
[4294741.972000]
[4294741.972000] ide: failed opcode was: unknown
[4294741.972000] hda: DMA disabled
[4294742.072000] ide0: reset: success
[4294744.350000] Adding 441716k swap on /dev/hda6.  Priority:-1 extents:1
[4294744.493000] EXT3 FS on hda2, internal journal
[4294750.069000] parport: PnPBIOS parport detected.
[4294750.069000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294750.129000] parport0: Printer, Canon BJC-1000SP
[4294750.133000] lp0: using parport0 (interrupt-driven).
[4294750.159000] mice: PS/2 mouse device common for all mice
[4294750.176000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[4294753.306000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294753.873000] cdrom: open failed.
[4294753.878000] cdrom: open failed.
[4294773.897000] hda: dma_timer_expiry: dma status == 0x21
[4294783.897000] hda: DMA timeout error
[4294783.897000] hda: dma timeout error: status=0xd0 { Busy }
[4294783.897000]
[4294783.897000] ide: failed opcode was: unknown
[4294783.897000] hda: DMA disabled
[4294783.947000] ide0: reset: success
[4294785.397000] Linux agpgart interface v0.101 (c) Dave Jones
[4294785.403000] agpgart: Detected SiS 661 chipset
[4294785.421000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294785.494000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294785.498000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294785.498000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294785.709000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[4294786.018000] intel8x0_measure_ac97_clock: measured 49615 usecs
[4294786.018000] intel8x0: clocking to 48000
[4294788.278000] Real Time Clock Driver v1.12
[4294788.330000] input: PC Speaker
[4294788.425000] Floppy drive(s): fd0 is 1.44M
[4294788.440000] FDC 0 is a post-1991 82077
[4294788.675000] ts: Compaq touchscreen protocol output
[4294790.400000] NET: Registered protocol family 17
[4294793.391000] eth0: Media Link On 100mbps full-duplex
[4294813.689000] NET: Registered protocol family 10
[4294813.689000] Disabled Privacy Extensions on device c02eb280(lo)
[4294813.689000] IPv6 over IPv4 tunneling driver
[4294815.865000] ACPI: Power Button (FF) [PWRF]
[4294815.866000] ACPI: Power Button (CM) [PWRB]
[4294815.953000] ibm_acpi: ec object not found
[4294819.842000] Bluetooth: Core ver 2.7
[4294819.842000] NET: Registered protocol family 31
[4294819.842000] Bluetooth: HCI device and connection manager initialized
[4294819.842000] Bluetooth: HCI socket layer initialized
[4294820.043000] Bluetooth: L2CAP ver 2.7
[4294820.043000] Bluetooth: L2CAP socket layer initialized
[4294820.066000] Bluetooth: RFCOMM ver 1.5
[4294820.066000] Bluetooth: RFCOMM socket layer initialized
[4294820.066000] Bluetooth: RFCOMM TTY layer initialized
[4294824.059000] eth0: no IPv6 routers present
[4303902.684000] usb 1-1: new full speed USB device using ohci_hcd and address 2[4303902.764000] usb 1-1: device descriptor read/64, error -110
[4303902.945000] usb 1-1: device descriptor read/64, error -110
[4303903.119000] usb 1-1: new full speed USB device using ohci_hcd and address 3[4303903.199000] usb 1-1: device descriptor read/64, error -110
[4303903.380000] usb 1-1: device descriptor read/64, error -110
[4303903.554000] usb 1-1: new full speed USB device using ohci_hcd and address 4[4303903.958000] usb 1-1: device not accepting address 4, error -110
[4303904.031000] usb 1-1: new full speed USB device using ohci_hcd and address 5[4303904.435000] usb 1-1: device not accepting address 5, error -110
[4303947.824000] usb 4-4: new high speed USB device using ehci_hcd and address 4[4303948.371000] Initializing USB Mass Storage driver...
[4303948.377000] scsi2 : SCSI emulation for USB Mass Storage devices
[4303948.378000] usb-storage: device found at 4
[4303948.378000] usb-storage: waiting for device to settle before scanning
[4303948.378000] usbcore: registered new driver usb-storage
[4303948.378000] USB Mass Storage support registered.
[4303953.379000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 2254
[4303953.379000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4303953.388000] usb-storage: device scan complete
[4303953.462000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4304039.532000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[4304051.620000] sda: Write Protect is off
[4304051.621000] sda: Mode Sense: 55 53 55 53
[4304051.621000] sda: assuming drive cache: write through
[4304125.686000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[4304125.765000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4304185.773000] sda: Write Protect is off
[4304185.773000] sda: Mode Sense: 55 53 55 53
[4304185.773000] sda: assuming drive cache: write through
[4304185.774000]  /dev/scsi/host2/bus0/target0/lun0:<6>usb 4-4: reset high speed USB device using ehci_hcd and address 4
[4304259.921000]  unknown partition table
[4304259.921000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4304293.434000] usb 1-1: new full speed USB device using ohci_hcd and address 6[4304293.514000] usb 1-1: device descriptor read/64, error -110
[4304293.695000] usb 1-1: device descriptor read/64, error -110
[4304293.869000] usb 1-1: new full speed USB device using ohci_hcd and address 7[4304293.949000] usb 1-1: device descriptor read/64, error -110
[4304294.130000] usb 1-1: device descriptor read/64, error -110
[4304294.304000] usb 1-1: new full speed USB device using ohci_hcd and address 8[4304294.708000] usb 1-1: device not accepting address 8, error -110
[4304294.781000] usb 1-1: new full speed USB device using ohci_hcd and address 9[4304295.185000] usb 1-1: device not accepting address 9, error -110
[4305026.184000] usb 1-1: new full speed USB device using ohci_hcd and address 10
[4305026.264000] usb 1-1: device descriptor read/64, error -110
[4305026.445000] usb 1-1: device descriptor read/64, error -110
[4305026.619000] usb 1-1: new full speed USB device using ohci_hcd and address 11
[4305026.699000] usb 1-1: device descriptor read/64, error -110
[4305026.880000] usb 1-1: device descriptor read/64, error -110
[4305027.054000] usb 1-1: new full speed USB device using ohci_hcd and address 12
[4305027.458000] usb 1-1: device not accepting address 12, error -110
[4305027.531000] usb 1-1: new full speed USB device using ohci_hcd and address 13
[4305027.936000] usb 1-1: device not accepting address 13, error -110
[4305426.408000] usb 4-4: USB disconnect, address 4
[4305435.074000] usb 4-4: new high speed USB device using ehci_hcd and address 7[4305435.362000] scsi3 : SCSI emulation for USB Mass Storage devices
[4305435.363000] usb-storage: device found at 7
[4305435.363000] usb-storage: waiting for device to settle before scanning
[4305440.363000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 2254
[4305440.363000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4305440.366000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4305526.436000] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[4305538.521000] sda: Write Protect is off
[4305538.521000] sda: Mode Sense: 55 53 55 53
[4305538.521000] sda: assuming drive cache: write through
[4305612.604000] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[4305612.683000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4305702.691000] sda: Write Protect is off
[4305702.691000] sda: Mode Sense: 55 53 55 53
[4305702.691000] sda: assuming drive cache: write through
[4305702.691000]  /dev/scsi/host3/bus0/target0/lun0:<6>usb 4-4: reset high speed USB device using ehci_hcd and address 7
[4305776.840000]  unknown partition table
[4305776.840000] Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
[4305776.845000] usb-storage: device scan complete
[4305927.321000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4305927.627000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4305927.673000] NTFS volume version 3.0.

---

### Post by trent dillman on 2006-04-07
One of those is coming up as NTFS, so it will be read only.

---

### Post by nalmeth on 2006-04-08
If you have windows software to format your device(s) as fat32 or another filesystem NOT NTFS, then you should. Maybe there is an app you can download to do so?
downloads.com is where I always went when I used windows, but that was a long time ago.
to get more usb relevant results type this:
dmesg grep | usb

---

### Post by trent dillman on 2006-04-08
should read
```
dmesg | grep usb
```

---

### Post by nalmeth on 2006-04-08
oops :oops: my bad

---

