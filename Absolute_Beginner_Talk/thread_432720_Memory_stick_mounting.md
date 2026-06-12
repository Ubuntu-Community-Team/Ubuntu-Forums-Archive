---
title: "Memory stick mounting"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Partyboi2 on 2007-05-04
Trying to mount usb memory stick. When I plug it in lsusb does not show it, and when I dmesg this is wat I get:

[17179573.376000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.376000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.376000] mice: PS/2 mouse device common for all mice
[17179573.376000] EISA: Probing bus 0 at eisa.0
[17179573.376000] EISA: Detected 0 cards.
[17179573.376000] NET: Registered protocol family 2
[17179573.412000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.412000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.412000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.412000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.412000] TCP reno registered
[17179573.412000] TCP bic registered
[17179573.412000] NET: Registered protocol family 1
[17179573.412000] NET: Registered protocol family 8
[17179573.412000] NET: Registered protocol family 20
[17179573.412000] Using IPI Shortcut mode
[17179573.412000] Freeing unused kernel memory: 288k freed
[17179573.432000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.496000] vga16fb: initializing
[17179573.496000] vga16fb: mapped to 0xc00a0000
[17179573.624000] Console: switching to colour frame buffer device 80x25
[17179573.624000] fb0: VGA16 VGA frame buffer device
[17179574.744000] Capability LSM initialized
[17179575.924000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179575.924000] ICH2: chipset revision 18
[17179575.924000] ICH2: not 100% native mode: will probe irqs later
[17179575.924000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179575.924000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179575.924000] Probing IDE interface ide0...
[17179576.212000] hda: WDC WD200BB-75DEA0, ATA DISK drive
[17179576.884000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.884000] Probing IDE interface ide1...
[17179577.620000] hdc: TEAC CD-ROM CD-224E, ATAPI CD/DVD-ROM drive
[17179578.292000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.304000] hda: max request size: 128KiB
[17179578.316000] hda: Host Protected Area detected.
[17179578.316000]       current capacity is 39062500 sectors (20000 MB)
[17179578.316000]       native  capacity is 39102336 sectors (20020 MB)
[17179578.320000] hda: Host Protected Area disabled.
[17179578.320000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179578.320000] hda: cache flushes not supported
[17179578.320000]  hda: hda1 hda2 < hda5 >
[17179578.352000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[17179578.352000] Uniform CD-ROM driver Revision: 3.20
[17179578.632000] usbcore: registered new driver usbfs
[17179578.632000] usbcore: registered new driver hub
[17179578.636000] USB Universal Host Controller Interface driver v2.3
[17179578.636000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.636000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179578.640000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179578.640000] uhci_hcd 0000:00:1f.2: irq 185, io base 0x0000ff80
[17179578.640000] hub 1-0:1.0: USB hub found
[17179578.640000] hub 1-0:1.0: 2 ports detected
[17179578.744000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179578.744000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179578.744000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179578.744000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000ff60
[17179578.744000] hub 2-0:1.0: USB hub found
[17179578.744000] hub 2-0:1.0: 2 ports detected
[17179578.960000] Attempting manual resume
[17179578.984000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179579.012000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.016000] kjournald starting.  Commit interval 5 seconds
[17179579.372000] usb 1-2: new low speed USB device using uhci_hcd and address 3[17179579.784000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179590.584000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.584000] agpgart: Detected an Intel i845 Chipset.
[17179590.588000] agpgart: AGP aperture is 64M @ 0xf4000000
[17179590.928000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.940000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.996000] hw_random: RNG not detected
[17179591.132000] parport: PnPBIOS parport detected.
[17179591.132000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179591.764000] input: PC Speaker as /class/input/input1
[17179591.860000] usbcore: registered new driver hiddev
[17179591.880000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179591.884000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1f.2-2
[17179591.884000] usbcore: registered new driver usbhid
[17179591.884000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.012000] Real Time Clock Driver v1.12
[17179592.048000] eth0: register 'cdc_ether' at usb-0000:00:1f.2-1, CDC Ethernet Device, 00:14:04:01:f7:98
[17179592.048000] usbcore: registered new driver cdc_ether
[17179592.064000] Floppy drive(s): fd0 is 1.44M
[17179592.080000] FDC 0 is a post-1991 82077
[17179592.356000] SCSI subsystem initialized
[17179592.388000] Initializing USB Mass Storage driver...
[17179592.388000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179592.388000] usb-storage: device found at 2
[17179592.388000] usb-storage: waiting for device to settle before scanning
[17179592.388000] usbcore: registered new driver usb-storage
[17179592.388000] USB Mass Storage support registered.
[17179592.500000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179592.500000] 0000:02:0c.0: 3Com PCI 3c905C Tornado at d093cc00. Vers LK1.1.19
[17179592.524000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179592.840000] intel8x0_measure_ac97_clock: measured 4292183283 usecs
[17179592.840000] intel8x0: measured clock 0 rejected
[17179592.840000] intel8x0: clocking to 48000
[17179592.952000] ts: Compaq touchscreen protocol output
[17179593.520000] lp0: using parport0 (interrupt-driven).
[17179593.616000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179593.784000] EXT3 FS on hda1, internal journal
[17179593.896000] NET: Registered protocol family 17
[17179594.084000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.084000] md: bitmap version 4.39
[17179594.748000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179595.484000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179595.484000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179595.484000] ide: failed opcode was: unknown
[17179595.484000] cdrom: open failed.
[17179598.252000]   Vendor: OTi       Model: Flash Disk        Rev: 2.00
[17179598.252000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179598.256000] usb-storage: device scan complete
[17179598.368000] Driver 'sd' needs updating - please use bus_type methods
[17179600.856000] NET: Registered protocol family 10
[17179600.856000] lo: Disabled Privacy Extensions
[17179600.856000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179600.856000] IPv6 over IPv4 tunneling driver
[17179603.296000] ready
[17179604.048000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
[17179604.808000] sda: Write Protect is off
[17179604.808000] sda: Mode Sense: 03 00 00 00
[17179604.808000] sda: assuming drive cache: write through
[17179607.828000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
[17179608.584000] sda: Write Protect is off
[17179608.584000] sda: Mode Sense: 03 00 00 00
[17179608.584000] sda: assuming drive cache: write through
[17179608.584000]  sda: sda1
[17179609.340000] sd 0:0:0:0: Attached scsi removable disk sda
[17179609.372000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179610.860000] eth1: no IPv6 routers present
[17179622.260000] ppdev: user-space parallel port driver
[17179622.848000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179624.096000] [drm] Initialized drm 1.0.1 20051102
[17179624.112000] [drm] Initialized r128 2.5.0 20030725 on minor 0
[17179624.112000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179624.112000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179624.112000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179624.504000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[17179624.504000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[17179624.504000] ide: failed opcode was: 0xec
[17179635.196000] Bluetooth: Core ver 2.8
[17179635.196000] NET: Registered protocol family 31
[17179635.196000] Bluetooth: HCI device and connection manager initialized
[17179635.196000] Bluetooth: HCI socket layer initialized
[17179635.232000] Bluetooth: L2CAP ver 2.8
[17179635.232000] Bluetooth: L2CAP socket layer initialized
[17179635.252000] Bluetooth: RFCOMM socket layer initialized
[17179635.252000] Bluetooth: RFCOMM TTY layer initialized
[17179635.252000] Bluetooth: RFCOMM ver 1.7
[17180383.736000] FAT: invalid media value (0x01)
[17180383.736000] VFS: Can't find a valid FAT filesystem on dev sda.
[17182102.376000] usb 2-2: USB disconnect, address 2


how do I find out what sort of file system is on it? And do I need to update the drivers for it and if so how....

---

### Post by ajmorris on 2007-05-05
have you tried manually mounting it? (it you don't know what the device name is/ what it gets mounted as do *sudo mount -a* in a terminal)

---

### Post by tgalati4 on 2007-05-05
Try plugging the memory stick in a digital camera and hooking the camera up with USB.  You should be able to see the memory stick and then read and write from it.

You could try sudo cfdisk /dev/sda1 and reformat as FAT.  I believe the memory sticks are formatted with FAT 12-bit or some variant that may interefere with proper reading.  If you have other devices that rely on this memory stick, you will need to test them to make sure that the reformatted disk works.  If it is a magic-gate stick, there is some form of copy protection and that may also trip up detection.

---

### Post by Partyboi2 on 2007-05-06
I was using /dev/sda as the file system instead of /dev/sda1 now that I have changed it over in /etc/fstab it is reading it and mounting it. Something so simple but atleast I am learning by it all lol...
Now the device is recognized when the pc boots up with the memory stick in the usb port, and I am able to mount it, but if I disconnect the memory stick from the usb while pc is on and reconnect it, when I try to mount the device I get the error message:

mount: special device /dev/sda1 does not exist

Is there away to get the system to recognize the device when I plug it into the usb port? So that I dont have to keep rebooting if I want to use the device?

---

### Post by tgalati4 on 2007-05-06
Don't pull the card until after you right-click on the desktop icon and "eject" it.  Pulling it without a proper "eject" can leave the mount in an indeterminent state.

You shouldn't have to mount it.  The Hotplug routine should mount it automatically once you plug it in.  On some machines this can take 30 seconds or so.  Not sure why, but it does take quite a while, but then it does show up without mounting it in terminal.

---

