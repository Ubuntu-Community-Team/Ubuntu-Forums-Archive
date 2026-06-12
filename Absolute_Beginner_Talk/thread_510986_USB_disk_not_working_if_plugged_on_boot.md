---
title: "USB disk not working if plugged on boot"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by zxccvb on 2007-07-27
I have a USB external hard drive.

The problem is that if it is plugged on boot it is not recognized.
If i unplug it and retry doesn't work anyway so i have to reboot the whole system without my disk plugged  and plug it only later, which is kind of a pain in the *** because i always forget it plugged and im forced to reboot.

What is even worse is that if i leave it plugged at boot not only i lose any hope to use it in this sessinion but the whole USB hotplug capability stops working.
This means that if i hotplug a mouse it won't work either.

When i boot unplugged instead i can hotplug at will.

What's going on?

---

### Post by cek on 2007-07-27
After you boot with the drive plugged in, plugg in another USB device.

In a terminal window, type:   dmesg

And post the output here.  That will help us to see if the device is being recognized (by the kernel) when plugged in.

---

### Post by moore.bryan on 2007-07-27
[I]i have a 120gb western digital external and i got it to work perfectly by adding an fstab entry since i almost never unplug it and take it anywhere.  you might want to try the same thing.  
1.  turn-on your computer without the drive attached and then connect the drive.  
[/I][I]2.  make an entry in your /media folder for the drive.  you can make this anything, but i'll use xhd as the example.
```
sudo make /media/xhd
```
[/I][I]3.  type the following into a terminal 
```
ls -l /dev/disk/by-uuid
```  
4.  edit your stab:
```
sudo nano /etc/fstab
``` and include the uuid:
```
UUID=##################    /media/xhd
     default      default     0      0
```
5.  restart your computer and everything should be okay...

post if there are any problems!  ;-)
[/I]

---

### Post by zxccvb on 2007-07-27
in the meanwhile i try the fstab suggestion this is the dmesg output:



[    3.804000] Time: acpi_pm clocksource has been installed.
[    3.872000] usb 2-1: configuration #1 chosen from 1 choice
[    4.008000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.008000] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[    4.008000] ata1.00: 156301488 sectors, multi 16: LBA48
[    4.008000] ata1.01: ATAPI, max UDMA/33
[    4.016000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.016000] ata1.00: configured for UDMA/100
[    4.124000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    4.180000] ata1.01: configured for UDMA/33
[    4.180000] scsi1 : ata_piix
[    4.288000] usb 2-2: configuration #1 chosen from 1 choice
[    4.336000] ATA: abnormal status 0x7F on port 0x00010177
[    4.340000] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[    4.344000] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-845D          D100 PQ: 0 ANSI: 5
[    4.348000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.396000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0002800-b0002fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.396000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.396000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[    4.396000] eth0: RTL8169sb/8110sb at 0xf8922000, 00:0f:b0:94:01:c1, IRQ 22
[    4.396000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    4.396000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    4.396000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.396000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.396000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.396000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.396000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.396000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0x70000000
[    4.400000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.400000] usb usb5: configuration #1 chosen from 1 choice
[    4.400000] hub 5-0:1.0: USB hub found
[    4.400000] hub 5-0:1.0: 8 ports detected
[    4.416000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.420000] sda: Write Protect is off
[    4.420000] sda: Mode Sense: 00 3a 00 00
[    4.420000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.420000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    4.420000] Uniform CD-ROM driver Revision: 3.20
[    4.420000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.424000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.424000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    4.428000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.428000] sda: Write Protect is off
[    4.428000] sda: Mode Sense: 00 3a 00 00
[    4.432000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.432000]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[    4.508000] sd 0:0:0:0: Attached scsi disk sda
[    4.556000] usb 2-1: USB disconnect, address 2
[    4.684000] usb 2-2: USB disconnect, address 3
[    4.872000] Attempting manual resume
[    4.872000] swsusp: Resume From Partition 8:6
[    4.872000] PM: Checking swsusp image.
[    4.872000] PM: Resume from disk failed.
[    4.920000] kjournald starting.  Commit interval 5 seconds
[    4.920000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.052000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    5.668000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f597b4039fd]
[    6.052000] ehci_hcd 0000:00:1d.7: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   16.596000] usb 5-3: device not accepting address 2, error -110
[   16.708000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   20.280000] r8169: eth0: link up
[   20.828000] NET: Registered protocol family 10
[   20.828000] lo: Disabled Privacy Extensions
[   21.540000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.588000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.804000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.848000] agpgart: Detected an Intel 915GM Chipset.
[   22.152000] intel_rng: FWH not detected
[   22.308000] agpgart: AGP aperture is 256M @ 0x0
[   22.352000] Yenta: CardBus bridge found at 0000:06:04.0 [1025:007f]
[   22.352000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   22.352000] Yenta: Routing CardBus interrupts to PCI
[   22.352000] Yenta TI: socket 0000:06:04.0, mfunc 0x89501212, devctl 0x44
[   22.356000] iTCO_vendor_support: vendor-support=0
[   22.360000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   22.380000] sdhci: Secure Digital Host Controller Interface driver
[   22.380000] sdhci: Copyright(c) Pierre Ossman
[   22.584000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   22.584000] Socket status: 30000006
[   22.584000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   22.584000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x7fff
[   22.584000] cs: IO port probe 0x6000-0x7fff: clean.
[   22.584000] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb3ffffff
[   22.584000] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   22.584000] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   22.584000] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   22.584000] mmc0: SDHCI at 0xb0000100 irq 17 DMA
[   22.740000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   22.772000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.776000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   22.776000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.172000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.172000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   23.180000] parport: PnPBIOS parport detected.
[   23.180000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   23.216000] irda_init()
[   23.216000] NET: Registered protocol family 23
[   23.556000] cs: IO port probe 0x100-0x3af: clean.
[   23.556000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.556000] cs: IO port probe 0x820-0x8ff: clean.
[   23.556000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.560000] cs: IO port probe 0xa00-0xaff: clean.
[   23.676000] lp0: using parport0 (interrupt-driven).
[   23.880000] fuse init (API version 7.8)
[   23.904000] Adding 497972k swap on /dev/disk/by-uuid/f2530b84-07f3-4afb-83b2-740f27adf208.  Priority:-1 extents:1 across:497972k
[   24.180000] EXT3 FS on sda4, internal journal
[   28.252000] usb 5-3: device not accepting address 3, error -110
[   28.364000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[   31.320000] eth0: no IPv6 routers present
[   38.788000] usb 5-3: device not accepting address 4, error -110
[   38.900000] usb 5-3: new high speed USB device using ehci_hcd and address 5
[   49.324000] usb 5-3: device not accepting address 5, error -110
[   49.564000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[   61.108000] usb 5-4: device not accepting address 6, error -110
[   61.220000] usb 5-4: new high speed USB device using ehci_hcd and address 7
[   72.764000] usb 5-4: device not accepting address 7, error -110
[   72.876000] usb 5-4: new high speed USB device using ehci_hcd and address 8
[   77.732000] kjournald starting.  Commit interval 5 seconds
[   77.732000] EXT3 FS on sda7, internal journal
[   77.732000] EXT3-fs: mounted filesystem with ordered data mode.
[   78.760000] input: Power Button (FF) as /class/input/input3
[   78.764000] ACPI: Power Button (FF) [PWRF]
[   78.804000] input: Lid Switch as /class/input/input4
[   78.804000] ACPI: Lid Switch [LID0]
[   78.844000] input: Power Button (CM) as /class/input/input5
[   78.848000] ACPI: Power Button (CM) [PWRB]
[   78.884000] input: Sleep Button (CM) as /class/input/input6
[   78.888000] ACPI: Sleep Button (CM) [SLPB]
[   78.912000] ACPI: ACPI Dock Station Driver
[   78.988000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   78.988000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   79.004000] Using specific hotkey driver
[   79.104000] ibm_acpi: ec object not found
[   79.196000] ACPI: AC Adapter [ACAD] (on-line)
[   79.308000] ACPI: Battery Slot [BAT1] (battery present)
[   79.328000] pcc_acpi: loading...
[   82.000000] ppdev: user-space parallel port driver
[   83.300000] usb 5-4: device not accepting address 8, error -110
[   83.412000] usb 5-4: new high speed USB device using ehci_hcd and address 9
[   84.068000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   84.076000] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[   84.076000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   84.204000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   85.732000] apm: BIOS not found.
[   86.492000] [fglrx] total      GART = 130023424
[   86.492000] [fglrx] free       GART = 114032640
[   86.492000] [fglrx] max single GART = 114032640
[   86.492000] [fglrx] total      LFB  = 134086656
[   86.492000] [fglrx] free       LFB  = 115871744
[   86.492000] [fglrx] max single LFB  = 115871744
[   86.492000] [fglrx] total      Inv  = 0
[   86.492000] [fglrx] free       Inv  = 0
[   86.492000] [fglrx] max single Inv  = 0
[   86.492000] [fglrx] total      TIM  = 0
[   86.832000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   87.172000] Netfilter messages via NETLINK v0.30.
[   87.384000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   93.836000] usb 5-4: device not accepting address 9, error -110
[   94.020000] usbcore: registered new interface driver libusual
[   94.060000] Initializing USB Mass Storage driver...
[   94.300000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   94.476000] usb 3-1: configuration #1 chosen from 1 choice
[   94.480000] usbcore: registered new interface driver usb-storage
[   94.480000] USB Mass Storage support registered.
[   94.632000] usbcore: registered new interface driver hiddev
[   94.648000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input7
[   94.648000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1
[   94.648000] usbcore: registered new interface driver usbhid
[   94.648000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   95.244000] NET: Registered protocol family 17
[   95.312000] Bluetooth: Core ver 2.11
[   95.312000] NET: Registered protocol family 31
[   95.312000] Bluetooth: HCI device and connection manager initialized
[   95.312000] Bluetooth: HCI socket layer initialized
[   95.336000] Bluetooth: L2CAP ver 2.8
[   95.336000] Bluetooth: L2CAP socket layer initialized
[   95.344000] Bluetooth: RFCOMM socket layer initialized
[   95.344000] Bluetooth: RFCOMM TTY layer initialized
[   95.344000] Bluetooth: RFCOMM ver 1.8
[   95.468000] device eth0 entered promiscuous mode
[   95.468000] audit(1185539665.576:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  620.268000] [fglrx] PCIe has already been initialized. Reinitializing ...
[  620.280000] [fglrx] total      GART = 130023424
[  620.280000] [fglrx] free       GART = 114032640
[  620.280000] [fglrx] max single GART = 114032640
[  620.280000] [fglrx] total      LFB  = 134086656
[  620.280000] [fglrx] free       LFB  = 115871744
[  620.280000] [fglrx] max single LFB  = 115871744
[  620.280000] [fglrx] total      Inv  = 0
[  620.280000] [fglrx] free       Inv  = 0
[  620.280000] [fglrx] max single Inv  = 0
[  620.280000] [fglrx] total      TIM  = 0
[ 4137.268000] usb 5-1: new high speed USB device using ehci_hcd and address 11
[ 4148.812000] usb 5-1: device not accepting address 11, error -110
[ 4148.924000] usb 5-1: new high speed USB device using ehci_hcd and address 12
[ 4160.468000] usb 5-1: device not accepting address 12, error -110
[ 4160.580000] usb 5-1: new high speed USB device using ehci_hcd and address 13
[ 4171.004000] usb 5-1: device not accepting address 13, error -110
[ 4171.116000] usb 5-1: new high speed USB device using ehci_hcd and address 14
[ 4181.540000] usb 5-1: device not accepting address 14, error -110

---

