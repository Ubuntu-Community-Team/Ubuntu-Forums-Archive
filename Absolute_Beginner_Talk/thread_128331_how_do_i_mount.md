---
title: "how do i mount"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by souteneur3190 on 2006-02-11
i did a ls for my usb ports on my computer and it detected my mp3 LG cell phone.  How do i mount it?

---

### Post by taurus on 2006-02-11
I believe the kernel sees your usb device as /dev/sda1 so

sudo mkdir /mnt/usb
sudo mount /dev/sda1 /mnt/usb

---

### Post by souteneur3190 on 2006-02-11
I get an error

mount: you must specify the filesystem type

wuts wront now

---

### Post by atoponce on 2006-02-11
Double-check that your MP3 LG phone is listed.  Run:

```
sudo fdisk -l
``` 
Find your phone (probably /dev/sda1) then you will need to create a dirctory first, before you can mount it.  Try:

```
sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb
``` 
That *should* work.

---

### Post by souteneur3190 on 2006-02-11
[COLOR="Red"]Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 100 MB, 100646912 bytes
64 heads, 32 sectors/track, 95 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?      937477     1203315   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(937476, 3, 15)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(1203314, 30, 19)
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?      649505      912677   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(649504, 0, 11)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(912676, 1, 10)
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?      263179      945973   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(263178, 26, 16)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(945972, 51, 15)
Partition 3 does not end on cylinder boundary.
/dev/hdb4   *      680971      680981       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(680970, 34, 16)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(680980, 61, 8)
Partition 4 does not end on cylinder boundary[/COLOR].

Partition table entries are not in disk order
malubankudi@Tobuntu:~$

I can see that that diddnt work, but is see my phone listed in the device manger

---

### Post by atoponce on 2006-02-11
Okay.  How is it listed in the device manager?

---

### Post by souteneur3190 on 2006-02-11
erm i have no idea what to look for
info bus: usb_device?

---

### Post by Lord Illidan on 2006-02-11
Could it be that it is already mounted?

Check in /media

Also, do a ```
dmesg
``` and post the output here.

---

### Post by souteneur3190 on 2006-02-11
[QUOTE=Lord Illidan]Could it be that it is already mounted?

Check in /media

Also, do a ```
dmesg
``` and post the output here.[/QUOTE]

I see usb in the media but its only a folder and as for that command.....

00000000 00000000 00000000
[4294668.357000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.357000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294668.357000] CPU: L2 cache: 512K
[4294668.357000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[4294668.357000] CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[4294668.357000] Enabling fast FPU save and restore... done.
[4294668.357000] Enabling unmasked SIMD FPU exception support... done.
[4294668.357000] Checking 'hlt' instruction... OK.
[4294668.361000] Checking for popad bug... OK.
[4294668.361000] checking if image is initramfs... it is
[4294668.957000] Freeing initrd memory: 5172k freed
[4294668.963000] ACPI: Looking for DSDT in initrd... not found!
[4294669.033000]  not found!
[4294669.068000] ENABLING IO-APIC IRQs
[4294669.069000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.179000] NET: Registered protocol family 16
[4294669.179000] EISA bus registered
[4294669.179000] ACPI: bus type pci registered
[4294669.192000] PCI: PCI BIOS revision 2.10 entry at 0xfbe74, last bus=2
[4294669.192000] PCI: Using configuration type 1
[4294669.192000] mtrr: v2.0 (20020519)
[4294669.193000] ACPI: Subsystem revision 20050729
[4294669.231000] ACPI: Interpreter enabled
[4294669.231000] ACPI: Using IOAPIC for interrupt routing
[4294669.236000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.236000] PCI: Probing PCI hardware (bus 00)
[4294669.236000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.236000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.250000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.250000] Boot video device is 0000:02:02.0
[4294669.250000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.288000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.295000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294669.315000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294669.316000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294669.317000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294669.317000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294669.318000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294669.319000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294669.320000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294669.321000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)[4294669.321000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.321000] pnp: PnP ACPI init
[4294669.351000] pnp: PnP ACPI: found 11 devices
[4294669.351000] PnPBIOS: Disabled by ACPI PNP
[4294669.351000] PCI: Using ACPI for IRQ routing
[4294669.351000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.367000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[4294669.367000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[4294669.367000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[4294669.367000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[4294669.367000] Simple Boot Flag at 0x7a set to 0x1
[4294669.368000] audit: initializing netlink socket (disabled)
[4294669.368000] audit: initialized
[4294669.368000] highmem bounce pool size: 64 pages
[4294669.368000] VFS: Disk quotas dquot_6.5.1
[4294669.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.368000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.368000] devfs: boot_options: 0x0
[4294669.368000] Initializing Cryptographic API
[4294669.368000] isapnp: Scanning for PnP cards...
[4294669.722000] isapnp: No Plug & Play device found
[4294669.742000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294669.746000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.747000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.747000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.747000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.749000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.749000] io scheduler noop registered
[4294669.749000] io scheduler anticipatory registered
[4294669.749000] io scheduler deadline registered
[4294669.749000] io scheduler cfq registered
[4294669.750000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.751000] EISA: Probing bus 0 at eisa.0
[4294669.751000] EISA: Detected 0 cards.
[4294669.751000] NET: Registered protocol family 2
[4294669.762000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.762000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294669.765000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.766000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.766000] NET: Registered protocol family 8
[4294669.766000] NET: Registered protocol family 20
[4294669.766000] ACPI wakeup devices:
[4294669.766000] VBTN PCI0 USB0 USB1 USB2 PCI1  KBD
[4294669.766000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.767000] Freeing unused kernel memory: 224k freed
[4294669.779000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.791000] vga16fb: initializing
[4294669.791000] vga16fb: mapped to 0xc00a0000
[4294669.858000] Console: switching to colour frame buffer device 80x30
[4294669.858000] fb0: VGA16 VGA frame buffer device
[4294671.026000] Capability LSM initialized
[4294671.042000] NET: Registered protocol family 1
[4294671.061000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.061000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.061000] ACPI: bus type ide registered
[4294671.069000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294671.069000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.069000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294671.069000] ICH4: chipset revision 1
[4294671.069000] ICH4: not 100% native mode: will probe irqs later
[4294671.069000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294671.069000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294671.069000] Probing IDE interface ide0...
[4294671.333000] hda: ST320011A, ATA DISK drive
[4294671.741000] hdb: IOMEGA ZIP 250 ATAPI Floppy, ATAPI FLOPPY drive
[4294671.792000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.792000] Probing IDE interface ide1...
[4294672.158000] hdc: Lite-On LTN486S 48x Max, ATAPI CD/DVD-ROM drive
[4294672.464000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.464000] Probing IDE interface ide2...
[4294672.977000] Probing IDE interface ide3...
[4294673.489000] Probing IDE interface ide4...
[4294674.001000] Probing IDE interface ide5...
[4294674.518000] hda: max request size: 128KiB
[4294674.518000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[4294674.518000] hda: cache flushes not supported
[4294674.518000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294674.562000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache
[4294674.562000] Uniform CD-ROM driver Revision: 3.20
[4294674.930000] Attempting manual resume
[4294674.930000] swsusp: Suspend partition has wrong signature?
[4294674.960000] usbcore: registered new driver usbfs
[4294674.960000] usbcore: registered new driver hub
[4294674.961000] USB Universal Host Controller Interface driver v2.2
[4294674.961000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294674.961000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.961000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294675.023000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.023000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[4294675.023000] hub 1-0:1.0: USB hub found
[4294675.023000] hub 1-0:1.0: 2 ports detected
[4294675.026000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294675.026000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.026000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294675.088000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.088000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[4294675.088000] hub 2-0:1.0: USB hub found
[4294675.088000] hub 2-0:1.0: 2 ports detected
[4294675.091000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294675.091000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.091000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294675.153000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.153000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[4294675.153000] hub 3-0:1.0: USB hub found
[4294675.153000] hub 3-0:1.0: 2 ports detected
[4294675.184000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294675.184000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.184000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294675.184000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.184000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.184000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe100800
[4294675.188000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294675.188000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.189000] hub 4-0:1.0: USB hub found
[4294675.189000] hub 4-0:1.0: 6 ports detected
[4294675.275000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294675.275000] 8139cp: pci dev 0000:02:01.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294675.275000] 8139cp: Try the "8139too" driver instead.
[4294675.277000] 8139too Fast Ethernet driver 0.9.27
[4294675.277000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294675.277000] eth0: RealTek RTL8139 at 0xe400, 00:e0:7d:f7:46:f6, IRQ 22
[4294675.277000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294675.299000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294675.299000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294675.299000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294675.322000] e100: eth1: e100_probe: addr 0xfdefe000, irq 20, MAC addr 00:07:E9:B1:CE:97
[4294677.890000] ACPI: CPU0 (power states: C1[C1])
[4294678.102000] Attempting manual resume
[4294678.103000] swsusp: Suspend partition has wrong signature?
[4294678.113000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294678.113000] EXT3-fs: write access will be enabled during recovery.
[4294678.864000] kjournald starting.  Commit interval 5 seconds
[4294678.864000] EXT3-fs: hda1: orphan cleanup on readonly fs
[4294678.864000] ext3_orphan_cleanup: deleting unreferenced inode 1556624
[4294678.864000] ext3_orphan_cleanup: deleting unreferenced inode 1556496
[4294678.864000] EXT3-fs: hda1: 2 orphan inodes deleted
[4294678.864000] EXT3-fs: recovery complete.
[4294678.890000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.433000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.449000] Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1
[4294684.768000] EXT3 FS on hda1, internal journal
[4294691.454000] parport: PnPBIOS parport detected.
[4294691.454000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294691.540000] lp0: using parport0 (interrupt-driven).
[4294691.583000] mice: PS/2 mouse device common for all mice
[4294691.966000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294692.445000] ts: Compaq touchscreen protocol output
[4294695.547000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294696.604000] cdrom: open failed.
[4294698.836000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.849000] agpgart: Detected an Intel 845G Chipset.
[4294698.878000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294698.988000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294698.995000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.995000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294699.375000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294699.375000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294699.480000] hw_random hardware driver 1.0.0 loaded
[4294700.078000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294700.078000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294700.388000] intel8x0_measure_ac97_clock: measured 49975 usecs
[4294700.388000] intel8x0: clocking to 48000
[4294703.168000] input: PC Speaker
[4294703.227000] Real Time Clock Driver v1.12
[4294703.320000] Floppy drive(s): fd0 is 1.44M
[4294703.340000] FDC 0 is a post-1991 82077
[4294703.806000] ide-floppy driver 0.99.newide
[4294703.879000] hdb: 98288kB, 196576 blocks, 512 sector size
[4294703.882000] hdb: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[4294703.927000]  /dev/ide/host0/bus0/target1/lun0: unknown partition table
[4294704.837000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294704.851000] NET: Registered protocol family 17
[4294708.581000] NET: Registered protocol family 10
[4294708.582000] Disabled Privacy Extensions on device c02eb280(lo)
[4294708.582000] IPv6 over IPv4 tunneling driver
[4294710.332000] ACPI: Power Button (FF) [PWRF]
[4294710.332000] ACPI: Power Button (CM) [VBTN]
[4294710.484000] ibm_acpi: ec object not found
[4294719.261000] eth0: no IPv6 routers present
[4294721.007000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294721.007000] apm: overridden by ACPI.
[4294722.360000] Bluetooth: Core ver 2.7
[4294722.360000] NET: Registered protocol family 31
[4294722.360000] Bluetooth: HCI device and connection manager initialized
[4294722.360000] Bluetooth: HCI socket layer initialized
[4294722.434000] Bluetooth: L2CAP ver 2.7
[4294722.434000] Bluetooth: L2CAP socket layer initialized
[4294722.468000] Bluetooth: RFCOMM ver 1.5
[4294722.468000] Bluetooth: RFCOMM socket layer initialized
[4294722.468000] Bluetooth: RFCOMM TTY layer initialized
[4334714.008000] usb 2-1: new full speed USB device using uhci_hcd and address 2[4334714.456000] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[4334714.471000] usbcore: registered new driver cdc_acm
[4334714.471000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
[4334739.415000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4334956.975000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4334961.810000] cdrom: This disc doesn't have any tracks I recognize!
[4334967.514000] cdrom: This disc doesn't have any tracks I recognize!
[4336484.521000] hdb: 244736kB, 239/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[4336484.521000]  /dev/ide/host0/bus0/target1/lun0: unknown partition table
[4336486.896000] hdb: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[4336486.897000]  /dev/ide/host0/bus0/target1/lun0: unknown partition table
[4336717.788000]  /dev/ide/host0/bus0/target1/lun0: unknown partition table
[4336718.748000]  /dev/ide/host0/bus0/target1/lun0: unknown partition table
malubankudi@Tobuntu:~$ dmesg

---

### Post by bartbes on 2006-02-11
[quote=taurus]sudo mkdir /mnt/usb
sudo mount /dev/sda1 /mnt/usb[/quote] it asks for an filesystem so I would say: ```
sudo mount /dev/sda1 /mnt/usb **-t usbfs**
``` or maybe if you have pmount this also works ```
pmount /dev/sda1
```

---

### Post by souteneur3190 on 2006-02-11
root@Tobuntu:~# sudo mount /dev/sda1 /mnt/usb -t usbfs
mount: /dev/sda1 already mounted or /mnt/usb busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/usb

If it is already mounted, how do i browse the contents of the phone like i would on windows

---

### Post by bartbes on 2006-02-11
as easy as ```
cd /mnt/usb
``` because it's mounted there

---

### Post by souteneur3190 on 2006-02-11
when i open mt/usb folders i see the following folders

001 002 003 004, and in them is 1 file that cant be accessed

---

### Post by saphire_2001 on 2006-03-31
Here's what I would try.
I would look up the device name. [user@host ~$ sudo fdisk -l]
then I would try to have it detect the type [user@host ~$ sudo mount -tauto /dev/<insert device name here> /media/mnt]
After it is mounted you should be able to browse from your filesystem (Places/Computers/Filesystem on your gnome menu) and see what's in /mnt.  If you want to see what is mounted type sudo mount
Without any arguments it will show you what you have mounted.

---

### Post by Scunizi on 2006-04-01
I found out how to make it all work.....in my case anyway.  [See my post (#5) here]("http://www.ubuntuforums.org/showthread.php?t=152362&highlight=usb").....

---

