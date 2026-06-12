---
title: "ppc, wired network card loose WAN but not LAN"
date: 2007-04-21
forum: Apple PPC Users
---

### Post by Maelvon on 2007-04-21
[COLOR="Red"]FALSE ALERT, it was an ISP problem, Grrrrr ![/COLOR]

Hello,

I've make an upgrade to Festy I think. I'm on a Ubuntu modified to a Xubuntu.

And my network is weird. I can ping the local machines (ping 10.0.0.254 = OK), but cannot ping internet (ping free.fr = unknow host).

As I am on a PPC, i've blacklisted ipv6... Tested some solution (tcp_window_scaling, etc..), but cannot surf internet. I cannot found, what it could be ! 

Someone have a tip ?

```
#ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:05:02:C7:E9:B8  
          inet adr:10.0.0.50  Bcast:10.255.255.255  Masque:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:6473 erreurs:0 :0 overruns:0 frame:0
          TX packets:1042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:461954 (451.1 KiB) Octets transmis:132333 (129.2 KiB)
          Interruption:42 Adresse de base:0xe000 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:85 erreurs:0 :0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reÃ§us:5946 (5.8 KiB) Octets transmis:5946 (5.8 KiB)

```


```
# uname -a
Linux ubuntu 2.6.12-9-powerpc #1 Mon Oct 10 15:26:45 BST 2005 ppc GNU/Linux
```

```
# cat /proc/version
Linux version 2.6.12-9-powerpc (buildd@adare) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 15:26:45 BST 2005
```

```

# dmesg
[    0.000000] mem_pieces_remove: [329000,8ea26b) not in any region
[    0.000000] Total memory = 512MB; using 1024kB for hash table (at c0900000)
[    0.000000] Linux version 2.6.12-9-powerpc (buildd@adare) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 15:26:45 BST 2005
[    0.000000] Found a Heathrow mac-io controller, rev: 1, mapped at 0xfda7f000
[    0.000000] PowerMac motherboard: PowerMac G3 (Silk)
[    0.000000] Found Grackle (MPC106) PCI host bridge at 0x80000000. Firmware bus number: 0->1
[    0.000000] nvram: OF partition at 0x1800
[    0.000000] nvram: XP partition at 0x1300
[    0.000000] nvram: NR partition at 0x1400
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 131072 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:1
[    0.000000]   HighMem zone: 0 pages, LIFO batch:1
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: ramdisk_size=8192 root=/dev/sdb2 acpi=off apm=on
[    0.000000] System has 64 possible interrupts
[    0.000000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[    0.000000] GMT Delta read from XPRAM: 60 minutes, DST: off
[    0.000000] via_calibrate_decr: ticks per jiffy = 16707 (1002473 ticks)
[   39.722228] Console: colour dummy device 80x25
[   39.722370] serial8250_console_init: nothing to do on PowerMac
[   39.727035] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   39.731474] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   39.809479] Memory: 509056k available (1920k kernel code, 1160k data, 172k init, 0k highmem)
[   39.809798] Calibrating delay loop... 665.60 BogoMIPS (lpj=332800)
[   39.831918] Mount-cache hash table entries: 512
[   39.832556] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,750
[   39.834398] checking if image is initramfs... it is
[   41.729162] Freeing initrd memory: 5892k freed
[   41.732184] NET: Registered protocol family 16
[   41.736037] PCI: Probing PCI hardware
[   41.738211] Registering pmac pic with sysfs...
[   41.740908] Thermal assist unit using timers, shrink_timer: 2000 jiffies
[   41.742858] audit: initializing netlink socket (disabled)
[   41.742902] audit: initialized
[   41.743426] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   41.743469] devfs: boot_options: 0x0
[   41.743607] Initializing Cryptographic API
[   41.744075] PCI: Enabling device 0000:00:12.0 (0086 -> 0087)
[   41.744126] atyfb: using auxiliary register aperture
[   41.745059] atyfb: 3D RAGE PRO (Mach64 GP, PQFP, PCI) [0x4750 rev 0x7c]
[   41.745127] atyfb: 6M SGRAM (1:1), 14.31818 MHz XTAL, 230 MHz PLL, 100 Mhz MCLK, 100 MHz XCLK
[   41.745222] atyfb: monitor sense=737, mode 5
[   41.805334] Console: switching to colour frame buffer device 80x30
[   41.805570] atyfb: fb0: ATY Mach64 frame buffer device on PCI
[   41.806584] MacOS display is /pci/ATY,mach64_3DUPro
[   41.814045] Generic RTC Driver v1.07
[   41.814317] Macintosh non-volatile memory driver v1.1
[   41.814617] serial8250_init: nothing to do on PowerMac
[   41.820552] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   41.832079] ttyS0 at MMIO 0xf3013020 (irq = 15) is a Z85c30 ESCC - Serial port
[   41.843926] ttyS1 at MMIO 0xf3013000 (irq = 16) is a Z85c30 ESCC - Serial port
[   41.856175] io scheduler noop registered
[   41.862086] io scheduler anticipatory registered
[   41.867920] io scheduler deadline registered
[   41.873661] io scheduler cfq registered
[   41.879395] fd0: SWIM3 floppy controller 
[   41.887030] RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
[   41.898818] MacIO PCI driver attached to Heathrow chipset
[   41.906584] input: Macintosh mouse button emulation
[   41.912486] Macintosh CUDA driver v0.5 for Unified ADB.
[   41.918466] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   41.924435] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   41.936676] adb: starting probe task...
[   42.163617] adb devices: [1]: 1 34 [2]: 2 5 [15]: 1 34
[   42.199918] ADB keyboard at 2, handler set to 3
[   42.205896] Detected ADB keyboard, type ISO, swapping keys.
[   42.211890] input: ADB keyboard on adb2:2.05/input
[   42.217756] adb: finished probe task...
[   42.960608] ide0: Found Apple Heathrow ATA controller, bus ID 0, irq 13
[   42.966550] Probing IDE interface ide0...
[   43.484574] ide0: Bus empty, interface released.
[   44.501509] ide0: Found Apple Heathrow ATA controller, bus ID 1, irq 14
[   44.507556] Probing IDE interface ide0...
[   45.026477] ide0: Bus empty, interface released.
[   45.032873] mice: PS/2 mouse device common for all mice
[   45.039268] NET: Registered protocol family 2
[   45.053715] IP: routing cache hash table of 4096 buckets, 32Kbytes
[   45.060593] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   45.080452] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   45.089003] TCP: Hash tables configured (established 131072 bind 65536)
[   45.095272] Freeing unused kernel memory: 172k init 4k chrp 32k prep
[   45.390020] NET: Registered protocol family 1
[   45.503671] SCSI subsystem initialized
[   46.011791] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
[   46.011804]         <Adaptec 29160N Ultra160 SCSI adapter>
[   46.011812]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   46.011821] 
[   61.268533]   Vendor: QUANTUM   Model: VIKING II 9.1WSE  Rev: 5520
[   61.275115]   Type:   Direct-Access                      ANSI SCSI revision: 02
[   61.287213] scsi0:A:1:0: Tagged Queuing enabled.  Depth 32
[   61.293292]  target0:0:1: Beginning Domain Validation
[   61.301727] WIDTH IS 1
[   61.308334] (scsi0:A:1): 6.600MB/s transfers (16bit)
[   61.314857] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x1a6) SCSIRATE(0x80)
[   61.328627]  target0:0:1: Wide Transfers Fail
[   61.334709]  target0:0:1: Domain Validation skipping write tests
[   61.341371] (scsi0:A:1): 20.000MB/s transfers (20.000MHz, offset 31)
[   61.349761]  target0:0:1: Ending Domain Validation
[   61.614927]   Vendor: MATSHITA  Model: CD-ROM CR-8024    Rev: 2.0e
[   61.621441]   Type:   CD-ROM                             ANSI SCSI revision: 02
[   61.633477]  target0:0:3: Beginning Domain Validation
[   61.642805]  target0:0:3: Domain Validation skipping write tests
[   61.649152] (scsi0:A:3): 10.000MB/s transfers (10.000MHz, offset 16)
[   61.659166]  target0:0:3: Ending Domain Validation
[   62.179988]   Vendor: COMPAQPC  Model: ATLAS10K2-TY184L  Rev: DDC2
[   62.186310]   Type:   Direct-Access                      ANSI SCSI revision: 03
[   62.197908] scsi0:A:6:0: Tagged Queuing enabled.  Depth 32
[   62.203894]  target0:0:6: Beginning Domain Validation
[   62.210996] WIDTH IS 1
[   62.217313] (scsi0:A:6): 6.600MB/s transfers (16bit)
[   62.223400] (scsi0:A:6:0): parity error detected in Data-in phase. SEQADDR(0x82) SCSIRATE(0x80)
[   62.235869]  target0:0:6: Wide Transfers Fail
[   62.242168] (scsi0:A:6): 3.300MB/s transfers
[   62.248941] (scsi0:A:6): 20.000MB/s transfers (20.000MHz, offset 31)
[   62.256787]  target0:0:6: Ending Domain Validation
[   64.408237] SCSI device sda: 17836668 512-byte hdwr sectors (9132 MB)
[   64.415533] SCSI device sda: drive cache: write back
[   64.422326] SCSI device sda: 17836668 512-byte hdwr sectors (9132 MB)
[   64.429538] SCSI device sda: drive cache: write back
[   64.435207]  /dev/scsi/host0/bus0/target1/lun0: [mac] p1 p2 p3 p4 p5 p6 p7 p8 p9 p10
[   64.461963] Attached scsi disk sda at scsi0, channel 0, id 1, lun 0
[   64.468179] SCSI device sdb: 35566000 512-byte hdwr sectors (18210 MB)
[   64.475377] SCSI device sdb: drive cache: write back
[   64.481653] SCSI device sdb: 35566000 512-byte hdwr sectors (18210 MB)
[   64.488784] SCSI device sdb: drive cache: write back
[   64.494531]  /dev/scsi/host0/bus0/target6/lun0: [mac] p1 p2 p3
[   64.501648] Attached scsi disk sdb at scsi0, channel 0, id 6, lun 0
[   64.975440] Attempting manual resume
[   64.992839] swsusp: Suspend partition has wrong signature?
[   65.420681] usbcore: registered new driver usbfs
[   65.426748] usbcore: registered new driver hub
[   65.437350] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   65.437547] PCI: Enabling device 0000:01:09.0 (0004 -> 0006)
[   65.443229] ohci_hcd 0000:01:09.0: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller
[   65.454953] ohci_hcd 0000:01:09.0: new USB bus registered, assigned bus number 1
[   65.466662] ohci_hcd 0000:01:09.0: irq 25, io mem 0x80800000
[   65.555674] hub 1-0:1.0: USB hub found
[   65.561645] hub 1-0:1.0: 2 ports detected
[   65.777237] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   67.729497] usbcore: registered new driver hiddev
[   67.742514] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:01:09.0-2
[   67.754722] usbcore: registered new driver usbhid
[   67.760754] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   69.466276] Attempting manual resume
[   69.472448] swsusp: Suspend partition has wrong signature?
[   69.608939] kjournald starting.  Commit interval 5 seconds
[   69.614608] EXT3-fs: mounted filesystem with ordered data mode.
[   81.063219] eth0: BMAC at 00:05:02:c7:e9:b8
[   81.151376] mesh: configured for synchronous 5 MB/s
[   81.357414] mesh: performing initial bus reset...
[   85.362076] scsi1 : MESH
[   88.689086] ieee1394: Initialized config rom entry `ip1394'
[   88.699861] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   92.608851] EXT3 FS on sdb2, internal journal
[   93.451213] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   97.003900] phy registers:
[   97.003920]  0000 0000 0000 0000 0000 0000 0000 0000
[   97.014594]  0000 0000 0000 0000 0000 0000 0000 0000
[   97.025261]  0000 0000 0000 0000 0000 0000 0000 0000
[   97.035928]  0000 0000 0000 0000 0000 0000 0000 0000
[  177.512239] Linux Kernel Card Services
[  177.512261]   options:  [pci] [cardbus] [pm]
[  264.146241] NET: Registered protocol family 5
[  309.583832] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
```

```
auto lo
iface lo inet loopback

iface eth0 inet static
#Put your own IP address information here
address 10.0.0.50
netmask 255.0.0.0
gateway 10.0.0.254

auto eth0
```

```
# lspci -vv
00:00.0 Host bridge: Motorola MPC106 [Grackle] (rev 40)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes

00:0e.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
	Subsystem: Adaptec 29160N Ultra160 SCSI Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (10000ns min, 6250ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 24
	BIST result: 00
	Region 0: I/O ports at <unassigned> [disabled]
	Region 1: Memory at 80900000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at 80920000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0f.0 PCI bridge: Texas Instruments PCI2250 PCI-to-PCI Bridge (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 80800000-808fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] #06 [0000]

00:10.0 Class ff00: Apple Computer Inc. Heathrow Mac I/O (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Region 0: Memory at f3000000 (32-bit, non-prefetchable) [size=512K]

00:12.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 81000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: I/O ports at 0c00 [size=256]
	Region 2: Memory at 80901000 (32-bit, non-prefetchable) [size=4K]

01:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04) (prog-if 10 [OHCI])
	Subsystem: Agere Systems FW323
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at 80801000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:09.0 USB Controller: Agere Systems USS-312 USB Controller (rev 10) (prog-if 10 [OHCI])
	Subsystem: Agere Systems USS-312 USB Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at 80800000 (32-bit, non-prefetchable) [size=4K]

```

```
#lspci -vvn
00:00.0 0600: 1057:0002 (rev 40)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes

00:0e.0 0100: 9005:0080 (rev 02)
	Subsystem: 9005:62a0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (10000ns min, 6250ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 24
	BIST result: 00
	Region 0: I/O ports at <unassigned> [disabled]
	Region 1: Memory at 80900000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at 80920000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0f.0 0604: 104c:ac23 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 80800000-808fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] #06 [0000]

00:10.0 ff00: 106b:0010 (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Region 0: Memory at f3000000 (32-bit, non-prefetchable) [size=512K]

00:12.0 0300: 1002:4750 (rev 5c)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 81000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: I/O ports at 0c00 [size=256]
	Region 2: Memory at 80901000 (32-bit, non-prefetchable) [size=4K]

01:00.0 0c00: 11c1:5811 (rev 04) (prog-if 10)
	Subsystem: 11c1:5811
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at 80801000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:09.0 0c03: 11c1:5802 (rev 10) (prog-if 10)
	Subsystem: 11c1:5802
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at 80800000 (32-bit, non-prefetchable) [size=4K]

```

---

