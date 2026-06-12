---
title: "Help needed installing a wireless network on Acer Travelmate 2200"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-06-28
I can't get my wireless connection to work.

I haven't installed anything yet because I don't know what I'm looking for.
I'm not sure how to find out what wireless card I have so I'll need some instructions if you need to know that information.

I have installed wine if that helps because I might have to install Windows drives.

Does anyone know what I need to do?

Thanks

---

### Post by RanulfWolfSage on 2007-06-28
Check out this post, see if it helps. I added my Wireless G PC-Card into my laptop and got nothing, as it didn't have a driver for it. Thanks to Ndiswrapper I was able to use the Windows version of the driver and now it works fine.

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html")

I hope that helps! :)

---

### Post by nirpius on 2007-06-28
I couldn't use that guide because I didn't know what drivers I was looking for or where it was. Also, I don't think this is normal, when I go to System, Administration, Network it doesn't show any wireless option in there. I only have wired and modem.

I did manage to install ndiswrapper though.

---

### Post by nirpius on 2007-06-28
I found a driver on the internet at the Acer help page :) I installed that using this guide [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html) but then it said I need to know the device name.

It told me to run dmesg in the terminal but that just gave me squillions of lines of gobblydegook which I don't understand. What exactly am I supposed to be looking for in there to find the device name for my Wireless card (it's an inbuilt card and on the website it says it's got something to do with Acer IPN2220).

Here's a copy of my dmesg

> nirpius@ACER2200:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000008000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037e70000 end: 0000000037f70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037f70000 size: 000000000000b000 end: 0000000037f7b000 type: 3
[    0.000000] copy_e820_map() start: 0000000037f7b000 size: 0000000000005000 end: 0000000037f80000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f80000 size: 0000000000080000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 0000000047f80000 size: 0000000000080000 end: 0000000048000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037f70000 (usable)
[    0.000000]  BIOS-e820: 0000000037f70000 - 0000000037f7b000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037f7b000 - 0000000037f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f80000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 0000000047f80000 - 0000000048000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 895MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6950
[    0.000000] Entering add_active_range(0, 0, 229232) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229232
[    0.000000]   HighMem    229232 ->   229232
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229232
[    0.000000] On node 0 totalpages: 229232
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1758 pages used for memmap
[    0.000000]   Normal zone: 223378 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f69b0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37f77870
[    0.000000] ACPI: FADT (v001 COMPAL ELW80    0x06040000 ATI  0x00000003) @ 0x37f7af32
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37f7afa6
[    0.000000] ACPI: DSDT (v001 COMPAL    ELW80 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 48000000:b6c00000)
[    0.000000] Detected 2666.708 MHz processor.
[   11.723795] Built 1 zonelists.  Total pages: 227442
[   11.723808] Kernel command line: root=UUID=bc0ca013-e945-4bfc-88a4-cf58a7d7a0d0 ro quiet splash
[   11.724174] mapped APIC to ffffd000 (fee00000)
[   11.724177] mapped IOAPIC to ffffc000 (fec00000)
[   11.724189] Enabling fast FPU save and restore... done.
[   11.724193] Enabling unmasked SIMD FPU exception support... done.
[   11.724222] Initializing CPU#0
[   11.724349] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.726341] Console: colour VGA+ 80x25
[   11.727608] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.729615] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.768529] Memory: 897848k/916928k available (1992k kernel code, 18452k reserved, 900k data, 328k init, 0k highmem)
[   11.768556] virtual kernel memory layout:
[   11.768557]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.768558]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.768559]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.768560]     lowmem  : 0xc0000000 - 0xf7f70000   ( 895 MB)
[   11.768562]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   11.768563]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   11.768572]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   11.768576] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.848041] Calibrating delay using timer specific routine.. 5340.44 BogoMIPS (lpj=10680886)
[   11.848144] Security Framework v1.0.0 initialized
[   11.848159] SELinux:  Disabled at boot.
[   11.848196] Mount-cache hash table entries: 512
[   11.848529] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   11.848548] monitor/mwait feature present.
[   11.848558] using mwait in idle threads.
[   11.848574] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   11.848577] CPU: L2 cache: 256K
[   11.848588] CPU: Hyper-Threading is disabled
[   11.848590] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   11.848619] Compat vDSO mapped to ffffe000.
[   11.848623] Remapping vsyscall page to ffffe000
[   11.848665] Checking 'hlt' instruction... OK.
[   11.864230] SMP alternatives: switching to UP code
[   11.864798] Freeing SMP alternatives: 11k freed
[   11.865383] Early unpacking initramfs... done
[   12.511319] ACPI: Core revision 20060707
[   12.532096] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.539416] CPU0: Intel(R) Celeron(R) CPU 2.66GHz stepping 04
[   12.539461] Total of 1 processors activated (5340.44 BogoMIPS).
[   12.539527] ENABLING IO-APIC IRQs
[   12.539705] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.579341] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   12.579377] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   12.579380] ...trying to set up timer as Virtual Wire IRQ... works.
[   12.725882] Brought up 1 CPUs
[   12.726186] Booting paravirtualized kernel on bare hardware
[   12.726287] Time: 18:26:26  Date: 05/28/107
[   12.726331] NET: Registered protocol family 16
[   12.726478] EISA bus registered
[   12.726486] ACPI: bus type pci registered
[   12.758591] PCI: PCI BIOS revision 2.10 entry at 0xfd768, last bus=2
[   12.758594] PCI: Using configuration type 1
[   12.758597] Setting up standard PCI resources
[   12.785627] ACPI: Interpreter enabled
[   12.785634] ACPI: Using IOAPIC for interrupt routing
[   12.786340] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.786351] PCI: Probing PCI hardware (bus 00)
[   12.787676] Boot video device is 0000:01:05.0
[   12.787945] PCI: Transparent bridge - 0000:00:14.4
[   12.788049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.790644] ACPI: PCI Interrupt Link [LNK0] (IRQs 10 11) *0, disabled.
[   12.790929] ACPI: PCI Interrupt Link [LNK1] (IRQs 10 11) *0, disabled.
[   12.791211] ACPI: PCI Interrupt Link [LNK2] (IRQs 10 11) *0, disabled.
[   12.791487] ACPI: PCI Interrupt Link [LNK3] (IRQs 10 11) *0, disabled.
[   12.797434] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   12.798821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.799432] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.799456] pnp: PnP ACPI init
[   12.805236] pnp: PnP ACPI: found 10 devices
[   12.805245] PnPBIOS: Disabled by ACPI PNP
[   12.805332] PCI: Using ACPI for IRQ routing
[   12.805336] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.809539] NET: Registered protocol family 8
[   12.809543] NET: Registered protocol family 20
[   12.809871] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[   12.809875] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[   12.809878] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[   12.809881] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   12.810359] PCI: Bridge: 0000:00:01.0
[   12.810364]   IO window: 9000-9fff
[   12.810369]   MEM window: d0100000-d01fffff
[   12.810373]   PREFETCH window: e0000000-efffffff
[   12.810386] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   12.810389]   IO window: 0000a800-0000a8ff
[   12.810394]   IO window: 0000ac00-0000acff
[   12.810400]   PREFETCH window: 50000000-53ffffff
[   12.810406]   MEM window: 54000000-57ffffff
[   12.810411] PCI: Bridge: 0000:00:14.4
[   12.810415]   IO window: a000-afff
[   12.810420]   MEM window: d0200000-d02fffff
[   12.810425]   PREFETCH window: 50000000-53ffffff
[   12.810469] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.810509] NET: Registered protocol family 2
[   12.841648] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.841934] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.843534] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.844412] TCP: Hash tables configured (established 131072 bind 65536)
[   12.844419] TCP reno registered
[   12.853737] checking if image is initramfs... it is
[   13.469768] Freeing initrd memory: 6784k freed
[   13.470477] audit: initializing netlink socket (disabled)
[   13.470498] audit(1183055186.792:1): initialized
[   13.470686] VFS: Disk quotas dquot_6.5.1
[   13.470711] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.470781] io scheduler noop registered
[   13.470785] io scheduler anticipatory registered
[   13.470787] io scheduler deadline registered
[   13.470801] io scheduler cfq registered (default)
[   13.998947] isapnp: Scanning for PnP cards...
[   14.350203] isapnp: No Plug & Play device found
[   14.448434] Real Time Clock Driver v1.12ac
[   14.448514] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.448647] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.450511] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   14.450521] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   14.450629] mice: PS/2 mouse device common for all mice
[   14.451449] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.451827] input: Macintosh mouse button emulation as /class/input/input0
[   14.451883] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.451889] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.452135] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.452510] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.452561] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.452568] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.452571] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.452573] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.452576] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.452768] EISA: Probing bus 0 at eisa.0
[   14.452781] Cannot allocate resource for EISA slot 1
[   14.452800] Cannot allocate resource for EISA slot 8
[   14.452802] EISA: Detected 0 cards.
[   14.482831] TCP cubic registered
[   14.482843] NET: Registered protocol family 1
[   14.482873] Using IPI No-Shortcut mode
[   14.482999] ACPI: (supports S0 S3 S4 S5)
[   14.483049]   Magic number: 11:388:444
[   14.483703] Freeing unused kernel memory: 328k freed
[   14.485355] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.485402] Time: tsc clocksource has been installed.
[   15.789171] Capability LSM initialized
[   15.849763] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   15.849777] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.612304] usbcore: registered new interface driver usbfs
[   16.612341] usbcore: registered new interface driver hub
[   16.612377] usbcore: registered new device driver usb
[   16.613423] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.613472] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   16.613489] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.613648] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.613676] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0001000
[   16.697886] usb usb1: configuration #1 chosen from 1 choice
[   16.697926] hub 1-0:1.0: USB hub found
[   16.697941] hub 1-0:1.0: 3 ports detected
[   16.796512] 8139too Fast Ethernet driver 0.9.28
[   16.803746] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   16.803768] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.803806] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.803824] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd0002000
[   16.867571] usb usb2: configuration #1 chosen from 1 choice
[   16.867613] hub 2-0:1.0: USB hub found
[   16.867627] hub 2-0:1.0: 3 ports detected
[    4.608000] Time: acpi_pm clocksource has been installed.
[    4.640000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    4.640000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.640000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.640000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xd0003000
[    4.640000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.640000] usb usb3: configuration #1 chosen from 1 choice
[    4.640000] hub 3-0:1.0: USB hub found
[    4.640000] hub 3-0:1.0: 6 ports detected
[    4.748000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.748000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.748000] ATIIXP: chipset revision 0
[    4.748000] ATIIXP: not 100% native mode: will probe irqs later
[    4.748000]     ide0: BM-DMA at 0x8070-0x8077, BIOS settings: hda:DMA, hdb:pio
[    4.748000]     ide1: BM-DMA at 0x8078-0x807f, BIOS settings: hdc:DMA, hdd:pio
[    4.748000] Probing IDE interface ide0...
[    5.040000] hda: IC25N040ATCS05-0, ATA DISK drive
[    5.716000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.732000] Probing IDE interface ide1...
[    6.472000] hdc: HL-DT-ST DVDRAM GSA-4080N, ATAPI CD/DVD-ROM drive
[    6.812000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.828000] SCSI subsystem initialized
[    6.836000] libata version 2.20 loaded.
[    6.840000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[    6.840000] eth0: RealTek RTL8139 at 0xf8824c00, 00:02:3f:0b:26:73, IRQ 18
[    6.840000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.844000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.860000] hda: max request size: 128KiB
[    6.868000] hda: 78140160 sectors (40007 MB) w/7898KiB Cache, CHS=65535/16/63, UDMA(100)
[    6.868000] hda: cache flushes not supported
[    6.868000]  hda: hda1 hda2 < hda5 >
[    6.932000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.932000] Uniform CD-ROM driver Revision: 3.20
[    7.124000] Attempting manual resume
[    7.124000] swsusp: Resume From Partition 3:5
[    7.124000] PM: Checking swsusp image.
[    7.124000] PM: Resume from disk failed.
[    7.176000] kjournald starting.  Commit interval 5 seconds
[    7.176000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.140000] eth0: link down
[   22.432000] NET: Registered protocol family 17
[   23.248000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   23.720000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.724000] agpgart: Detected Ati IGP9100/M chipset
[   23.728000] agpgart: AGP aperture is 32M @ 0xd2000000
[   23.788000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.796000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.016000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   24.016000] atiixp: codec reset timeout
[   24.380000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   24.412000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   24.432000] irda_init()
[   24.432000] NET: Registered protocol family 23
[   24.448000] input: PC Speaker as /class/input/input3
[   24.536000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   24.556000] Yenta: CardBus bridge found at 0000:02:04.0 [1025:0065]
[   24.556000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.556000] Yenta: Routing CardBus interrupts to PCI
[   24.556000] Yenta TI: socket 0000:02:04.0, mfunc 0x00111c12, devctl 0x44
[   24.792000] Yenta: ISA IRQ mask 0x0a68, PCI irq 16
[   24.792000] Socket status: 30000006
[   24.792000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   24.792000] cs: IO port probe 0xa000-0xafff: clean.
[   24.792000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   24.792000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   25.136000] cs: IO port probe 0x100-0x3af: clean.
[   25.140000] cs: IO port probe 0x3e0-0x4ff: clean.
[   25.140000] cs: IO port probe 0x820-0x8ff: clean.
[   25.140000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[   25.140000] cs: IO port probe 0xa00-0xaff: clean.
[   25.312000] fuse init (API version 7.8)
[   25.400000] lp: driver loaded but no devices found
[   25.448000] Adding 1646620k swap on /dev/disk/by-uuid/cea4aafd-8acf-404b-ba74-1c0603f6a621.  Priority:-1 extents:1 across:1646620k
[   25.604000] EXT3 FS on hda1, internal journal
[   29.840000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   29.904000] usbcore: registered new interface driver ndiswrapper
[   31.576000] input: Power Button (FF) as /class/input/input4
[   31.584000] ACPI: Power Button (FF) [PWRF]
[   31.624000] input: Lid Switch as /class/input/input5
[   31.628000] ACPI: Lid Switch [LID]
[   31.668000] input: Power Button (CM) as /class/input/input6
[   31.676000] ACPI: Power Button (CM) [PWRB]
[   31.712000] ACPI: Battery Slot [BAT1] (battery present)
[   31.844000] ibm_acpi: ec object not found
[   31.888000] ACPI: AC Adapter [ACAD] (on-line)
[   31.940000] No dock devices found.
[   31.960000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.980000] Using specific hotkey driver
[   32.084000] pcc_acpi: loading...
[   37.060000] [drm] Initialized drm 1.1.0 20060810
[   37.076000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.080000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   37.804000] ppdev: user-space parallel port driver
[   39.984000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   39.984000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   39.984000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
[   40.144000] [drm] Setting GART location based on new memory map
[   40.144000] [drm] Loading R200 Microcode
[   40.144000] [drm] writeback test succeeded in 1 usecs
[   40.976000] apm: BIOS not found.
[   41.476000] Bluetooth: Core ver 2.11
[   41.476000] NET: Registered protocol family 31
[   41.476000] Bluetooth: HCI device and connection manager initialized
[   41.476000] Bluetooth: HCI socket layer initialized
[   41.524000] Bluetooth: L2CAP ver 2.8
[   41.524000] Bluetooth: L2CAP socket layer initialized
[   41.644000] Bluetooth: RFCOMM socket layer initialized
[   41.648000] Bluetooth: RFCOMM TTY layer initialized
[   41.648000] Bluetooth: RFCOMM ver 1.8
[   54.100000] NET: Registered protocol family 10
[   54.100000] lo: Disabled Privacy Extensions
[   54.100000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4894.124000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 4894.124000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4908.076000] eth0: no IPv6 routers present


Any ideas?

---

### Post by RanulfWolfSage on 2007-06-28
After running the modprobe ndiswrapper command and not getting any errors, it instructs to continue using the terminal to test everything out. Personally, yes that will work but I diverted at that point. I ran the command 'iwconfig' in terminal to verify the connection was created, it is most likely wlan0. Then since I was running Ubuntu Fiesty Fawn, I just used the network manager applet link on the top bar to view the wireless connection, and search for available networks.

Also, [http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/") is a great site for finding the correct drivers for wireless network cards/chips/devices.

---

