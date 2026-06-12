---
title: "searching for mounting devices drives (multi card reader)"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-12
I have searched google and came up with this for help on mounting

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

and this for explaing the fstab file 

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

My question is more basic.  (Please feel free to answer with a link to the manual/thread that deals with this.  I am sure it is there, but I have missed it in my searching.  I remember reading something about it in the ubuntu web pages someplace but can't locate it again.)

Anyway, my question:  How do I search for the mountable devices?  I have an internal multi - card reader (for digital camera) it also has a USB port.  There are 5 slots, 6 with the USB. (Some of the slots look like I can insert more than one size card.)

The devices are not mounted and I don't even know where to begin looking for them.  Here is some information on my system that may help someone point me in the right dirction.

My /etc/fstab file looks like this (why is swap not mounted???)
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```
df -h
```

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             6.1G  2.6G  3.3G  44% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile


my /dev folder has about a hundred different files.  Please point me in the right direction.  I like working from the Command Line in that I hope it will help me to eventually understand what is going on.  I also do not mind reading threads or other web pages, but am kind of stuck.
[edit:  I am also kind of slow, but I am trying real hard to understand all of this new information.  I appreciate the patience of the ubuntu community.]

---

### Post by bountonw on 2006-02-12
I should also have said that there is nothing in my /mnt directory.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=bountonw]I have searched google and came up with this for help on mounting

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

and this for explaing the fstab file 

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

My question is more basic.  (Please feel free to answer with a link to the manual/thread that deals with this.  I am sure it is there, but I have missed it in my searching.  I remember reading something about it in the ubuntu web pages someplace but can't locate it again.)

Anyway, my question:  How do I search for the mountable devices?  I have an internal multi - card reader (for digital camera) it also has a USB port.  There are 5 slots, 6 with the USB. (Some of the slots look like I can insert more than one size card.)

The devices are not mounted and I don't even know where to begin looking for them.  Here is some information on my system that may help someone point me in the right dirction.

My /etc/fstab file looks like this (why is swap not mounted???)


```
df -h
```



my /dev folder has about a hundred different files.  Please point me in the right direction.  I like working from the Command Line in that I hope it will help me to eventually understand what is going on.  I also do not mind reading threads or other web pages, but am kind of stuck.
[edit:  I am also kind of slow, but I am trying real hard to understand all of this new information.  I appreciate the patience of the ubuntu community.][/QUOTE]

For hot-pluggable devices that don't get mounted automatically, the best thing at this point is to plug in the device and type the following command in the terminal:
```

$ dmesg

```
If the system detects your device, it creates a device file for it (something like /dev/<devicename>).  The name of the device shows up in the output from dmesg.  For example when I plug in my flash drive:
```

[4300972.920000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4300973.307000] Initializing USB Mass Storage driver...
[4300973.324000] scsi2 : SCSI emulation for USB Mass Storage devices
[4300973.347000] usb-storage: device found at 2
[4300973.347000] usb-storage: waiting for device to settle before scanning
[4300973.348000] usbcore: registered new driver usb-storage
[4300973.348000] USB Mass Storage support registered.
[4300978.350000]   Vendor: VIKING    Model: USB FLASH DRIVE   Rev: 1.10
[4300978.350000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
[4300978.366000] **SCSI device sdb: 125952 512-byte hdwr **sectors (64 MB)
[4300978.370000] sdb: Write Protect is off
[4300978.370000] sdb: Mode Sense: 23 00 00 00
[4300978.370000] sdb: assuming drive cache: write through
[4300978.412000] SCSI device sdb: 125952 512-byte hdwr sectors (64 MB)
[4300978.416000] sdb: Write Protect is off
[4300978.416000] sdb: Mode Sense: 23 00 00 00
[4300978.416000] sdb: assuming drive cache: write through
[4300978.416000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4300978.434000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4300978.452000] usb-storage: device scan complete

```
As you can see, there is a lot of mention about device "sdb".  Since the drive has a single partition, the device file created for it is "/dev/sdb1".

Hope that helps.

---

### Post by eriefisher on 2006-02-12
You won't see anything untill you actually plug in a usb device or slide in a card. When you plug something in it will probably show up on you desk top as a drive. From there you can mount it and use it.

eriefisher

---

### Post by bountonw on 2006-02-12
My problem is that the muti card reader is internal and I can't unplug it and plug it back in.  (I also have windows drives as I dual boot, and I though I had alloted more space to my linux install, but don't see it.  I would like to understand how to look for these devices and drives so that I can mount/unmount them.

Doing dmesg gets the following.  
> 0] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294670.428000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294670.430000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.430000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.430000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.433000] io scheduler noop registered
[4294670.433000] io scheduler anticipatory registered
[4294670.433000] io scheduler deadline registered
[4294670.433000] io scheduler cfq registered
[4294670.433000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294670.433000] EISA: Probing bus 0 at eisa.0
[4294670.433000] Cannot allocate resource for EISA slot 8
[4294670.433000] EISA: Detected 0 cards.
[4294670.433000] NET: Registered protocol family 2
[4294670.442000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.442000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294670.442000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.442000] TCP: Hash tables configured (established 32768 bind 32768)
[4294670.442000] NET: Registered protocol family 8
[4294670.442000] NET: Registered protocol family 20
[4294670.442000] ACPI wakeup devices:
[4294670.442000] P0P1 P0P3 BNIC P0P4 P0P5 P0P6 P0P7 PS2K USB1 USB2 USB3 USB4 EUSB MC97
[4294670.442000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.442000] Freeing unused kernel memory: 224k freed
[4294670.455000] vga16fb: initializing
[4294670.455000] vga16fb: mapped to 0xc00a0000
[4294670.582000] Console: switching to colour frame buffer device 80x30
[4294670.582000] fb0: VGA16 VGA frame buffer device
[4294670.602000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.733000] Capability LSM initialized
[4294671.742000] NET: Registered protocol family 1
[4294671.755000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.755000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294671.755000] ACPI: bus type ide registered
[4294671.764000] SCSI subsystem initialized
[4294671.765000] libata version 1.11 loaded.
[4294671.766000] ata_piix version 1.03
[4294671.766000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294671.766000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.766000] ata1: SATA max UDMA/133 cmd 0x9400 ctl 0x9002 bmdma 0x8000 irq19
[4294671.766000] ata2: SATA max UDMA/133 cmd 0x8800 ctl 0x8402 bmdma 0x8008 irq19
[4294671.920000] ata1: dev 0 cfg 49:2f00 82:3069 83:7d01 84:4023 85:3069 86:3c01 87:4023 88:203f
[4294671.920000] ata1: dev 0 ATA, max UDMA/100, 312581808 sectors: lba48
[4294671.920000] ata1: dev 0 configured for UDMA/100
[4294671.920000] scsi0 : ata_piix
[4294672.081000] ATA: abnormal status 0x7F on port 0x8807
[4294672.081000] ata2: disabling port
[4294672.081000] scsi1 : ata_piix
[4294672.081000]   Vendor: ATA       Model: ST3160023AS       Rev: 3.43
[4294672.081000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294672.086000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294672.086000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294672.086000] ICH6: chipset revision 3
[4294672.086000] ICH6: not 100% native mode: will probe irqs later
[4294672.086000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294672.086000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[4294672.086000] Probing IDE interface ide0...
[4294672.758000] hda: HL-DT-STDVDRRW GWA-4164B, ATAPI CD/DVD-ROM drive
[4294673.071000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.071000] Probing IDE interface ide1...
[4294673.589000] Probing IDE interface ide1...
[4294674.107000] Probing IDE interface ide2...
[4294674.619000] Probing IDE interface ide3...
[4294675.131000] Probing IDE interface ide4...
[4294675.643000] Probing IDE interface ide5...
[4294676.160000] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294676.160000] Uniform CD-ROM driver Revision: 3.20
[4294676.174000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.174000] SCSI device sda: drive cache: write back
[4294676.174000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.174000] SCSI device sda: drive cache: write back
[4294676.174000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 p8 > p3
[4294676.255000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294676.485000] Attempting manual resume
[4294676.485000] swsusp: Suspend partition has wrong signature?
[4294676.515000] usbcore: registered new driver usbfs
[4294676.516000] usbcore: registered new driver hub
[4294676.516000] USB Universal Host Controller Interface driver v2.2
[4294676.516000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294676.516000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.516000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB UHCI #1
[4294676.578000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.578000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009800
[4294676.578000] hub 1-0:1.0: USB hub found
[4294676.578000] hub 1-0:1.0: 2 ports detected
[4294676.581000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294676.581000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.581000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB UHCI #2
[4294676.643000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.643000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a000
[4294676.643000] hub 2-0:1.0: USB hub found
[4294676.643000] hub 2-0:1.0: 2 ports detected
[4294676.646000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294676.646000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.646000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB UHCI #3
[4294676.708000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.708000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
[4294676.708000] hub 3-0:1.0: USB hub found
[4294676.708000] hub 3-0:1.0: 2 ports detected
[4294676.711000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294676.711000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294676.711000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB UHCI #4
[4294676.747000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294676.773000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294676.773000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a800
[4294676.773000] hub 4-0:1.0: USB hub found
[4294676.773000] hub 4-0:1.0: 2 ports detected
[4294676.799000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294676.800000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.800000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB2 EHCI Controller
[4294676.800000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.800000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294676.800000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd7dfbc00
[4294676.803000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294676.803000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.804000] hub 5-0:1.0: USB hub found
[4294676.804000] hub 5-0:1.0: 8 ports detected
[4294676.877000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294676.877000] 8139cp: pci dev 0000:03:02.0 (id 10ec:8139 rev 10) is not an 81 39C+ compatible chip
[4294676.877000] 8139cp: Try the "8139too" driver instead.
[4294676.879000] 8139too Fast Ethernet driver 0.9.27
[4294676.879000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294676.879000] eth0: RealTek RTL8139 at 0xe400, 00:13:d4:a9:b3:ed, IRQ 21
[4294676.879000] eth0:  Identified 8139 chip type 'RTL-8101'
[4294677.384000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294677.652000] usb 4-1: new full speed USB device using uhci_hcd and address 2[4294678.899000] usbcore: registered new driver hiddev
[4294678.916000] input: USB HID v1.10 Mouse [062a:0000] on usb-0000:00:1d.0-2
[4294678.916000] usbcore: registered new driver usbhid
[4294678.916000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.940000] Initializing USB Mass Storage driver...
[4294678.942000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294678.942000] usb-storage: device found at 2
[4294678.942000] usb-storage: waiting for device to settle before scanning
[4294678.942000] usbcore: registered new driver usb-storage
[4294678.942000] USB Mass Storage support registered.
[4294679.426000] ACPI: CPU0 (power states: C1[C1])
[4294679.426000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294679.675000] Attempting manual resume
[4294679.679000] swsusp: Suspend partition has wrong signature?
[4294679.694000] kjournald starting.  Commit interval 5 seconds
[4294679.694000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.581000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.704000] Adding 313228k swap on /dev/sda8.  Priority:-1 extents:1
[4294683.942000] EXT3 FS on sda3, internal journal
[4294683.946000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294683.946000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.969000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4294683.973000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294683.973000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.988000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 1
[4294683.992000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294683.992000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.007000] Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 2
[4294684.011000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294684.011000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.026000] Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 3
[4294684.027000] usb-storage: device scan complete
[4294690.531000] parport: PnPBIOS parport detected.
[4294690.531000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294690.616000] lp0: using parport0 (interrupt-driven).
[4294690.657000] mice: PS/2 mouse device common for all mice
[4294690.708000] ieee1394: Initialized config rom entry `ip1394'
[4294690.712000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294693.477000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294696.647000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.654000] agpgart: Detected an Intel 915G Chipset.
[4294696.684000] agpgart: AGP aperture is 256M @ 0x0
[4294696.747000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294696.756000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294696.893000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294696.893000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294697.943000] hw_random hardware driver 1.0.0 loaded
[4294698.225000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294698.225000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294698.282000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d7fff800-d7ffffff]  Max Packet=[2048]
[4294699.548000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800005b3432][4294699.886000] Real Time Clock Driver v1.12
[4294699.929000] input: PC Speaker
[4294700.326000] ts: Compaq touchscreen protocol output
[4294700.985000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294700.993000] NET: Registered protocol family 17
[4294707.913000] ACPI: Power Button (FF) [PWRF]
[4294707.913000] ACPI: Power Button (CM) [PWRB]
[4294707.999000] ibm_acpi: ec object not found
[4294709.952000] cdrom: This disc doesn't have any tracks I recognize!
[4294717.630000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294717.630000] apm: overridden by ACPI.
[4294718.135000] Bluetooth: Core ver 2.7
[4294718.135000] NET: Registered protocol family 31
[4294718.135000] Bluetooth: HCI device and connection manager initialized
[4294718.135000] Bluetooth: HCI socket layer initialized
[4294718.149000] Bluetooth: L2CAP ver 2.7
[4294718.149000] Bluetooth: L2CAP socket layer initialized
[4294718.167000] Bluetooth: RFCOMM ver 1.5
[4294718.167000] Bluetooth: RFCOMM socket layer initialized
[4294718.167000] Bluetooth: RFCOMM TTY layer initialized
[4294936.747000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294936.747000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294936.825000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4294936.825000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294936.905000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294936.905000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294936.975000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4294936.975000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294937.016000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294937.016000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294937.141000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4294937.141000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295873.321000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295873.321000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295873.388000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295873.388000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295961.595000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295961.595000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295961.672000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295961.672000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295963.554000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295963.554000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295963.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295963.648000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296349.032000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296349.032000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296349.122000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296349.122000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296818.525000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296818.525000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296818.602000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296818.602000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


[edit:  I forgot to disable smilies and now have smilies in the code.  Sorry.]

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=bountonw]My problem is that the muti card reader is internal and I can't unplug it and plug it back in.  (I also have windows drives as I dual boot, and I though I had alloted more space to my linux install, but don't see it.  I would like to understand how to look for these devices and drives so that I can mount/unmount them.

Doing dmesg gets the following.  


[edit:  I forgot to disable smilies and now have smilies in the code.  Sorry.][/QUOTE]
Well, it helps to know what you do have in your system and how it is recognized.  For example, it I pipe your dmesg output thought grep and look for sda and sdb (some of the more common SCSI device names), I see:
```

[4294676.174000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.174000] SCSI device sda: drive cache: write back
[4294676.174000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.174000] SCSI device sda: drive cache: write back
[4294676.255000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294683.704000] Adding 313228k swap on /dev/sda8. Priority:-1 extents:1
[4294683.942000] EXT3 FS on sda3, internal journal

```
and 
```

[4294683.969000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0

```
Now, I might guess that one of these was your card reader, but you could actually have two SCSI drives in your PC.  Device sda looks like it has 160042 MB, so I am guessing it is *not* the card reader.  Device sdb has less inforamtion about it, so I am guessing it is the more likely candidate.

It is as much an art as a science, I think.

---

