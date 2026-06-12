---
title: "ps/2 to usb using iogear GUC10KM"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by kamilczauz on 2006-09-26
hey guys i just bought a ps2 to usb convertor for my laptop so i can connect my keyboard and mouse via a kvm switch.  

Ubuntu doesnt seem to like this new device and it wont work at all.

here is my dmesg

please help me
Kamil

```
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000000ff70000 - 000000000ff7e000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ff7e000 - 000000000ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65392
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61296 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f7450
[17179569.184000] ACPI: XSDT (v001 IBM    TP-1A    0x00001180  LTP 0x00000000) @ 0x0ff73af2
[17179569.184000] ACPI: FADT (v001 IBM    TP-1A    0x00001180 IBM  0x00000001) @ 0x0ff73c00
[17179569.184000] ACPI: SSDT (v001 IBM    TP-1A    0x00001180 MSFT 0x0100000d) @ 0x0ff73cb4
[17179569.184000] ACPI: ECDT (v001 IBM    TP-1A    0x00001180 IBM  0x00000001) @ 0x0ff7ded1
[17179569.184000] ACPI: BOOT (v001 IBM    TP-1A    0x00001180  LTP 0x00000001) @ 0x0ff7dfd8
[17179569.184000] ACPI: DSDT (v001 IBM    TP-1A    0x00001180 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:ef800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01200000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 1199.133 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.664000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.664000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.680000] Memory: 248628k/261568k available (1976k kernel code, 12352k reserved, 606k data, 288k init, 0k highmem)
[17179569.680000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.760000] Calibrating delay using timer specific routine.. 2400.02 BogoMIPS (lpj=4800042)
[17179569.760000] Security Framework v1.0.0 initialized
[17179569.760000] SELinux:  Disabled at boot.
[17179569.760000] Mount-cache hash table entries: 512
[17179569.760000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.760000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.760000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.760000] CPU: L2 cache: 512K
[17179569.760000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.760000] mtrr: v2.0 (20020519)
[17179569.760000] CPU: Intel Mobile Intel(R) Pentium(R) III CPU - M  1200MHz stepping 04
[17179569.760000] Enabling fast FPU save and restore... done.
[17179569.760000] Enabling unmasked SIMD FPU exception support... done.
[17179569.760000] Checking 'hlt' instruction... OK.
[17179569.776000] checking if image is initramfs... it is
[17179571.000000] Freeing initrd memory: 6617k freed
[17179571.016000] ACPI: Looking for DSDT ... not found!
[17179571.024000] ACPI: setting ELCR to 0200 (from 0800)
[17179571.240000] NET: Registered protocol family 16
[17179571.240000] EISA bus registered
[17179571.240000] ACPI: bus type pci registered
[17179571.240000] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[17179571.240000] PCI: Using configuration type 1
[17179571.244000] ACPI: Subsystem revision 20051216
[17179571.244000] ACPI: Found ECDT
[17179571.256000] ACPI: Interpreter enabled
[17179571.256000] ACPI: Using PIC for interrupt routing
[17179571.256000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.260000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.260000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.260000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.260000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.260000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179571.264000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179571.264000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179571.264000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.264000] PCI: Probing PCI hardware (bus 00)
[17179571.268000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.268000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.268000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.268000] Boot video device is 0000:01:00.0
[17179571.268000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.276000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179571.276000] ACPI: Power Resource [PUBS] (on)
[17179571.280000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.280000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.280000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.280000] pnp: PnP ACPI init
[17179571.288000] pnp: PnP ACPI: found 13 devices
[17179571.288000] PnPBIOS: Disabled by ACPI PNP
[17179571.288000] PCI: Using ACPI for IRQ routing
[17179571.288000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.296000] PCI: Bridge: 0000:00:01.0
[17179571.296000]   IO window: disabled.
[17179571.296000]   MEM window: c0100000-c01fffff
[17179571.296000]   PREFETCH window: e0000000-ebffffff
[17179571.296000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[17179571.296000]   IO window: 00002000-000020ff
[17179571.296000]   IO window: 00002400-000024ff
[17179571.296000]   PREFETCH window: f0000000-f1ffffff
[17179571.296000]   MEM window: c2000000-c3ffffff
[17179571.296000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[17179571.296000]   IO window: 00002800-000028ff
[17179571.296000]   IO window: 00002c00-00002cff
[17179571.296000]   PREFETCH window: f2000000-f3ffffff
[17179571.296000]   MEM window: c4000000-c5ffffff
[17179571.296000] PCI: Bridge: 0000:00:1e.0
[17179571.296000]   IO window: 2000-6fff
[17179571.296000]   MEM window: c0200000-cfffffff
[17179571.296000]   PREFETCH window: f0000000-f7ffffff
[17179571.296000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.296000] **** SET: Misaligned resource pointer: cf992f02 Type 07 Len 0
[17179571.296000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179571.296000] PCI: setting IRQ 11 as level-triggered
[17179571.296000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179571.296000] **** SET: Misaligned resource pointer: cf992f02 Type 07 Len 0
[17179571.300000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179571.300000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179571.300000] Simple Boot Flag at 0x35 set to 0x1
[17179571.300000] audit: initializing netlink socket (disabled)
[17179571.300000] audit(1159296207.300:1): initialized
[17179571.300000] VFS: Disk quotas dquot_6.5.1
[17179571.300000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.300000] Initializing Cryptographic API
[17179571.300000] io scheduler noop registered
[17179571.300000] io scheduler anticipatory registered
[17179571.300000] io scheduler deadline registered
[17179571.300000] io scheduler cfq registered
[17179571.300000] isapnp: Scanning for PnP cards...
[17179571.652000] isapnp: No Plug & Play device found
[17179571.676000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179571.684000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.684000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.684000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.688000] **** SET: Misaligned resource pointer: cfc7aaa2 Type 00 Len 42
[17179571.688000] pnp: Device 00:09 activated.
[17179571.688000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179571.688000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.688000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.688000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.688000] mice: PS/2 mouse device common for all mice
[17179571.692000] EISA: Probing bus 0 at eisa.0
[17179571.692000] Cannot allocate resource for EISA slot 1
[17179571.692000] Cannot allocate resource for EISA slot 2
[17179571.692000] Cannot allocate resource for EISA slot 3
[17179571.692000] Cannot allocate resource for EISA slot 4
[17179571.692000] Cannot allocate resource for EISA slot 5
[17179571.692000] Cannot allocate resource for EISA slot 6
[17179571.692000] EISA: Detected 0 cards.
[17179571.692000] NET: Registered protocol family 2
[17179571.704000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.736000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.736000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.736000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.736000] TCP: Hash tables configured (established 16384 bind 16384)
[17179571.736000] TCP reno registered
[17179571.736000] TCP bic registered
[17179571.736000] NET: Registered protocol family 1
[17179571.736000] NET: Registered protocol family 8
[17179571.736000] NET: Registered protocol family 20
[17179571.736000] Using IPI Shortcut mode
[17179571.736000] ACPI wakeup devices: 
[17179571.736000]  LID SLPB PCI0 UART PCI1 USB0 USB1 USB2 AC97 
[17179571.736000] ACPI: (supports S0 S3 S4 S5)
[17179571.736000] Freeing unused kernel memory: 288k freed
[17179571.808000] vga16fb: initializing
[17179571.808000] vga16fb: mapped to 0xc00a0000
[17179571.924000] Console: switching to colour frame buffer device 80x25
[17179571.924000] fb0: VGA16 VGA frame buffer device
[17179572.940000] Capability LSM initialized
[17179573.068000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.068000] ACPI: Thermal Zone [THM0] (62 C)
[17179573.632000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179573.632000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.632000] **** SET: Misaligned resource pointer: cfc11ae2 Type 07 Len 0
[17179573.632000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179573.632000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179573.632000] ICH3M: chipset revision 2
[17179573.632000] ICH3M: not 100% native mode: will probe irqs later
[17179573.632000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179573.632000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179573.632000] Probing IDE interface ide0...
[17179573.920000] hda: ST94019A, ATA DISK drive
[17179574.592000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.788000] Probing IDE interface ide1...
[17179575.580000] hdc: TOSHIBA DVD-ROM SD-C2512, ATAPI CD/DVD-ROM drive
[17179576.272000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.292000] hda: max request size: 1024KiB
[17179576.304000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.308000] hda: cache flushes supported
[17179576.308000]  hda: hda1 hda2 < hda5 >
[17179576.608000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179576.608000] Uniform CD-ROM driver Revision: 3.20
[17179578.940000] usbcore: registered new driver usbfs
[17179578.940000] usbcore: registered new driver hub
[17179578.944000] USB Universal Host Controller Interface driver v2.3
[17179578.944000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179578.944000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.944000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.944000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.944000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[17179578.948000] hub 1-0:1.0: USB hub found
[17179578.948000] hub 1-0:1.0: 2 ports detected
[17179579.052000] **** SET: Misaligned resource pointer: cea1db02 Type 07 Len 0
[17179579.052000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179579.052000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179579.052000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.052000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.052000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.052000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[17179579.052000] hub 2-0:1.0: USB hub found
[17179579.052000] hub 2-0:1.0: 2 ports detected
[17179579.156000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179579.156000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.156000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.156000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.156000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[17179579.156000] hub 3-0:1.0: USB hub found
[17179579.156000] hub 3-0:1.0: 2 ports detected
[17179579.544000] Attempting manual resume
[17179579.564000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.564000] EXT3-fs: write access will be enabled during recovery.
[17179579.792000] EXT3-fs: recovery complete.
[17179579.792000] kjournald starting.  Commit interval 5 seconds
[17179579.808000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.356000] windrvr6: no version for "struct_module" found: kernel tainted.
[17179593.356000] windrvr6: module license 'Proprietary' taints kernel.
[17179593.356000] windrvr6: Unknown symbol class_simple_device_add
[17179593.356000] windrvr6: Unknown symbol class_simple_destroy
[17179593.360000] windrvr6: Unknown symbol class_simple_device_remove
[17179593.360000] windrvr6: Unknown symbol class_simple_create
[17179593.360000] windrvr6: Unknown symbol class_simple_device_add
[17179593.360000] windrvr6: Unknown symbol class_simple_destroy
[17179593.360000] windrvr6: Unknown symbol class_simple_device_remove
[17179593.364000] windrvr6: Unknown symbol class_simple_create
[17179593.364000] windrvr6: Unknown symbol class_simple_device_add
[17179593.364000] windrvr6: Unknown symbol class_simple_destroy
[17179593.364000] windrvr6: Unknown symbol class_simple_device_remove
[17179593.368000] windrvr6: Unknown symbol class_simple_create
[17179593.400000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.404000] agpgart: Detected an Intel 830M Chipset.
[17179593.420000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179593.440000] windrvr6: Unknown symbol class_simple_device_add
[17179593.440000] windrvr6: Unknown symbol class_simple_destroy
[17179593.440000] windrvr6: Unknown symbol class_simple_device_remove
[17179593.440000] windrvr6: Unknown symbol class_simple_create
[17179594.096000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.100000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.112000] windrvr6: Unknown symbol class_simple_device_add
[17179594.112000] windrvr6: Unknown symbol class_simple_destroy
[17179594.112000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.112000] windrvr6: Unknown symbol class_simple_create
[17179594.116000] windrvr6: Unknown symbol class_simple_device_add
[17179594.116000] windrvr6: Unknown symbol class_simple_destroy
[17179594.116000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.116000] windrvr6: Unknown symbol class_simple_create
[17179594.120000] windrvr6: Unknown symbol class_simple_device_add
[17179594.120000] windrvr6: Unknown symbol class_simple_destroy
[17179594.120000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.120000] windrvr6: Unknown symbol class_simple_create
[17179594.444000] windrvr6: Unknown symbol class_simple_device_add
[17179594.444000] windrvr6: Unknown symbol class_simple_destroy
[17179594.448000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.448000] windrvr6: Unknown symbol class_simple_create
[17179594.676000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179594.700000] input: TPPS/2 IBM TrackPoint as /class/input/input1
[17179594.732000] Real Time Clock Driver v1.12
[17179594.760000] windrvr6: Unknown symbol class_simple_device_add
[17179594.760000] windrvr6: Unknown symbol class_simple_destroy
[17179594.760000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.760000] windrvr6: Unknown symbol class_simple_create
[17179594.768000] hw_random hardware driver 1.0.0 loaded
[17179594.776000] Floppy drive(s): fd0 is 1.44M
[17179594.792000] FDC 0 is a National Semiconductor PC87306
[17179594.864000] parport: PnPBIOS parport detected.
[17179594.864000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179594.904000] windrvr6: Unknown symbol class_simple_device_add
[17179594.908000] windrvr6: Unknown symbol class_simple_destroy
[17179594.908000] windrvr6: Unknown symbol class_simple_device_remove
[17179594.908000] windrvr6: Unknown symbol class_simple_create
[17179595.008000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[17179595.008000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.008000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179595.176000] input: PC Speaker as /class/input/input2
[17179595.232000] irda_init()
[17179595.232000] NET: Registered protocol family 23
[17179595.252000] ts: Compaq touchscreen protocol output
[17179595.304000] **** SET: Misaligned resource pointer: cb274842 Type 00 Len 42
[17179595.304000] **** SET: Misaligned resource pointer: cb2748c6 Type 07 Len 0
[17179595.304000] pnp: Device 00:0b activated.
[17179595.304000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179595.304000] nsc-ircc, chip->init
[17179595.304000] nsc-ircc, Found chip at base=0x02e
[17179595.304000] nsc-ircc, driver loaded (Dag Brattli)
[17179595.304000] IrDA: Registered device irda0
[17179595.304000] nsc-ircc, Found dongle: HP HSDL-1100/HSDL-2100
[17179595.412000] Loading Lucent Modem Controller driver version 8.26-alk-8
[17179595.416000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179595.416000] Detected Parameters Irq=11 BaseAddress=0x6000 ComAddress=0x6440
[17179595.416000] ttyLTM0 at I/O 0x6000 (irq = 11) is a Lucent/Agere Modem
[17179595.428000] windrvr6: Unknown symbol class_simple_device_add
[17179595.428000] windrvr6: Unknown symbol class_simple_destroy
[17179595.428000] windrvr6: Unknown symbol class_simple_device_remove
[17179595.432000] windrvr6: Unknown symbol class_simple_create
[17179595.696000] intel8x0_measure_ac97_clock: measured 4294353370 usecs
[17179595.696000] intel8x0: measured clock 0 rejected
[17179595.696000] intel8x0: clocking to 48000
[17179595.696000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179595.696000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:023b]
[17179595.696000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.696000] Yenta: Routing CardBus interrupts to PCI
[17179595.696000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21022, devctl 0x64
[17179595.724000] windrvr6: Unknown symbol class_simple_device_add
[17179595.724000] windrvr6: Unknown symbol class_simple_destroy
[17179595.724000] windrvr6: Unknown symbol class_simple_device_remove
[17179595.724000] windrvr6: Unknown symbol class_simple_create
[17179595.812000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179595.812000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179595.928000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[17179595.928000] Socket status: 30000006
[17179595.928000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[17179595.928000] cs: IO port probe 0x2000-0x6fff: clean.
[17179595.928000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179595.928000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[17179595.928000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.928000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:023b]
[17179595.928000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.928000] Yenta: Routing CardBus interrupts to PCI
[17179595.928000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21022, devctl 0x64
[17179596.160000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[17179596.160000] Socket status: 30000006
[17179596.160000] Yenta: Raising subordinate bus# of parent bus (#02) from #08 to #0a
[17179596.160000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[17179596.160000] cs: IO port probe 0x2000-0x6fff: clean.
[17179596.160000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179596.160000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[17179596.188000] windrvr6: Unknown symbol class_simple_device_add
[17179596.188000] windrvr6: Unknown symbol class_simple_destroy
[17179596.188000] windrvr6: Unknown symbol class_simple_device_remove
[17179596.188000] windrvr6: Unknown symbol class_simple_create
[17179596.196000] **** SET: Misaligned resource pointer: ca4e90c2 Type 07 Len 0
[17179596.196000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179596.196000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179596.216000] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:02:8A:21:4B:F8
[17179596.232000] windrvr6: Unknown symbol class_simple_device_add
[17179596.232000] windrvr6: Unknown symbol class_simple_destroy
[17179596.232000] windrvr6: Unknown symbol class_simple_device_remove
[17179596.232000] windrvr6: Unknown symbol class_simple_create
[17179596.284000] windrvr6: Unknown symbol class_simple_device_add
[17179596.288000] windrvr6: Unknown symbol class_simple_destroy
[17179596.288000] windrvr6: Unknown symbol class_simple_device_remove
[17179596.288000] windrvr6: Unknown symbol class_simple_create
[17179596.436000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17179596.848000] cs: IO port probe 0x100-0x3af: clean.
[17179596.848000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.848000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.848000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.848000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.848000] cs: IO port probe 0x100-0x3af: clean.
[17179596.852000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.852000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.852000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.852000] cs: IO port probe 0xa00-0xaff: clean.
[17179597.168000] lp0: using parport0 (interrupt-driven).
[17179597.252000] Adding 1132540k swap on /dev/hda5.  Priority:-1 extents:1 across:1132540k
[17179597.376000] EXT3 FS on hda1, internal journal
[17179597.468000] NET: Registered protocol family 17
[17179597.576000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.576000] md: bitmap version 4.39
[17179598.064000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179600.112000] NET: Registered protocol family 10
[17179600.112000] lo: Disabled Privacy Extensions
[17179600.112000] IPv6 over IPv4 tunneling driver
[17179607.364000] ACPI: AC Adapter [AC] (on-line)
[17179607.376000] ACPI: Battery Slot [BAT0] (battery present)
[17179607.508000] ACPI: Power Button (FF) [PWRF]
[17179607.508000] ACPI: Lid Switch [LID]
[17179607.508000] ACPI: Sleep Button (CM) [SLPB]
[17179607.668000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179607.668000] ibm_acpi: http://ibm-acpi.sf.net/
[17179607.672000] ibm_acpi: dock device not present
[17179607.700000] pcc_acpi: loading...
[17179607.848000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179611.072000] eth1: no IPv6 routers present
[17179614.216000] [drm] Initialized drm 1.0.1 20051102
[17179614.248000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179614.248000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[17179614.260000] mtrr: base(0xe4000000) is not aligned on a size(0x5000000) boundary
[17179614.260000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179614.264000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179614.264000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179615.772000] ppdev: user-space parallel port driver
[17179616.328000] IBM machine detected. Enabling interrupts during APM calls.
[17179616.332000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179616.332000] apm: overridden by ACPI.
[17179621.688000] Non-volatile memory driver v1.2
[17179624.940000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179625.156000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179625.156000] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
[17179625.156000] NFSD: starting 90-second grace period
[17179627.172000] Bluetooth: Core ver 2.8
[17179627.172000] NET: Registered protocol family 31
[17179627.172000] Bluetooth: HCI device and connection manager initialized
[17179627.172000] Bluetooth: HCI socket layer initialized
[17179627.212000] Bluetooth: L2CAP ver 2.8
[17179627.212000] Bluetooth: L2CAP socket layer initialized
[17179627.220000] Bluetooth: RFCOMM socket layer initialized
[17179627.220000] Bluetooth: RFCOMM TTY layer initialized
[17179627.220000] Bluetooth: RFCOMM ver 1.7
[17179628.012000] /dev/vmmon[5128]: Module vmmon: registered with major=10 minor=165
[17179628.012000] /dev/vmmon[5128]: Module vmmon: initialized
[17179628.552000] /dev/vmnet: open called by PID 5152 (vmnet-bridge)
[17179628.552000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179628.552000] /dev/vmnet: port on hub 0 successfully opened
[17179628.552000] bridge-eth1: enabling the bridge
[17179628.552000] bridge-eth1: up
[17179628.552000] bridge-eth1: already up
[17179628.552000] bridge-eth1: attached
[17179628.636000] /dev/vmnet: open called by PID 5166 (vmnet-natd)
[17179628.636000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179628.636000] /dev/vmnet: port on hub 8 successfully opened
[17179635.876000] eth1: no IPv6 routers present
[17179638.876000] /dev/vmnet: open called by PID 5297 (vmnet-netifup)
[17179638.876000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179638.876000] /dev/vmnet: port on hub 1 successfully opened
[17179638.884000] /dev/vmnet: open called by PID 5298 (vmnet-netifup)
[17179638.884000] /dev/vmnet: port on hub 8 successfully opened
[17179638.996000] /dev/vmnet: open called by PID 5323 (vmnet-dhcpd)
[17179638.996000] /dev/vmnet: port on hub 1 successfully opened
[17179639.000000] /dev/vmnet: open called by PID 5324 (vmnet-dhcpd)
[17179639.000000] /dev/vmnet: port on hub 8 successfully opened
[17179649.344000] vmnet8: no IPv6 routers present
[17179649.876000] vmnet1: no IPv6 routers present
[17179703.692000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179703.952000] ISOFS: changing to secondary root

```

windrvr6 is another problem i am having, but it is unrelated to this.

please let me know if u need more info

thanks
kamil

---

