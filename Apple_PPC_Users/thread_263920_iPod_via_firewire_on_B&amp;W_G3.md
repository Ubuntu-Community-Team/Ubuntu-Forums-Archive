---
title: "iPod via firewire on B&amp;W G3"
date: 2006-09-23
forum: Apple PPC Users
---

### Post by iamdigitalman on 2006-09-23
ok, new one here: my 4th gen U2 iPod (black and white screen), I connected it to my firewire port (one of the built in ones), and nothing happened. so, I found the iPod howto (except it had instructions for USB.), and I installed ipodslave, rebooted the computer, reset the iPod, and plugged it in. nothing happened, so I rebooted the computer again with the ipod plugged in (just to be safe), and it still didnt come up on the desktop automagically. so, I popped open terminal, ran dmesg, and here is the output:

> [    0.000000] Total memory = 512MB; using 1024kB for hash table (at cff00000)
[    0.000000] Linux version 2.6.15-27-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Sat Sep 16 01:55:03 UTC 2006
[    0.000000] Found initrd at 0xc1900000:0xc20b8000
[    0.000000] Found a Paddington mac-io controller, rev: 0, mapped at 0xfdf80000
[    0.000000] PowerMac motherboard: Blue&White G3
[    0.000000] Found Grackle (MPC106) PCI host bridge at 0x80000000. Firmware bus number: 0->1
[    0.000000] nvram: OF partition at 0x140
[    0.000000] nvram: XP partition at 0x11b0
[    0.000000] nvram: NR partition at 0x12b0
[    0.000000] Top of RAM: 0x20000000, Total RAM: 0x20000000
[    0.000000] Memory hole size: 0MB
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 131072 pages, LIFO batch:31
[    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hdc3 ro quiet splash
[    0.000000] irq: Found primary Apple PIC /pci@80000000/pci-bridge@d/mac-io@5 for 64 irqs
[    0.000000] irq: System has 64 possible interrupts
[    0.000000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[    0.000000] GMT Delta read from XPRAM: -240 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 24.934150 MHz
[    0.000000] time_init: processor frequency   = 400.000000 MHz
[   31.641070] Console: colour dummy device 80x25
[   31.644431] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.647832] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.702323] High memory: 0k
[   31.702341] Memory: 506368k/524288k available (2692k kernel code, 17492k reserved, 276k data, 304k bss, 180k init)
[   31.702668] Calibrating delay loop... 49.79 BogoMIPS (lpj=99584)
[   31.780059] Security Framework v1.0.0 initialized
[   31.780095] SELinux:  Disabled at boot.
[   31.780155] Mount-cache hash table entries: 512
[   31.780666] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,750@0
[   31.782870] checking if image is initramfs... it is
[   34.155551] Freeing initrd memory: 7904k freed
[   34.158636] NET: Registered protocol family 16
[   34.158995] Registering pmac pic with sysfs...
[   34.159106] PCI: Probing PCI hardware
[   34.164030] Thermal assist unit using timers, shrink_timer: 500 jiffies
[   34.166013] audit: initializing netlink socket (disabled)
[   34.166048] audit(1159070566.520:1): initialized
[   34.166425] VFS: Disk quotas dquot_6.5.1
[   34.166504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.166692] Initializing Cryptographic API
[   34.166711] io scheduler noop registered
[   34.166733] io scheduler anticipatory registered
[   34.166762] io scheduler deadline registered
[   34.166820] io scheduler cfq registered
[   34.167418] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[   34.168615] aty128fb: Found Open Firmware ROM Image
[   34.168638] aty128fb: BIOS not located, guessing timings.
[   34.168659] aty128fb: Rage128 RE PCI [chip rev 0x2] 16M 128-bit SDR SGRAM (1:1)
[   34.209325] Console: switching to colour frame buffer device 128x48
[   34.209351] fb0: ATY Rage128 frame buffer device on Rage128 RE PCI
[   34.276500] Macintosh non-volatile memory driver v1.1
[   34.276709] IN from bad port 64 at c018d298
[   34.276772] IN from bad port 60 at c018d2cc
[   34.276783] IN from bad port 64 at c018d298
[   34.276843] IN from bad port 60 at c018d2cc
[   34.276854] IN from bad port 64 at c018d298
[   34.276913] IN from bad port 60 at c018d2cc
[   34.276924] IN from bad port 64 at c018d298
[   34.276983] IN from bad port 60 at c018d2cc
[   34.276994] IN from bad port 64 at c018d298
[   34.277054] IN from bad port 60 at c018d2cc
[   34.277065] IN from bad port 64 at c018d298
[   34.277124] IN from bad port 60 at c018d2cc
[   34.277135] IN from bad port 64 at c018d298
[   34.277194] IN from bad port 60 at c018d2cc
[   34.277205] IN from bad port 64 at c018d298
[   34.277264] IN from bad port 60 at c018d2cc
[   34.277275] IN from bad port 64 at c018d298
[   34.277335] IN from bad port 60 at c018d2cc
[   34.277346] IN from bad port 64 at c018d298
[   34.277405] IN from bad port 60 at c018d2cc
[   34.277416] IN from bad port 64 at c018d298
[   34.277475] IN from bad port 60 at c018d2cc
[   34.277486] IN from bad port 64 at c018d298
[   34.277545] IN from bad port 60 at c018d2cc
[   34.277556] IN from bad port 64 at c018d298
[   34.277616] IN from bad port 60 at c018d2cc
[   34.277627] IN from bad port 64 at c018d298
[   34.277686] IN from bad port 60 at c018d2cc
[   34.277697] IN from bad port 64 at c018d298
[   34.277756] IN from bad port 60 at c018d2cc
[   34.277767] IN from bad port 64 at c018d298
[   34.277826] IN from bad port 60 at c018d2cc
[   34.277838] IN from bad port 64 at c018d298
[   34.277847] i8042.c: No controller found.
[   34.279543] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.279873] MacIO PCI driver attached to Paddington chipset
[   34.280762] Can't request resource 0 for MacIO device 0.00000000:power-mg
[   34.282312] input: Macintosh mouse button emulation as /class/input/input0
[   34.282400] Macintosh CUDA driver v0.5 for Unified ADB.
[   34.282546] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.282565] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.282612] adb: starting probe task...
[   34.360739] adb devices: [2]: 2 2
[   34.384406] ADB keyboard at 2, handler set to 3
[   34.384439] Detected ADB keyboard, type ANSI.
[   34.384631] input: ADB keyboard as /class/input/input1
[   34.384655] adb: finished probe task...
[   35.307946] ide0: Found Apple Heathrow ATA controller, bus ID 0, irq 13
[   35.307989] Probing IDE interface ide0...
[   35.708138] hda: SAMSUNG CDRW/DVD SM-308B, ATAPI CD/DVD-ROM drive
[   36.156129] hdb: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[   36.211962] hda: Enabling MultiWord DMA 2
[   36.230378] ide0 at 0xe100e000-0xe100e007,0xe100e160 on irq 13
[   36.231050] mice: PS/2 mouse device common for all mice
[   36.231288] NET: Registered protocol family 2
[   36.264131] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)[   36.265433] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   36.269066] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   36.270900] TCP: Hash tables configured (established 131072 bind 65536)
[   36.270914] TCP reno registered
[   36.271224] TCP bic registered
[   36.271253] NET: Registered protocol family 1
[   36.271280] NET: Registered protocol family 8
[   36.271290] NET: Registered protocol family 20
[   36.271467] Freeing unused kernel memory: 180k init
[   37.683171] Capability LSM initialized
[   40.093879] hda: ATAPI 32X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   40.093921] Uniform CD-ROM driver Revision: 3.20
[   42.452961] CMD646: IDE controller at PCI slot 0000:01:01.0
[   42.453022] CMD646: chipset revision 5
[   42.453035] CMD646: chipset revision 0x05, UltraDMA Capable
[   42.453071] CMD646: 100% native mode on irq 26
[   42.453099]     ide1: BM-DMA at 0x1050-0x1057, BIOS settings: hdc:pio, hdd:pio
[   42.453141]     ide2: BM-DMA at 0x1058-0x105f, BIOS settings: hde:pio, hdf:pio
[   42.453178] Probing IDE interface ide1...
[   42.740104] hdc: ST3120026A, ATA DISK drive
[   43.412535] ide1 at 0x1090-0x1097,0x1082 on irq 26
[   43.413087] Probing IDE interface ide2...
[   44.020536] hdc: max request size: 1024KiB
[   44.021199] hdc: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(33)
[   44.021369] hdc: cache flushes supported
[   44.021893]  hdc: [mac] hdc1 hdc2 hdc3 hdc4
[   44.757956] usbcore: registered new driver usbfs
[   44.760411] usbcore: registered new driver hub
[   44.769282] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   44.771772] ohci_hcd 0000:01:02.0: OHCI Host Controller
[   44.772972] ohci_hcd 0000:01:02.0: new USB bus registered, assigned bus number 1
[   44.773007] ohci_hcd 0000:01:02.0: irq 23, io mem 0x80883000
[   44.850247] hub 1-0:1.0: USB hub found
[   44.850300] hub 1-0:1.0: 3 ports detected
[   44.952665] ohci_hcd 0000:01:02.1: OHCI Host Controller
[   44.953166] ohci_hcd 0000:01:02.1: new USB bus registered, assigned bus number 2
[   44.953200] ohci_hcd 0000:01:02.1: irq 23, io mem 0x80882000
[   45.028255] hub 2-0:1.0: USB hub found
[   45.028311] hub 2-0:1.0: 2 ports detected
[   45.132465] ohci_hcd 0000:01:06.0: OHCI Host Controller
[   45.132961] ohci_hcd 0000:01:06.0: new USB bus registered, assigned bus number 3
[   45.132989] ohci_hcd 0000:01:06.0: irq 28, io mem 0x80881000
[   45.133038] PCI: Enabling device 0000:01:02.2 (0014 -> 0016)
[   45.133059] ehci_hcd 0000:01:02.2: EHCI Host Controller
[   45.156427] ehci_hcd 0000:01:02.2: new USB bus registered, assigned bus number 4
[   45.156452] ehci_hcd 0000:01:02.2: irq 23, io mem 0x80880000
[   45.156477] ehci_hcd 0000:01:02.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   45.157469] hub 4-0:1.0: USB hub found
[   45.157521] hub 4-0:1.0: 5 ports detected
[   45.261485] hub 3-0:1.0: USB hub found
[   45.261539] hub 3-0:1.0: 2 ports detected
[   46.005469] Attempting manual resume
[   46.134593] kjournald starting.  Commit interval 5 seconds
[   46.134637] EXT3-fs: mounted filesystem with ordered data mode.
[   46.144009] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   46.675972] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   46.891924] hub 1-1:1.0: USB hub found
[   46.894837] hub 1-1:1.0: 4 ports detected
[   47.319981] usb 1-3: new full speed USB device using ohci_hcd and address 4
[   47.535814] hub 1-3:1.0: USB hub found
[   47.538735] hub 1-3:1.0: 4 ports detected
[   47.873723] usb 1-1.2: new low speed USB device using ohci_hcd and address 5
[   48.213712] usb 1-3.4: new full speed USB device using ohci_hcd and address 6[   53.864908] ts: Compaq touchscreen protocol output
[   63.706565] ieee1394: Initialized config rom entry `ip1394'
[   63.754922] PCI: Enabling device 0000:01:00.0 (0014 -> 0016)
[   63.756509] pcilynx0: allocated PCL memory 4096 Bytes @ 0xc0908000
[   63.756637] pcilynx0: allocated interrupt 21
[   63.756654] pcilynx0: remapped memory spaces reg 0xe2090000, rom 0xe2160000, ram 0xe20e0000, aux 0xe2140000
[   63.756672] pcilynx0: found 1394a conform PHY (using extended register set)
[   63.756694] pcilynx0: PHY vendor id 0x080028
[   63.756712] pcilynx0: PHY product id 0x000000
[   63.761051] pcilynx0: got bus info block from serial eeprom
[   63.761066] pcilynx0: read a valid bus info block from
[   64.760012] pcilynx0: resetting bus (short bus reset) on request
[   64.760042] pcilynx0: bus reset interrupt
[   64.763945] pcilynx0: SelfID process finished (phyid 1, root)
[   64.763959] pcilynx0: SelfID packet 0x807f8780 rcvd
[   64.763971] pcilynx0: SelfID packet 0x817f8c76 rcvd
[   65.040080] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a270002bf7144]
[   65.042519] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0800070200000000]
[   66.066899] SCSI subsystem initialized
[   66.085232] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   66.085247] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   66.085259] ieee1394: sbp2: Try serialize_io=0 for better performance
[   66.085529] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
[   68.232263] usbcore: registered new driver hiddev
[   68.234088] drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
[   68.242892] drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0304
[   68.243579] usbcore: registered new driver usblp
[   68.243594] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver[   68.294384] ide-floppy driver 0.99.newide
[   68.415545] input: Logitech Apple Optical USB Mouse as /class/input/input2
[   68.416975] input: USB HID v1.10 Mouse [Logitech Apple Optical USB Mouse] on usb-0000:01:02.0-1.2
[   68.417028] usbcore: registered new driver usbhid
[   68.417040] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   68.441177] hdb: 98304kB, 196608 blocks, 512 sector size
[   68.490149] hdb: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[   68.680729]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[   69.286801]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[   69.718833]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[   87.895942] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out[   87.897689] sbp2: probe of 000a270002bf7144-0 failed with error -16
[   89.133260] eth0: BMAC+ at 00:50:e4:a0:58:02
[   89.328136] mesh: configured for synchronous 5 MB/s
[   89.511103] phy registers:
[   89.511121]  1400 782d 7810 0001 00a1 41e1 0001 0000
[   89.521433]  0000 0000 0000 0000 0000 0000 0000 0000
[   89.531740]  0000 0000 4000 0000 2ffb 0010 0000 0002
[   89.542048]  0001 0000 0000 0000 0000 0000 0000 0000
[   89.588098] mesh: performing initial bus reset...
[   90.683995] NET: Registered protocol family 17
[   93.439583] NET: Registered protocol family 10
[   93.440039] lo: Disabled Privacy Extensions
[   93.440563] IPv6 over IPv4 tunneling driver
[   93.591975] scsi1 : MESH
[   96.547046] input: PowerMac Beep as /class/input/input3
[   97.446643] Adding 1508868k swap on /dev/hdc4.  Priority:-1 extents:1 across:1508868k
[   97.672530] EXT3 FS on hdc3, internal journal
[   98.344275] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   98.344296] md: bitmap version 4.39
[   99.044073]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[   99.907804]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  100.731772]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  101.483818]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  102.303796]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  103.075750]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  103.535946] eth0: no IPv6 routers present
[  104.351913] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  105.015867]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  105.827739]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  106.563801]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  107.375738]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  108.235730]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  108.879802]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  109.607730]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  110.379810]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  111.568241] cdrom: open failed.
[  111.767703]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5
[  130.297746] lp: driver loaded but no devices found
[  130.638742] ppdev: user-space parallel port driver
[  133.231233] Linux agpgart interface v0.101 (c) Dave Jones
[  133.284929] [drm] Initialized drm 1.0.1 20051102
[  133.312640] [drm] Initialized r128 2.5.0 20030725 on minor 0
[  139.696772] NET: Registered protocol family 5
[  190.038064] Bluetooth: Core ver 2.8
[  190.038088] NET: Registered protocol family 31
[  190.038098] Bluetooth: HCI device and connection manager initialized
[  190.038136] Bluetooth: HCI socket layer initialized
[  190.125336] Bluetooth: L2CAP ver 2.8
[  190.125358] Bluetooth: L2CAP socket layer initialized
[  190.255565] Bluetooth: RFCOMM socket layer initialized
[  190.255625] Bluetooth: RFCOMM TTY layer initialized
[  190.255636] Bluetooth: RFCOMM ver 1.7
[ 5931.704651] pcilynx0: bus reset interrupt
[ 5931.704697] pcilynx0: SelfID process finished (phyid 0, root)
[ 5931.704710] pcilynx0: SelfID packet 0x807f8c56 rcvd
[ 5931.983238] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 5931.983612] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a270002bf7144]
[ 6483.457730] pcilynx0: bus reset interrupt
[ 6483.457894] pcilynx0: SelfID process finished (phyid 1, root)
[ 6483.458103] pcilynx0: SelfID process finished (phyid 1, root)
[ 6483.458115] pcilynx0: SelfID packet 0x807f8782 rcvd
[ 6483.458128] ieee1394: Spurious SelfID packet (0x807f8782) received from bus 1023
[ 6483.458142] pcilynx0: SelfID packet 0x817f8c74 rcvd
[ 6483.458154] ieee1394: Spurious SelfID packet (0x817f8c74) received from bus 1023
[ 6483.458167] ieee1394: SelfID completion called outside of bus reset!
[ 6483.728147] ieee1394: impossible ack_complete from node 65535 (tcode 4)
[ 6483.728177] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 6483.728925] pcilynx0: resetting bus (long bus reset, force_root set) on request
[ 6483.728946] pcilynx0: bus reset interrupt
[ 6483.729134] pcilynx0: SelfID process finished (phyid 1, root)
[ 6483.729149] pcilynx0: SelfID packet 0x807f8780 rcvd
[ 6483.729161] pcilynx0: SelfID packet 0x817f8c76 rcvd
[ 6484.001760] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a270002bf7144][ 6484.002353] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 6484.003273] scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices
[ 6505.900202] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out[ 6505.903886] sbp2: probe of 000a270002bf7144-0 failed with error -16
[ 7447.985264] pcilynx0: bus reset interrupt
[ 7447.985310] pcilynx0: SelfID process finished (phyid 0, root)
[ 7447.985323] pcilynx0: SelfID packet 0x807f8c56 rcvd
[ 7448.256250] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 7448.256633] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a270002bf7144]
[ 7464.436025] pcilynx0: bus reset interrupt
[ 7464.436190] pcilynx0: SelfID process finished (phyid 1, root)
[ 7464.436398] pcilynx0: SelfID process finished (phyid 1, root)
[ 7464.436411] pcilynx0: SelfID packet 0x807f8782 rcvd
[ 7464.436424] ieee1394: Spurious SelfID packet (0x807f8782) received from bus 1023
[ 7464.436438] pcilynx0: SelfID packet 0x817f8c74 rcvd
[ 7464.436449] ieee1394: Spurious SelfID packet (0x817f8c74) received from bus 1023
[ 7464.436462] ieee1394: SelfID completion called outside of bus reset!
[ 7464.708554] ieee1394: impossible ack_complete from node 65535 (tcode 4)
[ 7464.708582] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 7464.709329] pcilynx0: resetting bus (long bus reset, force_root set) on request
[ 7464.709350] pcilynx0: bus reset interrupt
[ 7464.709538] pcilynx0: SelfID process finished (phyid 1, root)
[ 7464.709553] pcilynx0: SelfID packet 0x807f8780 rcvd
[ 7464.709565] pcilynx0: SelfID packet 0x817f8c76 rcvd
[ 7464.982175] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a270002bf7144][ 7464.982762] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 7464.983298] scsi3 : SCSI emulation for IEEE-1394 SBP-2 Devices
[ 7486.875947] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out[ 7486.877923] sbp2: probe of 000a270002bf7144-0 failed with error -16


note the last few lines. iee1394, that's my firewire interface, right? why is it trying (and failing) to log into the interface? do I have a bad firewire module, or what else is it?

thanks.

EDIT: fogot to mention that it IS charging the iPod, so atleast I have that going for me. the module is getting power. oh, and no I dont have any other firewire devices to test with. I also dont have an iPod USB cable to test that interface with, but i could hit up the apple store for one, if needed.

-digital ;)

---

### Post by iamdigitalman on 2006-09-26
please, somebody has got to know. there HAS GOT to be somebody with the same machine (and I know there are), with the same generation of iPod (4th gen B&W), and the same connection cable (offical apple firewire cable bought 2 months ago at CompUSA), and with the same issue.

dont make me go get a PCI firewire card. I really dont have the money or a free PCI slot.

thanks. -digital ;)

---

### Post by iamdigitalman on 2006-09-28
ok, I am getting closer.

I did reboot the pod, and boot in diagnostic mode (center button and menu simotaniously to reboot, and center boutton an rewind simotaniously for diag mode at the apple logo. if done right, the backlight should come on, then you will se a backwards apple logo, then it will say iramtest. hit play, you'll see the screen go funky, then you'll hear a beep. backwards and forewards to go up and down the list (3 screens worth of options), and play AND center button to sellect/activate), and I went under firewire test. it shows it is hooked to both power AND data, when I try it on BOTH ports, I get the exact same thing. I also went under the hidden disk mode in the diag menu, hit it, it reboots, I get the do not disconnect screen FOR A SECOND, then I get the OK to disconnect.]

hopefully somebody has an answer. ](*,) 

oh, and despite what it says in the little blurb in the corner, I am NOT using edgy. I only download burn and test each knot as it comes out, and play with it for a few hours, but dapper is my current home. looking good devs. keep up the good work. cant wait to use it as my primary system.

-digital ;)

---

