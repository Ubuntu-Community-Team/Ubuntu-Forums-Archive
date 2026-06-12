---
title: "very slow boot with gusty"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by drvista on 2007-10-18
my ubuntu gusty is very slow at boot and i don't know why any suggestions

---

### Post by drvista on 2007-10-18
this is my dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f69d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f69d000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7860
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77B0 checksum 0
[    0.000000] ACPI: RSDP 000F77B0, 0014 (r0 FSC   )
[    0.000000] ACPI: RSDT 3F697739, 0044 (r1 FSC    PC        6040000  LTP        0)
[    0.000000] ACPI: FACP 3F69CE20, 0074 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 3F69837D, 4AA3 (r1 UW____ F34_____  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F69DFC0, 0040
[    0.000000] ACPI: APIC 3F69CE94, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F69CEFC, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F69CF34, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 3F69CF70, 0068 (r1 FSC    PC        6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F69CFD8, 0028 (r1 MSTEST TESTONLY  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F698173, 020A (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F69777D, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257699
[    0.000000] Kernel command line: root=UUID=fdc55d7d-0a22-4d76-9a93-f0b00d5495b0 ro quiet splash profile
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1866.931 MHz processor.
[   87.705441] Console: colour VGA+ 80x25
[   87.705737] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   87.706096] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   87.736301] Memory: 1018176k/1038912k available (2015k kernel code, 19960k reserved, 916k data, 364k init, 121408k highmem)
[   87.736310] virtual kernel memory layout:
[   87.736311]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   87.736313]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   87.736314]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   87.736315]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   87.736316]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   87.736318]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   87.736319]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   87.736322] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   87.736356] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   87.736489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   87.736493] hpet0: 3 64-bit timers, 14318180 Hz
[   87.817431] Calibrating delay using timer specific routine.. 3737.65 BogoMIPS (lpj=7475301)
[   87.817452] Security Framework v1.0.0 initialized
[   87.817459] SELinux:  Disabled at boot.
[   87.817471] Mount-cache hash table entries: 512
[   87.817582] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   87.817590] monitor/mwait feature present.
[   87.817592] using mwait in idle threads.
[   87.817596] CPU: L1 I cache: 32K, L1 D cache: 32K
[   87.817598] CPU: L2 cache: 2048K
[   87.817601] CPU: Physical Processor ID: 0
[   87.817603] CPU: Processor Core ID: 0
[   87.817604] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   87.817613] Compat vDSO mapped to ffffe000.
[   87.817624] Checking 'hlt' instruction... OK.
[   87.833517] SMP alternatives: switching to UP code
[   87.833931] Early unpacking initramfs... done
[   88.148132] ACPI: Core revision 20070126
[   88.148190] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   88.166407] CPU0: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   88.166424] SMP alternatives: switching to SMP code
[   88.166548] Booting processor 1/1 eip 3000
[   88.176768] Initializing CPU#1
[   88.256980] Calibrating delay using timer specific routine.. 3733.46 BogoMIPS (lpj=7466939)
[   88.256987] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   88.256992] monitor/mwait feature present.
[   88.256995] CPU: L1 I cache: 32K, L1 D cache: 32K
[   88.256998] CPU: L2 cache: 2048K
[   88.257000] CPU: Physical Processor ID: 0
[   88.257001] CPU: Processor Core ID: 1
[   88.257003] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   88.257544] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   88.257568] Total of 2 processors activated (7471.12 BogoMIPS).
[   88.257764] ENABLING IO-APIC IRQs
[   88.257974] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   88.404925] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   88.424923] Brought up 2 CPUs
[   88.542455] migration_cost=47
[   88.542592] Booting paravirtualized kernel on bare hardware
[   88.542684] Time: 16:54:00  Date: 09/18/107
[   88.542705] NET: Registered protocol family 16
[   88.542788] EISA bus registered
[   88.542793] ACPI: bus type pci registered
[   88.581618] PCI: PCI BIOS revision 2.10 entry at 0xfd843, last bus=6
[   88.581620] PCI: Using configuration type 1
[   88.581622] Setting up standard PCI resources
[   88.585432] ACPI: EC: Look up EC in DSDT
[   88.585983] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   88.587319] ACPI: System BIOS is requesting _OSI(Linux)
[   88.587321] ACPI: Please test with "acpi_osi=!Linux"
[   88.587322] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   88.587859] ACPI: Interpreter enabled
[   88.587862] ACPI: (supports S0 S3 S4 S5)
[   88.587877] ACPI: Using IOAPIC for interrupt routing
[   88.593151] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   88.593202] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   88.593213] PCI: Probing PCI hardware (bus 00)
[   88.593959] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   88.593963] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   88.595061] PCI: Transparent bridge - 0000:00:1e.0
[   88.595136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   88.595425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   88.595541] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   88.595656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   88.595785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   88.598615] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   88.598705] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   88.598792] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   88.598878] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   88.598964] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   88.599050] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   88.599137] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   88.599222] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   88.599331] Linux Plug and Play Support v0.97 (c) Adam Belay
[   88.599340] pnp: PnP ACPI init
[   88.599347] ACPI: bus type pnp registered
[   88.600973] pnp: PnP ACPI: found 11 devices
[   88.600975] ACPI: ACPI bus type pnp unregistered
[   88.600979] PnPBIOS: Disabled by ACPI PNP
[   88.601020] PCI: Using ACPI for IRQ routing
[   88.601022] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   88.601102] PCI: Cannot allocate resource region 0 of device 0000:05:00.0
[   88.621888] NET: Registered protocol family 8
[   88.621890] NET: Registered protocol family 20
[   88.621956] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   88.621959] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   88.621962] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   88.621965] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   88.621972] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   88.621978] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   88.621981] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   88.624616] Time: tsc clocksource has been installed.
[   88.624630] Switched to high resolution mode on CPU 0
[   88.624716] Switched to high resolution mode on CPU 1
[   88.652268] PCI: Bridge: 0000:00:1c.0
[   88.652271]   IO window: f000-ffff
[   88.652278]   MEM window: fac00000-febfffff
[   88.652282]   PREFETCH window: disabled.
[   88.652288] PCI: Bridge: 0000:00:1c.1
[   88.652289]   IO window: disabled.
[   88.652295]   MEM window: disabled.
[   88.652299]   PREFETCH window: disabled.
[   88.652317] PCI: Bridge: 0000:00:1c.2
[   88.652318]   IO window: disabled.
[   88.652324]   MEM window: f7000000-f70fffff
[   88.652329]   PREFETCH window: disabled.
[   88.652338] PCI: Bridge: 0000:00:1e.0
[   88.652341]   IO window: 2000-2fff
[   88.652347]   MEM window: f0200000-f02fffff
[   88.652351]   PREFETCH window: disabled.
[   88.652378] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   88.652384] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   88.652393] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   88.652417] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   88.652424] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   88.652447] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
[   88.652452] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   88.652459] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   88.652473] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   88.652484] NET: Registered protocol family 2
[   88.692536] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   88.692596] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   88.693586] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   88.693956] TCP: Hash tables configured (established 131072 bind 65536)
[   88.693959] TCP reno registered
[   88.708641] checking if image is initramfs... it is
[   89.332481] Freeing initrd memory: 7118k freed
[   89.332601] Simple Boot Flag at 0x35 set to 0x1
[   89.333083] audit: initializing netlink socket (disabled)
[   89.333098] audit(1192726440.252:1): initialized
[   89.333199] highmem bounce pool size: 64 pages
[   89.335027] VFS: Disk quotas dquot_6.5.1
[   89.335075] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   89.335165] io scheduler noop registered
[   89.335167] io scheduler anticipatory registered
[   89.335171] io scheduler deadline registered
[   89.335184] io scheduler cfq registered (default)
[   89.335199] Boot video device is 0000:00:02.0
[   89.335366] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   89.335423] assign_interrupt_mode Found MSI capability
[   89.335426] Allocate Port Service[0000:00:1c.0:pcie00]
[   89.335461] Allocate Port Service[0000:00:1c.0:pcie02]
[   89.335556] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   89.335613] assign_interrupt_mode Found MSI capability
[   89.335615] Allocate Port Service[0000:00:1c.1:pcie00]
[   89.335646] Allocate Port Service[0000:00:1c.1:pcie02]
[   89.335746] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   89.335803] assign_interrupt_mode Found MSI capability
[   89.335805] Allocate Port Service[0000:00:1c.2:pcie00]
[   89.335834] Allocate Port Service[0000:00:1c.2:pcie02]
[   89.335999] isapnp: Scanning for PnP cards...
[   89.689619] isapnp: No Plug & Play device found
[   89.710378] Real Time Clock Driver v1.12ac
[   89.710617] hpet_resources: 0xfed00000 is busy
[   89.710646] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   89.711701] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   89.711827] input: Macintosh mouse button emulation as /class/input/input0
[   89.711897] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   89.714142] i8042.c: Detected active multiplexing controller, rev 1.1.
[   89.715404] serio: i8042 KBD port at 0x60,0x64 irq 1
[   89.715408] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   89.715411] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   89.715413] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   89.715416] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   89.715618] mice: PS/2 mouse device common for all mice
[   89.715913] EISA: Probing bus 0 at eisa.0
[   89.715922] Cannot allocate resource for EISA slot 1
[   89.715926] Cannot allocate resource for EISA slot 2
[   89.715953] EISA: Detected 0 cards.
[   89.716136] TCP cubic registered
[   89.716152] NET: Registered protocol family 1
[   89.716175] Using IPI No-Shortcut mode
[   89.716329]   Magic number: 11:963:944
[   89.716392]   hash matches device ptyyf
[   89.716449]   hash matches device tty1
[   89.716668] Freeing unused kernel memory: 364k freed
[   89.793236] input: AT Translated Set 2 keyboard as /class/input/input1
[   90.908227] AppArmor: AppArmor initialized<5>audit(1192726441.752:2):  type=1505 info="AppArmor initialized" pid=1260
[   90.913554] fuse init (API version 7.8)
[   90.917481] Failure registering capabilities with primary security module.
[   90.934226] ACPI: SSDT 3F697EBE, 022C (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   90.934421] ACPI: SSDT 3F697C73, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   90.934654] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   90.934659] ACPI: Processor [CPU0] (supports 8 throttling states)
[   90.934876] ACPI: SSDT 3F6980EA, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   90.935048] ACPI: SSDT 3F697E39, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   90.935307] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])

---

### Post by drvista on 2007-10-18
[   90.935312] ACPI: Processor [CPU1] (supports 8 throttling states)
[   90.936569] ACPI: Thermal Zone [THRM] (62 C)
[    3.076000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.080000] Time: hpet clocksource has been installed.
[    3.456000] usbcore: registered new interface driver usbfs
[    3.456000] usbcore: registered new interface driver hub
[    3.456000] usbcore: registered new device driver usb
[    3.456000] USB Universal Host Controller Interface driver v3.0
[    3.456000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.456000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.456000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.456000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.456000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.456000] usb usb1: configuration #1 chosen from 1 choice
[    3.456000] hub 1-0:1.0: USB hub found
[    3.456000] hub 1-0:1.0: 2 ports detected
[    3.520000] SCSI subsystem initialized
[    3.528000] libata version 2.21 loaded.
[    3.560000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.560000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.560000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.560000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.560000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.560000] usb usb2: configuration #1 chosen from 1 choice
[    3.560000] hub 2-0:1.0: USB hub found
[    3.560000] hub 2-0:1.0: 2 ports detected
[    3.596000] 8139too Fast Ethernet driver 0.9.28
[    3.664000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.664000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.664000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.664000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.664000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.664000] usb usb3: configuration #1 chosen from 1 choice
[    3.664000] hub 3-0:1.0: USB hub found
[    3.664000] hub 3-0:1.0: 2 ports detected
[    3.768000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    3.768000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.768000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.768000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.768000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    3.768000] usb usb4: configuration #1 chosen from 1 choice
[    3.768000] hub 4-0:1.0: USB hub found
[    3.768000] hub 4-0:1.0: 2 ports detected
[    3.872000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.872000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.872000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.872000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.872000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.872000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.872000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0004000
[    3.876000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.876000] usb usb5: configuration #1 chosen from 1 choice
[    3.876000] hub 5-0:1.0: USB hub found
[    3.876000] hub 5-0:1.0: 8 ports detected
[    3.980000] ahci 0000:00:1f.2: version 2.2
[    3.980000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.000000] Clocksource tsc unstable (delta = -242300485 ns)
[    4.984000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    4.984000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    4.984000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.984000] scsi0 : ahci
[    4.984000] scsi1 : ahci
[    4.984000] scsi2 : ahci
[    4.984000] scsi3 : ahci
[    4.984000] ata1: SATA max UDMA/133 cmd 0xf8884500 ctl 0x00000000 bmdma 0x00000000 irq 20
[    4.984000] ata2: SATA max UDMA/133 cmd 0xf8884580 ctl 0x00000000 bmdma 0x00000000 irq 20
[    4.984000] ata3: SATA max UDMA/133 cmd 0xf8884600 ctl 0x00000000 bmdma 0x00000000 irq 20
[    4.984000] ata4: SATA max UDMA/133 cmd 0xf8884680 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.472000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.520000] ata1.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    5.520000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.520000] ata1.00: configured for UDMA/133
[    5.836000] ata2: SATA link down (SStatus 0 SControl 0)
[    6.152000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.468000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.468000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-2 04.0 PQ: 0 ANSI: 5
[    6.468000] PCI: Enabling device 0000:06:04.0 (0195 -> 0197)
[    6.468000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[    6.516000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f0200000-f02007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.516000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.516000] sd 0:0:0:0: [sda] Write Protect is off
[    6.516000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.516000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.516000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.516000] sd 0:0:0:0: [sda] Write Protect is off
[    6.516000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.516000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.516000]  sda:<7>ata_piix 0000:00:1f.1: version 2.11
[    6.524000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[    6.524000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.524000] scsi4 : ata_piix
[    6.524000] scsi5 : ata_piix
[    6.524000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    6.524000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    6.568000]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[    6.628000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.632000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.844000] ata5.00: ATAPI: Optiarc DVD RW AD-7540A, 1.42, max UDMA/33
[    7.016000] ata5.00: configured for UDMA/33
[    7.016000] ata6: port disabled. ignoring.
[    7.020000] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7540A  1.42 PQ: 0 ANSI: 5
[    7.020000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    7.020000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[    7.020000] eth0: RealTek RTL8139 at 0xf8860c00, 00:03:0d:59:f8:65, IRQ 17
[    7.020000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.024000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    7.056000] Attempting manual resume
[    7.056000] swsusp: Resume From Partition 8:6
[    7.056000] PM: Checking swsusp image.
[    7.056000] PM: Resume from disk failed.
[    7.056000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.056000] Uniform CD-ROM driver Revision: 3.20
[    7.056000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.064000] ReiserFS: sda7: found reiserfs format "3.6" with standard journal
[    7.064000] ReiserFS: sda7: using ordered data mode
[    7.068000] ReiserFS: sda7: journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    7.068000] ReiserFS: sda7: checking transaction log (sda7)
[    7.096000] ReiserFS: sda7: Using r5 hash to sort names
[    7.792000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d005008ac33]
[   40.252000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   41.048000] Linux agpgart interface v0.102 (c) Dave Jones
[   41.068000] agpgart: Detected an Intel 945GM Chipset.
[   41.072000] agpgart: Detected 7932K stolen memory.
[   41.092000] agpgart: AGP aperture is 256M @ 0xc0000000
[   41.668000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.708000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.744000] intel_rng: FWH not detected
[   41.788000] NET: Registered protocol family 10
[   41.788000] lo: Disabled Privacy Extensions
[   41.904000] sdhci: Secure Digital Host Controller Interface driver
[   41.904000] sdhci: Copyright(c) Pierre Ossman
[   41.904000] sdhci: SDHCI controller found at 0000:06:04.2 [1217:7120] (rev 1)
[   41.904000] ACPI: PCI Interrupt 0000:06:04.2[A] -> GSI 18 (level, low) -> IRQ 18
[   41.904000] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   41.904000] mmc0: SDHCI at 0xb0300800 irq 18 PIO
[   42.072000] iTCO_vendor_support: vendor-support=0
[   42.080000] ieee80211_crypt: registered algorithm 'NULL'
[   42.092000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   42.092000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   42.096000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.340000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   42.368000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   42.372000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   42.372000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.420000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   42.420000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   42.420000] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[   42.420000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   42.420000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   42.424000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   43.248000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   43.248000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   43.628000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   44.244000] lp: driver loaded but no devices found
[   44.480000] Adding 1052216k swap on /dev/sda6.  Priority:-1 extents:1 across:1052216k
[   44.712000] ipw3945: Radio Frequency Kill Switch is On:
[   44.712000] Kill switch must be turned off for wireless networking to work.
[   51.948000] eth0: no IPv6 routers present
[   57.756000] ReiserFS: sda8: found reiserfs format "3.6" with standard journal
[   57.756000] ReiserFS: sda8: using ordered data mode
[   57.772000] ReiserFS: sda8: journal params: device sda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   57.772000] ReiserFS: sda8: checking transaction log (sda8)
[   57.812000] ReiserFS: sda8: Using r5 hash to sort names
[   60.476000] ACPI: AC Adapter [AC0] (on-line)
[   60.488000] No dock devices found.
[   60.544000] input: Power Button (FF) as /class/input/input3
[   60.544000] ACPI: Power Button (FF) [PWRF]
[   60.544000] input: Lid Switch as /class/input/input4
[   60.544000] ACPI: Lid Switch [LID0]
[   60.544000] input: Power Button (CM) as /class/input/input5
[   60.544000] ACPI: Power Button (CM) [PWRB]
[   60.544000] input: Sleep Button (CM) as /class/input/input6
[   60.544000] ACPI: Sleep Button (CM) [SLPB]
[   60.692000] ACPI: Battery Slot [BAT0] (battery present)
[   60.700000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   60.700000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   61.728000] ppdev: user-space parallel port driver
[   62.836000] audit(1192719301.744:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5152 profile="/usr/sbin/cupsd"
[   62.956000] apm: BIOS not found.
[   64.692000] Failure registering capabilities with primary security module.
[   70.580000] [drm] Initialized drm 1.1.0 20060810
[   70.588000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   70.588000] [drm] Initialized i915 1.6.0 20060119 on minor 0
amr@amr-laptop:~$

---

### Post by Marink on 2007-10-18
So is mine, it takes ages to boot, and in between the start up screen and the login screen it's black, where the loading bar should be.
Any help ?

---

### Post by hobo on 2007-10-18
Mine too. IBM Thinkpad T42. Everything else is great. It even recognized my wireless and it works without my intervention. Also the (beryl/compiz) eye candy works also with no input from me. Very slick install. But sloooow to boot up !

---

### Post by portach king on 2007-10-19
I'm also having this issue.
After Grub boots I get the message:
Cannot Allocate Region Resource 7 of the Bridge
Cannot Allocate Region Resource 8 of the Bridge
Followed by a long black screen....

This happened in both my 64-bit and i386 attempts at installations.

Apart from that Gutsy seems to work flawlessy. Bravo on getting my broadcom wireless working out of the box guys!

I'm very disappointed in the above mentioned issue however as I've been an ubuntu user for just a year now and this is the first time anything like this has gone wrong. To be honest it was _extremely worrying._

Hopefully, this will be resolved in an update very soon??

By the way my laptop in a HP Pavillion zv6000, 2.2Ghz AMD64, 1 Gig Ram

---

### Post by skymera on 2007-10-19
from Launchpad i was told that boot loaded all wireless drivers, which explains the slowness.

but looking at yours its hanging after your processor

---

### Post by mech7 on 2007-10-19
With mine too.. it takes enormously long to boot, dont know what dmesg is but here it is..

```

[    0.000000] ACPI: MCFG 7FE88F9C, 003C (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: BOOT 7FE88FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FE813F6, 0235 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 7FE8121E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 7FE81005, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec20000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 255, address 0xfec20000, GSI 24-279
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 519811
[    0.000000] Kernel command line: root=UUID=72ad26b5-e137-48b6-9fdb-410331e967a0 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] mapped IOAPIC to ffffb000 (fec20000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.020 MHz processor.
[    8.668469] Console: colour VGA+ 80x25
[    8.668776] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.669188] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.786275] Memory: 2066224k/2095616k available (2015k kernel code, 28136k reserved, 916k data, 364k init, 1178112k highmem)
[    8.786285] virtual kernel memory layout:
[    8.786286]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    8.786288]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.786289]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.786290]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.786292]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    8.786293]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    8.786294]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    8.786298] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.786345] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.866341] Calibrating delay using timer specific routine.. 3460.84 BogoMIPS (lpj=6921697)
[    8.866377] Security Framework v1.0.0 initialized
[    8.866388] SELinux:  Disabled at boot.
[    8.866402] Mount-cache hash table entries: 512
[    8.866556] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    8.866570] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.866572] CPU: L2 cache: 2048K
[    8.866575] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    8.866586] Compat vDSO mapped to ffffe000.
[    8.866599] Checking 'hlt' instruction... OK.
[    8.882471] SMP alternatives: switching to UP code
[    8.882716] Freeing SMP alternatives: 11k freed
[    8.882997] Early unpacking initramfs... done
[    9.218023] ACPI: Core revision 20070126
[    9.218101] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.222420] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    9.222442] Total of 1 processors activated (3460.84 BogoMIPS).
[    9.223848] ENABLING IO-APIC IRQs
[    9.224044] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.370205] Brought up 1 CPUs
[    9.370321] Booting paravirtualized kernel on bare hardware
[    9.370377] Time: 15:55:15  Date: 09/19/107
[    9.370397] NET: Registered protocol family 16
[    9.370470] EISA bus registered
[    9.370482] ACPI: bus type pci registered
[    9.370807] PCI: PCI BIOS revision 2.10 entry at 0xfd7be, last bus=7
[    9.370809] PCI: Using configuration type 1
[    9.370811] Setting up standard PCI resources
[    9.375713] ACPI: EC: Look up EC in DSDT
[    9.376336] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[    9.762240] ACPI: Interpreter enabled
[    9.762243] ACPI: (supports S0 S3 S4 S5)
[    9.762258] ACPI: Using IOAPIC for interrupt routing
[    9.766967] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[    9.767009] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.767019] PCI: Probing PCI hardware (bus 00)
[    9.767514] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.767518] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.768173] PCI: Transparent bridge - 0000:00:1e.0
[    9.768271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.768584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    9.768713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.768837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.768976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.773197] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.773290] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.773382] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.773473] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.773563] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.773653] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.773744] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.773835] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.773929] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.773941] pnp: PnP ACPI init
[    9.773949] ACPI: bus type pnp registered
[    9.776392] pnp: PnP ACPI: found 9 devices
[    9.776394] ACPI: ACPI bus type pnp unregistered
[    9.776398] PnPBIOS: Disabled by ACPI PNP
[    9.776436] PCI: Using ACPI for IRQ routing
[    9.776439] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.776444] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    9.776480] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    9.776513] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[    9.776546] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    9.776579] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    9.776612] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    9.776645] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    9.776678] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    9.776711] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[    9.789620] NET: Registered protocol family 8
[    9.789622] NET: Registered protocol family 20
[    9.789671] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.789674] pnp: 00:01: iomem range 0xf0000000-0xf0003fff could not be reserved
[    9.789678] pnp: 00:01: iomem range 0xf0004000-0xf0004fff could not be reserved
[    9.789681] pnp: 00:01: iomem range 0xf0005000-0xf0005fff could not be reserved
[    9.790011] Time: tsc clocksource has been installed.
[    9.819942] PCI: Bridge: 0000:00:01.0
[    9.819945]   IO window: 3000-3fff
[    9.819949]   MEM window: c8100000-c81fffff
[    9.819952]   PREFETCH window: d0000000-d7ffffff
[    9.819955] PCI: Bridge: 0000:00:1c.0
[    9.819957]   IO window: disabled.
[    9.819961]   MEM window: disabled.
[    9.819964]   PREFETCH window: disabled.
[    9.819968] PCI: Bridge: 0000:00:1c.1
[    9.819969]   IO window: disabled.
[    9.819973]   MEM window: disabled.
[    9.819976]   PREFETCH window: disabled.
[    9.819980] PCI: Bridge: 0000:00:1c.2
[    9.819982]   IO window: disabled.
[    9.819986]   MEM window: disabled.
[    9.819989]   PREFETCH window: disabled.
[    9.819995] PCI: Bus 7, cardbus bridge: 0000:06:01.0
[    9.819997]   IO window: 00004000-000040ff
[    9.820001]   IO window: 00004400-000044ff
[    9.820006]   PREFETCH window: 88000000-8bffffff
[    9.820010]   MEM window: 8c000000-8fffffff
[    9.820014] PCI: Bridge: 0000:00:1e.0
[    9.820017]   IO window: 4000-4fff
[    9.820021]   MEM window: c8200000-c82fffff
[    9.820025]   PREFETCH window: 88000000-8bffffff
[    9.820038] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.820043] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.820058] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    9.820064] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.820078] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    9.820084] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.820099] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.820104] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.820113] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.820125] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 18
[    9.820138] NET: Registered protocol family 2
[    9.858009] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.858069] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    9.859269] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.859840] TCP: Hash tables configured (established 131072 bind 65536)
[    9.859843] TCP reno registered
[    9.870142] checking if image is initramfs... it is
[   10.321822] Switched to high resolution mode on CPU 0
[   10.526868] Freeing initrd memory: 7054k freed
[   10.527165] Simple Boot Flag at 0x36 set to 0x1
[   10.527417] audit: initializing netlink socket (disabled)
[   10.527431] audit(1192809315.336:1): initialized
[   10.527501] highmem bounce pool size: 64 pages
[   10.529216] VFS: Disk quotas dquot_6.5.1
[   10.529265] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.529351] io scheduler noop registered
[   10.529353] io scheduler anticipatory registered
[   10.529355] io scheduler deadline registered
[   10.529369] io scheduler cfq registered (default)
[   10.529451] Boot video device is 0000:01:00.0
[   10.529525] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   10.529553] assign_interrupt_mode Found MSI capability
[   10.529557] Allocate Port Service[0000:00:01.0:pcie00]
[   10.529619] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.529669] assign_interrupt_mode Found MSI capability
[   10.529671] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.529699] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.529772] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.529805] assign_interrupt_mode Found MSI capability
[   10.529808] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.529835] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.529901] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.529935] assign_interrupt_mode Found MSI capability
[   10.529937] Allocate Port Service[0000:00:1c.2:pcie00]
[   10.529964] Allocate Port Service[0000:00:1c.2:pcie02]
[   10.530091] isapnp: Scanning for PnP cards...
[   10.883155] isapnp: No Plug & Play device found
[   10.906688] Real Time Clock Driver v1.12ac
[   10.906792] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.906974] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   10.907472] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 19
[   10.907480] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   10.907984] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.908167] input: Macintosh mouse button emulation as /class/input/input0
[   10.908235] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.911661] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.911666] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.911807] mice: PS/2 mouse device common for all mice
[   10.911901] EISA: Probing bus 0 at eisa.0
[   10.911908] Cannot allocate resource for EISA slot 1
[   10.911910] Cannot allocate resource for EISA slot 2
[   10.911913] Cannot allocate resource for EISA slot 3
[   10.911915] Cannot allocate resource for EISA slot 4
[   10.911928] EISA: Detected 0 cards.
[   10.912020] TCP cubic registered
[   10.912034] NET: Registered protocol family 1
[   10.912057] Using IPI No-Shortcut mode
[   10.912220]   Magic number: 11:932:942
[   10.912274]   hash matches device ptyyd
[   10.912515] Freeing unused kernel memory: 364k freed
[   10.985537] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.090772] AppArmor: AppArmor initialized<5>audit(1192809316.836:2):  type=1505 info="AppArmor initialized" pid=1208
[   12.211355] fuse init (API version 7.8)
[   12.311757] Failure registering capabilities with primary security module.
[   12.512968] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   12.512974] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.512985] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   12.912581] ACPI: Thermal Zone [THRM] (38 C)
[   22.265247] usbcore: registered new interface driver usbfs
[   22.265270] usbcore: registered new interface driver hub
[   22.265288] usbcore: registered new device driver usb
[   22.266001] USB Universal Host Controller Interface driver v3.0
[   22.266062] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   22.266072] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.266076] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.266248] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.266275] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   22.266377] usb usb1: configuration #1 chosen from 1 choice
[   22.266399] hub 1-0:1.0: USB hub found
[   22.266404] hub 1-0:1.0: 2 ports detected
[   22.368240] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   22.368251] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.368255] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.368275] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.368302] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[   22.368388] usb usb2: configuration #1 chosen from 1 choice
[   22.368412] hub 2-0:1.0: USB hub found
[   22.368418] hub 2-0:1.0: 2 ports detected
[   22.472164] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18

```

---

### Post by mech7 on 2007-10-19
And the rest..

```


[   22.472173] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.472177] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.472195] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.472222] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   22.472308] usb usb3: configuration #1 chosen from 1 choice
[   22.472332] hub 3-0:1.0: USB hub found
[   22.472337] hub 3-0:1.0: 2 ports detected
[   22.576146] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   22.576158] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.576162] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.576183] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.576212] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   22.576305] usb usb4: configuration #1 chosen from 1 choice
[   22.576330] hub 4-0:1.0: USB hub found
[   22.576336] hub 4-0:1.0: 2 ports detected
[   22.818212] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   22.818225] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.818228] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.818254] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.818282] ehci_hcd 0000:00:1d.7: debug port 1
[   22.818288] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   22.818296] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xc8000000
[   22.822170] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.822259] usb usb5: configuration #1 chosen from 1 choice
[   22.822285] hub 5-0:1.0: USB hub found
[   22.822291] hub 5-0:1.0: 8 ports detected
[   23.380468] b44.c:v1.01 (Jun 16, 2006)
[   23.380490] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.383966] eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:bb:e5:90
[   23.410005] SCSI subsystem initialized
[   23.414941] libata version 2.21 loaded.
[   23.417977] ata_piix 0000:00:1f.1: version 2.11
[   23.417991] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   23.418022] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.418083] scsi0 : ata_piix
[   23.418122] scsi1 : ata_piix
[   23.418335] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118c0 irq 14
[   23.418338] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118c8 irq 15
[   23.807787] ata1.00: ATA-6: TOSHIBA MK8025GAS, KA023A, max UDMA/100
[   23.807792] ata1.00: 156301488 sectors, multi 16: LBA 
[   23.807797] ata1.01: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[   23.815775] ata1.00: configured for UDMA/100
[   23.987765] ata1.01: configured for UDMA/33
[   23.987794] ata2: port disabled. ignoring.
[   23.995371] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8025GA KA02 PQ: 0 ANSI: 5
[   23.997256] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
[   23.997481] ACPI: PCI Interrupt 0000:06:01.2[A] -> GSI 18 (level, low) -> IRQ 18
[   24.047266] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8209000-c82097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.663075] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.667055] sd 0:0:0:0: [sda] Write Protect is off
[   24.667058] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.675043] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.683036] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.687033] sd 0:0:0:0: [sda] Write Protect is off
[   24.687035] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.695028] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.695032]  sda: sda1 sda2 sda3
[   24.972837] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.977303] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.977321] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.991720] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.991725] Uniform CD-ROM driver Revision: 3.20
[   24.991764] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   25.314836] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00005be740]
[   26.317799] Attempting manual resume
[   26.317802] swsusp: Resume From Partition 8:3
[   26.317804] PM: Checking swsusp image.
[   26.414224] PM: Resume from disk failed.
[   27.121927] kjournald starting.  Commit interval 5 seconds
[   27.121936] EXT3-fs: mounted filesystem with ordered data mode.
[  118.668871] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  118.702368] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  118.798133] Linux agpgart interface v0.102 (c) Dave Jones
[  119.596950] iTCO_vendor_support: vendor-support=0
[  119.790466] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  119.791584] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[  119.792402] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  119.853169] ACPI: PCI Interrupt 0000:06:01.3[A] -> GSI 18 (level, low) -> IRQ 18
[  119.859322] Yenta: CardBus bridge found at 0000:06:01.0 [1025:0066]
[  119.859337] Yenta: Enabling burst memory read transactions
[  119.859342] Yenta: Using CSCINT to route CSC interrupts to PCI
[  119.859344] Yenta: Routing CardBus interrupts to PCI
[  119.859349] Yenta TI: socket 0000:06:01.0, mfunc 0x01c21b22, devctl 0x64
[  119.890202] intel_rng: FWH not detected
[  111.044000] Marking TSC unstable due to: possible TSC halt in C2.
[  111.048000] Time: acpi_pm clocksource has been installed.
[  111.156000] ieee80211_crypt: registered algorithm 'NULL'
[  111.188000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[  111.188000] Socket status: 30000006
[  111.188000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #08
[  111.188000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[  111.188000] cs: IO port probe 0x4000-0x4fff: clean.
[  111.188000] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[  111.188000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[  111.212000] irda_init()
[  111.212000] NET: Registered protocol family 23
[  111.276000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  111.276000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  111.364000] Clocksource tsc unstable (delta = -758554975 ns)
[  111.376000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[  111.376000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  111.376000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[  111.376000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  111.644000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  111.784000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[  111.820000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[  111.824000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[  111.824000] nsc-ircc, chip->init
[  111.824000] nsc-ircc, Found chip at base=0x164e
[  111.824000] nsc-ircc, driver loaded (Dag Brattli)
[  111.824000] nsc_ircc_open(), can't get iobase of 0x2f8
[  111.824000] nsc-ircc, Found chip at base=0x164e
[  111.824000] nsc-ircc, driver loaded (Dag Brattli)
[  111.824000] nsc_ircc_open(), can't get iobase of 0x2f8
[  111.824000] pnp: Device 00:06 disabled.
[  111.864000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[  111.864000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[  111.964000] cs: IO port probe 0x100-0x3af: clean.
[  111.964000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  111.964000] cs: IO port probe 0x820-0x8ff: clean.
[  111.964000] cs: IO port probe 0xc00-0xcf7: clean.
[  111.964000] cs: IO port probe 0xa00-0xaff: clean.
[  112.184000] intel8x0_measure_ac97_clock: measured 54141 usecs
[  112.184000] intel8x0: clocking to 48000
[  113.260000] lp: driver loaded but no devices found
[  113.320000] Adding 722916k swap on /dev/sda3.  Priority:-1 extents:1 across:722916k
[  113.740000] EXT3 FS on sda2, internal journal
[  116.272000] ACPI: Battery Slot [BAT1] (battery present)
[  116.272000] ACPI: Battery Slot [BAT2] (battery absent)
[  116.480000] input: Power Button (FF) as /class/input/input3
[  116.480000] ACPI: Power Button (FF) [PWRF]
[  116.520000] input: Lid Switch as /class/input/input4
[  116.524000] ACPI: Lid Switch [LID]
[  116.564000] input: Power Button (CM) as /class/input/input5
[  116.568000] ACPI: Power Button (CM) [PWRB]
[  116.604000] input: Sleep Button (CM) as /class/input/input6
[  116.608000] ACPI: Sleep Button (CM) [SLPB]
[  116.648000] ACPI: AC Adapter [ACAD] (on-line)
[  116.688000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  116.704000] ACPI: ACPI Dock Station Driver 
[  116.728000] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: found ejectable bay
[  116.728000] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: Adding notify handler
[  116.728000] ACPI: Error installing bay notify handler
[  116.728000] ACPI: Bay [\_SB_.PCI0.PATA.PRID.BAY_] Added
[  118.216000] ttyS1: LSR safety check engaged!
[  119.456000] ppdev: user-space parallel port driver
[  119.684000] audit(1192802235.484:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4991 profile="/usr/sbin/cupsd"
[  122.040000] apm: BIOS not found.
[  122.420000] Failure registering capabilities with primary security module.
[  122.668000] Bluetooth: Core ver 2.11
[  122.668000] NET: Registered protocol family 31
[  122.668000] Bluetooth: HCI device and connection manager initialized
[  122.668000] Bluetooth: HCI socket layer initialized
[  122.708000] Bluetooth: L2CAP ver 2.8
[  122.708000] Bluetooth: L2CAP socket layer initialized
[  122.880000] Bluetooth: RFCOMM socket layer initialized
[  122.880000] Bluetooth: RFCOMM TTY layer initialized
[  122.880000] Bluetooth: RFCOMM ver 1.8
[  124.840000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  124.844000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[  124.844000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  124.908000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  127.104000] [fglrx] total      GART = 130023424
[  127.104000] [fglrx] free       GART = 114032640
[  127.104000] [fglrx] max single GART = 114032640
[  127.104000] [fglrx] total      LFB  = 66977792
[  127.104000] [fglrx] free       LFB  = 52588544
[  127.104000] [fglrx] max single LFB  = 52588544
[  127.104000] [fglrx] total      Inv  = 0
[  127.104000] [fglrx] free       Inv  = 0
[  127.104000] [fglrx] max single Inv  = 0
[  127.104000] [fglrx] total      TIM  = 0
[  137.476000] synaptics: using relaxed packet validation
[  155.216000] NET: Registered protocol family 17
[  155.488000] ieee80211_crypt: registered algorithm 'TKIP'
[  170.788000] NET: Registered protocol family 10
[  170.788000] lo: Disabled Privacy Extensions
[  170.788000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  181.136000] eth1: no IPv6 routers present
chris@chris-laptop:~$ 



```

---

### Post by Arroyo on 2007-10-19
I'm having the same problem on my Compaq Presario 1500 - booting takes forever. Here is my dmesg:


```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001fff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000001fff0c00 - 000000001fffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fffc000 - 0000000020000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9970 checksum 0
[    0.000000] ACPI: RSDP 000F9970, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 1FFF0C84, 002C (r1 COMPAQ CPQ004A  24070220 CPQ         1)
[    0.000000] ACPI: FACP 1FFF0C00, 0084 (r2 COMPAQ CPQ004A         2 CPQ         1)
[    0.000000] ACPI: DSDT 1FFF0CB0, 5987 (r1 COMPAQ  EVON800    10000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFFBE80, 0040
[    0.000000] ACPI: SSDT 1FFF6637, 0343 (r1 COMPAQ CPQCroDT     1001 MSFT  100000E)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:e0000000)
[    0.000000] Built 1 zonelists.  Total pages: 130001
[    0.000000] Kernel command line: root=UUID=c6735f5f-3ec2-4a44-9b52-bccdb8211e4a ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2392.391 MHz processor.
[   18.712085] Console: colour VGA+ 80x25
[   18.712569] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.713025] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.727501] Memory: 507788k/524096k available (2015k kernel code, 15724k reserved, 916k data, 364k init, 0k highmem)
[   18.727513] virtual kernel memory layout:
[   18.727514]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.727515]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.727517]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   18.727518]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   18.727519]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.727520]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   18.727522]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   18.727525] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.727570] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.807590] Calibrating delay using timer specific routine.. 4789.03 BogoMIPS (lpj=9578063)
[   18.807621] Security Framework v1.0.0 initialized
[   18.807629] SELinux:  Disabled at boot.
[   18.807644] Mount-cache hash table entries: 512
[   18.807812] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   18.807826] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   18.807830] CPU: L2 cache: 512K
[   18.807833] CPU: Hyper-Threading is disabled
[   18.807836] CPU: After all inits, caps: 3febf9ff 00000000 00000000 0000b080 00000000 00000000 00000000
[   18.807853] Compat vDSO mapped to ffffe000.
[   18.807869] Checking 'hlt' instruction... OK.
[   18.823756] SMP alternatives: switching to UP code
[   18.824002] Freeing SMP alternatives: 11k freed
[   18.824390] Early unpacking initramfs... done
[   19.197460] ACPI: Core revision 20070126
[   19.197551] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.200419] ACPI: setting ELCR to 0200 (from 0c20)
[   19.233989] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
[   19.233999] SMP motherboard not detected.
[   19.234001] Local APIC not detected. Using dummy APIC emulation.
[   19.234047] Brought up 1 CPUs
[   19.234201] Booting paravirtualized kernel on bare hardware
[   19.234278] Time: 17:07:55  Date: 09/19/107
[   19.234311] NET: Registered protocol family 16
[   19.234430] EISA bus registered
[   19.234447] ACPI: bus type pci registered
[   19.236312] PCI: BIOS32 entry (0xc00f0000) in high memory, cannot use.
[   19.236315] PCI: Using configuration type 1
[   19.236317] Setting up standard PCI resources
[   19.237924] ACPI: EC: Look up EC in DSDT
[   19.238033] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   19.260739] ACPI: Interpreter enabled
[   19.260745] ACPI: (supports S0 S3 S4 S5)
[   19.260767] ACPI: Using PIC for interrupt routing
[   19.272212] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   19.272330] ACPI: PCI Root Bridge [C03B] (0000:00)
[   19.272339] PCI: Probing PCI hardware (bus 00)
[   19.272579] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   19.272583] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[   19.273046] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   19.273304] PCI: Transparent bridge - 0000:00:1e.0
[   19.273404] ACPI: PCI Interrupt Routing Table [\_SB_.C03B._PRT]
[   19.273431] ACPI: PCI Interrupt Routing Table [\_SB_.C03B.C03C._PRT]
[   19.273450] ACPI: PCI Interrupt Routing Table [\_SB_.C03B.C04D._PRT]
[   19.279540] ACPI: PCI Interrupt Link [C0B5] (IRQs 5 10 *11)
[   19.279809] ACPI: PCI Interrupt Link [C0B6] (IRQs *5 10 11)
[   19.280013] ACPI: PCI Interrupt Link [C0B7] (IRQs 5 10 *11)
[   19.280216] ACPI: PCI Interrupt Link [C0B8] (IRQs 5 10 *11)
[   19.280419] ACPI: PCI Interrupt Link [C0B9] (IRQs 5 *10 11)
[   19.280517] ACPI: Blank IRQ resource
[   19.280519] ACPI: Resource is not an IRQ entry
[   19.280667] ACPI: PCI Interrupt Link [C0BA] (IRQs) *0, disabled.
[   19.280763] ACPI: Blank IRQ resource
[   19.280765] ACPI: Resource is not an IRQ entry
[   19.280908] ACPI: PCI Interrupt Link [C0BB] (IRQs) *0, disabled.
[   19.281005] ACPI: Blank IRQ resource
[   19.281007] ACPI: Resource is not an IRQ entry
[   19.281149] ACPI: PCI Interrupt Link [C0BC] (IRQs) *0, disabled.
[   19.281412] ACPI: Power Resource [C142] (off)
[   19.281506] ACPI: Power Resource [C156] (off)
[   19.281598] ACPI: Power Resource [C15A] (off)
[   19.281690] ACPI: Power Resource [C15E] (off)
[   19.281741] ACPI: Power Resource [C167] (on)
[   19.281811] ACPI: Power Resource [C0CE] (on)
[   19.281905] ACPI: Power Resource [C1D3] (off)
[   19.281992] ACPI: Power Resource [C1D4] (off)
[   19.282079] ACPI: Power Resource [C1D5] (off)
[   19.282170] ACPI: Power Resource [C1D6] (off)
[   19.282263] ACPI: Power Resource [C1E1] (off)
[   19.282351] ACPI: Power Resource [C1E2] (off)
[   19.282438] ACPI: Power Resource [C1E3] (off)
[   19.282448] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.282467] pnp: PnP ACPI init
[   19.282481] ACPI: bus type pnp registered
[   19.293282] pnp: PnP ACPI: found 14 devices
[   19.293286] ACPI: ACPI bus type pnp unregistered
[   19.293291] PnPBIOS: Disabled by ACPI PNP
[   19.293363] PCI: Using ACPI for IRQ routing
[   19.293367] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.293469] NET: Registered protocol family 8
[   19.293472] NET: Registered protocol family 20
[   19.293564] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   19.293568] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   19.293571] pnp: 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   19.293587] pnp: 00:0c: iomem range 0xffb00000-0xffbfffff has been reserved
[   19.293590] pnp: 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[   19.293596] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   19.293599] pnp: 00:0d: ioport range 0x1000-0x107f has been reserved
[   19.293602] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[   19.293605] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[   19.293608] pnp: 00:0d: iomem range 0xffc00000-0xffc003ff has been reserved
[   19.295563] Time: tsc clocksource has been installed.
[   19.324017] PCI: Bridge: 0000:00:01.0
[   19.324020]   IO window: 3000-3fff
[   19.324025]   MEM window: 40400000-404fffff
[   19.324030]   PREFETCH window: 48000000-4fffffff
[   19.324037] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   19.324040]   IO window: 00002400-000024ff
[   19.324045]   IO window: 00002800-000028ff
[   19.324049]   PREFETCH window: 30000000-33ffffff
[   19.324054]   MEM window: 38000000-3bffffff
[   19.324059] PCI: Bridge: 0000:00:1e.0
[   19.324062]   IO window: 2000-2fff
[   19.324068]   MEM window: 40000000-403fffff
[   19.324073]   PREFETCH window: 30000000-33ffffff
[   19.324093] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.324445] ACPI: PCI Interrupt Link [C0B8] enabled at IRQ 11
[   19.324449] PCI: setting IRQ 11 as level-triggered
[   19.324453] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0B8] -> GSI 11 (level, low) -> IRQ 11
[   19.324475] NET: Registered protocol family 2
[   19.363614] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.363686] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   19.363852] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   19.363963] TCP: Hash tables configured (established 16384 bind 16384)
[   19.363967] TCP reno registered
[   19.375727] checking if image is initramfs... it is
[   19.827556] Switched to high resolution mode on CPU 0
[   20.111128] Freeing initrd memory: 7348k freed
[   20.111602] audit: initializing netlink socket (disabled)
[   20.111623] audit(1192813675.044:1): initialized
[   20.114177] VFS: Disk quotas dquot_6.5.1
[   20.114249] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.114383] io scheduler noop registered
[   20.114386] io scheduler anticipatory registered
[   20.114388] io scheduler deadline registered
[   20.114409] io scheduler cfq registered (default)
[   20.114435] Boot video device is 0000:01:00.0
[   20.114657] isapnp: Scanning for PnP cards...
[   20.468821] isapnp: No Plug & Play device found
[   20.503261] Real Time Clock Driver v1.12ac
[   20.503492] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.503597] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.504049] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a NS16550A
[   20.504652] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.505754] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.506057] input: Macintosh mouse button emulation as /class/input/input0
[   20.506165] PNP: PS/2 Controller [PNP0303:C164,PNP0f13:C165] at 0x60,0x64 irq 1,12
[   20.509580] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.510752] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.510762] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.510766] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.510769] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.510772] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.511062] mice: PS/2 mouse device common for all mice
[   20.511312] EISA: Probing bus 0 at eisa.0
[   20.511324] Cannot allocate resource for EISA slot 1
[   20.511326] Cannot allocate resource for EISA slot 2
[   20.511329] Cannot allocate resource for EISA slot 3
[   20.511331] Cannot allocate resource for EISA slot 4
[   20.511349] EISA: Detected 0 cards.
[   20.511514] TCP cubic registered
[   20.511529] NET: Registered protocol family 1
[   20.511559] Using IPI No-Shortcut mode
[   20.511772]   Magic number: 11:320:138
[   20.512616] Freeing unused kernel memory: 364k freed
[   20.624185] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.766251] AppArmor: AppArmor initialized<5>audit(1192813676.544:2):  type=1505 info="AppArmor initialized" pid=1243
[   21.782629] fuse init (API version 7.8)
[   21.788822] Failure registering capabilities with primary security module.
[   21.892007] ACPI: Transitioning device [C1D7] to D3
[   21.892012] ACPI: Transitioning device [C1D7] to D3
[   21.892016] ACPI: Fan [C1D7] (off)
[   21.892177] ACPI: Transitioning device [C1D8] to D3
[   21.892180] ACPI: Transitioning device [C1D8] to D3
[   21.892183] ACPI: Fan [C1D8] (off)
[   21.892343] ACPI: Transitioning device [C1D9] to D3
[   21.892345] ACPI: Transitioning device [C1D9] to D3
[   21.892349] ACPI: Fan [C1D9] (off)
[   21.892508] ACPI: Transitioning device [C1DA] to D3
[   21.892510] ACPI: Transitioning device [C1DA] to D3
[   21.892514] ACPI: Fan [C1DA] (off)
[   21.892680] ACPI: Transitioning device [C1E4] to D3
[   21.892682] ACPI: Transitioning device [C1E4] to D3
[   21.892685] ACPI: Fan [C1E4] (off)
[   21.892846] ACPI: Transitioning device [C1E5] to D3
[   21.892848] ACPI: Transitioning device [C1E5] to D3
[   21.892852] ACPI: Fan [C1E5] (off)
[   21.893012] ACPI: Transitioning device [C1E6] to D3
[   21.893015] ACPI: Transitioning device [C1E6] to D3
[   21.893018] ACPI: Fan [C1E6] (off)
[   21.898997] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.899006] ACPI: Processor [C000] (supports 8 throttling states)
[   21.916563] ACPI: Thermal Zone [TZ1] (37 C)
[   21.927842] ACPI: Thermal Zone [TZ2] (32 C)
[   22.727341] ACPI: Thermal Zone [TZ3] (26 C)
[   33.198107] SCSI subsystem initialized
[   33.205649] libata version 2.21 loaded.
[   33.207757] ata_piix 0000:00:1f.1: version 2.11
[   33.207776] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   33.208165] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 11
[   33.208169] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0B7] -> GSI 11 (level, low) -> IRQ 11
[   33.208229] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   33.208345] scsi0 : ata_piix
[   33.208406] scsi1 : ata_piix
[   33.208492] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014440 irq 14
[   33.208496] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014448 irq 15
[   33.370361] ata1.00: ATA-5: TOSHIBA MK4018GAP, M0.03 A, max UDMA/100
[   33.370368] ata1.00: 78140160 sectors, multi 16: LBA 
[   33.378345] ata1.00: configured for UDMA/100
[   33.698271] ata2.00: ATAPI: SD-R2102, 1A16, max MWDMA2
[   33.870304] ata2.00: configured for MWDMA2
[   33.877985] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4018GA M0.0 PQ: 0 ANSI: 5
[   33.883965] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A16 PQ: 0 ANSI: 5
[   33.889459] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [C0B7] -> GSI 11 (level, low) -> IRQ 11
[   33.939388] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[40300000-403007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.961025] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   33.961029] e100: Copyright(c) 1999-2006 Intel Corporation
[   33.961486] ACPI: PCI Interrupt Link [C0B9] enabled at IRQ 10
[   33.961490] PCI: setting IRQ 10 as level-triggered
[   33.961494] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[   34.117035] e100: eth0: e100_probe: addr 0x40180000, irq 10, MAC addr 00:08:02:00:95:E9
[   34.117281] usbcore: registered new interface driver usbfs
[   34.117318] usbcore: registered new interface driver hub
[   34.117355] usbcore: registered new device driver usb
[   34.118627] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   34.118686] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[   34.118701] ohci_hcd 0000:02:0e.0: OHCI Host Controller
[   34.118941] ohci_hcd 0000:02:0e.0: new USB bus registered, assigned bus number 1
[   34.118961] ohci_hcd 0000:02:0e.0: irq 10, io mem 0x40200000
[   34.738074] usb usb1: configuration #1 chosen from 1 choice
[   34.738113] hub 1-0:1.0: USB hub found
[   34.738129] hub 1-0:1.0: 3 ports detected
[   35.209973] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000802719cba9bf4]
[   35.253954] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[   35.253973] ehci_hcd 0000:02:0e.2: EHCI Host Controller
[   35.254001] ehci_hcd 0000:02:0e.2: new USB bus registered, assigned bus number 2
[   35.277787] ehci_hcd 0000:02:0e.2: irq 10, io mem 0x40380000
[   35.277796] ehci_hcd 0000:02:0e.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   35.277892] usb usb2: configuration #1 chosen from 1 choice
[   35.277932] hub 2-0:1.0: USB hub found
[   35.277940] hub 2-0:1.0: 5 ports detected
[   35.382122] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[   35.382143] ohci_hcd 0000:02:0e.1: OHCI Host Controller
[   35.382178] ohci_hcd 0000:02:0e.1: new USB bus registered, assigned bus number 3
[   35.382197] ohci_hcd 0000:02:0e.1: irq 10, io mem 0x40280000
[   36.030978] usb usb3: configuration #1 chosen from 1 choice
[   36.031014] hub 3-0:1.0: USB hub found
[   36.031028] hub 3-0:1.0: 2 ports detected
[   36.054871] Floppy drive(s): fd0 is 1.44M
[   36.095580] FDC 0 is a National Semiconductor PC87306
[   36.377708] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   36.381680] sd 0:0:0:0: [sda] Write Protect is off
[   36.381683] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.389659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.397658] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   36.401657] sd 0:0:0:0: [sda] Write Protect is off
[   36.401660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.409656] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.409662]  sda: sda1 sda2 < sda5 >
[   36.501222] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.511850] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   36.511856] Uniform CD-ROM driver Revision: 3.20
[   36.511923] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   36.702484] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.702512] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   38.767615] Attempting manual resume
[   38.767620] swsusp: Resume From Partition 8:5
[   38.767623] PM: Checking swsusp image.
[   38.865378] PM: Resume from disk failed.
[   39.585380] kjournald starting.  Commit interval 5 seconds
[   39.585397] EXT3-fs: mounted filesystem with ordered data mode.
[  135.054399] Linux agpgart interface v0.102 (c) Dave Jones
[  135.062673] agpgart: Detected an Intel 845G Chipset.
[  135.076961] agpgart: AGP aperture is 256M @ 0x60000000
[  135.330013] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  135.336259] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  136.647695] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:004e]
[  136.647717] Yenta: Enabling burst memory read transactions
[  136.647723] Yenta: Using CSCINT to route CSC interrupts to PCI
[  136.647725] Yenta: Routing CardBus interrupts to PCI
[  136.647731] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[  136.878874] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[  136.878880] Socket status: 30000020
[  136.878883] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[  136.878892] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[  136.878895] cs: IO port probe 0x2000-0x2fff: clean.
[  136.879132] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[  136.879136] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[  136.997197] intel_rng: FWH not detected
[  137.020156] iTCO_vendor_support: vendor-support=0
[  137.021724] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  137.021812] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[  137.021861] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  137.514327] pccard: CardBus card inserted into slot 0
[  138.331808] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
[  138.368068] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[  138.521057] parport_pc 00:05: reported by Plug and Play ACPI
[  138.521165] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  138.537340] input: PC Speaker as /class/input/input3
[  138.631657] irda_init()
[  138.631680] NET: Registered protocol family 23
[  138.836524] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3E8 ; irq 3 ; dma 3.
[  138.836558] nsc-ircc, chip->init
[  138.836569] nsc-ircc, Found chip at base=0x02e
[  138.836594] nsc-ircc, driver loaded (Dag Brattli)
[  138.836603] nsc_ircc_open(), can't get iobase of 0x3e8
[  138.836632] nsc-ircc, Found chip at base=0x02e
[  138.836658] nsc-ircc, driver loaded (Dag Brattli)
[  138.836661] nsc_ircc_open(), can't get iobase of 0x3e8
[  138.838763] pnp: Device 00:04 disabled.
[  139.129920] ACPI: PCI Interrupt Link [C0B6] enabled at IRQ 5
[  139.129927] PCI: setting IRQ 5 as level-triggered
[  139.129931] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B6] -> GSI 5 (level, low) -> IRQ 5
[  139.129952] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  139.200407] cs: IO port probe 0x100-0x3af: clean.
[  139.202363] cs: IO port probe 0x3e0-0x4ff: clean.
[  139.203136] cs: IO port probe 0x820-0x8ff: clean.
[  139.203816] cs: IO port probe 0xc00-0xcf7: clean.
[  139.204650] cs: IO port probe 0xa00-0xaff: clean.
[  139.334843] ieee80211_crypt: registered algorithm 'NULL'
[  139.337813] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  139.337817] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  139.404338] bcm43xx driver
[  139.798050] intel8x0_measure_ac97_clock: measured 54732 usecs
[  139.798055] intel8x0: clocking to 48000
[  139.799567] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[  139.799590] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0B8] -> GSI 11 (level, low) -> IRQ 11
[  139.799605] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  141.811212] lp0: using parport0 (interrupt-driven).
[  142.155608] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[  143.531475] EXT3 FS on sda1, internal journal
[  151.056081] No dock devices found.
[  155.192597] ACPI: Battery Slot [C11E] (battery present)
[  156.004195] input: Power Button (FF) as /class/input/input4
[  156.009733] ACPI: Power Button (FF) [PWRF]
[  156.048768] input: Power Button (CM) as /class/input/input5
[  156.054266] ACPI: Power Button (CM) [C17A]
[  156.094340] input: Sleep Button (CM) as /class/input/input6
[  156.099837] ACPI: Sleep Button (CM) [C120]
[  156.138557] input: Lid Switch as /class/input/input7
[  156.144013] ACPI: Lid Switch [C11F]
[  156.405137] ACPI: AC Adapter [C11B] (on-line)
[  165.178110] ttyS2: LSR safety check engaged!
[  165.935227] ppdev: user-space parallel port driver
[  166.445651] audit(1192813822.667:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5114 profile="/usr/sbin/cupsd"
[  166.599114] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  166.599120] apm: overridden by ACPI.
[  168.094903] Failure registering capabilities with primary security module.
[  161.128000] Marking TSC unstable due to: possible TSC halt in C2.
[  161.132000] Time: acpi_pm clocksource has been installed.
[  162.208000] [drm] Initialized drm 1.1.0 20060810
[  162.228000] ACPI: PCI Interrupt Link [C0B5] enabled at IRQ 11
[  162.228000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0B5] -> GSI 11 (level, low) -> IRQ 11
[  162.232000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  164.604000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  164.604000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  164.604000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  165.072000] Clocksource tsc unstable (delta = -62909998 ns)
[  165.912000] [drm] Setting GART location based on new memory map
[  165.912000] [drm] writeback test succeeded in 2 usecs
[  205.696000] NET: Registered protocol family 17
[  206.532000] ieee80211_crypt: registered algorithm 'WEP'
[  207.388000] SoftMAC: Open Authentication completed with 00:09:5b:9e:48:02
[  210.336000] NET: Registered protocol family 10
[  210.336000] lo: Disabled Privacy Extensions
[  210.336000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  226.140000] eth1: no IPv6 routers present
```

---

### Post by Arroyo on 2007-10-19
In my case, following the instructions in this post solved the problem:
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Now there's no more black screen during bootup, and it's also *much* faster.

---

### Post by mech7 on 2007-10-19
it says with me: # Usplash configuration file
xres=1280
yres=1024

Which is correct resolution

---

### Post by exidez on 2007-10-20
> **Arroyo said:**
> In my case, following the instructions in this post solved the problem:
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Now there's no more black screen during bootup, and it's also *much* faster.

I followed the post and it fixed the problem. I can now see the splash screen and it didnt take the long couple of minutes to load...

---

### Post by mmmfottrell on 2007-10-20
> **Arroyo said:**
> In my case, following the instructions in this post solved the problem:
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Now there's no more black screen during bootup, and it's also *much* faster.

Being a Linux newbie I am not sure how to do this. :( can anyone give more detailed directions for us cmd illiterate?

---

### Post by malcam on 2007-10-21
> **mmmfottrell said:**
> Being a Linux newbie I am not sure how to do this. :( can anyone give more detailed directions for us cmd illiterate?
Rough translation, although I don't speak newbie that well. :)

Open terminal, (ie Applications > Accessories > Terminal), then type:

sudo nano -w /etc/usplash.conf

As aways, sudo will require you to enter your password.

Change the xres to 1024 and the yres to 768.

Hold down Ctrl and X, release those keys, press Y and press Return.

sudo nano -w /boot/grub/menu.lst

Hold down Ctrl and W, release those keys, type "vga=791" (without quotes) and press Return. This will take you to the correct part of the file. Now, type "defoptions=vga=791" (without quotes) in the blank line below the one that starts with "# defoptions=quiet".

Hold down Ctrl and X, release those keys, press Y and press Return.

Then type: sudo update-initramfs -u -k `uname -r`

Bear in mind I haven't told you how to make copies of each of the files, so be careful not to make a mistake.

---

### Post by mmmfottrell on 2007-10-21
great directions! your newbie is quite good :) 

so this actually worked for the screen when i shut down, but when i start up it still has the same problem,

i DID get an error after entering the last part thoughit looks like this:

matt@MattF-Laptop:~$ sudo update-initramfs -u -k 'uname -r'
update-initramfs: Generating /boot/initrd.img-uname -r
Cannot find /lib/modules/uname -r
update-initramfs: failed for /boot/initrd.img-uname -r

hopefully i can get this fixed soon. i dont care about aesthetics, but it just takes FOREVER to start up.

---

### Post by misfitpierce on 2007-10-21
Mine boots super fast :) If not getting boot up screen malcam has posted way to get it fixed as I did that on friends computer.

---

### Post by riviera84 on 2007-10-21
Hi there. I'm fairly new to Linux, and brand new to Ubuntu as of yesterday. I've been using SUSE for compatibility reasons. Anyways, I had this same problem with the poor load time and no splash screen. The fix in this thread worked fantastically.  

I run an HP Pavilion dv8309us laptop
radeon xpress200M - graphics
AMD Turion64

running dual boot 

Gutsy Gibbon and XP Media Center

Keep up the good work, 7.10 is very well polished. Hard to believe they give this thing away.

---

### Post by pologoped2 on 2007-10-21
This Method:

 Originally Posted by Arroyo  View Post
In my case, following the instructions in this post solved the problem:
[http://ubuntuforums.org/showpost.php...87&postcount=4](http://ubuntuforums.org/showpost.php...87&postcount=4)

Now there's no more black screen during bootup, and it's also much faster.

Will vastly improve your bootup/shutdown time and show the ubuntu graphics while booting or shutting down, HOWEVER the reason that ubuntu gusty takes so long to boot is so that it establishes a connection via wireless.  

I followed the above procedure and my wireless stopped working (not getting an ip address).  After undoing the procedure, bootup took twice as long but i had my internet back up and running.  

Its worth the wait to have your internet properly work.  I am using WEP with a linksys router and compaq nc4010 laptop

---

### Post by berZirker on 2007-10-21
Another win for fcumok.  Thanks alot!!!

---

### Post by Strangerdave on 2007-10-21
Well I used to have a dual boot Toshiba Satellite A70 with Windoze XP and Gutsy.  Gutsy booted super fast and I was really impressed so I wiped windoze from my machine and reinstalled Gutsy.  I took forever to boot up and I couldn't understand why the change, but I would like to thank Malcam for the detailed instructions which seemed to have fixed the problem.

Great work!!

-SD-

---

### Post by sapack on 2007-10-21
I got the same thing until I looked at it again real hard.  The quote mark on the `uname -r` is not the single quote ' 
It's the tick mark on the tilde key (hash mark?).  Try it again.  This worked for me.

> **mmmfottrell said:**
> great directions! your newbie is quite good :) 

so this actually worked for the screen when i shut down, but when i start up it still has the same problem,

i DID get an error after entering the last part thoughit looks like this:

matt@MattF-Laptop:~$ sudo update-initramfs -u -k 'uname -r'
update-initramfs: Generating /boot/initrd.img-uname -r
Cannot find /lib/modules/uname -r
update-initramfs: failed for /boot/initrd.img-uname -r

hopefully i can get this fixed soon. i dont care about aesthetics, but it just takes FOREVER to start up.

---

### Post by Anbog on 2007-10-22
Hi have the same problem and will try this solution as well. However, I would like to know what I'm actually doing:
1. Changing the resolution of what?
2. Is it running the "defoptions=quiet" or is it blocked by the "#" and what does "defoptions=vga=791" do?
3. I have no idea what's happening here!

Sorry if this seems really easy, but I only installed Gutsy 2 days ago and never used Linux before - hope someone has the time to answer! :)

---

### Post by malcam on 2007-10-22
> **sapack said:**
> I got the same thing until I looked at it again real hard.  The quote mark on the `uname -r` is not the single quote ' 
It's the tick mark on the tilde key (hash mark?).  Try it again.  This worked for me.
Yeah, those are back ticks, not single quotes. On my keyboard - for example - it's the key located above the tab key. Easiest option is to copy the line and then hold down Shift and Insert whilst within the terminal window to paste the text.

---

### Post by crjackson on 2007-10-22
> **Anbog said:**
> Hi have the same problem and will try this solution as well. However, I would like to know what I'm actually doing:
1. Changing the resolution of what?
2. Is it running the "defoptions=quiet" or is it blocked by the "#" and what does "defoptions=vga=791" do?
3. I have no idea what's happening here!

Sorry if this seems really easy, but I only installed Gutsy 2 days ago and never used Linux before - hope someone has the time to answer! :)

quite tells it not to show you all the text output, vga=791 tells it to use 1024x768 during the boot process

---

### Post by crono141 on 2007-10-22
Does this fix kill your wireless internet?  I'm running my gutsy on a laptop and wireless is the most desired internet interface.

---

### Post by crjackson on 2007-10-22
> **crono141 said:**
> Does this fix kill your wireless internet?  I'm running my gutsy on a laptop and wireless is the most desired internet interface.

quite tells it not to show you all the text output, vga=791 tells it to use 1024x768 during the boot process

It has nothing to do with your internet.  I don't see how it could effect it at all.

---

### Post by KoD7085 on 2007-10-22
> **Arroyo said:**
> In my case, following the instructions in this post solved the problem:
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Now there's no more black screen during bootup, and it's also *much* faster.

Thank you, this really helped!  Now, I don't have to wait 2 minutes just to log in.

---

### Post by mmmfottrell on 2007-10-23
> **malcam said:**
> Yeah, those are back ticks, not single quotes. On my keyboard - for example - it's the key located above the tab key. Easiest option is to copy the line and then hold down Shift and Insert whilst within the terminal window to paste the text.

malcam you are great. i was making the mistake of using single quotes without realizing it. this fixed mine and everything now works completely normal with Gutsy :D

:guitar:

---

### Post by mech7 on 2007-10-23
Aahh i first installed updates and then did this trick.. and now it Says Kernel panic.. and file not sun attept kill init..

And it wont boot at all anymore :(

---

### Post by portach king on 2007-10-24
Thank you so much!
This worked marvelously!

---

### Post by curramberon on 2007-10-25
I was having the same problem (randomly), until I realized that the issue was the USB hub that is integrated into my LCD. 

My motherboard gave one extra beep when it detected the LCD USB Hub. The device caused Ubuntu to boot up very slowly.

But this did not happen every time even though the USB hub was always connected. It seemed like the motherboard did not always detect the USB device. When it missed it, Ubuntu would boot up normally.

I disconnected the USB hub, and now I don't have the problem.

Obviously I lost the convenience of being able to connect my mouse, keyboard, and iPod Shuffle to my LCD, and run a single USB cable from the LCD to the PC. 

The motherboard is a GIGABYTE GA-G33M-DS2R.
The LCD is a Getaway FPD2275W.

---

### Post by hobo on 2007-10-26
I too lost my wireless connection after fixing the slow boot problem. The only way I could find to correct this was to go back to the original files. All is well but the slow boot is back. IBM t42, wep,atheros.

---

### Post by DarkKnight70 on 2007-10-26
This worked for me, Thank you. I'm not seeing any issue with the wireless so far. I'm running an IBM thinkpad T41.

---

### Post by Drakkor on 2007-10-26
It is much quicker,now if only I could get rid of that bright peach colored screen after login, I'd be a happy man ! :) I have set the background color in "Login Window Preferences" local tab,to black, put it stll displays that hard on the eyes stupid peach color, full screen !!
Make it stop !! :mad:

---

### Post by crjackson on 2007-10-26
> **hobo said:**
> I too lost my wireless connection after fixing the slow boot problem. The only way I could find to correct this was to go back to the original files. All is well but the slow boot is back. IBM t42, wep,atheros.

How did you go back to the original files?

---

### Post by hobo on 2007-10-27
I had made copies before I modified them. I just renamed them,

---

### Post by Roelski on 2007-10-29
An award-winning thread!  

If there's a Top Ten Things To Know When Installing Gutsy, put this one in there.

Enjoy Ubuntu!


Roelski

---

### Post by ussgeronimo on 2007-10-30
> **mmmfottrell said:**
> great directions! your newbie is quite good :) 

so this actually worked for the screen when i shut down, but when i start up it still has the same problem,

i DID get an error after entering the last part thoughit looks like this:

matt@MattF-Laptop:~$ sudo update-initramfs -u -k 'uname -r'
update-initramfs: Generating /boot/initrd.img-uname -r
Cannot find /lib/modules/uname -r
update-initramfs: failed for /boot/initrd.img-uname -r

hopefully i can get this fixed soon. i dont care about aesthetics, but it just takes FOREVER to start up.
I am getting the same error message after applying the fix, have you found a solution?  Thanks.

---

### Post by diom on 2007-10-31
@ussgeronimo: You have to use the tick mark not the single-quote. That is you use ` not '. The tick mark on Irish (/UK?) keyboards is above the tab sign.

@Everyone else: I had the exact same problem and I've gotten the exact same result. This is by far the best result a single thread has ever delivered for me. Not only is boot up about 5 times faster (literally), I have also noticed that my system is more stable in general...but that may be my imagination. :D

---

### Post by smellydog on 2007-10-31
> **Drakkor said:**
> It is much quicker,now if only I could get rid of that bright peach colored screen after login, I'd be a happy man ! :) I have set the background color in "Login Window Preferences" local tab,to black, put it stll displays that hard on the eyes stupid peach color, full screen !!
Make it stop !! :mad:

give this a try, change the solid color in your desktop background.  I am guessing that it is showing your desktop without loading any of your goodies, and just guessing, you have a wallpaper selected, so it is showing your naked desktop.  Just a guess, but give it a try.

Back to the real problem, my options in this entire thread was the same.  I upgraded from a CD using the update manager.  It cleared up a lot of problems i had when i was using feisty, but my boot is STILL slow, a couple of minutes.  I am using an Averatec 3270 with a sempron processor, 512mb ram, the RAlink evil wireless chip... if my settings are the same as in this thread... any other ideas?

---

### Post by Drakkor on 2007-10-31
Thanks for the try, smellydog  but as far as I know I have changed all the settings I know,and still get this bright peach hard on the eyes,especially in the morning damned 
screen ! And it lasts a full agonizing 30 seconds !  Aaaargh !! :(

---

### Post by stilus on 2007-10-31
> **Drakkor said:**
> Thanks for the try, smellydog  but as far as I know I have changed all the settings I know,and still get this bright peach hard on the eyes,especially in the morning damned 
screen ! And it lasts a full agonizing 30 seconds !  Aaaargh !! :(

(!careful: I'm still running Feisty!)

The bugger is in /usr/share/pixmaps/splash. You can move/ replace/symlink the gnome-splash.png in there, but there must be a nicer way, right? Right: 
open gconf-editor (with alt+F2 ) and go to 
/apps/gnome-session/options/splash_image

Here you can hack it to your hearts content. 

Maybe this is old news (old distro), but I also found: 

If You go to the "Computer" Dropdown, then to "System Configuration"
there's an option called "Login Screen Setup" You choose the gdm splash
screen from the "Graphical Greeter" tab. Right now the only options are
the default gnome splashes or the new Human splash. You can find more
splash screens at [http://www.gnome-look.org](http://www.gnome-look.org) and use the Install theme
button to install them.

---

### Post by Drakkor on 2007-10-31
These are the settings I have,are these what you're referring to ? Even with these settings,
I still get the peach screen.

---

### Post by stilus on 2007-10-31
Ah, I misread. Not a peach splash, but a peach screen. I'm keeping myself awake during an upgrade to gutsy, so I figured: why not figure this out. I have no clue where this gets managed, cause this whole distro with all its bells and whistles is running in 20 directions at the same time, or so it seems. However, the GUI made it possible for me to dump the peach for a more sophisticated black. 

System > Administration > Login window.

Local 

Select the theme you want and use "background color" under the previews. Log out and log back in (maybe a CTRL + Alt + Backspace when you reach the login windows might be a good idea). This works for me. 

Greetings and have fun!

Bouke

---

### Post by dralaroc on 2007-10-31
> **Drakkor said:**
> These are the settings I have,are these what you're referring to ? Even with these settings,
I still get the peach screen.

+1...I am plagued by the Peach screen also.  I want mine black.

---

### Post by stilus on 2007-10-31
hmz, just tried it on gutsy, doesn't work like on feisty. What does work (again, for me!) is:
1) change the color of the background in the login window (under system > adminstration > login window + |local| )
2) hack into /etc/gdm/PreSession/Default, line 61 and change the #dab082 (I believe it was) to #000000. logout and back in, dont forget to set your regular background wallpaper color as well.  

PS: WTF is this so hard?

---

### Post by Drakkor on 2007-10-31
Ok,stilus,that did it,but now I get no progress (flash) ? screen,you know the one that says Ubuntu,and there's a progess bar loading, just black,then the login screen,then black again.
I just want black after I login, I want the load progress bar.

---

### Post by touf on 2007-11-01
Hi,
I tried it on Xubuntu 7.10 ... doesn't changed nothing, boot still slow (but maybe due mainly to my poor computer).
Thanks for the trick, I'll will try on my acer (w Ubuntu) when Acer will have repaired it:(
Cau

---

### Post by natewhipple on 2007-11-04
thanks malcam the instructions worked flawlessly for me. compaq x1030us

many thanks to the UBUNTU community from yet another newby

---

### Post by Evanlec on 2007-11-04
> **stilus said:**
> hmz, just tried it on gutsy, doesn't work like on feisty. What does work (again, for me!) is:
1) change the color of the background in the login window (under system > adminstration > login window + |local| )
2) hack into /etc/gdm/PreSession/Default, line 61 and change the #dab082 (I believe it was) to #000000. logout and back in, dont forget to set your regular background wallpaper color as well.  

PS: WTF is this so hard?

I agree, why is this so difficult?
anyone have easier solution (i realize we're getting a little off topic here)

---

### Post by touf on 2007-11-04
Hi,
works perfectly on acer aspire 5672
no pbs with wifi
thanks a lot

---

### Post by jellytree on 2007-12-29
**mmmfottrell**  - sorry this post is late but I just came across the exact same problem and this is what I did to fix the "***update-initramfs: failed for /boot/initrd.img-uname -r***" error.  

[INDENT]1. Run uname -r in a terminal window and make note of its output (i.e. 2.6.22-14-generic)[/INDENT]

[INDENT]2. Simply replace the 'uname -r' portion of the command with the value obtained above. So in my case I ran "sudo update-initramfs -u -k 2.6.22-14-generic".
[/INDENT]

Hope this helps everyone else who has this problem.

---

