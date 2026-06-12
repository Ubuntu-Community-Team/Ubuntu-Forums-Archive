---
title: "Can't mount 1 of my USB flash drive"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by gilbre on 2008-04-09
I can't get one of my USB drives to mount.  I have tried 4 others that mount just fine.  I was able to mount this a few days ago and it just stopped.  I am not sure how to fix this.  It shows up with command lsusb, but not with fdisk -l.  I have tried gparted.  Additionally, have reformatted in XP and using the manufacturer software to format (adata).  

when I plug in other USB drives and watch the /DEV/ folder not much happens, however when I watch that folder with this drive I get a bunch of usbdev1.1_ep00 files.  There are about 40 files like this with incremental names.... usbdev1.1epXX all the way up to usbdev5.1_epXX

The drive does work in XP just fine...  Stumped.

I attached my dmesg and lsusb results.  If anyone can help me I would really appreciate it.  

Thanks in advance!

---

### Post by dokdoom on 2008-04-09
I didn't see any dmesg output in that file. But you have you tried mounting it manually? I'm not sure how that works in ubuntu but when I used debian I had to mount all of my drives manually. 

run dmesg to find out what to mount. Sometimes (Not always.) You can just mount /dev/sda1 even if it doesn't say sda1. Let's just say i've gotten lucky many times. 

mkdir /mnt/usb
cd /mnt/
mount /dev/sda1 /mnt/usb

Check your your usb directory if you aren't given an error about not being able to find /dev/sda1/

If that doesn't work I don't know what to tell you.

---

### Post by eternicode on 2008-04-09
A simple "fdisk -l" won't list devices owned by root -- such as the main hard drive, etc.  Try using "sudo fdisk -l" and see if it's listed.  Once you have a device name, you can use "pmount /dev/sdaX" to mount it as a user to a temporary folder.  Issue "mount" to find out where it's mounted, open a file manager and navigate to that folder to work with the contents.  When you're done, use "pumount /dev/sdaX" to safely unmount it.

---

### Post by KCormier on 2008-04-10
If you use it on xp machines as well make sure you safely remove the drive before sticking it into an ubuntu machine.  If the drive isn't safely removed, the previous mount isn't properly unmounted, and you must FORCE ubuntu to mount the drive.  It's a security thing because not properly removing media can result in data corruption so it doesn't automatically mount anything that's been removed incorrectly!  Try putting it in the xp machine and then safely removing it (with the little green arrow down by the clock! wait till it says "safe to remove hardware")

-Kevin

---

### Post by gilbre on 2008-04-10
Here is my output from sudo fdisk -l


Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f352f34

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       26626   213873313+   7  HPFS/NTFS
/dev/hda2           26627       59572   264638745   83  Linux
/dev/hda3           59573       60801     9871942+   5  Extended
/dev/hda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076ee0

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30515   245111706    7  HPFS/NTFS
brent@brent-desktop:~$ 



And here is my dmesg output (most of it anyway):
[    1.388000] Cannot allocate resource for EISA slot 6
[    1.388000] EISA: Detected 0 cards.
[    1.388000] TCP cubic registered
[    1.388000] NET: Registered protocol family 1
[    1.388000] Using IPI No-Shortcut mode
[    1.388000]   Magic number: 4:575:752
[    1.388000]   hash matches device ttyS3
[    1.388000] Freeing unused kernel memory: 364k freed
[    1.420000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.544000] AppArmor: AppArmor initialized<5>audit(1207777465.048:2):  type=1505 info="AppArmor initialized" pid=1229
[    2.548000] fuse init (API version 7.8)
[    2.552000] Failure registering capabilities with primary security module.
[    2.908000] usbcore: registered new interface driver usbfs
[    2.908000] usbcore: registered new interface driver hub
[    2.908000] usbcore: registered new device driver usb
[    2.908000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.912000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    2.912000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 16
[    2.912000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    2.912000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.912000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.912000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfbefe000
[    2.932000] SCSI subsystem initialized
[    2.932000] libata version 2.21 loaded.
[    2.948000] USB Universal Host Controller Interface driver v3.0
[    2.968000] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.972000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    2.980000] usb usb1: configuration #1 chosen from 1 choice
[    2.980000] hub 1-0:1.0: USB hub found
[    2.980000] hub 1-0:1.0: 10 ports detected
[    3.084000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    3.084000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 22 (level, low) -> IRQ 17
[    3.084000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    3.084000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.084000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.084000] ehci_hcd 0000:00:02.1: debug port 1
[    3.084000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    3.084000] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfbefdc00
[    3.084000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.084000] usb usb2: configuration #1 chosen from 1 choice
[    3.084000] hub 2-0:1.0: USB hub found
[    3.084000] hub 2-0:1.0: 10 ports detected
[    3.188000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[    3.188000] ACPI: PCI Interrupt 0000:01:07.2[C] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 18
[    3.188000] ehci_hcd 0000:01:07.2: EHCI Host Controller
[    3.188000] ehci_hcd 0000:01:07.2: new USB bus registered, assigned bus number 3
[    3.188000] ehci_hcd 0000:01:07.2: irq 18, io mem 0xfbfffc00
[    3.188000] ehci_hcd 0000:01:07.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.188000] usb usb3: configuration #1 chosen from 1 choice
[    3.188000] hub 3-0:1.0: USB hub found
[    3.188000] hub 3-0:1.0: 4 ports detected
[    3.188000] sata_nv 0000:00:07.0: version 3.4
[    3.188000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    3.188000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LSA0] -> GSI 21 (level, low) -> IRQ 19
[    3.188000] sata_nv 0000:00:07.0: Using ADMA mode
[    3.188000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    3.188000] scsi0 : sata_nv
[    3.188000] scsi1 : sata_nv
[    3.188000] ata1: SATA max UDMA/133 cmd 0xf889e480 ctl 0xf889e4a0 bmdma 0x0001b800 irq 19
[    3.188000] ata2: SATA max UDMA/133 cmd 0xf889e580 ctl 0xf889e5a0 bmdma 0x0001b808 irq 19
[    3.500000] ata1: SATA link down (SStatus 0 SControl 300)
[    3.812000] ata2: SATA link down (SStatus 0 SControl 300)
[    3.812000] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 20
[    3.812000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA1] -> GSI 20 (level, low) -> IRQ 20
[    3.812000] sata_nv 0000:00:08.0: Using ADMA mode
[    3.812000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    3.812000] scsi2 : sata_nv
[    3.812000] scsi3 : sata_nv
[    3.812000] ata3: SATA max UDMA/133 cmd 0xf883e480 ctl 0xf883e4a0 bmdma 0x0001ac00 irq 20
[    3.812000] ata4: SATA max UDMA/133 cmd 0xf883e580 ctl 0xf883e5a0 bmdma 0x0001ac08 irq 20
[    4.028000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    4.124000] ata3: SATA link down (SStatus 0 SControl 300)
[    4.252000] usb 1-1: configuration #1 chosen from 1 choice
[    4.272000] usbcore: registered new interface driver libusual
[    4.276000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.276000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.276000] Initializing USB Mass Storage driver...
[    4.276000] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.276000] usb-storage: device found at 2
[    4.276000] usb-storage: waiting for device to settle before scanning
[    4.276000] usbcore: registered new interface driver usb-storage
[    4.276000] USB Mass Storage support registered.
[    4.592000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.772000] ata4.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[    4.960000] ata4.00: configured for UDMA/100
[    4.960000] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[    4.960000] ata4: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[    4.960000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[    4.960000] NFORCE-CK804: chipset revision 242
[    4.960000] NFORCE-CK804: not 100% native mode: will probe irqs later
[    4.960000] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[    4.960000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[    4.960000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[    4.960000] Probing IDE interface ide0...
[    4.980000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.980000] Uniform CD-ROM driver Revision: 3.20
[    4.980000] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.980000] sr 3:0:0:0: Attached scsi generic sg0 type 5
[    5.248000] hda: Maxtor 6H500R0, ATA DISK drive
[    5.528000] hdb: Maxtor 7Y250P0, ATA DISK drive
[    5.584000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.604000] Probing IDE interface ide1...
[    6.340000] hdc: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[    7.012000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.012000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 18
[    7.012000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[    7.016000] eth0: ADMtek Comet rev 17 at Port 0xd400, 00:18:F8:0B:1A:8E, IRQ 18.
[    7.016000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[    7.016000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 21
[    7.016000] uhci_hcd 0000:01:07.0: UHCI Host Controller
[    7.016000] uhci_hcd 0000:01:07.0: new USB bus registered, assigned bus number 4
[    7.016000] uhci_hcd 0000:01:07.0: irq 21, io base 0x0000dc00
[    7.016000] usb usb4: configuration #1 chosen from 1 choice
[    7.016000] hub 4-0:1.0: USB hub found
[    7.016000] hub 4-0:1.0: 2 ports detected
[    7.024000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.024000] hda: max request size: 512KiB
[    7.028000] hda: 976773168 sectors (500107 MB) w/16384KiB Cache, CHS=60801/255/63, UDMA(133)
[    7.028000] hda: cache flushes supported
[    7.028000]  hda: hda1 hda2 hda3 < hda5 >
[    7.064000] hdb: max request size: 512KiB
[    7.064000] hdb: 490234752 sectors (251000 MB) w/7936KiB Cache, CHS=30515/255/63, UDMA(133)
[    7.064000] hdb: cache flushes supported
[    7.064000]  hdb: hdb1
[    7.120000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 17
[    7.120000] ACPI: PCI Interrupt 0000:01:07.1[B] -> Link [LNKB] -> GSI 17 (level, low) -> IRQ 22
[    7.120000] uhci_hcd 0000:01:07.1: UHCI Host Controller
[    7.120000] uhci_hcd 0000:01:07.1: new USB bus registered, assigned bus number 5
[    7.120000] uhci_hcd 0000:01:07.1: irq 22, io base 0x0000d880
[    7.120000] usb usb5: configuration #1 chosen from 1 choice
[    7.120000] hub 5-0:1.0: USB hub found
[    7.120000] hub 5-0:1.0: 2 ports detected
[    7.224000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    7.224000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 16
[    7.224000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    7.224000] forcedeth: using HIGHDMA
[    7.480000] Attempting manual resume
[    7.480000] swsusp: Resume From Partition 3:5
[    7.480000] PM: Checking swsusp image.
[    7.480000] PM: Resume from disk failed.
[    7.488000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    7.500000] kjournald starting.  Commit interval 5 seconds
[    7.500000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.648000] usb 4-2: configuration #1 chosen from 1 choice
[    7.744000] eth1: forcedeth.c: subsystem: 01462:7325 bound to 0000:00:0a.0
[    7.744000] ACPI: PCI Interrupt 0000:01:07.3[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 21
[    7.796000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    7.804000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    9.076000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106000000e332]
[    9.276000] usb-storage: device scan complete
[    9.284000] scsi 4:0:0:0: Direct-Access     HP       psc 24xx         1.00 PQ: 0 ANSI: 2
[    9.284000] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[   12.700000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.732000] Netfilter messages via NETLINK v0.30.
[   12.740000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   13.784000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.784000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.828000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   13.828000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   13.916000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3611
[   13.916000] usbcore: registered new interface driver usblp
[   13.916000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   14.020000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.064000] input: PC Speaker as /class/input/input2
[   14.104000] Linux video capture interface: v2.00
[   14.200000] sd 4:0:0:0: [sda] Attached SCSI removable disk
[   14.248000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[   14.264000] nvidia: module license 'NVIDIA' taints kernel.
[   14.276000] usb 4-2: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F5)
[   14.512000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 18
[   14.512000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   14.512000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   14.592000] usb 4-2: No supported image sensor detected for this bridge
[   14.592000] usbcore: registered new interface driver sn9c102
[   14.676000] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 22
[   14.676000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LACI] -> GSI 22 (level, low) -> IRQ 17
[   14.676000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.704000] usbcore: registered new interface driver snd-usb-audio
[   15.000000] intel8x0_measure_ac97_clock: measured 54751 usecs
[   15.000000] intel8x0: clocking to 46930
[   15.184000] input: ImExPS/2 Logitech MX Mouse as /class/input/input3
[   15.188000] parport_pc 00:06: reported by Plug and Play ACPI
[   15.188000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   15.616000] lp0: using parport0 (interrupt-driven).
[   15.652000] Adding 9871900k swap on /dev/hda5.  Priority:-1 extents:1 across:9871900k
[   16.020000] EXT3 FS on hda2, internal journal
[   16.900000] No dock devices found.
[   16.980000] input: Power Button (FF) as /class/input/input4
[   16.980000] ACPI: Power Button (FF) [PWRF]
[   16.980000] input: Power Button (CM) as /class/input/input5
[   16.980000] ACPI: Power Button (CM) [PWRB]
[   17.220000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (version 2.00.00)
[   17.220000] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0x9
[   17.220000] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xb
[   17.220000] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xd
[   17.220000] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xf
[   17.220000] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x11
[   17.220000] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[   18.212000] eth0: no link during initialization.
[   18.312000] ppdev: user-space parallel port driver
[   18.680000] audit(1207795482.037:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5329 profile="/usr/sbin/cupsd"
[   21.316000] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   21.316000] eth1: Setting full-duplex based on MII#1 link partner capability of 41e1.
[   21.880000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.880000] apm: disabled - APM is not SMP safe.
[   22.068000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.068000] vboxdrv: Successfully done.
[   22.340000] Failure registering capabilities with primary security module.
[   22.492000] Bluetooth: Core ver 2.11
[   22.492000] NET: Registered protocol family 31
[   22.492000] Bluetooth: HCI device and connection manager initialized
[   22.492000] Bluetooth: HCI socket layer initialized
[   22.504000] Bluetooth: L2CAP ver 2.8
[   22.504000] Bluetooth: L2CAP socket layer initialized
[   22.560000] Bluetooth: RFCOMM socket layer initialized
[   22.560000] Bluetooth: RFCOMM TTY layer initialized
[   22.560000] Bluetooth: RFCOMM ver 1.8
[   23.544000] Clocksource tsc unstable (delta = -187411584 ns)
[   26.924000] NET: Registered protocol family 17
[   33.104000] NET: Registered protocol family 10
[   33.104000] lo: Disabled Privacy Extensions
[   33.104000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.828000] eth1: no IPv6 routers present
[  164.776000] usb 2-6: new high speed USB device using ehci_hcd and address 3
[  164.908000] usb 2-6: configuration #1 chosen from 1 choice
[  164.908000] scsi5 : SCSI emulation for USB Mass Storage devices
[  164.908000] usb-storage: device found at 3
[  164.908000] usb-storage: waiting for device to settle before scanning
[  169.908000] usb-storage: device scan complete
[  175.520000] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  185.764000] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  202.008000] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  202.256000] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  212.500000] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  212.632000] scsi 5:0:0:0: scsi: Device offlined - not ready after error recovery

---

### Post by eternicode on 2008-04-10
o_0 hm.

For starters, try using the method found at [http://obsidianlake.blogspot.com/2007/09/reset-high-speed-usb-device.html](http://obsidianlake.blogspot.com/2007/09/reset-high-speed-usb-device.html) .  If that doesn't work, you can re-enable the USB2 module by running "sudo modprobe ehci-hcd".

If that doesn't work, I'm not sure what could be the problem....

---

### Post by y-aji on 2008-04-10
> **KCormier said:**
> If you use it on xp machines as well make sure you safely remove the drive before sticking it into an ubuntu machine.  If the drive isn't safely removed, the previous mount isn't properly unmounted, and you must FORCE ubuntu to mount the drive.  It's a security thing because not properly removing media can result in data corruption so it doesn't automatically mount anything that's been removed incorrectly!  Try putting it in the xp machine and then safely removing it (with the little green arrow down by the clock! wait till it says "safe to remove hardware")

-Kevin

Yeah, I did this yesterday, and can confirm that you definately HAVE to disconnect safely on xp on certain items for it to connect properly to something non-windows..

---

### Post by gilbre on 2008-04-10
Thanks for your replies.  I just used XP to remove the drive correctly.  That didn't work..  So I tried to reformat it, remove it properly and then tried again.  Nothing.  So I tried disabling usb2 and that didn't work so I enabled it again.  It still recognizes all of my other drives just fine just not this particular USB flash drive....  ????

I am totally stumped!  I guess that is part of the fun though eh?!

---

### Post by |{urse on 2008-04-10
> **y-aji said:**
> Yeah, I did this yesterday, and can confirm that you definately HAVE to disconnect safely on xp on certain items for it to connect properly to something non-windows..

and the same applies for linux, thats why the 

sync

command is so important.

---

### Post by eternicode on 2008-04-11
Well, all else fails, check for errors (though I can't imagine why there would be errors on a newly formatted drive).

Assuming it's FAT32 formatted, make sure it's unmounted (shouldn't be a problem in your case), then run:
```
sudo fsck.vfat -afvw /dev/sdaX
```

fsck (**F**ile**s**ystem **C**hec**k**) is the linux equivalent of chkdsk.

If that doesn't work, sounds like a hardware issue :p

---

### Post by buried on 2008-04-11
Are you sure you didn't mount it with a / mount point?

---

