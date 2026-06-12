---
title: "Freezes"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by mellamopobrede on 2007-08-18
Hello.  I dont know if this might help explain why i might be having freezing problems on my computer but i found on another forum.

poorav@poorav:~$ uname -a
Linux poorav 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
poorav@poorav:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA [SiS] (rev 01)
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:09.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
poorav@poorav:~$ dmesg
[ 0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[ 0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fef0000 end: 000000005fff0000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000005fff0000 size: 0000000000003000 end: 000000005fff3000 type: 4
[ 0.000000] copy_e820_map() start: 000000005fff3000 size: 000000000000d000 end: 0000000060000000 type: 3
[ 0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[ 0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[ 0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[ 0.000000] BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] 639MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000f6450
[ 0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 393200
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 393200
[ 0.000000] On node 0 totalpages: 393200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 1279 pages used for memmap
[ 0.000000] HighMem zone: 162545 pages, LIFO batch:31
[ 0.000000] DMI 2.4 present.
[ 0.000000] ACPI: RSDP (v000 AWARD ) @ 0x000f7f80
[ 0.000000] ACPI: RSDT (v001 AWARD AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff3040
[ 0.000000] ACPI: FADT (v001 AWARD AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff30c0
[ 0.000000] ACPI: MADT (v001 AWARD AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff7380
[ 0.000000] ACPI: DSDT (v001 AWARD AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 15:12 APIC version 16
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[ 0.000000] Detected 1808.457 MHz processor.
[ 10.863011] Built 1 zonelists. Total pages: 390129
[ 10.863015] Kernel command line: root=UUID=f173f60b-851d-4745-a5b4-f808e613b9f2 ro quiet splash
[ 10.863155] mapped APIC to ffffd000 (fee00000)
[ 10.863157] mapped IOAPIC to ffffc000 (fec00000)
[ 10.863160] Enabling fast FPU save and restore... done.
[ 10.863163] Enabling unmasked SIMD FPU exception support... done.
[ 10.863171] Initializing CPU#0
[ 10.863217] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 10.864633] Console: colour VGA+ 80x25
[ 10.865077] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 10.865835] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 10.909919] Memory: 1547964k/1572800k available (1992k kernel code, 23588k reserved, 900k data, 328k init, 655296k highmem)
[ 10.909930] virtual kernel memory layout:
[ 10.909932] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 10.909933] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 10.909934] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 10.909936] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 10.909937] .init : 0xc03d9000 - 0xc042b000 ( 328 kB)
[ 10.909938] .data : 0xc02f2374 - 0xc03d36d4 ( 900 kB)
[ 10.909940] .text : 0xc0100000 - 0xc02f2374 (1992 kB)
[ 10.909943] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 10.987173] Calibrating delay using timer specific routine.. 3618.71 BogoMIPS (lpj=7237422)
[ 10.987213] Security Framework v1.0.0 initialized
[ 10.987223] SELinux: Disabled at boot.
[ 10.987237] Mount-cache hash table entries: 512
[ 10.987372] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[ 10.987381] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 10.987383] CPU: L2 Cache: 256K (64 bytes/line)
[ 10.987386] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[ 10.987397] Compat vDSO mapped to ffffe000.
[ 10.987402] Remapping vsyscall page to ffffe000
[ 10.987412] Checking 'hlt' instruction... OK.
[ 11.003286] SMP alternatives: switching to UP code
[ 11.003468] Freeing SMP alternatives: 11k freed
[ 11.003665] Early unpacking initramfs... done
[ 11.312168] ACPI: Core revision 20060707
[ 11.316688] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 11.319141] CPU0: AMD Sempron(tm) Processor 3100+ stepping 00
[ 11.319158] Total of 1 processors activated (3618.71 BogoMIPS).
[ 11.319251] ENABLING IO-APIC IRQs
[ 11.319413] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 11.467027] Brought up 1 CPUs
[ 11.467224] Booting paravirtualized kernel on bare hardware
[ 11.467289] Time: 9:40:28 Date: 07/18/107
[ 11.467315] NET: Registered protocol family 16
[ 11.467393] EISA bus registered
[ 11.467396] ACPI: bus type pci registered
[ 11.488271] PCI: PCI BIOS revision 2.10 entry at 0xf2550, last bus=1
[ 11.488273] PCI: Using configuration type 1
[ 11.488275] Setting up standard PCI resources
[ 11.496731] ACPI: Interpreter enabled
[ 11.496735] ACPI: Using IOAPIC for interrupt routing
[ 11.497363] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 11.497368] PCI: Probing PCI hardware (bus 00)
[ 11.497457] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[ 11.498100] Boot video device is 0000:01:00.0
[ 11.498160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 11.528255] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[ 11.528542] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[ 11.528825] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[ 11.529108] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[ 11.529389] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 11.529670] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 11.529949] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 11.530229] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 11.531870] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 11.531879] pnp: PnP ACPI init
[ 11.534493] pnp: PnP ACPI: found 10 devices
[ 11.534497] PnPBIOS: Disabled by ACPI PNP
[ 11.534540] PCI: Using ACPI for IRQ routing
[ 11.534544] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 11.540305] NET: Registered protocol family 8
[ 11.540307] NET: Registered protocol family 20
[ 11.540876] PCI: Bridge: 0000:00:01.0
[ 11.540879] IO window: a000-afff
[ 11.540884] MEM window: e4000000-e5ffffff
[ 11.540887] PREFETCH window: d0000000-dfffffff
[ 11.540918] NET: Registered protocol family 2
[ 11.579019] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 11.579179] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 11.580240] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 11.580788] TCP: Hash tables configured (established 131072 bind 65536)
[ 11.580792] TCP reno registered
[ 11.591066] checking if image is initramfs... it is
[ 12.200161] Freeing initrd memory: 6786k freed
[ 12.200536] audit: initializing netlink socket (disabled)
[ 12.200548] audit(1187430028.416:1): initialized
[ 12.200603] highmem bounce pool size: 64 pages
[ 12.200657] VFS: Disk quotas dquot_6.5.1
[ 12.200676] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 12.200723] io scheduler noop registered
[ 12.200726] io scheduler anticipatory registered
[ 12.200728] io scheduler deadline registered
[ 12.200735] io scheduler cfq registered (default)
[ 12.200957] isapnp: Scanning for PnP cards...
[ 12.554206] isapnp: No Plug & Play device found
[ 12.576845] Real Time Clock Driver v1.12ac
[ 12.576883] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 12.576984] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 12.577576] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 12.577772] mice: PS/2 mouse device common for all mice
[ 12.578194] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 12.578359] input: Macintosh mouse button emulation as /class/input/input0
[ 12.578385] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 12.578388] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 12.578610] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[ 12.578613] PNP: PS/2 controller doesn't have AUX irq; using default 12
[ 12.834825] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 12.834945] EISA: Probing bus 0 at eisa.0
[ 12.834953] Cannot allocate resource for EISA slot 1
[ 12.834962] Cannot allocate resource for EISA slot 4
[ 12.834976] EISA: Detected 0 cards.
[ 12.865044] TCP cubic registered
[ 12.865051] NET: Registered protocol family 1
[ 12.865070] Using IPI No-Shortcut mode
[ 12.865125] ACPI: (supports S0 S1 S3 S4 S5)
[ 12.865166] Magic number: 3:450:677
[ 12.865524] Freeing unused kernel memory: 328k freed
[ 12.866451] Time: tsc clocksource has been installed.
[ 12.883803] input: AT Translated Set 2 keyboard as /class/input/input1
[ 14.112838] Capability LSM initialized
[ 14.152271] ACPI: Fan [FAN] (on)
[ 14.161124] ACPI: Thermal Zone [THRM] (40 C)
[ 14.704798] SCSI subsystem initialized
[ 14.709134] libata version 2.20 loaded.
[ 14.710379] pata_sis 0000:00:02.5: version 0.5.1
[ 14.710450] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[ 14.710475] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[ 14.710492] scsi0 : pata_sis
[ 14.740826] usbcore: registered new interface driver usbfs
[ 14.740850] usbcore: registered new interface driver hub
[ 14.740868] usbcore: registered new device driver usb
[ 14.769901] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 14.805649] ieee1394: Initialized config rom entry `ip1394'
[ 14.819000] sis900.c: v1.08.10 Apr. 2 2006
[ 14.927615] ata1.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[ 14.927621] ata1.00: ATA-7: ST3300620A, 3.AAE, max UDMA/100
[ 14.927624] ata1.00: 586072368 sectors, multi 16: LBA48
[ 14.994190] ata1.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[ 14.994196] ata1.00: configured for UDMA/100
[ 14.994207] scsi1 : pata_sis
[ 15.164614] ATA: abnormal status 0x7F on port 0x00010177
[ 15.175668] ATA: abnormal status 0x7F on port 0x00010177
[ 15.345662] ata2.01: ATAPI, max UDMA/66
[ 15.517597] ata2.01: configured for UDMA/66
[ 15.517707] scsi 0:0:0:0: Direct-Access ATA ST3300620A 3.AA PQ: 0 ANSI: 5
[ 15.518465] scsi 1:0:1:0: CD-ROM DVDRW IDE1008 0055 PQ: 0 ANSI: 5
[ 15.523696] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[ 15.523709] PCI: Setting latency timer of device 0000:00:03.0 to 64
[ 15.523713] ohci_hcd 0000:00:03.0: OHCI Host Controller
[ 15.523817] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[ 15.523833] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe700b000
[ 15.540389] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[ 15.540401] sda: Write Protect is off
[ 15.540404] sda: Mode Sense: 00 3a 00 00
[ 15.540416] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 15.540462] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[ 15.540470] sda: Write Protect is off
[ 15.540472] sda: Mode Sense: 00 3a 00 00
[ 15.540483] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 15.540486] sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[ 15.583483] hub 1-0:1.0: USB hub found
[ 15.583493] hub 1-0:1.0: 3 ports detected
[ 15.585586] sda5 >
[ 15.586041] sd 0:0:0:0: Attached scsi disk sda
[ 15.590683] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 15.590799] sr 1:0:1:0: Attached scsi generic sg1 type 5
[ 15.610890] sr0: scsi3-mmc drive: 1x/40x writer cd/rw xa/form2 cdda tray
[ 15.610895] Uniform CD-ROM driver Revision: 3.20
[ 15.611112] sr 1:0:1:0: Attached scsi CD-ROM sr0
[ 15.689419] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 17
[ 15.689435] PCI: Setting latency timer of device 0000:00:03.1 to 64
[ 15.689439] ohci_hcd 0000:00:03.1: OHCI Host Controller
[ 15.689461] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[ 15.689476] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe700c000
[ 15.751360] usb usb2: configuration #1 chosen from 1 choice
[ 15.751386] hub 2-0:1.0: USB hub found
[ 15.751395] hub 2-0:1.0: 3 ports detected
[ 15.768118] Attempting manual resume
[ 15.768122] swsusp: Resume From Partition 8:5
[ 15.768124] PM: Checking swsusp image.
[ 15.768326] PM: Resume from disk failed.
[ 15.785567] EXT3-fs: INFO: recovery required on readonly filesystem.
[ 15.785571] EXT3-fs: write access will be enabled during recovery.
[ 15.857356] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[ 15.857372] PCI: Setting latency timer of device 0000:00:03.2 to 64
[ 15.857376] ohci_hcd 0000:00:03.2: OHCI Host Controller
[ 15.857397] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[ 15.857413] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe7008000
[ 15.919287] usb usb3: configuration #1 chosen from 1 choice
[ 15.919311] hub 3-0:1.0: USB hub found
[ 15.919321] hub 3-0:1.0: 2 ports detected
[ 15.997182] usb 1-3: new full speed USB device using ohci_hcd and address 2
[ 16.025355] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 19
[ 16.078728] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19] MMIO=[e700e000-e700e7ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 16.084133] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[ 16.085021] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[ 16.094326] 0000:00:04.0: Using transceiver found at address 1 as default
[ 16.094965] eth0: SiS 900 PCI Fast Ethernet at 0xb800, IRQ 20, 00:13:d4:19:80:11.
[ 16.095045] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
[ 16.095054] ehci_hcd 0000:00:03.3: EHCI Host Controller
[ 16.095077] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[ 16.095107] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[ 16.095118] ehci_hcd 0000:00:03.3: irq 21, io mem 0xe7009000
[ 16.095125] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 16.095197] usb usb4: configuration #1 chosen from 1 choice
[ 16.095222] hub 4-0:1.0: USB hub found
[ 16.095229] hub 4-0:1.0: 8 ports detected
[ 16.201286] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 22
[ 16.201293] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[ 16.201299] 0000:00:09.0: 3Com PCI 3c905 Boomerang 100baseTx at 0001d400.
[ 16.222760] sata_sis 0000:00:05.0: version 0.7
[ 16.222774] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[ 16.222783] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[ 16.223133] ata3: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001c002 bmdma 0x0001cc00 irq 22
[ 16.223158] ata4: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c802 bmdma 0x0001cc08 irq 22
[ 16.223174] scsi2 : sata_sis
[ 16.536970] ata3: SATA link down (SStatus 0 SControl 300)
[ 16.547486] ATA: abnormal status 0x7F on port 0x0001bc07
[ 16.547567] scsi3 : sata_sis
[ 16.592041] kjournald starting. Commit interval 5 seconds
[ 16.592054] EXT3-fs: recovery complete.
[ 16.602334] EXT3-fs: mounted filesystem with ordered data mode.
[ 16.860842] ata4: SATA link down (SStatus 0 SControl 300)
[ 16.871358] ATA: abnormal status 0x7F on port 0x0001c407
[ 17.080753] usb 2-2: new low speed USB device using ohci_hcd and address 2
[ 17.300621] usb 2-2: configuration #1 chosen from 1 choice
[ 17.376764] ieee1394: Host added: ID:BUS[0-00:1023] GUID[0011d800003c30a1]
[ 17.608547] usb 1-3: new full speed USB device using ohci_hcd and address 3
[ 17.816376] usb 1-3: configuration #1 chosen from 1 choice
[ 24.406387] eth1: setting full-duplex.
[ 24.426109] eth0: Media Link Off
[ 25.577208] NET: Registered protocol family 17
[ 25.874625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 25.876366] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 26.284426] Linux agpgart interface v0.102 (c) Dave Jones
[ 26.361988] agpgart: Detected AGP bridge 0
[ 26.363962] agpgart: AGP aperture is 64M @ 0xe0000000
[ 26.791269] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 19
[ 26.791275] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[ 26.791281] RT61: Vendor = 0x1814, Product = 0x0301
[ 26.894582] input: PC Speaker as /class/input/input2
[ 27.034798] usbcore: registered new interface driver libusual
[ 27.043922] usbcore: registered new interface driver hiddev
[ 27.059316] parport: PnPBIOS parport detected.
[ 27.059365] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 27.065148] Initializing USB Mass Storage driver...
[ 27.223407] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[ 27.234808] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /class/input/input3
[ 27.234884] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:03.1-2
[ 27.234948] scsi4 : SCSI emulation for USB Mass Storage devices
[ 27.234997] usbcore: registered new interface driver usb-storage
[ 27.235001] USB Mass Storage support registered.
[ 27.235113] usbcore: registered new interface driver usbhid
[ 27.235116] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 27.235551] usb-storage: device found at 3
[ 27.235553] usb-storage: waiting for device to settle before scanning
[ 27.544524] intel8x0_measure_ac97_clock: measured 57948 usecs
[ 27.544528] intel8x0: clocking to 48000
[ 27.710417] fuse init (API version 7.
[ 27.728288] lp0: using parport0 (interrupt-driven).
[ 27.784353] Adding 4554388k swap on /dev/disk/by-uuid/e0da9d15-9e3b-4a12-a153-fa8c52632a92. Priority:-1 extents:1 across:4554388k
[ 27.965271] EXT3 FS on sda1, internal journal
[ 29.542073] NET: Registered protocol family 10
[ 29.542151] lo: Disabled Privacy Extensions
[ 29.542201] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 32.137089] input: Power Button (FF) as /class/input/input4
[ 32.141510] ACPI: Power Button (FF) [PWRF]
[ 32.175328] input: Power Button (CM) as /class/input/input5
[ 32.179662] ACPI: Power Button (CM) [PWRB]
[ 32.212898] input: Sleep Button (CM) as /class/input/input6
[ 32.217298] ACPI: Sleep Button (CM) [FUTS]
[ 32.236282] usb-storage: device scan complete
[ 32.244283] scsi 4:0:0:0: Direct-Access Generic USB SD Reader 1.00 PQ: 0 ANSI: 0
[ 32.245166] ibm_acpi: ec object not found
[ 32.250277] scsi 4:0:0:1: Direct-Access Generic USB CF Reader 1.01 PQ: 0 ANSI: 0
[ 32.258281] scsi 4:0:0:2: Direct-Access Generic USB SM Reader 1.02 PQ: 0 ANSI: 0
[ 32.265271] scsi 4:0:0:3: Direct-Access Generic USB MS Reader 1.03 PQ: 0 ANSI: 0
[ 32.278300] sd 4:0:0:0: Attached scsi removable disk sdb
[ 32.278336] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 32.286541] No dock devices found.
[ 32.289297] sd 4:0:0:1: Attached scsi removable disk sdc
[ 32.289337] sd 4:0:0:1: Attached scsi generic sg3 type 0
[ 32.300300] sd 4:0:0:2: Attached scsi removable disk sdd
[ 32.300337] sd 4:0:0:2: Attached scsi generic sg4 type 0
[ 32.310672] sd 4:0:0:3: Attached scsi removable disk sde
[ 32.310709] sd 4:0:0:3: Attached scsi generic sg5 type 0
[ 32.487696] Using specific hotkey driver
[ 32.639425] pcc_acpi: loading...
[ 32.885799] powernow-k8: Found 1 AMD Sempron(tm) Processor 3100+ processors (version 2.00.00)
[ 32.885843] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[ 32.885846] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[ 32.885849] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[ 32.885852] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[ 32.885855] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[ 32.885858] powernow-k8: 0 : fid 0xa (1800 MHz), vid 0x6
[ 36.578578] RT61: RfIcType= 3
[ 38.153607] ppdev: user-space parallel port driver
[ 39.051921] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[ 39.051926] apm: overridden by ACPI.
[ 39.311070] Bluetooth: Core ver 2.11
[ 39.311116] NET: Registered protocol family 31
[ 39.311119] Bluetooth: HCI device and connection manager initialized
[ 39.311122] Bluetooth: HCI socket layer initialized
[ 39.417287] Bluetooth: L2CAP ver 2.8
[ 39.417291] Bluetooth: L2CAP socket layer initialized
[ 40.470795] Bluetooth: RFCOMM socket layer initialized
[ 40.470809] Bluetooth: RFCOMM TTY layer initialized
[ 40.470811] Bluetooth: RFCOMM ver 1.8
[ 54.521649] eth1: no IPv6 routers present

---

