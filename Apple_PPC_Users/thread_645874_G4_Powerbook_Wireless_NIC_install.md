---
title: "G4 Powerbook Wireless NIC install?"
date: 2007-12-20
forum: Apple PPC Users
---

### Post by SamZor on 2007-12-20
Hi I have installed kubuntu 6.06 LTS on my friends powerbook g4 and i need to get the wireless NIC working. (normal NIC works fine)
Im usually ok with device installation only i did not have much time to play around with it to get everything working (usually use standard pc hardware).

* cant **iwscan** and **iwconfig** seems to have no valid entry leading me to believe that the NIC does not have the required libraries to work properly.

I have posted a bunch of log files so that somebody more experienced can help spot the problem and point me in the right direction.

cheers :)

**iwconfig**
```

eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4306" Mode:Managed Access Point: Invalid Bit Rate:1 Mb/s RTS thr:off Fragment thr:off Link Quality:0 Signal level:0 Noise level:0 Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

**interfaces log**
```

auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0 auto eth0 iface eth0 inet dhcp auto eth1 iface eth1 inet dhcp auto eth2 iface eth2 inet dhcp auto ath0 iface ath0 inet dhcp auto wlan0 iface wlan0 inet dhcp 

```

**dmesg log**
```

[    0.000000] Total memory = 256MB; using 512kB for hash table (at cff80000)
[    0.000000] Linux version 2.6.15-26-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Fri Sep 8 19:51:33 UTC 2006
[    0.000000] Found initrd at 0xc1900000:0xc20c5000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xfdf40000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: iBook G4
[    0.000000] Enabling clock spreading on Intrepid ASIC
[    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver 2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=224, gen1=223
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x10000000, Total RAM: 0x10000000
[    0.000000] Memory hole size: 0MB
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 65536 pages, LIFO batch:15
[    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 18.432000 MHz
[    0.000000] time_init: processor frequency   = 1199.999997 MHz
[   35.198240] Console: colour dummy device 80x25
[   35.198852] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   35.199589] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.214132] High memory: 0k
[   35.214143] Memory: 247296k/262144k available (2692k kernel code, 14556k reserved, 276k data, 304k bss, 180k init)
[   35.214372] Calibrating delay loop... 36.73 BogoMIPS (lpj=73472)
[   35.286009] Security Framework v1.0.0 initialized
[   35.286033] SELinux:  Disabled at boot.
[   35.286074] Mount-cache hash table entries: 512
[   35.286409] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,G4@0
[   35.289013] checking if image is initramfs... it is
[   37.034232] Freeing initrd memory: 7956k freed
[   37.036202] NET: Registered protocol family 16
[   37.037028] PCI: Probing PCI hardware
[   37.039665] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
[   37.039688] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[   37.039717] Apple USB OHCI 0001:10:18.0 disabled by firmware
[   37.039729] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   37.041714] Registering PowerMac CPU frequency driver
[   37.041726] Low: 599 Mhz, High: 1199 Mhz, Boot: 599 Mhz
[   37.046042] Thermal assist unit not available
[   37.046749] audit: initializing netlink socket (disabled)
[   37.046769] audit(1198147890.844:1): initialized
[   37.046934] VFS: Disk quotas dquot_6.5.1
[   37.046969] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.047068] Initializing Cryptographic API
[   37.047078] io scheduler noop registered
[   37.047087] io scheduler anticipatory registered
[   37.047096] io scheduler deadline registered
[   37.047116] io scheduler cfq registered
[   37.047474] PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
[   37.243273] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
[   37.243282] radeonfb: Retreived PLL infos from Open Firmware
[   37.243289] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=190.00 Mhz, System=183.00 MHz
[   37.243294] radeonfb: PLL min 12000 max 35000
[   38.178914] radeonfb: Monitor 1 type LCD found
[   38.178919] radeonfb: EDID probed
[   38.178922] radeonfb: Monitor 2 type no found
[   38.178936] radeonfb: Using Firmware dividers 0x000600ad from PPLL 0
[   38.317928] radeonfb: Dynamic Clock Power Management enabled
[   38.361768] Console: switching to colour frame buffer device 128x48
[   38.361841] Registered "mnca" backlight controller,level: 15/15
[   38.361845] radeonfb (0000:00:10.0): ATI Radeon \c 
[   38.383272] Macintosh non-volatile memory driver v1.1
[   38.383377] IN from bad port 64 at c018d2a8
[   38.383432] IN from bad port 60 at c018d2dc
[   38.383436] IN from bad port 64 at c018d2a8
[   38.383490] IN from bad port 60 at c018d2dc
[   38.383494] IN from bad port 64 at c018d2a8
[   38.383547] IN from bad port 60 at c018d2dc
[   38.383552] IN from bad port 64 at c018d2a8
[   38.383605] IN from bad port 60 at c018d2dc
[   38.383609] IN from bad port 64 at c018d2a8
[   38.383662] IN from bad port 60 at c018d2dc
[   38.383667] IN from bad port 64 at c018d2a8
[   38.383720] IN from bad port 60 at c018d2dc
[   38.383724] IN from bad port 64 at c018d2a8
[   38.383778] IN from bad port 60 at c018d2dc
[   38.383782] IN from bad port 64 at c018d2a8
[   38.383835] IN from bad port 60 at c018d2dc
[   38.383840] IN from bad port 64 at c018d2a8
[   38.383893] IN from bad port 60 at c018d2dc
[   38.383897] IN from bad port 64 at c018d2a8
[   38.383950] IN from bad port 60 at c018d2dc
[   38.383955] IN from bad port 64 at c018d2a8
[   38.384008] IN from bad port 60 at c018d2dc
[   38.384012] IN from bad port 64 at c018d2a8
[   38.384065] IN from bad port 60 at c018d2dc
[   38.384070] IN from bad port 64 at c018d2a8
[   38.384123] IN from bad port 60 at c018d2dc
[   38.384127] IN from bad port 64 at c018d2a8
[   38.384181] IN from bad port 60 at c018d2dc
[   38.384185] IN from bad port 64 at c018d2a8
[   38.384238] IN from bad port 60 at c018d2dc
[   38.384242] IN from bad port 64 at c018d2a8
[   38.384296] IN from bad port 60 at c018d2dc
[   38.384300] IN from bad port 64 at c018d2a8
[   38.384304] i8042.c: No controller found.
[   38.384877] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.385054] MacIO PCI driver attached to Intrepid chipset
[   38.385882] input: Macintosh mouse button emulation as /class/input/input0
[   38.386083] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.386091] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.386111] adb: starting probe task...
[   38.387512] PCI: Enabling device 0002:20:0d.0 (0000 -> 0002)
[   38.633651] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[   38.639406] ADB keyboard at 2, handler 1
[   38.639418] Detected ADB keyboard, type ANSI.
[   38.639517] input: ADB keyboard as /class/input/input1
[   38.639587] input: ADB Powerbook buttons as /class/input/input2
[   38.654298] ADB mouse at 3, handler set to 4 (trackpad)
[   38.713189] input: ADB mouse as /class/input/input3
[   38.713195] adb: finished probe task...
[   39.405932] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
[   39.405949] Probing IDE interface ide0...
[   39.694114] hda: TOSHIBA MK3025GAS, ATA DISK drive
[   40.365941] hda: Enabling Ultra DMA 5
[   40.366987] ide0 at 0xd101a000-0xd101a007,0xd101a160 on irq 39
[   41.385931] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
[   41.385945] Probing IDE interface ide1...
[   41.786117] hdc: MATSHITACD-RW CW-8124, ATAPI CD/DVD-ROM drive
[   42.121936] hdc: Enabling MultiWord DMA 2
[   42.122959] ide1 at 0xd100e000-0xd100e007,0xd100e160 on irq 24
[   42.123197] mice: PS/2 mouse device common for all mice
[   42.123299] NET: Registered protocol family 2
[   42.158021] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   42.158276] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   42.158398] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   42.158520] TCP: Hash tables configured (established 16384 bind 16384)
[   42.158526] TCP reno registered
[   42.158641] TCP bic registered
[   42.158653] NET: Registered protocol family 1
[   42.158664] NET: Registered protocol family 8
[   42.158667] NET: Registered protocol family 20
[   42.158741] Freeing unused kernel memory: 180k init
[   43.380370] Capability LSM initialized
[   43.440944] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
[   43.441092] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
[   44.170537] hda: max request size: 1024KiB
[   44.175733] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
[   44.175751] Uniform CD-ROM driver Revision: 3.20
[   44.219086] hda: 58605120 sectors (30005 MB), CHS=16383/255/63, UDMA(100)
[   44.219167] hda: cache flushes supported
[   44.219490]  hda: [mac] hda1 hda2 hda3 hda4
[   44.807054] usbcore: registered new driver usbfs
[   44.807669] usbcore: registered new driver hub
[   44.811778] PCI: Enabling device 0001:10:1b.2 (0004 -> 0006)
[   44.811803] ehci_hcd 0001:10:1b.2: EHCI Host Controller
[   44.834794] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 1
[   44.834818] ehci_hcd 0001:10:1b.2: irq 63, io mem 0x80080000
[   44.834833] ehci_hcd 0001:10:1b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.835347] hub 1-0:1.0: USB hub found
[   44.835370] hub 1-0:1.0: 5 ports detected
[   45.095636] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   45.096298] Apple USB OHCI 0001:10:18.0 disabled by firmware
[   45.096311] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   45.096324] PCI: Enabling device 0001:10:1a.0 (0000 -> 0002)
[   45.096348] ohci_hcd 0001:10:1a.0: OHCI Host Controller
[   45.096662] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 2
[   45.096682] ohci_hcd 0001:10:1a.0: irq 29, io mem 0x80083000
[   45.130142] hub 2-0:1.0: USB hub found
[   45.130168] hub 2-0:1.0: 2 ports detected
[   45.148310] ieee1394: Initialized config rom entry `ip1394'
[   45.234368] PCI: Enabling device 0001:10:1b.0 (0000 -> 0002)
[   45.234397] ohci_hcd 0001:10:1b.0: OHCI Host Controller
[   45.234591] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 3
[   45.234608] ohci_hcd 0001:10:1b.0: irq 63, io mem 0x80082000
[   45.269842] hub 3-0:1.0: USB hub found
[   45.269864] hub 3-0:1.0: 3 ports detected
[   45.370152] PCI: Enabling device 0001:10:1b.1 (0000 -> 0002)
[   45.370167] ohci_hcd 0001:10:1b.1: OHCI Host Controller
[   45.370331] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 4
[   45.370343] ohci_hcd 0001:10:1b.1: irq 63, io mem 0x80081000
[   45.405797] hub 4-0:1.0: USB hub found
[   45.405813] hub 4-0:1.0: 2 ports detected
[   45.508745] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   45.508782] PCI: Enabling device 0002:20:0e.0 (0000 -> 0002)
[   45.509369] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[   45.560538] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
[   45.858255] Attempting manual resume
[   45.967137] kjournald starting.  Commit interval 5 seconds
[   45.967165] EXT3-fs: mounted filesystem with ordered data mode.
[   46.834388] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001451fffe1c9822]
[  104.649498] ts: Compaq touchscreen protocol output
[  109.224928] Linux agpgart interface v0.101 (c) Dave Jones
[  109.226966] agpgart: Detected Apple UniNorth 2 chipset
[  109.227067] agpgart: configuring for size idx: 4
[  109.227125] agpgart: AGP aperture is 16M @ 0x0
[  109.243874] ieee80211_crypt: registered algorithm 'NULL'
[  109.246439] ieee80211: 802.11 data/management/control stack, git-1.1.7
[  109.246447] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  109.329174] bcm43xx driver
[  109.329366] PCI: Enabling device 0001:10:12.0 (0004 -> 0006)
[  109.352711] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[  109.418286] PHY ID: 4061e4, addr: 0
[  109.418995] eth1: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:14:51:1c:98:22 
[  109.419004] eth1: Found BCM5221 PHY
[  110.731442] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  110.747775] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  111.450039] NET: Registered protocol family 17
[  111.818058] eth0: Link is up at 100 Mbps, full-duplex.
[  111.818070] eth0: Pause is disabled
[  111.914275] input: PowerMac Beep as /class/input/input4
[  112.113621] apm_emu: APM Emulation 0.5 initialized.
[  112.396497] SCSI subsystem initialized
[  112.445774] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[  112.445784] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[  112.445788] ieee1394: sbp2: Try serialize_io=0 for better performance
[  112.697193] Adding 747832k swap on /dev/hda4.  Priority:-1 extents:1 across:747832k
[  112.884039] EXT3 FS on hda3, internal journal
[  113.274780] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  113.274790] md: bitmap version 4.39
[  114.244818] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[  115.528806] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  115.528819] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[  115.528826] ide: failed opcode was: unknown
[  115.529154] cdrom: open failed.
[  119.715883] NET: Registered protocol family 10
[  119.716105] lo: Disabled Privacy Extensions
[  119.716385] IPv6 over IPv4 tunneling driver
[  130.445930] eth0: no IPv6 routers present
[  130.580396] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  130.580403] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120378
[  130.580419] ide: failed opcode was: unknown
[  130.580428] end_request: I/O error, dev hda, sector 30120378
[  138.959620] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  138.959632] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120386
[  138.959648] ide: failed opcode was: unknown
[  138.959658] end_request: I/O error, dev hda, sector 30120386
[  147.338828] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  147.338837] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  147.338852] ide: failed opcode was: unknown
[  147.338859] end_request: I/O error, dev hda, sector 30120394
[  155.775031] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  155.775040] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  155.775055] ide: failed opcode was: unknown
[  155.775062] end_request: I/O error, dev hda, sector 30120394
[  164.182731] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  164.182739] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  164.182754] ide: failed opcode was: unknown
[  164.182759] end_request: I/O error, dev hda, sector 30120394
[  179.957843] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  179.957856] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  179.957872] ide: failed opcode was: unknown
[  179.957883] end_request: I/O error, dev hda, sector 30120394
[  188.408271] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  188.408284] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  188.408300] ide: failed opcode was: unknown
[  188.408309] end_request: I/O error, dev hda, sector 30120394
[  188.781491] lp: driver loaded but no devices found
[  188.924172] ppdev: user-space parallel port driver
[  190.102105] Bluetooth: Core ver 2.8
[  190.102117] NET: Registered protocol family 31
[  190.102120] Bluetooth: HCI device and connection manager initialized
[  190.102141] Bluetooth: HCI socket layer initialized
[  190.126375] Bluetooth: L2CAP ver 2.8
[  190.126387] Bluetooth: L2CAP socket layer initialized
[  190.242911] Bluetooth: RFCOMM socket layer initialized
[  190.242948] Bluetooth: RFCOMM TTY layer initialized
[  190.242952] Bluetooth: RFCOMM ver 1.7
[  194.073129] [drm] Initialized drm 1.0.1 20051102
[  194.092437] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[  195.271816] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
[  195.271837] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
[  195.342127] [drm] Setting GART location based on old memory map
[  195.342153] [drm] Loading R200 Microcode
[  195.342214] [drm] writeback test succeeded in 1 usecs
[  223.449786] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  223.449805] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  223.449829] ide: failed opcode was: unknown
[  223.449841] end_request: I/O error, dev hda, sector 30120394
[  231.985743] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  231.985762] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
[  231.985786] ide: failed opcode was: unknown
[  231.985799] end_request: I/O error, dev hda, sector 30120394

```

**syslog log**
```

Dec 20 20:07:44 bridie-laptop syslogd 1.4.1#17ubuntu7: restart.
Dec 20 20:07:44 bridie-laptop anacron[3766]: Job `cron.daily' terminated
Dec 20 20:07:50 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Dec 20 20:08:00 bridie-laptop kernel: [  495.473627] usb 2-2: new high speed USB device using ehci_hcd and address 2
Dec 20 20:08:00 bridie-laptop kernel: [  495.981535] Initializing USB Mass Storage driver...
Dec 20 20:08:00 bridie-laptop kernel: [  495.982914] scsi0 : SCSI emulation for USB Mass Storage devices
Dec 20 20:08:00 bridie-laptop kernel: [  495.983617] usb-storage: device found at 2
Dec 20 20:08:00 bridie-laptop kernel: [  495.983626] usb-storage: waiting for device to settle before scanning
Dec 20 20:08:00 bridie-laptop kernel: [  495.984014] usbcore: registered new driver usb-storage
Dec 20 20:08:00 bridie-laptop kernel: [  495.984024] USB Mass Storage support registered.
Dec 20 20:08:05 bridie-laptop kernel: [  500.986337]   Vendor: ST350083  Model: 0AS               Rev:     
Dec 20 20:08:05 bridie-laptop kernel: [  500.986375]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec 20 20:08:05 bridie-laptop kernel: [  501.009242] usb-storage: device scan complete
Dec 20 20:08:06 bridie-laptop kernel: [  501.151363] Driver 'sd' needs updating - please use bus_type methods
Dec 20 20:08:06 bridie-laptop kernel: [  501.174699] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Dec 20 20:08:06 bridie-laptop kernel: [  501.174717] sda: assuming drive cache: write through
Dec 20 20:08:06 bridie-laptop kernel: [  501.199519] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Dec 20 20:08:06 bridie-laptop kernel: [  501.199610] sda: assuming drive cache: write through
Dec 20 20:08:06 bridie-laptop kernel: [  501.201076]  sda: sda1
Dec 20 20:08:06 bridie-laptop kernel: [  501.218454] sd 0:0:0:0: Attached scsi disk sda
Dec 20 20:08:06 bridie-laptop kernel: [  501.274037] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 20 20:08:10 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:08:10 bridie-laptop kernel: [  506.072280] UDF-fs: No VRS found
Dec 20 20:08:11 bridie-laptop kernel: [  506.248111] UDF-fs: No VRS found
Dec 20 20:08:11 bridie-laptop kernel: [  506.319530] Unable to identify CD-ROM format.
Dec 20 20:08:11 bridie-laptop kernel: [  506.383906] Unable to identify CD-ROM format.
Dec 20 20:08:11 bridie-laptop kernel: [  506.450599] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Dec 20 20:08:18 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Dec 20 20:08:35 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:08:35 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:11:49 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:11:57 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Dec 20 20:12:17 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Dec 20 20:12:26 bridie-laptop anacron[3766]: Job `cron.weekly' started
Dec 20 20:12:26 bridie-laptop anacron[5279]: Updated timestamp for job `cron.weekly' to 2007-12-20
Dec 20 20:12:28 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 20:12:28 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:12:28 bridie-laptop exiting on signal 15
Dec 20 20:12:29 bridie-laptop syslogd 1.4.1#17ubuntu7: restart.
Dec 20 20:12:29 bridie-laptop anacron[3766]: Job `cron.weekly' terminated
Dec 20 20:12:33 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Dec 20 20:12:33 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:12:36 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 20 20:12:42 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Dec 20 20:12:42 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:12:44 bridie-laptop anacron[5432]: Anacron 2.3 started on 2007-12-20
Dec 20 20:12:44 bridie-laptop anacron[5432]: Job `cron.monthly' locked by another anacron - skipping
Dec 20 20:12:44 bridie-laptop anacron[5432]: Normal exit (0 jobs run)
Dec 20 20:12:45 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 20 20:12:45 bridie-laptop pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd powersave battery ' launched and exited normally 
Dec 20 20:12:50 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:12:50 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:12:57 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Dec 20 20:12:57 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:13:18 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Dec 20 20:13:18 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:13:29 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:13:29 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:17:01 bridie-laptop /USR/SBIN/CRON[6007]: (root) CMD (   run-parts --report /etc/cron.hourly)
Dec 20 20:17:26 bridie-laptop anacron[3766]: Job `cron.monthly' started
Dec 20 20:17:26 bridie-laptop anacron[6068]: Updated timestamp for job `cron.monthly' to 2007-12-20
Dec 20 20:17:29 bridie-laptop anacron[3766]: Job `cron.monthly' terminated
Dec 20 20:17:29 bridie-laptop anacron[3766]: Normal exit (3 jobs run)
Dec 20 20:19:51 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:19:53 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:19:53 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:19:59 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Dec 20 20:19:59 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Dec 20 20:19:59 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:08 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Dec 20 20:20:08 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:17 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 20 20:20:18 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Dec 20 20:20:18 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:30 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 20:20:31 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 20 20:20:31 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:39 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Dec 20 20:20:39 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:41 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 20 20:20:48 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:20:48 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:20:51 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Dec 20 20:20:52 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:20:52 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:20:54 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:20:54 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:24:35 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:24:35 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:24:41 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Dec 20 20:24:41 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:24:58 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:24:58 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:25:12 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Dec 20 20:25:12 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:25:30 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:25:30 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:25:36 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:25:36 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:27:37 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:27:45 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 20 20:27:54 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 20 20:28:07 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Dec 20 20:28:27 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 20:28:38 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:28:38 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:30:18 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 20:30:18 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:30:23 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:30:23 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:30:31 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Dec 20 20:30:31 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:30:39 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:30:39 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:30:53 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 20 20:30:53 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:31:01 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:31:01 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:31:15 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Dec 20 20:31:15 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:31:19 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:31:19 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:34:09 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:34:17 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 20:34:28 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Dec 20 20:34:46 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 20 20:34:59 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 20:35:10 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:35:10 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:37:07 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Dec 20 20:37:07 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:10 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:37:10 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:16 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 20:37:16 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:22 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Dec 20 20:37:22 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:37 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Dec 20 20:37:37 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:47 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Dec 20 20:37:47 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:37:52 bridie-laptop kernel: [ 2287.364622] Unable to identify CD-ROM format.
Dec 20 20:37:52 bridie-laptop kernel: [ 2287.475330] Unable to identify CD-ROM format.
Dec 20 20:37:59 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Dec 20 20:37:59 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:38:02 bridie-laptop kernel: [ 2298.128801] Unable to identify CD-ROM format.
Dec 20 20:38:03 bridie-laptop kernel: [ 2298.245866] Unable to identify CD-ROM format.
Dec 20 20:38:08 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:38:08 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:40:35 bridie-laptop kernel: [ 2450.322811] Unable to identify CD-ROM format.
Dec 20 20:40:35 bridie-laptop kernel: [ 2450.450644] Unable to identify CD-ROM format.
Dec 20 20:42:21 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:42:29 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 20 20:42:42 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 20 20:42:49 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 20 20:42:56 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 20:43:07 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 20 20:43:22 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:43:22 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:44:04 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 20:44:04 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:44:09 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 20:44:09 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:44:14 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Dec 20 20:44:14 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:44:25 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Dec 20 20:44:25 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:44:37 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:44:37 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:44:51 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:44:51 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:45:05 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:45:05 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:46:10 bridie-laptop anacron[10346]: Anacron 2.3 started on 2007-12-20
Dec 20 20:46:10 bridie-laptop anacron[10346]: Normal exit (0 jobs run)
Dec 20 20:46:10 bridie-laptop pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' launched and exited normally 
Dec 20 20:46:50 bridie-laptop kernel: [ 2825.201897] ISO 9660 Extensions: Microsoft Joliet Level 1
Dec 20 20:46:50 bridie-laptop kernel: [ 2825.239345] ISOFS: changing to secondary root
Dec 20 20:50:16 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 20 20:50:22 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Dec 20 20:50:36 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 20 20:50:48 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:50:56 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 20 20:51:11 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 20 20:51:17 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:51:17 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:51:31 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 20 20:51:31 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:51:39 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Dec 20 20:51:39 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:51:55 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Dec 20 20:51:55 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:52:11 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:52:11 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:52:25 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 20:52:25 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:52:32 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:52:32 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:54:42 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 20 20:54:47 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 20:54:55 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Dec 20 20:55:11 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 20 20:55:11 bridie-laptop kernel: [ 3326.407678] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
Dec 20 20:55:11 bridie-laptop kernel: [ 3326.407699] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
Dec 20 20:55:11 bridie-laptop kernel: [ 3326.417390] [drm] Setting GART location based on old memory map
Dec 20 20:55:11 bridie-laptop kernel: [ 3326.417410] [drm] Loading R200 Microcode
Dec 20 20:55:11 bridie-laptop kernel: [ 3326.417473] [drm] writeback test succeeded in 1 usecs
Dec 20 20:55:14 bridie-laptop shutdown[10662]: shutting down for system halt
Dec 20 20:55:14 bridie-laptop init: Switching to runlevel: 0
Dec 20 20:55:20 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Dec 20 20:55:22 bridie-laptop sdpd[4095]: terminating...   
Dec 20 20:55:22 bridie-laptop hcid[4091]: Exit.
Dec 20 20:55:22 bridie-laptop kernel: Kernel logging (proc) stopped.
Dec 20 20:55:22 bridie-laptop kernel: Kernel log daemon terminating.
Dec 20 20:55:23 bridie-laptop exiting on signal 15
Dec 20 20:58:39 bridie-laptop syslogd 1.4.1#17ubuntu7: restart.
Dec 20 20:58:39 bridie-laptop kernel: Inspecting /boot/System.map-2.6.15-26-powerpc
Dec 20 20:58:39 bridie-laptop kernel: Loaded 21084 symbols from /boot/System.map-2.6.15-26-powerpc.
Dec 20 20:58:39 bridie-laptop kernel: Symbols match kernel version 2.6.15.
Dec 20 20:58:39 bridie-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Total memory = 256MB; using 512kB for hash table (at cff80000)
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Linux version 2.6.15-26-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Thu Aug 3 02:53:39 UTC 2006
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found initrd at 0xc1900000:0xc2136000
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Mapped at 0xfdfc0000
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xfdf40000
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Processor NAP mode on idle enabled.
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] PowerMac motherboard: iBook G4
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Enabling clock spreading on Intrepid ASIC
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] via-pmu: Server Mode is disabled
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] PMU driver 2 initialized for Core99, firmware: 0c
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: Checking bank 0...
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: gen0=224, gen1=223
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: Active bank is: 0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: OF partition at 0x410
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: XP partition at 0x1020
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] nvram: NR partition at 0x1120
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Top of RAM: 0x10000000, Total RAM: 0x10000000
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Memory hole size: 0MB
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] On node 0 totalpages: 65536
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000]   DMA zone: 65536 pages, LIFO batch:15
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000]   Normal zone: 0 pages, LIFO batch:0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000]   HighMem zone: 0 pages, LIFO batch:0
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Built 1 zonelists
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] mpic: Initializing for 64 sources
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] time_init: decrementer frequency = 18.432000 MHz
Dec 20 20:58:39 bridie-laptop kernel: [    0.000000] time_init: processor frequency   = 1199.999997 MHz
Dec 20 20:58:39 bridie-laptop kernel: [   28.492047] Console: colour dummy device 80x25
Dec 20 20:58:39 bridie-laptop kernel: [   28.492658] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   28.493396] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   28.507919] High memory: 0k
Dec 20 20:58:39 bridie-laptop kernel: [   28.507931] Memory: 246784k/262144k available (2692k kernel code, 15008k reserved, 276k data, 304k bss, 180k init)
Dec 20 20:58:39 bridie-laptop kernel: [   28.508160] Calibrating delay loop... 36.73 BogoMIPS (lpj=73472)
Dec 20 20:58:39 bridie-laptop kernel: [   28.579825] Security Framework v1.0.0 initialized
Dec 20 20:58:39 bridie-laptop kernel: [   28.579850] SELinux:  Disabled at boot.
Dec 20 20:58:39 bridie-laptop kernel: [   28.579890] Mount-cache hash table entries: 512
Dec 20 20:58:39 bridie-laptop kernel: [   28.580227] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,G4@0
Dec 20 20:58:39 bridie-laptop kernel: [   28.582838] checking if image is initramfs... it is
Dec 20 20:58:39 bridie-laptop kernel: [   30.416266] Freeing initrd memory: 8408k freed
Dec 20 20:58:39 bridie-laptop kernel: [   30.418296] NET: Registered protocol family 16
Dec 20 20:58:39 bridie-laptop kernel: [   30.419036] PCI: Probing PCI hardware
Dec 20 20:58:39 bridie-laptop kernel: [   30.421481] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
Dec 20 20:58:39 bridie-laptop kernel: [   30.421503] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
Dec 20 20:58:39 bridie-laptop kernel: [   30.421532] Apple USB OHCI 0001:10:18.0 disabled by firmware
Dec 20 20:58:39 bridie-laptop kernel: [   30.421544] Apple USB OHCI 0001:10:19.0 disabled by firmware
Dec 20 20:58:39 bridie-laptop kernel: [   30.423549] Registering PowerMac CPU frequency driver
Dec 20 20:58:39 bridie-laptop kernel: [   30.423561] Low: 599 Mhz, High: 1199 Mhz, Boot: 599 Mhz
Dec 20 20:58:39 bridie-laptop kernel: [   30.427858] Thermal assist unit not available
Dec 20 20:58:39 bridie-laptop kernel: [   30.428547] audit: initializing netlink socket (disabled)
Dec 20 20:58:39 bridie-laptop kernel: [   30.428566] audit(1198144596.932:1): initialized
Dec 20 20:58:39 bridie-laptop kernel: [   30.428736] VFS: Disk quotas dquot_6.5.1
Dec 20 20:58:39 bridie-laptop kernel: [   30.428768] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   30.428866] Initializing Cryptographic API
Dec 20 20:58:39 bridie-laptop kernel: [   30.428874] io scheduler noop registered
Dec 20 20:58:39 bridie-laptop kernel: [   30.428884] io scheduler anticipatory registered
Dec 20 20:58:39 bridie-laptop kernel: [   30.428892] io scheduler deadline registered
Dec 20 20:58:39 bridie-laptop kernel: [   30.428912] io scheduler cfq registered
Dec 20 20:58:39 bridie-laptop kernel: [   30.429274] PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
Dec 20 20:58:39 bridie-laptop kernel: [   30.625027] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
Dec 20 20:58:39 bridie-laptop kernel: [   30.625037] radeonfb: Retreived PLL infos from Open Firmware
Dec 20 20:58:39 bridie-laptop kernel: [   30.625043] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=190.00 Mhz, System=183.00 MHz
Dec 20 20:58:39 bridie-laptop kernel: [   30.625048] radeonfb: PLL min 12000 max 35000
Dec 20 20:58:39 bridie-laptop kernel: [   31.560730] radeonfb: Monitor 1 type LCD found
Dec 20 20:58:39 bridie-laptop kernel: [   31.560735] radeonfb: EDID probed
Dec 20 20:58:39 bridie-laptop kernel: [   31.560738] radeonfb: Monitor 2 type no found
Dec 20 20:58:39 bridie-laptop kernel: [   31.560752] radeonfb: Using Firmware dividers 0x000600ad from PPLL 0
Dec 20 20:58:39 bridie-laptop kernel: [   31.699744] radeonfb: Dynamic Clock Power Management enabled
Dec 20 20:58:39 bridie-laptop kernel: [   31.743190] Console: switching to colour frame buffer device 128x48
Dec 20 20:58:39 bridie-laptop kernel: [   31.743258] Registered "mnca" backlight controller,level: 15/15
Dec 20 20:58:39 bridie-laptop kernel: [   31.743262] radeonfb (0000:00:10.0): ATI Radeon \c 
Dec 20 20:58:39 bridie-laptop kernel: [   31.764137] Macintosh non-volatile memory driver v1.1
Dec 20 20:58:39 bridie-laptop kernel: [   31.764244] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764300] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764304] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764357] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764362] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764415] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764420] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764473] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764477] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764530] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764535] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764588] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764592] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764646] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764650] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764703] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764707] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764761] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764765] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764818] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764822] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764876] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764880] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764933] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764937] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.764991] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.764995] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.765048] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.765052] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.765106] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.765110] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.765163] IN from bad port 60 at c018d2dc
Dec 20 20:58:39 bridie-laptop kernel: [   31.765168] IN from bad port 64 at c018d2a8
Dec 20 20:58:39 bridie-laptop kernel: [   31.765171] i8042.c: No controller found.
Dec 20 20:58:39 bridie-laptop kernel: [   31.765779] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 20 20:58:39 bridie-laptop kernel: [   31.765949] MacIO PCI driver attached to Intrepid chipset
Dec 20 20:58:39 bridie-laptop kernel: [   31.766791] input: Macintosh mouse button emulation as /class/input/input0
Dec 20 20:58:39 bridie-laptop kernel: [   31.766997] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 20 20:58:39 bridie-laptop kernel: [   31.767006] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 20 20:58:39 bridie-laptop kernel: [   31.767027] adb: starting probe task...
Dec 20 20:58:39 bridie-laptop kernel: [   31.768431] PCI: Enabling device 0002:20:0d.0 (0000 -> 0002)
Dec 20 20:58:39 bridie-laptop kernel: [   32.012776] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
Dec 20 20:58:39 bridie-laptop kernel: [   32.018557] ADB keyboard at 2, handler 1
Dec 20 20:58:39 bridie-laptop kernel: [   32.018567] Detected ADB keyboard, type ANSI.
Dec 20 20:58:39 bridie-laptop kernel: [   32.018649] input: ADB keyboard as /class/input/input1
Dec 20 20:58:39 bridie-laptop kernel: [   32.018728] input: ADB Powerbook buttons as /class/input/input2
Dec 20 20:58:39 bridie-laptop kernel: [   32.033565] ADB mouse at 3, handler set to 4 (trackpad)
Dec 20 20:58:39 bridie-laptop kernel: [   32.091931] input: ADB mouse as /class/input/input3
Dec 20 20:58:39 bridie-laptop kernel: [   32.091937] adb: finished probe task...
Dec 20 20:58:39 bridie-laptop kernel: [   32.787749] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
Dec 20 20:58:39 bridie-laptop kernel: [   32.787766] Probing IDE interface ide0...
Dec 20 20:58:39 bridie-laptop kernel: [   33.075931] hda: TOSHIBA MK3025GAS, ATA DISK drive
Dec 20 20:58:39 bridie-laptop kernel: [   33.747757] hda: Enabling Ultra DMA 5
Dec 20 20:58:39 bridie-laptop kernel: [   33.748804] ide0 at 0xd101a000-0xd101a007,0xd101a160 on irq 39
Dec 20 20:58:39 bridie-laptop kernel: [   34.767747] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
Dec 20 20:58:39 bridie-laptop kernel: [   34.767762] Probing IDE interface ide1...
Dec 20 20:58:39 bridie-laptop kernel: [   35.167932] hdc: MATSHITACD-RW CW-8124, ATAPI CD/DVD-ROM drive
Dec 20 20:58:39 bridie-laptop kernel: [   35.503751] hdc: Enabling MultiWord DMA 2
Dec 20 20:58:39 bridie-laptop kernel: [   35.504774] ide1 at 0xd100e000-0xd100e007,0xd100e160 on irq 24
Dec 20 20:58:39 bridie-laptop kernel: [   35.505022] mice: PS/2 mouse device common for all mice
Dec 20 20:58:39 bridie-laptop kernel: [   35.505126] NET: Registered protocol family 2
Dec 20 20:58:39 bridie-laptop kernel: [   35.539840] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   35.540099] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   35.540221] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
Dec 20 20:58:39 bridie-laptop kernel: [   35.540343] TCP: Hash tables configured (established 16384 bind 16384)
Dec 20 20:58:39 bridie-laptop kernel: [   35.540349] TCP reno registered
Dec 20 20:58:39 bridie-laptop kernel: [   35.540464] TCP bic registered
Dec 20 20:58:39 bridie-laptop kernel: [   35.540476] NET: Registered protocol family 1
Dec 20 20:58:39 bridie-laptop kernel: [   35.540487] NET: Registered protocol family 8
Dec 20 20:58:39 bridie-laptop kernel: [   35.540491] NET: Registered protocol family 20
Dec 20 20:58:39 bridie-laptop kernel: [   35.540565] Freeing unused kernel memory: 180k init
Dec 20 20:58:39 bridie-laptop kernel: [   36.762132] Capability LSM initialized
Dec 20 20:58:39 bridie-laptop kernel: [   36.822211] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
Dec 20 20:58:39 bridie-laptop kernel: [   36.822349] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
Dec 20 20:58:39 bridie-laptop kernel: [   37.555652] hda: max request size: 1024KiB
Dec 20 20:58:39 bridie-laptop kernel: [   37.560815] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
Dec 20 20:58:39 bridie-laptop kernel: [   37.560834] Uniform CD-ROM driver Revision: 3.20
Dec 20 20:58:39 bridie-laptop kernel: [   37.604268] hda: 58605120 sectors (30005 MB), CHS=16383/255/63, UDMA(100)
Dec 20 20:58:39 bridie-laptop kernel: [   37.604362] hda: cache flushes supported
Dec 20 20:58:39 bridie-laptop kernel: [   37.604621]  hda: [mac] hda1 hda2 hda3 hda4
Dec 20 20:58:39 bridie-laptop kernel: [   49.295837] usbcore: registered new driver usbfs
Dec 20 20:58:39 bridie-laptop kernel: [   49.296448] usbcore: registered new driver hub
Dec 20 20:58:39 bridie-laptop kernel: [   49.300530] PCI: Enabling device 0001:10:1b.2 (0004 -> 0006)
Dec 20 20:58:39 bridie-laptop kernel: [   49.300555] ehci_hcd 0001:10:1b.2: EHCI Host Controller
Dec 20 20:58:39 bridie-laptop kernel: [   49.302931] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Dec 20 20:58:39 bridie-laptop kernel: [   49.303539] Apple USB OHCI 0001:10:18.0 disabled by firmware
Dec 20 20:58:39 bridie-laptop kernel: [   49.303551] Apple USB OHCI 0001:10:19.0 disabled by firmware
Dec 20 20:58:39 bridie-laptop kernel: [   49.303562] PCI: Enabling device 0001:10:1a.0 (0000 -> 0002)
Dec 20 20:58:39 bridie-laptop kernel: [   49.303584] ohci_hcd 0001:10:1a.0: OHCI Host Controller
Dec 20 20:58:39 bridie-laptop kernel: [   49.305718] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 1
Dec 20 20:58:39 bridie-laptop kernel: [   49.305741] ohci_hcd 0001:10:1a.0: irq 29, io mem 0x80083000
Dec 20 20:58:39 bridie-laptop kernel: [   49.325096] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 2
Dec 20 20:58:39 bridie-laptop kernel: [   49.325115] ehci_hcd 0001:10:1b.2: irq 63, io mem 0x80080000
Dec 20 20:58:39 bridie-laptop kernel: [   49.325129] ehci_hcd 0001:10:1b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 20 20:58:39 bridie-laptop kernel: [   49.327337] hub 2-0:1.0: USB hub found
Dec 20 20:58:39 bridie-laptop kernel: [   49.327363] hub 2-0:1.0: 5 ports detected
Dec 20 20:58:39 bridie-laptop kernel: [   49.552604] hub 1-0:1.0: USB hub found
Dec 20 20:58:39 bridie-laptop kernel: [   49.552632] hub 1-0:1.0: 2 ports detected
Dec 20 20:58:39 bridie-laptop kernel: [   49.579439] ieee1394: Initialized config rom entry `ip1394'
Dec 20 20:58:39 bridie-laptop kernel: [   49.656116] PCI: Enabling device 0001:10:1b.0 (0000 -> 0002)
Dec 20 20:58:39 bridie-laptop kernel: [   49.656148] ohci_hcd 0001:10:1b.0: OHCI Host Controller
Dec 20 20:58:39 bridie-laptop kernel: [   49.656345] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 3
Dec 20 20:58:39 bridie-laptop kernel: [   49.656363] ohci_hcd 0001:10:1b.0: irq 63, io mem 0x80082000
Dec 20 20:58:39 bridie-laptop kernel: [   49.691650] hub 3-0:1.0: USB hub found
Dec 20 20:58:39 bridie-laptop kernel: [   49.691671] hub 3-0:1.0: 3 ports detected
Dec 20 20:58:39 bridie-laptop kernel: [   49.791929] PCI: Enabling device 0001:10:1b.1 (0000 -> 0002)
Dec 20 20:58:39 bridie-laptop kernel: [   49.791942] ohci_hcd 0001:10:1b.1: OHCI Host Controller
Dec 20 20:58:39 bridie-laptop kernel: [   49.792104] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 4
Dec 20 20:58:39 bridie-laptop kernel: [   49.792113] ohci_hcd 0001:10:1b.1: irq 63, io mem 0x80081000
Dec 20 20:58:39 bridie-laptop kernel: [   49.827625] hub 4-0:1.0: USB hub found
Dec 20 20:58:39 bridie-laptop kernel: [   49.827641] hub 4-0:1.0: 2 ports detected
Dec 20 20:58:39 bridie-laptop kernel: [   49.933336] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
Dec 20 20:58:39 bridie-laptop kernel: [   49.933379] PCI: Enabling device 0002:20:0e.0 (0000 -> 0002)
Dec 20 20:58:39 bridie-laptop kernel: [   49.933527] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
Dec 20 20:58:39 bridie-laptop kernel: [   49.985168] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
Dec 20 20:58:39 bridie-laptop kernel: [   50.273332] Attempting manual resume
Dec 20 20:58:39 bridie-laptop kernel: [   50.382537] kjournald starting.  Commit interval 5 seconds
Dec 20 20:58:39 bridie-laptop kernel: [   50.382564] EXT3-fs: mounted filesystem with ordered data mode.
Dec 20 20:58:39 bridie-laptop kernel: [   51.260209] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001451fffe1c9822]
Dec 20 20:58:39 bridie-laptop kernel: [   78.323834] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:58:39 bridie-laptop kernel: [   78.323847] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29953997, high=1, low=13176781, sector=29953994
Dec 20 20:58:39 bridie-laptop kernel: [   78.323863] ide: failed opcode was: unknown
Dec 20 20:58:39 bridie-laptop kernel: [   78.323871] end_request: I/O error, dev hda, sector 29953994
Dec 20 20:58:39 bridie-laptop kernel: [  125.392911] ts: Compaq touchscreen protocol output
Dec 20 20:58:39 bridie-laptop kernel: [  128.846804] ieee80211_crypt: registered algorithm 'NULL'
Dec 20 20:58:39 bridie-laptop kernel: [  128.849331] ieee80211: 802.11 data/management/control stack, git-1.1.7
Dec 20 20:58:39 bridie-laptop kernel: [  128.849339] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 20 20:58:39 bridie-laptop kernel: [  128.922243] bcm43xx driver
Dec 20 20:58:39 bridie-laptop kernel: [  128.922440] PCI: Enabling device 0001:10:12.0 (0004 -> 0006)
Dec 20 20:58:39 bridie-laptop kernel: [  129.801507] Linux agpgart interface v0.101 (c) Dave Jones
Dec 20 20:58:39 bridie-laptop kernel: [  129.803392] agpgart: Detected Apple UniNorth 2 chipset
Dec 20 20:58:39 bridie-laptop kernel: [  129.803491] agpgart: configuring for size idx: 4
Dec 20 20:58:39 bridie-laptop kernel: [  129.803552] agpgart: AGP aperture is 16M @ 0x0
Dec 20 20:58:39 bridie-laptop kernel: [  130.455858] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
Dec 20 20:58:39 bridie-laptop kernel: [  130.556374] PHY ID: 4061e4, addr: 0
Dec 20 20:58:39 bridie-laptop kernel: [  130.557081] eth1: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:14:51:1c:98:22 
Dec 20 20:58:39 bridie-laptop kernel: [  130.557091] eth1: Found BCM5221 PHY
Dec 20 20:58:39 bridie-laptop kernel: [  131.810946] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 20:58:39 bridie-laptop kernel: [  131.921106] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 20:58:39 bridie-laptop kernel: [  132.515984] input: PowerMac Beep as /class/input/input4
Dec 20 20:58:39 bridie-laptop kernel: [  132.680747] apm_emu: APM Emulation 0.5 initialized.
Dec 20 20:58:39 bridie-laptop kernel: [  132.804476] NET: Registered protocol family 17
Dec 20 20:58:39 bridie-laptop kernel: [  132.898245] SCSI subsystem initialized
Dec 20 20:58:39 bridie-laptop kernel: [  132.954986] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
Dec 20 20:58:39 bridie-laptop kernel: [  132.954997] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Dec 20 20:58:39 bridie-laptop kernel: [  132.955001] ieee1394: sbp2: Try serialize_io=0 for better performance
Dec 20 20:58:39 bridie-laptop kernel: [  133.356433] Adding 747832k swap on /dev/hda4.  Priority:-1 extents:1 across:747832k
Dec 20 20:58:39 bridie-laptop kernel: [  133.493346] EXT3 FS on hda3, internal journal
Dec 20 20:58:39 bridie-laptop kernel: [  133.887182] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Dec 20 20:58:39 bridie-laptop kernel: [  133.887192] md: bitmap version 4.39
Dec 20 20:58:39 bridie-laptop kernel: [  134.787833] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Dec 20 20:58:39 bridie-laptop pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: ALSA. 
Dec 20 20:58:39 bridie-laptop pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Dec 20 20:58:40 bridie-laptop pbbuttonsd: INFO: pbbuttonsd 0.7.2: iBook/G3 PB Pismo/G4 PB Titanium (PMU version: 12) 
Dec 20 20:58:40 bridie-laptop anacron[3695]: Anacron 2.3 started on 2007-12-20
Dec 20 20:58:40 bridie-laptop anacron[3695]: Normal exit (0 jobs run)
Dec 20 20:58:40 bridie-laptop pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' launched and exited normally 
Dec 20 20:58:41 bridie-laptop hpiod: 0.9.7 accepting connections at 44823... 
Dec 20 20:58:43 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Dec 20 20:58:43 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:58:49 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Dec 20 20:58:50 bridie-laptop kernel: [  163.575106] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:58:50 bridie-laptop kernel: [  163.575118] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964858
Dec 20 20:58:50 bridie-laptop kernel: [  163.575134] ide: failed opcode was: unknown
Dec 20 20:58:50 bridie-laptop kernel: [  163.575144] end_request: I/O error, dev hda, sector 29964858
Dec 20 20:58:56 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Dec 20 20:58:56 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:58:58 bridie-laptop kernel: [  171.940567] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:58:58 bridie-laptop kernel: [  171.940579] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964866
Dec 20 20:58:58 bridie-laptop kernel: [  171.940594] ide: failed opcode was: unknown
Dec 20 20:58:58 bridie-laptop kernel: [  171.940604] end_request: I/O error, dev hda, sector 29964866
Dec 20 20:59:06 bridie-laptop kernel: [  180.306023] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:59:06 bridie-laptop kernel: [  180.306033] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964874
Dec 20 20:59:06 bridie-laptop kernel: [  180.306049] ide: failed opcode was: unknown
Dec 20 20:59:06 bridie-laptop kernel: [  180.306058] end_request: I/O error, dev hda, sector 29964874
Dec 20 20:59:07 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Dec 20 20:59:09 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 20:59:09 bridie-laptop dhclient: send_packet: Network is down
Dec 20 20:59:15 bridie-laptop kernel: [  188.671474] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:59:15 bridie-laptop kernel: [  188.671486] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964882
Dec 20 20:59:15 bridie-laptop kernel: [  188.671501] ide: failed opcode was: unknown
Dec 20 20:59:15 bridie-laptop kernel: [  188.671510] end_request: I/O error, dev hda, sector 29964882
Dec 20 20:59:23 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:59:23 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:59:23 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 20:59:23 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 20:59:23 bridie-laptop kernel: [  197.093929] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:59:23 bridie-laptop kernel: [  197.093942] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964882
Dec 20 20:59:23 bridie-laptop kernel: [  197.093958] ide: failed opcode was: unknown
Dec 20 20:59:23 bridie-laptop kernel: [  197.093968] end_request: I/O error, dev hda, sector 29964882
Dec 20 20:59:32 bridie-laptop kernel: [  205.559120] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 20:59:32 bridie-laptop kernel: [  205.559132] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=29964887, high=1, low=13187671, sector=29964882
Dec 20 20:59:32 bridie-laptop kernel: [  205.559147] ide: failed opcode was: unknown
Dec 20 20:59:32 bridie-laptop kernel: [  205.559155] end_request: I/O error, dev hda, sector 29964882
Dec 20 20:59:32 bridie-laptop ntpdate[3766]: can't find host ntp.ubuntu.com 
Dec 20 20:59:32 bridie-laptop ntpdate[3766]: no servers can be used, exiting
Dec 20 20:59:32 bridie-laptop ntpdate[3767]: can't find host ntp.ubuntu.com 
Dec 20 20:59:32 bridie-laptop ntpdate[3767]: no servers can be used, exiting
Dec 20 20:59:32 bridie-laptop kernel: [  206.318628] lp: driver loaded but no devices found
Dec 20 20:59:32 bridie-laptop kernel: [  206.460523] ppdev: user-space parallel port driver
Dec 20 20:59:36 bridie-laptop hcid[3907]: Bluetooth HCI daemon
Dec 20 20:59:36 bridie-laptop kernel: [  210.140144] Bluetooth: Core ver 2.8
Dec 20 20:59:36 bridie-laptop kernel: [  210.140156] NET: Registered protocol family 31
Dec 20 20:59:36 bridie-laptop kernel: [  210.140160] Bluetooth: HCI device and connection manager initialized
Dec 20 20:59:36 bridie-laptop kernel: [  210.140179] Bluetooth: HCI socket layer initialized
Dec 20 20:59:36 bridie-laptop kernel: [  210.166195] Bluetooth: L2CAP ver 2.8
Dec 20 20:59:36 bridie-laptop kernel: [  210.166208] Bluetooth: L2CAP socket layer initialized
Dec 20 20:59:36 bridie-laptop sdpd[3911]: Bluetooth SDP daemon 
Dec 20 20:59:36 bridie-laptop hcid[3907]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 20 20:59:36 bridie-laptop kernel: [  210.249878] Bluetooth: RFCOMM socket layer initialized
Dec 20 20:59:36 bridie-laptop kernel: [  210.249913] Bluetooth: RFCOMM TTY layer initialized
Dec 20 20:59:36 bridie-laptop kernel: [  210.249918] Bluetooth: RFCOMM ver 1.7
Dec 20 20:59:36 bridie-laptop anacron[3956]: Anacron 2.3 started on 2007-12-20
Dec 20 20:59:36 bridie-laptop anacron[3956]: Normal exit (0 jobs run)
Dec 20 20:59:37 bridie-laptop /usr/sbin/cron[3981]: (CRON) INFO (pidfile fd = 3)
Dec 20 20:59:37 bridie-laptop /usr/sbin/cron[3982]: (CRON) STARTUP (fork ok)
Dec 20 20:59:37 bridie-laptop /usr/sbin/cron[3982]: (CRON) INFO (Running @reboot jobs)
Dec 20 20:59:40 bridie-laptop kernel: [  213.839165] [drm] Initialized drm 1.0.1 20051102
Dec 20 20:59:40 bridie-laptop kernel: [  213.858581] [drm] Initialized radeon 1.24.0 20060225 on minor 0
Dec 20 20:59:41 bridie-laptop kernel: [  215.037642] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
Dec 20 20:59:41 bridie-laptop kernel: [  215.037664] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
Dec 20 20:59:41 bridie-laptop kernel: [  215.127111] [drm] Setting GART location based on old memory map
Dec 20 20:59:41 bridie-laptop kernel: [  215.127136] [drm] Loading R200 Microcode
Dec 20 20:59:41 bridie-laptop kernel: [  215.127197] [drm] writeback test succeeded in 1 usecs
Dec 20 20:59:49 bridie-laptop kdm_greet[4394]: Can't open default user face
Dec 20 21:00:00 bridie-laptop kdm_greet[4394]: Internal error: memory corruption detected
Dec 20 21:01:45 bridie-laptop firmware_helper[4761]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 21:01:45 bridie-laptop kernel: [  338.560999] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:01:47 bridie-laptop firmware_helper[4767]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 21:01:47 bridie-laptop kernel: [  341.471046] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:04:56 bridie-laptop firmware_helper[5392]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 21:04:56 bridie-laptop kernel: [  529.720412] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:05:03 bridie-laptop firmware_helper[5398]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 21:05:03 bridie-laptop kernel: [  536.550326] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:05:47 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 20 21:05:52 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 20 21:05:57 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 20 21:06:08 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Dec 20 21:06:11 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Dec 20 21:06:11 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:06:15 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 20 21:06:15 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:06:23 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 21:06:23 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:06:26 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 20 21:06:36 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 20 21:06:37 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Dec 20 21:06:37 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:06:48 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 21:06:48 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 21:06:48 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 21:06:48 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:06:55 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 21:06:55 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:07:02 bridie-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Dec 20 21:07:02 bridie-laptop dhclient: send_packet: Network is down
Dec 20 21:07:12 bridie-laptop dhclient: No DHCPOFFERS received.
Dec 20 21:07:12 bridie-laptop dhclient: No working leases in persistent database - sleeping.
Dec 20 21:08:03 bridie-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.3
Dec 20 21:08:03 bridie-laptop dhclient: Copyright 2004-2005 Internet Systems Consortium.
Dec 20 21:08:03 bridie-laptop dhclient: All rights reserved.
Dec 20 21:08:03 bridie-laptop dhclient: For info, please visit http://www.isc.org/products/DHCP
Dec 20 21:08:03 bridie-laptop dhclient: 
Dec 20 21:08:03 bridie-laptop dhclient: Listening on LPF/eth1/00:11:24:94:a3:11
Dec 20 21:08:03 bridie-laptop dhclient: Sending on   LPF/eth1/00:11:24:94:a3:11
Dec 20 21:08:03 bridie-laptop dhclient: Sending on   Socket/fallback
Dec 20 21:11:06 bridie-laptop anacron[5894]: Anacron 2.3 started on 2007-12-20
Dec 20 21:11:06 bridie-laptop anacron[5894]: Normal exit (0 jobs run)
Dec 20 21:11:06 bridie-laptop pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd powersave battery ' launched and exited normally 
Dec 20 21:12:15 bridie-laptop kernel: [  969.355881] eth0: Link is up at 100 Mbps, full-duplex.
Dec 20 21:12:15 bridie-laptop kernel: [  969.355897] eth0: Pause is disabled
Dec 20 21:13:08 bridie-laptop kernel: [ 1022.155830] eth0: Link down
Dec 20 21:13:11 bridie-laptop kernel: [ 1024.555882] eth0: Link is up at 100 Mbps, full-duplex.
Dec 20 21:13:11 bridie-laptop kernel: [ 1024.555897] eth0: Pause is disabled
Dec 20 21:14:08 bridie-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 20 21:14:10 bridie-laptop dhclient: DHCPOFFER from 10.1.1.1
Dec 20 21:14:10 bridie-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 20 21:14:10 bridie-laptop dhclient: DHCPACK from 10.1.1.1
Dec 20 21:14:10 bridie-laptop dhclient: bound to 10.1.1.2 -- renewal in 42503 seconds.
Dec 20 21:15:49 bridie-laptop kernel: [ 1182.673803] NET: Registered protocol family 10
Dec 20 21:15:49 bridie-laptop kernel: [ 1182.674128] lo: Disabled Privacy Extensions
Dec 20 21:15:49 bridie-laptop kernel: [ 1182.674534] IPv6 over IPv4 tunneling driver
Dec 20 21:16:00 bridie-laptop kernel: [ 1193.635752] eth0: no IPv6 routers present
Dec 20 21:17:01 bridie-laptop /USR/SBIN/CRON[6987]: (root) CMD (   run-parts --report /etc/cron.hourly)
Dec 20 21:29:33 bridie-laptop init: Trying to re-exec init
Dec 20 21:31:46 bridie-laptop kernel: [ 2139.851192] ISO 9660 Extensions: Microsoft Joliet Level 1
Dec 20 21:31:47 bridie-laptop kernel: [ 2139.985837] ISOFS: changing to secondary root
Dec 20 21:34:00 bridie-laptop exiting on signal 15
Dec 20 21:47:13 localhost syslogd 1.4.1#17ubuntu7.1: restart.
Dec 20 21:50:18 localhost kernel: [ 3252.073558] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
Dec 20 21:50:18 localhost kernel: [ 3252.073579] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
Dec 20 21:50:18 localhost kernel: [ 3252.149283] [drm] Setting GART location based on old memory map
Dec 20 21:50:18 localhost kernel: [ 3252.149307] [drm] Loading R200 Microcode
Dec 20 21:50:18 localhost kernel: [ 3252.149370] [drm] writeback test succeeded in 1 usecs
Dec 20 21:50:21 localhost shutdown[25210]: shutting down for system reboot
Dec 20 21:50:22 localhost init: Switching to runlevel: 6
Dec 20 21:50:30 localhost sdpd[3911]: terminating...   
Dec 20 21:50:30 localhost hcid[3907]: Exit.
Dec 20 21:50:31 localhost kernel: Kernel logging (proc) stopped.
Dec 20 21:50:31 localhost kernel: Kernel log daemon terminating.
Dec 20 21:50:31 localhost exiting on signal 15
Dec 20 21:53:35 localhost syslogd 1.4.1#17ubuntu7.1: restart.
Dec 20 21:53:36 localhost kernel: Inspecting /boot/System.map-2.6.15-26-powerpc
Dec 20 21:53:36 localhost kernel: Loaded 21084 symbols from /boot/System.map-2.6.15-26-powerpc.
Dec 20 21:53:36 localhost kernel: Symbols match kernel version 2.6.15.
Dec 20 21:53:36 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Dec 20 21:53:36 localhost kernel: [    0.000000] Total memory = 256MB; using 512kB for hash table (at cff80000)
Dec 20 21:53:36 localhost kernel: [    0.000000] Linux version 2.6.15-26-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Fri Sep 8 19:51:33 UTC 2006
Dec 20 21:53:36 localhost kernel: [    0.000000] Found initrd at 0xc1900000:0xc20c5000
Dec 20 21:53:36 localhost kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
Dec 20 21:53:36 localhost kernel: [    0.000000] Mapped at 0xfdfc0000
Dec 20 21:53:36 localhost kernel: [    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xfdf40000
Dec 20 21:53:36 localhost kernel: [    0.000000] Processor NAP mode on idle enabled.
Dec 20 21:53:36 localhost kernel: [    0.000000] PowerMac motherboard: iBook G4
Dec 20 21:53:36 localhost kernel: [    0.000000] Enabling clock spreading on Intrepid ASIC
Dec 20 21:53:36 localhost kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
Dec 20 21:53:36 localhost kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->0
Dec 20 21:53:36 localhost kernel: [    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
Dec 20 21:53:36 localhost kernel: [    0.000000] via-pmu: Server Mode is disabled
Dec 20 21:53:36 localhost kernel: [    0.000000] PMU driver 2 initialized for Core99, firmware: 0c
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: Checking bank 0...
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: gen0=224, gen1=223
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: Active bank is: 0
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: OF partition at 0x410
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: XP partition at 0x1020
Dec 20 21:53:36 localhost kernel: [    0.000000] nvram: NR partition at 0x1120
Dec 20 21:53:36 localhost kernel: [    0.000000] Top of RAM: 0x10000000, Total RAM: 0x10000000
Dec 20 21:53:36 localhost kernel: [    0.000000] Memory hole size: 0MB
Dec 20 21:53:36 localhost kernel: [    0.000000] On node 0 totalpages: 65536
Dec 20 21:53:36 localhost kernel: [    0.000000]   DMA zone: 65536 pages, LIFO batch:15
Dec 20 21:53:36 localhost kernel: [    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
Dec 20 21:53:36 localhost kernel: [    0.000000]   Normal zone: 0 pages, LIFO batch:0
Dec 20 21:53:36 localhost kernel: [    0.000000]   HighMem zone: 0 pages, LIFO batch:0
Dec 20 21:53:36 localhost kernel: [    0.000000] Built 1 zonelists
Dec 20 21:53:36 localhost kernel: [    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
Dec 20 21:53:36 localhost kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
Dec 20 21:53:36 localhost kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Dec 20 21:53:36 localhost kernel: [    0.000000] mpic: Initializing for 64 sources
Dec 20 21:53:36 localhost kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Dec 20 21:53:36 localhost kernel: [    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
Dec 20 21:53:36 localhost kernel: [    0.000000] time_init: decrementer frequency = 18.432000 MHz
Dec 20 21:53:36 localhost kernel: [    0.000000] time_init: processor frequency   = 1199.999997 MHz
Dec 20 21:53:36 localhost kernel: [   35.198240] Console: colour dummy device 80x25
Dec 20 21:53:36 localhost kernel: [   35.198852] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 20 21:53:36 localhost kernel: [   35.199589] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 20 21:53:36 localhost kernel: [   35.214132] High memory: 0k
Dec 20 21:53:36 localhost kernel: [   35.214143] Memory: 247296k/262144k available (2692k kernel code, 14556k reserved, 276k data, 304k bss, 180k init)
Dec 20 21:53:36 localhost kernel: [   35.214372] Calibrating delay loop... 36.73 BogoMIPS (lpj=73472)
Dec 20 21:53:36 localhost kernel: [   35.286009] Security Framework v1.0.0 initialized
Dec 20 21:53:36 localhost kernel: [   35.286033] SELinux:  Disabled at boot.
Dec 20 21:53:36 localhost kernel: [   35.286074] Mount-cache hash table entries: 512
Dec 20 21:53:36 localhost kernel: [   35.286409] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,G4@0
Dec 20 21:53:36 localhost kernel: [   35.289013] checking if image is initramfs... it is
Dec 20 21:53:36 localhost kernel: [   37.034232] Freeing initrd memory: 7956k freed
Dec 20 21:53:36 localhost kernel: [   37.036202] NET: Registered protocol family 16
Dec 20 21:53:36 localhost kernel: [   37.037028] PCI: Probing PCI hardware
Dec 20 21:53:36 localhost kernel: [   37.039665] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
Dec 20 21:53:36 localhost kernel: [   37.039688] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
Dec 20 21:53:36 localhost kernel: [   37.039717] Apple USB OHCI 0001:10:18.0 disabled by firmware
Dec 20 21:53:36 localhost kernel: [   37.039729] Apple USB OHCI 0001:10:19.0 disabled by firmware
Dec 20 21:53:36 localhost kernel: [   37.041714] Registering PowerMac CPU frequency driver
Dec 20 21:53:36 localhost kernel: [   37.041726] Low: 599 Mhz, High: 1199 Mhz, Boot: 599 Mhz
Dec 20 21:53:36 localhost kernel: [   37.046042] Thermal assist unit not available
Dec 20 21:53:36 localhost kernel: [   37.046749] audit: initializing netlink socket (disabled)
Dec 20 21:53:36 localhost kernel: [   37.046769] audit(1198147890.844:1): initialized
Dec 20 21:53:36 localhost kernel: [   37.046934] VFS: Disk quotas dquot_6.5.1
Dec 20 21:53:36 localhost kernel: [   37.046969] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 20 21:53:36 localhost kernel: [   37.047068] Initializing Cryptographic API
Dec 20 21:53:36 localhost kernel: [   37.047078] io scheduler noop registered
Dec 20 21:53:36 localhost kernel: [   37.047087] io scheduler anticipatory registered
Dec 20 21:53:36 localhost kernel: [   37.047096] io scheduler deadline registered
Dec 20 21:53:36 localhost kernel: [   37.047116] io scheduler cfq registered
Dec 20 21:53:36 localhost kernel: [   37.047474] PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
Dec 20 21:53:36 localhost kernel: [   37.243273] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
Dec 20 21:53:36 localhost kernel: [   37.243282] radeonfb: Retreived PLL infos from Open Firmware
Dec 20 21:53:36 localhost kernel: [   37.243289] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=190.00 Mhz, System=183.00 MHz
Dec 20 21:53:36 localhost kernel: [   37.243294] radeonfb: PLL min 12000 max 35000
Dec 20 21:53:36 localhost kernel: [   38.178914] radeonfb: Monitor 1 type LCD found
Dec 20 21:53:36 localhost kernel: [   38.178919] radeonfb: EDID probed
Dec 20 21:53:36 localhost kernel: [   38.178922] radeonfb: Monitor 2 type no found
Dec 20 21:53:36 localhost kernel: [   38.178936] radeonfb: Using Firmware dividers 0x000600ad from PPLL 0
Dec 20 21:53:36 localhost kernel: [   38.317928] radeonfb: Dynamic Clock Power Management enabled
Dec 20 21:53:36 localhost kernel: [   38.361768] Console: switching to colour frame buffer device 128x48
Dec 20 21:53:36 localhost kernel: [   38.361841] Registered "mnca" backlight controller,level: 15/15
Dec 20 21:53:36 localhost kernel: [   38.361845] radeonfb (0000:00:10.0): ATI Radeon \c 
Dec 20 21:53:36 localhost kernel: [   38.383272] Macintosh non-volatile memory driver v1.1
Dec 20 21:53:36 localhost kernel: [   38.383377] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383432] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383436] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383490] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383494] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383547] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383552] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383605] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383609] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383662] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383667] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383720] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383724] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383778] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383782] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383835] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383840] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383893] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383897] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.383950] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.383955] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384008] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384012] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384065] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384070] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384123] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384127] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384181] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384185] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384238] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384242] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384296] IN from bad port 60 at c018d2dc
Dec 20 21:53:36 localhost kernel: [   38.384300] IN from bad port 64 at c018d2a8
Dec 20 21:53:36 localhost kernel: [   38.384304] i8042.c: No controller found.
Dec 20 21:53:36 localhost kernel: [   38.384877] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 20 21:53:36 localhost kernel: [   38.385054] MacIO PCI driver attached to Intrepid chipset
Dec 20 21:53:36 localhost kernel: [   38.385882] input: Macintosh mouse button emulation as /class/input/input0
Dec 20 21:53:36 localhost kernel: [   38.386083] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 20 21:53:36 localhost kernel: [   38.386091] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 20 21:53:36 localhost kernel: [   38.386111] adb: starting probe task...
Dec 20 21:53:36 localhost kernel: [   38.387512] PCI: Enabling device 0002:20:0d.0 (0000 -> 0002)
Dec 20 21:53:36 localhost kernel: [   38.633651] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
Dec 20 21:53:36 localhost kernel: [   38.639406] ADB keyboard at 2, handler 1
Dec 20 21:53:36 localhost kernel: [   38.639418] Detected ADB keyboard, type ANSI.
Dec 20 21:53:36 localhost kernel: [   38.639517] input: ADB keyboard as /class/input/input1
Dec 20 21:53:36 localhost kernel: [   38.639587] input: ADB Powerbook buttons as /class/input/input2
Dec 20 21:53:36 localhost kernel: [   38.654298] ADB mouse at 3, handler set to 4 (trackpad)
Dec 20 21:53:36 localhost kernel: [   38.713189] input: ADB mouse as /class/input/input3
Dec 20 21:53:36 localhost kernel: [   38.713195] adb: finished probe task...
Dec 20 21:53:36 localhost kernel: [   39.405932] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
Dec 20 21:53:36 localhost kernel: [   39.405949] Probing IDE interface ide0...
Dec 20 21:53:36 localhost kernel: [   39.694114] hda: TOSHIBA MK3025GAS, ATA DISK drive
Dec 20 21:53:36 localhost kernel: [   40.365941] hda: Enabling Ultra DMA 5
Dec 20 21:53:36 localhost kernel: [   40.366987] ide0 at 0xd101a000-0xd101a007,0xd101a160 on irq 39
Dec 20 21:53:36 localhost kernel: [   41.385931] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
Dec 20 21:53:36 localhost kernel: [   41.385945] Probing IDE interface ide1...
Dec 20 21:53:36 localhost kernel: [   41.786117] hdc: MATSHITACD-RW CW-8124, ATAPI CD/DVD-ROM drive
Dec 20 21:53:36 localhost kernel: [   42.121936] hdc: Enabling MultiWord DMA 2
Dec 20 21:53:36 localhost kernel: [   42.122959] ide1 at 0xd100e000-0xd100e007,0xd100e160 on irq 24
Dec 20 21:53:36 localhost kernel: [   42.123197] mice: PS/2 mouse device common for all mice
Dec 20 21:53:36 localhost kernel: [   42.123299] NET: Registered protocol family 2
Dec 20 21:53:36 localhost kernel: [   42.158021] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 20 21:53:36 localhost kernel: [   42.158276] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
Dec 20 21:53:36 localhost kernel: [   42.158398] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
Dec 20 21:53:36 localhost kernel: [   42.158520] TCP: Hash tables configured (established 16384 bind 16384)
Dec 20 21:53:36 localhost kernel: [   42.158526] TCP reno registered
Dec 20 21:53:36 localhost kernel: [   42.158641] TCP bic registered
Dec 20 21:53:36 localhost kernel: [   42.158653] NET: Registered protocol family 1
Dec 20 21:53:36 localhost kernel: [   42.158664] NET: Registered protocol family 8
Dec 20 21:53:36 localhost kernel: [   42.158667] NET: Registered protocol family 20
Dec 20 21:53:36 localhost kernel: [   42.158741] Freeing unused kernel memory: 180k init
Dec 20 21:53:36 localhost kernel: [   43.380370] Capability LSM initialized
Dec 20 21:53:36 localhost kernel: [   43.440944] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
Dec 20 21:53:36 localhost kernel: [   43.441092] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
Dec 20 21:53:36 localhost kernel: [   44.170537] hda: max request size: 1024KiB
Dec 20 21:53:36 localhost kernel: [   44.175733] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
Dec 20 21:53:36 localhost kernel: [   44.175751] Uniform CD-ROM driver Revision: 3.20
Dec 20 21:53:36 localhost kernel: [   44.219086] hda: 58605120 sectors (30005 MB), CHS=16383/255/63, UDMA(100)
Dec 20 21:53:36 localhost kernel: [   44.219167] hda: cache flushes supported
Dec 20 21:53:36 localhost kernel: [   44.219490]  hda: [mac] hda1 hda2 hda3 hda4
Dec 20 21:53:36 localhost kernel: [   44.807054] usbcore: registered new driver usbfs
Dec 20 21:53:36 localhost kernel: [   44.807669] usbcore: registered new driver hub
Dec 20 21:53:36 localhost kernel: [   44.811778] PCI: Enabling device 0001:10:1b.2 (0004 -> 0006)
Dec 20 21:53:36 localhost kernel: [   44.811803] ehci_hcd 0001:10:1b.2: EHCI Host Controller
Dec 20 21:53:36 localhost kernel: [   44.834794] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 1
Dec 20 21:53:36 localhost kernel: [   44.834818] ehci_hcd 0001:10:1b.2: irq 63, io mem 0x80080000
Dec 20 21:53:36 localhost kernel: [   44.834833] ehci_hcd 0001:10:1b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 20 21:53:36 localhost kernel: [   44.835347] hub 1-0:1.0: USB hub found
Dec 20 21:53:36 localhost kernel: [   44.835370] hub 1-0:1.0: 5 ports detected
Dec 20 21:53:36 localhost kernel: [   45.095636] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Dec 20 21:53:36 localhost kernel: [   45.096298] Apple USB OHCI 0001:10:18.0 disabled by firmware
Dec 20 21:53:36 localhost kernel: [   45.096311] Apple USB OHCI 0001:10:19.0 disabled by firmware
Dec 20 21:53:36 localhost kernel: [   45.096324] PCI: Enabling device 0001:10:1a.0 (0000 -> 0002)
Dec 20 21:53:36 localhost kernel: [   45.096348] ohci_hcd 0001:10:1a.0: OHCI Host Controller
Dec 20 21:53:36 localhost kernel: [   45.096662] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 2
Dec 20 21:53:36 localhost kernel: [   45.096682] ohci_hcd 0001:10:1a.0: irq 29, io mem 0x80083000
Dec 20 21:53:36 localhost kernel: [   45.130142] hub 2-0:1.0: USB hub found
Dec 20 21:53:36 localhost kernel: [   45.130168] hub 2-0:1.0: 2 ports detected
Dec 20 21:53:36 localhost kernel: [   45.148310] ieee1394: Initialized config rom entry `ip1394'
Dec 20 21:53:36 localhost kernel: [   45.234368] PCI: Enabling device 0001:10:1b.0 (0000 -> 0002)
Dec 20 21:53:36 localhost kernel: [   45.234397] ohci_hcd 0001:10:1b.0: OHCI Host Controller
Dec 20 21:53:36 localhost kernel: [   45.234591] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 3
Dec 20 21:53:36 localhost kernel: [   45.234608] ohci_hcd 0001:10:1b.0: irq 63, io mem 0x80082000
Dec 20 21:53:36 localhost kernel: [   45.269842] hub 3-0:1.0: USB hub found
Dec 20 21:53:36 localhost kernel: [   45.269864] hub 3-0:1.0: 3 ports detected
Dec 20 21:53:36 localhost kernel: [   45.370152] PCI: Enabling device 0001:10:1b.1 (0000 -> 0002)
Dec 20 21:53:36 localhost kernel: [   45.370167] ohci_hcd 0001:10:1b.1: OHCI Host Controller
Dec 20 21:53:36 localhost kernel: [   45.370331] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 4
Dec 20 21:53:36 localhost kernel: [   45.370343] ohci_hcd 0001:10:1b.1: irq 63, io mem 0x80081000
Dec 20 21:53:36 localhost kernel: [   45.405797] hub 4-0:1.0: USB hub found
Dec 20 21:53:36 localhost kernel: [   45.405813] hub 4-0:1.0: 2 ports detected
Dec 20 21:53:36 localhost kernel: [   45.508745] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
Dec 20 21:53:36 localhost kernel: [   45.508782] PCI: Enabling device 0002:20:0e.0 (0000 -> 0002)
Dec 20 21:53:36 localhost kernel: [   45.509369] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
Dec 20 21:53:36 localhost kernel: [   45.560538] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
Dec 20 21:53:36 localhost kernel: [   45.858255] Attempting manual resume
Dec 20 21:53:36 localhost kernel: [   45.967137] kjournald starting.  Commit interval 5 seconds
Dec 20 21:53:36 localhost kernel: [   45.967165] EXT3-fs: mounted filesystem with ordered data mode.
Dec 20 21:53:36 localhost kernel: [   46.834388] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001451fffe1c9822]
Dec 20 21:53:36 localhost kernel: [  104.649498] ts: Compaq touchscreen protocol output
Dec 20 21:53:36 localhost kernel: [  109.224928] Linux agpgart interface v0.101 (c) Dave Jones
Dec 20 21:53:36 localhost kernel: [  109.226966] agpgart: Detected Apple UniNorth 2 chipset
Dec 20 21:53:36 localhost kernel: [  109.227067] agpgart: configuring for size idx: 4
Dec 20 21:53:36 localhost kernel: [  109.227125] agpgart: AGP aperture is 16M @ 0x0
Dec 20 21:53:36 localhost kernel: [  109.243874] ieee80211_crypt: registered algorithm 'NULL'
Dec 20 21:53:36 localhost kernel: [  109.246439] ieee80211: 802.11 data/management/control stack, git-1.1.7
Dec 20 21:53:36 localhost kernel: [  109.246447] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 20 21:53:36 localhost kernel: [  109.329174] bcm43xx driver
Dec 20 21:53:36 localhost kernel: [  109.329366] PCI: Enabling device 0001:10:12.0 (0004 -> 0006)
Dec 20 21:53:36 localhost kernel: [  109.352711] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
Dec 20 21:53:36 localhost kernel: [  109.418286] PHY ID: 4061e4, addr: 0
Dec 20 21:53:36 localhost kernel: [  109.418995] eth1: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:14:51:1c:98:22 
Dec 20 21:53:36 localhost kernel: [  109.419004] eth1: Found BCM5221 PHY
Dec 20 21:53:36 localhost kernel: [  110.731442] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:53:36 localhost kernel: [  110.747775] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 21:53:36 localhost kernel: [  111.450039] NET: Registered protocol family 17
Dec 20 21:53:36 localhost kernel: [  111.818058] eth0: Link is up at 100 Mbps, full-duplex.
Dec 20 21:53:36 localhost kernel: [  111.818070] eth0: Pause is disabled
Dec 20 21:53:36 localhost kernel: [  111.914275] input: PowerMac Beep as /class/input/input4
Dec 20 21:53:36 localhost kernel: [  112.113621] apm_emu: APM Emulation 0.5 initialized.
Dec 20 21:53:36 localhost kernel: [  112.396497] SCSI subsystem initialized
Dec 20 21:53:36 localhost kernel: [  112.445774] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
Dec 20 21:53:36 localhost kernel: [  112.445784] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Dec 20 21:53:36 localhost kernel: [  112.445788] ieee1394: sbp2: Try serialize_io=0 for better performance
Dec 20 21:53:36 localhost kernel: [  112.697193] Adding 747832k swap on /dev/hda4.  Priority:-1 extents:1 across:747832k
Dec 20 21:53:36 localhost kernel: [  112.884039] EXT3 FS on hda3, internal journal
Dec 20 21:53:36 localhost kernel: [  113.274780] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Dec 20 21:53:36 localhost kernel: [  113.274790] md: bitmap version 4.39
Dec 20 21:53:36 localhost kernel: [  114.244818] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Dec 20 21:53:36 localhost kernel: [  115.528806] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  115.528819] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 20 21:53:36 localhost kernel: [  115.528826] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  115.529154] cdrom: open failed.
Dec 20 21:53:36 localhost kernel: [  119.715883] NET: Registered protocol family 10
Dec 20 21:53:36 localhost kernel: [  119.716105] lo: Disabled Privacy Extensions
Dec 20 21:53:36 localhost kernel: [  119.716385] IPv6 over IPv4 tunneling driver
Dec 20 21:53:36 localhost kernel: [  130.445930] eth0: no IPv6 routers present
Dec 20 21:53:36 localhost kernel: [  130.580396] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  130.580403] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120378
Dec 20 21:53:36 localhost kernel: [  130.580419] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  130.580428] end_request: I/O error, dev hda, sector 30120378
Dec 20 21:53:36 localhost kernel: [  138.959620] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  138.959632] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120386
Dec 20 21:53:36 localhost kernel: [  138.959648] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  138.959658] end_request: I/O error, dev hda, sector 30120386
Dec 20 21:53:36 localhost kernel: [  147.338828] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  147.338837] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:53:36 localhost kernel: [  147.338852] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  147.338859] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:53:36 localhost kernel: [  155.775031] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  155.775040] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:53:36 localhost kernel: [  155.775055] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  155.775062] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:53:36 localhost kernel: [  164.182731] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:36 localhost kernel: [  164.182739] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:53:36 localhost kernel: [  164.182754] ide: failed opcode was: unknown
Dec 20 21:53:36 localhost kernel: [  164.182759] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:53:38 localhost pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: ALSA. 
Dec 20 21:53:38 localhost pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Dec 20 21:53:39 localhost pbbuttonsd: INFO: pbbuttonsd 0.7.2: iBook/G3 PB Pismo/G4 PB Titanium (PMU version: 12) 
Dec 20 21:53:39 localhost anacron[3797]: Anacron 2.3 started on 2007-12-20
Dec 20 21:53:40 localhost anacron[3797]: Normal exit (0 jobs run)
Dec 20 21:53:40 localhost pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd powersave battery ' launched and exited normally 
Dec 20 21:53:40 localhost hpiod: 0.9.7 accepting connections at 48381... 
Dec 20 21:53:44 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Dec 20 21:53:44 localhost dhclient: send_packet: Network is down
Dec 20 21:53:47 localhost dhclient: No DHCPOFFERS received.
Dec 20 21:53:47 localhost dhclient: No working leases in persistent database - sleeping.
Dec 20 21:53:49 localhost ntpdate[3856]: step time server 91.189.94.4 offset 0.005108 sec
Dec 20 21:53:49 localhost kernel: [  179.957843] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:49 localhost kernel: [  179.957856] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:53:49 localhost kernel: [  179.957872] ide: failed opcode was: unknown
Dec 20 21:53:49 localhost kernel: [  179.957883] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:53:57 localhost kernel: [  188.408271] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:53:57 localhost kernel: [  188.408284] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:53:57 localhost kernel: [  188.408300] ide: failed opcode was: unknown
Dec 20 21:53:57 localhost kernel: [  188.408309] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:53:58 localhost kernel: [  188.781491] lp: driver loaded but no devices found
Dec 20 21:53:58 localhost kernel: [  188.924172] ppdev: user-space parallel port driver
Dec 20 21:53:59 localhost hcid[3980]: Bluetooth HCI daemon
Dec 20 21:53:59 localhost kernel: [  190.102105] Bluetooth: Core ver 2.8
Dec 20 21:53:59 localhost kernel: [  190.102117] NET: Registered protocol family 31
Dec 20 21:53:59 localhost kernel: [  190.102120] Bluetooth: HCI device and connection manager initialized
Dec 20 21:53:59 localhost kernel: [  190.102141] Bluetooth: HCI socket layer initialized
Dec 20 21:53:59 localhost kernel: [  190.126375] Bluetooth: L2CAP ver 2.8
Dec 20 21:53:59 localhost kernel: [  190.126387] Bluetooth: L2CAP socket layer initialized
Dec 20 21:53:59 localhost sdpd[3986]: Bluetooth SDP daemon 
Dec 20 21:53:59 localhost hcid[3980]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 20 21:53:59 localhost kernel: [  190.242911] Bluetooth: RFCOMM socket layer initialized
Dec 20 21:53:59 localhost kernel: [  190.242948] Bluetooth: RFCOMM TTY layer initialized
Dec 20 21:53:59 localhost kernel: [  190.242952] Bluetooth: RFCOMM ver 1.7
Dec 20 21:53:59 localhost anacron[4030]: Anacron 2.3 started on 2007-12-20
Dec 20 21:53:59 localhost anacron[4030]: Normal exit (0 jobs run)
Dec 20 21:54:00 localhost /usr/sbin/cron[4056]: (CRON) INFO (pidfile fd = 3)
Dec 20 21:54:00 localhost /usr/sbin/cron[4057]: (CRON) STARTUP (fork ok)
Dec 20 21:54:00 localhost /usr/sbin/cron[4057]: (CRON) INFO (Running @reboot jobs)
Dec 20 21:54:03 localhost kernel: [  194.073129] [drm] Initialized drm 1.0.1 20051102
Dec 20 21:54:03 localhost kernel: [  194.092437] [drm] Initialized radeon 1.24.0 20060225 on minor 0
Dec 20 21:54:04 localhost kernel: [  195.271816] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
Dec 20 21:54:04 localhost kernel: [  195.271837] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
Dec 20 21:54:04 localhost kernel: [  195.342127] [drm] Setting GART location based on old memory map
Dec 20 21:54:04 localhost kernel: [  195.342153] [drm] Loading R200 Microcode
Dec 20 21:54:04 localhost kernel: [  195.342214] [drm] writeback test succeeded in 1 usecs
Dec 20 21:54:12 localhost kdm_greet[4485]: Can't open default user face
Dec 20 21:54:23 localhost kdm_greet[4485]: Internal error: memory corruption detected
Dec 20 21:54:32 localhost kernel: [  223.449786] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:54:41 localhost kernel: [  223.449805] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:54:41 localhost kernel: [  223.449829] ide: failed opcode was: unknown
Dec 20 21:54:41 localhost kernel: [  223.449841] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:54:41 localhost kernel: [  231.985743] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec 20 21:54:41 localhost kernel: [  231.985762] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=30120400, high=1, low=13343184, sector=30120394
Dec 20 21:54:41 localhost kernel: [  231.985786] ide: failed opcode was: unknown
Dec 20 21:54:41 localhost kernel: [  231.985799] end_request: I/O error, dev hda, sector 30120394
Dec 20 21:57:15 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Dec 20 21:57:15 localhost dhclient: send_packet: Network is down
Dec 20 21:57:19 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 21:57:19 localhost dhclient: send_packet: Network is down
Dec 20 21:57:26 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Dec 20 21:57:26 localhost dhclient: send_packet: Network is down
Dec 20 21:57:38 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Dec 20 21:57:38 localhost dhclient: send_packet: Network is down
Dec 20 21:57:53 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 21:57:53 localhost dhclient: send_packet: Network is down
Dec 20 21:58:00 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Dec 20 21:58:00 localhost dhclient: send_packet: Network is down
Dec 20 21:58:16 localhost dhclient: No DHCPOFFERS received.
Dec 20 21:58:16 localhost dhclient: No working leases in persistent database - sleeping.
Dec 20 22:03:35 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 22:03:35 localhost dhclient: send_packet: Network is down
Dec 20 22:03:40 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Dec 20 22:03:40 localhost dhclient: send_packet: Network is down
Dec 20 22:03:51 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Dec 20 22:03:51 localhost dhclient: send_packet: Network is down
Dec 20 22:04:03 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 20 22:04:03 localhost dhclient: send_packet: Network is down
Dec 20 22:04:10 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Dec 20 22:04:10 localhost dhclient: send_packet: Network is down
Dec 20 22:04:31 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Dec 20 22:04:31 localhost dhclient: send_packet: Network is down
Dec 20 22:04:36 localhost dhclient: No DHCPOFFERS received.
Dec 20 22:04:36 localhost dhclient: No working leases in persistent database - sleeping.
Dec 20 22:09:40 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 20 22:09:40 localhost dhclient: send_packet: Network is down
Dec 20 22:09:48 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Dec 20 22:09:48 localhost dhclient: send_packet: Network is down
Dec 20 22:10:01 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Dec 20 22:10:01 localhost dhclient: send_packet: Network is down
Dec 20 22:10:08 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Dec 20 22:10:08 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Dec 20 22:10:08 localhost dhclient: All rights reserved.
Dec 20 22:10:08 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Dec 20 22:10:08 localhost dhclient: 
Dec 20 22:10:08 localhost firmware_helper[7522]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 22:10:08 localhost kernel: [ 1158.838815] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 22:10:08 localhost firmware_helper[7525]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with driver 'bcm43xx'
Dec 20 22:10:08 localhost kernel: [ 1158.893216] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Dec 20 22:10:09 localhost dhclient: Listening on LPF/eth1/00:11:24:94:a3:11
Dec 20 22:10:09 localhost dhclient: Sending on   LPF/eth1/00:11:24:94:a3:11
Dec 20 22:10:09 localhost dhclient: Sending on   Socket/fallback
Dec 20 22:10:09 localhost dhclient: receive_packet failed on eth1: Network is down
Dec 20 22:10:10 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 20 22:10:10 localhost dhclient: send_packet: Network is down
Dec 20 22:10:16 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 20 22:10:16 localhost dhclient: send_packet: Network is down
Dec 20 22:10:20 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Dec 20 22:10:20 localhost dhclient: send_packet: Network is down
Dec 20 22:10:30 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Dec 20 22:10:30 localhost dhclient: send_packet: Network is down
Dec 20 22:10:41 localhost dhclient: No DHCPOFFERS received.
Dec 20 22:10:41 localhost dhclient: No working leases in persistent database - sleeping.
Dec 20 22:10:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Dec 20 22:10:46 localhost dhclient: send_packet: Network is down


```

---

### Post by stmiller on 2007-12-20
Hey the airport extreme works automagically in the last two releases of Ubuntu. So try to upgrade to Feisty or Gutsy if possible for an easy solution, and newer kernel. 

For that older release, check out this page which might have some info to get it going:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

