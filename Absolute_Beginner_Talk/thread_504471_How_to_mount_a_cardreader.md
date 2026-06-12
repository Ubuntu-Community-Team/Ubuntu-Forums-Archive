---
title: "How to mount a cardreader"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-19
Hi I have four built in card readers, and i have a SD card where i have got some photos that I would like to put on my PC. The problem is that Ubuntu wont recognize my card readers, none of them shows up, I have got my phone plugged in where I have another mini card in and that works fine in USB.

It seems like the card drives are not even mounted, liek cdrom is mounted even when its empty, the card drives aren't. How can I solve this?

---

### Post by anubhavrocks on 2007-07-19
after you insert the card into the card reader,on the terminal give the ```
dmesg 
``` command,paste the output that you get

---

### Post by mcduck on 2007-07-19
Card reader aren't mounted, cards are. So if you are trying to get empty card reader to show somewhere, you are wasting your time. ;)

---

### Post by Matakoo on 2007-07-19
Insert the card, and open a terminal (it's normal to not have an icon for the cardreader on your desktop. There's nothing there unless there's a card in the reader).

Type df, and see if the card is mounted somewhere and just does not show up on your desktop.

The output for the card should be something like this:

/dev/sdc1     vfat    120M   32K  120M   1% /media/disk

It will be different on your machine, but the vfat part will be there. Just look for that
and a size (120M in the example) that matches the size of your card.

If that doesn't show anything, use the command dmesg

The output for the card should, if the reader is recognized properly, look something like this:

[10429.344328] sd 2:0:0:0: [sdc] 245504 512-byte hardware sectors (126 MB)
[10429.345453] sd 2:0:0:0: [sdc] Write Protect is off
[10429.345458] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[10429.345460] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[10429.346453] sd 2:0:0:0: [sdc] 245504 512-byte hardware sectors (126 MB)
[10429.347574] sd 2:0:0:0: [sdc] Write Protect is off
[10429.347578] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[10429.347580] sd 2:0:0:0: [sdc] Assuming drive cache: write through

Post whatever messages you get and we might find a solution. Unless you're unfortunate and the cardreader doesn't work in Linux. Unlikely (I have yet to come across one that doesn't), but not impossible.

---

### Post by kasperbs on 2007-07-19
Output from dmesg
> rudolf@rudolf-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fef0000 end: 000000002fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fff0000 size: 0000000000003000 end: 000000002fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000002fff3000 size: 000000000000d000 end: 0000000030000000 type: 3
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5890
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f7260
[    0.000000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3000
[    0.000000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3040
[    0.000000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff6980
[    0.000000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:d0000000)
[    0.000000] Detected 2672.855 MHz processor.
[   14.700061] Built 1 zonelists.  Total pages: 195057
[   14.700067] Kernel command line: root=UUID=6a990e16-dd72-4e11-bed9-738f9261da35 ro quiet splash locale=da_DK
[   14.700239] mapped APIC to ffffd000 (fee00000)
[   14.700241] mapped IOAPIC to ffffc000 (fec00000)
[   14.700245] Enabling fast FPU save and restore... done.
[   14.700248] Enabling unmasked SIMD FPU exception support... done.
[   14.700263] Initializing CPU#0
[   14.700359] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.701411] Console: colour VGA+ 80x25
[   14.702248] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.703066] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.719921] Memory: 768312k/786368k available (1992k kernel code, 17424k reserved, 900k data, 328k init, 0k highmem)
[   14.719932] virtual kernel memory layout:
[   14.719933]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.719934]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.719935]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   14.719936]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   14.719937]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   14.719938]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   14.719939]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   14.719942] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.796337] Calibrating delay using timer specific routine.. 5349.72 BogoMIPS (lpj=10699453)
[   14.796383] Security Framework v1.0.0 initialized
[   14.796391] SELinux:  Disabled at boot.
[   14.796409] Mount-cache hash table entries: 512
[   14.796563] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   14.796576] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   14.796579] CPU: L2 cache: 512K
[   14.796581] CPU: Hyper-Threading is disabled
[   14.796584] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
[   14.796595] Compat vDSO mapped to ffffe000.
[   14.796598] Remapping vsyscall page to ffffe000
[   14.796612] Checking 'hlt' instruction... OK.
[   14.812429] SMP alternatives: switching to UP code
[   14.812622] Freeing SMP alternatives: 11k freed
[   14.812833] Early unpacking initramfs... done
[   15.098794] ACPI: Core revision 20060707
[   15.106307] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.110110] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[   15.110154] Total of 1 processors activated (5349.72 BogoMIPS).
[   15.110263] ENABLING IO-APIC IRQs
[   15.110447] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.256250] Brought up 1 CPUs
[   15.256508] Booting paravirtualized kernel on bare hardware
[   15.256592] Time: 16:21:59  Date: 06/19/107
[   15.256626] NET: Registered protocol family 16
[   15.256730] EISA bus registered
[   15.256736] ACPI: bus type pci registered
[   15.296019] PCI: PCI BIOS revision 2.10 entry at 0xfb400, last bus=1
[   15.296021] PCI: Using configuration type 1
[   15.296023] Setting up standard PCI resources
[   15.312709] ACPI: Interpreter enabled
[   15.312713] ACPI: Using IOAPIC for interrupt routing
[   15.313346] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.313352] PCI: Probing PCI hardware (bus 00)
[   15.313419] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   15.313794] Enabling SiS 96x SMBus.
[   15.315019] Boot video device is 0000:01:00.0
[   15.315102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.338938] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   15.339187] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   15.339433] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   15.339679] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   15.339932] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   15.340178] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   15.340443] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *13
[   15.340687] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   15.343114] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.343128] pnp: PnP ACPI init
[   15.346646] pnp: PnP ACPI: found 14 devices
[   15.346652] PnPBIOS: Disabled by ACPI PNP
[   15.346714] PCI: Using ACPI for IRQ routing
[   15.346718] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.360921] NET: Registered protocol family 8
[   15.360923] NET: Registered protocol family 20
[   15.361533] PCI: Bridge: 0000:00:01.0
[   15.361535]   IO window: disabled.
[   15.361544]   MEM window: e0000000-e1ffffff
[   15.361551]   PREFETCH window: d8000000-dfffffff
[   15.361608] NET: Registered protocol family 2
[   15.392259] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.392481] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.393668] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.394481] TCP: Hash tables configured (established 131072 bind 65536)
[   15.394487] TCP reno registered
[   15.404351] checking if image is initramfs... it is
[   15.972212] Freeing initrd memory: 6783k freed
[   15.972703] audit: initializing netlink socket (disabled)
[   15.972721] audit(1184862119.356:1): initialized
[   15.972885] VFS: Disk quotas dquot_6.5.1
[   15.972908] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.972964] io scheduler noop registered
[   15.972967] io scheduler anticipatory registered
[   15.972969] io scheduler deadline registered
[   15.972980] io scheduler cfq registered (default)
[   16.068175] isapnp: Scanning for PnP cards...
[   16.421979] isapnp: No Plug & Play device found
[   16.450307] Real Time Clock Driver v1.12ac
[   16.450365] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.450495] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.451328] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.451668] mice: PS/2 mouse device common for all mice
[   16.452348] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.452615] input: Macintosh mouse button emulation as /class/input/input0
[   16.452660] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.452665] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.452952] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.453269] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.453274] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.453399] EISA: Probing bus 0 at eisa.0
[   16.453408] Cannot allocate resource for EISA slot 1
[   16.453418] Cannot allocate resource for EISA slot 4
[   16.453433] EISA: Detected 0 cards.
[   16.483539] TCP cubic registered
[   16.483549] NET: Registered protocol family 1
[   16.483578] Using IPI No-Shortcut mode
[   16.483680] ACPI: (supports S0 S3 S4 S5)
[   16.483730]   Magic number: 15:951:388
[   16.483863] Time: tsc clocksource has been installed.
[   16.484316] Freeing unused kernel memory: 328k freed
[   16.499713] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.723184] Capability LSM initialized
[   17.759532] ACPI: Fan [FAN] (on)
[   17.764704] ACPI: Thermal Zone [THRM] (44 C)
[   18.299480] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   18.299516] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   18.299530] SIS5513: chipset revision 0
[   18.299532] SIS5513: not 100% native mode: will probe irqs later
[   18.299549] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[   18.299572]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA
[   18.299588]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[   18.299598] Probing IDE interface ide0...
[   18.327559] usbcore: registered new interface driver usbfs
[   18.327585] usbcore: registered new interface driver hub
[   18.327609] usbcore: registered new device driver usb
[   18.328451] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.356622] sis900.c: v1.08.10 Apr. 2 2006
[   18.393554] ieee1394: Initialized config rom entry `ip1394'
[   18.468555] Floppy drive(s): fd0 is 1.44M
[   18.519398] FDC 0 is a post-1991 82077
[   18.603268] hda: ST3120023A, ATA DISK drive
[   19.055104] hdb: JLMS DVD-ROM LTD-165H, ATAPI CD/DVD-ROM drive
[   19.111553] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.116404] Probing IDE interface ide1...
[   19.854832] hdc: TSSTcorpCD-R/RW SH-R522C, ATAPI CD/DVD-ROM drive
[   20.134705] hdd: Maxtor 5T040H4, ATA DISK drive
[   20.190885] ide1 at 0x170-0x177,0x376 on irq 15
[   20.202177] SCSI subsystem initialized
[   20.208265] libata version 2.20 loaded.
[   20.214133] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   20.214153] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   20.214503] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   20.214543] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe2420000
[   20.224493] hda: max request size: 128KiB
[   20.238149] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   20.239255] hda: cache flushes supported
[   20.239306]  hda: hda1 hda2 hda3
[   20.272645] usb usb1: configuration #1 chosen from 1 choice
[   20.272674] hub 1-0:1.0: USB hub found
[   20.272686] hub 1-0:1.0: 2 ports detected
[   20.276014] hdd: max request size: 128KiB
[   20.276457] hdd: 80043264 sectors (40982 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   20.276464] hdd: cache flushes not supported
[   20.276499]  hdd:<6>hdb: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(44)
[   20.276785] Uniform CD-ROM driver Revision: 3.20
[   20.286086]  hdd1
[   20.296394] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   20.378672] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   20.378697] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   20.378721] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   20.378741] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe2421000
[   20.436570] usb usb2: configuration #1 chosen from 1 choice
[   20.436600] hub 2-0:1.0: USB hub found
[   20.436612] hub 2-0:1.0: 2 ports detected
[   20.542564] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
[   20.542588] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   20.542613] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   20.542633] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe2422000
[   20.562845] Attempting manual resume
[   20.562850] swsusp: Resume From Partition 3:2
[   20.562852] PM: Checking swsusp image.
[   20.563174] PM: Resume from disk failed.
[   20.590362] kjournald starting.  Commit interval 5 seconds
[   20.590375] EXT3-fs: mounted filesystem with ordered data mode.
[   20.600518] usb usb3: configuration #1 chosen from 1 choice
[   20.600550] hub 3-0:1.0: USB hub found
[   20.600562] hub 3-0:1.0: 2 ports detected
[   20.706621] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[   20.707708] 0000:00:04.0: Unknown PHY transceiver found at address 0.
[   20.708474] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   20.709239] 0000:00:04.0: Unknown PHY transceiver found at address 2.
[   20.710005] 0000:00:04.0: Unknown PHY transceiver found at address 3.
[   20.710818] 0000:00:04.0: Unknown PHY transceiver found at address 4.
[   20.711601] 0000:00:04.0: Unknown PHY transceiver found at address 5.
[   20.712367] 0000:00:04.0: Unknown PHY transceiver found at address 6.
[   20.713132] 0000:00:04.0: Unknown PHY transceiver found at address 7.
[   20.713898] 0000:00:04.0: Unknown PHY transceiver found at address 8.
[   20.714665] 0000:00:04.0: Unknown PHY transceiver found at address 9.
[   20.715433] 0000:00:04.0: Unknown PHY transceiver found at address 10.
[   20.716198] 0000:00:04.0: Unknown PHY transceiver found at address 11.
[   20.716964] 0000:00:04.0: Unknown PHY transceiver found at address 12.
[   20.717729] 0000:00:04.0: Unknown PHY transceiver found at address 13.
[   20.718496] 0000:00:04.0: Unknown PHY transceiver found at address 14.
[   20.719265] 0000:00:04.0: Unknown PHY transceiver found at address 15.
[   20.720030] 0000:00:04.0: Unknown PHY transceiver found at address 16.
[   20.720795] 0000:00:04.0: Unknown PHY transceiver found at address 17.
[   20.721560] 0000:00:04.0: Unknown PHY transceiver found at address 18.
[   20.722325] 0000:00:04.0: Unknown PHY transceiver found at address 19.
[   20.723100] 0000:00:04.0: Unknown PHY transceiver found at address 20.
[   20.723866] 0000:00:04.0: Unknown PHY transceiver found at address 21.
[   20.724631] 0000:00:04.0: Unknown PHY transceiver found at address 22.
[   20.725396] 0000:00:04.0: Unknown PHY transceiver found at address 23.
[   20.726162] 0000:00:04.0: Unknown PHY transceiver found at address 24.
[   20.726931] 0000:00:04.0: Unknown PHY transceiver found at address 25.
[   20.727697] 0000:00:04.0: Unknown PHY transceiver found at address 26.
[   20.728462] 0000:00:04.0: Unknown PHY transceiver found at address 27.
[   20.729228] 0000:00:04.0: Unknown PHY transceiver found at address 28.
[   20.729993] 0000:00:04.0: Unknown PHY transceiver found at address 29.
[   20.730791] 0000:00:04.0: Unknown PHY transceiver found at address 30.
[   20.731557] 0000:00:04.0: Unknown PHY transceiver found at address 31.
[   20.755504] 0000:00:04.0: Using transceiver found at address 1 as default
[   20.756334] eth0: SiS 900 PCI Fast Ethernet at 0xec00, IRQ 20, 00:10:dc:77:f5:7f.
[   20.756451] ACPI: PCI Interrupt 0000:00:02.3[B] -> GSI 17 (level, low) -> IRQ 21
[   20.808315] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e2426000-e24267ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[   20.818818] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 22
[   20.818835] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   20.818882] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   20.818929] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   20.818939] ehci_hcd 0000:00:03.3: irq 22, io mem 0xe2423000
[   20.818948] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.819038] usb usb4: configuration #1 chosen from 1 choice
[   20.819068] hub 4-0:1.0: USB hub found
[   20.819079] hub 4-0:1.0: 6 ports detected
[   20.874311] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   21.865974] usb 2-1: new full speed USB device using ohci_hcd and address 3
[   22.073737] usb 2-1: configuration #1 chosen from 1 choice
[   22.098004] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc000b5a62]
[   22.389793] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   22.608503] usb 3-1: configuration #1 chosen from 1 choice
[   29.120561] NET: Registered protocol family 17
[   29.892386] eth0: Media Link On 100mbps full-duplex 
[   29.987829] Linux agpgart interface v0.102 (c) Dave Jones
[   29.989669] agpgart: Detected SiS 648 chipset
[   29.997457] agpgart: AGP aperture is 128M @ 0xd0000000
[   30.015771] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[   30.239360] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.242307] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.479573] Linux video capture interface: v2.00
[   30.596778] input: PC Speaker as /class/input/input2
[   30.919719] input: PS2++ Logitech MX Mouse as /class/input/input3
[   31.166386] parport: PnPBIOS parport detected.
[   31.166493] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   31.588689] usbcore: registered new interface driver libusual
[   31.588724] cdc_acm 3-1:1.1: ttyACM0: USB ACM device
[   31.600990] cdc_acm 3-1:1.3: ttyACM1: USB ACM device
[   31.607054] usbcore: registered new interface driver cdc_acm
[   31.607059] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[   31.615347] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.616312] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 20
[   31.616325] saa7134[0]: found at 0000:00:08.0, rev: 1, irq: 20, latency: 32, mmio: 0xe2425000
[   31.616334] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   31.616350] saa7134[0]: board init: gpio is 0
[   31.762641] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   31.762654] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   31.762664] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   31.762675] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.762685] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.762695] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.762705] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.762716] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.765446] Initializing USB Mass Storage driver...
[   31.765585] scsi0 : SCSI emulation for USB Mass Storage devices
[   31.765682] usb-storage: device found at 3
[   31.765684] usb-storage: waiting for device to settle before scanning
[   31.782599] saa7134[0] Tuner type is 38
[   31.817941] scsi1 : SCSI emulation for USB Mass Storage devices
[   31.818026] usbcore: registered new interface driver usb-storage
[   31.818030] USB Mass Storage support registered.
[   31.818163] usb-storage: device found at 2
[   31.818165] usb-storage: waiting for device to settle before scanning
[   31.866602] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   31.866661] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.886560] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   31.886565] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[   31.886622] tuner 1-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   31.886625] tuner 1-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   31.906574] saa7134[0]: registered device video0 [v4l2]
[   31.906609] saa7134[0]: registered device vbi0
[   31.906640] saa7134[0]: registered device radio0
[   32.020730] saa7134 ALSA driver for DMA sound loaded
[   32.020765] saa7134[0]/alsa: saa7134[0] at 0xe2425000 irq 20 registered as card -2
[   32.407891] nvidia: module license 'NVIDIA' taints kernel.
[   32.662438] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.662763] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   32.703462] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   33.026178] intel8x0_measure_ac97_clock: measured 56918 usecs
[   33.026183] intel8x0: clocking to 48000
[   33.206370] fuse init (API version 7.8)
[   33.250730] lp0: using parport0 (interrupt-driven).
[   33.313926] Adding 1172736k swap on /dev/disk/by-uuid/6f928e71-84d9-47cf-b66c-e69555ad22ea.  Priority:-1 extents:1 across:1172736k
[   33.480786] EXT3 FS on hda1, internal journal
[   36.766078] usb-storage: device scan complete
[   36.818051] usb-storage: device scan complete
[   36.822041] scsi 0:0:0:0: Direct-Access     Medion   Flash XL  MMC/SD 2.6D PQ: 0 ANSI: 0 CCS
[   36.825040] scsi 1:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[   36.829024] scsi 0:0:0:1: Direct-Access     Medion   Flash XL      CF 2.6D PQ: 0 ANSI: 0 CCS
[   36.836022] scsi 0:0:0:2: Direct-Access     Medion   Flash XL      MS 2.6D PQ: 0 ANSI: 0 CCS
[   36.843020] scsi 0:0:0:3: Direct-Access     Medion   Flash XL      SM 2.6D PQ: 0 ANSI: 0 CCS
[   36.895019] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[   36.902155] sda: Write Protect is off
[   36.902160] sda: Mode Sense: 00 47 00 00
[   36.902162] sda: assuming drive cache: write through
[   36.921464] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[   36.927977] sda: Write Protect is off
[   36.927982] sda: Mode Sense: 00 47 00 00
[   36.927984] sda: assuming drive cache: write through
[   36.927989]  sda: unknown partition table
[   36.988984] sd 0:0:0:0: Attached scsi removable disk sda
[   37.010976] sd 0:0:0:1: Attached scsi removable disk sdb
[   37.021969] sd 0:0:0:2: Attached scsi removable disk sdc
[   37.032964] sd 0:0:0:3: Attached scsi removable disk sdd
[   37.064904] SCSI device sde: 960512 512-byte hdwr sectors (492 MB)
[   37.078009] sde: Write Protect is off
[   37.078012] sde: Mode Sense: 00 6a 00 00
[   37.078015] sde: assuming drive cache: write through
[   37.096885] SCSI device sde: 960512 512-byte hdwr sectors (492 MB)
[   37.109877] sde: Write Protect is off
[   37.109880] sde: Mode Sense: 00 6a 00 00
[   37.109882] sde: assuming drive cache: write through
[   37.109886]  sde: sde1
[   37.130905] sd 1:0:0:0: Attached scsi removable disk sde
[   37.145360] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.145384] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   37.145404] sd 0:0:0:2: Attached scsi generic sg2 type 0
[   37.145428] sd 0:0:0:3: Attached scsi generic sg3 type 0
[   37.145450] sd 1:0:0:0: Attached scsi generic sg4 type 0
[   46.512947] ibm_acpi: ec object not found
[   46.575752] Using specific hotkey driver
[   46.654111] input: Power Button (FF) as /class/input/input4
[   46.658786] ACPI: Power Button (FF) [PWRF]
[   46.694568] input: Power Button (CM) as /class/input/input5
[   46.699211] ACPI: Power Button (CM) [PWRB]
[   46.735346] input: Sleep Button (CM) as /class/input/input6
[   46.740034] ACPI: Sleep Button (CM) [FUTS]
[   46.836692] No dock devices found.
[   46.887132] pcc_acpi: loading...
[   51.196745] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   51.196777] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   51.196784] agpgart: SiS delay workaround: giving bridge time to recover.
[   51.212079] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   51.743444] ppdev: user-space parallel port driver
[   53.705000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   53.705006] apm: overridden by ACPI.
[   55.090428] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   55.090434] vboxdrv: Successfully done.
[   55.570130] Bluetooth: Core ver 2.11
[   55.570203] NET: Registered protocol family 31
[   55.570206] Bluetooth: HCI device and connection manager initialized
[   55.570209] Bluetooth: HCI socket layer initialized
[   55.640982] Bluetooth: L2CAP ver 2.8
[   55.640987] Bluetooth: L2CAP socket layer initialized
[   55.716281] Bluetooth: RFCOMM socket layer initialized
[   55.716297] Bluetooth: RFCOMM TTY layer initialized
[   55.716299] Bluetooth: RFCOMM ver 1.8
[  147.166336] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[  147.173332] sda: Write Protect is off
[  147.173337] sda: Mode Sense: 00 47 00 00
[  147.173340] sda: assuming drive cache: write through
[  147.188318] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[  147.195314] sda: Write Protect is off
[  147.195318] sda: Mode Sense: 00 47 00 00
[  147.195320] sda: assuming drive cache: write through
[  147.195859]  sda: unknown partition table


---

### Post by Matakoo on 2007-07-19
Your machine DOES recognize the card-reader, as seen by the below. So far, so good.

```
[   36.822041] scsi 0:0:0:0: Direct-Access     Medion   Flash XL  MMC/SD 2.6D PQ: 0 ANSI: 0 CCS
[   36.825040] scsi 1:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[   36.829024] scsi 0:0:0:1: Direct-Access     Medion   Flash XL      CF 2.6D PQ: 0 ANSI: 0 CCS
[   36.836022] scsi 0:0:0:2: Direct-Access     Medion   Flash XL      MS 2.6D PQ: 0 ANSI: 0 CCS
[   36.843020] scsi 0:0:0:3: Direct-Access     Medion   Flash XL      SM 2.6D PQ: 0 ANSI: 0 CCS
```However, there's something wrong with the partition table. 

```

[  147.166336] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[  147.173332] sda: Write Protect is off
[  147.173337] sda: Mode Sense: 00 47 00 00
[  147.173340] sda: assuming drive cache: write through
[  147.188318] SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
[  147.195314] sda: Write Protect is off
[  147.195318] sda: Mode Sense: 00 47 00 00
[  147.195320] sda: assuming drive cache: write through
[  147.195859]  sda: unknown partition table 
```Which tells me one of two things:

1. Something has happened to damage the contents/file system on the card.

or

2. There is no file system on the card that Linux knows what to do with. Is it possible that the camera may use the card in RAW format, that is: without a file system? The manual to the camera should make that clear.

Try the following:

```
 sudo fdisk -l /dev/sda
```and post the result.

---

### Post by kasperbs on 2007-07-19
Output while the card was in the card reader:
> Disk /dev/sda: 65 Mb, 65536000 byte
8 hoveder, 32 sektorer/spor, 500 cylindre
Enheder = cylindre af 256 * 512 = 131072 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1         500       63980+   1  FAT12
Partition 1 har forskellig fysisk/logisk begyndelse (ikke-Linux?):
     fys=(0, 1, 1) logisk=(0, 1, 8)
Partition 1 har forskellig fysisk/logisk endelse:
     fys=(498, 7, 32) logisk=(499, 7, 32)
rudolf@rudolf-desktop:~$ 

---

### Post by Matakoo on 2007-07-19
> **kasperbs said:**
> Output while the card was in the card reader:

There's something odd here...no idea why it's FAT12 on the card (it doesn't seem to be a very good choice for a card of that size) or why Linux refuses to recognize it, since Linux does indeed support that special variety of FAT, but I saw somewhere that some cameras store the filesystem type in the wrong place and that's why the automount features has problem with it.

If so, this explicit mount might work:

```
sudo mount -t fat -o fat=12 /dev/sda1 /mnt
```That should hopefully mount your card in /mnt so you can copy the files over. It is a bit of a drag having to do things this way, I know, so let's hope a better fix (if my suggestion is indeed a fix) comes along.

---

### Post by kasperbs on 2007-07-20
> **Matakoo said:**
> There's something odd here...no idea why it's FAT12 on the card (it doesn't seem to be a very good choice for a card of that size) or why Linux refuses to recognize it, since Linux does indeed support that special variety of FAT, but I saw somewhere that some cameras store the filesystem type in the wrong place and that's why the automount features has problem with it.

If so, this explicit mount might work:

```
sudo mount -t fat -o fat=12 /dev/sda1 /mnt
```That should hopefully mount your card in /mnt so you can copy the files over. It is a bit of a drag having to do things this way, I know, so let's hope a better fix (if my suggestion is indeed a fix) comes along.
I get the message that its an unknown filesystem 'fat', and it suggests that maybe i meant to use 'vfat'
and when i try
> rudolf@rudolf-desktop:~$ sudo mount -t vfat -o fat=12 /dev/sda1 /mnt
I get a message saying that the device /dev/sda1 does not exist

---

### Post by JesterDev on 2007-07-20
Just a thought, but how about:

```

sudo mount -t vfat -o fat=12 /dev/sda /mnt

```

Or perhaps instead of sda use sg0? 

Another thing you might consider is making a dir inside /mnt and mounting to that dir. i.e. /mnt/pictures:

```

sudo mount -t vfat -o fat=12 /dev/sda /mnt/pictures

```

I seem to remember having a simular issue many years ago and making a dir under /mnt fixed it.

---

### Post by kasperbs on 2007-07-20
> **JesterDev said:**
> Just a thought, but how about:

```

sudo mount -t vfat -o fat=12 /dev/sda /mnt

```

Or perhaps instead of sda use sg0? 

Another thing you might consider is making a dir inside /mnt and mounting to that dir. i.e. /mnt/pictures:

```

sudo mount -t vfat -o fat=12 /dev/sda /mnt/pictures

```

I seem to remember having a simular issue many years ago and making a dir under /mnt fixed it.
Thanks for your suggestion, but I get the following error, also when mounting to a directory
> rudolf@rudolf-desktop:~$ sudo mount -t vfat -o fat=12 /dev/sda /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rudolf@rudolf-desktop:~$ 

---

### Post by Matakoo on 2007-07-20
> **kasperbs said:**
> Thanks for your suggestion, but I get the following error, also when mounting to a directory

I'm not surprised. That's what I would expect when trying to mount an entire disk (dev/sda) instead of its partition(s) (/dev/sda1).

You might want to change vfat to msdos. Like:

```
sudo mount -t msdos -o fat=12 /dev/sda1 /mnt
```I don't know if it makes any difference, but doesn't hurt to try.

To be honest, I think you've been bitten by the bug mention here:

[http://lkml.org/lkml/2005/8/19/32](http://lkml.org/lkml/2005/8/19/32)

If one can call it bug when expecting the filesystem information to be in the correct place...

There ought to be a workaround, but I can't think of one. I'd write a bugreport on launchpad.net if I were you.

---

### Post by kasperbs on 2007-07-20
> To be honest, I think you've been bitten by the bug mention here:
I think you are right, because it doesn't work, thanks for your effort thought.

---

### Post by yogo on 2007-08-14
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
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
[    0.000000] Entering add_active_range(0, 0, 81648) 0 entries of 256 used
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
[   63.724465] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
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
[   65.383640] fuse init (API version 7.8)
[   65.456381] lp0: using parport0 (interrupt-driven).
[   65.583056] Adding 931728k swap on /dev/disk/by-uuid/b87c6b86-a9b1-400b-9065-a17584da64aa.  Priority:-1 extents:1 across:931728k
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

The above is mine, it is from an internal card reader that is attached to the internal usb header. Doesn't seem to have power or enough of power.

---

