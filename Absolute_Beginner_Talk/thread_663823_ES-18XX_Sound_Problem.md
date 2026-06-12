---
title: "ES-18XX Sound Problem"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jjohnson1032 on 2008-01-10
Hello, I'm really new to linux and so far the experience has been great.  However I have never been able to get sound out of my computer.  Windows says that I have an es-1868 sound card and windows plays sound with no problem.  I've spent weeks reading through posts of similar issues and have not been able to solve the issue yet.  The sound card is just not recognized.  I even made a soundcard file in my etc/modprobe.d folder and ran the required code but it just fails and says no soundcard.  Where do i go from here?  I'm loving linux but if I can't get sound then I'm going to be forced to run back to windows.  can someone please point me in the right direction?

Here is the output of dmesg

jason@ubuntujason:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000a000000 (usable)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 160MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 40960) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    40960
[    0.000000]   HighMem     40960 ->    40960
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    40960
[    0.000000] On node 0 totalpages: 40960
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 288 pages used for memmap
[    0.000000]   Normal zone: 36576 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0a000000:f5ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 40640
[    0.000000] Kernel command line: root=UUID=fa463562-c885-443f-973c-fc9d43d748a3 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0114b000)
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 300.699 MHz processor.
[   40.771681] Console: colour VGA+ 80x25
[   40.777266] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   40.778112] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   40.810118] Memory: 150924k/163840k available (2015k kernel code, 12424k reserved, 916k data, 364k init, 0k highmem)
[   40.810188] virtual kernel memory layout:
[   40.810196]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   40.810207]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.810217]     vmalloc : 0xca800000 - 0xff7fe000   ( 847 MB)
[   40.810226]     lowmem  : 0xc0000000 - 0xca000000   ( 160 MB)
[   40.810236]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   40.810246]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   40.810256]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   40.810278] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.810513] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   40.890570] Calibrating delay using timer specific routine.. 602.29 BogoMIPS (lpj=1204592)
[   40.890737] Security Framework v1.0.0 initialized
[   40.890797] SELinux:  Disabled at boot.
[   40.890904] Mount-cache hash table entries: 512
[   40.891670] CPU: After generic identify, caps: 0080f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.891744] CPU: L1 I cache: 16K, L1 D cache: 16K
[   40.891763] CPU: L2 cache: 512K
[   40.891783] CPU: After all inits, caps: 0080f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   40.891850] Compat vDSO mapped to ffffe000.
[   40.891928] Checking 'hlt' instruction... OK.
[   40.906728] SMP alternatives: switching to UP code
[   40.907672] Freeing SMP alternatives: 11k freed
[   40.909300] Early unpacking initramfs... done
[   43.078417] CPU0: Intel Pentium II (Klamath) stepping 04
[   43.078460] SMP motherboard not detected.
[   43.078476] Local APIC not detected. Using dummy APIC emulation.
[   43.078765] Brought up 1 CPUs
[   43.079541] Booting paravirtualized kernel on bare hardware
[   43.079807] Time: 18:00:15  Date: 00/10/108
[   43.080000] NET: Registered protocol family 16
[   43.080629] EISA bus registered
[   43.083155] PCI: PCI BIOS revision 2.10 entry at 0xfd9fd, last bus=1
[   43.083174] PCI: Using configuration type 1
[   43.083188] Setting up standard PCI resources
[   43.094637] ACPI: Interpreter disabled.
[   43.094662] Linux Plug and Play Support v0.97 (c) Adam Belay
[   43.094732] pnp: PnP ACPI: disabled
[   43.094751] PnPBIOS: Scanning system for PnP BIOS support...
[   43.094830] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6f90
[   43.094853] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa607, dseg 0x400
[   43.115059] PnPBIOS: 21 nodes reported by PnP BIOS; 21 recorded by driver
[   43.115400] PCI: Probing PCI hardware
[   43.115427] PCI: Probing PCI hardware (bus 00)
[   43.116251] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   43.116264] * this clock source is slow. Consider trying other clock sources
[   43.116360] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   43.116380] PCI quirk: region 2180-218f claimed by PIIX4 SMB
[   43.119265] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:14.0
[   43.121469] NET: Registered protocol family 8
[   43.121486] NET: Registered protocol family 20
[   43.121920] pnp: 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[   43.121968] pnp: 00:01: iomem range 0x0-0x9ffff could not be reserved
[   43.121990] pnp: 00:01: iomem range 0xd8000-0xfffff could not be reserved
[   43.122013] pnp: 00:01: iomem range 0x100000-0x9ffffff could not be reserved
[   43.122075] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   43.122096] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   43.122117] pnp: 00:0a: ioport range 0x2180-0x218f has been reserved
[   43.122157] pnp: 00:0b: iomem range 0xc8000-0xcbfff has been reserved
[   43.122199] pnp: 00:0c: iomem range 0xfec00000-0xfec0ffff has been reserved
[   43.122222] pnp: 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   43.122311] Time: tsc clocksource has been installed.
[   43.124865] PCI: Bridge: 0000:00:01.0
[   43.124887]   IO window: e000-efff
[   43.124911]   MEM window: fd000000-febfffff
[   43.124931]   PREFETCH window: 10000000-100fffff
[   43.125027] NET: Registered protocol family 2
[   43.162601] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   43.162880] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   43.163509] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   43.163910] TCP: Hash tables configured (established 8192 bind 8192)
[   43.163928] TCP reno registered
[   43.175083] checking if image is initramfs... it is
[   47.318828] Freeing initrd memory: 7066k freed
[   47.325561] audit: initializing netlink socket (disabled)
[   47.325643] audit(1199988019.316:1): initialized
[   47.343602] VFS: Disk quotas dquot_6.5.1
[   47.344079] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   47.345141] io scheduler noop registered
[   47.345161] io scheduler anticipatory registered
[   47.345175] io scheduler deadline registered
[   47.345371] io scheduler cfq registered (default)
[   47.345434] Limiting direct PCI/PCI transfers.
[   47.345515] Boot video device is 0000:01:00.0
[   47.346457] isapnp: Scanning for PnP cards...
[   47.701321] isapnp: No Plug & Play device found
[   47.932292] Real Time Clock Driver v1.12ac
[   47.932832] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   47.933111] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.937441] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.943736] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   47.944677] input: Macintosh mouse button emulation as /class/input/input0
[   47.945383] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   47.948838] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.948874] serio: i8042 AUX port at 0x60,0x64 irq 12
[   47.950187] mice: PS/2 mouse device common for all mice
[   47.951064] EISA: Probing bus 0 at eisa.0
[   47.951161] Cannot allocate resource for EISA slot 8
[   47.951177] EISA: Detected 0 cards.
[   47.951799] TCP cubic registered
[   47.951907] NET: Registered protocol family 1
[   47.952068] Using IPI No-Shortcut mode
[   47.952506]   Magic number: 8:589:38
[   47.952939]   hash matches device 00:0a
[   47.955266] Freeing unused kernel memory: 364k freed
[   48.033983] input: AT Translated Set 2 keyboard as /class/input/input1
[   50.370477] AppArmor: AppArmor initialized<5>audit(1199988022.316:2):  type=1505 info="AppArmor initialized" pid=1123
[   50.419931] fuse init (API version 7.8)
[   50.458236] Failure registering capabilities with primary security module.
[   50.572004] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   53.919083] SCSI subsystem initialized
[   54.004281] libata version 2.21 loaded.
[   54.028812] ata_piix 0000:00:14.1: version 2.11
[   54.029725] scsi0 : ata_piix
[   54.030051] scsi1 : ata_piix
[   54.030233] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fcf0 irq 14
[   54.030260] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fcf8 irq 15
[   54.249302] ata1.00: ATA-4: QUANTUM Bigfoot TX8.0AT, A04.0T00, max UDMA/33
[   54.249335] ata1.00: 15698592 sectors, multi 16: LBA 
[   54.265249] ata1.00: configured for UDMA/33
[   54.360725] usbcore: registered new interface driver usbfs
[   54.360884] usbcore: registered new interface driver hub
[   54.361108] usbcore: registered new device driver usb
[   54.372327] USB Universal Host Controller Interface driver v3.0
[   54.605256] ata2.00: ATAPI: COMPAQ DVD-ROM GD-2000, 0056, max MWDMA2
[   54.777263] ata2.00: configured for MWDMA2
[   54.785153] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM Bigfoot  A04. PQ: 0 ANSI: 5
[   54.787497] scsi 1:0:0:0: CD-ROM            COMPAQ   DVD-ROM GD-2000  0056 PQ: 0 ANSI: 5
[   54.818158] PCI: setting IRQ 9 as level-triggered
[   54.818181] PCI: Found IRQ 9 for device 0000:00:14.2
[   54.818251] uhci_hcd 0000:00:14.2: UHCI Host Controller
[   54.818842] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
[   54.818936] uhci_hcd 0000:00:14.2: irq 9, io base 0x0000fcc0
[   54.819770] usb usb1: configuration #1 chosen from 1 choice
[   54.819983] hub 1-0:1.0: USB hub found
[   54.820045] hub 1-0:1.0: 2 ports detected
[   55.160989] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   55.340556] usb 1-1: configuration #1 chosen from 1 choice
[   55.526277] Floppy drive(s): fd0 is 1.44M
[   55.643609] FDC 0 is a post-1991 82077
[   56.068928] sd 0:0:0:0: [sda] 15698592 512-byte hardware sectors (8038 MB)
[   56.074319] sd 0:0:0:0: [sda] Write Protect is off
[   56.074344] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.074544] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.074931] sd 0:0:0:0: [sda] 15698592 512-byte hardware sectors (8038 MB)
[   56.075025] sd 0:0:0:0: [sda] Write Protect is off
[   56.075046] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.075197] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.075234]  sda: sda1 sda2 < sda5 >
[   56.233034] sd 0:0:0:0: [sda] Attached SCSI disk
[   56.234308] sr0: scsi3-mmc drive: 8x/20x cd/rw xa/form2 cdda tray
[   56.234332] Uniform CD-ROM driver Revision: 3.20
[   56.235501] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   56.273321] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   56.273475] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   57.358114] Attempting manual resume
[   57.358140] swsusp: Resume From Partition 8:5
[   57.358153] PM: Checking swsusp image.
[   57.389549] PM: Resume from disk failed.
[   57.565491] EXT3-fs: INFO: recovery required on readonly filesystem.
[   57.565521] EXT3-fs: write access will be enabled during recovery.
[   74.725712] kjournald starting.  Commit interval 5 seconds
[   74.725807] EXT3-fs: recovery complete.
[   74.727701] EXT3-fs: mounted filesystem with ordered data mode.
[  104.570603] piix4_smbus 0000:00:14.3: Found 0000:00:14.3 device
[  106.730045] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  106.917870] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  107.187303] Linux agpgart interface v0.102 (c) Dave Jones
[  107.314240] agpgart: Detected an Intel 440LX Chipset.
[  107.324444] agpgart: AGP aperture is 64M @ 0xf8000000
[  107.642939] input: PS/2 Logitech Mouse as /class/input/input2
[  108.035085] input: PC Speaker as /class/input/input3
[  111.838532] parport_pc 00:1c: reported by Plug and Play BIOS
[  111.838608] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  112.604797] gameport: NS558 PnP Gameport is pnp00:1f/gameport0, io 0x201, speed 745kHz
[  112.839444] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
[  112.839470] prism2usb_init: dev_info is: prism2_usb
[  112.840674] usbcore: registered new interface driver prism2_usb
[  114.367847] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[  114.367880] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[  114.367961] prism2sta_getcardinfo: Failed, result=-5
[  114.368020] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[  115.367489] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[  115.848357] loop: module loaded
[  115.965048] lp0: using parport0 (interrupt-driven).
[  116.456145] Adding 385520k swap on /dev/sda5.  Priority:-1 extents:1 across:385520k
[  116.973021] EXT3 FS on sda1, internal journal
[  122.998901] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  122.999493] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  123.001327] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  123.002143] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  127.805518] ppdev: user-space parallel port driver
[  128.539158] audit(1199988100.658:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4208 profile="/usr/sbin/cupsd"
[  128.780607] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  130.097630] Failure registering capabilities with primary security module.
[  131.195684] Bluetooth: Core ver 2.11
[  131.196387] NET: Registered protocol family 31
[  131.196410] Bluetooth: HCI device and connection manager initialized
[  131.196432] Bluetooth: HCI socket layer initialized
[  131.339511] Bluetooth: L2CAP ver 2.8
[  131.339542] Bluetooth: L2CAP socket layer initialized
[  131.458063] Bluetooth: RFCOMM socket layer initialized
[  131.458652] Bluetooth: RFCOMM TTY layer initialized
[  131.458674] Bluetooth: RFCOMM ver 1.8
[  303.169454] UDF-fs: No VRS found
[  303.233980] ISO 9660 Extensions: Microsoft Joliet Level 3
[  303.450979] ISOFS: changing to secondary root
[  454.567840] ident: nic h/w: id=0x8010 1.0.0
[  454.569476] ident: pri f/w: id=0x15 1.1.3
[  454.570817] ident: sta f/w: id=0x1f 1.7.1
[  454.571820] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[  454.572820] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[  454.573820] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[  454.574820] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
[  454.575820] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[  454.576819] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[  454.577819] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[  454.578815] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[  455.151671] linkstatus=CONNECTED
[  457.024899] NET: Registered protocol family 17
[  457.158478] prism2mgmt_scan_results: dot11req_scan_results can only be used after a successful dot11req_scan.
[  457.178911] linkstatus=DISCONNECTED (unhandled)
[  457.784786] linkstatus=CONNECTED
[  594.117948] prism2mgmt_scan_results: dot11req_scan_results can only be used after a successful dot11req_scan.
[  594.146489] linkstatus=DISCONNECTED (unhandled)
[  594.742995] linkstatus=CONNECTED
[  696.090151] prism2mgmt_scan_results: dot11req_scan_results can only be used after a successful dot11req_scan.
[  696.108344] linkstatus=DISCONNECTED (unhandled)
[  696.775201] linkstatus=CONNECTED
[  705.599948] NET: Registered protocol family 10
[  705.601186] lo: Disabled Privacy Extensions
[  716.155498] wlan0: no IPv6 routers present
[ 4161.340099] NETDEV WATCHDOG: wlan0: transmit timed out
[ 4161.344224] wlan0 rx pipe reset complete.
[ 4161.345208] wlan0 tx pipe reset complete.
[ 4649.700544] es18xx: unable to grap ports 0x0-0xf
[ 4649.701105] es18xx: probe of es18xx.0 failed with error -16
[ 5106.229407] NETDEV WATCHDOG: wlan0: transmit timed out
[ 5106.230638] wlan0 rx pipe reset complete.
[ 5106.231617] wlan0 tx pipe reset complete.
[ 5633.231511] opl3: Unknown parameter `port'

---

### Post by stchman on 2008-01-10
Post an lspci output here.  Need to know what chipset the sound card uses.

---

### Post by jjohnson1032 on 2008-01-10
Here is the output for lspci:

jason@ubuntujason:~$ lspci
00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
jason@ubuntujason:~$

---

### Post by jjohnson1032 on 2008-01-11
In the past couple of weeks I have leared so much about Ubuntu while trying to fix my sound issue.  I think I love it now more than ever.  But I would still like sound.  Can anyone tell me why I can't here anything?  

I followed the Comprehensive Sound Problem Solutions Guide v0.5e
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and many others and still nothing.

Is there not anything I can do?  Because no matter how much I love Ubuntu I may have to go back to windows with my head held down in shame, because I really need sound.

---

### Post by jjohnson1032 on 2008-01-13
Has anyone ever had success with Ubuntu and a es-18xx soundcard?  If so please let me know how you did it, because every forum I go the example never work for my situation.

---

