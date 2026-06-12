---
title: "After Feisty upgrade my sound card won't work"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by spgillooly on 2007-04-26
I have tried it all! Recompiled ALSA, reloaded modules, you name it. I have the Cirrus Logic CS4610 which uses snd-cs46xx module.

I was running fine on Edgy, but installed Feisty over the top of it (partly because I couldn't figure out how to do an upgrade, since the upgrade utility stopped showing Feisty after I applied the other patches that were recommended).

After installing Feisty everything worked (the wireless works better now that I installed NDISWRAPPER) except the sound. Still can't get that to do anything.

Any suggestions?

Thanks!

PS - here's the dump from the system:

=================

gillooly@Columbia:~$ tail -2 /proc/asound/oss/sndstat

Mixers: NOT ENABLED IN CONFIG

gillooly@Columbia:~$ amixer
amixer: Mixer attach default error: No such device

gillooly@Columbia:~$ lspci -nv
00:00.0 0600: 8086:7190 (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 0604: 8086:7191 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f5000000-f5ffffff
        Prefetchable memory behind bridge: fc000000-fcffffff

00:07.0 0601: 8086:7110 (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 0101: 8086:7111 (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 10a0 [size=16]

00:07.2 0c03: 8086:7112 (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1080 [size=32]

00:07.3 0680: 8086:7113 (rev 02)
        Flags: medium devsel, IRQ 9

00:0b.0 0401: 1013:6001 (rev 01)
        Subsystem: 8086:8080
        Flags: medium devsel, IRQ 9
        Memory at f4002000 (32-bit, non-prefetchable) [size=4K]
        Memory at f4100000 (32-bit, non-prefetchable) [size=1M]

00:0d.0 0200: 10b7:7646 (rev 30)
        Subsystem: 10b7:7646
        Flags: bus master, medium devsel, latency 80, IRQ 11
        I/O ports at 1000 [size=128]
        Memory at f4004000 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0e.0 0400: 11de:6120 (rev 03)
        Subsystem: 1328:f001
        Flags: bus master, fast devsel, latency 64, IRQ 9
        Memory at f4003000 (32-bit, non-prefetchable) [size=4K]

00:0f.0 0280: 14e4:4320 (rev 03)
        Subsystem: 1737:0014
        Flags: bus master, fast devsel, latency 64, IRQ 9
        Memory at f4000000 (32-bit, non-prefetchable) [size=8K]

01:00.0 0300: 10de:0020 (rev 04) (prog-if 00 [VGA])
        Subsystem: 10b4:2749
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at fc000000 (32-bit, prefetchable) [size=16M]
        Capabilities: <access denied>

gillooly@Columbia:~$ asoundconf list
Names of available sound cards:

gillooly@Columbia:~$ gillooly@Columbia:~$ asoundconf list
bash: gillooly@Columbia:~$: command not found
gillooly@Columbia:~$ Names of available sound cards:
bash: Names: command not found

gillooly@Columbia:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e7000 size: 0000000000019000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000003ffdc00 end: 00000000040fdc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000040fdc00 size: 0000000000001c00 end: 00000000040ff800 type: 3
[    0.000000] copy_e820_map() start: 00000000040ff800 size: 0000000000000400 end: 00000000040ffc00 type: 4
[    0.000000] copy_e820_map() start: 00000000040ffc00 size: 0000000013f00400 end: 0000000018000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fffe7000 size: 0000000000019000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000040fdc00 (usable)
[    0.000000]  BIOS-e820: 00000000040fdc00 - 00000000040ff800 (ACPI data)
[    0.000000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000040ffc00 - 0000000018000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 384MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98304) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98304
[    0.000000]   HighMem     98304 ->    98304
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98304
[    0.000000] On node 0 totalpages: 98304
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 736 pages used for memmap
[    0.000000]   Normal zone: 93472 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fdd77
[    0.000000] ACPI: FADT (v001 DELL   KHAN     0x19990921 PTL  0x000f4240) @ 0x040ff78c
[    0.000000] ACPI: DSDT (v001  Dell    Khan   0x00000000 MSFT 0x01000004) @ 0x00000000
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7fe7000)
[    0.000000] Detected 348.506 MHz processor.
[   60.834426] Built 1 zonelists.  Total pages: 97536
[   60.834444] Kernel command line: root=UUID=6eb01823-02de-4f66-98bb-90848f522975 ro quiet splash
[   60.835537] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   60.835581] mapped APIC to ffffd000 (0130b000)
[   60.835599] Enabling fast FPU save and restore... done.
[   60.835646] Initializing CPU#0
[   60.835806] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   60.837514] Console: colour VGA+ 80x25
[   60.839060] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   60.840604] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   60.913355] Memory: 378432k/393216k available (1992k kernel code, 14180k reserved, 893k data, 328k init, 0k highmem)
[   60.913415] virtual kernel memory layout:
[   60.913423]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   60.913431]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   60.913440]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   60.913448]     lowmem  : 0xc0000000 - 0xd8000000   ( 384 MB)
[   60.913456]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   60.913464]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   60.913472]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   60.913492] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   60.991797] Calibrating delay using timer specific routine.. 697.98 BogoMIPS (lpj=1395962)
[   60.992027] Security Framework v1.0.0 initialized
[   60.992063] SELinux:  Disabled at boot.
[   60.992159] Mount-cache hash table entries: 512
[   60.992831] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   60.992888] CPU: L1 I cache: 16K, L1 D cache: 16K
[   60.992904] CPU: L2 cache: 512K
[   60.992918] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   60.992976] Compat vDSO mapped to ffffe000.
[   60.993008] Remapping vsyscall page to ffffe000
[   60.993052] Checking 'hlt' instruction... OK.
[   61.007913] SMP alternatives: switching to UP code
[   61.008680] Freeing SMP alternatives: 11k freed
[   61.009582] Early unpacking initramfs... done
[   62.828744] CPU0: Intel Pentium II (Deschutes) stepping 01
[   62.828774] SMP motherboard not detected.
[   62.828787] Local APIC not detected. Using dummy APIC emulation.
[   62.829021] Brought up 1 CPUs
[   62.830309] Booting paravirtualized kernel on bare hardware
[   62.830576] Time: 22:04:12  Date: 03/26/107
[   62.830729] NET: Registered protocol family 16
[   62.831199] EISA bus registered
[   62.832063] PCI: PCI BIOS revision 2.10 entry at 0xfd9a3, last bus=1
[   62.832079] PCI: Using configuration type 1
[   62.832090] Setting up standard PCI resources
[   62.840186] ACPI: Interpreter disabled.
[   62.840209] Linux Plug and Play Support v0.97 (c) Adam Belay
[   62.840253] pnp: PnP ACPI: disabled
[   62.840271] PnPBIOS: Scanning system for PnP BIOS support...
[   62.840338] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   62.840357] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9f5d, dseg 0x400
[   62.849858] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   62.850147] PCI: Probing PCI hardware
[   62.850188] PCI: Probing PCI hardware (bus 00)
[   62.850813] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   62.850824] * this clock source is slow. Consider trying other clock sources
[   62.850906] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   62.850923] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   62.851572] Boot video device is 0000:01:00.0
[   62.854778] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   62.857535] NET: Registered protocol family 8
[   62.857550] NET: Registered protocol family 20
[   62.857853] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   62.857920] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   62.857938] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   62.857955] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   62.860027] PCI: Failed to allocate mem resource #6:10000@fd000000 for 0000:01:00.0
[   62.860104] PCI: Bridge: 0000:00:01.0
[   62.860113]   IO window: disabled.
[   62.860132]   MEM window: f5000000-f5ffffff
[   62.860148]   PREFETCH window: fc000000-fcffffff
[   62.860287] NET: Registered protocol family 2
[   62.896004] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   62.896451] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   62.897087] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   62.897421] TCP: Hash tables configured (established 16384 bind 8192)
[   62.897436] TCP reno registered
[   62.908232] checking if image is initramfs... it is
[   66.385626] Freeing initrd memory: 7011k freed
[   66.387516] audit: initializing netlink socket (disabled)
[   66.387573] audit(1177625055.740:1): initialized
[   66.388257] VFS: Disk quotas dquot_6.5.1
[   66.388354] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   66.388623] io scheduler noop registered
[   66.388640] io scheduler anticipatory registered
[   66.388653] io scheduler deadline registered
[   66.388721] io scheduler cfq registered (default)
[   66.388755] Limiting direct PCI/PCI transfers.
[   66.389703] isapnp: Scanning for PnP cards...
[   66.556822] isapnp: Card 'CS4236B'
[   66.556836] isapnp: Card 'U.S. Robotics 56K Voice INT'
[   66.556849] isapnp: 2 Plug & Play cards detected total
[   66.746033] Real Time Clock Driver v1.12ac
[   66.746494] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   66.746883] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   66.750465] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   66.754124] pnp: Device 01:02.00 activated.
[   66.754597] 01:02.00: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   66.755843] mice: PS/2 mouse device common for all mice
[   66.759870] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   66.760769] input: Macintosh mouse button emulation as /class/input/input0
[   66.761013] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   66.761036] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   66.761920] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   66.761938] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   67.015620] serio: i8042 KBD port at 0x60,0x64 irq 1
[   67.016323] EISA: Probing bus 0 at eisa.0
[   67.016356] Cannot allocate resource for EISA slot 1
[   67.016412] Cannot allocate resource for EISA slot 7
[   67.016426] Cannot allocate resource for EISA slot 8
[   67.016437] EISA: Detected 0 cards.
[   67.016842] TCP cubic registered
[   67.016883] NET: Registered protocol family 1
[   67.016980] Using IPI No-Shortcut mode
[   67.017117]   Magic number: 3:788:98
[   67.019132] Freeing unused kernel memory: 328k freed
[   67.019259] Time: tsc clocksource has been installed.
[   67.034000] input: AT Translated Set 2 keyboard as /class/input/input1
[   69.221918] Capability LSM initialized
[   69.484468] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   71.937250] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   71.937305] PIIX4: chipset revision 1
[   71.937317] PIIX4: not 100% native mode: will probe irqs later
[   71.937347]     ide0: BM-DMA at 0x10a0-0x10a7, BIOS settings: hda:pio, hdb:DMA
[   71.937390]     ide1: BM-DMA at 0x10a8-0x10af, BIOS settings: hdc:DMA, hdd:pio
[   71.937431] Probing IDE interface ide0...
[   72.028553] usbcore: registered new interface driver usbfs
[   72.028674] usbcore: registered new interface driver hub
[   72.028825] usbcore: registered new device driver usb
[   72.038265] USB Universal Host Controller Interface driver v3.0
[   72.522942] hda: Maxtor 91360D8, ATA DISK drive
[   72.802937] hdb: WDC WD800BB-75CAA0, ATA DISK drive
[   72.860006] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   72.860312] Probing IDE interface ide1...
[   73.073774] Floppy drive(s): fd0 is 1.44M
[   73.244396] FDC 0 is a post-1991 82077
[   73.258952] hdc: Hewlett-Packard CD-Writer Plus 9500, ATAPI CD/DVD-ROM drive
[   74.042886] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[   74.099656] ide1 at 0x170-0x177,0x376 on irq 15
[   74.111224] PCI: setting IRQ 9 as level-triggered
[   74.111246] PCI: Found IRQ 9 for device 0000:00:07.2
[   74.111313] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   74.112601] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   74.112676] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001080
[   74.115353] usb usb1: configuration #1 chosen from 1 choice
[   74.116297] hub 1-0:1.0: USB hub found
[   74.116355] hub 1-0:1.0: 2 ports detected
[   74.176551] SCSI subsystem initialized
[   74.247806] libata version 2.20 loaded.
[   74.267433] PCI: setting IRQ 11 as level-triggered
[   74.267453] PCI: Found IRQ 11 for device 0000:00:0d.0
[   74.267495] PCI: Sharing IRQ 11 with 0000:01:00.0
[   74.267519] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   74.267546] 0000:00:0d.0: 3Com PCI 3cSOHO100-TX Hurricane at d883e000.
[   74.344778] hda: max request size: 128KiB
[   74.428612] hda: 26563824 sectors (13600 MB) w/256KiB Cache, CHS=26353/16/63, UDMA(33)
[   74.428648] hda: cache flushes not supported
[   74.428811]  hda:ide-floppy driver 0.99.newide
[   74.457395]  hda1 hda2 < hda5 >
[   74.481105] hdb: max request size: 128KiB
[   74.510644] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   74.531762] hdb: Host Protected Area detected.
[   74.531773]  current capacity is 156250000 sectors (80000 MB)
[   74.531782]  native  capacity is 156301488 sectors (80026 MB)
[   74.545265] hdb: Host Protected Area disabled.
[   74.545293] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   74.545322] hdb: cache flushes not supported
[   74.545473]  hdb: hdb1
[   74.550012] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[   74.550050] Uniform CD-ROM driver Revision: 3.20
[   74.707418] hdd: No disk in drive
[   74.757682] hdd: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[   75.510583] uhci_hcd 0000:00:07.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   75.544537] Attempting manual resume
[   75.544555] swsusp: Resume From Partition 3:5
[   75.544566] PM: Checking swsusp image.
[   75.573562] PM: Resume from disk failed.
[   75.630556] usb 1-1: device descriptor read/64, error -71
[   75.709876] kjournald starting.  Commit interval 5 seconds
[   75.709929] EXT3-fs: mounted filesystem with ordered data mode.
[   80.854064] usb 1-1: device descriptor read/64, error -71
[   81.070047] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   82.189930] usb 1-1: device descriptor read/64, error -71
[   87.413463] usb 1-1: device descriptor read/64, error -71
[   87.629443] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   93.041012] usb 1-1: device not accepting address 4, error -71
[   93.152986] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   98.560486] usb 1-1: device not accepting address 5, error -71
[   98.800515] usb 1-2: new full speed USB device using uhci_hcd and address 6
[   98.954440] usb 1-2: configuration #1 chosen from 1 choice
[   98.956285] hub 1-2:1.0: USB hub found
[   98.959072] hub 1-2:1.0: 4 ports detected
[   99.228412] eth0:  setting full-duplex.
[   99.273993] usb 1-2.2: new low speed USB device using uhci_hcd and address 7
[   99.391297] usb 1-2.2: configuration #1 chosen from 1 choice
[   99.449154] hdd: No disk in drive
[  101.276981] NET: Registered protocol family 17
[  105.438989] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  105.554512] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  105.675322] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  107.387230] Linux agpgart interface v0.102 (c) Dave Jones
[  107.409128] agpgart: Detected an Intel 440BX Chipset.
[  107.416890] agpgart: AGP aperture is 64M @ 0xf8000000
[  107.470598] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[  107.629259] HiSax: Linux Driver for passive ISDN cards
[  107.629277] HiSax: Version 3.5 (module)
[  107.629290] HiSax: Layer1 Revision 2.46.2.5
[  107.629302] HiSax: Layer2 Revision 2.30.2.4
[  107.629313] HiSax: TeiMgr Revision 2.20.2.3
[  107.629323] HiSax: Layer3 Revision 2.22.2.3
[  107.629334] HiSax: LinkLayer Revision 2.59.2.4
[  111.246443] input: PC Speaker as /class/input/input2
[  113.039281] pnp: Device 01:01.00 activated.
[  113.042045] pnp: Device 01:01.00 disabled.
[  113.042071] cs4232-pnpbios: probe of 01:01.00 failed with error -2
[  113.042356] CS4232 soundcard not found or device busy
[  113.217020] pnp: Device 01:01.01 activated.
[  113.234169] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 685kHz
[  113.907514] parport: PnPBIOS parport detected.
[  113.907585] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  114.098948] PCI: Found IRQ 9 for device 0000:00:0b.0
[  114.098994] PCI: Sharing IRQ 9 with 0000:00:0f.0
[  114.623661] usbcore: registered new interface driver hiddev
[  114.791018] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  114.800608] input: HID 413c:3010 as /class/input/input3
[  114.801208] input: USB HID v1.00 Mouse [HID 413c:3010] on usb-0000:00:07.2-2.2
[  114.801287] usbcore: registered new interface driver usbhid
[  114.801305] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  115.910908] usb 1-1: device descriptor read/64, error -71
[  116.902829] create - never read codec ready from AC'97
[  116.902852] it is not probably bug, try to use CS4236 driver
[  116.903033] Sound Fusion CS46xx: probe of 0000:00:0b.0 failed with error -5
[  117.309779] fuse init (API version 7.8)
[  117.434857] lp0: using parport0 (interrupt-driven).
[  117.629218] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  117.806361] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[  117.807436] PCI: Found IRQ 9 for device 0000:00:0f.0
[  117.807474] PCI: Sharing IRQ 9 with 0000:00:0b.0
[  117.818450] ndiswrapper: using IRQ 9
[  118.824342] eth1: ethernet device 00:0c:41:65:c2:f4 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
[  118.824471] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  121.134446] usb 1-1: device descriptor read/64, error -71
[  121.350425] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  122.470320] usb 1-1: device descriptor read/64, error -71
[  127.693856] usb 1-1: device descriptor read/64, error -71
[  127.909855] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  133.317336] usb 1-1: device not accepting address 10, error -71
[  133.429345] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  138.836836] usb 1-1: device not accepting address 11, error -71
[  138.842098] usbcore: registered new interface driver ndiswrapper
[  138.983202] Adding 602396k swap on /dev/disk/by-uuid/2132e96b-ac41-80ac-ca06-f9d73f67b0a4.  Priority:-1 extents:1 across:602396k
[  139.287092] EXT3 FS on hda1, internal journal
[  139.826223] NET: Registered protocol family 10
[  139.826725] lo: Disabled Privacy Extensions
[  148.498427] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  148.498946] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  148.500464] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  148.501165] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  150.611768] eth0: no IPv6 routers present
[  160.857367] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  162.565251] ppdev: user-space parallel port driver
[  167.015496] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  168.773887] Bluetooth: Core ver 2.11
[  168.774114] NET: Registered protocol family 31
[  168.774157] Bluetooth: HCI device and connection manager initialized
[  168.774174] Bluetooth: HCI socket layer initialized
[  168.939948] Bluetooth: L2CAP ver 2.8
[  168.939969] Bluetooth: L2CAP socket layer initialized
[  168.975055] Bluetooth: RFCOMM socket layer initialized
[  168.975111] Bluetooth: RFCOMM TTY layer initialized
[  168.975124] Bluetooth: RFCOMM ver 1.8
[  178.421270] eth0: no IPv6 routers present

gillooly@Columbia:~$ cat /proc/interrupts
           CPU0       
  0:    1075312    XT-PIC-XT        timer
  1:        619    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  6:          5    XT-PIC-XT        floppy
  7:          0    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:      81178    XT-PIC-XT        uhci_hcd:usb1, eth1
 11:       2267    XT-PIC-XT        eth0
 14:      11185    XT-PIC-XT        ide0
 15:      37685    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

---

### Post by cmat on 2007-04-27
I'm having the same problem and there seems to be no fix for it yet. I tryed every walk-around and nothing worked. Maybe the older ALSA from edgy can be used as a substitute. :confused:

---

### Post by kingjere on 2007-05-09
I'm working on the same problem with my IBM A21m witch uses the same sound driver as you spgillooly. At this point after following

[This workaround]("http://ubuntuforums.org/showthread.php?t=425170&highlight=no+sound+restore")

AND adding "snd_cs46xx" to the file /etc/default/acpi-support like this

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="snd_cs46xx"

I have sound after a suspend but kmix is absent from my systray (KDE). As far as I'm concerned that is minor and who knows, if you use Gnome you might not have that problem.

---

### Post by scholzilla on 2007-06-30
See my [bug post #121105 ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121105")at launchpad. I believe the problem is with the kernel upgrades and have a "fix" posted there? 

What I'd like to know is when I can install these upgrades without killing my sound? Does anyone know what security risk is posed by not installing them?

---

