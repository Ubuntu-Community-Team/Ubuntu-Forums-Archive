---
title: "Kubuntu hard freezes randomly - needs clues"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by babysteps on 2007-08-11
I have finally gotten my laptop to go on line! 

Then it would hard freeze so that nothing short of unplugging the cable will shut down.  

could someone read my dmesg and see if they can tell me what's going on? 


[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff3800 (reserved)
[17179569.184000]  BIOS-e820: 000000000fff3800 - 0000000010000000 (ACPI NVS)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f9970
[17179569.184000] ACPI: RSDT (v001 COMPAQ RSDTBL   0x00000001 CPQ  0x00000001) @ 0x0fff4800
[17179569.184000] ACPI: FADT (v001 COMPAQ CPQB151  0x20001117 CPQ  0x00000001) @ 0x0fff4828
[17179569.184000] ACPI: DSDT (v001 COMPAQ ARMADAE7 0x00010000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:f0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 597.030 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.724000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.724000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.752000] Memory: 249140k/262080k available (1976k kernel code, 12352k reserved, 606k data, 288k init, 0k highmem)
[17179571.752000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.836000] Calibrating delay using timer specific routine.. 1195.10 BogoMIPS (lpj=2390200)
[17179571.836000] Security Framework v1.0.0 initialized
[17179571.836000] SELinux:  Disabled at boot.
[17179571.836000] Mount-cache hash table entries: 512
[17179571.836000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.836000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.836000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179571.836000] CPU: L2 cache: 128K
[17179571.836000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179571.836000] mtrr: v2.0 (20020519)
[17179571.836000] CPU: Intel Celeron (Coppermine) stepping 03
[17179571.836000] Enabling fast FPU save and restore... done.
[17179571.836000] Enabling unmasked SIMD FPU exception support... done.
[17179571.836000] Checking 'hlt' instruction... OK.
[17179571.852000] checking if image is initramfs... it is
[17179574.376000] Freeing initrd memory: 6614k freed
[17179574.416000] ACPI: Looking for DSDT ... not found!
[17179574.424000] ACPI: setting ELCR to 0200 (from 0800)
[17179574.428000] NET: Registered protocol family 16
[17179574.428000] EISA bus registered
[17179574.428000] ACPI: bus type pci registered
[17179574.428000] PCI: PCI BIOS revision 2.10 entry at 0xf0478, last bus=1
[17179574.428000] PCI: Using configuration type 1
[17179574.432000] ACPI: Subsystem revision 20051216
[17179574.460000] ACPI: Interpreter enabled
[17179574.460000] ACPI: Using PIC for interrupt routing
[17179574.460000] ACPI: PCI Root Bridge [C005] (0000:00)
[17179574.460000] PCI: Probing PCI hardware (bus 00)
[17179574.460000] ACPI: Assume root bridge [\_SB_.C005] bus is 0
[17179574.484000] PCI quirk: region 5000-503f claimed by PIIX4 ACPI
[17179574.484000] PCI quirk: region 4000-400f claimed by PIIX4 SMB
[17179574.484000] PIIX4 devres C PIO at 0100-0107
[17179574.484000] PIIX4 devres I PIO at 00e0-00e3
[17179574.484000] PIIX4 devres J PIO at 00f8-00fb
[17179574.484000] Boot video device is 0000:01:00.0
[17179574.484000] ACPI: PCI Interrupt Routing Table [\_SB_.C005._PRT]
[17179574.520000] ACPI: Power Resource [C138] (on)
[17179574.524000] ACPI: Power Resource [C0F3] (on)
[17179574.536000] ACPI: Power Resource [C1A5] (on)
[17179574.536000] ACPI: Power Resource [C1AB] (off)
[17179574.540000] ACPI: PCI Interrupt Link [C151] (IRQs *11)
[17179574.544000] ACPI: PCI Interrupt Link [C157] (IRQs 11) *0, disabled.
[17179574.544000] ACPI: PCI Interrupt Link [C158] (IRQs *11)
[17179574.544000] ACPI: PCI Interrupt Link [C159] (IRQs *11)
[17179574.548000] ACPI: Power Resource [C16D] (off)
[17179574.552000] ACPI: Power Resource [C16F] (off)
[17179574.556000] ACPI: Power Resource [C171] (off)
[17179574.556000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.556000] pnp: PnP ACPI init
[17179574.588000] pnp: PnP ACPI: found 15 devices
[17179574.588000] PnPBIOS: Disabled by ACPI PNP
[17179574.588000] PCI: Using ACPI for IRQ routing
[17179574.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.624000] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[17179574.624000] pnp: 00:0c: ioport range 0x800-0x87f has been reserved
[17179574.624000] pnp: 00:0c: ioport range 0x4000-0x400f has been reserved
[17179574.624000] pnp: 00:0c: ioport range 0x5000-0x5063 could not be reserved
[17179574.624000] pnp: 00:0c: ioport range 0x6004-0x6005 could not be reserved
[17179574.624000] pnp: 00:0c: ioport range 0xf000-0xf0cf has been reserved
[17179574.624000] PCI: Bridge: 0000:00:01.0
[17179574.624000]   IO window: 1000-1fff
[17179574.624000]   MEM window: 40000000-410fffff
[17179574.624000]   PREFETCH window: 28000000-280fffff
[17179574.624000] PCI: Bus 2, cardbus bridge: 0000:00:04.0
[17179574.624000]   IO window: 00002c00-00002cff
[17179574.624000]   IO window: 00003000-000030ff
[17179574.624000]   PREFETCH window: 20000000-21ffffff
[17179574.624000]   MEM window: 22000000-23ffffff
[17179574.624000] PCI: Bus 6, cardbus bridge: 0000:00:04.1
[17179574.624000]   IO window: 00003400-000034ff
[17179574.624000]   IO window: 00003800-000038ff
[17179574.624000]   PREFETCH window: 24000000-25ffffff
[17179574.624000]   MEM window: 26000000-27ffffff
[17179574.624000] **** SET: Misaligned resource pointer: ce9d15e2 Type 07 Len 0
[17179574.624000] ACPI: PCI Interrupt Link [C151] enabled at IRQ 11
[17179574.624000] PCI: setting IRQ 11 as level-triggered
[17179574.624000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [C151] -> GSI 11 (level, low) -> IRQ 11
[17179574.624000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [C151] -> GSI 11 (level, low) -> IRQ 11
[17179574.628000] audit: initializing netlink socket (disabled)
[17179574.628000] audit(1186516219.628:1): initialized
[17179574.628000] VFS: Disk quotas dquot_6.5.1
[17179574.628000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.628000] Initializing Cryptographic API
[17179574.628000] io scheduler noop registered
[17179574.628000] io scheduler anticipatory registered
[17179574.628000] io scheduler deadline registered
[17179574.628000] io scheduler cfq registered
[17179574.628000] Limiting direct PCI/PCI transfers.
[17179574.628000] isapnp: Scanning for PnP cards...
[17179574.980000] isapnp: No Plug & Play device found
[17179575.044000] PNP: PS/2 Controller [PNP0303:C0F0,PNP0f0e:C0F1] at 0x60,0x64 irq 1,12
[17179575.044000] i8042.c: Detected active multiplexing controller, rev 1.0.
[17179575.044000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179575.044000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179575.048000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179575.048000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179575.048000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.048000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179575.048000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.048000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179575.056000] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.056000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179575.056000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.056000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179575.056000] mice: PS/2 mouse device common for all mice
[17179575.060000] EISA: Probing bus 0 at eisa.0
[17179575.060000] Cannot allocate resource for EISA slot 1
[17179575.060000] Cannot allocate resource for EISA slot 2
[17179575.060000] Cannot allocate resource for EISA slot 3
[17179575.060000] Cannot allocate resource for EISA slot 4
[17179575.060000] Cannot allocate resource for EISA slot 5
[17179575.060000] Cannot allocate resource for EISA slot 6
[17179575.060000] EISA: Detected 0 cards.
[17179575.060000] NET: Registered protocol family 2
[17179575.092000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.096000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179575.096000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.096000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.096000] TCP: Hash tables configured (established 16384 bind 16384)
[17179575.096000] TCP reno registered
[17179575.096000] TCP bic registered
[17179575.096000] NET: Registered protocol family 1
[17179575.096000] NET: Registered protocol family 8
[17179575.096000] NET: Registered protocol family 20
[17179575.096000] Using IPI Shortcut mode
[17179575.096000] ACPI wakeup devices:
[17179575.096000] C0B4 C0B5 C0B6 C0B7 C0B8 C0B9 C0BA C0BB C0BC C0BD C0BE C0BF C0C0 C0C1 C0C2 C0C3 C0C4 C0C5 C0C6 C0C7 C0C8 C0C9 C0CA C0CB C11B C11E C13A C13B C13C C13D C13E C13F C140 C141 C15A C197 C1A6 C057 C179
[17179575.096000] ACPI: (supports S0 S1 S3 S4 S5)
[17179575.096000] Freeing unused kernel memory: 288k freed
[17179575.268000] vga16fb: initializing
[17179575.268000] vga16fb: mapped to 0xc00a0000
[17179575.384000] Console: switching to colour frame buffer device 80x25
[17179575.384000] fb0: VGA16 VGA frame buffer device
[17179576.504000] Capability LSM initialized
[17179576.612000] ACPI: Fan [C16B] (off)
[17179576.612000] ACPI: Fan [C16E] (off)
[17179576.616000] ACPI: Fan [C170] (off)
[17179576.628000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179576.628000] ACPI: Processor [C0CC] (supports 8 throttling states)
[17179576.644000] ACPI: Thermal Zone [C16C] (30 C)
[17179578.240000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179578.240000] PIIX4: chipset revision 1
[17179578.240000] PIIX4: not 100% native mode: will probe irqs later
[17179578.240000]     ide0: BM-DMA at 0x2420-0x2427, BIOS settings: hda:DMA, hdb:pio
[17179578.240000] Probing IDE interface ide0...
[17179578.528000] hda: WDC WD800VE-00HDT0, ATA DISK drive
[17179578.976000] hdb: Compaq DVD-ROM SD-C2402, ATAPI CD/DVD-ROM drive
[17179579.032000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.108000] hda: max request size: 128KiB
[17179579.132000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[17179579.136000] hda: cache flushes supported
[17179579.136000]  hda: hda1 hda2 < hda5 >
[17179579.188000] hdb: ATAPI 24X DVD-ROM drive, 128kB Cache, DMA
[17179579.188000] Uniform CD-ROM driver Revision: 3.20
[17179579.676000] usbcore: registered new driver usbfs
[17179579.676000] usbcore: registered new driver hub
[17179579.680000] USB Universal Host Controller Interface driver v2.3
[17179579.684000] **** SET: Misaligned resource pointer: cfc705e2 Type 07 Len 0
[17179579.684000] ACPI: PCI Interrupt Link [C159] enabled at IRQ 11
[17179579.684000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [C159] -> GSI 11 (level, low) -> IRQ 11
[17179579.684000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179579.684000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179579.684000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00002400
[17179579.684000] hub 1-0:1.0: USB hub found
[17179579.684000] hub 1-0:1.0: 2 ports detected
[17179579.836000] Probing IDE interface ide1...
[17179580.512000] Attempting manual resume
[17179580.548000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179580.548000] EXT3-fs: write access will be enabled during recovery.
[17179584.216000] EXT3-fs: hda1: orphan cleanup on readonly fs
[17179584.216000] ext3_orphan_cleanup: deleting unreferenced inode 9340284
[17179584.216000] EXT3-fs: hda1: 1 orphan inode deleted
[17179584.216000] EXT3-fs: recovery complete.
[17179584.216000] kjournald starting.  Commit interval 5 seconds
[17179584.224000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.224000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [C151] -> GSI 11 (level, low) -> IRQ 11
[17179599.224000] Yenta: CardBus bridge found at 0000:00:04.0 [0e11:b121]
[17179599.224000] Yenta: Enabling burst memory read transactions
[17179599.224000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179599.224000] Yenta: Routing CardBus interrupts to PCI
[17179599.224000] Yenta TI: socket 0000:00:04.0, mfunc 0x01001c72, devctl 0x64
[17179599.236000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179599.260000] Linux agpgart interface v0.101 (c) Dave Jones
[17179599.264000] agpgart: Detected an Intel 440BX Chipset.
[17179599.272000] agpgart: AGP aperture is 64M @ 0x50000000
[17179599.456000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179599.456000] Socket status: 30000020
[17179599.456000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [C151] -> GSI 11 (level, low) -> IRQ 11
[17179599.456000] Yenta: CardBus bridge found at 0000:00:04.1 [0e11:b121]
[17179599.456000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179599.456000] Yenta: Routing CardBus interrupts to PCI
[17179599.456000] Yenta TI: socket 0000:00:04.1, mfunc 0x01001c72, devctl 0x64
[17179599.688000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179599.688000] Socket status: 30000006
[17179599.688000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.688000] ltmodem: module license 'Proprietary' taints kernel.
[17179599.712000] Loading Lucent Modem Controller driver version 8.26-alk-8
[17179599.716000] **** SET: Misaligned resource pointer: cfd2b402 Type 07 Len 0
[17179599.716000] ACPI: PCI Interrupt Link [C158] enabled at IRQ 11
[17179599.716000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [C158] -> GSI 11 (level, low) -> IRQ 11
[17179599.720000] Detected Parameters Irq=11 BaseAddress=0x2800 ComAddress=0x2430
[17179599.720000] ttyLTM0 at I/O 0x2800 (irq = 11) is a Lucent/Agere Modem
[17179600.108000] pccard: CardBus card inserted into slot 0
[17179600.144000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179600.876000] input: PS/2 Generic Mouse as /class/input/input1
[17179601.320000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [C158] -> GSI 11 (level, low) -> IRQ 11
[17179601.380000] Floppy drive(s): fd0 is 1.44M
[17179601.396000] FDC 0 is a post-1991 82077
[17179601.608000] Synaptics Touchpad, model: 1, fw: 5.6, id: 0x165eb1, caps: 0x804713/0x0
[17179601.660000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179601.924000] es1968: clocking to 48000
[17179601.960000] input: PC Speaker as /class/input/input3
[17179601.972000] parport: PnPBIOS parport detected.
[17179601.972000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179601.996000] Real Time Clock Driver v1.12
[17179603.040000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[17179603.040000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179603.040000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.040000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.040000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.100000] ts: Compaq touchscreen protocol output
[17179603.108000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[17179603.112000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179603.112000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.112000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.112000] cs: IO port probe 0xa00-0xaff: clean.
[17179605.164000] lp0: using parport0 (interrupt-driven).
[17179605.244000] ndiswrapper version 1.47 loaded (smp=no)
[17179605.312000] ndiswrapper: driver mrv8000c (Marvell,02/22/2005,3.1.1.7) loaded
[17179605.312000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179605.312000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [C151] -> GSI 11 (level, low) -> IRQ 11
[17179605.312000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179605.320000] ndiswrapper: using IRQ 11
[17179605.596000] wlan0: ethernet device 00:18:4d:ee:d4:65 using NDIS driver: mrv8000c, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[17179605.596000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179605.596000] usbcore: registered new driver ndiswrapper
[17179605.764000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179605.956000] EXT3 FS on hda1, internal journal
[17179606.336000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179606.336000] md: bitmap version 4.39
[17179607.116000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179607.916000] cdrom: open failed.
[17179609.232000] pnp: Device 00:03 disabled.
[17179609.232000] **** SET: Misaligned resource pointer: cfad4242 Type 04 Len 42
[17179609.232000] **** SET: Misaligned resource pointer: cfad42c6 Type 01 Len 42
[17179609.240000] pnp: Device 00:03 activated.
[17179609.360000] irda_init()
[17179609.360000] NET: Registered protocol family 23
[17179609.412000] found SMC SuperIO Chip (devid=0x0a rev=00 base=0x00e0): FDC37N971
[17179609.412000] SMsC IrDA Controller found
[17179609.412000]  IrCC version 2.0, firport 0x100, sirport 0x3e8 dma=4, irq=3
[17179609.412000] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[17179609.412000] No transceiver found. Defaulting to Fast pin select
[17179609.416000] IrDA: Registered device irda0
[17179611.464000] ACPI: AC Adapter [C10E] (on-line)
[17179611.472000] ACPI: Battery Slot [C116] (battery absent)
[17179611.472000] ACPI: Battery Slot [C117] (battery absent)
[17179611.472000] ACPI: Battery Slot [C118] (battery absent)
[17179611.716000] ACPI: Power Button (FF) [PWRF]
[17179611.716000] ACPI: Sleep Button (CM) [C057]
[17179611.716000] ACPI: Lid Switch [C179]
[17179612.052000] ibm_acpi: ec object not found
[17179612.144000] pcc_acpi: loading...
[17179616.288000] ppdev: user-space parallel port driver
[17179616.868000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179616.868000] apm: overridden by ACPI.
[17179621.812000] smsc_ircc_change_speed() changing speed to: 9600
[17179621.812000] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[17179621.812000] irlap_change_speed(), setting speed to 9600
[17179621.812000] smsc_ircc_net_open(), unable to allocate DMA=4
[17179623.440000] Bluetooth: Core ver 2.8
[17179623.440000] NET: Registered protocol family 31
[17179623.440000] Bluetooth: HCI device and connection manager initialized
[17179623.440000] Bluetooth: HCI socket layer initialized
[17179623.480000] Bluetooth: L2CAP ver 2.8
[17179623.480000] Bluetooth: L2CAP socket layer initialized
[17179623.516000] Bluetooth: RFCOMM socket layer initialized
[17179623.516000] Bluetooth: RFCOMM TTY layer initialized
[17179623.516000] Bluetooth: RFCOMM ver 1.7


thanks!

Babysteps

---

### Post by SOULRiDER on 2007-08-11
Does it slow down before it freezes? Do you get any sympthoms or it just freezes randomly? See if you can monitor the RAM and SWAP usage and see what it is when it freezes.

---

