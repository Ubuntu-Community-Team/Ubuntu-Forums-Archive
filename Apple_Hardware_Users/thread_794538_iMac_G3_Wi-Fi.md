---
title: "iMac G3 Wi-Fi"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by violinmandan on 2008-05-14
I just got a "new" iMac G3 (600MHz) from a professor who was throwing it away. I want to get wireless working. I just got an AirPort card and adapter from eBay, but after I installed it, it's not even detected (I'm using Xubuntu 6.06). 
I didn't expect this venture to be without trouble, so if someone could point me in the right direction, I would appreciate it.

---

### Post by ssam on 2008-05-15
can you post the output of the commands
```
dmesg
```
and
```
iwconfig
```

---

### Post by violinmandan on 2008-05-15
dmesg:
```
[    0.000000] Total memory = 256MB; using 512kB for hash table (at cff80000)
[    0.000000] Linux version 2.6.15-51-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Tue Feb 12 16:54:18 UTC 2008
[    0.000000] Found initrd at 0xc1900000:0xc20c6000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xc0
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Pangea mac-io controller, rev: 0, mapped at 0xfdf40000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: iMac "Flower Power"
[    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver 2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=338, gen1=337
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x210
[    0.000000] nvram: XP partition at 0x1220
[    0.000000] nvram: NR partition at 0x1320
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
[    0.000000] GMT Delta read from XPRAM: -300 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 24.960000 MHz
[    0.000000] time_init: processor frequency   = 600.000000 MHz
[   23.197378] Console: colour dummy device 80x25
[   23.199075] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.200501] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.227614] High memory: 0k
[   23.227629] Memory: 247296k/262144k available (2692k kernel code, 14528k reserved, 276k data, 304k bss, 180k init)
[   23.227892] Calibrating delay loop... 49.79 BogoMIPS (lpj=99584)
[   23.305132] Security Framework v1.0.0 initialized
[   23.305168] SELinux:  Disabled at boot.
[   23.305215] Mount-cache hash table entries: 512
[   23.305663] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,750@0
[   23.307574] checking if image is initramfs... it is
[   24.933225] Freeing initrd memory: 7960k freed
[   24.935812] NET: Registered protocol family 16
[   24.936267] PCI: Probing PCI hardware
[   24.942103] Thermal assist unit using timers, shrink_timer: 500 jiffies
[   24.943646] audit: initializing netlink socket (disabled)
[   24.943689] audit(1210899112.740:1): initialized
[   24.944021] VFS: Disk quotas dquot_6.5.1
[   24.944100] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.944288] Initializing Cryptographic API
[   24.944305] io scheduler noop registered
[   24.944328] io scheduler anticipatory registered
[   24.944344] io scheduler deadline registered
[   24.944383] io scheduler cfq registered
[   24.944983] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[   24.945840] aty128fb: Invalid ROM signature 8181 should  be 0xaa55
[   24.945861] aty128fb: BIOS not located, guessing timings.
[   24.945880] aty128fb: Rage128 TR Ultra AGP [chip rev 0x4] 16M 128-bit SDR SGRAM (1:1)
[   24.979133] Console: switching to colour frame buffer device 128x48
[   24.979173] fb0: ATY Rage128 frame buffer device on Rage128 TR Ultra AGP
[   25.037367] Macintosh non-volatile memory driver v1.1
[   25.037615] IN from bad port 64 at c018d668
[   25.037676] IN from bad port 60 at c018d69c
[   25.037684] IN from bad port 64 at c018d668
[   25.037740] IN from bad port 60 at c018d69c
[   25.037748] IN from bad port 64 at c018d668
[   25.037804] IN from bad port 60 at c018d69c
[   25.037811] IN from bad port 64 at c018d668
[   25.037867] IN from bad port 60 at c018d69c
[   25.037875] IN from bad port 64 at c018d668
[   25.037931] IN from bad port 60 at c018d69c
[   25.037939] IN from bad port 64 at c018d668
[   25.037995] IN from bad port 60 at c018d69c
[   25.038003] IN from bad port 64 at c018d668
[   25.038059] IN from bad port 60 at c018d69c
[   25.038066] IN from bad port 64 at c018d668
[   25.038122] IN from bad port 60 at c018d69c
[   25.038130] IN from bad port 64 at c018d668
[   25.038186] IN from bad port 60 at c018d69c
[   25.038194] IN from bad port 64 at c018d668
[   25.038250] IN from bad port 60 at c018d69c
[   25.038258] IN from bad port 64 at c018d668
[   25.038314] IN from bad port 60 at c018d69c
[   25.038321] IN from bad port 64 at c018d668
[   25.038377] IN from bad port 60 at c018d69c
[   25.038385] IN from bad port 64 at c018d668
[   25.038441] IN from bad port 60 at c018d69c
[   25.038449] IN from bad port 64 at c018d668
[   25.038505] IN from bad port 60 at c018d69c
[   25.038513] IN from bad port 64 at c018d668
[   25.038569] IN from bad port 60 at c018d69c
[   25.038576] IN from bad port 64 at c018d668
[   25.038632] IN from bad port 60 at c018d69c
[   25.038640] IN from bad port 64 at c018d668
[   25.038647] i8042.c: No controller found.
[   25.039920] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.040250] MacIO PCI driver attached to Pangea chipset
[   25.042293] input: Macintosh mouse button emulation as /class/input/input0
[   25.042669] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.042689] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.042727] adb: starting probe task...
[   25.042742] adb: finished probe task...
[   26.061054] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[   26.061103] Probing IDE interface ide0...
[   26.349365] hda: Maxtor 34098H4 B, ATA DISK drive
[   26.797355] hdb: MATSHITA CD-RW CW-7121, ATAPI CD/DVD-ROM drive
[   26.853061] hda: Enabling Ultra DMA 2
[   26.854069] hdb: Enabling MultiWord DMA 2
[   26.856115] ide0 at 0xd100e000-0xd100e007,0xd100e160 on irq 19
[   26.856798] mice: PS/2 mouse device common for all mice
[   26.857023] NET: Registered protocol family 2
[   26.893257] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   26.893811] TCP established hash table entries: 16384 (order: 4, 65536 bytes)[   26.894229] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   26.894632] TCP: Hash tables configured (established 16384 bind 16384)
[   26.894643] TCP reno registered
[   26.894875] TCP bic registered
[   26.894894] NET: Registered protocol family 1
[   26.894921] NET: Registered protocol family 8
[   26.894928] NET: Registered protocol family 20
[   26.895095] Freeing unused kernel memory: 180k init
[   28.245909] Capability LSM initialized
[   28.358217] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
[   28.358510] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
[   30.130524] hda: max request size: 128KiB
[   30.164163] hda: Host Protected Area detected.
[   30.164175]  current capacity is 80023104 sectors (40971 MB)
[   30.164180]  native  capacity is 80043264 sectors (40982 MB)
[   30.164499] hda: Host Protected Area disabled.
[   30.164510] hda: 80043264 sectors (40982 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   30.164529] hda: cache flushes not supported
[   30.165185]  hda: [mac] hda1 hda2 hda3 hda4
[   30.264148] hdb: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   30.264185] Uniform CD-ROM driver Revision: 3.20
[   30.918448] usbcore: registered new driver usbfs
[   30.919858] usbcore: registered new driver hub
[   30.926026] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   30.927396] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
[   30.927445] ohci_hcd 0001:10:18.0: OHCI Host Controller
[   30.929142] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[   30.929180] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[   31.426883] hub 1-0:1.0: USB hub found
[   31.426949] hub 1-0:1.0: 2 ports detected
[   31.440759] ieee1394: Initialized config rom entry `ip1394'
[   31.529748] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
[   31.529799] ohci_hcd 0001:10:19.0: OHCI Host Controller
[   31.530239] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[   31.530276] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[   31.565162] hub 2-0:1.0: USB hub found
[   31.565214] hub 2-0:1.0: 2 ports detected
[   31.669833] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   31.671817] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[   31.817066] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[   31.817170] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
[   31.913385] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[   31.969148] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   32.157023] Attempting manual resume
[   32.307383] kjournald starting.  Commit interval 5 seconds
[   32.307432] EXT3-fs: mounted filesystem with ordered data mode.
[   32.373151] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   32.587302] usbcore: registered new driver hiddev
[   32.594293] input: Dell Dell USB Keyboard as /class/input/input1
[   32.594338] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0001:10:18.0-1
[   32.606204] input: Logitech USB RECEIVER as /class/input/input2
[   32.606261] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0001:10:19.0-1
[   32.606293] usbcore: registered new driver usbhid
[   32.606302] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   33.009313] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[   42.134299] ts: Compaq touchscreen protocol output
[   45.830901] Linux agpgart interface v0.101 (c) Dave Jones
[   45.842781] agpgart: Detected Apple UniNorth/Pangea chipset
[   45.843065] agpgart: configuring for size idx: 4
[   45.847655] agpgart: AGP aperture is 16M @ 0x0
[   47.068963] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   47.133412] PHY ID: 406212, addr: 0
[   47.134674] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:04:4f:e8
[   47.134696] eth0: Found BCM5201 PHY
[   48.863342] apm_emu: APM Emulation 0.5 initialized.
[   48.994578] SCSI subsystem initialized
[   49.018196] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   49.018221] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   49.018229] ieee1394: sbp2: Try serialize_io=0 for better performance
[   49.790715] NET: Registered protocol family 17
[   50.232339] input: PowerMac Beep as /class/input/input3
[   50.937158] Adding 747176k swap on /dev/hda4.  Priority:-1 extents:1 across:747176k
[   51.187837] EXT3 FS on hda3, internal journal
[   51.802333] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   51.802353] md: bitmap version 4.39
[   53.144221] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   54.717758] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   54.717784] hdb: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[   54.717797] ide: failed opcode was: unknown
[   54.718156] cdrom: open failed.
[   73.615998] lp: driver loaded but no devices found
[   73.903417] ppdev: user-space parallel port driver
[   76.205711] NET: Registered protocol family 10
[   76.206101] lo: Disabled Privacy Extensions
[   76.206301] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.206403] IPv6 over IPv4 tunneling driver

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

