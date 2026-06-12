---
title: "Cannot access USB floppy from Fiesty"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by paulholbrook on 2007-05-03
I have just installed Fiesty and cannot access my USB attached floppy.  If I go go COMPUTER, the floppy drive does not appear in the set of devices.  My CDROM is there but no floppy.  There is no icon on my desktop for the floppy.  The floppy works fine with Windows XP.  I have a dual boot.
I am running on a Compaq AMD Sempron 3200+

---

### Post by xopher on 2007-05-03
First off, a thing that highly irritates me, and probably other people too. IT'S FEISTY, not fiesty.

Right, now that that's dealt with, is the floppy device recognized?

```
lsusb
```

That lists all your USB-devices, and you should find the drive there, when connected.

---

### Post by paulholbrook on 2007-05-03
Sorry about Feisty.

This is what I got back:

bash: tsusb: command not found

What do I do now?

I just noticed the misspelling.  When I tried  lsusb     nothing was displayed.

---

### Post by Cypher on 2007-05-03
That's "el"susb..not "t"..:)

And don't fret the Feisty/Fiesty/Fiesta..call it 7.04 and be done with it..:)

---

### Post by paulholbrook on 2007-05-03
I retried  lsusb and nothing was returned.

---

### Post by Cypher on 2007-05-03
Is your floppy the only USB device you have plugged in? If not, you should be seeing some numbers and indications that there are other devices present..

---

### Post by paulholbrook on 2007-05-03
Yes, the floppy is the only USB device I have.

---

### Post by Cypher on 2007-05-03
Well then, the fact that "lsusb" is showing nothing would indicate that either the USB port on your computer is busted or the floppy is busted. Can you plug some other USB device and check the "lsusb" output and confirm that you do get something.

This will at least tell you where the breakage is..

---

### Post by paulholbrook on 2007-05-03
I don't have any other USB devices but if I drop Ubuntu and go back to Windows (dual boot) it works fine.

---

### Post by paulholbrook on 2007-05-03
I just borrowed a flash drive from my neighbor and tried it.  Ubuntu "lsusb" doesn't see it either  but Windows can access  both the USB flash drive and the floppy disk.

This is a show stopper for me being able to migrate to Ubuntu.  Do you have any other ideas?

---

### Post by Cypher on 2007-05-03
It looks like the USB driver isn't loading. Can you run "dmesg" after inserting the USB device and see if you any activity, also show us what you get when you type
```

lsmod

```

---

### Post by paulholbrook on 2007-05-03
This is very long.  Is there a better way to send this rather than an imbed?

paul@paul-home:~$ dmsg
bash: dmsg: command not found
paul@paul-home:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001bdf0000 end: 000000001bef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001bef0000 size: 0000000000003000 end: 000000001bef3000 type: 4
[    0.000000] copy_e820_map() start: 000000001bef3000 size: 000000000000d000 end: 000000001bf00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6080
[    0.000000] Entering add_active_range(0, 0, 114416) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114416
[    0.000000]   HighMem    114416 ->   114416
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114416
[    0.000000] On node 0 totalpages: 114416
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109459 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 HP-CPC                                ) @ 0x000f7c60
[    0.000000]   >>> ERROR: Invalid checksum
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1bf00000:c4100000)
[    0.000000] Detected 1790.887 MHz processor.
[   19.698711] Built 1 zonelists.  Total pages: 113523
[   19.698714] Kernel command line: root=UUID=e8cec987-4575-47fc-ac04-004cd818e5fc ro quiet splash noapic
[   19.698854] mapped APIC to ffffd000 (fee00000)
[   19.698856] mapped IOAPIC to ffffc000 (fec00000)
[   19.698859] Enabling fast FPU save and restore... done.
[   19.698861] Enabling unmasked SIMD FPU exception support... done.
[   19.698867] Initializing CPU#0
[   19.698922] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   19.699853] Console: colour VGA+ 80x25
[   19.699978] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.700189] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.707548] Memory: 442432k/457664k available (1992k kernel code, 14688k reserved, 893k data, 328k init, 0k highmem)
[   19.707558] virtual kernel memory layout:
[   19.707559]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   19.707561]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.707562]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   19.707563]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[   19.707565]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   19.707566]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   19.707567]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   19.707570] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.786811] Calibrating delay using timer specific routine.. 3585.44 BogoMIPS (lpj=7170885)
[   19.786846] Security Framework v1.0.0 initialized
[   19.786851] SELinux:  Disabled at boot.
[   19.786865] Mount-cache hash table entries: 512
[   19.786969] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   19.786977] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.786980] CPU: L2 Cache: 256K (64 bytes/line)
[   19.786982] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   19.786991] Compat vDSO mapped to ffffe000.
[   19.786994] Remapping vsyscall page to ffffe000
[   19.787003] Checking 'hlt' instruction... OK.
[   19.802886] SMP alternatives: switching to UP code
[   19.803052] Freeing SMP alternatives: 11k freed
[   19.803247] Early unpacking initramfs... done
[   20.118408] CPU0: AMD Sempron(tm) Processor 3200+ stepping 02
[   20.118427] Total of 1 processors activated (3585.44 BogoMIPS).
[   20.226264] Brought up 1 CPUs
[   20.226455] Booting paravirtualized kernel on bare hardware
[   20.226538] Time: 15:36:10  Date: 04/03/107
[   20.226564] NET: Registered protocol family 16
[   20.226638] EISA bus registered
[   20.259327] PCI: PCI BIOS revision 3.00 entry at 0xf1d50, last bus=2
[   20.259329] PCI: Using configuration type 1
[   20.259331] Setting up standard PCI resources
[   20.261466] ACPI: Interpreter disabled.
[   20.261471] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.261478] pnp: PnP ACPI: disabled
[   20.261481] PnPBIOS: Scanning system for PnP BIOS support...
[   20.261712] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc3b0
[   20.261718] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3e0, dseg 0xf0000
[   20.262302] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   20.262335] PCI: Probing PCI hardware
[   20.262340] PCI: Probing PCI hardware (bus 00)
[   20.263124] Boot video device is 0000:01:05.0
[   20.263478] PCI: Transparent bridge - 0000:00:14.4
[   20.311353] NET: Registered protocol family 8
[   20.311355] NET: Registered protocol family 20
[   20.311409] pnp: 00:0b: ioport range 0x800-0x87f has been reserved
[   20.311621] PCI: Bridge: 0000:00:01.0
[   20.311624]   IO window: e000-efff
[   20.311627]   MEM window: fde00000-fdefffff
[   20.311630]   PREFETCH window: d8000000-dfffffff
[   20.311634] PCI: Bridge: 0000:00:14.4
[   20.311637]   IO window: d000-dfff
[   20.311644]   MEM window: fdd00000-fddfffff
[   20.311649]   PREFETCH window: fdc00000-fdcfffff
[   20.311697] NET: Registered protocol family 2
[   20.342129] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.342210] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   20.342305] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   20.342354] TCP: Hash tables configured (established 16384 bind 8192)
[   20.342357] TCP reno registered
[   20.354156] checking if image is initramfs... it is
[   20.982875] Freeing initrd memory: 7005k freed
[   20.983230] audit: initializing netlink socket (disabled)
[   20.983241] audit(1178206571.368:1): initialized
[   20.983347] VFS: Disk quotas dquot_6.5.1
[   20.983364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.983417] io scheduler noop registered
[   20.983419] io scheduler anticipatory registered
[   20.983421] io scheduler deadline registered
[   20.983434] io scheduler cfq registered (default)
[   20.983629] isapnp: Scanning for PnP cards...
[   21.337625] isapnp: No Plug & Play device found
[   21.365278] Real Time Clock Driver v1.12ac
[   21.365329] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.366030] mice: PS/2 mouse device common for all mice
[   21.366432] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.366615] input: Macintosh mouse button emulation as /class/input/input0
[   21.366641] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.366645] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.366891] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   21.370000] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.370006] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.370128] EISA: Probing bus 0 at eisa.0
[   21.370171] EISA: Detected 0 cards.
[   21.370239] TCP cubic registered
[   21.370247] NET: Registered protocol family 1
[   21.370267] Using IPI No-Shortcut mode
[   21.370286]   Magic number: 7:389:638
[   21.370591] Freeing unused kernel memory: 328k freed
[   21.372673] Time: tsc clocksource has been installed.
[   21.396319] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.580188] Capability LSM initialized
[   22.627344] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   23.021653] SCSI subsystem initialized
[   23.025908] libata version 2.20 loaded.
[   23.054326] sata_sil 0000:00:12.0: version 2.2
[   23.054425] ata1: SATA max UDMA/100 cmd 0xdc828080 ctl 0xdc82808a bmdma 0xdc828000 irq 11
[   23.054450] ata2: SATA max UDMA/100 cmd 0xdc8280c0 ctl 0xdc8280ca bmdma 0xdc828008 irq 11
[   23.054463] scsi0 : sata_sil
[   23.093818] usbcore: registered new interface driver usbfs
[   23.093838] usbcore: registered new interface driver hub
[   23.093855] usbcore: registered new device driver usb
[   23.094538] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.114552] 8139too Fast Ethernet driver 0.9.28
[   23.125252] ieee1394: Initialized config rom entry `ip1394'
[   23.369812] ata1: SATA link down (SStatus 0 SControl 300)
[   23.369834] scsi1 : sata_sil
[   23.681373] ata2: SATA link down (SStatus 0 SControl 300)
[   23.683370] PCI: No IRQ known for interrupt pin A of device 0000:00:13.0. Please try using pci=biosirq.
[   23.683375] ohci_hcd 0000:00:13.0: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.0 setup!
[   23.683382] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -19
[   23.683400] PCI: No IRQ known for interrupt pin A of device 0000:00:13.1. Please try using pci=biosirq.
[   23.683403] ohci_hcd 0000:00:13.1: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.1 setup!
[   23.683408] ohci_hcd 0000:00:13.1: init 0000:00:13.1 fail, -19
[   23.683472] PCI: No IRQ known for interrupt pin A of device 0000:00:13.2. Please try using pci=biosirq.
[   23.683476] ehci_hcd 0000:00:13.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.2 setup!
[   23.683481] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[   23.685732] eth0: RealTek RTL8139 at 0xdc81c000, 00:13:d4:ea:6f:27, IRQ 10
[   23.685736] eth0:  Identified 8139 chip type 'RTL-8101'
[   23.687540] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   23.687647] PCI: No IRQ known for interrupt pin A of device 0000:02:05.0. Please try using pci=biosirq.
[   23.738365] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   23.738385] ATIIXP: chipset revision 0
[   23.738387] ATIIXP: not 100% native mode: will probe irqs later
[   23.738396]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:pio
[   23.738410]     ide1: BM-DMA at 0xf908-0xf90f, BIOS settings: hdc:pio, hdd:pio
[   23.738420] Probing IDE interface ide0...
[   23.751987] IRQ handler type mismatch for IRQ 0
[   23.751991] current handler: timer
[   23.751997]  [<c01540fe>] setup_irq+0x12e/0x1e0
[   23.752007]  [<dc8e73b0>] ohci_irq_handler+0x0/0x990 [ohci1394]
[   23.752014]  [<c0154253>] request_irq+0xa3/0xc0
[   23.752020]  [<dc8e707d>] ohci1394_pci_probe+0x3cd/0x700 [ohci1394]
[   23.752027]  [<c01fb953>] pci_match_device+0x13/0xc0
[   23.752032]  [<dc8e6cb0>] ohci1394_pci_probe+0x0/0x700 [ohci1394]
[   23.752038]  [<c01fba76>] pci_device_probe+0x56/0x80
[   23.752043]  [<c0257a66>] really_probe+0x66/0x190
[   23.752048]  [<c0257bd9>] driver_probe_device+0x49/0xc0
[   23.752054]  [<c0257dae>] __driver_attach+0x9e/0xa0
[   23.752059]  [<c0256f3b>] bus_for_each_dev+0x3b/0x60
[   23.752065]  [<c0257904>] driver_attach+0x24/0x30
[   23.752068]  [<c0257d10>] __driver_attach+0x0/0xa0
[   23.752072]  [<c02572cb>] bus_add_driver+0x7b/0x1a0
[   23.752078]  [<c01fbc44>] __pci_register_driver+0x74/0xc0
[   23.752083]  [<c014421d>] sys_init_module+0x15d/0x1ba0
[   23.752097]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   23.752103]  [<c0103280>] syscall_call+0x7/0xb
[   23.752110]  =======================
[   23.752113] ohci1394: Failed to allocate shared interrupt 0
[   23.752142] ohci1394: probe of 0000:02:05.0 failed with error -12
[   24.029311] hda: WDC WD1600BB-22GUC0, ATA DISK drive
[   24.705247] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.705443] Probing IDE interface ide1...
[   25.443320] hdc: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[   26.118137] ide1 at 0x170-0x177,0x376 on irq 15
[   26.124060] hda: max request size: 512KiB
[   26.140108] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[   26.141824] hda: cache flushes supported
[   26.141864]  hda: hda1 hda2 hda3 hda4 < hda5 >
[   26.182564] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   26.182572] Uniform CD-ROM driver Revision: 3.20
[   26.523250] Attempting manual resume
[   26.523254] swsusp: Resume From Partition 3:5
[   26.523256] PM: Checking swsusp image.
[   26.541661] PM: Resume from disk failed.
[   26.572798] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.572802] EXT3-fs: write access will be enabled during recovery.
[   27.812291] kjournald starting.  Commit interval 5 seconds
[   27.812306] EXT3-fs: recovery complete.
[   27.812648] EXT3-fs: mounted filesystem with ordered data mode.
[   35.158786] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   36.359724] NET: Registered protocol family 17
[   36.753053] Linux agpgart interface v0.102 (c) Dave Jones
[   36.812942] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.814722] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.001961] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   37.237657] input: PC Speaker as /class/input/input2
[   37.276153] parport: PnPBIOS parport detected.
[   37.276198] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   37.379929] parport0: Printer, Hewlett-Packard HP LaserJet 6MP
[   37.872940] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   38.064136] fuse init (API version 7.8)
[   38.091215] lp0: using parport0 (interrupt-driven).
[   38.139854] Adding 1317288k swap on /dev/disk/by-uuid/17da34ed-0fed-429c-916b-728c5076472a.  Priority:-1 extents:1 across:1317288k
[   38.251240] EXT3 FS on hda3, internal journal
[   38.373456] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   38.721202] NET: Registered protocol family 10
[   38.721301] lo: Disabled Privacy Extensions
[   43.843935] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   43.843974] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   43.844050] powernow_k8: Unknown symbol acpi_processor_register_performance
[   43.872268] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   43.872306] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   43.872395] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   43.872441] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   47.961137] ppdev: user-space parallel port driver
[   48.772590] apm: BIOS not found.
[   48.904527] Bluetooth: Core ver 2.11
[   48.904581] NET: Registered protocol family 31
[   48.904583] Bluetooth: HCI device and connection manager initialized
[   48.904587] Bluetooth: HCI socket layer initialized
[   48.934105] Bluetooth: L2CAP ver 2.8
[   48.934110] Bluetooth: L2CAP socket layer initialized
[   48.940430] Bluetooth: RFCOMM socket layer initialized
[   48.940444] Bluetooth: RFCOMM TTY layer initialized
[   48.940445] Bluetooth: RFCOMM ver 1.8
[   64.695635] eth0: no IPv6 routers present
paul@paul-home:~$ 
paul@paul-home:~$ 

paul@paul-home:~$ 
paul@paul-home:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
ipv6                  268704  8 
nls_utf8                3072  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  3 
snd_atiixp             20620  1 
snd_ac97_codec         98336  1 snd_atiixp
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
psmouse                38920  0 
snd                    54020  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_atiixp,snd_pcm
k8temp                  6656  0 
i2c_piix4               9740  0 
serio_raw               7940  0 
ati_agp                10124  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_core               22784  1 i2c_piix4
agpgart                35400  1 ati_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  1 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
8139cp                 25088  0 
ata_generic             9092  0 
atiixp                  7440  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
8139too                27648  0 
mii                     6528  2 8139cp,8139too
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
sata_sil               12808  0 
libata                125720  2 ata_generic,sata_sil
scsi_mod              142348  2 sbp2,libata
generic                 5124  0 [permanent]
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
paul@paul-home:~$

---

