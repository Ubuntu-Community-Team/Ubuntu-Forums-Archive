---
title: "Mounting CD-ROM in Feisty"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Ken T on 2007-11-01
Hi folks,

Feisty isn't recognising my cdrom drive,  telling me that "mount: special device /dev/scd0 does not exist." 

I found several other posts on this forum and via a quick web search, but no complete answers (that I could make sense of). The most (apparently) useful one suggested posting the terminal output from the command  "cat / etc/fstab", which I've done below - any ideas would be welcome... 

ken@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3a0e9aa-0ff9-4e2c-83f7-ec6232853855 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0af30e55-a53d-4ea8-b0d6-65f50fa3dfc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Additional info: I'm running Feisty as a guest OS under Mac OSX 10.4.9 on an intel dual-core macbook, about 1yrold.

Many thanks,
Ken.
***************

---

### Post by veerakumar on 2007-11-01
[[img]http://sfx-images.mozilla.org/affiliates/Buttons/firefox2/foxkeh-fx2-300x250.png[/img]](http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=223)
Send the output from this command
dmesg

---

### Post by Ken T on 2007-11-01
ken@Ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000ff00000 end: 0000000010000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: Unable to locate RSDP
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:f0000000)
[    0.000000] Detected 1380.756 MHz processor.
[ 1271.363344] Built 1 zonelists.  Total pages: 65024
[ 1271.363349] Kernel command line: root=UUID=e3a0e9aa-0ff9-4e2c-83f7-ec6232853855 ro quiet splash
[ 1271.363559] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 1271.363582] mapped APIC to ffffd000 (01209000)
[ 1271.363604] Enabling fast FPU save and restore... done.
[ 1271.363610] Enabling unmasked SIMD FPU exception support... done.
[ 1271.363633] Initializing CPU#0
[ 1271.363774] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 1271.365168] Console: colour VGA+ 80x25
[ 1271.365552] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 1271.365721] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 1271.368931] Memory: 248888k/262144k available (1993k kernel code, 12736k reserved, 900k data, 328k init, 0k highmem)
[ 1271.368942] virtual kernel memory layout:
[ 1271.368943]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[ 1271.368945]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 1271.368946]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[ 1271.368948]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[ 1271.368949]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[ 1271.368950]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[ 1271.368952]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[ 1271.368956] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 1271.580059] Calibrating delay using timer specific routine.. 9446.93 BogoMIPS (lpj=18893871)
[ 1271.580190] Security Framework v1.0.0 initialized
[ 1271.580197] SELinux:  Disabled at boot.
[ 1271.580236] Mount-cache hash table entries: 512
[ 1271.580515] CPU: After generic identify, caps: 0f80b9b9 00000000 00000000 00000000 00000001 00000000 00000000
[ 1271.580537] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 1271.580540] CPU: L3 cache: 4096K
[ 1271.580552] CPU: After all inits, caps: 0f80b9b9 00000000 00000000 00000140 00000001 00000000 00000000
[ 1271.580596] Compat vDSO mapped to ffffe000.
[ 1271.580600] Remapping vsyscall page to ffffe000
[ 1271.580641] Checking 'hlt' instruction... OK.
[ 1271.582827] SMP alternatives: switching to UP code
[ 1271.583098] Freeing SMP alternatives: 11k freed
[ 1271.583451] Early unpacking initramfs... done
[ 1272.043069] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[ 1272.043092] SMP motherboard not detected.
[ 1272.043095] Local APIC not detected. Using dummy APIC emulation.
[ 1272.043166] Brought up 1 CPUs
[ 1272.043595] Booting paravirtualized kernel on bare hardware
[ 1272.043754] Time: 19:02:21  Date: 10/01/107
[ 1272.043798] NET: Registered protocol family 16
[ 1272.043955] EISA bus registered
[ 1272.044271] PCI: PCI BIOS revision 2.10 entry at 0xf81a4, last bus=1
[ 1272.044273] PCI: Using configuration type 1
[ 1272.044276] Setting up standard PCI resources
[ 1272.045616] ACPI: Interpreter disabled.
[ 1272.045620] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 1272.045628] pnp: PnP ACPI: disabled
[ 1272.045631] PnPBIOS: Scanning system for PnP BIOS support...
[ 1272.045644] PnPBIOS: PnP BIOS support was not detected.
[ 1272.045716] PCI: Probing PCI hardware
[ 1272.045719] PCI: Probing PCI hardware (bus 00)
[ 1272.046289] Boot video device is 0000:00:02.0
[ 1272.047969] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[ 1272.051912] PCI: Device 0000:00:1d.7 not found by BIOS
[ 1272.054352] PCI: Device 0000:00:1f.5 not found by BIOS
[ 1272.054378] NET: Registered protocol family 8
[ 1272.054380] NET: Registered protocol family 20
[ 1272.054787] NET: Registered protocol family 2
[ 1272.168565] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 1272.168705] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 1272.168882] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 1272.168968] TCP: Hash tables configured (established 8192 bind 4096)
[ 1272.168973] TCP reno registered
[ 1272.176041] checking if image is initramfs... it is
[ 1272.946350] Freeing initrd memory: 6785k freed
[ 1272.946796] audit: initializing netlink socket (disabled)
[ 1272.946814] audit(1193943742.324:1): initialized
[ 1272.946943] VFS: Disk quotas dquot_6.5.1
[ 1272.946962] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1272.947145] io scheduler noop registered
[ 1272.947148] io scheduler anticipatory registered
[ 1272.947150] io scheduler deadline registered
[ 1272.947161] io scheduler cfq registered (default)
[ 1272.947477] isapnp: Scanning for PnP cards...
[ 1274.159295] isapnp: No Plug & Play device found
[ 1274.182290] Real Time Clock Driver v1.12ac
[ 1274.182402] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 1274.183144] mice: PS/2 mouse device common for all mice
[ 1274.184189] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 1274.184476] input: Macintosh mouse button emulation as /class/input/input0
[ 1274.184544] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1274.184549] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1274.185468] PNP: No PS/2 controller found. Probing ports directly.
[ 1274.186257] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1274.186262] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1274.186905] input: AT Translated Set 2 keyboard as /class/input/input1
[ 1274.187106] EISA: Probing bus 0 at eisa.0
[ 1274.187118] Cannot allocate resource for EISA slot 1
[ 1274.187137] Cannot allocate resource for EISA slot 4
[ 1274.187139] Cannot allocate resource for EISA slot 5
[ 1274.187142] Cannot allocate resource for EISA slot 6
[ 1274.187145] Cannot allocate resource for EISA slot 7
[ 1274.187156] EISA: Detected 0 cards.
[ 1274.187329] TCP cubic registered
[ 1274.187337] NET: Registered protocol family 1
[ 1274.187357] Using IPI No-Shortcut mode
[ 1274.187383]   Magic number: 15:82:40
[ 1274.187710] Freeing unused kernel memory: 328k freed
[ 1274.188747] Time: tsc clocksource has been installed.
[ 1276.134204] Capability LSM initialized
[ 1276.679778] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 1291.697173] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[ 1291.697181]   [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
[ 1291.697883] eth0: RealTek RTL-8029 found at 0x4c00, IRQ 10, 00:FB:11:9E:F1:51.
[ 1291.723867] usbcore: registered new interface driver usbfs
[ 1291.723953] usbcore: registered new interface driver hub
[ 1291.723988] usbcore: registered new device driver usb
[ 1291.725473] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 1291.725484] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 1291.725954] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 1291.726060] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[ 1291.726073] ehci_hcd 0000:00:1d.7: irq 9, io mem 0xc1000000
[ 1291.726189] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 1291.726311] usb usb1: configuration #1 chosen from 1 choice
[ 1291.726363] hub 1-0:1.0: USB hub found
[ 1291.726375] hub 1-0:1.0: 8 ports detected
[ 1291.873816] SCSI subsystem initialized
[ 1291.948100] libata version 2.20 loaded.
[ 1291.949990] ata_piix 0000:00:1f.1: version 2.10ac1
[ 1291.950079] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 1291.950174] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00016c00 irq 14
[ 1291.950239] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00016c08 irq 15
[ 1291.950271] scsi0 : ata_piix
[ 1292.115808] USB Universal Host Controller Interface driver v3.0
[ 1292.396153] ata1.00: ATA-5: Virtual  HDD [0], FWR10003, max UDMA/100
[ 1292.396165] ata1.00: 16384032 sectors, multi 128: LBA48 
[ 1292.396168] ata1.01: ATAPI, max UDMA/25
[ 1292.397021] ata1.00: configured for UDMA/100
[ 1292.623898] ata1.01: configured for UDMA/25
[ 1292.623933] scsi1 : ata_piix
[ 1292.624059] ata2: port disabled. ignoring.
[ 1292.624359] scsi 0:0:0:0: Direct-Access     ATA      Virtual  HDD [0] FWR1 PQ: 0 ANSI: 5
[ 1292.628628] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1292.628668] ata1.01: (BMDMA stat 0x66)
[ 1292.628674] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[ 1292.628676]          res 51/50:03:00:00:00/00:00:00:00:00/b0 Emask 0x20 (host bus error)
[ 1292.849804] ata1.00: configured for UDMA/100
[ 1293.075346] ata1.01: configured for UDMA/25
[ 1293.075368] ata1: EH complete
[ 1293.079391] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1293.079398] ata1.01: (BMDMA stat 0x66)
[ 1293.079403] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[ 1293.079405]          res 51/50:03:00:00:00/00:00:00:00:00/b0 Emask 0x20 (host bus error)
[ 1293.302247] ata1.00: configured for UDMA/100
[ 1293.524630] ata1.01: configured for UDMA/25
[ 1293.524651] ata1: EH complete
[ 1293.528538] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1293.528544] ata1.01: (BMDMA stat 0x66)
[ 1293.528550] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[ 1293.528552]          res 51/50:03:00:00:00/00:00:00:00:00/b0 Emask 0x20 (host bus error)
[ 1293.751675] ata1.00: configured for UDMA/100
[ 1293.964319] ata1.01: configured for UDMA/25
[ 1293.964344] ata1: EH complete
[ 1293.968708] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1293.968717] ata1.01: (BMDMA stat 0x66)
[ 1293.968729] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[ 1293.968733]          res 51/50:03:00:00:00/00:00:00:00:00/b0 Emask 0x20 (host bus error)
[ 1294.112140] ata1.00: configured for UDMA/100
[ 1294.251972] ata1.01: configured for UDMA/25
[ 1294.252008] ata1: EH complete
[ 1294.260157] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 1294.260174] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 1294.260581] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1294.260686] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00005000
[ 1294.262657] usb usb2: configuration #1 chosen from 1 choice
[ 1294.263158] hub 2-0:1.0: USB hub found
[ 1294.263170] hub 2-0:1.0: 2 ports detected
[ 1294.298497] SCSI device sda: 16384032 512-byte hdwr sectors (8389 MB)
[ 1294.298511] sda: Write Protect is off
[ 1294.298514] sda: Mode Sense: 00 3a 00 00
[ 1294.298528] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1294.298616] SCSI device sda: 16384032 512-byte hdwr sectors (8389 MB)
[ 1294.298625] sda: Write Protect is off
[ 1294.298627] sda: Mode Sense: 00 3a 00 00
[ 1294.298641] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1294.298645]  sda: sda1 sda2 < sda5 >
[ 1294.339803] sd 0:0:0:0: Attached scsi disk sda
[ 1294.357772] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1294.649620] Attempting manual resume
[ 1294.649630] swsusp: Resume From Partition 8:5
[ 1294.649632] PM: Checking swsusp image.
[ 1294.650249] PM: Resume from disk failed.
[ 1294.688479] kjournald starting.  Commit interval 5 seconds
[ 1294.688490] EXT3-fs: mounted filesystem with ordered data mode.
[ 1315.933690] NET: Registered protocol family 17
[ 1317.972863] iTCO_vendor_support: vendor-support=0
[ 1317.987350] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 1317.987537] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x1060)
[ 1317.987586] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
[ 1317.987638] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 1318.026940] Linux agpgart interface v0.102 (c) Dave Jones
[ 1318.031687] agpgart: Detected an Intel i815 Chipset.
[ 1318.034548] agpgart: AGP aperture is 64M @ 0xe0000000
[ 1318.219905] intel_rng: FWH not detected
[ 1318.397111] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[ 1318.888777] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[ 1319.921648] intel8x0_measure_ac97_clock: measured 11015 usecs
[ 1319.921655] intel8x0: measured clock 743713 rejected
[ 1319.921658] intel8x0: clocking to 48000
[ 1320.318470] fuse init (API version 7.8)
[ 1320.489297] lp: driver loaded but no devices found
[ 1320.601768] Adding 393552k swap on /dev/disk/by-uuid/0af30e55-a53d-4ea8-b0d6-65f50fa3dfc6.  Priority:-1 extents:1 across:393552k
[ 1320.784741] EXT3 FS on sda1, internal journal
[ 1321.051710] NET: Registered protocol family 10
[ 1321.051868] lo: Disabled Privacy Extensions
[ 1328.270131] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[ 1328.270198] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[ 1328.270379] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[ 1328.270464] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[ 1330.963489] eth0: no IPv6 routers present
[ 1332.628754] ppdev: user-space parallel port driver
[ 1332.988723] mtrr: your processor doesn't support write-combining
[ 1334.387460] apm: BIOS not found.
[ 1334.992881] Bluetooth: Core ver 2.11
[ 1334.992960] NET: Registered protocol family 31
[ 1334.992964] Bluetooth: HCI device and connection manager initialized
[ 1334.992968] Bluetooth: HCI socket layer initialized
[ 1335.121236] Bluetooth: L2CAP ver 2.8
[ 1335.121241] Bluetooth: L2CAP socket layer initialized
[ 1335.176906] Bluetooth: RFCOMM socket layer initialized
[ 1335.176925] Bluetooth: RFCOMM TTY layer initialized
[ 1335.176928] Bluetooth: RFCOMM ver 1.8
[ 1448.568714] TSC appears to be running slowly. Marking it as unstable
[  161.148000] Time: pit clocksource has been installed.
[  841.648000] eth0: no IPv6 routers present
ken@Ubuntu:~$

---

### Post by Ken T on 2007-11-05
Any takers on this one? Output from dmesg attached below.... thanks, K.

---

