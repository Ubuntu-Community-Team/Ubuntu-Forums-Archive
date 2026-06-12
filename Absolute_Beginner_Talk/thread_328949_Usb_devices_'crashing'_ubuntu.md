---
title: "Usb devices 'crashing' ubuntu"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2006-12-31
Evening All,

Been having this problem since install really. Every time i connect a usb device after boot it crashes. It does it on my usb storage stick, camera, and recently printer. ](*,) 

If i have them pluged in during boot everythings fine. Unless i disconnect them, and then reconnect. At which point i have the same problem. :confused: 

Cheers in advance for any help! 

Mr Bond

---

### Post by pseudonym on 2006-12-31
Hi, what messages do you get when you plug the drives in after boot? If you don't know, open up a console and type 'dmesg' , then look for things related to usb (should be the last few lines). Post back with the output...

PS - James Bond, on a computer, on the internet, on New Year's Eve?...Not a good look :D

---

### Post by Mr_Bond_UK on 2006-12-31
Yes, i should be out saving the world and all, but somethings are just more important!

here's the read out

[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fadd0
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x3fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x3fff0030
[17179569.184000] ACPI: DSDT (v001    VIA APOLLO-P 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01803000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[    0.000000] Detected 800.092 MHz processor.
[   51.810461] Using tsc for high-res timesource
[   51.811547] Console: colour VGA+ 80x25
[   51.813257] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   51.817792] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   51.952146] Memory: 1028816k/1048512k available (1976k kernel code, 18940k reserved, 606k data, 288k init, 131008k highmem)
[   51.952159] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   52.030644] Calibrating delay using timer specific routine.. 1602.78 BogoMIPS (lpj=3205574)
[   52.030759] Security Framework v1.0.0 initialized
[   52.030816] SELinux:  Disabled at boot.
[   52.030863] Mount-cache hash table entries: 512
[   52.031209] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   52.031236] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   52.031259] CPU: L1 I cache: 16K, L1 D cache: 16K
[   52.031266] CPU: L2 cache: 256K
[   52.031274] CPU serial number disabled.
[   52.031282] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   52.031336] mtrr: v2.0 (20020519)
[   52.031349] CPU: Intel Pentium III (Coppermine) stepping 06
[   52.031360] Enabling fast FPU save and restore... done.
[   52.031366] Enabling unmasked SIMD FPU exception support... done.
[   52.031379] Checking 'hlt' instruction... OK.
[   52.047266] checking if image is initramfs... it is
[   53.947539] Freeing initrd memory: 6616k freed
[   53.972519] NET: Registered protocol family 16
[   53.972595] EISA bus registered
[   53.987684] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   53.987704] PCI: Using configuration type 1
[   53.988747] ACPI: Subsystem revision 20051216
[   53.988754] ACPI: Interpreter disabled.
[   53.988762] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.988780] pnp: PnP ACPI: disabled
[   53.988792] PnPBIOS: Scanning system for PnP BIOS support...
[   53.988858] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6f00
[   53.988866] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6004, dseg 0xf0000[   53.989615] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   53.989720] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   53.989816] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   53.989902] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   53.990036] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   53.990101] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   53.990157] PCI: Probing PCI hardware
[   53.990170] PCI: Probing PCI hardware (bus 00)
[   53.990582] PCI quirk: region 5000-50ff claimed by vt82c586 ACPI
[   53.990591] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   53.990599] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[   53.991102] Boot video device is 0000:01:00.0
[   53.992257] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   53.995350] PCI: Bridge: 0000:00:01.0
[   53.995359]   IO window: 9000-9fff
[   53.995368]   MEM window: dde00000-dfefffff
[   53.995375]   PREFETCH window: cdc00000-ddcfffff
[   53.995400] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   53.996383] audit: initializing netlink socket (disabled)
[   53.996417] audit(1167599965.900:1): initialized
[   53.996567] highmem bounce pool size: 64 pages
[   53.996705] VFS: Disk quotas dquot_6.5.1
[   53.996775] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   53.996904] Initializing Cryptographic API
[   53.996915] io scheduler noop registered
[   53.996930] io scheduler anticipatory registered
[   53.996941] io scheduler deadline registered
[   53.996965] io scheduler cfq registered
[   53.996979] PCI: Disabling Via external APIC routing
[   53.997470] isapnp: Scanning for PnP cards...
[   54.351970] isapnp: No Plug & Play device found
[   54.391066] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   54.391348] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.391469] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.391551] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   54.391752] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.391978] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.397815] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.398218] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.399384] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.399513] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   54.399524] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   54.399849] mice: PS/2 mouse device common for all mice
[   54.400124] EISA: Probing bus 0 at eisa.0
[   54.400161] Cannot allocate resource for EISA slot 5
[   54.400167] Cannot allocate resource for EISA slot 6
[   54.400182] EISA: Detected 0 cards.
[   54.400288] NET: Registered protocol family 2
[   54.433065] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)[   54.433997] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[   54.441526] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   54.442961] TCP: Hash tables configured (established 262144 bind 65536)
[   54.442971] TCP reno registered
[   54.443289] TCP bic registered
[   54.443327] NET: Registered protocol family 1
[   54.443350] NET: Registered protocol family 8
[   54.443356] NET: Registered protocol family 20
[   54.443414] Using IPI Shortcut mode
[   54.443525] Freeing unused kernel memory: 288k freed
[   54.574776] vga16fb: initializing
[   54.574792] vga16fb: mapped to 0xc00a0000
[   54.695787] Console: switching to colour frame buffer device 80x25
[   54.695803] fb0: VGA16 VGA frame buffer device
[   55.820847] Capability LSM initialized
[   57.232966] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   57.233002] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[   57.233037] VP_IDE: chipset revision 16
[   57.233043] VP_IDE: not 100% native mode: will probe irqs later
[   57.233070] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[   57.233089]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   57.233123]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   57.233147] Probing IDE interface ide0...
[   57.646732] hda: Maxtor 33073H3, ATA DISK drive
[   58.318684] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   58.319070] Probing IDE interface ide1...
[   59.181630] hdc: PIONEER DVD-ROM DVD-115, ATAPI CD/DVD-ROM drive
[   59.965071] hdd: GoldStar CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[   59.965532] ide1 at 0x170-0x177,0x376 on irq 15
[   59.982869] hda: max request size: 128KiB
[   60.015745] hda: 60032448 sectors (30736 MB) w/2048KiB Cache, CHS=59556/16/63, UDMA(66)
[   60.015767] hda: cache flushes not supported
[   60.016164]  hda: hda1 hda2 hda3 hda4 < hda5 >
[   60.062280] hdc: ATAPI DVD-ROM drive, 512kB Cache, UDMA(33)
[   60.062300] Uniform CD-ROM driver Revision: 3.20
[   60.065228] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   60.750097] usbcore: registered new driver usbfs
[   60.750889] usbcore: registered new driver hub
[   60.756088] USB Universal Host Controller Interface driver v2.3
[   60.757037] PCI: Found IRQ 9 for device 0000:00:07.2
[   60.757057] PCI: Sharing IRQ 9 with 0000:00:07.3
[   60.757075] PCI: Sharing IRQ 9 with 0000:00:11.0
[   60.757101] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   60.758123] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   60.758150] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000d000
[   60.758885] hub 1-0:1.0: USB hub found
[   60.758911] hub 1-0:1.0: 2 ports detected
[   60.812859] ieee1394: Initialized config rom entry `ip1394'
[   60.860855] PCI: Found IRQ 9 for device 0000:00:07.3
[   60.860875] PCI: Sharing IRQ 9 with 0000:00:07.2
[   60.860891] PCI: Sharing IRQ 9 with 0000:00:11.0
[   60.860918] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   60.861146] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   60.861166] uhci_hcd 0000:00:07.3: irq 9, io base 0x0000d400
[   60.861709] hub 2-0:1.0: USB hub found
[   60.861732] hub 2-0:1.0: 2 ports detected
[   60.967687] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   60.967726] PCI: Found IRQ 10 for device 0000:00:0f.0
[   60.968593] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[   61.020605] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[dfffe000-dfffe7ff]  Max Packet=[512]
[   61.210128] Attempting manual resume
[   61.228158] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   61.244180] EXT3-fs: INFO: recovery required on readonly filesystem.
[   61.244194] EXT3-fs: write access will be enabled during recovery.
[   61.660674] usbcore: registered new driver hiddev
[   61.678837] input: BTC USB Multimedia Keyboard as /class/input/input0
[   61.678875] input: USB HID v1.00 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:07.2-2
[   61.702815] input: BTC USB Multimedia Keyboard as /class/input/input1
[   61.703055] input,hiddev96: USB HID v1.00 Device [BTC USB Multimedia Keyboard] on usb-0000:00:07.2-2
[   61.703093] usbcore: registered new driver usbhid
[   61.703101] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   62.301835] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090960000025264]
[   64.540076] EXT3-fs: recovery complete.
[   64.540128] kjournald starting.  Commit interval 5 seconds
[   64.545036] EXT3-fs: mounted filesystem with ordered data mode.
[   79.786314] Linux agpgart interface v0.101 (c) Dave Jones
[   79.793126] agpgart: Detected VIA Apollo Pro 133 chipset
[   80.013760] agpgart: AGP aperture is 64M @ 0xe0000000
[   80.375754] parport_pc: VIA 686A/8231 detected
[   80.375766] parport_pc: probing current configuration
[   80.375786] parport_pc: Current parallel port base: 0x378
[   80.375860] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   80.400622] parport0: Printer, Canon BJC-8200
[   80.400687] parport_pc: VIA parallel port: io=0x378, irq=7
[   80.762686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   80.768261] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   81.287773] Linux video capture interface: v1.00
[   81.347311] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[   81.347319]   originally by Donald Becker <becker@scyld.com>
[   81.347323]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[   81.347326]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   81.347464] PCI: Found IRQ 11 for device 0000:00:0e.0
[   81.349283] natsemi eth0: NatSemi DP8381[56] at 0xdffff000 (0000:00:0e.0), 00:09:5b:21:19:f8, IRQ 11, port TP.
[   81.489793] PCI: Found IRQ 10 for device 0000:00:10.1
[   81.489817] PCI: Sharing IRQ 10 with 0000:00:07.6
[   81.489826] PCI: Sharing IRQ 10 with 0000:00:10.0
[   81.577994] bttv: driver version 0.9.16 loaded
[   81.578007] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   81.578077] bttv: Bt8xx card found (0).
[   81.578110] PCI: Found IRQ 10 for device 0000:00:10.0
[   81.578127] PCI: Sharing IRQ 10 with 0000:00:07.6
[   81.578137] PCI: Sharing IRQ 10 with 0000:00:10.1
[   81.578158] bttv0: Bt878 (rev 17) at 0000:00:10.0, irq: 10, latency: 64, mmio: 0xdddfe000
[   81.578185] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   81.578193] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   81.578240] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   81.580732] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   81.673697] tveeprom 0-0050: Hauppauge model 38105, rev B435, serial# 5092625[   81.673707] tveeprom 0-0050: tuner model is Temic 4066FY5 (idx 35, type 18)
[   81.673715] tveeprom 0-0050: TV standards PAL(I) (eeprom 0x10)
[   81.673722] tveeprom 0-0050: audio processor is None (idx 0)
[   81.673730] tveeprom 0-0050: has no radio
[   81.673735] bttv0: using tuner=18
[   81.673744] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   81.675947] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   81.678157] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   81.732421] PCI: Found IRQ 10 for device 0000:00:07.6
[   81.732449] PCI: Sharing IRQ 10 with 0000:00:10.0
[   81.732456] PCI: Sharing IRQ 10 with 0000:00:10.1
[   81.786342] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   81.825868] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   81.825932] tuner 0-0061: type set to 18 (Temic PAL_I (4066 FY5))
[   81.857398] bttv0: registered device video0
[   81.857437] bttv0: registered device vbi0
[   81.857484] bttv0: PLL: 28636363 => 35468950 .. ok
[   81.912794] bt878: AUDIO driver version 0.0.0 loaded
[   82.480963] PCI: Setting latency timer of device 0000:00:07.6 to 64
[   82.673217] nvidia: module license 'NVIDIA' taints kernel.
[   83.006622] gameport: EMU10K1 is pci0000:00:11.1/gameport0, io 0xdc00, speed 1242kHz
[   83.006987] PCI: Found IRQ 9 for device 0000:00:11.0
[   83.007003] PCI: Sharing IRQ 9 with 0000:00:07.3
[   83.007010] PCI: Sharing IRQ 9 with 0000:00:07.2
[   83.025442] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[   83.372167] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   83.656506] input: PC Speaker as /class/input/input3
[   83.796610] Real Time Clock Driver v1.12
[   84.572257] Floppy drive(s): fd0 is 1.44M
[   84.591143] FDC 0 is a post-1991 82077
[   84.769201] ts: Compaq touchscreen protocol output
[   85.069551] eth0: DSPCFG accepted after 0 usec.
[   85.069565] eth0: link up.
[   85.069583] eth0: Setting full-duplex based on negotiated link capability.
[   86.150448] NET: Registered protocol family 17
[   86.368648] lp0: using parport0 (interrupt-driven).
[   86.485854] SCSI subsystem initialized
[   86.506707] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   86.506723] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   86.506729] ieee1394: sbp2: Try serialize_io=0 for better performance
[   86.657042] Adding 602396k swap on /dev/hda5.  Priority:-1 extents:1 across:602396k
[   86.834343] EXT3 FS on hda3, internal journal
[   87.171196] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   87.171208] md: bitmap version 4.39
[   87.945908] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   88.305988] cdrom: open failed.
[   88.925175] cdrom: open failed.
[   88.927945] cdrom: open failed.
[   96.402277] CSLIP: code copyright 1989 Regents of the University of California
[   96.413674] PPP generic driver version 2.4.2
[   96.516267] NET: Registered protocol family 10
[   96.516588] lo: Disabled Privacy Extensions
[   96.516997] IPv6 over IPv4 tunneling driver
[   96.577269] NET: Registered protocol family 24
[   98.016995] ip_tables: (C) 2000-2002 Netfilter core team
[  106.883552] eth0: no IPv6 routers present
[  116.132520] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  116.132765] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  116.133032] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  118.632216] ppdev: user-space parallel port driver
[  119.368591] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  121.071836] hdc: drive_cmd: status=0x01 { Error }
[  121.071854] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  121.071861] ide: failed opcode was: 0xec
[  121.131247] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  121.131268] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  121.131275] ide: failed opcode was: 0xec
[  127.566338] Bluetooth: Core ver 2.8
[  127.566358] NET: Registered protocol family 31
[  127.566363] Bluetooth: HCI device and connection manager initialized
[  127.566397] Bluetooth: HCI socket layer initialized
[  127.588090] Bluetooth: L2CAP ver 2.8
[  127.588105] Bluetooth: L2CAP socket layer initialized
[  127.597090] Bluetooth: RFCOMM socket layer initialized
[  127.597134] Bluetooth: RFCOMM TTY layer initialized
[  127.597139] Bluetooth: RFCOMM ver 1.7
[  182.020182] ppdev0: registered pardevice
[  182.034402] ppdev0: negotiated back to compatibility mode because user-space forgot
[  182.034658] ppdev0: unregistered pardevice
[  258.862806] ppdev0: registered pardevice
[  258.879695] ppdev0: negotiated back to compatibility mode because user-space forgot
[  258.879966] ppdev0: unregistered pardevice
[  276.502549] ppdev0: registered pardevice
[  276.518799] ppdev0: negotiated back to compatibility mode because user-space forgot
[  276.519050] ppdev0: unregistered pardevice
[  297.000063] FIFO write timed out
[  311.261914] parport0: BUSY timeout (1) in compat_write_block_pio

Hope this means something to you......

---

### Post by pseudonym on 2006-12-31
Sorry, my request was a little ambiguous. What's needed is the output which occurs immediately after you plug in a usb device, and it fails. What you've posted isn't showing any problems.

Try plugging in a flash drive. Then do dmesg again, but only post the last 15 lines - it's not needed in its entirety....

---

### Post by Mr_Bond_UK on 2006-12-31
Would love to do that for you, but it freezes completly, keboard mouse everything! so cant access terminal.
Any other suggestions?

---

### Post by pseudonym on 2006-12-31
Were you forced to reboot? In any case, the messages I'm looking for will be stored in a file called /var/log/syslog or /var/log/syslog.0 . Can you post both as attachments (not in the body of your post)?

Also, is the place where you're plugging the devices in at the back of the computer or at the front? I once had a faulty front-panel usb port and it caused a similar problem to yours...

---

### Post by Mr_Bond_UK on 2006-12-31
Cant load them as attachments, file too big apparently. Email them to you? Yes they're attatched to my front usb. Should try the back i guess.
Forced to switch the computer off by the mains!

---

### Post by pseudonym on 2006-12-31
> **Mr_Bond_UK said:**
> Cant load them as attachments, file too big apparently. Email them to you?
Try and PM them to me first...

---

