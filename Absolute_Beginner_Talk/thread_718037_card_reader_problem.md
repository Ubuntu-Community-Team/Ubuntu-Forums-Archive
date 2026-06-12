---
title: "card reader problem"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-03-07
Yep another card reader problem !.I know there is another thread that is similar but I did not want to invade it. 
My card reader is a stand alone ECS USB multi card reader , the problem is Gutsy does not see it at all . The thing I noticed is that I see that mode probe fails on starting Ubuntu and sometimes it even stalls on booting , if I unplug the card reader Ubuntu boots:confused:
The card reader work flawlessly in PCLOS and windows.Would like to get it working or maybe someone can recommend one that works out of the box with Ubuntu maybe.
Thanks Steve

---

### Post by bossa on 2008-03-08
Any recommendations for a compatible card reader ?

---

### Post by bossa on 2008-03-08
I remembered that my printer had a built in card reader (Canon PixmaMP170) so I  put in a SM card and low and behold a page flashed up on the monitor showing the folder with the photos in . The big downer ....it never did it again, I tried an SD card and nothing  :( 
 Anyone know how to solve this?

---

### Post by herbster on 2008-03-08
Paste the output of

```
dmesg
```

And with that card popped in the printer, paste

```
df -h
```

and

```
sudo fdisk -l
```

---

### Post by bossa on 2008-03-08
Herbster 
Here it is ..

 	```
  [    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 628C (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9540, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF9480, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:7 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=733faac8-077e-4b5c-a560-e8abfc6d056b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.212 MHz processor.
[   28.374897] spurious 8259A interrupt: IRQ7.
[   28.376095] Console: colour VGA+ 80x25
[   28.376373] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.376681] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.433089] Memory: 2067320k/2097088k available (2015k kernel code, 28456k reserved, 915k data, 364k init, 1179584k highmem)
[   28.433097] virtual kernel memory layout:
[   28.433098]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   28.433099]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.433101]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.433102]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.433103]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   28.433104]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   28.433105]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   28.433107] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.433138] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   28.513105] Calibrating delay using timer specific routine.. 4423.21 BogoMIPS (lpj=8846420)
[   28.513127] Security Framework v1.0.0 initialized
[   28.513131] SELinux:  Disabled at boot.
[   28.513141] Mount-cache hash table entries: 512
[   28.513230] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   28.513237] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.513240] CPU: L2 Cache: 1024K (64 bytes/line)
[   28.513242] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   28.513250] Compat vDSO mapped to ffffe000.
[   28.513258] Checking 'hlt' instruction... OK.
[   28.529194] SMP alternatives: switching to UP code
[   28.529336] Freeing SMP alternatives: 11k freed
[   28.529540] Early unpacking initramfs... done
[   28.799114] ACPI: Core revision 20070126
[   28.799175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.802606] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 02
[   28.802620] Total of 1 processors activated (4423.21 BogoMIPS).
[   28.802750] ENABLING IO-APIC IRQs
[   28.802925] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   28.948879] Brought up 1 CPUs
[   28.948964] Booting paravirtualized kernel on bare hardware
[   28.949001] Time: 21:26:18  Date: 02/08/108
[   28.949017] NET: Registered protocol family 16
[   28.949073] EISA bus registered
[   28.949080] ACPI: bus type pci registered
[   28.953575] PCI: PCI BIOS revision 3.00 entry at 0xfaa00, last bus=5
[   28.953577] PCI: Using configuration type 1
[   28.953579] Setting up standard PCI resources
[   28.956616] ACPI: EC: Look up EC in DSDT
[   28.961544] ACPI: Interpreter enabled
[   28.961546] ACPI: (supports S0 S3 S4 S5)
[   28.961557] ACPI: Using IOAPIC for interrupt routing
[   28.968955] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.968959] PCI: Probing PCI hardware (bus 00)
[   28.969305] PCI: Transparent bridge - 0000:00:09.0
[   28.969529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.969740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   29.023852] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.023997] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.024143] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   29.024288] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   29.024435] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.024580] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   29.024725] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.024872] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   29.025017] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   29.025162] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   29.025307] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   29.025452] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   29.025599] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.025751] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   29.025904] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   29.026057] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   29.026215] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   29.026368] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   29.026521] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   29.026674] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   29.026776] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   29.026934] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   29.027091] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   29.027248] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   29.027405] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   29.027561] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   29.027718] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   29.027875] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   29.028034] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   29.028198] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   29.028361] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   29.028524] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   29.028601] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.028608] pnp: PnP ACPI init
[   29.028612] ACPI: bus type pnp registered
[   29.032780] pnp: PnP ACPI: found 13 devices
[   29.032781] ACPI: ACPI bus type pnp unregistered
[   29.032784] PnPBIOS: Disabled by ACPI PNP
[   29.032816] PCI: Using ACPI for IRQ routing
[   29.032819] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.083316] NET: Registered protocol family 8
[   29.083317] NET: Registered protocol family 20
[   29.083355] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   29.083357] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   29.083360] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   29.083362] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   29.083364] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   29.083367] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   29.083376] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   29.083380] pnp: 00:0c: iomem range 0xd1800-0xd3fff has been reserved
[   29.083382] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   29.083385] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   29.083387] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   29.084773] Time: tsc clocksource has been installed.
[   29.113547] PCI: Bridge: 0000:00:09.0
[   29.113549]   IO window: a000-afff
[   29.113552]   MEM window: fe900000-fe9fffff
[   29.113554]   PREFETCH window: fea00000-feafffff
[   29.113556] PCI: Bridge: 0000:00:0b.0
[   29.113558]   IO window: 9000-9fff
[   29.113560]   MEM window: fe800000-fe8fffff
[   29.113563]   PREFETCH window: fe700000-fe7fffff
[   29.113565] PCI: Bridge: 0000:00:0c.0
[   29.113567]   IO window: 8000-8fff
[   29.113569]   MEM window: fe600000-fe6fffff
[   29.113571]   PREFETCH window: fe500000-fe5fffff
[   29.113573] PCI: Bridge: 0000:00:0d.0
[   29.113575]   IO window: 7000-7fff
[   29.113577]   MEM window: fe400000-fe4fffff
[   29.113580]   PREFETCH window: fe300000-fe3fffff
[   29.113583] PCI: Bridge: 0000:00:0e.0
[   29.113585]   IO window: 6000-6fff
[   29.113587]   MEM window: fb000000-fdffffff
[   29.113589]   PREFETCH window: d0000000-dfffffff
[   29.113595] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   29.113600] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.113605] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   29.113610] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   29.113614] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.113623] NET: Registered protocol family 2
[   29.152758] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.152836] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   29.153726] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.154034] TCP: Hash tables configured (established 131072 bind 65536)
[   29.154036] TCP reno registered
[   29.164813] checking if image is initramfs... it is
[   29.616461] Switched to high resolution mode on CPU 0
[   29.692670] Freeing initrd memory: 7372k freed
[   29.692919] audit: initializing netlink socket (disabled)
[   29.692927] audit(1205011579.052:1): initialized
[   29.692969] highmem bounce pool size: 64 pages
[   29.694133] VFS: Disk quotas dquot_6.5.1
[   29.694165] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.694221] io scheduler noop registered
[   29.694223] io scheduler anticipatory registered
[   29.694225] io scheduler deadline registered
[   29.694236] io scheduler cfq registered (default)
[   29.708341] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   29.708347] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.708352] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   29.708359] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.708364] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   29.708370] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.708375] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   29.708381] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.708386] Boot video device is 0000:05:00.0
[   29.708436] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.708453] assign_interrupt_mode Found MSI capability
[   29.708455] Allocate Port Service[0000:00:0b.0:pcie00]
[   29.708496] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   29.708511] assign_interrupt_mode Found MSI capability
[   29.708513] Allocate Port Service[0000:00:0c.0:pcie00]
[   29.708553] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   29.708569] assign_interrupt_mode Found MSI capability
[   29.708570] Allocate Port Service[0000:00:0d.0:pcie00]
[   29.708609] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.708624] assign_interrupt_mode Found MSI capability
[   29.708626] Allocate Port Service[0000:00:0e.0:pcie00]
[   29.708699] isapnp: Scanning for PnP cards...
[   30.061067] isapnp: No Plug & Play device found
[   30.077006] Real Time Clock Driver v1.12ac
[   30.077070] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.077142] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.077254] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.077607] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.078032] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.078166] input: Macintosh mouse button emulation as /class/input/input0
[   30.078234] PNP: No PS/2 controller found. Probing ports directly.
[   30.081327] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.081330] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.081428] mice: PS/2 mouse device common for all mice
[   30.081491] EISA: Probing bus 0 at eisa.0
[   30.081502] Cannot allocate resource for EISA slot 4
[   30.081506] Cannot allocate resource for EISA slot 6
[   30.081508] Cannot allocate resource for EISA slot 7
[   30.081509] Cannot allocate resource for EISA slot 8
[   30.081511] EISA: Detected 0 cards.
[   30.081570] TCP cubic registered
[   30.081579] NET: Registered protocol family 1
[   30.081593] Using IPI No-Shortcut mode
[   30.081711]   Magic number: 0:185:449
[   30.081999] Freeing unused kernel memory: 364k freed
[   31.260939] AppArmor: AppArmor initialized<5>audit(1205011580.552:2):  type=1505 info="AppArmor initialized" pid=1241
[   31.267452] fuse init (API version 7.8)
[   31.271132] Failure registering capabilities with primary security module.
[   31.273938] ACPI: Fan [FAN] (on)
[   31.277139] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.278031] ACPI: Thermal Zone [THRM] (40 C)
[   31.716959] usbcore: registered new interface driver usbfs
[   31.716979] usbcore: registered new interface driver hub
[   31.716994] usbcore: registered new device driver usb
[   31.717447] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.717732] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   31.717738] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   31.717748] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.717750] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   31.717859] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   31.717872] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfebff000
[   31.773323] SCSI subsystem initialized
[   31.776751] libata version 2.21 loaded.
[   31.797783] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   31.812907] usb usb1: configuration #1 chosen from 1 choice
[   31.812927] hub 1-0:1.0: USB hub found
[   31.812934] hub 1-0:1.0: 10 ports detected
[   31.823020] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.823024] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.915307] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   31.915315] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   31.915323] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   31.915326] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   31.915344] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   31.915365] ehci_hcd 0000:00:02.1: debug port 1
[   31.915368] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   31.915376] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfeb00000
[   31.915381] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.915434] usb usb2: configuration #1 chosen from 1 choice
[   31.915452] hub 2-0:1.0: USB hub found
[   31.915457] hub 2-0:1.0: 10 ports detected
[   31.928604] Floppy drive(s): fd0 is 1.44M
[   31.983828] FDC 0 is a post-1991 82077
[   32.020448] sata_nv 0000:00:07.0: version 3.4
[   32.020775] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   32.020782] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   32.020786] sata_nv 0000:00:07.0: Using ADMA mode
[   32.020816] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   32.020893] scsi0 : sata_nv
[   32.034810] scsi1 : sata_nv
[   32.034877] ata1: SATA max UDMA/133 cmd 0xf883e480 ctl 0xf883e4a0 bmdma 0x0001cc00 irq 18
[   32.034880] ata2: SATA max UDMA/133 cmd 0xf883e580 ctl 0xf883e5a0 bmdma 0x0001cc08 irq 18
[   32.346447] ata1: SATA link down (SStatus 0 SControl 300)
[   32.562290] usb 1-9: new low speed USB device using ohci_hcd and address 2
[   32.776252] usb 1-9: configuration #1 chosen from 1 choice
[   32.788737] usbcore: registered new interface driver hiddev
[   32.799419] input: Logitech USB Receiver as /class/input/input1
[   32.799428] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-9
[   32.810465] input: Logitech USB Receiver as /class/input/input2
[   32.810567] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-9
[   32.810574] usbcore: registered new interface driver usbhid
[   32.810577] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.814126] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.822310] ata2.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   32.822313] ata2.00: 488397168 sectors, multi 16: LBA48 
[   32.830258] ata2.00: configured for UDMA/133
[   32.830334] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   32.830340] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   32.830707] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   32.830714] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   32.830717] sata_nv 0000:00:08.0: Using ADMA mode
[   32.830747] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   32.830808] scsi2 : sata_nv
[   32.830833] scsi3 : sata_nv
[   32.830873] ata3: SATA max UDMA/133 cmd 0xf8860480 ctl 0xf88604a0 bmdma 0x0001b800 irq 19
[   32.830876] ata4: SATA max UDMA/133 cmd 0xf8860580 ctl 0xf88605a0 bmdma 0x0001b808 irq 19
[   33.141878] ata3: SATA link down (SStatus 0 SControl 300)
[   33.453656] ata4: SATA link down (SStatus 0 SControl 300)
[   33.453968] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   33.453970] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   33.453974] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   33.453978] forcedeth: using HIGHDMA
[   33.462052] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   33.462062] sd 1:0:0:0: [sda] Write Protect is off
[   33.462064] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.462076] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.462108] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   33.462114] sd 1:0:0:0: [sda] Write Protect is off
[   33.462116] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.462126] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.462130]  sda: sda1 sda2
[   33.479329] sd 1:0:0:0: [sda] Attached SCSI disk
[   33.482740] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   33.973750] eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
[   33.973929] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   33.973943] NFORCE-CK804: chipset revision 162
[   33.973945] NFORCE-CK804: not 100% native mode: will probe irqs later
[   33.973949] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   33.973952] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   33.973959]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   33.973966]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   33.973972] Probing IDE interface ide0...
[   34.261150] hda: SAMSUNG SP0812N, ATA DISK drive
[   34.932720] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.944679] Probing IDE interface ide1...
[   35.680137] hdc: PIONEER DVD-RW DVR-112L, ATAPI CD/DVD-ROM drive
[   36.016305] ide1 at 0x170-0x177,0x376 on irq 15
[   36.018159] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   36.018166] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   36.070051] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   36.082118] hda: max request size: 512KiB
[   36.089019] hda: Host Protected Area detected.
[   36.089021]  current capacity is 156365903 sectors (80059 MB)
[   36.089022]  native  capacity is 156368016 sectors (80060 MB)
[   36.106841] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   36.106845] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   36.106848] ide: failed opcode was: 0x37
[   36.106861] hda: 156365903 sectors (80059 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   36.107240] hda: cache flushes supported
[   36.107269]  hda: hda1 hda2 < hda5 >
[   36.141153] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[   36.141159] Uniform CD-ROM driver Revision: 3.20
[   36.316106] Attempting manual resume
[   36.316108] swsusp: Resume From Partition 3:5
[   36.316110] PM: Checking swsusp image.
[   36.316246] PM: Resume from disk failed.
[   36.354528] kjournald starting.  Commit interval 5 seconds
[   36.354536] EXT3-fs: mounted filesystem with ordered data mode.
[   37.346943] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000142f9e]
[   42.852801] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   42.852823] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4d00
[   43.128616] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.131063] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.767092] input: PC Speaker as /class/input/input3
[   43.819994] parport_pc 00:0a: reported by Plug and Play ACPI
[   43.820032] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.850358] Linux agpgart interface v0.102 (c) Dave Jones
[   43.886802] irda_init()
[   43.886817] NET: Registered protocol family 23
[   44.066441] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   44.066445] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   44.066460] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   44.111631] nvidia: module license 'NVIDIA' taints kernel.
[   44.425827] intel8x0_measure_ac97_clock: measured 53982 usecs
[   44.425831] intel8x0: clocking to 46969
[   44.428473] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   44.428481] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   44.428488] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   44.428670] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   45.319659] lp0: using parport0 (interrupt-driven).
[   45.355298] it87: Found IT8712F chip at 0x290, revision 6
[   45.404529] Adding 3229024k swap on /dev/hda5.  Priority:-1 extents:1 across:3229024k
[   45.785376] EXT3 FS on hda1, internal journal
[   45.954957] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   47.386486] input: Power Button (FF) as /class/input/input4
[   47.389845] ACPI: Power Button (FF) [PWRF]
[   47.419296] input: Power Button (CM) as /class/input/input5
[   47.422598] ACPI: Power Button (CM) [PWRB]
[   47.508385] No dock devices found.
[   47.732823] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   47.737009] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   48.835469] Failure registering capabilities with primary security module.
[   49.055066] ppdev: user-space parallel port driver
[   49.306957] audit(1205011598.837:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5048 profile="/usr/sbin/cupsd"
[   49.404153] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   49.404157] apm: overridden by ACPI.
[   51.203685] /dev/vmmon[5282]: Module vmmon: registered with major=10 minor=165
[   51.203970] /dev/vmmon[5282]: Module vmmon: initialized
[   51.358689] /dev/vmnet: open called by PID 5307 (vmnet-bridge)
[   51.358931] /dev/vmnet: hub 0 does not exist, allocating memory.
[   51.359139] /dev/vmnet: port on hub 0 successfully opened
[   51.359339] bridge-eth0: enabling the bridge
[   51.359505] bridge-eth0: up
[   51.359641] bridge-eth0: already up
[   51.359644] bridge-eth0: attached
[   51.472192] /dev/vmnet: open called by PID 5339 (vmnet-netifup)
[   51.472436] /dev/vmnet: hub 1 does not exist, allocating memory.
[   51.472644] /dev/vmnet: port on hub 1 successfully opened
[   51.475339] /dev/vmnet: open called by PID 5340 (vmnet-netifup)
[   51.475608] /dev/vmnet: hub 8 does not exist, allocating memory.
[   51.475817] /dev/vmnet: port on hub 8 successfully opened
[   51.479149] /dev/vmnet: open called by PID 5337 (vmnet-natd)
[   51.479382] /dev/vmnet: port on hub 8 successfully opened
[   51.870287] /dev/vmnet: open called by PID 5366 (vmnet-dhcpd)
[   51.870503] /dev/vmnet: port on hub 1 successfully opened
[   51.871264] /dev/vmnet: open called by PID 5367 (vmnet-dhcpd)
[   51.871459] /dev/vmnet: port on hub 8 successfully opened
[   56.760226] NET: Registered protocol family 17
[   61.481327] NET: Registered protocol family 10
[   61.481492] lo: Disabled Privacy Extensions
[   72.054112] vmnet8: no IPv6 routers present
[   72.241977] vmnet1: no IPv6 routers present
[   72.429850] eth0: no IPv6 routers present
[12958.959080] usb 1-6: new full speed USB device using ohci_hcd and address 3
[12959.176634] usb 1-6: configuration #1 chosen from 1 choice
[12959.251725] usbcore: registered new interface driver libusual
[12959.267792] Initializing USB Mass Storage driver...
steve@steve-desktop:~$ 


```


```

steve@steve-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G   16G   52G  23% /
varrun               1014M  368K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   76K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              49G   22G   27G  45% /media/Vista
steve@steve-desktop:~$ 


```


```
steve@steve-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083d89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30401   192996877+  83  Linux

Disk /dev/hda: 80.0 GB, 80059342336 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96833ab0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9331    74951226   83  Linux
/dev/hda2            9332        9733     3229065    5  Extended
/dev/hda5            9332        9733     3229033+  82  Linux swap / Solaris
steve@steve-desktop:~$ 

```

---

### Post by herbster on 2008-03-08
What filesystem is the SD card? FAT16/32? It's definitely seen by the system and working, just a mounting issue.

---

### Post by bossa on 2008-03-09
Hi herbster

Sorry for the delay in replying it was V late here (UK) so I had to go to sleep ;) 
Regarding the file system I went into windows Vista and all it says there is FAT for both the SD/SM cards....I dont know how else to check. (Very rare that I go into windows anymore ;) )
Just a note the PC boots some times with the card reader plugged in and other times it stalls  on the progress bar on boot.

---

### Post by herbster on 2008-03-09
Try:

```
sudo modprobe ohci_hcd
```

and popping the card in again. We know the reader and card work as you see them in Vista, so it's got to be a module issue most likely. It did work the one time at least.

---

### Post by bossa on 2008-03-09
> **herbster said:**
> Try:

```
sudo modprobe ohci_hcd
```

and popping the card in again. We know the reader and card work as you see them in Vista, so it's got to be a module issue most likely. It did work the one time at least.

Hi herbster

nothing happens when I enter sudo modprobe ohci_hcd 

am I doing something wrong?


EDIT : while posting this message a window opened up asking me if I wanted to import images! This is from my printer card reader using an SD card. Still wondering why that CLI did nothing.

---

### Post by herbster on 2008-03-09
Nothing happens on a successful modprobe, it just loads the module. You only get output if it fails/you don't use sudo.

So it works? This just means the module is not autoloading.

---

### Post by bossa on 2008-03-09
> **herbster said:**
> Nothing happens on a successful modprobe, it just loads the module. You only get output if it fails/you don't use sudo.

So it works? This just means the module is not autoloading.

Thats great thanks! Yes it works with the printer card reader :)

Tried the modprobe with the stand alone card reader ...there was no output in the terminal ,but still doesn't work.
Will I have to modprobe to get the printer card reader to be recognised every time ?

---

### Post by herbster on 2008-03-09
Check /etc/modules (I believe that's what debian/Ubuntu uses for module loading). Edit it as root and add "ohci_hcd" to the end.

For your standalone card reader, pull it out and paste output of "dmesg." Now put it in and paste the output again, we should be able to see the module/driver it's using as well.

---

### Post by bossa on 2008-03-09
> **herbster said:**
> Check /etc/modules (I believe that's what debian/Ubuntu uses for module loading). Edit it as root and add "ohci_hcd" to the end.

For your standalone card reader, pull it out and paste output of "dmesg." Now put it in and paste the output again, we should be able to see the module/driver it's using as well.

Just to get this right the first time. When you say    " Edit it as root and add "ohci_hcd" to the end"

 is that at the bottom of  the text that is there or the top ? . Just wondering as the cursor starts at the top of the text.
Also should I edit that before I do the "dmesg"  for the stand alone ?

---

### Post by bossa on 2008-03-09
the output with out any editing.
 BTW I have reboot the PC a couple of times now and the card reader on the PC sees the SD card everytime I insert it  (no editing) :)

```
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=733faac8-077e-4b5c-a560-e8abfc6d056b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.213 MHz processor.
[   27.720562] spurious 8259A interrupt: IRQ7.
[   27.721762] Console: colour VGA+ 80x25
[   27.722040] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.722349] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.778758] Memory: 2067320k/2097088k available (2015k kernel code, 28456k reserved, 915k data, 364k init, 1179584k highmem)
[   27.778767] virtual kernel memory layout:
[   27.778767]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   27.778769]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.778770]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.778771]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.778772]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   27.778773]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   27.778774]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   27.778777] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.778808] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.858775] Calibrating delay using timer specific routine.. 4423.21 BogoMIPS (lpj=8846430)
[   27.858796] Security Framework v1.0.0 initialized
[   27.858800] SELinux:  Disabled at boot.
[   27.858810] Mount-cache hash table entries: 512
[   27.858900] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   27.858907] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.858909] CPU: L2 Cache: 1024K (64 bytes/line)
[   27.858911] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   27.858919] Compat vDSO mapped to ffffe000.
[   27.858927] Checking 'hlt' instruction... OK.
[   27.874863] SMP alternatives: switching to UP code
[   27.875005] Freeing SMP alternatives: 11k freed
[   27.875209] Early unpacking initramfs... done
[   28.144783] ACPI: Core revision 20070126
[   28.144844] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.148274] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 02
[   28.148289] Total of 1 processors activated (4423.21 BogoMIPS).
[   28.148419] ENABLING IO-APIC IRQs
[   28.148594] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   28.294548] Brought up 1 CPUs
[   28.294634] Booting paravirtualized kernel on bare hardware
[   28.294670] Time: 22:11:03  Date: 02/09/108
[   28.294686] NET: Registered protocol family 16
[   28.294742] EISA bus registered
[   28.294749] ACPI: bus type pci registered
[   28.299245] PCI: PCI BIOS revision 3.00 entry at 0xfaa00, last bus=5
[   28.299246] PCI: Using configuration type 1
[   28.299248] Setting up standard PCI resources
[   28.302284] ACPI: EC: Look up EC in DSDT
[   28.307213] ACPI: Interpreter enabled
[   28.307215] ACPI: (supports S0 S3 S4 S5)
[   28.307226] ACPI: Using IOAPIC for interrupt routing
[   28.314623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.314627] PCI: Probing PCI hardware (bus 00)
[   28.314974] PCI: Transparent bridge - 0000:00:09.0
[   28.315197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.315408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.369520] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.369666] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.369812] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   28.369957] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   28.370104] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.370249] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.370394] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.370541] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.370686] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   28.370831] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.370976] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.371121] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   28.371268] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.371420] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.371573] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.371726] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.371884] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   28.372038] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   28.372191] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   28.372343] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   28.372446] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   28.372603] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   28.372760] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   28.372917] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   28.373074] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   28.373231] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   28.373388] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   28.373544] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   28.373703] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   28.373867] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   28.374030] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   28.374194] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   28.374271] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.374277] pnp: PnP ACPI init
[   28.374282] ACPI: bus type pnp registered
[   28.378449] pnp: PnP ACPI: found 13 devices
[   28.378451] ACPI: ACPI bus type pnp unregistered
[   28.378453] PnPBIOS: Disabled by ACPI PNP
[   28.378485] PCI: Using ACPI for IRQ routing
[   28.378488] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.428986] NET: Registered protocol family 8
[   28.428988] NET: Registered protocol family 20
[   28.429025] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   28.429028] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   28.429030] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   28.429032] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   28.429035] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   28.429037] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   28.429047] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   28.429050] pnp: 00:0c: iomem range 0xd1800-0xd3fff has been reserved
[   28.429053] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   28.429055] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   28.429058] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   28.430442] Time: tsc clocksource has been installed.
[   28.459217] PCI: Bridge: 0000:00:09.0
[   28.459219]   IO window: a000-afff
[   28.459222]   MEM window: fe900000-fe9fffff
[   28.459224]   PREFETCH window: fea00000-feafffff
[   28.459226] PCI: Bridge: 0000:00:0b.0
[   28.459228]   IO window: 9000-9fff
[   28.459231]   MEM window: fe800000-fe8fffff
[   28.459233]   PREFETCH window: fe700000-fe7fffff
[   28.459235] PCI: Bridge: 0000:00:0c.0
[   28.459237]   IO window: 8000-8fff
[   28.459239]   MEM window: fe600000-fe6fffff
[   28.459241]   PREFETCH window: fe500000-fe5fffff
[   28.459243] PCI: Bridge: 0000:00:0d.0
[   28.459245]   IO window: 7000-7fff
[   28.459248]   MEM window: fe400000-fe4fffff
[   28.459250]   PREFETCH window: fe300000-fe3fffff
[   28.459253] PCI: Bridge: 0000:00:0e.0
[   28.459255]   IO window: 6000-6fff
[   28.459257]   MEM window: fb000000-fdffffff
[   28.459260]   PREFETCH window: d0000000-dfffffff
[   28.459265] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   28.459270] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   28.459275] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   28.459280] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   28.459285] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   28.459293] NET: Registered protocol family 2
[   28.498427] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.498506] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   28.499394] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.499702] TCP: Hash tables configured (established 131072 bind 65536)
[   28.499704] TCP reno registered
[   28.510483] checking if image is initramfs... it is
[   28.962131] Switched to high resolution mode on CPU 0
[   29.038343] Freeing initrd memory: 7372k freed
[   29.038591] audit: initializing netlink socket (disabled)
[   29.038599] audit(1205100664.052:1): initialized
[   29.038642] highmem bounce pool size: 64 pages
[   29.039806] VFS: Disk quotas dquot_6.5.1
[   29.039838] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.039894] io scheduler noop registered
[   29.039896] io scheduler anticipatory registered
[   29.039897] io scheduler deadline registered
[   29.039908] io scheduler cfq registered (default)
[   29.054010] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   29.054017] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054022] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   29.054028] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054033] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   29.054040] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054044] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   29.054051] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054056] Boot video device is 0000:05:00.0
[   29.054106] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.054122] assign_interrupt_mode Found MSI capability
[   29.054125] Allocate Port Service[0000:00:0b.0:pcie00]
[   29.054165] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   29.054181] assign_interrupt_mode Found MSI capability
[   29.054183] Allocate Port Service[0000:00:0c.0:pcie00]
[   29.054223] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   29.054238] assign_interrupt_mode Found MSI capability
[   29.054240] Allocate Port Service[0000:00:0d.0:pcie00]
[   29.054278] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.054294] assign_interrupt_mode Found MSI capability
[   29.054295] Allocate Port Service[0000:00:0e.0:pcie00]
[   29.054369] isapnp: Scanning for PnP cards...
[   29.406737] isapnp: No Plug & Play device found
[   29.422653] Real Time Clock Driver v1.12ac
[   29.422718] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.422790] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.422901] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.423255] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.423678] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.423812] input: Macintosh mouse button emulation as /class/input/input0
[   29.423880] PNP: No PS/2 controller found. Probing ports directly.
[   29.426974] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.426977] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.427075] mice: PS/2 mouse device common for all mice
[   29.427138] EISA: Probing bus 0 at eisa.0
[   29.427149] Cannot allocate resource for EISA slot 4
[   29.427153] Cannot allocate resource for EISA slot 6
[   29.427155] Cannot allocate resource for EISA slot 7
[   29.427157] Cannot allocate resource for EISA slot 8
[   29.427158] EISA: Detected 0 cards.
[   29.427218] TCP cubic registered
[   29.427226] NET: Registered protocol family 1
[   29.427241] Using IPI No-Shortcut mode
[   29.427359]   Magic number: 0:607:198
[   29.427392]   hash matches device ttypd
[   29.427649] Freeing unused kernel memory: 364k freed
[   30.606593] AppArmor: AppArmor initialized<5>audit(1205100665.552:2):  type=1505 info="AppArmor initialized" pid=1241
[   30.613210] fuse init (API version 7.8)
[   30.616849] Failure registering capabilities with primary security module.
[   30.619620] ACPI: Fan [FAN] (on)
[   30.622898] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   30.623795] ACPI: Thermal Zone [THRM] (40 C)
[   31.090472] usbcore: registered new interface driver usbfs
[   31.090493] usbcore: registered new interface driver hub
[   31.090507] usbcore: registered new device driver usb
[   31.091421] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   31.091428] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   31.091436] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   31.091439] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   31.091542] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   31.091564] ehci_hcd 0000:00:02.1: debug port 1
[   31.091567] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   31.091574] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfeb00000
[   31.091579] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.091648] usb usb1: configuration #1 chosen from 1 choice
[   31.091667] hub 1-0:1.0: USB hub found
[   31.091673] hub 1-0:1.0: 10 ports detected
[   31.107048] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.107052] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.117367] SCSI subsystem initialized
[   31.120800] libata version 2.21 loaded.
[   31.145765] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.150788] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   31.204029] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   31.204037] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 17
[   31.255781] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   31.272709] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   31.272717] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 18
[   31.272727] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.272730] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   31.272762] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   31.272774] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfebff000
[   31.330455] usb usb2: configuration #1 chosen from 1 choice
[   31.330476] hub 2-0:1.0: USB hub found
[   31.330484] hub 2-0:1.0: 10 ports detected
[   31.370751] Floppy drive(s): fd0 is 1.44M
[   31.402611] FDC 0 is a post-1991 82077
[   31.434544] sata_nv 0000:00:07.0: version 3.4
[   31.434881] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   31.434888] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 19
[   31.434891] sata_nv 0000:00:07.0: Using ADMA mode
[   31.434921] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   31.435003] scsi0 : sata_nv
[   31.435031] scsi1 : sata_nv
[   31.435074] ata1: SATA max UDMA/133 cmd 0xf884e480 ctl 0xf884e4a0 bmdma 0x0001cc00 irq 19
[   31.435077] ata2: SATA max UDMA/133 cmd 0xf884e580 ctl 0xf884e5a0 bmdma 0x0001cc08 irq 19
[   31.736084] usb 2-9: new low speed USB device using ohci_hcd and address 2
[   31.744079] ata1: SATA link down (SStatus 0 SControl 300)
[   31.950037] usb 2-9: configuration #1 chosen from 1 choice
[   31.962631] usbcore: registered new interface driver hiddev
[   31.973198] input: Logitech USB Receiver as /class/input/input1
[   31.973208] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-9
[   31.984259] input: Logitech USB Receiver as /class/input/input2
[   31.984360] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-9
[   31.984368] usbcore: registered new interface driver usbhid
[   31.984370] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.211752] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.219906] ata2.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   32.219908] ata2.00: 488397168 sectors, multi 16: LBA48 
[   32.227877] ata2.00: configured for UDMA/133
[   32.227950] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   32.227955] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   32.228331] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   32.228338] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   32.228341] sata_nv 0000:00:08.0: Using ADMA mode
[   32.228370] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   32.228428] scsi2 : sata_nv
[   32.228455] scsi3 : sata_nv
[   32.228500] ata3: SATA max UDMA/133 cmd 0xf8868480 ctl 0xf88684a0 bmdma 0x0001b800 irq 20
[   32.228503] ata4: SATA max UDMA/133 cmd 0xf8868580 ctl 0xf88685a0 bmdma 0x0001b808 irq 20
[   32.531570] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000142f9e]
[   32.539512] ata3: SATA link down (SStatus 0 SControl 300)
[   32.851288] ata4: SATA link down (SStatus 0 SControl 300)
[   32.851628] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   32.851631] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   32.851636] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   32.851641] forcedeth: using HIGHDMA
[   32.859626] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.859636] sd 1:0:0:0: [sda] Write Protect is off
[   32.859638] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.859649] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.859681] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.859687] sd 1:0:0:0: [sda] Write Protect is off
[   32.859689] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.859698] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.859701]  sda: sda1 sda2
[   32.870064] sd 1:0:0:0: [sda] Attached SCSI disk
[   32.873549] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   33.371384] eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
[   33.371561] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   33.371576] NFORCE-CK804: chipset revision 162
[   33.371578] NFORCE-CK804: not 100% native mode: will probe irqs later
[   33.371581] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   33.371585] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   33.371591]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   33.371598]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   33.371604] Probing IDE interface ide0...
[   33.658786] hda: SAMSUNG SP0812N, ATA DISK drive
[   34.330355] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.342245] Probing IDE interface ide1...
[   35.077773] hdc: PIONEER DVD-RW DVR-112L, ATAPI CD/DVD-ROM drive
[   35.413861] ide1 at 0x170-0x177,0x376 on irq 15
[   35.420196] hda: max request size: 512KiB
[   35.426014] hda: Host Protected Area detected.
[   35.426016]  current capacity is 156365903 sectors (80059 MB)
[   35.426017]  native  capacity is 156368016 sectors (80060 MB)
[   35.444448] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   35.444453] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   35.444455] ide: failed opcode was: 0x37
[   35.444469] hda: 156365903 sectors (80059 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   35.444839] hda: cache flushes supported
[   35.444867]  hda: hda1 hda2 < hda5 >
[   35.486284] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[   35.486291] Uniform CD-ROM driver Revision: 3.20
[   35.646113] Attempting manual resume
[   35.646115] swsusp: Resume From Partition 3:5
[   35.646117] PM: Checking swsusp image.
[   35.646253] PM: Resume from disk failed.
[   35.692137] kjournald starting.  Commit interval 5 seconds
[   35.692145] EXT3-fs: mounted filesystem with ordered data mode.
[   42.475216] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   42.475238] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4d00
[   42.482864] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.501977] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.895531] input: PC Speaker as /class/input/input3
[   43.085737] irda_init()
[   43.085749] NET: Registered protocol family 23
[   43.091783] parport_pc 00:0a: reported by Plug and Play ACPI
[   43.091821] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.196242] Linux agpgart interface v0.102 (c) Dave Jones
[   43.243213] nvidia: module license 'NVIDIA' taints kernel.
[   43.503881] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   43.503890] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   43.503896] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   43.504055] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   43.695331] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   43.695335] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 18
[   43.695349] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   44.015329] intel8x0_measure_ac97_clock: measured 54775 usecs
[   44.015332] intel8x0: clocking to 46950
[   44.665549] lp0: using parport0 (interrupt-driven).
[   44.701178] it87: Found IT8712F chip at 0x290, revision 6
[   44.750651] Adding 3229024k swap on /dev/hda5.  Priority:-1 extents:1 across:3229024k
[   45.147946] EXT3 FS on hda1, internal journal
[   45.325826] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   46.766130] input: Power Button (FF) as /class/input/input4
[   46.769477] ACPI: Power Button (FF) [PWRF]
[   46.798640] input: Power Button (CM) as /class/input/input5
[   46.801968] ACPI: Power Button (CM) [PWRB]
[   46.889900] No dock devices found.
[   47.128651] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   47.132840] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   48.189626] Failure registering capabilities with primary security module.
[   48.390653] ppdev: user-space parallel port driver
[   48.658518] audit(1205100683.831:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5046 profile="/usr/sbin/cupsd"
[   48.750026] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.750030] apm: overridden by ACPI.
[   50.641137] /dev/vmmon[5264]: Module vmmon: registered with major=10 minor=165
[   50.641419] /dev/vmmon[5264]: Module vmmon: initialized
[   50.870998] /dev/vmnet: open called by PID 5306 (vmnet-bridge)
[   50.871233] /dev/vmnet: hub 0 does not exist, allocating memory.
[   50.871432] /dev/vmnet: port on hub 0 successfully opened
[   50.871620] bridge-eth0: enabling the bridge
[   50.871781] bridge-eth0: up
[   50.871913] bridge-eth0: already up
[   50.871916] bridge-eth0: attached
[   50.919056] /dev/vmnet: open called by PID 5320 (vmnet-natd)
[   50.919299] /dev/vmnet: hub 8 does not exist, allocating memory.
[   50.919500] /dev/vmnet: port on hub 8 successfully opened
[   50.927862] /dev/vmnet: open called by PID 5321 (vmnet-netifup)
[   50.928096] /dev/vmnet: hub 1 does not exist, allocating memory.
[   50.928305] /dev/vmnet: port on hub 1 successfully opened
[   50.930801] /dev/vmnet: open called by PID 5322 (vmnet-netifup)
[   50.931042] /dev/vmnet: port on hub 8 successfully opened
[   51.753496] /dev/vmnet: open called by PID 5365 (vmnet-dhcpd)
[   51.753616] /dev/vmnet: port on hub 8 successfully opened
[   51.754322] /dev/vmnet: open called by PID 5364 (vmnet-dhcpd)
[   51.754438] /dev/vmnet: port on hub 1 successfully opened
[   56.139349] NET: Registered protocol family 17
[   60.001239] NET: Registered protocol family 10
[   60.001698] lo: Disabled Privacy Extensions
[   70.285290] eth0: no IPv6 routers present
[   70.769184] vmnet8: no IPv6 routers present
[   70.897160] vmnet1: no IPv6 routers present
[  137.003976] usb 1-10: new high speed USB device using ehci_hcd and address 3
[  137.137873] usb 1-10: configuration #1 chosen from 1 choice
[  137.340911] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x170A
[  137.341300] usbcore: registered new interface driver usblp
[  137.341486] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  137.413605] usbcore: registered new interface driver libusual
[  137.689614] Initializing USB Mass Storage driver...
[  137.689885] scsi4 : SCSI emulation for USB Mass Storage devices
[  137.690114] usb-storage: device found at 3
[  137.690116] usb-storage: waiting for device to settle before scanning
[  137.690488] usbcore: registered new interface driver usb-storage
[  137.690688] USB Mass Storage support registered.
[  142.684377] usb-storage: device scan complete
[  142.685750] scsi 4:0:0:0: Direct-Access     Canon    MP170Storage     0108 PQ: 0 ANSI: 2
[  142.690382] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  142.690407] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  178.792033] sd 4:0:0:0: [sdb] 994304 512-byte hardware sectors (509 MB)
[  178.793782] sd 4:0:0:0: [sdb] Write Protect is on
[  178.793785] sd 4:0:0:0: [sdb] Mode Sense: 37 00 80 08
[  178.793787] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  178.796902] sd 4:0:0:0: [sdb] 994304 512-byte hardware sectors (509 MB)
[  178.798778] sd 4:0:0:0: [sdb] Write Protect is on
[  178.798781] sd 4:0:0:0: [sdb] Mode Sense: 37 00 80 08
[  178.798783] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  178.798785]  sdb: sdb1
[  247.803841] usb 1-10: USB disconnect, address 3
[  247.804000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[  247.930021] scsi 4:0:0:0: rejecting I/O to dead device
[  265.304501] usb 2-6: new full speed USB device using ohci_hcd and address 3
[  265.522239] usb 2-6: configuration #1 chosen from 1 choice
[  309.136675] usb-storage: probe of 2-6:1.0 failed with error -1
[  309.136770] usb 2-6: USB disconnect, address 3
steve@steve-desktop:~$ 


```

Card reader plugged in:

```

[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=733faac8-077e-4b5c-a560-e8abfc6d056b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.213 MHz processor.
[   27.720562] spurious 8259A interrupt: IRQ7.
[   27.721762] Console: colour VGA+ 80x25
[   27.722040] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.722349] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.778758] Memory: 2067320k/2097088k available (2015k kernel code, 28456k reserved, 915k data, 364k init, 1179584k highmem)
[   27.778767] virtual kernel memory layout:
[   27.778767]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   27.778769]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.778770]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.778771]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.778772]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   27.778773]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   27.778774]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   27.778777] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.778808] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.858775] Calibrating delay using timer specific routine.. 4423.21 BogoMIPS (lpj=8846430)
[   27.858796] Security Framework v1.0.0 initialized
[   27.858800] SELinux:  Disabled at boot.
[   27.858810] Mount-cache hash table entries: 512
[   27.858900] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   27.858907] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.858909] CPU: L2 Cache: 1024K (64 bytes/line)
[   27.858911] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   27.858919] Compat vDSO mapped to ffffe000.
[   27.858927] Checking 'hlt' instruction... OK.
[   27.874863] SMP alternatives: switching to UP code
[   27.875005] Freeing SMP alternatives: 11k freed
[   27.875209] Early unpacking initramfs... done
[   28.144783] ACPI: Core revision 20070126
[   28.144844] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.148274] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 02
[   28.148289] Total of 1 processors activated (4423.21 BogoMIPS).
[   28.148419] ENABLING IO-APIC IRQs
[   28.148594] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   28.294548] Brought up 1 CPUs
[   28.294634] Booting paravirtualized kernel on bare hardware
[   28.294670] Time: 22:11:03  Date: 02/09/108
[   28.294686] NET: Registered protocol family 16
[   28.294742] EISA bus registered
[   28.294749] ACPI: bus type pci registered
[   28.299245] PCI: PCI BIOS revision 3.00 entry at 0xfaa00, last bus=5
[   28.299246] PCI: Using configuration type 1
[   28.299248] Setting up standard PCI resources
[   28.302284] ACPI: EC: Look up EC in DSDT
[   28.307213] ACPI: Interpreter enabled
[   28.307215] ACPI: (supports S0 S3 S4 S5)
[   28.307226] ACPI: Using IOAPIC for interrupt routing
[   28.314623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.314627] PCI: Probing PCI hardware (bus 00)
[   28.314974] PCI: Transparent bridge - 0000:00:09.0
[   28.315197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.315408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.369520] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.369666] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.369812] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   28.369957] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   28.370104] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.370249] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.370394] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.370541] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.370686] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   28.370831] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.370976] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.371121] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   28.371268] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.371420] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.371573] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.371726] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   28.371884] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   28.372038] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   28.372191] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   28.372343] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   28.372446] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   28.372603] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   28.372760] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   28.372917] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   28.373074] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   28.373231] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   28.373388] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   28.373544] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   28.373703] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   28.373867] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   28.374030] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   28.374194] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   28.374271] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.374277] pnp: PnP ACPI init
[   28.374282] ACPI: bus type pnp registered
[   28.378449] pnp: PnP ACPI: found 13 devices
[   28.378451] ACPI: ACPI bus type pnp unregistered
[   28.378453] PnPBIOS: Disabled by ACPI PNP
[   28.378485] PCI: Using ACPI for IRQ routing
[   28.378488] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.428986] NET: Registered protocol family 8
[   28.428988] NET: Registered protocol family 20
[   28.429025] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   28.429028] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   28.429030] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   28.429032] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   28.429035] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   28.429037] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   28.429047] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   28.429050] pnp: 00:0c: iomem range 0xd1800-0xd3fff has been reserved
[   28.429053] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   28.429055] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   28.429058] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   28.430442] Time: tsc clocksource has been installed.
[   28.459217] PCI: Bridge: 0000:00:09.0
[   28.459219]   IO window: a000-afff
[   28.459222]   MEM window: fe900000-fe9fffff
[   28.459224]   PREFETCH window: fea00000-feafffff
[   28.459226] PCI: Bridge: 0000:00:0b.0
[   28.459228]   IO window: 9000-9fff
[   28.459231]   MEM window: fe800000-fe8fffff
[   28.459233]   PREFETCH window: fe700000-fe7fffff
[   28.459235] PCI: Bridge: 0000:00:0c.0
[   28.459237]   IO window: 8000-8fff
[   28.459239]   MEM window: fe600000-fe6fffff
[   28.459241]   PREFETCH window: fe500000-fe5fffff
[   28.459243] PCI: Bridge: 0000:00:0d.0
[   28.459245]   IO window: 7000-7fff
[   28.459248]   MEM window: fe400000-fe4fffff
[   28.459250]   PREFETCH window: fe300000-fe3fffff
[   28.459253] PCI: Bridge: 0000:00:0e.0
[   28.459255]   IO window: 6000-6fff
[   28.459257]   MEM window: fb000000-fdffffff
[   28.459260]   PREFETCH window: d0000000-dfffffff
[   28.459265] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   28.459270] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   28.459275] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   28.459280] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   28.459285] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   28.459293] NET: Registered protocol family 2
[   28.498427] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.498506] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   28.499394] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.499702] TCP: Hash tables configured (established 131072 bind 65536)
[   28.499704] TCP reno registered
[   28.510483] checking if image is initramfs... it is
[   28.962131] Switched to high resolution mode on CPU 0
[   29.038343] Freeing initrd memory: 7372k freed
[   29.038591] audit: initializing netlink socket (disabled)
[   29.038599] audit(1205100664.052:1): initialized
[   29.038642] highmem bounce pool size: 64 pages
[   29.039806] VFS: Disk quotas dquot_6.5.1
[   29.039838] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.039894] io scheduler noop registered
[   29.039896] io scheduler anticipatory registered
[   29.039897] io scheduler deadline registered
[   29.039908] io scheduler cfq registered (default)
[   29.054010] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   29.054017] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054022] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   29.054028] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054033] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   29.054040] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054044] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   29.054051] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   29.054056] Boot video device is 0000:05:00.0
[   29.054106] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.054122] assign_interrupt_mode Found MSI capability
[   29.054125] Allocate Port Service[0000:00:0b.0:pcie00]
[   29.054165] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   29.054181] assign_interrupt_mode Found MSI capability
[   29.054183] Allocate Port Service[0000:00:0c.0:pcie00]
[   29.054223] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   29.054238] assign_interrupt_mode Found MSI capability
[   29.054240] Allocate Port Service[0000:00:0d.0:pcie00]
[   29.054278] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.054294] assign_interrupt_mode Found MSI capability
[   29.054295] Allocate Port Service[0000:00:0e.0:pcie00]
[   29.054369] isapnp: Scanning for PnP cards...
[   29.406737] isapnp: No Plug & Play device found
[   29.422653] Real Time Clock Driver v1.12ac
[   29.422718] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.422790] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.422901] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.423255] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.423678] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.423812] input: Macintosh mouse button emulation as /class/input/input0
[   29.423880] PNP: No PS/2 controller found. Probing ports directly.
[   29.426974] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.426977] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.427075] mice: PS/2 mouse device common for all mice
[   29.427138] EISA: Probing bus 0 at eisa.0
[   29.427149] Cannot allocate resource for EISA slot 4
[   29.427153] Cannot allocate resource for EISA slot 6
[   29.427155] Cannot allocate resource for EISA slot 7
[   29.427157] Cannot allocate resource for EISA slot 8
[   29.427158] EISA: Detected 0 cards.
[   29.427218] TCP cubic registered
[   29.427226] NET: Registered protocol family 1
[   29.427241] Using IPI No-Shortcut mode
[   29.427359]   Magic number: 0:607:198
[   29.427392]   hash matches device ttypd
[   29.427649] Freeing unused kernel memory: 364k freed
[   30.606593] AppArmor: AppArmor initialized<5>audit(1205100665.552:2):  type=1505 info="AppArmor initialized" pid=1241
[   30.613210] fuse init (API version 7.8)
[   30.616849] Failure registering capabilities with primary security module.
[   30.619620] ACPI: Fan [FAN] (on)
[   30.622898] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   30.623795] ACPI: Thermal Zone [THRM] (40 C)
[   31.090472] usbcore: registered new interface driver usbfs
[   31.090493] usbcore: registered new interface driver hub
[   31.090507] usbcore: registered new device driver usb
[   31.091421] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   31.091428] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   31.091436] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   31.091439] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   31.091542] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   31.091564] ehci_hcd 0000:00:02.1: debug port 1
[   31.091567] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   31.091574] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfeb00000
[   31.091579] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.091648] usb usb1: configuration #1 chosen from 1 choice
[   31.091667] hub 1-0:1.0: USB hub found
[   31.091673] hub 1-0:1.0: 10 ports detected
[   31.107048] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.107052] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.117367] SCSI subsystem initialized
[   31.120800] libata version 2.21 loaded.
[   31.145765] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.150788] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   31.204029] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   31.204037] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 17
[   31.255781] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   31.272709] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   31.272717] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 18
[   31.272727] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.272730] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   31.272762] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   31.272774] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfebff000
[   31.330455] usb usb2: configuration #1 chosen from 1 choice
[   31.330476] hub 2-0:1.0: USB hub found
[   31.330484] hub 2-0:1.0: 10 ports detected
[   31.370751] Floppy drive(s): fd0 is 1.44M
[   31.402611] FDC 0 is a post-1991 82077
[   31.434544] sata_nv 0000:00:07.0: version 3.4
[   31.434881] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   31.434888] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 19
[   31.434891] sata_nv 0000:00:07.0: Using ADMA mode
[   31.434921] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   31.435003] scsi0 : sata_nv
[   31.435031] scsi1 : sata_nv
[   31.435074] ata1: SATA max UDMA/133 cmd 0xf884e480 ctl 0xf884e4a0 bmdma 0x0001cc00 irq 19
[   31.435077] ata2: SATA max UDMA/133 cmd 0xf884e580 ctl 0xf884e5a0 bmdma 0x0001cc08 irq 19
[   31.736084] usb 2-9: new low speed USB device using ohci_hcd and address 2
[   31.744079] ata1: SATA link down (SStatus 0 SControl 300)
[   31.950037] usb 2-9: configuration #1 chosen from 1 choice
[   31.962631] usbcore: registered new interface driver hiddev
[   31.973198] input: Logitech USB Receiver as /class/input/input1
[   31.973208] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-9
[   31.984259] input: Logitech USB Receiver as /class/input/input2
[   31.984360] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-9
[   31.984368] usbcore: registered new interface driver usbhid
[   31.984370] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.211752] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.219906] ata2.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   32.219908] ata2.00: 488397168 sectors, multi 16: LBA48 
[   32.227877] ata2.00: configured for UDMA/133
[   32.227950] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   32.227955] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   32.228331] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   32.228338] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   32.228341] sata_nv 0000:00:08.0: Using ADMA mode
[   32.228370] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   32.228428] scsi2 : sata_nv
[   32.228455] scsi3 : sata_nv
[   32.228500] ata3: SATA max UDMA/133 cmd 0xf8868480 ctl 0xf88684a0 bmdma 0x0001b800 irq 20
[   32.228503] ata4: SATA max UDMA/133 cmd 0xf8868580 ctl 0xf88685a0 bmdma 0x0001b808 irq 20
[   32.531570] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000142f9e]
[   32.539512] ata3: SATA link down (SStatus 0 SControl 300)
[   32.851288] ata4: SATA link down (SStatus 0 SControl 300)
[   32.851628] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   32.851631] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   32.851636] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   32.851641] forcedeth: using HIGHDMA
[   32.859626] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.859636] sd 1:0:0:0: [sda] Write Protect is off
[   32.859638] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.859649] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.859681] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.859687] sd 1:0:0:0: [sda] Write Protect is off
[   32.859689] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.859698] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.859701]  sda: sda1 sda2
[   32.870064] sd 1:0:0:0: [sda] Attached SCSI disk
[   32.873549] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   33.371384] eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
[   33.371561] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   33.371576] NFORCE-CK804: chipset revision 162
[   33.371578] NFORCE-CK804: not 100% native mode: will probe irqs later
[   33.371581] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   33.371585] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   33.371591]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   33.371598]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   33.371604] Probing IDE interface ide0...
[   33.658786] hda: SAMSUNG SP0812N, ATA DISK drive
[   34.330355] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.342245] Probing IDE interface ide1...
[   35.077773] hdc: PIONEER DVD-RW DVR-112L, ATAPI CD/DVD-ROM drive
[   35.413861] ide1 at 0x170-0x177,0x376 on irq 15
[   35.420196] hda: max request size: 512KiB
[   35.426014] hda: Host Protected Area detected.
[   35.426016]  current capacity is 156365903 sectors (80059 MB)
[   35.426017]  native  capacity is 156368016 sectors (80060 MB)
[   35.444448] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   35.444453] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   35.444455] ide: failed opcode was: 0x37
[   35.444469] hda: 156365903 sectors (80059 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   35.444839] hda: cache flushes supported
[   35.444867]  hda: hda1 hda2 < hda5 >
[   35.486284] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[   35.486291] Uniform CD-ROM driver Revision: 3.20
[   35.646113] Attempting manual resume
[   35.646115] swsusp: Resume From Partition 3:5
[   35.646117] PM: Checking swsusp image.
[   35.646253] PM: Resume from disk failed.
[   35.692137] kjournald starting.  Commit interval 5 seconds
[   35.692145] EXT3-fs: mounted filesystem with ordered data mode.
[   42.475216] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   42.475238] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4d00
[   42.482864] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.501977] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.895531] input: PC Speaker as /class/input/input3
[   43.085737] irda_init()
[   43.085749] NET: Registered protocol family 23
[   43.091783] parport_pc 00:0a: reported by Plug and Play ACPI
[   43.091821] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.196242] Linux agpgart interface v0.102 (c) Dave Jones
[   43.243213] nvidia: module license 'NVIDIA' taints kernel.
[   43.503881] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   43.503890] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   43.503896] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   43.504055] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   43.695331] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   43.695335] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 18
[   43.695349] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   44.015329] intel8x0_measure_ac97_clock: measured 54775 usecs
[   44.015332] intel8x0: clocking to 46950
[   44.665549] lp0: using parport0 (interrupt-driven).
[   44.701178] it87: Found IT8712F chip at 0x290, revision 6
[   44.750651] Adding 3229024k swap on /dev/hda5.  Priority:-1 extents:1 across:3229024k
[   45.147946] EXT3 FS on hda1, internal journal
[   45.325826] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   46.766130] input: Power Button (FF) as /class/input/input4
[   46.769477] ACPI: Power Button (FF) [PWRF]
[   46.798640] input: Power Button (CM) as /class/input/input5
[   46.801968] ACPI: Power Button (CM) [PWRB]
[   46.889900] No dock devices found.
[   47.128651] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   47.132840] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   48.189626] Failure registering capabilities with primary security module.
[   48.390653] ppdev: user-space parallel port driver
[   48.658518] audit(1205100683.831:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5046 profile="/usr/sbin/cupsd"
[   48.750026] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.750030] apm: overridden by ACPI.
[   50.641137] /dev/vmmon[5264]: Module vmmon: registered with major=10 minor=165
[   50.641419] /dev/vmmon[5264]: Module vmmon: initialized
[   50.870998] /dev/vmnet: open called by PID 5306 (vmnet-bridge)
[   50.871233] /dev/vmnet: hub 0 does not exist, allocating memory.
[   50.871432] /dev/vmnet: port on hub 0 successfully opened
[   50.871620] bridge-eth0: enabling the bridge
[   50.871781] bridge-eth0: up
[   50.871913] bridge-eth0: already up
[   50.871916] bridge-eth0: attached
[   50.919056] /dev/vmnet: open called by PID 5320 (vmnet-natd)
[   50.919299] /dev/vmnet: hub 8 does not exist, allocating memory.
[   50.919500] /dev/vmnet: port on hub 8 successfully opened
[   50.927862] /dev/vmnet: open called by PID 5321 (vmnet-netifup)
[   50.928096] /dev/vmnet: hub 1 does not exist, allocating memory.
[   50.928305] /dev/vmnet: port on hub 1 successfully opened
[   50.930801] /dev/vmnet: open called by PID 5322 (vmnet-netifup)
[   50.931042] /dev/vmnet: port on hub 8 successfully opened
[   51.753496] /dev/vmnet: open called by PID 5365 (vmnet-dhcpd)
[   51.753616] /dev/vmnet: port on hub 8 successfully opened
[   51.754322] /dev/vmnet: open called by PID 5364 (vmnet-dhcpd)
[   51.754438] /dev/vmnet: port on hub 1 successfully opened
[   56.139349] NET: Registered protocol family 17
[   60.001239] NET: Registered protocol family 10
[   60.001698] lo: Disabled Privacy Extensions
[   70.285290] eth0: no IPv6 routers present
[   70.769184] vmnet8: no IPv6 routers present
[   70.897160] vmnet1: no IPv6 routers present
[  137.003976] usb 1-10: new high speed USB device using ehci_hcd and address 3
[  137.137873] usb 1-10: configuration #1 chosen from 1 choice
[  137.340911] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x170A
[  137.341300] usbcore: registered new interface driver usblp
[  137.341486] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  137.413605] usbcore: registered new interface driver libusual
[  137.689614] Initializing USB Mass Storage driver...
[  137.689885] scsi4 : SCSI emulation for USB Mass Storage devices
[  137.690114] usb-storage: device found at 3
[  137.690116] usb-storage: waiting for device to settle before scanning
[  137.690488] usbcore: registered new interface driver usb-storage
[  137.690688] USB Mass Storage support registered.
[  142.684377] usb-storage: device scan complete
[  142.685750] scsi 4:0:0:0: Direct-Access     Canon    MP170Storage     0108 PQ: 0 ANSI: 2
[  142.690382] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  142.690407] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  178.792033] sd 4:0:0:0: [sdb] 994304 512-byte hardware sectors (509 MB)
[  178.793782] sd 4:0:0:0: [sdb] Write Protect is on
[  178.793785] sd 4:0:0:0: [sdb] Mode Sense: 37 00 80 08
[  178.793787] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  178.796902] sd 4:0:0:0: [sdb] 994304 512-byte hardware sectors (509 MB)
[  178.798778] sd 4:0:0:0: [sdb] Write Protect is on
[  178.798781] sd 4:0:0:0: [sdb] Mode Sense: 37 00 80 08
[  178.798783] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  178.798785]  sdb: sdb1
[  247.803841] usb 1-10: USB disconnect, address 3
[  247.804000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[  247.930021] scsi 4:0:0:0: rejecting I/O to dead device
[  265.304501] usb 2-6: new full speed USB device using ohci_hcd and address 3
[  265.522239] usb 2-6: configuration #1 chosen from 1 choice
[  309.136675] usb-storage: probe of 2-6:1.0 failed with error -1
[  309.136770] usb 2-6: USB disconnect, address 3
[  621.774338] usb 2-6: new full speed USB device using ohci_hcd and address 4
[  621.991698] usb 2-6: configuration #1 chosen from 1 choice
steve@steve-desktop:~$ 

```

---

### Post by herbster on 2008-03-09
So both are working now? It would appear it's loading the module properly.

---

### Post by bossa on 2008-03-09
> **herbster said:**
> So both are working now? It would appear it's loading the module properly.

The stand alone does not show in "computer" or give me an option to import images on inserting SD  card. Printer Card reader works every time now

---

