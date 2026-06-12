---
title: "[SOLVED] My Ubuntu 7.10 Takes forever to boot up..anyone have this problem?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by UMD TERPS FAN on 2008-01-25
I just did a complete install NO dual boot.  So far Ubuntu 7.10 64 bit has been running  good, however it takes forever to boot up (5 minutes or so).  Anyone have this problem?  My computer is a Gateway MX6446 AMD Turion 64 2GHZ 1 GB ram etc.  Any help to make it boot fast would be great!

Thanks,

Grant

---

### Post by shutslar on 2008-01-25
If you go to System > Administration > System Log > syslog

What does it say is happening as you boot up?

---

### Post by ByteJuggler on 2008-01-25
I have seen this issue (or something like it) when running SATA drives in "IDE" mode in the BIOS on some controllers (ICH9R for example.)  Setting to RAID (even for a single drive),  or I *think* AHCI mode, cures the problem.

It would be clarifying to know what takes so long during the boot process.  To help diagnose, please press Alt-F2, which should bring up a "Run" dialog, and copy & paste or enter the following command into it, then press enter:

```
dmesg > /tmp/dmsg.txt; gedit /tmp/dmsg.txt
```

This command line will put the output of the dmsg command into a text editor window from where you can copy and paste it.

The number along the left side, btw, is a time indicator, so wherever you see large gaps in the numbers, is where the boot process waited for some reason.

---

### Post by UMD TERPS FAN on 2008-01-25
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=63537ed2-153b-4cca-8220-24856c8afe30 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e80000 (usable)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037e91000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e91000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228992) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F88E0 checksum 0
[    0.000000] ACPI: RSDP 000F88E0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 37E8B5D3, 0034 (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] ACPI: FACP 37E90DEB, 0074 (r1 GATEWA M367     20060904 ATI     F4240)
[    0.000000] ACPI: DSDT 37E8B607, 57E4 (r1 GATEWA M367     20060904 MSFT  100000E)
[    0.000000] ACPI: FACS 37E91FC0, 0040
[    0.000000] ACPI: SSDT 37E90E5F, 0115 (r1 GATEWA M367     20060904  LTP        1)
[    0.000000] ACPI: APIC 37E90F74, 0050 (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] ACPI: MCFG 37E90FC4, 003C (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037e80000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228992) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037e80000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   228992
[    0.000000] On node 0 totalpages: 228893
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3074 pages used for memmap
[    0.000000]   DMA32 zone: 221822 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 224638
[    0.000000] Kernel command line: root=UUID=63537ed2-153b-4cca-8220-24856c8afe30 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.361445] time.c: Detected 1995.025 MHz processor.
[   14.362357] Console: colour VGA+ 80x25
[   14.362372] Checking aperture...
[   14.362375] CPU 0: aperture @ d456000000 size 32 MB
[   14.362377] Aperture too small (32 MB)
[   14.374056] No AGP bridge found
[   14.381858] Memory: 890672k/915968k available (2274k kernel code, 24900k reserved, 1181k data, 296k init)
[   14.381908] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.459396] Calibrating delay using timer specific routine.. 3994.05 BogoMIPS (lpj=7988105)
[   14.459429] Security Framework v1.0.0 initialized
[   14.459435] SELinux:  Disabled at boot.
[   14.459524] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.460159] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.460437] Mount-cache hash table entries: 256
[   14.460575] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.460577] CPU: L2 Cache: 512K (64 bytes/line)
[   14.460580] CPU 0/0 -> Node 0
[   14.460598] SMP alternatives: switching to UP code
[   14.460754] Freeing SMP alternatives: 24k freed
[   14.461066] Early unpacking initramfs... done
[   14.769468] ACPI: Core revision 20070126
[   14.769525] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.219435] Using local APIC timer interrupts.
[   15.269536] result 12468905
[   15.269537] Detected 12.468 MHz APIC timer.
[   15.271032] Brought up 1 CPUs
[   15.271230] NET: Registered protocol family 16
[   15.271310] ACPI: bus type pci registered
[   15.271317] PCI: Using configuration type 1
[   15.272057] ACPI: EC: Look up EC in DSDT
[   15.272969] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   15.274057] ACPI: Interpreter enabled
[   15.274060] ACPI: (supports S0 S3 S4 S5)
[   15.274074] ACPI: Using IOAPIC for interrupt routing
[   15.278582] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   15.278618] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.278629] PCI: Probing PCI hardware (bus 00)
[   15.279933] PCI: Transparent bridge - 0000:00:14.4
[   15.280035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.280184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   15.280287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   15.280402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   15.280493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   15.282676] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.282805] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.282932] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283099] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283226] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283353] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283480] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283607] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283734] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 11) *0, disabled.
[   15.283805] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.283817] pnp: PnP ACPI init
[   15.283825] ACPI: bus type pnp registered
[   15.285902] pnp: PnP ACPI: found 10 devices
[   15.285905] ACPI: ACPI bus type pnp unregistered
[   15.285965] PCI: Using ACPI for IRQ routing
[   15.285968] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.286065] NET: Registered protocol family 8
[   15.286067] NET: Registered protocol family 20
[   15.286180] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.286183] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.286187] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.286198] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   15.286201] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   15.286204] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   15.286207] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.286212] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   15.286215] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   15.286218] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   15.286474] PCI: Bridge: 0000:00:01.0
[   15.286477]   IO window: 9000-9fff
[   15.286480]   MEM window: c0100000-c01fffff
[   15.286483]   PREFETCH window: c8000000-cfffffff
[   15.286486] PCI: Bridge: 0000:00:04.0
[   15.286488]   IO window: a000-afff
[   15.286491]   MEM window: c0200000-c02fffff
[   15.286493]   PREFETCH window: disabled.
[   15.286496] PCI: Bridge: 0000:00:05.0
[   15.286497]   IO window: disabled.
[   15.286500]   MEM window: c0300000-c03fffff
[   15.286502]   PREFETCH window: disabled.
[   15.286511] PCI: Bus 9, cardbus bridge: 0000:08:09.0
[   15.286513]   IO window: 00002000-000020ff
[   15.286519]   IO window: 00002400-000024ff
[   15.286524]   PREFETCH window: 50000000-53ffffff
[   15.286530]   MEM window: 54000000-57ffffff
[   15.286535] PCI: Bridge: 0000:00:14.4
[   15.286539]   IO window: 2000-2fff
[   15.286545]   MEM window: c0400000-c04fffff
[   15.286550]   PREFETCH window: 50000000-53ffffff
[   15.286568] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.286575] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.286603] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   15.286657] NET: Registered protocol family 2
[   15.286982] Time: tsc clocksource has been installed.
[   15.323023] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.323363] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   15.325026] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.325554] TCP: Hash tables configured (established 131072 bind 65536)
[   15.325557] TCP reno registered
[   15.335086] checking if image is initramfs... it is
[   15.936242] Freeing initrd memory: 7749k freed
[   15.940607] audit: initializing netlink socket (disabled)
[   15.940619] audit(1201309695.136:1): initialized
[   15.942365] VFS: Disk quotas dquot_6.5.1
[   15.942414] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.942505] io scheduler noop registered
[   15.942507] io scheduler anticipatory registered
[   15.942509] io scheduler deadline registered
[   15.942591] io scheduler cfq registered (default)
[   15.942597] PCI: MSI quirk detected. MSI deactivated.
[   15.943083] Boot video device is 0000:01:05.0
[   15.943225] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.943243] assign_interrupt_mode Found MSI capability
[   15.943248] Allocate Port Service[0000:00:04.0:pcie00]
[   15.943306] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.943323] assign_interrupt_mode Found MSI capability
[   15.943326] Allocate Port Service[0000:00:05.0:pcie00]
[   15.964712] Real Time Clock Driver v1.12ac
[   15.964789] Linux agpgart interface v0.102 (c) Dave Jones
[   15.964792] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.965726] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.965923] input: Macintosh mouse button emulation as /class/input/input0
[   15.965985] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   15.968518] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.968524] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.968700] mice: PS/2 mouse device common for all mice
[   15.968811] TCP cubic registered
[   15.968877] NET: Registered protocol family 1
[   15.969058] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.969065] Freeing unused kernel memory: 296k freed
[   16.038677] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.131787] AppArmor: AppArmor initialized<5>audit(1201309696.328:2):  type=1505 info="AppArmor initialized" pid=1214
[   17.248233] fuse init (API version 7.8)
[   17.348795] Failure registering capabilities with primary security module.
[   17.452588] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   17.452594] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.452604] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.849767] ACPI: Thermal Zone [THRM] (55 C)
[   27.714739] usbcore: registered new interface driver usbfs
[   27.714763] usbcore: registered new interface driver hub
[   27.714783] usbcore: registered new device driver usb
[   27.715445] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.715484] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   27.715574] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.715732] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.715754] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[   27.768959] usb usb1: configuration #1 chosen from 1 choice
[   27.768984] hub 1-0:1.0: USB hub found
[   27.768996] hub 1-0:1.0: 4 ports detected
[   27.872906] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   27.873016] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.873068] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.873090] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[   27.928889] usb usb2: configuration #1 chosen from 1 choice
[   27.928919] hub 2-0:1.0: USB hub found
[   27.928931] hub 2-0:1.0: 4 ports detected
[   28.040397] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   28.040510] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   28.040565] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   28.040626] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[   28.040639] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.040736] usb usb3: configuration #1 chosen from 1 choice
[   28.040762] hub 3-0:1.0: USB hub found
[   28.040769] hub 3-0:1.0: 8 ports detected
[   28.367135] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.367141] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.367870] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   28.367890] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   28.367901] ATIIXP: chipset revision 128
[   28.367904] ATIIXP: not 100% native mode: will probe irqs later
[   28.367913]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA
[   28.367927] ATIIXP: simplex device: DMA disabled
[   28.367928] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   28.367932] Probing IDE interface ide0...
[   28.656808] hda: HTS421210H9AT00, ATA DISK drive
[   29.440406] hdb: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[   29.495974] hda: selected mode 0x45
[   29.496247] hdb: selected mode 0x42
[   29.497163] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.874888] Probing IDE interface ide1...
[   30.442719] SCSI subsystem initialized
[   30.447646] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 21 (level, low) -> IRQ 21
[   30.498209] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0405000-c04057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.499149] libata version 2.21 loaded.
[   30.507997] hda: max request size: 512KiB
[   30.514952] hda: 195371568 sectors (100030 MB) w/7528KiB Cache, CHS=16383/255/63, UDMA(100)
[   30.515246] hda: cache flushes supported
[   30.515297]  hda: hda1 hda2 < hda5 >
[   30.592611] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   30.592621] Uniform CD-ROM driver Revision: 3.20
[   31.766940] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80367007af0]
[   32.386818] Attempting manual resume
[   32.386822] swsusp: Resume From Partition 3:5
[   32.386824] PM: Checking swsusp image.
[   32.486472] PM: Resume from disk failed.
[   33.498022] kjournald starting.  Commit interval 5 seconds
[   33.498032] EXT3-fs: mounted filesystem with ordered data mode.
[  121.556238] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  121.561972] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  121.832756] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  121.832771] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  121.832884] sky2 0000:02:00.0: v1.18 addr 0xc0200000 irq 16 Yukon-FE (0xb7) rev 1
[  121.833061] sky2 eth0: addr 00:e0:b8:b8:8b:e6
[  121.927140] ieee80211_crypt: registered algorithm 'NULL'
[  121.930175] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  121.930179] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  121.943009] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  121.999628] bcm43xx driver
[  121.999731] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  121.999742] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  123.198278] Yenta: CardBus bridge found at 0000:08:09.0 [107b:0367]
[  123.198306] Yenta: Using CSCINT to route CSC interrupts to PCI
[  123.198308] Yenta: Routing CardBus interrupts to PCI
[  123.198315] Yenta TI: socket 0000:08:09.0, mfunc 0x01ac1b22, devctl 0x64
[  123.215977] input: PC Speaker as /class/input/input2
[  123.430350] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[  123.430356] Socket status: 30000868
[  123.430360] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[  123.430364] pcmcia: parent PCI bridge Memory window: 0xc0400000 - 0xc04fffff
[  123.430367] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[  123.430678] ACPI: PCI Interrupt 0000:08:09.2[A] -> GSI 20 (level, low) -> IRQ 20
[  123.835393] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[  124.065280] pccard: CardBus card inserted into slot 0
[  124.079116] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[  124.111782] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[  124.720769] ath_hal: module license 'Proprietary' taints kernel.
[  124.721979] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  124.912092] wlan: 0.8.4.2 (0.9.3.2)
[  124.955527] ath_pci: 0.9.4.5 (0.9.3.2)
[  124.956037] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
[  124.956047] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[  125.648974] ath_rate_sample: 1.2 (0.9.3.2)
[  125.650219] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  125.650225] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  125.650233] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  125.650238] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  125.650241] wifi0: mac 7.9 phy 4.5 radio 5.6
[  125.650246] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  125.650248] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  125.650250] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  125.650252] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  125.650253] wifi0: Use hw queue 8 for CAB traffic
[  125.650255] wifi0: Use hw queue 9 for beacons
[  125.685538] wifi0: Atheros 5212: mem=0x54000000, irq=20
[  126.716744] lp: driver loaded but no devices found
[  127.321279] Adding 2626588k swap on /dev/hda5.  Priority:-1 extents:1 across:2626588k
[  128.968584] EXT3 FS on hda1, internal journal
[  135.439586] ACPI: Battery Slot [BAT1] (battery absent)
[  135.865525] No dock devices found.
[  136.587021] ACPI: AC Adapter [ACAD] (on-line)
[  137.006272] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  137.136633] input: Power Button (FF) as /class/input/input4
[  137.140604] ACPI: Power Button (FF) [PWRF]
[  137.163263] input: Lid Switch as /class/input/input5
[  137.167200] ACPI: Lid Switch [LID]
[  137.189824] input: Sleep Button (CM) as /class/input/input6
[  137.193753] ACPI: Sleep Button (CM) [SLPB]
[  137.216376] input: Power Button (CM) as /class/input/input7
[  137.220292] ACPI: Power Button (CM) [PWRB]
[  139.391620] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[  139.391660] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[  139.391663] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[  139.391665] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[  139.391668] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[  147.205016] sky2 eth0: enabling interface
[  147.394743] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  147.501991] ppdev: user-space parallel port driver
[  149.135331] audit(1201309829.356:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5005 profile="/usr/sbin/cupsd"
[  150.494823] Failure registering capabilities with primary security module.
[  150.620821] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  152.048027] Bluetooth: Core ver 2.11
[  152.048129] NET: Registered protocol family 31
[  152.048132] Bluetooth: HCI device and connection manager initialized
[  152.048135] Bluetooth: HCI socket layer initialized
[  152.130827] Bluetooth: L2CAP ver 2.8
[  152.130832] Bluetooth: L2CAP socket layer initialized
[  152.202323] Bluetooth: RFCOMM socket layer initialized
[  152.202399] Bluetooth: RFCOMM TTY layer initialized
[  152.202402] Bluetooth: RFCOMM ver 1.8
[  162.753414] Marking TSC unstable due to possible TSC halt in C2
[  162.754016] Time: acpi_pm clocksource has been installed.
[  168.506348] hda-intel: Invalid position buffer, using LPIB read method instead.
[  168.807056] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  178.874100] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  182.316372] NET: Registered protocol family 17
[  189.474560] NET: Registered protocol family 10
[  189.474696] lo: Disabled Privacy Extensions
[  189.474819] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  193.475923] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  193.991165] ath0: no IPv6 routers present
[  205.838153] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  219.267484] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  277.748459] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  351.665180] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  369.301449] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  383.685710] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  396.812036] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  408.562577] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  424.003345] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  488.463783] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  549.311264] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  607.800149] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  668.192837] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  728.453361] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  785.829450] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  850.362900] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  913.215994] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  969.222050] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1025.511424] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1089.167709] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1140.487935] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1199.969551] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1269.178004] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1320.744730] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1370.771620] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1434.420279] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1501.423957] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1563.498439] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1630.849590] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1697.240673] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1708.866229] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1725.666219] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1737.640404] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1751.064163] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

What should I delete? I dont want to delete a critical file:)...Btw I'm using a Dlink PCI wireless card instead of the integrated broadcom wireless card, because Ubuntu does not support Broadcom wireless.

Thanks,

Grant
[ 1765.451612] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by MikeyXX on 2008-01-25
This is what I did. Don't know where i got  the instructions, but I can't find them again.

1) Edit menu.lst
```
 sudo gedit /boot/grub/menu.lst
```

2) At the very end of the kernel line after "splash" , add "vga=791" 
```
 title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e25fb39e-cded-4529-9537-1861e4637173 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quie t
```

3) Save that file, close it, and open up usplash's config file:
```
sudo gedit /etc/usplash.conf
```

Should look like this (if your resolution is 1440 x 900 of course)
```
# Usplash configuration file
xres=1440
yres=900
```

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

```
uname -r
```
This lists your current kernel version.
```

sudo update-initramfs -u -k <insert results from uname -r here>
```

This rebuilds the image that Grub uses to start the system.


It worked for me. Turns out the usplash routine picks up the wrong resolution and pauses. Dunno why, but again, this worked for me.

---

### Post by smurphy_it on 2008-01-25
I don't know how much help I can be for speeding up the boot process, but I know that the broadcom wireless driver is still trying to initialize, as is indicated at the end of your log with the **bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.**

You can disable the broadcom driver from even initializing which might help a little bit for speeding up the boot process.

in a terminal type **sudo gedit /etc/modprobe.d/blacklist** and then go to the very end of the file and add this command [B][COLOR="DarkRed"]blacklist bcm43xx
[/COLOR][/B]
This will blacklist the broadcom wireless card and stop it from attempting to load on bootup.

---

### Post by UMD TERPS FAN on 2008-01-25
> **ByteJuggler said:**
> I have seen this issue (or something like it) when running SATA drives in "IDE" mode in the BIOS on some controllers (ICH9R for example.)  Setting to RAID (even for a single drive),  or I *think* AHCI mode, cures the problem.

It would be clarifying to know what takes so long during the boot process.  To help diagnose, please press Alt-F2, which should bring up a "Run" dialog, and copy & paste or enter the following command into it, then press enter:

```
dmesg > /tmp/dmsg.txt; gedit /tmp/dmsg.txt
```

This command line will put the output of the dmsg command into a text editor window from where you can copy and paste it.

The number along the left side, btw, is a time indicator, so wherever you see large gaps in the numbers, is where the boot process waited for some reason.

Do you just delete what failed or takes long to load?

-Grant

---

### Post by UMD TERPS FAN on 2008-01-25
hmmmm I deteled the broadcom crap with blacklisting it, however it still takes a while to boot.  My Gateway has a ATI Xpress 200m, its comming up under the restricted driver Manager as well as the Broadcom wireless.......im still having trouble...

Thanks for the help!

-Grant

---

### Post by zerofill on 2008-01-25
Same stuff happens to me...but mine happened after I added the bcm43xx fwcutter driver to it....So I could use my wireless....for whatever reason it makes booting take forever!

---

### Post by nshorts on 2008-01-28
> **MikeyXX said:**
> This is what I did. Don't know where i got  the instructions, but I can't find them again.

1) Edit menu.lst
```
 sudo gedit /boot/grub/menu.lst
```

2) At the very end of the kernel line after "splash" , add "vga=791" 
```
 title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e25fb39e-cded-4529-9537-1861e4637173 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quie t
```

3) Save that file, close it, and open up usplash's config file:
```
sudo gedit /etc/usplash.conf
```

Should look like this (if your resolution is 1440 x 900 of course)
```
# Usplash configuration file
xres=1440
yres=900
```

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

```
uname -r
```
This lists your current kernel version.
```

sudo update-initramfs -u -k <insert results from uname -r here>
```

This rebuilds the image that Grub uses to start the system.


It worked for me. Turns out the usplash routine picks up the wrong resolution and pauses. Dunno why, but again, this worked for me.

Your post just fixed 3 machines- THANK YOU!

---

### Post by MikeyXX on 2008-01-31
GREAT!

I'm glad it worked out. Took me forever to trip over that information. Hopefully it helps others as well.

---

