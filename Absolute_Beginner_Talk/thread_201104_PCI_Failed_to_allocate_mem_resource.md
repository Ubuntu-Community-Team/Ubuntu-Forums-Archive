---
title: "PCI: Failed to allocate mem resource"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-21
I have acpi=off noacpi noapic nolapic pci=routeirq in boot options.  But regardless, even with or without those I always get this when starting up:

```
From dmesg:
[   18.023742] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.0
[   18.023791] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.1
```

What is this and is there a way to rectify/get rid of it?

thanks

Edit: here is the full dmesg output if anyone needs it.  plus this is on an HP zv5260us notebook
```
[17179569.184000] Linux version 2.6.15-25-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 130928
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126832 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda5 ro quiet splash acpi=off noapic pci=routeirq noacpi nolapic noapm
[17179569.184000] mapped APIC to ffffd000 (014c1000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 1995.006 MHz processor.
[   17.397061] Using tsc for high-res timesource
[   17.398625] Console: colour VGA+ 80x25
[   17.399253] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.399784] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.409611] Memory: 507252k/523712k available (2094k kernel code, 15912k reserved, 597k data, 332k init, 0k highmem)
[   17.409614] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.485758] Calibrating delay using timer specific routine.. 3994.10 BogoMIPS (lpj=7988207)
[   17.485794] Security Framework v1.0.0 initialized
[   17.485800] SELinux:  Disabled at boot.
[   17.485814] Mount-cache hash table entries: 512
[   17.485896] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   17.485902] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   17.485909] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.485911] CPU: L2 Cache: 1024K (64 bytes/line)
[   17.485913] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   17.485924] mtrr: v2.0 (20020519)
[   17.485927] Enabling fast FPU save and restore... done.
[   17.485929] Enabling unmasked SIMD FPU exception support... done.
[   17.485933] Checking 'hlt' instruction... OK.
[   17.501825] SMP alternatives: switching to UP code
[   17.502026] checking if image is initramfs... it is
[   18.007839] Freeing initrd memory: 6765k freed
[   18.015294] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 0a
[   18.015300] SMP motherboard not detected.
[   18.015302] Local APIC not detected. Using dummy APIC emulation.
[   18.015357] Brought up 1 CPUs
[   18.015602] NET: Registered protocol family 16
[   18.015627] EISA bus registered
[   18.015747] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[   18.015754] PCI: Using configuration type 1
[   18.016065] ACPI: Subsystem revision 20051216
[   18.016066] ACPI: Interpreter disabled.
[   18.016070] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.016076] pnp: PnP ACPI: disabled
[   18.016079] PnPBIOS: Scanning system for PnP BIOS support...
[   18.016086] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7280
[   18.016088] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71d, dseg 0x400
[   18.017840] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   18.017849] PCI: Probing PCI hardware
[   18.017852] PCI: Probing PCI hardware (bus 00)
[   18.018513] Boot video device is 0000:01:00.0
[   18.019020] PCI: Using IRQ router default [10de/00d0] at 0000:00:01.0
[   18.023611] pnp: 00:09: ioport range 0xfe00-0xfe01 has been reserved
[   18.023742] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.0
[   18.023791] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.1
[   18.023837] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   18.023839]   IO window: 00003000-000030ff
[   18.023843]   IO window: 00003400-000034ff
[   18.023846]   PREFETCH window: 30000000-31ffffff
[   18.023849] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[   18.023851]   IO window: 00003800-000038ff
[   18.023854]   IO window: 00003c00-00003cff
[   18.023857]   PREFETCH window: 32000000-33ffffff
[   18.023860] PCI: Bridge: 0000:00:0a.0
[   18.023862]   IO window: 3000-7fff
[   18.023865]   MEM window: e0100000-e17fffff
[   18.023868]   PREFETCH window: 30000000-33ffffff
[   18.023871] PCI: Bridge: 0000:00:0b.0
[   18.023872]   IO window: disabled.
[   18.023876]   MEM window: e2000000-e2ffffff
[   18.023880]   PREFETCH window: f0000000-f80fffff
[   18.023888] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   18.024182] audit: initializing netlink socket (disabled)
[   18.024189] audit(1150876717.988:1): initialized
[   18.024268] VFS: Disk quotas dquot_6.5.1
[   18.024283] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.024330] Initializing Cryptographic API
[   18.024334] io scheduler noop registered
[   18.024339] io scheduler anticipatory registered
[   18.024343] io scheduler deadline registered
[   18.024354] io scheduler cfq registered
[   18.024482] isapnp: Scanning for PnP cards...
[   18.378299] isapnp: No Plug & Play device found
[   18.387869] Real Time Clock Driver v1.12
[   18.387988] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   18.396472] i8042.c: Detected active multiplexing controller, rev 1.9.
[   18.402587] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.403519] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.404435] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.405432] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.406142] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.406168] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   18.407647] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.407684] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.407687] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.407818] mice: PS/2 mouse device common for all mice
[   18.408927] EISA: Probing bus 0 at eisa.0
[   18.408934] Cannot allocate resource for EISA slot 1
[   18.408936] Cannot allocate resource for EISA slot 2
[   18.408938] Cannot allocate resource for EISA slot 3
[   18.408940] Cannot allocate resource for EISA slot 4
[   18.408942] Cannot allocate resource for EISA slot 5
[   18.408943] Cannot allocate resource for EISA slot 6
[   18.408945] Cannot allocate resource for EISA slot 7
[   18.408949] EISA: Detected 0 cards.
[   18.409021] NET: Registered protocol family 2
[   18.417378] spurious 8259A interrupt: IRQ7.
[   18.441293] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[   18.441448] TCP established hash table entries: 32768 (order: 6, 393216 bytes)
[   18.441966] TCP bind hash table entries: 32768 (order: 6, 393216 bytes)
[   18.442455] TCP: Hash tables configured (established 32768 bind 32768)
[   18.442458] TCP reno registered
[   18.442548] TCP bic registered
[   18.442555] NET: Registered protocol family 1
[   18.442559] NET: Registered protocol family 8
[   18.442561] NET: Registered protocol family 20
[   18.442577] Using IPI No-Shortcut mode
[   18.442614] Freeing unused kernel memory: 332k freed
[   18.482424] vga16fb: initializing
[   18.482429] vga16fb: mapped to 0xc00a0000
[   18.664493] Console: switching to colour frame buffer device 80x25
[   18.664498] fb0: VGA16 VGA frame buffer device
[   18.961208] input: AT Translated Set 2 keyboard as /class/input/input0
[   19.682583] Capability LSM initialized
[   20.336045] NFORCE3-150: IDE controller at PCI slot 0000:00:08.0
[   20.336061] NFORCE3-150: chipset revision 165
[   20.336063] NFORCE3-150: not 100% native mode: will probe irqs later
[   20.336067] NFORCE3-150: BIOS didn't set cable bits correctly. Enabling workaround.
[   20.336072] NFORCE3-150: 0000:00:08.0 (rev a5) UDMA133 controller
[   20.336082]     ide0: BM-DMA at 0x2080-0x2087, BIOS settings: hda:DMA, hdb:pio
[   20.336092]     ide1: BM-DMA at 0x2088-0x208f, BIOS settings: hdc:DMA, hdd:pio
[   20.336100] Probing IDE interface ide0...
[   20.624062] hda: IC25N080ATMR04-0, ATA DISK drive
[   21.296046] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   21.296172] Probing IDE interface ide1...
[   22.031261] hdc: SD-R6252, ATAPI CD/DVD-ROM drive
[   22.747216] ide1 at 0x170-0x177,0x376 on irq 15
[   22.750683] SCSI subsystem initialized
[   22.751953] libata version 1.20 loaded.
[   22.758174] hda: max request size: 1024KiB
[   22.779561] hda: 156301488 sectors (80026 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[   22.779878] hda: cache flushes supported
[   22.780012]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 hda8 hda9 hda10 >
[   22.912916] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   22.912924] Uniform CD-ROM driver Revision: 3.20
[   23.580959] usbcore: registered new driver usbfs
[   23.581210] usbcore: registered new driver hub
[   23.582153] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   23.582874] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.582877] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   23.785710] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   23.785717] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[   23.840438] hub 1-0:1.0: USB hub found
[   23.840451] hub 1-0:1.0: 3 ports detected
[   23.861074] ieee1394: Initialized config rom entry `ip1394'
[   23.942284] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   23.942289] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   24.144535] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   24.144543] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[   24.200174] hub 2-0:1.0: USB hub found
[   24.200182] hub 2-0:1.0: 3 ports detected
[   24.302939] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   24.302942] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   24.302967] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   24.303115] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   24.303120] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[   24.303125] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.303371] hub 3-0:1.0: USB hub found
[   24.303380] hub 3-0:1.0: 6 ports detected
[   24.406407] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   24.456426] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e0108000-e01087ff]  Max Packet=[2048]
[   24.812266] Attempting manual resume
[   24.851138] ReiserFS: hda5: found reiserfs format "3.6" with standard journal
[   24.912392] ReiserFS: hda5: using ordered data mode
[   24.928756] ReiserFS: hda5: journal params: device hda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   24.929272] ReiserFS: hda5: checking transaction log (hda5)
[   24.962848] ReiserFS: hda5: Using r5 hash to sort names
[   25.157406] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   25.374252] ohci_hcd 0000:00:02.1: wakeup
[   25.757061] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   25.783542] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[463f0200463f0200]
[   32.033624] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x2040
[   32.033639] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   32.130525] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.163903] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.179969] Linux agpgart interface v0.101 (c) Dave Jones
[   32.197355] agpgart: Detected AGP bridge 0
[   32.197368] agpgart: Setting up Nforce3 AGP.
[   32.201435] agpgart: AGP aperture is 128M @ 0xe8000000
[   32.559771] ieee80211_crypt: registered algorithm 'NULL'
[   32.560932] ieee80211: 802.11 data/management/control stack, git-1.1.7
[   32.560934] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   32.596816] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   32.596840] 8139cp: pci dev 0000:02:01.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   32.596843] 8139cp: Try the "8139too" driver instead.
[   32.603129] 8139too Fast Ethernet driver 0.9.27
[   32.603453] eth0: RealTek RTL8139 at 0xe0af0800, 00:0f:b0:02:da:31, IRQ 10
[   32.603455] eth0:  Identified 8139 chip type 'RTL-8101'
[   32.629382] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[   32.629400] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   32.629402]   IO window: 00003000-000030ff
[   32.629406]   IO window: 00003400-000034ff
[   32.629409]   PREFETCH window: 30000000-31ffffff
[   32.629413]   MEM window: e0400000-e07fffff
[   32.629417] Yenta: Enabling burst memory read transactions
[   32.629420] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.629422] Yenta: Routing CardBus interrupts to PCI
[   32.629426] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   32.706724] bcm43xx driver
[   32.738320] usbcore: registered new driver hiddev
[   32.757646] input: Logitech Trackball as /class/input/input1
[   32.757672] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:02.0-1
[   32.766712] input: USBPS2 as /class/input/input2
[   32.766731] input: USB HID v1.00 Keyboard [USBPS2] on usb-0000:00:02.1-1
[   32.777718] input: USBPS2 as /class/input/input3
[   32.777750] input: USB HID v1.00 Mouse [USBPS2] on usb-0000:00:02.1-1
[   32.777759] usbcore: registered new driver usbhid
[   32.777762] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.814626] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   32.829129] input: PS/2 Mouse as /class/input/input4
[   32.853804] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
[   32.861842] Yenta: ISA IRQ mask 0x02f8, PCI irq 11
[   32.861845] Socket status: 30000086
[   32.861848] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   32.861853] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   32.861857] cs: IO port probe 0x3000-0x7fff: clean.
[   32.862707] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   32.862710] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   32.863613] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[   32.863628] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.863630] Yenta: Routing CardBus interrupts to PCI
[   32.863634] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   33.093725] Yenta: ISA IRQ mask 0x02f8, PCI irq 10
[   33.093730] Socket status: 30000006
[   33.093733] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   33.093738] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   33.093742] cs: IO port probe 0x3000-0x7fff: clean.
[   33.094591] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   33.094594] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   33.160349] nvidia: module license 'NVIDIA' taints kernel.
[   33.243793] input: PC Speaker as /class/input/input6
[   33.250687] ts: Compaq touchscreen protocol output
[   33.384932] intel8x0_measure_ac97_clock: measured 55622 usecs
[   33.384936] intel8x0: clocking to 48000
[   33.385622] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[   33.683310] parport: PnPBIOS parport detected.
[   33.683361] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   33.833106] parport0: Printer, Canon BJC-240
[   34.380645] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   34.382364] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   34.383104] cs: IO port probe 0x820-0x8ff: clean.
[   34.383716] cs: IO port probe 0xc00-0xcf7: clean.
[   34.384481] cs: IO port probe 0xa00-0xaff: clean.
[   34.440864] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   34.442578] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   34.443317] cs: IO port probe 0x820-0x8ff: clean.
[   34.443928] cs: IO port probe 0xc00-0xcf7: clean.
[   34.444695] cs: IO port probe 0xa00-0xaff: clean.
[   34.815371] lp0: using parport0 (interrupt-driven).
[   34.838021] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   34.838025] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   34.838027] ieee1394: sbp2: Try serialize_io=0 for better performance
[   34.886562] Adding 506008k swap on /dev/hda6.  Priority:-1 extents:1 across:506008k
[   35.320097] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   35.320101] md: bitmap version 4.39
[   36.166156] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   37.011955] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   37.011961] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[   37.011965] ide: failed opcode was: unknown
[   37.013082] cdrom: open failed.
[   51.038460] kjournald starting.  Commit interval 5 seconds
[   51.038601] EXT3 FS on hda3, internal journal
[   51.038606] EXT3-fs: mounted filesystem with ordered data mode.
[   51.070198] ReiserFS: hda10: found reiserfs format "3.6" with standard journal
[   52.782557] ReiserFS: hda10: using ordered data mode
[   52.807367] ReiserFS: hda10: journal params: device hda10, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   52.807850] ReiserFS: hda10: checking transaction log (hda10)
[   52.833841] ReiserFS: hda10: Using r5 hash to sort names
[   52.960524] NTFS driver 2.1.25 [Flags: R/O MODULE].
[   53.014460] NTFS volume version 3.1.
[   53.060876] NTFS volume version 3.1.
[   53.086460] ReiserFS: hda9: found reiserfs format "3.6" with standard journal
[   53.441890] ReiserFS: hda9: using ordered data mode
[   53.456673] ReiserFS: hda9: journal params: device hda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   53.457211] ReiserFS: hda9: checking transaction log (hda9)
[   53.492419] ReiserFS: hda9: Using r5 hash to sort names
[   53.516551] ReiserFS: hda7: found reiserfs format "3.6" with standard journal
[   54.836432] ReiserFS: hda7: using ordered data mode
[   54.861922] ReiserFS: hda7: journal params: device hda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   54.862427] ReiserFS: hda7: checking transaction log (hda7)
[   54.978763] ReiserFS: hda7: Using r5 hash to sort names
[   55.076238] ReiserFS: hda8: found reiserfs format "3.6" with standard journal
[   55.729863] ReiserFS: hda8: using ordered data mode
[   55.771998] ReiserFS: hda8: journal params: device hda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   55.772440] ReiserFS: hda8: checking transaction log (hda8)
[   55.929577] ReiserFS: hda8: Using r5 hash to sort names
[   63.319653] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   63.324024] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   64.055749] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   65.183892] ppdev: user-space parallel port driver
[   65.512436] apm: BIOS not found.
[   68.795462] Bluetooth: Core ver 2.8
[   68.795467] NET: Registered protocol family 31
[   68.795469] Bluetooth: HCI device and connection manager initialized
[   68.795479] Bluetooth: HCI socket layer initialized
[   68.817436] Bluetooth: L2CAP ver 2.8
[   68.817441] Bluetooth: L2CAP socket layer initialized
[   68.819607] Bluetooth: RFCOMM socket layer initialized
[   68.819618] Bluetooth: RFCOMM TTY layer initialized
[   68.819620] Bluetooth: RFCOMM ver 1.7
[  170.539967] CSLIP: code copyright 1989 Regents of the University of California
[  170.549281] PPP generic driver version 2.4.2
[  170.607841] NET: Registered protocol family 10
[  170.607975] lo: Disabled Privacy Extensions
[  170.608049] IPv6 over IPv4 tunneling driver
[  174.458282] PPP BSD Compression module registered
[  174.502104] PPP Deflate Compression module registered
```

---

### Post by unisol on 2006-07-06
i get a similar message Pci: failed to allocate mem resources is this from adding a new piece of hardware that is not recognized by the system or because the driver wasnt installed

---

### Post by Frank Golden on 2006-07-06
sorry for double post

---

### Post by Frank Golden on 2006-07-06
I get the same message (it flashes for about a half second at bootup).
It doesn't appear to cause any problems with my Acer Aspire 5672 so I 
ignore it. If it required input from me, well that's another story.
Maybe it's a bug in the present Ubuntu kernel. My machine uses PCI Express
maybe it's a legacy thing. Dunno.

---

