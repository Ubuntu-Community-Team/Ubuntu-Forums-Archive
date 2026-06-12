---
title: "cant format new hard drive"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mad chey on 2007-10-02
ive tried both the command line and the gparted methods as per detailed in threads on this forum

gparted will partition the drive but wont format it (ive tried several diff formats too)

and the command line, i can get the list of the hdds in my pc, and the sdc is listed but when i ask for the id of it so that i can put that in fstab, it tells me that sdc doesnt exist

im baffled, ok its late but this just cant be right

any suggestions guys?


thanks

---

### Post by Pumalite on 2007-10-02
Do you have the Ubuntu Live CD?. If so, post:
sudo fdisk -lu
lshw

---

### Post by bodhi.zazen on 2007-10-02
odd ...

did you run gparted as root ? Is the disk mounted ?

What command did you use to format and what , if any , was the error message ?

---

### Post by shad0w_walker on 2007-10-02
You don't strictly need the ID of the drive to put it in fstab, its just the way Ubuntu does things so its easier to track drives when they get moved. It should work if you just use good old /dev/sdc1

P.S. Did you try to find the ID for /dev/sdc or /dev/sdc1?

The drive won't produce an ID but the partition (sdc1) will.

---

### Post by mad chey on 2007-10-03
ok, its very early in the morning and im just about to do a 600 mile road trip, but i will feedback what i can quickly

**gparted** - run as root, would not let it run without sudo in front of it

the error message was

An error occurred while applying the operations
the following operation could not be applied to disk
format /dev/sdc1 as ext3
see the details for more information

the details are as follows

GParted 0.2.5

Format /dev/sdc1 as ext3    ( ERROR )
     	
set partitiontype    ( ERROR )

ok, i tried to put the /dev/sdc1 into fstab like my old notes said (from when i started first using ubuntu) and got the following error message 

wrong fs type, bad option, bad superblock on /dev/sdc1, so im assuming, that is because its not formated

results of **dmesg**

[   32.863571] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   32.863851] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   32.865553] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.865559] pnp: PnP ACPI init
[   32.869086] pnp: PnP ACPI: found 14 devices
[   32.869089] PnPBIOS: Disabled by ACPI PNP
[   32.869116] PCI: Using ACPI for IRQ routing
[   32.869119] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.893421] NET: Registered protocol family 8
[   32.893423] NET: Registered protocol family 20
[   32.893704] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   32.893706] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   32.893708] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   32.893710] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   32.893712] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   32.893715] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   32.893849] PCI: Bridge: 0000:00:06.0
[   32.893850]   IO window: disabled.
[   32.893853]   MEM window: fb000000-fb0fffff
[   32.893854]   PREFETCH window: disabled.
[   32.893858] PCI: Bridge: 0000:00:0f.0
[   32.893859]   IO window: a000-afff
[   32.893861]   MEM window: f8000000-faffffff
[   32.893863]   PREFETCH window: e0000000-efffffff
[   32.893870] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   32.893876] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   32.893891] NET: Registered protocol family 2
[   32.932144] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.932262] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   32.932597] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   32.932786] TCP: Hash tables configured (established 131072 bind 65536)
[   32.932788] TCP reno registered
[   32.944183] checking if image is initramfs... it is
[   33.472808] Freeing initrd memory: 8055k freed
[   33.473047] audit: initializing netlink socket (disabled)
[   33.473055] audit(1191344598.248:1): initialized
[   33.473089] highmem bounce pool size: 64 pages
[   33.473124] VFS: Disk quotas dquot_6.5.1
[   33.473135] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.473169] io scheduler noop registered
[   33.473171] io scheduler anticipatory registered
[   33.473172] io scheduler deadline registered
[   33.473177] io scheduler cfq registered (default)
[   33.473298] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   33.473314] assign_interrupt_mode Found MSI capability
[   33.473316] Allocate Port Service[0000:00:0f.0:pcie00]
[   33.473380] isapnp: Scanning for PnP cards...
[   33.825637] isapnp: No Plug & Play device found
[   33.840314] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.840410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.840844] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.840985] mice: PS/2 mouse device common for all mice
[   33.841266] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.841382] input: Macintosh mouse button emulation as /class/input/input0
[   33.841400] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.841402] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.841514] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.842406] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.842410] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.842487] EISA: Probing bus 0 at eisa.0
[   33.842492] Cannot allocate resource for EISA slot 1
[   33.842506] EISA: Detected 0 cards.
[   33.872536] TCP cubic registered
[   33.872540] NET: Registered protocol family 1
[   33.872552] Using IPI Shortcut mode
[   33.872586] ACPI: (supports S0 S1 S4 S5)
[   33.872623]   Magic number: 11:489:86
[   33.872906] Freeing unused kernel memory: 328k freed
[   33.875098] Time: tsc clocksource has been installed.
[   33.883988] input: AT Translated Set 2 keyboard as /class/input/input1
[   35.051151] Capability LSM initialized
[   35.062295] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   35.150004] md: linear personality registered for level -1
[   35.152473] md: multipath personality registered for level -4
[   35.154874] md: raid0 personality registered for level 0
[   35.157565] md: raid1 personality registered for level 1
[   35.159935] raid5: automatically using best checksumming function: pIII_sse
[   35.177698]    pIII_sse  :  7109.000 MB/sec
[   35.177700] raid5: using function: pIII_sse (7109.000 MB/sec)
[   35.249648] raid6: int32x1   1029 MB/s
[   35.317573] raid6: int32x2   1045 MB/s
[   35.385486] raid6: int32x4    870 MB/s
[   35.453473] raid6: int32x8    651 MB/s
[   35.521354] raid6: mmxx1     1925 MB/s
[   35.589257] raid6: mmxx2     3573 MB/s
[   35.657208] raid6: sse1x1    1931 MB/s
[   35.725118] raid6: sse1x2    3228 MB/s
[   35.793048] raid6: sse2x1    3337 MB/s
[   35.860971] raid6: sse2x2    4524 MB/s
[   35.860972] raid6: using algorithm sse2x2 (4524 MB/s)
[   35.860975] md: raid6 personality registered for level 6
[   35.860976] md: raid5 personality registered for level 5
[   35.860978] md: raid4 personality registered for level 4
[   35.889635] md: raid10 personality registered for level 10
[   36.190433] usbcore: registered new interface driver usbfs
[   36.190449] usbcore: registered new interface driver hub
[   36.190464] usbcore: registered new device driver usb
[   36.190955] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.191212] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
[   36.191214] PCI: setting IRQ 5 as level-triggered
[   36.191217] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUBA] -> GSI 5 (level, low) -> IRQ 5
[   36.191225] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   36.191227] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   36.191338] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   36.191350] ohci_hcd 0000:00:02.0: irq 5, io mem 0xfb104000
[   36.223161] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   36.241367] ieee1394: Initialized config rom entry `ip1394'
[   36.266195] usb usb1: configuration #1 chosen from 1 choice
[   36.266216] hub 1-0:1.0: USB hub found
[   36.266225] hub 1-0:1.0: 10 ports detected
[   36.362614] Floppy drive(s): fd0 is 1.44M
[   36.368807] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[   36.368811] PCI: setting IRQ 10 as level-triggered
[   36.368814] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[   36.368822] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   36.368824] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   36.368839] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   36.368859] ehci_hcd 0000:00:02.1: debug port 1
[   36.368862] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   36.368868] ehci_hcd 0000:00:02.1: irq 10, io mem 0xfb105000
[   36.368874] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.368914] usb usb2: configuration #1 chosen from 1 choice
[   36.368928] hub 2-0:1.0: USB hub found
[   36.368933] hub 2-0:1.0: 10 ports detected
[   36.382546] FDC 0 is a post-1991 82077
[   36.476431] SCSI subsystem initialized
[   36.479771] libata version 2.20 loaded.
[   36.482137] sata_nv 0000:00:05.0: version 3.3
[   36.482378] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 11
[   36.482380] PCI: setting IRQ 11 as level-triggered
[   36.482384] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LSID] -> GSI 11 (level, low) -> IRQ 11
[   36.482397] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   36.482437] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001c400 irq 11
[   36.482453] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001c408 irq 11
[   36.482461] scsi0 : sata_nv
[   36.947814] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   36.957150] ata1.00: ata_hpa_resize 1: sectors = 488395055, hpa_sectors = 488397168
[   36.957154] ata1.00: Host Protected Area detected.
[   36.957155]      current size : 488395055 sectors (250058 MB)
[   36.957156]      native  size : 488397168 sectors (250059 MB)
[   36.959231] ata1.00: SET of native returned 486539294, expected 488397168
[   36.963875] ata1.00: Native size increased to 488397168 sectors
[   36.963877] ata1.00: ATA-6: WDC WD2500JD-00HBC0, 08.02D08, max UDMA/133
[   36.963879] ata1.00: 488397168 sectors, multi 16: LBA48 
[   36.973142] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   36.973144] ata1.00: configured for UDMA/133
[   36.973150] scsi1 : sata_nv
[   37.015728] usb 1-9: new full speed USB device using ohci_hcd and address 2
[   37.390899] usb 1-9: configuration #1 chosen from 1 choice
[   37.439298] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   37.447458] ata2.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   37.447462] ata2.00: ATA-7: SAMSUNG HD401LJ, ZZ100-15, max UDMA7
[   37.447464] ata2.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.455440] ata2.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   37.455442] ata2.00: configured for UDMA/133
[   37.455513] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
[   37.455857] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD401LJ  ZZ10 PQ: 0 ANSI: 5
[   37.456210] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 15
[   37.456213] PCI: setting IRQ 15 as level-triggered
[   37.456216] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [LFID] -> GSI 15 (level, low) -> IRQ 15
[   37.456231] PCI: Setting latency timer of device 0000:00:05.1 to 64
[   37.456255] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001d800 irq 15
[   37.456271] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001d808 irq 15
[   37.456279] scsi2 : sata_nv
[   37.922775] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   37.931827] ata3.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   37.931830] ata3.00: ATA-7: Maxtor 6V300F0, VA111900, max UDMA/133
[   37.931832] ata3.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.939831] ata3.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   37.939833] ata3.00: configured for UDMA/133
[   37.939838] scsi3 : sata_nv
[   38.250406] ata4: SATA link down (SStatus 0 SControl 300)
[   38.260582] ATA: abnormal status 0x7F on port 0x00010967
[   38.260647] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[   38.261979] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   38.261982] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   38.261987] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   38.261992] forcedeth: using HIGHDMA
[   38.273511] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   38.273529] sda: Write Protect is off
[   38.273531] sda: Mode Sense: 00 3a 00 00
[   38.273539] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.273571] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   38.273575] sda: Write Protect is off
[   38.273577] sda: Mode Sense: 00 3a 00 00
[   38.273583] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.273586]  sda: sda1
[   38.293317] sd 0:0:0:0: Attached scsi disk sda
[   38.293525] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   38.293530] sdb: Write Protect is off
[   38.293532] sdb: Mode Sense: 00 3a 00 00
[   38.293539] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.293558] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   38.293563] sdb: Write Protect is off
[   38.293564] sdb: Mode Sense: 00 3a 00 00
[   38.293571] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.293572]  sdb: sdb1
[   38.301420] sd 1:0:0:0: Attached scsi disk sdb
[   38.301645] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
[   38.301650] sdc: Write Protect is off
[   38.301652] sdc: Mode Sense: 00 3a 00 00
[   38.301659] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.301679] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
[   38.301684] sdc: Write Protect is off
[   38.301685] sdc: Mode Sense: 00 3a 00 00
[   38.301691] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.301693]  sdc: unknown partition table
[   38.306496] sd 2:0:0:0: Attached scsi disk sdc
[   38.309017] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.309030] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.309042] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   38.782092] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:08.0
[   38.782395] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[   38.782398] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNK3] -> GSI 11 (level, low) -> IRQ 11
[   38.832128] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fb004000-fb0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   38.832211] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[   38.832220] NFORCE-MCP55: chipset revision 161
[   38.832222] NFORCE-MCP55: not 100% native mode: will probe irqs later
[   38.832225] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling workaround.
[   38.832228] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[   38.832233]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   38.832240] Probing IDE interface ide0...
[   39.117547] hda: Maxtor 6Y080P0, ATA DISK drive
[   39.565065] hdb: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[   39.621849] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   39.640522] hda: max request size: 128KiB
[   39.646025] hda: Host Protected Area detected.
[   39.646027]  current capacity is 126529471 sectors (64783 MB)
[   39.646028]  native  capacity is 160086528 sectors (81964 MB)
[   39.664749] hda: Host Protected Area disabled.
[   39.664753] hda: 160086528 sectors (81964 MB) w/7936KiB Cache, CHS=65535/16/63
[   39.664898] hda: cache flushes supported
[   39.664928]  hda: hda1 hda2 hda3
[   39.715664] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   39.715670] Uniform CD-ROM driver Revision: 3.20
[   39.897829] kjournald starting.  Commit interval 5 seconds
[   39.897835] EXT3-fs: mounted filesystem with ordered data mode.
[   40.100540] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b87903]
[   50.660715] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.662094] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.744542] NET: Registered protocol family 17
[   51.187569] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   51.187592] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   51.239825] input: PC Speaker as /class/input/input2
[   51.313454] Bluetooth: Core ver 2.11
[   51.313496] NET: Registered protocol family 31
[   51.313498] Bluetooth: HCI device and connection manager initialized
[   51.313500] Bluetooth: HCI socket layer initialized
[   51.330708] parport: PnPBIOS parport detected.
[   51.330752] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   51.338633] Real Time Clock Driver v1.12ac
[   51.350648] Linux agpgart interface v0.102 (c) Dave Jones
[   51.609254] Bluetooth: HCI USB driver ver 2.9
[   51.621922] nvidia: module license 'NVIDIA' taints kernel.
[   52.007710] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   52.025243] usbcore: registered new interface driver hci_usb
[   52.405907] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 5
[   52.405910] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK6] -> GSI 5 (level, low) -> IRQ 5
[   52.405917] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   52.406079] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   52.756258] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 15
[   52.756262] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LAZA] -> GSI 15 (level, low) -> IRQ 15
[   52.756273] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   52.962640] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   53.197594] lp0: using parport0 (interrupt-driven).
[   53.317994] Adding 10482404k swap on /dev/disk/by-uuid/f8b4d31f-e6c4-4331-85bf-b8aae6ca167c.  Priority:-1 extents:1 across:10482404k
[   53.562457] EXT3 FS on hda1, internal journal
[   55.202104] kjournald starting.  Commit interval 5 seconds
[   55.202547] EXT3 FS on dm-2, internal journal
[   55.202550] EXT3-fs: mounted filesystem with ordered data mode.
[   55.222270] kjournald starting.  Commit interval 5 seconds
[   55.222275] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   55.222777] EXT3 FS on dm-3, internal journal
[   55.222780] EXT3-fs: mounted filesystem with ordered data mode.
[   55.247893] kjournald starting.  Commit interval 5 seconds
[   55.247900] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   55.248119] EXT3 FS on dm-4, internal journal
[   55.248122] EXT3-fs: mounted filesystem with ordered data mode.
[   55.349934] Adding 10482404k swap on /dev/disk/by-uuid/f8b4d31f-e6c4-4331-85bf-b8aae6ca167c.  Priority:-2 extents:1 across:10482404k
[   55.428585] NET: Registered protocol family 10
[   55.428643] lo: Disabled Privacy Extensions
[   60.688630] input: Power Button (FF) as /class/input/input4
[   60.691302] ACPI: Power Button (FF) [PWRF]
[   60.717470] input: Power Button (CM) as /class/input/input5
[   60.720133] ACPI: Power Button (CM) [PWRB]
[   60.732239] Using specific hotkey driver
[   60.760006] No dock devices found.
[   60.787050] ibm_acpi: ec object not found
[   60.864879] pcc_acpi: loading...
[   61.033681] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (version 2.00.00)
[   61.033715] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0xc
[   61.033717] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xe
[   61.033719] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x10
[   61.033720] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x10
[   61.033722] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[   66.404196] eth0: no IPv6 routers present
[   74.011901] ppdev: user-space parallel port driver
[   74.263535] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   74.263539] apm: overridden by ACPI.
[   79.609696] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   79.609700] vboxdrv: Successfully done.
[   47.304000] Time: acpi_pm clocksource has been installed.
[   47.580000] Bluetooth: L2CAP ver 2.8
[   47.580000] Bluetooth: L2CAP socket layer initialized
[   47.608000] Bluetooth: RFCOMM socket layer initialized
[   47.608000] Bluetooth: RFCOMM TTY layer initialized
[   47.608000] Bluetooth: RFCOMM ver 1.8
[   57.156000] eth0: no IPv6 routers present
[10219.112000] usb 2-8: new high speed USB device using ehci_hcd and address 3
[10219.244000] usb 2-8: configuration #1 chosen from 1 choice
[10220.304000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[10220.304000] usbcore: registered new interface driver usblp
[10220.304000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[10220.328000] usbcore: registered new interface driver libusual
[10220.360000] Initializing USB Mass Storage driver...
[10220.360000] scsi4 : SCSI emulation for USB Mass Storage devices
[10220.360000] usb-storage: device found at 3
[10220.360000] usb-storage: waiting for device to settle before scanning
[10220.360000] usbcore: registered new interface driver usb-storage
[10220.360000] USB Mass Storage support registered.
[10225.360000] usb-storage: device scan complete
[10225.360000] scsi 4:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[10225.372000] sd 4:0:0:0: Attached scsi removable disk sdd
[10225.372000] sd 4:0:0:0: Attached scsi generic sg3 type 0
[10257.680000] usb 2-8: USB disconnect, address 3
[10257.680000] drivers/usb/class/usblp.c: usblp0: removed
[10271.780000] usb 2-8: new high speed USB device using ehci_hcd and address 4
[10271.912000] usb 2-8: configuration #1 chosen from 1 choice
[10271.912000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[10272.100000] scsi5 : SCSI emulation for USB Mass Storage devices
[10272.100000] usb-storage: device found at 4
[10272.100000] usb-storage: waiting for device to settle before scanning
[10277.100000] usb-storage: device scan complete
[10277.100000] scsi 5:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[10277.112000] sd 5:0:0:0: Attached scsi removable disk sdd
[10277.112000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[10309.408000] usb 2-8: USB disconnect, address 4
[10309.408000] drivers/usb/class/usblp.c: usblp0: removed
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] sdd : READ CAPACITY failed.
[10309.408000] sdd : status=0, message=00, host=1, driver=00 
[10309.408000] sdd : sense not available. 
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] sdd: Write Protect is off
[10309.408000] sdd: Mode Sense: 00 00 00 00
[10309.408000] sdd: assuming drive cache: write through
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] sdd : READ CAPACITY failed.
[10309.408000] sdd : status=0, message=00, host=1, driver=00 
[10309.408000] sdd : sense not available. 
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10309.408000] sdd: Write Protect is off
[10309.408000] sdd: Mode Sense: 00 00 00 00
[10309.408000] sdd: assuming drive cache: write through
[10309.408000] scsi 5:0:0:0: rejecting I/O to dead device
[10322.988000] usb 2-8: new high speed USB device using ehci_hcd and address 5
[10323.120000] usb 2-8: configuration #1 chosen from 1 choice
[10323.120000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[10323.120000] scsi6 : SCSI emulation for USB Mass Storage devices
[10323.120000] usb-storage: device found at 5
[10323.120000] usb-storage: waiting for device to settle before scanning
[10328.120000] usb-storage: device scan complete
[10328.120000] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[10328.132000] sd 6:0:0:0: Attached scsi removable disk sdd
[10328.132000] sd 6:0:0:0: Attached scsi generic sg3 type 0
[10337.616000] usb 2-8: USB disconnect, address 5
[10337.616000] drivers/usb/class/usblp.c: usblp0: removed
[20947.020000] hdb: tray open
[20947.020000] end_request: I/O error, dev hdb, sector 0
[20947.020000] Buffer I/O error on device hdb, logical block 0
[20947.020000] Buffer I/O error on device hdb, logical block 1
[20947.020000] Buffer I/O error on device hdb, logical block 2
[20947.020000] Buffer I/O error on device hdb, logical block 3
[20947.020000] Buffer I/O error on device hdb, logical block 4
[20947.020000] Buffer I/O error on device hdb, logical block 5
[20947.020000] Buffer I/O error on device hdb, logical block 6
[20947.020000] Buffer I/O error on device hdb, logical block 7
[20947.020000] hdb: tray open
[20947.020000] end_request: I/O error, dev hdb, sector 0
[20947.020000] Buffer I/O error on device hdb, logical block 0
[20947.020000] hdb: tray open
[20947.020000] end_request: I/O error, dev hdb, sector 4
[20947.020000] Buffer I/O error on device hdb, logical block 1
[20947.024000] hdb: tray open
[20947.024000] end_request: I/O error, dev hdb, sector 0
[20947.024000] hdb: tray open
[20947.024000] end_request: I/O error, dev hdb, sector 4
[20947.024000] hdb: tray open
[20947.024000] end_request: I/O error, dev hdb, sector 0
[20947.024000] hdb: tray open
[20947.024000] end_request: I/O error, dev hdb, sector 4
[20947.028000] hdb: tray open
[20947.028000] end_request: I/O error, dev hdb, sector 0
[20947.028000] hdb: tray open
[20947.028000] end_request: I/O error, dev hdb, sector 4
[20947.028000] hdb: tray open
[20947.028000] end_request: I/O error, dev hdb, sector 0
[20947.028000] hdb: tray open
[20947.028000] end_request: I/O error, dev hdb, sector 4
[21530.712000] smb_add_request: request [f022cec0, mid=13] timed out!
[21560.840000] smb_add_request: request [f022cec0, mid=14] timed out!
[21624.488000] smb_add_request: request [ea46fe80, mid=15] timed out!
[21644.124000] smb_add_request: request [ea46f080, mid=16] timed out!
[21655.856000] smb_add_request: request [ea46fe80, mid=17] timed out!
[21658.104000] smb_add_request: request [ea46fd80, mid=18] timed out!
[21674.208000] smb_add_request: request [ea46f080, mid=19] timed out!
[21685.932000] smb_add_request: request [ea46fe80, mid=20] timed out!
[21688.224000] smb_add_request: request [ea46fd80, mid=21] timed out!
[21704.280000] smb_add_request: request [ea46f080, mid=22] timed out!
[21716.024000] smb_add_request: request [ea46fe80, mid=23] timed out!
[21751.340000] smb_add_request: request [eefe4ec0, mid=24] timed out!
[21751.376000] smb_add_request: request [eefe4dc0, mid=25] timed out!
[21769.000000] smb_add_request: request [eefe40c0, mid=26] timed out!
[21781.420000] smb_add_request: request [eefe4dc0, mid=27] timed out!
[21799.052000] smb_add_request: request [eefe40c0, mid=28] timed out!
[21811.444000] smb_add_request: request [eefe4dc0, mid=29] timed out!
[22278.904000] smb_add_request: request [de180e80, mid=30] timed out!
[22309.024000] smb_add_request: request [de180e80, mid=31] timed out!
[22339.080000] smb_add_request: request [de180e80, mid=32] timed out!
[22346.320000] smb_add_request: request [de180080, mid=33] timed out!
[22393.336000] smb_add_request: request [e6edcec0, mid=34] timed out!
[22401.468000] smb_add_request: request [e6edcdc0, mid=35] timed out!
[22483.016000] smb_add_request: request [f3277e80, mid=36] timed out!
[22513.076000] smb_add_request: request [f3277e80, mid=37] timed out!
[23434.036000] kjournald starting.  Commit interval 5 seconds
[23434.040000] EXT3 FS on hda3, internal journal
[23434.040000] EXT3-fs: recovery complete.
[23434.044000] EXT3-fs: mounted filesystem with ordered data mode.
[23434.064000] VFS: Can't find ext3 filesystem on dev sdc1.
[23450.068000] smb_add_request: request [e3cebec0, mid=39] timed out!
[47854.876000] smb_add_request: request [c59dde80, mid=40] timed out!
[47885.012000] smb_add_request: request [c59dde80, mid=41] timed out!
[48148.776000] smb_add_request: request [c3828ec0, mid=42] timed out!
[48340.812000] VFS: Can't find ext3 filesystem on dev sdc1.


sorry i know thats long

**sudo fdisk -l **results

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666   83  Linux

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3916    31455238+  83  Linux
/dev/hda2            8660        9964    10482412+  82  Linux swap / Solaris
/dev/hda3            3917        8659    38098147+  83  Linux

Partition table entries are not in disk order

**sudo vol_id -u /dev/sdc1**
/dev/sdc1: unknown volume type

 **sudo lshw -C disk**
  *-disk                  
       description: ATA Disk
       product: Maxtor 6Y080P0
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: YAR41BW0
       serial: Y21XW19E
       size: 76GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 29GB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 10236MB
          capabilities: primary nofs
     *-volume:2
          description: Linux filesystem partition
          physical id: 3
          bus info: ide@0.0,3
          logical name: /dev/hda3
          capacity: 36GB
          capabilities: primary
  *-cdrom
       description: DVD-RAM writer
       product: TSSTcorpCD/DVDW SH-S182D
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: SB04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdb
  *-disk:0
       description: SCSI Disk
       product: WDC WD2500JD-00H
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WCAL76962764
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 232GB
          capabilities: primary
  *-disk:1
       description: SCSI Disk
       product: SAMSUNG HD401LJ
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: ZZ10
       serial: S0HVJ1CLA08716
       size: 372GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@1:0.0.0,1
          logical name: /dev/sdb1
          capacity: 372GB
          capabilities: primary
  *-disk
       description: SCSI Disk
       product: Maxtor 6V300F0
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: VA11
       serial: V60VTHQG
       size: 279GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@2:0.0.0,1
          logical name: /dev/sdc1
          capacity: 279GB
          capabilities: primary

**lshw**
WARNING: you should run this program as super-user.
cheyenne                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1011MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 7
          bus info: cpu@0
          version: 15.11.2
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP55 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: ioport:1c00-1c3f ioport:1c80-1cbf irq:15
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fb104000-fb104fff irq:5
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-386 ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb
                description: Bluetooth wireless interface
                product: Bluetooth Dongle (HCI mode)
                vendor: Cambridge Silicon Radio, Ltd
                physical id: 9
                bus info: usb@1:9
                version: 19.58
                capabilities: bluetooth usb-2.00
                configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fb105000-fb1050ff irq:10
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-16-386 ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f000-f00f
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-disk
                product: Maxtor 6Y080P0
                vendor: Maxtor
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capacity: 76GB
           *-cdrom
                product: TSSTcorpCD/DVDW SH-S182D
                physical id: 1
                bus info: ide@0.1
                logical name: /dev/hdb
                capabilities: packet
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:c400-c40f iomemory:fb109000-fb109fff irq:11
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.1
          bus info: pci@00:05.1
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9e0-9e7 ioport:be0-be3 ioport:960-967 ioport:b60-b63 ioport:d800-d80f iomemory:fb10a000-fb10afff irq:15
     *-pci:0
          description: PCI bridge
          product: MCP55 PCI bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: a
             bus info: pci@01:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
             resources: iomemory:fb004000-fb0047ff iomemory:fb000000-fb003fff irq:11
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:fb100000-fb103fff irq:15
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a2
          serial: 00:16:e6:82:13:bf
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=192.168.0.69 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: iomemory:fb106000-fb106fff ioport:dc00-dc07 iomemory:fb107000-fb1070ff iomemory:fb108000-fb10800f irq:10
     *-pci:1
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver

[B]
sudo fdisk -lu[/B]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   488392064   244196001   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   781417664   390708801   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   586099394   293049666   83  Linux

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    62910539    31455238+  83  Linux
/dev/hda2       139106835   160071659    10482412+  82  Linux swap / Solaris
/dev/hda3        62910540   139106834    38098147+  83  Linux

Partition table entries are not in disk order

i think that covers all the questions you asked, but if not just let me know, thanks for your quick responses guys, check back with ya later

---

