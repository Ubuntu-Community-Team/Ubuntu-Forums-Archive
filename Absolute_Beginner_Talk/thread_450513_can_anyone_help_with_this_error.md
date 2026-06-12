---
title: "can anyone help with this error"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-05-21
9.047183] scsi1 : ata_piix
[ 29.214040] ATA: abnormal status 0x7F on port 0x00010177
[ 29.225235] ATA: abnormal status 0x7F on port 0x00010177

[ 139.784220] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 139.784254] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x46 d
ata 8 in
[ 139.784259] res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeo
ut)
[ 146.782010] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 169.790770] ata2: port failed to respond (30 secs, Status 0xd0)
[ 169.790795] ata2: soft resetting port

this was frm the cmd    dmesg | more

shrikant@shrikant-desktop:~$ dmesg | more
[ 0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2
(Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.2
7-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 en
d: 000000000009fc00 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 en
d: 00000000000a0000 type: 2
[ 0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 en
d: 0000000000100000 type: 2
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fe00000 en
d: 000000000ff00000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 en
d: 0000000100000000 type: 2
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000000ff00000 (usable)
[ 0.000000] BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 255MB LOWMEM available.
[ 0.000000] Entering add_active_range(0, 0, 65280) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 65280
[ 0.000000] HighMem 65280 -> 65280
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 65280
[ 0.000000] On node 0 totalpages: 65280
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 478 pages used for memmap
[ 0.000000] Normal zone: 60706 pages, LIFO batch:15
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] DMI 2.2 present.
[ 0.000000] ACPI: Unable to locate RSDP
[ 0.000000] Allocating PCI resources starting at 10000000 (gap: 0ff00000:efc0
0000)
[ 0.000000] Detected 701.633 MHz processor.
[ 21.460363] Built 1 zonelists. Total pages: 64770
[ 21.460373] Kernel command line: root=UUID=6ac2775e-df02-4bd3-ab89-fafd358b6b
2f ro quiet splash
[ 21.460960] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 21.460988] mapped APIC to ffffd000 (0120a000)
[ 21.461000] Enabling fast FPU save and restore... done.
[ 21.461008] Enabling unmasked SIMD FPU exception support... done.
[ 21.461039] Initializing CPU#0
[ 21.461174] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 21.463382] Console: colour VGA+ 80x25
[ 21.463947] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 21.464458] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 21.497653] Memory: 247872k/261120k available (1992k kernel code, 12732k rese
rved, 893k data, 328k init, 0k highmem)
[ 21.497688] virtual kernel memory layout:
[ 21.497691] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 21.497696] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 21.497700] vmalloc : 0xd0800000 - 0xff7fe000 ( 751 MB)
[ 21.497704] lowmem : 0xc0000000 - 0xcff00000 ( 255 MB)
[ 21.497708] .init : 0xc03d7000 - 0xc0429000 ( 328 kB)
[ 21.497712] .data : 0xc02f2264 - 0xc03d16d4 ( 893 kB)
[ 21.497716] .text : 0xc0100000 - 0xc02f2264 (1992 kB)
[ 21.497726] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[ 21.577142] Calibrating delay using timer specific routine.. 1404.60 BogoMIPS
 (lpj=2809213)
[ 21.577264] Security Framework v1.0.0 initialized
[ 21.577285] SELinux: Disabled at boot.
[ 21.577333] Mount-cache hash table entries: 512
[ 21.577697] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 000
00000 00000000 00000000 00000000
[ 21.577727] CPU: L1 I cache: 16K, L1 D cache: 16K
[ 21.577735] CPU: L2 cache: 256K
[ 21.577744] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 0
0000000 00000000 00000000
[ 21.577773] Compat vDSO mapped to ffffe000.
[ 21.577792] Remapping vsyscall page to ffffe000
[ 21.577818] Checking 'hlt' instruction... OK.
[ 21.593411] SMP alternatives: switching to UP code
[ 21.593909] Freeing SMP alternatives: 11k freed
[ 21.594474] Early unpacking initramfs... done
[ 22.530904] CPU0: Intel Pentium III (Coppermine) stepping 03
[ 22.530927] SMP motherboard not detected.
[ 22.530936] Local APIC not detected. Using dummy APIC emulation.
[ 22.531098] Brought up 1 CPUs
[ 22.531941] Booting paravirtualized kernel on bare hardware
[ 22.548873] Time: 15:02:34 Date: 04/21/107
[ 22.548993] NET: Registered protocol family 16
[ 22.549362] EISA bus registered
[ 22.575028] PCI: PCI BIOS revision 2.10 entry at 0xfb0e0, last bus=1
[ 22.575036] PCI: Using configuration type 1
[ 22.575042] Setting up standard PCI resources
[ 22.577339] ACPI: Interpreter disabled.
[ 22.577353] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 22.577381] pnp: PnP ACPI: disabled
[ 22.577392] PnPBIOS: Scanning system for PnP BIOS support...
[ 22.577547] PnPBIOS: Found PnP BIOS installation structure at 0xc00fba60
[ 22.577559] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xba90, dseg 0xf0000
[ 22.579955] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[ 22.580146] PCI: Probing PCI hardware
[ 22.580160] PCI: Probing PCI hardware (bus 00)
[ 22.580408] Boot video device is 0000:00:01.0
[ 22.580561] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[ 22.580570] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[ 22.581228] PCI: Transparent bridge - 0000:00:1e.0
[ 22.582785] PCI: Using IRQ router PIIX/ICH [8086/2410] at 0000:00:1f.0
[ 22.592581] NET: Registered protocol family 8
[ 22.592589] NET: Registered protocol family 20
[ 22.592939] pnp: 00:0d: ioport range 0x3f0-0x3f1 has been reserved
[ 22.593810] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[ 22.593834] PCI: Bridge: 0000:00:1e.0
[ 22.593842] IO window: c000-cfff
[ 22.593855] MEM window: d4000000-d5ffffff
[ 22.593865] PREFETCH window: 10000000-100fffff
[ 22.593892] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 22.593973] NET: Registered protocol family 2
[ 22.633048] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 22.633276] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 22.633514] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 22.633651] TCP: Hash tables configured (established 8192 bind 4096)
[ 22.633660] TCP reno registered
[ 22.645226] checking if image is initramfs... it is
[ 24.400758] Freeing initrd memory: 6784k freed
[ 24.402039] audit: initializing netlink socket (disabled)
[ 24.402089] audit(1179759755.128:1): initialized
[ 24.402501] VFS: Disk quotas dquot_6.5.1
[ 24.402569] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 24.402749] io scheduler noop registered
[ 24.402758] io scheduler anticipatory registered
[ 24.402765] io scheduler deadline registered
[ 24.402802] io scheduler cfq registered (default)
[ 24.403500] isapnp: Scanning for PnP cards...
[ 24.757619] isapnp: No Plug & Play device found
[ 24.855315] Real Time Clock Driver v1.12ac
[ 24.855530] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[ 24.855763] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 24.856330] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 24.858122] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 24.858805] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 24.859606] mice: PS/2 mouse device common for all mice
[ 24.861452] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[ 24.862265] input: Macintosh mouse button emulation as /class/input/input0
[ 24.862374] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 24.862388] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[ 24.862929] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 24.866882] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 24.866900] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 24.867339] EISA: Probing bus 0 at eisa.0
[ 24.867378] Cannot allocate resource for EISA slot 4
[ 24.867405] EISA: Detected 0 cards.
[ 24.867661] TCP cubic registered
[ 24.867687] NET: Registered protocol family 1
[ 24.867751] Using IPI No-Shortcut mode
[ 24.867822] Magic number: 7:124:33
[ 24.868117] Time: tsc clocksource has been installed.
[ 24.869640] Freeing unused kernel memory: 328k freed
[ 24.886423] input: AT Translated Set 2 keyboard as /class/input/input1
[ 26.542200] Capability LSM initialized
[ 26.702364] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 28.549938] usbcore: registered new interface driver usbfs
[ 28.550014] usbcore: registered new interface driver hub
[ 28.550088] usbcore: registered new device driver usb
[ 28.554778] USB Universal Host Controller Interface driver v3.0
[ 28.554927] PCI: setting IRQ 9 as level-triggered
[ 28.554935] PCI: Found IRQ 9 for device 0000:00:1f.2
[ 28.555129] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 28.555142] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[ 28.555513] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus numbe
r 1
[ 28.555567] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000d000
[ 28.555915] usb usb1: configuration #1 chosen from 1 choice
[ 28.556002] hub 1-0:1.0: USB hub found
[ 28.556031] hub 1-0:1.0: 2 ports detected
[ 28.661233] uhci_hcd 0000:01:0a.0: UHCI Host Controller
[ 28.661349] uhci_hcd 0000:01:0a.0: new USB bus registered, assigned bus numbe
r 2
[ 28.661402] uhci_hcd 0000:01:0a.0: irq 9, io base 0x0000c400
[ 28.661718] usb usb2: configuration #1 chosen from 1 choice
[ 28.661797] hub 2-0:1.0: USB hub found
[ 28.661826] hub 2-0:1.0: 2 ports detected
[ 28.662650] SCSI subsystem initialized
[ 28.690749] libata version 2.20 loaded.
[ 28.727860] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[ 28.727868] [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
[ 28.763418] uhci_hcd 0000:01:0a.1: UHCI Host Controller
[ 28.763497] uhci_hcd 0000:01:0a.1: new USB bus registered, assigned bus numbe
r 3
[ 28.763546] uhci_hcd 0000:01:0a.1: irq 9, io base 0x0000c800
[ 28.763836] usb usb3: configuration #1 chosen from 1 choice
[ 28.763920] hub 3-0:1.0: USB hub found
[ 28.763946] hub 3-0:1.0: 2 ports detected
[ 28.876742] ata_piix 0000:00:1f.1: version 2.10ac1
[ 28.876820] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 28.876978] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001
f000 irq 14
[ 28.877064] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001
f008 irq 15
[ 28.877104] scsi0 : ata_piix
[ 29.039184] ata1.00: ata_hpa_resize 1: sectors = 39865392, hpa_sectors = 3986
5392
[ 29.039201] ata1.00: ATA-6: SAMSUNG SV2042H, PK100-21, max UDMA/100
[ 29.039210] ata1.00: 39865392 sectors, multi 16: LBA
[ 29.039231] ata1.00: limited to UDMA/33 due to 40-wire cable
[ 29.047141] ata1.00: ata_hpa_resize 1: sectors = 39865392, hpa_sectors = 3986
5392
[ 29.047151] ata1.00: configured for UDMA/33
[ 29.047183] scsi1 : ata_piix
[ 29.214040] ATA: abnormal status 0x7F on port 0x00010177
[ 29.225235] ATA: abnormal status 0x7F on port 0x00010177
[ 29.242040] Floppy drive(s): fd0 is 1.44M
[ 29.313635] FDC 0 is a National Semiconductor PC87306
[ 29.387061] ata2.01: ATAPI, max MWDMA2
[ 29.551022] ata2.01: configured for MWDMA2
[ 29.558865] scsi 0:0:0:0: Direct-Access ATA SAMSUNG SV2042H PK10 PQ
: 0 ANSI: 5
[ 29.559488] scsi 1:0:1:0: CD-ROM SAMSUNG CD-ROM SC-152C CS04 PQ
: 0 ANSI: 5
[ 29.563391] eth0: RealTek RTL-8029 found at 0xc000, IRQ 11, 00:20:18:2B:38:8B
.
[ 29.564319] ehci_hcd 0000:01:0a.2: EHCI Host Controller
[ 29.564433] ehci_hcd 0000:01:0a.2: new USB bus registered, assigned bus numbe
r 4
[ 29.564554] ehci_hcd 0000:01:0a.2: irq 11, io mem 0xd5000000
[ 29.564569] ehci_hcd 0000:01:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[ 29.564841] usb usb4: configuration #1 chosen from 1 choice
[ 29.564925] hub 4-0:1.0: USB hub found
[ 29.564952] hub 4-0:1.0: 4 ports detected
[ 29.616265] SCSI device sda: 39865392 512-byte hdwr sectors (20411 MB)
[ 29.616312] sda: Write Protect is off
[ 29.616320] sda: Mode Sense: 00 3a 00 00
[ 29.616368] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[ 29.616557] SCSI device sda: 39865392 512-byte hdwr sectors (20411 MB)
[ 29.616586] sda: Write Protect is off
[ 29.616593] sda: Mode Sense: 00 3a 00 00
[ 29.616638] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[ 29.616649] sda: sda1 sda2 < sda5 >
[ 29.661713] sd 0:0:0:0: Attached scsi disk sda
[ 29.684180] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 29.684523] sr 1:0:1:0: Attached scsi generic sg1 type 5
[ 29.693288] sr0: scsi3-mmc drive: 8x/52x cd/rw xa/form2 cdda tray
[ 29.693309] Uniform CD-ROM driver Revision: 3.20
[ 29.693477] sr 1:0:1:0: Attached scsi CD-ROM sr0
[ 30.255464] Attempting manual resume
[ 30.255476] swsusp: Resume From Partition 8:5
[ 30.255482] PM: Checking swsusp image.
[ 30.272549] PM: Resume from disk failed.
[ 30.387077] kjournald starting. Commit interval 5 seconds
[ 30.387116] EXT3-fs: mounted filesystem with ordered data mode.
[ 47.843836] NET: Registered protocol family 17
[ 51.445324] iTCO_vendor_support: vendor-support=0
[ 51.455545] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 51.455846] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hard
ware
[ 51.455866] iTCO_wdt: No card detected
[ 51.513482] Intel 82802 RNG detected
[ 51.555990] Linux agpgart interface v0.102 (c) Dave Jones
[ 51.589280] agpgart: Detected an Intel i810 Chipset.
[ 51.603477] agpgart: AGP aperture is 64M @ 0xd0000000
[ 52.651192] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 52.660317] input: PC Speaker as /class/input/input2
[ 52.843822] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[ 52.864973] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 53.255157] parport: PnPBIOS parport detected.
[ 53.255272] parport0: PC-style at 0x378, irq 7 [PCSPP]
[ 53.441599] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[ 54.110778] PCI: setting IRQ 5 as level-triggered
[ 54.110793] PCI: Found IRQ 5 for device 0000:00:1f.5
[ 54.110877] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[ 54.423032] intel8x0_measure_ac97_clock: measured 55245 usecs
[ 54.423049] intel8x0: clocking to 48000
[ 55.695841] fuse init (API version 7.8)
[ 55.755491] lp0: using parport0 (interrupt-driven).
[ 55.859108] Adding 746980k swap on /dev/disk/by-uuid/67a048ae-84f3-4353-9c95-
145c60aaf5b5. Priority:-1 extents:1 across:746980k
[ 56.095971] EXT3 FS on sda1, internal journal
[ 56.550380] NET: Registered protocol family 10
[ 56.550714] lo: Disabled Privacy Extensions
[ 64.402700] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[ 64.402898] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performanc
e
[ 64.403447] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performan
ce
[ 64.403702] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[ 67.150894] eth0: no IPv6 routers present
[ 75.127549] ppdev: user-space parallel port driver
[ 77.524604] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[ 79.317102] Bluetooth: Core ver 2.11
[ 79.317262] NET: Registered protocol family 31
[ 79.317269] Bluetooth: HCI device and connection manager initialized
[ 79.317278] Bluetooth: HCI socket layer initialized
[ 79.445881] Bluetooth: L2CAP ver 2.8
[ 79.445897] Bluetooth: L2CAP socket layer initialized
[ 79.832041] Bluetooth: RFCOMM socket layer initialized
[ 79.832087] Bluetooth: RFCOMM TTY layer initialized
[ 79.832093] Bluetooth: RFCOMM ver 1.8
[ 139.784220] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 139.784254] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x46 d
ata 8 in
[ 139.784259] res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeo
ut)
[ 146.782010] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 169.790770] ata2: port failed to respond (30 secs, Status 0xd0)
[ 169.790795] ata2: soft resetting port
[ 169.957893] ATA: abnormal status 0x7F on port 0x00010177
[ 169.969063] ATA: abnormal status 0x7F on port 0x00010177
[ 170.294834] ata2.01: configured for MWDMA2
[ 170.294910] ata2: EH complete
[ 868.636066] eth0: no IPv6 routers present
shrikant@shrikant-desktop:~$

---

### Post by drshrikant on 2007-05-21
cannot play anything from the cd rom.....

---

### Post by tgalati4 on 2007-05-21
Looks like a hardware problem.  Did the CD ROM work previously?  Try reseating ribbon cables and power connectors.  What is the brand of the CD ROM and about how old?  Did you make any hardware changes recently?

---

### Post by drshrikant on 2007-05-21
samsung cd rom sc 152c
firmware cs04
connection scsi
media cd rom drive
removable yes.

was absolutely fine till i installed ubuntu yesterday...

have made no changes recently to the hardware...

do i need to get a new drive??? this one must be very old indeed..

plz help.

---

### Post by Terl on 2007-05-21
I found this in the bug database.  Maybe it will help.

[Launchpad Link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706")

---

### Post by drshrikant on 2007-05-21
yes that is similar to wht i have... but ne solutions to in??

---

### Post by tgalati4 on 2007-05-22
What version of Ubuntu did you install?  Does your drive work with a live version of Dapper?  It appears that Feisty made some changes with the SCSI and IDE architecture.  That could certainly affect your drive performance.

Because SCSI CD-ROMS are older hardware, it is possible that hardware has died coincidently with  your install.

---

### Post by templer666 on 2007-05-24
please see my post on this here:
[http://ubuntuforums.org/showthread.php?p=2706945#post2706945](http://ubuntuforums.org/showthread.php?p=2706945#post2706945)

interestingly the very same problem exists with windows vista on the very same machine. did they steal open source code here? ;-)

/rw

---

