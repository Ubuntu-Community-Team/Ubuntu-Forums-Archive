---
title: "Mounting"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by knightinarms on 2006-10-23
How is it possible to mount a data DVD and a secondary slave drive?

---

### Post by taurus on 2006-10-23
```

sudo mkdir /media/DVD
sudo mount -t iso9660 /dev/hdd /media/DVD

```

---

### Post by knightinarms on 2006-10-23
That didn't work:

[IMG]http://img55.imageshack.us/img55/3919/screenshotta9.png[/IMG]

The DVD has .avi files on it.

---

### Post by taurus on 2006-10-23
So "sudo mount /dev/hdc /media/DVD" (or even "sudo mount -t iso9660 /dev/hdc /media/DVD")doesn't work either?  What is the output of "dmesg |tail" then?

---

### Post by knightinarms on 2006-10-23
This is a copy and paste from terminal:

knightinarms@knightinarms-pc:~$ sudo mount /dev/hdc /media/DVD
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

knightinarms@knightinarms-pc:~$ sudo mount /dev/hdc /media/DVD
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

knightinarms@knightinarms-pc:~$

**_dmesg:_**

> [17179570.796000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.940000] NET: Registered protocol family 16
[17179570.940000] EISA bus registered
[17179570.940000] ACPI: bus type pci registered
[17179570.940000] PCI: PCI BIOS revision 2.10 entry at 0xfba6a, last bus=2
[17179570.940000] PCI: Using configuration type 1
[17179570.940000] ACPI: Subsystem revision 20051216
[17179570.964000] ACPI: Interpreter enabled
[17179570.964000] ACPI: Using IOAPIC for interrupt routing
[17179570.968000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.968000] PCI: Probing PCI hardware (bus 00)
[17179570.968000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.988000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179570.988000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179570.988000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.988000] Boot video device is 0000:01:00.0
[17179570.988000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.988000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.156000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.176000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179571.176000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179571.176000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179571.176000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179571.176000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179571.176000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179571.180000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179571.180000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179571.180000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.180000] pnp: PnP ACPI init
[17179571.208000] pnp: PnP ACPI: found 12 devices
[17179571.208000] PnPBIOS: Disabled by ACPI PNP
[17179571.208000] PCI: Using ACPI for IRQ routing
[17179571.208000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.220000] pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
[17179571.220000] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[17179571.220000] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[17179571.220000] PCI: Bridge: 0000:00:01.0
[17179571.220000]   IO window: d000-dfff
[17179571.220000]   MEM window: fe900000-feafffff
[17179571.220000]   PREFETCH window: d8000000-efffffff
[17179571.220000] PCI: Bridge: 0000:00:1e.0
[17179571.220000]   IO window: c000-cfff
[17179571.220000]   MEM window: fe700000-fe8fffff
[17179571.220000]   PREFETCH window: 50000000-500fffff
[17179571.220000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.220000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[17179571.220000] Simple Boot Flag at 0x7a set to 0x1
[17179571.220000] audit: initializing netlink socket (disabled)
[17179571.220000] audit(1161647998.220:1): initialized
[17179571.220000] highmem bounce pool size: 64 pages
[17179571.220000] VFS: Disk quotas dquot_6.5.1
[17179571.220000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.220000] Initializing Cryptographic API
[17179571.220000] io scheduler noop registered
[17179571.220000] io scheduler anticipatory registered
[17179571.220000] io scheduler deadline registered
[17179571.220000] io scheduler cfq registered
[17179571.220000] isapnp: Scanning for PnP cards...
[17179571.576000] isapnp: No Plug & Play device found
[17179571.592000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179571.596000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.596000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.596000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.596000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.596000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.596000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.596000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.600000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.600000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.600000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.600000] mice: PS/2 mouse device common for all mice
[17179571.600000] EISA: Probing bus 0 at eisa.0
[17179571.600000] EISA: Detected 0 cards.
[17179571.600000] NET: Registered protocol family 2
[17179571.624000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.636000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.636000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179571.636000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.636000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.636000] TCP reno registered
[17179571.636000] TCP bic registered
[17179571.636000] NET: Registered protocol family 1
[17179571.636000] NET: Registered protocol family 8
[17179571.636000] NET: Registered protocol family 20
[17179571.636000] Using IPI Shortcut mode
[17179571.636000] ACPI wakeup devices:
[17179571.636000] VBTN PCI0 USB0 USB1 USB2 USB3 PCI1  KBD
[17179571.636000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.636000] Freeing unused kernel memory: 288k freed
[17179571.688000] vga16fb: initializing
[17179571.688000] vga16fb: mapped to 0xc00a0000
[17179571.848000] Console: switching to colour frame buffer device 80x25
[17179571.848000] fb0: VGA16 VGA frame buffer device
[17179572.860000] Capability LSM initialized
[17179573.596000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179573.596000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179573.596000] ICH5: chipset revision 2
[17179573.596000] ICH5: not 100% native mode: will probe irqs later
[17179573.596000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179573.596000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179573.596000] Probing IDE interface ide0...
[17179573.884000] hda: WDC WD1600JB-00GVC0, ATA DISK drive
[17179574.164000] hdb: IC35L060AVV207-0, ATA DISK drive
[17179574.220000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.224000] Probing IDE interface ide1...
[17179574.960000] hdc: PIONEER DVD-RW DVR-111D, ATAPI CD/DVD-ROM drive
[17179575.408000] hdd: LITE-ON CD-RW SOHR-5238S, ATAPI CD/DVD-ROM drive
[17179575.464000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.472000] hda: max request size: 1024KiB
[17179575.492000] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[17179575.492000] hda: cache flushes supported
[17179575.492000]  hda: hda1 hda2 < hda5 >
[17179575.536000] hdb: max request size: 1024KiB
[17179575.548000] hdb: 78125000 sectors (40000 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.552000] hdb: cache flushes supported
[17179575.552000]  hdb: hdb1
[17179575.556000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[17179575.556000] Uniform CD-ROM driver Revision: 3.20
[17179575.576000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.856000] SCSI subsystem initialized
[17179575.860000] ACPI: bus type scsi registered
[17179575.860000] libata version 1.20 loaded.
[17179575.860000] ata_piix 0000:00:1f.2: version 1.05
[17179575.860000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[17179575.860000] ata_pci_init_one: NO_LEGACY == 0
[17179575.860000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17179575.860000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.860000] ata1: PATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 169
[17179575.860000] ata2: PATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 169
[17179577.148000] scsi0 : ata_piix
[17179578.436000] scsi1 : ata_piix
[17179578.472000] usbcore: registered new driver usbfs
[17179578.472000] usbcore: registered new driver hub
[17179578.476000] USB Universal Host Controller Interface driver v2.3
[17179578.476000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179578.476000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.476000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.476000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.476000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000ff80
[17179578.480000] hub 1-0:1.0: USB hub found
[17179578.480000] hub 1-0:1.0: 2 ports detected
[17179578.584000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179578.584000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.584000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.584000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.584000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000ff60
[17179578.584000] hub 2-0:1.0: USB hub found
[17179578.584000] hub 2-0:1.0: 2 ports detected
[17179578.688000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179578.688000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.688000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.688000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.688000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000ff40
[17179578.688000] hub 3-0:1.0: USB hub found
[17179578.688000] hub 3-0:1.0: 2 ports detected
[17179578.792000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17179578.792000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179578.792000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179578.792000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179578.792000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ff20
[17179578.792000] hub 4-0:1.0: USB hub found
[17179578.792000] hub 4-0:1.0: 2 ports detected
[17179578.896000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179578.896000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.896000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.896000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.896000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179578.896000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179578.896000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffa80800
[17179578.900000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.900000] hub 5-0:1.0: USB hub found
[17179578.900000] hub 5-0:1.0: 8 ports detected
[17179578.928000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179579.124000] Attempting manual resume
[17179579.188000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.208000] kjournald starting.  Commit interval 5 seconds
[17179579.432000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179587.728000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.736000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.748000] Real Time Clock Driver v1.12
[17179587.760000] Floppy drive(s): fd0 is 1.44M
[17179587.776000] FDC 0 is a post-1991 82077
[17179587.816000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.948000] agpgart: Detected an Intel i875 Chipset.
[17179587.956000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179587.988000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179587.988000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179588.044000] hw_random hardware driver 1.0.0 loaded
[17179588.092000] parport: PnPBIOS parport detected.
[17179588.092000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179588.124000] input: PC Speaker as /class/input/input1
[17179588.272000] logips2pp: Detected unknown logitech mouse model 127
[17179588.316000] intel8x0_measure_ac97_clock: measured 55136 usecs
[17179588.316000] intel8x0: clocking to 48000
[17179588.716000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179589.032000] ts: Compaq touchscreen protocol output
[17179589.056000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17179589.056000] Copyright (c) 1999-2005 Intel Corporation.
[17179589.056000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179589.336000] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:f1:b2:24
[17179589.372000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179589.420000] adm8211: Copyright 2003, Jouni Malinen <jkmaline@cc.hut.fi>; Copyright 2004-2005, Michael Wu <flamingice@sourmilk.net>
[17179589.420000] adm8211: release 20050620
[17179589.420000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179589.552000] usbcore: registered new driver hiddev
[17179589.600000] 0000:02:01.0 (adm8211): EEPROM type 93C46
[17179589.604000] input: Logitech Logitech Dual Action as /class/input/input3
[17179589.604000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.1-2
[17179589.604000] usbcore: registered new driver usbhid
[17179589.604000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.604000] 0000:02:01.0 (adm8211): Channel range: 1 - 11
[17179589.604000] 0000:02:01.0 (adm8211): RFtype=1 BBPtype=1 Specific BBP=0 Transceiver=0
[17179589.604000] eth1: hwaddr 00:40:05:90:36:2c, IRQ 209, Rev 0x11
[17179591.632000] eth1: scanning..
[17179591.928000] lp0: using parport0 (interrupt-driven).
[17179591.936000] NET: Registered protocol family 17
[17179592.052000] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[17179592.316000] EXT3 FS on hda1, internal journal
[17179592.536000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.536000] md: bitmap version 4.39
[17179593.292000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179593.352000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=0 num=1/2 score=0
[17179593.352000] eth1: new BSSID 00:13:46:40:4d:08
[17179593.416000] eth1: authenticate with AP 00:13:46:40:4d:08 CHAN=6
[17179593.416000] eth1: TX authentication (alg=0 transaction=1)
[17179593.428000] eth1: RX authentication (alg=0 transaction=2 status=0 Success)
[17179593.428000] eth1: authenticated
[17179593.428000] eth1: associate with AP 00:13:46:40:4d:08
[17179593.428000] eth1: TX AssocReq (capab=0x421)
[17179593.436000] eth1: RX AssocResp (capab=0x421 aid=1 status=0 Success)
[17179593.436000] eth1: associated
[17179593.444000] eth1: LinkOn
[17179593.932000] cdrom: open failed.
[17179594.252000] cdrom: open failed.
[17179594.252000] cdrom: open failed.
[17179596.208000] NET: Registered protocol family 10
[17179596.208000] lo: Disabled Privacy Extensions
[17179596.208000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179596.248000] IPv6 over IPv4 tunneling driver
[17179598.928000] ACPI: Power Button (FF) [PWRF]
[17179598.928000] ACPI: Power Button (CM) [VBTN]
[17179599.056000] ibm_acpi: ec object not found
[17179599.088000] pcc_acpi: loading...
[17179603.408000] ppdev: user-space parallel port driver
[17179603.620000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179603.620000] apm: overridden by ACPI.
[17179604.256000] eth1 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179606.616000] Bluetooth: Core ver 2.8
[17179606.616000] NET: Registered protocol family 31
[17179606.616000] Bluetooth: HCI device and connection manager initialized
[17179606.616000] Bluetooth: HCI socket layer initialized
[17179606.624000] Bluetooth: L2CAP ver 2.8
[17179606.624000] Bluetooth: L2CAP socket layer initialized
[17179606.696000] Bluetooth: RFCOMM socket layer initialized
[17179606.696000] Bluetooth: RFCOMM TTY layer initialized
[17179606.696000] Bluetooth: RFCOMM ver 1.7
[17179606.972000] eth1: no IPv6 routers present
[17179686.112000] eth1: LinkOff
[17179686.212000] eth1: scanning..
[17179687.928000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=561/3 score=26
[17179688.056000] eth1: LinkOn
[17179771.268000] eth1: LinkOff
[17179771.368000] eth1: scanning..
[17179773.084000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=1212/3 score=26
[17179773.248000] eth1: LinkOn
[17179899.084000] eth1: LinkOff
[17179899.184000] eth1: scanning..
[17179900.900000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=2349/3 score=24
[17179901.032000] eth1: LinkOn
[17179993.484000] eth1: LinkOff
[17179993.584000] eth1: scanning..
[17179995.300000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=25 num=3050/4 score=25
[17179995.436000] eth1: LinkOn
[17180101.468000] eth1: LinkOff
[17180101.568000] eth1: scanning..
[17180103.284000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=18 num=3980/4 score=18
[17180103.460000] eth1: LinkOn
[17180288.172000] eth1: LinkOff
[17180288.272000] eth1: scanning..
[17180289.988000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=17 num=5680/7 score=17
[17180290.128000] eth1: LinkOn
[17180451.136000] eth1: LinkOff
[17180451.236000] eth1: scanning..
[17180452.952000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=22 num=7236/7 score=22
[17180453.040000] eth1: LinkOn
[17180519.268000] eth1: LinkOff
[17180519.368000] eth1: scanning..
[17180521.084000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=19 num=7710/8 score=19
[17180521.224000] eth1: LinkOn
[17180587.260000] eth1: LinkOff
[17180587.360000] eth1: scanning..
[17180589.076000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=8240/9 score=26
[17180589.212000] eth1: LinkOn
[17180798.424000] eth1: LinkOff
[17180798.524000] eth1: scanning..
[17180800.240000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=29 num=10240/11 score=29
[17180800.344000] eth1: LinkOn
[17180979.720000] eth1: LinkOff
[17180979.820000] eth1: scanning..
[17180981.536000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=28 num=11959/12 score=28
[17180981.680000] eth1: LinkOn
[17181122.872000] eth1: LinkOff
[17181122.972000] eth1: scanning..
[17181124.688000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=19 num=13217/13 score=19
[17181124.824000] eth1: LinkOn
[17181249.160000] eth1: LinkOff
[17181249.260000] eth1: scanning..
[17181250.976000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=16 num=14351/15 score=16
[17181251.084000] eth1: LinkOn
[17181329.468000] eth1: LinkOff
[17181329.568000] eth1: scanning..
[17181331.284000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=25 num=15020/17 score=25
[17181331.452000] eth1: LinkOn
[17181407.204000] eth1: LinkOff
[17181407.304000] eth1: scanning..
[17181409.020000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=17 num=15692/20 score=17
[17181409.168000] eth1: LinkOn
[17181486.532000] eth1: LinkOff
[17181486.632000] eth1: scanning..
[17181488.348000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=16387/21 score=23
[17181488.524000] eth1: LinkOn
[17181560.248000] Unable to identify CD-ROM format.
[17181572.552000] Unable to identify CD-ROM format.
[17181589.960000] eth1: LinkOff
[17181590.060000] eth1: scanning..
[17181591.776000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=28 num=17207/22 score=28
[17181591.940000] eth1: LinkOn
[17181696.584000] Unable to identify CD-ROM format.
[17181736.700000] Unable to identify CD-ROM format.
[17181739.732000] cdrom: open failed.
[17181739.784000] cdrom: open failed.
[17181739.840000] cdrom: open failed.
[17181739.892000] cdrom: open failed.
[17181739.976000] cdrom: open failed.
[17181740.032000] cdrom: open failed.
[17181740.064000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17181740.104000] cdrom: open failed.
[17181740.156000] cdrom: open failed.
[17181740.224000] cdrom: open failed.
[17181740.276000] cdrom: open failed.
[17181740.344000] cdrom: open failed.
[17181740.400000] cdrom: open failed.
[17181740.452000] cdrom: open failed.
[17181740.504000] cdrom: open failed.
[17181740.576000] cdrom: open failed.
[17181740.628000] cdrom: open failed.
[17181740.700000] cdrom: open failed.
[17181740.756000] cdrom: open failed.
[17181740.900000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17181740.900000] SGI XFS Quota Management subsystem
[17181740.940000] cdrom: open failed.
[17181740.992000] cdrom: open failed.
[17181741.028000] JFS: nTxBlock = 8090, nTxLock = 64725
[17181741.076000] cdrom: open failed.
[17181741.128000] cdrom: open failed.
[17181744.472000] Unable to identify CD-ROM format.
[17181913.212000] Unable to identify CD-ROM format.
[17181920.668000] Unable to identify CD-ROM format.
[17182041.116000] eth1: LinkOff
[17182041.216000] eth1: scanning..
[17182042.932000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=21 num=21534/23 score=21
[17182043.080000] eth1: LinkOn
[17182110.680000] eth1: LinkOff
[17182110.780000] eth1: scanning..
[17182112.496000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=28 num=22112/23 score=28
[17182112.604000] eth1: LinkOn
[17182180.340000] eth1: LinkOff
[17182180.440000] eth1: scanning..
[17182182.156000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=28 num=22562/23 score=28
[17182182.332000] eth1: LinkOn
[17182335.400000] eth1: LinkOff
[17182335.500000] eth1: scanning..
[17182337.216000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=23989/24 score=23
[17182337.356000] eth1: LinkOn
[17182558.844000] eth1: LinkOff
[17182558.944000] eth1: scanning..
[17182560.660000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=21 num=26147/24 score=21
[17182560.784000] eth1: LinkOn
[17182858.796000] eth1: LinkOff
[17182858.896000] eth1: scanning..
[17182860.612000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=20 num=28967/25 score=20
[17182860.784000] eth1: LinkOn
[17183005.364000] eth1: LinkOff
[17183005.464000] eth1: scanning..
[17183007.180000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=30022/25 score=24
[17183007.308000] eth1: LinkOn
[17183079.860000] eth1: LinkOff
[17183079.960000] eth1: scanning..
[17183081.676000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=30574/26 score=23
[17183081.852000] eth1: LinkOn
[17183148.612000] eth1: LinkOff
[17183148.712000] eth1: scanning..
[17183150.428000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=25 num=30961/27 score=25
[17183150.556000] eth1: LinkOn
[17183216.576000] eth1: LinkOff
[17183216.676000] eth1: scanning..
[17183218.392000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=31295/28 score=24
[17183218.544000] eth1: LinkOn
[17183290.264000] eth1: LinkOff
[17183290.364000] eth1: scanning..
[17183292.080000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=31691/29 score=24
[17183292.164000] eth1: LinkOn
[17183350.344000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[17183350.476000] usb 5-5: configuration #1 chosen from 2 choices
[17183350.568000] Initializing USB Mass Storage driver...
[17183350.568000] scsi2 : SCSI emulation for USB Mass Storage devices
[17183350.568000] usb-storage: device found at 3
[17183350.568000] usb-storage: waiting for device to settle before scanning
[17183350.568000] usbcore: registered new driver usb-storage
[17183350.568000] USB Mass Storage support registered.
[17183355.568000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17183355.568000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183355.576000] usb-storage: device scan complete
[17183355.608000] Driver 'sd' needs updating - please use bus_type methods
[17183355.612000] SCSI device sda: 39075372 2048-byte hdwr sectors (80026 MB)
[17183355.620000] sda: Write Protect is off
[17183355.620000] sda: Mode Sense: 68 00 00 08
[17183355.620000] sda: assuming drive cache: write through
[17183355.696000] SCSI device sda: 39075372 2048-byte hdwr sectors (80026 MB)
[17183355.700000] sda: Write Protect is off
[17183355.700000] sda: Mode Sense: 68 00 00 08
[17183355.700000] sda: assuming drive cache: write through
[17183355.700000]  sda: sda1 sda2
[17183355.728000] sd 2:0:0:0: Attached scsi removable disk sda
[17183355.740000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17183356.468000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17183358.252000] eth1: LinkOff
[17183358.352000] eth1: scanning..
[17183360.068000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=32056/29 score=23
[17183360.160000] eth1: LinkOn
[17183427.108000] eth1: LinkOff
[17183427.208000] eth1: scanning..
[17183428.924000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=32545/30 score=23
[17183429.064000] eth1: LinkOn
[17183495.020000] eth1: LinkOff
[17183495.120000] eth1: scanning..
[17183496.836000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=33055/31 score=23
[17183496.948000] eth1: LinkOn
[17183563.064000] eth1: LinkOff
[17183563.164000] eth1: scanning..
[17183564.880000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=33511/32 score=23
[17183565.040000] eth1: LinkOn
[17183631.992000] eth1: LinkOff
[17183632.092000] eth1: scanning..
[17183633.808000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=33952/32 score=23
[17183633.952000] eth1: LinkOn
[17183707.456000] eth1: LinkOff
[17183707.556000] eth1: scanning..
[17183709.272000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=34493/32 score=23
[17183709.412000] eth1: LinkOn
[17183775.204000] eth1: LinkOff
[17183775.304000] eth1: scanning..
[17183777.020000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=35019/33 score=26
[17183777.196000] eth1: LinkOn
[17183856.436000] eth1: LinkOff
[17183856.536000] eth1: scanning..
[17183858.252000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=16 num=35782/36 score=16
[17183858.396000] eth1: LinkOn
[17184059.404000] eth1: LinkOff
[17184059.504000] eth1: scanning..
[17184061.220000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=37705/36 score=26
[17184061.344000] eth1: LinkOn
[17184132.348000] eth1: LinkOff
[17184132.448000] eth1: scanning..
[17184134.164000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=23 num=38205/37 score=23
[17184134.248000] eth1: LinkOn
[17184203.820000] cdrom: open failed.
[17184218.336000] Unable to identify CD-ROM format.
[17184239.724000] ppdev0: registered pardevice
[17184239.772000] ppdev0: unregistered pardevice
[17184303.680000] eth1: LinkOff
[17184303.780000] eth1: scanning..
[17184305.496000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=17 num=39829/38 score=17
[17184305.644000] eth1: LinkOn
[17184359.852000] Unable to identify CD-ROM format.
[17184397.920000] eth1: LinkOff
[17184398.020000] eth1: scanning..
[17184399.736000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=40704/38 score=24
[17184399.844000] eth1: LinkOn
[17184465.772000] eth1: LinkOff
[17184465.872000] eth1: scanning..
[17184467.588000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=41298/38 score=24
[17184467.732000] eth1: LinkOn
[17184538.888000] eth1: LinkOff
[17184538.988000] eth1: scanning..
[17184540.704000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=25 num=41909/39 score=25
[17184540.840000] eth1: LinkOn
[17184557.132000] cdrom: open failed.
[17184622.980000] eth1: LinkOff
[17184623.080000] eth1: scanning..
[17184624.796000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=24 num=42690/41 score=24
[17184624.904000] eth1: LinkOn
[17184883.796000] UDF-fs: No fileset found
[17184901.496000] UDF-fs: No fileset found
[17184957.216000] eth1: LinkOff
[17184957.316000] eth1: scanning..
[17184959.032000] eth1: CHAN=6 BSSID=00:13:46:40:4d:08 SSID=default RSSI=26 num=45913/41 score=26
[17184959.124000] eth1: LinkOn
knightinarms@knightinarms-pc:~$
knightinarms@knightinarms-pc:~$

---

