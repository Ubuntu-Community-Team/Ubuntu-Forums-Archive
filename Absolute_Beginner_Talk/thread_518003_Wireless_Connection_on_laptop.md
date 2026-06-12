---
title: "Wireless Connection on laptop"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-05
I am running Ubuntu 7.04 off of the livecd on my Compaq Presario Laptop, and was attempting to get the wireless network working on it, to affirm that it will work, but it will can not find the wireless network with roaming, nor when I set the settings up for it.

The wireless works perfect on Windows, so it is a software issue with Ubuntu.
Any help or suggestions to try to get it to work, would be much appreciated.

Sincerely,
Dr Small

---

### Post by fimbulvetr on 2007-08-05
Paste the output of

```
dmesg
```
and
```
sudo iwlist scan
```

Both commands being ran from the terminal.

---

### Post by Dr Small on 2007-08-05
Output of dmesg:
> 
ubuntu@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 000000000002e000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000017df0000 end: 0000000017ef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000017ef0000 size: 000000000000f000 end: 0000000017eff000 type: 3
[    0.000000] copy_e820_map() start: 0000000017eff000 size: 0000000000001000 end: 0000000017f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000017f00000 size: 0000000008100000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8330
[    0.000000] Entering add_active_range(0, 0, 98032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98032
[    0.000000]   HighMem     98032 ->    98032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98032
[    0.000000] On node 0 totalpages: 98032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93203 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000f8280
[    0.000000] ACPI: RSDT (v001 HP     3096     0x20040608  LTP 0x00000000) @ 0x17ef8c5b
[    0.000000] ACPI: FADT (v001 HP     3096     0x20040608 PTL  0x0000005f) @ 0x17efee41
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x20040608  LTP 0x00000001) @ 0x17efeeb5
[    0.000000] ACPI: MADT (v001 PTLTD    3096   0x20040608  LTP 0x00000000) @ 0x17efef6a
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x20040608  LTP 0x00000000) @ 0x17efefc4
[    0.000000] ACPI: DSDT (v001 HP     3091     0x20040608 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 1600.246 MHz processor.
[   28.469320] Built 1 zonelists.  Total pages: 97267
[   28.469327] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[   28.469518] mapped APIC to ffffd000 (fee00000)
[   28.469521] mapped IOAPIC to ffffc000 (fec00000)
[   28.469525] Enabling fast FPU save and restore... done.
[   28.469528] Enabling unmasked SIMD FPU exception support... done.
[   28.469539] Initializing CPU#0
[   28.469620] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   28.470631] Console: colour VGA+ 80x25
[   28.470904] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.471219] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.480659] Memory: 377408k/392128k available (1992k kernel code, 14128k reserved, 893k data, 328k init, 0k highmem)
[   28.480671] virtual kernel memory layout:
[   28.480673]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.480675]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.480677]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   28.480678]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[   28.480680]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.480681]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.480683]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.480686] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.557499] Calibrating delay using timer specific routine.. 3203.92 BogoMIPS (lpj=6407844)
[   28.557546] Security Framework v1.0.0 initialized
[   28.557552] SELinux:  Disabled at boot.
[   28.557571] Mount-cache hash table entries: 512
[   28.557720] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000 00000001
[   28.557730] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.557733] CPU: L2 Cache: 256K (64 bytes/line)
[   28.557737] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000000 00000000 00000001
[   28.557747] Compat vDSO mapped to ffffe000.
[   28.557753] Remapping vsyscall page to ffffe000
[   28.557763] Checking 'hlt' instruction... OK.
[   28.573618] SMP alternatives: switching to UP code
[   28.573844] Freeing SMP alternatives: 11k freed
[   28.574113] Early unpacking initramfs... done
[   28.933752] ACPI: Core revision 20060707
[   28.934071] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.939169] CPU0: AMD Mobile AMD Sempron(tm) Processor 2800+ stepping 00
[   28.939194] Total of 1 processors activated (3203.92 BogoMIPS).
[   28.939375] ENABLING IO-APIC IRQs
[   28.939584] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.979259] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   28.979306] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   28.979310] ...trying to set up timer as Virtual Wire IRQ... works.
[   29.124720] Brought up 1 CPUs
[   29.124971] Booting paravirtualized kernel on bare hardware
[   29.125069] Time:  8:40:35  Date: 07/05/107
[   29.125112] NET: Registered protocol family 16
[   29.125215] EISA bus registered
[   29.125219] ACPI: bus type pci registered
[   29.125389] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=6
[   29.125392] PCI: Using configuration type 1
[   29.125395] Setting up standard PCI resources
[   29.128240] ACPI: Interpreter enabled
[   29.128248] ACPI: Using IOAPIC for interrupt routing
[   29.128831] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.128837] PCI: Probing PCI hardware (bus 00)
[   29.130750] Boot video device is 0000:01:05.0
[   29.131080] PCI: Transparent bridge - 0000:00:14.4
[   29.131157] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#06) (try 'pci=assign-busses')
[   29.131160] Please report the result to linux-kernel to fix this permanently
[   29.131184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.133939] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   29.134187] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   29.134431] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   29.134677] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   29.134919] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   29.135160] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   29.135403] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   29.135654] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   29.138177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   29.138556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   29.138975] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.138986] pnp: PnP ACPI init
[   29.141971] pnp: PnP ACPI: found 10 devices
[   29.141977] PnPBIOS: Disabled by ACPI PNP
[   29.142035] PCI: Using ACPI for IRQ routing
[   29.142039] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.159313] NET: Registered protocol family 8
[   29.159316] NET: Registered protocol family 20
[   29.159597] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   29.159600] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   29.159604] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   29.159607] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   29.159874] PCI: Bridge: 0000:00:01.0
[   29.159876]   IO window: 9000-9fff
[   29.159881]   MEM window: c0100000-c01fffff
[   29.159884]   PREFETCH window: c8000000-cfffffff
[   29.159890] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   29.159892]   IO window: 0000a400-0000a4ff
[   29.159899]   IO window: 0000a800-0000a8ff
[   29.159905]   PREFETCH window: 30000000-33ffffff
[   29.159912]   MEM window: 34000000-37ffffff
[   29.159917] PCI: Bridge: 0000:00:14.4
[   29.159921]   IO window: a000-afff
[   29.159927]   MEM window: c0200000-c02fffff
[   29.159933]   PREFETCH window: 30000000-33ffffff
[   29.159980] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   29.160031] NET: Registered protocol family 2
[   29.196667] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   29.196781] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   29.196936] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   29.197024] TCP: Hash tables configured (established 16384 bind 8192)
[   29.197027] TCP reno registered
[   29.208700] checking if image is initramfs... it is
[   29.921856] Freeing initrd memory: 6966k freed
[   29.922376] audit: initializing netlink socket (disabled)
[   29.922395] audit(1186303235.496:1): initialized
[   29.922547] VFS: Disk quotas dquot_6.5.1
[   29.922573] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.922635] io scheduler noop registered
[   29.922640] io scheduler anticipatory registered
[   29.922642] io scheduler deadline registered
[   29.922657] io scheduler cfq registered (default)
[   30.602800] isapnp: Scanning for PnP cards...
[   30.956953] isapnp: No Plug & Play device found
[   30.984951] Real Time Clock Driver v1.12ac
[   30.985003] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.985773] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   30.985785] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   30.985855] mice: PS/2 mouse device common for all mice
[   30.986456] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.986713] input: Macintosh mouse button emulation as /class/input/input0
[   30.986747] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.986754] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.987053] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   30.990177] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.990183] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.990333] EISA: Probing bus 0 at eisa.0
[   30.990345] Cannot allocate resource for EISA slot 1
[   30.990376] Cannot allocate resource for EISA slot 8
[   30.990378] EISA: Detected 0 cards.
[   31.020446] TCP cubic registered
[   31.020458] NET: Registered protocol family 1
[   31.020487] Using IPI No-Shortcut mode
[   31.020561] ACPI: (supports S0 S3 S4 S5)
[   31.020609]   Magic number: 3:366:674
[   31.021119] Freeing unused kernel memory: 328k freed
[   31.021875] Time: tsc clocksource has been installed.
[   31.036161] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.263796] Capability LSM initialized
[   32.306506] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   32.306512] ACPI: Processor [CPU0] (supports 8 throttling states)
[   32.309046] ACPI: Thermal Zone [THRM] (57 C)
[   32.834071] usbcore: registered new interface driver usbfs
[   32.834102] usbcore: registered new interface driver hub
[   32.834125] usbcore: registered new device driver usb
[   32.834936] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.834982] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   32.834998] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   32.835146] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   32.835173] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0000000
[   32.927438] usb usb1: configuration #1 chosen from 1 choice
[   32.927473] hub 1-0:1.0: USB hub found
[   32.927487] hub 1-0:1.0: 4 ports detected
[   33.031109] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   33.031129] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   33.031152] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   33.031172] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0001000
[   33.039910] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   33.091656] usb usb2: configuration #1 chosen from 1 choice
[   33.091685] hub 2-0:1.0: USB hub found
[   33.091700] hub 2-0:1.0: 4 ports detected
[    3.900000] Time: acpi_pm clocksource has been installed.
[    3.948000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    3.948000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.948000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.948000] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0002000
[    3.948000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.948000] usb usb3: configuration #1 chosen from 1 choice
[    3.948000] hub 3-0:1.0: USB hub found
[    3.948000] hub 3-0:1.0: 8 ports detected
[    4.052000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.052000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    4.052000] ATIIXP: chipset revision 0
[    4.052000] ATIIXP: not 100% native mode: will probe irqs later
[    4.052000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[    4.052000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[    4.052000] Probing IDE interface ide0...
[    4.340000] hda: ST94019A, ATA DISK drive
[    4.596000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    4.804000] usb 2-1: configuration #1 chosen from 1 choice
[    4.816000] usbcore: registered new interface driver hiddev
[    4.824000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    4.824000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.1-1
[    4.824000] usbcore: registered new interface driver usbhid
[    4.824000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.016000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.492000] Probing IDE interface ide1...
[    6.232000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4243N, ATAPI CD/DVD-ROM drive
[    6.568000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.576000] SCSI subsystem initialized
[    6.584000] libata version 2.20 loaded.
[    6.588000] 8139cp 0000:05:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.588000] 8139cp 0000:05:00.0: Try the "8139too" driver instead.
[    6.588000] 8139too Fast Ethernet driver 0.9.28
[    6.588000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    6.588000] eth0: RealTek RTL8139 at 0xd885c000, 00:c0:9f:a2:11:23, IRQ 19
[    6.588000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.600000] hda: max request size: 512KiB
[    6.600000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.612000] hda: cache flushes supported
[    6.612000]  hda: hda1
[    6.840000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[    6.840000] Uniform CD-ROM driver Revision: 3.20
[    7.640000] ISO 9660 Extensions: Microsoft Joliet Level 3
[    7.720000] ISO 9660 Extensions: RRIP_1991A
[    7.772000] Registering unionfs 20060916-2203
[    7.772000] unionfs: debugging is not enabled
[    7.788000] loop: loaded (max 8 devices)
[    7.856000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher
[  106.376000] eth0: link down
[  107.816000] Linux agpgart interface v0.102 (c) Dave Jones
[  108.172000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  109.656000] NET: Registered protocol family 17
[  109.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  109.920000] input: PC Speaker as /class/input/input3
[  110.052000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  110.376000] ieee80211_crypt: registered algorithm 'NULL'
[  110.376000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  110.376000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  110.584000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[  110.584000] Yenta: Enabling burst memory read transactions
[  110.584000] Yenta: Using CSCINT to route CSC interrupts to PCI
[  110.584000] Yenta: Routing CardBus interrupts to PCI
[  110.584000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x66
[  110.612000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[  110.644000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  110.768000] bcm43xx driver
[  110.816000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 16
[  110.816000] Socket status: 30000006
[  110.816000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[  110.816000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[  110.816000] cs: IO port probe 0xa000-0xafff: clean.
[  110.816000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[  110.816000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[  110.816000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[  111.104000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[  111.216000] MC'97 0 converters and GPIO not ready (0x1)
[  111.216000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[  111.252000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  111.436000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  111.448000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  111.824000] cs: IO port probe 0x100-0x3af: clean.
[  111.824000] cs: IO port probe 0x3e0-0x4ff: clean.
[  111.824000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[  111.828000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[  111.828000] cs: IO port probe 0xa00-0xaff: clean.
[  112.852000] fuse init (API version 7.8)
[  119.568000] ACPI: AC Adapter [ACAD] (on-line)
[  119.888000] ACPI: Battery Slot [BAT1] (battery present)
[  119.952000] input: Power Button (FF) as /class/input/input5
[  119.956000] ACPI: Power Button (FF) [PWRF]
[  120.000000] input: Power Button (CM) as /class/input/input6
[  120.004000] ACPI: Power Button (CM) [PWRB]
[  120.044000] input: Sleep Button (CM) as /class/input/input7
[  120.052000] ACPI: Sleep Button (CM) [SLPB]
[  120.096000] input: Lid Switch as /class/input/input8
[  120.100000] ACPI: Lid Switch [LID]
[  120.144000] No dock devices found.
[  120.168000] Using specific hotkey driver
[  120.228000] ibm_acpi: ec object not found
[  120.336000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  120.400000] pcc_acpi: loading...
[  120.444000] wmi_add device=d6111400
[  120.444000] calling WQBA
[  120.996000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 2800+ processors (version 2.00.00)
[  120.996000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x8
[  120.996000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x13
[  128.728000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  132.872000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  134.596000] lp: driver loaded but no devices found
[  134.680000] ppdev: user-space parallel port driver
[  148.356000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  150.648000] NET: Registered protocol family 10
[  150.648000] lo: Disabled Privacy Extensions
[  150.648000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  151.424000] apm: BIOS not found.
[  155.700000] Bluetooth: Core ver 2.11
[  155.700000] NET: Registered protocol family 31
[  155.700000] Bluetooth: HCI device and connection manager initialized
[  155.700000] Bluetooth: HCI socket layer initialized
[  156.164000] Bluetooth: L2CAP ver 2.8
[  156.164000] Bluetooth: L2CAP socket layer initialized
[  156.848000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  156.948000] Bluetooth: RFCOMM socket layer initialized
[  156.948000] Bluetooth: RFCOMM TTY layer initialized
[  156.948000] Bluetooth: RFCOMM ver 1.8
[  180.580000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  204.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  227.568000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  250.988000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  342.652000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  343.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  343.368000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  404.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  417.632000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  420.980000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  421.036000] eth0: link down
[  421.036000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  444.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  457.416000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  457.792000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  457.812000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  467.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  484.128000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  493.648000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  514.884000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  514.956000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  514.972000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  550.576000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  735.320000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  735.392000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  735.412000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  762.104000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  769.568000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  880.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  884.256000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  884.312000] eth0: link down
[  884.312000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  907.508000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  907.928000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  910.780000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  910.908000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  975.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  999.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1007.208000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1007.244000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1007.540000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1022.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1022.948000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1023.060000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1033.448000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1033.492000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1033.572000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1034.816000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1034.868000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1034.944000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1101.012000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1124.264000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1140.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2065.700000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2065.700000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2076.244000] eth0: no IPv6 routers present
[ 2115.780000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2122.524000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2124.560000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2124.560000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2143.588000] eth0: no IPv6 routers present
[ 3446.808000] APIC error on CPU0: 00(40)


Output of sudo iwlist scan:
> 
ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device


---

### Post by fimbulvetr on 2007-08-05
You have the bcm43xx, also known as the wireless card from hell!

Just kidding, it's not that bad, but it's not exactly plug and play either.

Follow these guides:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

(Hint, choose a guide at the bottom)

---

### Post by Dr Small on 2007-08-05
Ok. Thanks, I'll try that. I'll post back if I have any problems ;)
Thanks,

Dr Small

---

### Post by Dr Small on 2008-03-01
Ok, so the ole Windows XP finally died on the laptop and so I installed Ubuntu on it. I went through the Howto, finally got the broadcom card to work, so now networking works.

But whether I set it up for DHCP or Static IP, whenever the system is rebooted, Networking doesn't work right off the boot. I have to go in and turn off network, and turn it back on, in order for it to enable.

Is there any way to fix this glitch?

Dr Small

---

