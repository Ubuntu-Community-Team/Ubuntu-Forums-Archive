---
title: "enable DBV-T card"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by planC on 2007-12-24
I installed kaffeine to run the dvb-t card but how do i enable the card, and how do i install the drivers? wine won't do it.

---

### Post by as0l0 on 2007-12-24
what sort of card do you have?  i have a nova-t and i had to download a bit of firmware, rename it and have it in the right place.

i fuigured this out with dmesg at the command line and google.

---

### Post by planC on 2007-12-24
I have an Avermedia DVB-T super007. I tried to download the drivers but it wouldn't install. I don't know the code to enable the thing!

---

### Post by lgambett on 2007-12-24
Do not use wine and do not try to install anything, it is possible that your card is already functioning. Please enter a Terminal window and issue the command
dmesg
and post the output.
What kind / version of Ubuntu are you using ? (eg Feisty, Gutsy, Ubuntu, Kubuntu...)

---

### Post by planC on 2007-12-24
I am usung 'gutsy', here is the output:

[sudo] password for ian:
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff10000 (usable)
[    0.000000]  BIOS-e820: 000000007ff10000 - 000000007ff20000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff20000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524048
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524048
[    0.000000] On node 0 totalpages: 524048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292370 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAD60 checksum 0
[    0.000000] ACPI: RSDP 000FAD60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF10000, 0030 (r1 A M I  OEMRSDT  10000507 MSFT       97)
[    0.000000] ACPI: FACP 7FF10200, 0081 (r2 A M I  OEMFACP  10000507 MSFT       97)
[    0.000000] ACPI: DSDT 7FF103F0, 4B77 (r1  A0217 A0217001        1 INTL  2002026)
[    0.000000] ACPI: FACS 7FF20000, 0040
[    0.000000] ACPI: APIC 7FF10390, 005C (r1 A M I  OEMAPIC  10000507 MSFT       97)
[    0.000000] ACPI: OEMB 7FF20040, 0040 (r1 A M I  AMI_OEM  10000507 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] Built 1 zonelists.  Total pages: 519954
[    0.000000] Kernel command line: root=UUID=3e2f3a76-30bf-492e-b431-a55d7f41a10f ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.183 MHz processor.
[   25.594472] Console: colour VGA+ 80x25
[   25.594773] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.595106] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.653035] Memory: 2066844k/2096192k available (2015k kernel code, 28144k reserved, 916k data, 364k init, 1178688k highmem)
[   25.653044] virtual kernel memory layout:
[   25.653045]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.653046]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.653047]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.653048]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.653049]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.653051]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   25.653052]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   25.653054] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.653087] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.733035] Calibrating delay using timer specific routine.. 4402.49 BogoMIPS (lpj=8804982)
[   25.733059] Security Framework v1.0.0 initialized
[   25.733063] SELinux:  Disabled at boot.
[   25.733074] Mount-cache hash table entries: 512
[   25.733175] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   25.733182] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.733184] CPU: L2 Cache: 512K (64 bytes/line)
[   25.733186] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   25.733195] Compat vDSO mapped to ffffe000.
[   25.733204] Checking 'hlt' instruction... OK.
[   25.749138] SMP alternatives: switching to UP code
[   25.749305] Freeing SMP alternatives: 11k freed
[   25.749525] Early unpacking initramfs... done
[   26.011365] ACPI: Core revision 20070126
[   26.011420] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.012976] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 00
[   26.012991] Total of 1 processors activated (4402.49 BogoMIPS).
[   26.013078] ENABLING IO-APIC IRQs
[   26.013229] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.160712] Brought up 1 CPUs
[   26.160786] Booting paravirtualized kernel on bare hardware
[   26.160839] Time: 10:51:47  Date: 11/25/107
[   26.160853] NET: Registered protocol family 16
[   26.160909] EISA bus registered
[   26.160919] ACPI: bus type pci registered
[   26.161631] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   26.161633] PCI: Using configuration type 1
[   26.161635] Setting up standard PCI resources
[   26.168245] ACPI: EC: Look up EC in DSDT
[   26.171961] ACPI: Interpreter enabled
[   26.171963] ACPI: (supports S0 S1 S3 S4 S5)
[   26.171975] ACPI: Using IOAPIC for interrupt routing
[   26.178104] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.178112] PCI: Probing PCI hardware (bus 00)
[   26.178746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.178888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   26.178948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   26.186141] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   26.186229] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   26.186314] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 12 14 15)
[   26.186399] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   26.186502] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[   26.186601] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[   26.186697] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
[   26.186784] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[   26.186846] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.186854] pnp: PnP ACPI init
[   26.186861] ACPI: bus type pnp registered
[   26.190101] pnp: PnP ACPI: found 13 devices
[   26.190103] ACPI: ACPI bus type pnp unregistered
[   26.190106] PnPBIOS: Disabled by ACPI PNP
[   26.190142] PCI: Using ACPI for IRQ routing
[   26.190144] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.199383] NET: Registered protocol family 8
[   26.199385] NET: Registered protocol family 20
[   26.199429] pnp: 00:08: ioport range 0xc00-0xc0f has been reserved
[   26.199432] pnp: 00:08: ioport range 0xd00-0xd0f has been reserved
[   26.199434] pnp: 00:08: ioport range 0xa20-0xa2f has been reserved
[   26.199436] pnp: 00:08: ioport range 0xa30-0xa3f has been reserved
[   26.199440] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   26.199443] pnp: 00:09: iomem range 0xffee0000-0xffefffff could not be reserved
[   26.199446] pnp: 00:09: iomem range 0xfee00400-0xfee00fff has been reserved
[   26.199450] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.199453] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.199456] pnp: 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   26.199460] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   26.199463] pnp: 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[   26.199465] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   26.199468] pnp: 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[   26.200654] Time: tsc clocksource has been installed.
[   26.229632] PCI: Bridge: 0000:00:01.0
[   26.229635]   IO window: e000-efff
[   26.229638]   MEM window: dff00000-dfffffff
[   26.229641]   PREFETCH window: d0000000-deffffff
[   26.229645] PCI: Bridge: 0000:00:06.0
[   26.229647]   IO window: d000-dfff
[   26.229650]   MEM window: disabled.
[   26.229652]   PREFETCH window: disabled.
[   26.229655] PCI: Bridge: 0000:00:07.0
[   26.229657]   IO window: c000-cfff
[   26.229660]   MEM window: disabled.
[   26.229662]   PREFETCH window: disabled.
[   26.229677] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.229685] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   26.229693] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   26.229704] NET: Registered protocol family 2
[   26.268629] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.268730] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.269822] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.270200] TCP: Hash tables configured (established 131072 bind 65536)
[   26.270203] TCP reno registered
[   26.280697] checking if image is initramfs... it is
[   26.732217] Switched to high resolution mode on CPU 0
[   26.794469] Freeing initrd memory: 7062k freed
[   26.794750] audit: initializing netlink socket (disabled)
[   26.794761] audit(1198579906.944:1): initialized
[   26.794808] highmem bounce pool size: 64 pages
[   26.796032] VFS: Disk quotas dquot_6.5.1
[   26.796067] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.796141] io scheduler noop registered
[   26.796143] io scheduler anticipatory registered
[   26.796144] io scheduler deadline registered
[   26.796155] io scheduler cfq registered (default)
[   26.852051] Boot video device is 0000:03:00.0
[   26.852106] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.852131] assign_interrupt_mode Found MSI capability
[   26.852133] Allocate Port Service[0000:00:01.0:pcie00]
[   26.852235] isapnp: Scanning for PnP cards...
[   27.205378] isapnp: No Plug & Play device found
[   27.222176] Real Time Clock Driver v1.12ac
[   27.222243] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.222321] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.222794] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.223237] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.223387] input: Macintosh mouse button emulation as /class/input/input0
[   27.223431] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[   27.223433] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   27.223673] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.223677] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.223802] mice: PS/2 mouse device common for all mice
[   27.223870] EISA: Probing bus 0 at eisa.0
[   27.223901] EISA: Detected 0 cards.
[   27.224024] TCP cubic registered
[   27.224038] NET: Registered protocol family 1
[   27.224056] Using IPI No-Shortcut mode
[   27.224179]   Magic number: 3:315:882
[   27.224248]   hash matches device ptyx6
[   27.224505] Freeing unused kernel memory: 364k freed
[   28.401580] AppArmor: AppArmor initialized<5>audit(1198579908.444:2):  type=1505 info="AppArmor initialized" pid=1200
[   28.408660] fuse init (API version 7.8)
[   28.412635] Failure registering capabilities with primary security module.
[   28.429815] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.889889] SCSI subsystem initialized
[   28.893374] libata version 2.21 loaded.
[   28.895963] pata_sis 0000:00:02.5: version 0.5.1
[   28.896059] scsi0 : pata_sis
[   28.896091] scsi1 : pata_sis
[   28.896161] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   28.896164] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   28.922894] usbcore: registered new interface driver usbfs
[   28.922917] usbcore: registered new interface driver hub
[   28.922932] usbcore: registered new device driver usb
[   28.942121] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.007575] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   29.007578] Copyright (c) 1999-2006 Intel Corporation.
[   29.114457] Floppy drive(s): fd0 is 1.44M
[   29.156838] FDC 0 is a post-1991 82077
[   29.369903] ata2.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.29, max UDMA/66
[   29.541735] ata2.00: configured for UDMA/66
[   29.548419] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.29 PQ: 0 ANSI: 5
[   29.548549] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   29.548559] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   29.548674] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   29.548687] ohci_hcd 0000:00:03.0: irq 16, io mem 0xdfeb7000
[   29.586589] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   29.586594] Uniform CD-ROM driver Revision: 3.20
[   29.586746] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.590172] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   29.603509] usb usb1: configuration #1 chosen from 1 choice
[   29.603532] hub 1-0:1.0: USB hub found
[   29.603541] hub 1-0:1.0: 3 ports detected
[   29.705423] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   29.705434] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   29.705451] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   29.705463] ohci_hcd 0000:00:03.1: irq 17, io mem 0xdfebc000
[   29.763333] usb usb2: configuration #1 chosen from 1 choice
[   29.763352] hub 2-0:1.0: USB hub found
[   29.763359] hub 2-0:1.0: 3 ports detected
[   29.865235] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   29.865245] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   29.865261] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   29.865272] ohci_hcd 0000:00:03.2: irq 18, io mem 0xdfebd000
[   29.923166] usb usb3: configuration #1 chosen from 1 choice
[   29.923182] hub 3-0:1.0: USB hub found
[   29.923189] hub 3-0:1.0: 2 ports detected
[   30.009038] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   30.025393] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   30.025402] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   30.025420] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   30.025445] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   30.025452] ehci_hcd 0000:00:03.3: irq 19, io mem 0xdfebe000
[   30.184881] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.184957] usb usb4: configuration #1 chosen from 1 choice
[   30.184978] hub 4-0:1.0: USB hub found
[   30.184984] hub 4-0:1.0: 8 ports detected
[   30.288920] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   30.536308] e1000: 0000:00:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:15:f2:4e:89:e5
[   30.569175] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   30.569260] sata_sis 0000:00:05.0: version 0.8
[   30.569278] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   30.569283] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
[   30.569340] scsi2 : sata_sis
[   30.569372] scsi3 : sata_sis
[   30.569428] ata3: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b002 bmdma 0x0001a000 irq 21
[   30.569432] ata4: SATA max UDMA/133 cmd 0x0001a800 ctl 0x0001a402 bmdma 0x0001a008 irq 21
[   30.740344] usb 1-1: device not accepting address 2, error -62
[   31.036075] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.044326] ata3.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   31.044329] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.060313] ata3.00: configured for UDMA/133
[   31.527608] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.572429] ata4.00: ATA-7: ST380815AS, 3.AAD, max UDMA/133
[   31.572432] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.639002] ata4.00: configured for UDMA/133
[   31.639077] scsi 2:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   31.639417] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   31.639463] scsi 3:0:0:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[   31.639737] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   31.648822] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.648836] sd 2:0:0:0: [sda] Write Protect is off
[   31.648838] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.648849] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.648890] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.648896] sd 2:0:0:0: [sda] Write Protect is off
[   31.648898] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.648907] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.648910]  sda: sda1
[   31.652100] sd 2:0:0:0: [sda] Attached SCSI disk
[   31.652215] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   31.652222] sd 3:0:0:0: [sdb] Write Protect is off
[   31.652224] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   31.652233] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.652256] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   31.652262] sd 3:0:0:0: [sdb] Write Protect is off
[   31.652264] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   31.652273] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.652275]  sdb: sdb1 sdb2 < sdb5 >
[   31.713343] sd 3:0:0:0: [sdb] Attached SCSI disk
[   31.779362] usb 1-1: new full speed USB device using ohci_hcd and address 4
[   31.985932] Attempting manual resume
[   31.985935] swsusp: Resume From Partition 8:21
[   31.985936] PM: Checking swsusp image.
[   31.986134] PM: Resume from disk failed.
[   31.989374] usb 1-1: configuration #1 chosen from 1 choice
[   32.052544] kjournald starting.  Commit interval 5 seconds
[   32.052553] EXT3-fs: mounted filesystem with ordered data mode.
[   32.294867] usb 1-2: new low speed USB device using ohci_hcd and address 5
[   32.510874] usb 1-2: configuration #1 chosen from 1 choice
[   32.513942] usbcore: registered new interface driver libusual
[   32.751210] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.751214] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.828734] Initializing USB Mass Storage driver...
[   32.828784] scsi4 : SCSI emulation for USB Mass Storage devices
[   32.828817] usb-storage: device found at 4
[   32.828818] usb-storage: waiting for device to settle before scanning
[   32.828835] usbcore: registered new interface driver usb-storage
[   32.828837] USB Mass Storage support registered.
[   37.824016] usb-storage: device scan complete
[   37.837003] scsi 4:0:0:0: Direct-Access     Brother  DCP-115C         1.00 PQ: 0 ANSI: 2
[   37.867998] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   37.868029] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   38.020723] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.038143] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.435077] Linux video capture interface: v2.00
[   38.753183] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x018C
[   38.753199] usbcore: registered new interface driver usblp
[   38.753202] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   39.158634] saa7130/34: v4l2 driver version 0.2.14 loaded
[   39.158681] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 21
[   39.158688] saa7133[0]: found at 0000:00:09.0, rev: 209, irq: 21, latency: 64, mmio: 0xdfebf800
[   39.158693] saa7133[0]: subsystem: 1461:f01d, board: UNKNOWN/GENERIC [card=0,autodetected]
[   39.158699] saa7133[0]: board init: gpio is 40000
[   39.178122] usbcore: registered new interface driver hiddev
[   39.185917] input: CHESEN USB Keyboard as /class/input/input1
[   39.185945] input: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:03.0-2
[   39.199829] input: CHESEN USB Keyboard as /class/input/input2
[   39.199860] input: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:03.0-2
[   39.199869] usbcore: registered new interface driver usbhid
[   39.199872] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.224343] usbcore: registered new interface driver xpad
[   39.224347] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   39.258974] input: PC Speaker as /class/input/input3
[   39.292295] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   39.292302] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   39.292308] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   39.292314] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.292319] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[   39.292325] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.292330] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.292336] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.292610] saa7133[0]: registered device video0 [v4l2]
[   39.292630] saa7133[0]: registered device vbi0
[   39.419959] saa7134 ALSA driver for DMA sound loaded
[   39.419981] saa7133[0]/alsa: saa7133[0] at 0xdfebf800 irq 21 registered as card -2
[   39.687515] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   39.937371] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   40.107434] intel8x0_measure_ac97_clock: measured 52560 usecs
[   40.107437] intel8x0: clocking to 48000
[   40.691529] lp: driver loaded but no devices found
[   40.736114] Adding 3229024k swap on /dev/sdb5.  Priority:-1 extents:1 across:3229024k
[   41.010852] EXT3 FS on sdb1, internal journal
[   41.887215] No dock devices found.
[   42.064279] input: Power Button (FF) as /class/input/input5
[   42.067866] ACPI: Power Button (FF) [PWRF]
[   42.098505] input: Power Button (CM) as /class/input/input6
[   42.102035] ACPI: Power Button (CM) [PWRB]
[   42.254273] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[   42.255732] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   43.391272] ppdev: user-space parallel port driver
[   43.440628] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   43.642691] audit(1198540324.610:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4771 profile="/usr/sbin/cupsd"
[   43.750342] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.750346] apm: overridden by ACPI.
[   43.915302] Failure registering capabilities with primary security module.
[   44.077271] Bluetooth: Core ver 2.11
[   44.077395] NET: Registered protocol family 31
[   44.077397] Bluetooth: HCI device and connection manager initialized
[   44.077400] Bluetooth: HCI socket layer initialized
[   44.091814] Bluetooth: L2CAP ver 2.8
[   44.091817] Bluetooth: L2CAP socket layer initialized
[   44.168335] Bluetooth: RFCOMM socket layer initialized
[   44.168454] Bluetooth: RFCOMM TTY layer initialized
[   44.168456] Bluetooth: RFCOMM ver 1.8
[   45.872386] Linux agpgart interface v0.102 (c) Dave Jones
[   45.958586] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   45.962255] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   45.962553] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   46.210759] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 23
[   48.605636] NET: Registered protocol family 17
[   49.682449] [fglrx] total      GART = 130023424
[   49.682455] [fglrx] free       GART = 114032640
[   49.682457] [fglrx] max single GART = 114032640
[   49.682459] [fglrx] total      LFB  = 134086656
[   49.682460] [fglrx] free       LFB  = 107040768
[   49.682462] [fglrx] max single LFB  = 107040768
[   49.682464] [fglrx] total      Inv  = 0
[   49.682465] [fglrx] free       Inv  = 0
[   49.682466] [fglrx] max single Inv  = 0
[   49.682468] [fglrx] total      TIM  = 0
[   51.075357] NET: Registered protocol family 10
[   51.075571] lo: Disabled Privacy Extensions
[   61.117719] eth0: no IPv6 routers present
ian@ian-desktop:~$

---

### Post by sicofante on 2007-12-26
I have the same DVB-T hardware (a Philips SAA1733 based card) and have exactly the same issues. It seems Gutsy can see this hardware as a "Video Broadcast Device" but that's not enough. I've been to [LinuxTV.org]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers") but still haven't found how to make the tuner visible.

Here's my lspci output (check the line before the last):

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
06:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:02.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:03.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
06:08.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
I'll keep searching for info on this issue and will post any findings.

---

### Post by planC on 2007-12-26
Ok , thanks. Perhaps the new edition released in April will make these things work out of the box like they say. I will keep combing the threads till i find a solution.... perhaps...

---

### Post by sicofante on 2007-12-27
Good news here. After much research and trial and error, I got it working just by adding this line

```
 saa7134-dvb
```to the /etc/modules file and rebooting. (You must scan the channels with the scan command after that, but that's the normal procedure. I'll help with that if you don't know what I'm talking about.)

Give it a try.

---

