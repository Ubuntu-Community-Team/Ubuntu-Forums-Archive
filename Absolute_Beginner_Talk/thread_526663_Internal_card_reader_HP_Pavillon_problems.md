---
title: "Internal card reader HP Pavillon problems"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-15
I am not sure what if anything is going on with this internal reader, it is hooked up to a usb header on the motherboard. It does seem to have power as when I plug something into the USB port on it I get lights that flicker, seems like not enough power is going to it. Plus the led power light does not light up?





[ 0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e7800 size: 0000000000018800 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000013df0000 end: 0000000013ef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000013ef0000 size: 000000000000fc00 end: 0000000013effc00 type: 3
[    0.000000] copy_e820_map() start: 0000000013effc00 size: 0000000000000400 end: 0000000013f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000013f00000 size: 0000000000100000 end: 0000000014000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000013ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000013ef0000 - 0000000013effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000013effc00 - 0000000013f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000013f00000 - 0000000014000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 318MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 8164:cool: 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    81648
[    0.000000]   HighMem     81648 ->    81648
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81648
[    0.000000] On node 0 totalpages: 81648
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 605 pages used for memmap
[    0.000000]   Normal zone: 76947 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7470
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x13efcb9e
[    0.000000] ACPI: FADT (v001 HP     Hawk     0x06040000 PTL  0x000f4240) @ 0x13effb64
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x13effbd8
[    0.000000] ACPI: DSDT (v001  INTEL  Whitney 0x06040000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebf00000)
[    0.000000] Detected 701.661 MHz processor.
[   34.921527] Built 1 zonelists.  Total pages: 81011
[   34.921537] Kernel command line: root=UUID=d2c1942f-a382-4573-b2fe-2b24961fc71c ro quiet splash
[   34.922107] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   34.922133] mapped APIC to ffffd000 (0128a000)
[   34.922144] Enabling fast FPU save and restore... done.
[   34.922152] Enabling unmasked SIMD FPU exception support... done.
[   34.922175] Initializing CPU#0
[   34.922294] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   34.924662] Console: colour VGA+ 80x25
[   34.926101] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.928176] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   34.970279] Memory: 312504k/326592k available (1992k kernel code, 13448k reserved, 900k data, 328k init, 0k highmem)
[   34.970336] virtual kernel memory layout:
[   34.970339]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   34.970344]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.970348]     vmalloc : 0xd4800000 - 0xff7fe000   ( 687 MB)
[   34.970352]     lowmem  : 0xc0000000 - 0xd3ef0000   ( 318 MB)
[   34.970356]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   34.970361]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   34.970365]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   34.970375] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   35.050259] Calibrating delay using timer specific routine.. 1404.65 BogoMIPS (lpj=2809305)
[   35.050394] Security Framework v1.0.0 initialized
[   35.050424] SELinux:  Disabled at boot.
[   35.050481] Mount-cache hash table entries: 512
[   35.050938] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   35.050974] CPU: L1 I cache: 16K, L1 D cache: 16K
[   35.050983] CPU: L2 cache: 128K
[   35.050993] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   35.051027] Compat vDSO mapped to ffffe000.
[   35.051054] Remapping vsyscall page to ffffe000
[   35.051088] Checking 'hlt' instruction... OK.
[   35.066557] SMP alternatives: switching to UP code
[   35.067102] Freeing SMP alternatives: 11k freed
[   35.067748] Early unpacking initramfs... done
[   36.059752] CPU0: Intel Celeron (Coppermine) stepping 03
[   36.059774] SMP motherboard not detected.
[   36.059782] Local APIC not detected. Using dummy APIC emulation.
[   36.059944] Brought up 1 CPUs
[   36.060818] Booting paravirtualized kernel on bare hardware
[   36.061097] Time:  3:05:46  Date: 07/15/107
[   36.061213] NET: Registered protocol family 16
[   36.061652] EISA bus registered
[   36.063074] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[   36.063082] PCI: Using configuration type 1
[   36.063088] Setting up standard PCI resources
[   36.071031] ACPI: Interpreter disabled.
[   36.071049] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.071081] pnp: PnP ACPI: disabled
[   36.071089] PnPBIOS: Scanning system for PnP BIOS support...
[   36.071202] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7490
[   36.071212] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9da9, dseg 0x400
[   36.079713] PnPBIOS: 20 nodes reported by PnP BIOS; 20 recorded by driver
[   36.079915] PCI: Probing PCI hardware
[   36.079926] PCI: Probing PCI hardware (bus 00)
[   36.080298] Boot video device is 0000:00:01.0
[   36.080476] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   36.080487] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   36.081082] PCI: Transparent bridge - 0000:00:1e.0
[   36.082902] PCI: Using IRQ router PIIX/ICH [8086/2410] at 0000:00:1f.0
[   36.082946] PCI: setting IRQ 9 as level-triggered
[   36.082954] PCI: Found IRQ 9 for device 0000:00:1f.5
[   36.082973] PCI: Sharing IRQ 9 with 0000:00:1f.3
[   36.082988] PCI: Found IRQ 9 for device 0000:01:08.0
[   36.082998] PCI: Sharing IRQ 9 with 0000:00:01.0
[   36.087127] NET: Registered protocol family 8
[   36.087135] NET: Registered protocol family 20
[   36.087472] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   36.087486] pnp: 00:01: ioport range 0x1000-0x105f has been reserved
[   36.087496] pnp: 00:01: ioport range 0x1100-0x110f has been reserved
[   36.087504] pnp: 00:01: ioport range 0x1060-0x107f has been reserved
[   36.087513] pnp: 00:01: ioport range 0x1180-0x11af has been reserved
[   36.088863] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[   36.088885] PCI: Bridge: 0000:00:1e.0
[   36.088891]   IO window: disabled.
[   36.088904]   MEM window: f4100000-f41fffff
[   36.088913]   PREFETCH window: disabled.
[   36.088943] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.089037] NET: Registered protocol family 2
[   36.126215] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   36.126549] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   36.127162] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   36.127563] TCP: Hash tables configured (established 16384 bind 8192)
[   36.127575] TCP reno registered
[   36.138448] checking if image is initramfs... it is
[   37.952482] Freeing initrd memory: 6785k freed
[   37.953277] Simple Boot Flag at 0x36 set to 0x1
[   37.954079] audit: initializing netlink socket (disabled)
[   37.954126] audit(1187147148.216:1): initialized
[   37.954603] VFS: Disk quotas dquot_6.5.1
[   37.954674] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.954874] io scheduler noop registered
[   37.954885] io scheduler anticipatory registered
[   37.954892] io scheduler deadline registered
[   37.954935] io scheduler cfq registered (default)
[   37.955704] isapnp: Scanning for PnP cards...
[   38.310029] isapnp: No Plug & Play device found
[   38.505010] Real Time Clock Driver v1.12ac
[   38.505397] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.505696] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.506418] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.509329] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.510411] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.511644] mice: PS/2 mouse device common for all mice
[   38.514244] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.514886] input: Macintosh mouse button emulation as /class/input/input0
[   38.515049] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.515066] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.515786] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   38.519000] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.519020] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.519573] EISA: Probing bus 0 at eisa.0
[   38.519598] Cannot allocate resource for EISA slot 1
[   38.519644] EISA: Detected 0 cards.
[   38.519888] TCP cubic registered
[   38.519914] NET: Registered protocol family 1
[   38.519977] Using IPI No-Shortcut mode
[   38.520046]   Magic number: 3:965:57
[   38.521197] Time: tsc clocksource has been installed.
[   38.522133] Freeing unused kernel memory: 328k freed
[   38.708942] input: AT Raw Set 2 keyboard as /class/input/input1
[   40.424301] Capability LSM initialized
[   40.631629] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   42.821832] usbcore: registered new interface driver usbfs
[   42.821918] usbcore: registered new interface driver hub
[   42.822023] usbcore: registered new device driver usb
[   42.826802] USB Universal Host Controller Interface driver v3.0
[   42.826966] PCI: setting IRQ 11 as level-triggered
[   42.826976] PCI: Found IRQ 11 for device 0000:00:1f.2
[   42.827026] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   42.827038] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   42.827401] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   42.827470] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001080
[   42.827942] usb usb1: configuration #1 chosen from 1 choice
[   42.828036] hub 1-0:1.0: USB hub found
[   42.828073] hub 1-0:1.0: 2 ports detected
[   43.087850] SCSI subsystem initialized
[   43.117396] libata version 2.20 loaded.
[   43.136186] ata_piix 0000:00:1f.1: version 2.10ac1
[   43.136266] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   43.136469] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000110a0 irq 14
[   43.136584] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x000110a8 irq 15
[   43.136638] scsi0 : ata_piix
[   43.171830] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   43.300446] ata1.00: ata_hpa_resize 1: sectors = 78125000, hpa_sectors = 78125000
[   43.300464] ata1.00: ATA-6: IC35L060AVV207-0, V22OA66A, max UDMA/100
[   43.300474] ata1.00: 78125000 sectors, multi 16: LBA48 
[   43.308456] ata1.00: ata_hpa_resize 1: sectors = 78125000, hpa_sectors = 78125000
[   43.308476] ata1.00: configured for UDMA/66
[   43.322155] scsi1 : ata_piix
[   43.326616] usb 1-2: configuration #1 chosen from 1 choice
[   43.529399] Floppy drive(s): fd0 is 1.44M
[   43.593802] FDC 0 is a post-1991 82077
[   43.639920] ata2.00: ATAPI, max UDMA/33
[   43.803864] ata2.00: configured for UDMA/33
[   43.811705] scsi 0:0:0:0: Direct-Access     ATA      IC35L060AVV207-0 V22O PQ: 0 ANSI: 5
[   43.818395] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX195E1  ZYS5 PQ: 0 ANSI: 5
[   43.845362] usbcore: registered new interface driver hiddev
[   43.901281] input: HID 062a:0000 as /class/input/input2
[   43.901354] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1f.2-2
[   43.901402] usbcore: registered new interface driver usbhid
[   43.901414] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   43.959696] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[   43.959809] sda: Write Protect is off
[   43.959817] sda: Mode Sense: 00 3a 00 00
[   43.959869] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.960067] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[   43.960099] sda: Write Protect is off
[   43.960107] sda: Mode Sense: 00 3a 00 00
[   43.960153] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.960165]  sda: sda1 sda2 < sda5 >
[   44.016417] sd 0:0:0:0: Attached scsi disk sda
[   44.018522] sr0: scsi3-mmc drive: 239x/40x writer cd/rw xa/form2 cdda tray
[   44.018534] Uniform CD-ROM driver Revision: 3.20
[   44.019254] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   44.039092] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.039771] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   44.380018] Attempting manual resume
[   44.380030] swsusp: Resume From Partition 8:5
[   44.380036] PM: Checking swsusp image.
[   44.381526] PM: Resume from disk failed.
[   44.480519] kjournald starting.  Commit interval 5 seconds
[   44.480574] EXT3-fs: mounted filesystem with ordered data mode.
[   60.606690] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.613759] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   60.995687] iTCO_vendor_support: vendor-support=0
[   61.007636] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   61.007953] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   61.007973] iTCO_wdt: No card detected
[   61.041282] Intel 82802 RNG detected
[   61.796107] Linux agpgart interface v0.102 (c) Dave Jones
[   62.159482] agpgart: Detected an Intel i810 Chipset.
[   62.182833] agpgart: AGP aperture is 64M @ 0xf8000000
[   62.222214] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   62.760778] input: PC Speaker as /class/input/input3
[   63.724397] PCI: Enabling device 0000:01:08.0 (0110 -> 0112)
[   63.724426] PCI: Found IRQ 9 for device 0000:01:08.0
[   63.724440] PCI: Sharing IRQ 9 with 0000:00:01.0
[   63.724465] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
[   63.724487] RT61: Vendor = 0x1814, Product = 0x0301 
[   63.897007] PNPBIOS fault.. attempting recovery.
[   63.897025] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   63.897033] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   63.897041] PnPBIOS: Check with your vendor for an updated BIOS
[   63.897049] PnPBIOS: set_dev_node: unexpected status 0x37
[   63.897056] pnp: Failed to activate device 00:16.
[   63.897070] mpu401: probe of 00:16 failed with error -5
[   63.897084] MPU-401 device not found or device busy
[   64.019853] parport: PnPBIOS parport detected.
[   64.019902] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   64.376816] PCI: Found IRQ 9 for device 0000:00:1f.5
[   64.376849] PCI: Sharing IRQ 9 with 0000:00:1f.3
[   64.376922] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   64.689093] intel8x0_measure_ac97_clock: measured 54970 usecs
[   64.689111] intel8x0: clocking to 48000
[   64.782207] RT61: RfIcType= 3
[   65.383640] fuse init (API version 7.:cool:
[   65.456381] lp0: using parport0 (interrupt-driven).
[ 65.583056] Adding 931728k swap on /dev/disk/by-uuid/b87c6b86-a9b1-400b-9065-a17584da64aa. Priority:-1 extents:1 across:931728k
[   65.801041] EXT3 FS on sda1, internal journal
[   68.171605] NET: Registered protocol family 17
[   73.055499] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   73.128110] usbcore: registered new interface driver ndiswrapper
[   75.949891] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   75.950291] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   75.951028] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   75.951463] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   89.611332] ppdev: user-space parallel port driver
[   91.491734] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   93.582714] Bluetooth: Core ver 2.11
[   93.582906] NET: Registered protocol family 31
[   93.582915] Bluetooth: HCI device and connection manager initialized
[   93.582927] Bluetooth: HCI socket layer initialized
[   93.801083] Bluetooth: L2CAP ver 2.8
[   93.801099] Bluetooth: L2CAP socket layer initialized
[   93.812571] Bluetooth: RFCOMM socket layer initialized
[   93.812622] Bluetooth: RFCOMM TTY layer initialized
[   93.812628] Bluetooth: RFCOMM ver 1.8
[  135.404642] NET: Registered protocol family 10
[  135.405029] lo: Disabled Privacy Extensions
[  146.323441] ra1: no IPv6 routers present
[  196.855702] usb 1-2: USB disconnect, address 2
[  226.318462] usb 1-2: new low speed USB device using uhci_hcd and address 119
[  226.473235] usb 1-2: configuration #1 chosen from 1 choice
[  226.489552] input: HID 062a:0000 as /class/input/input4
[  226.489775] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1f.2-2
[  273.943592] usb 1-2: USB disconnect, address 119
[  297.864060] usb 1-2: new low speed USB device using uhci_hcd and address 88
[  298.018793] usb 1-2: configuration #1 chosen from 1 choice
[  298.035092] input: HID 062a:0000 as /class/input/input5
[  298.035315] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1f.2-2
naty@naty-desktop:~$

---

### Post by yogo on 2007-08-16
No ideas anyone?

---

### Post by alklein on 2007-08-28
I have the same problem - pavilion a556x, SD card reader lights up when the card is inserted, but nothing mounted, no errors, nothing.  Been looking for weeks.

Adam Klein

---

