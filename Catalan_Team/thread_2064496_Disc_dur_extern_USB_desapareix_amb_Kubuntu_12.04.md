---
title: "Disc dur extern USB desapareix amb Kubuntu 12.04"
date: 2012-09-29
forum: Catalan Team
---

### Post by vallibona on 2012-09-29
Hola a tots

Tinc un pc amb Kubuntu 12.04 actualitzada.
Tinc un hub usb on connecto el receptor d'un ratolí sense fils Logitech, i els discos externs. Tot ha funcionat sense problema des de fa anys, amb versions anteriors de Kubuntu, i fins avui amb la 12.04, a la que vaig saltar fa menys d'un mes.

Sense motiu aparent, després de baixar les actualitzacions d'avui, el Pendrive Kingston continua operatiu, el ratolí també però el disc dur extern USB Western Digital WD My Passport de 500gb ja no apareix.

El disc funciona bé al portàtil (tant en Kubuntu 10.04 com en WinVista)
Amb un altre cable tampoc el reconeix.
El mateix cable funciona amb un mòbil Nokia, que es reconeix sense problema.
Canviant l'entrada del hub on el connecto tampoc va.
La llum que marca la connexió del disc s'encén.

He googlejat i he vist recomanacions de fer lsub o dmesg, però les sortides no fan cap referència al disc.

Tota ajuda serà benvinguda.
Moltes gràcies

Salutacions,

---

### Post by wgarcia on 2012-09-29
Has notat si has rebut una actualització del nucli (algun paquet que comença amb "linux")? És possible que t'hagi afectat alguna regressió, tot i que seria estrany. Si és així pots provar d'entrar en un nucli més antic, si et surt en el menú d'entrada "grub", i veure si encara hi ha el problema amb el disc. Si no hi és pots anar entrant en aquest nucli més antic i esperar alguna actualització del nucli a veure si s'arregla.

---

### Post by vallibona on 2012-09-29
Hola! Moltes gràcies per la ràpida resposta.
Sols recordo que ha actualitzat Thunderbird. Ara, tafanejant per mirar de trobar un historial d'actualitzacions, he vist que hi havia 4 noves del GRUB.
Al arrencar no puc optar per kernels anteriors, no em surt el Grub ja que no tinc altres operatius instal·lats al PC (bé, sols WXP dins d'un VirtualBox)

Salutacions,

---

### Post by wgarcia on 2012-09-29
Per veure si el sistema el reconeix, les de desendollar i tornar a endollar, i mirar les últimes línies que et dóna la instrucció

```
dmesg
```

des d'una terminal.

---

### Post by CarlesOriol on 2012-09-29
Quin format té? Els discs ntfs (windows) marcats amb errors no es munten automàticament.

---

### Post by vallibona on 2012-09-29
No sé el format, però porta més d'un any funcionant a Kubuntu 10.04 i 3 setmanes a 12.04, a més d'anar vé a un altre pc amb Vista.

Us apego el resultat quilomètric del dmesg...

Moltes gràcies!!!

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:17:36 UTC 2012 (Ubuntu 3.2.0-31.50-generic 3.2.28)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee2000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. EP43T-UD3L/EP43T-UD3L, BIOS F3 10/16/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable                                                                                                                         
[    0.000000]   2 disabled                                                                                                                                                         
[    0.000000]   3 disabled                                                                                                                                                         
[    0.000000]   4 disabled                                                                                                                                                         
[    0.000000]   5 disabled                                                                                                                                                         
[    0.000000]   6 disabled                                                                                                                                                         
[    0.000000]   7 disabled                                                                                                                                                         
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                                                                                                     
[    0.000000] original variable MTRRs                                                                                                                                              
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB                                                                                                                                
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC                                                                                                                             
[    0.000000] total RAM covered: 2047M                                                                                                                                             
[    0.000000] Found optimal setting for mtrr clean up                                                                                                                              
[    0.000000]  gran_size: 64K  chunk_size: 2M  num_reg: 2      lose cover RAM: 0G                                                                                                  
[    0.000000] New variable MTRRs                                                                                                                                                   
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB                                                                                                                                
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC                                                                                                                             
[    0.000000] found SMP MP-table at [c00f5560] f5560                                                                                                                               
[    0.000000] initial memory mapped : 0 - 01c00000                                                                                                                                 
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384                                                                                                                
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000                                                                                                               
[    0.000000]  0000000000 - 0000400000 page 4k                                                                                                                                     
[    0.000000]  0000400000 - 0037400000 page 2M                                                                                                                                     
[    0.000000]  0037400000 - 00377fe000 page 4k                                                                                                                                     
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000                                                                                                        
[    0.000000] RAMDISK: 356e0000 - 36b68000                                                                                                                                         
[    0.000000] ACPI: RSDP 000f6f60 00014 (v00 GBT   )                                                                                                                               
[    0.000000] ACPI: RSDT 7fee2040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)                                                                                               
[    0.000000] ACPI: FACP 7fee20c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)                                                                                               
[    0.000000] ACPI: DSDT 7fee2180 04B3E (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)                                                                                               
[    0.000000] ACPI: FACS 7fee0000 00040                                                                                                                                            
[    0.000000] ACPI: HPET 7fee6e00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7fee6e80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: EUDS 7fee6ec0 00000 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 7fee73e0 0670A (v01 GBT    GBT   B0 5455312E BG?? 00020101)
[    0.000000] ACPI: APIC 7fee6d00 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 7feee150 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c1822ec0, node_mem_map f46e0200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:74100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77bd000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-31-generic root=UUID=1aca6558-dd52-4ae2-b7c9-8335372d1555 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 8383744 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2038876k/2096000k available (5618k kernel code, 56672k reserved, 2762k data, 712k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157cb04 - 0xc182f5c0   (2762 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157cb04   (5618 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f400a000 soft=f400c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2933.425 MHz processor.
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5866.85 BogoMIPS (lpj=11733700)
[    0.004005] pid_max: default: 32768 minimum: 301
[    0.004024] Security Framework initialized
[    0.004037] AppArmor: AppArmor initialized
[    0.004038] Yama: becoming mindful.
[    0.004081] Mount-cache hash table entries: 512
[    0.004183] Initializing cgroup subsys cpuacct
[    0.004187] Initializing cgroup subsys memory
[    0.004193] Initializing cgroup subsys devices
[    0.004195] Initializing cgroup subsys freezer
[    0.004197] Initializing cgroup subsys blkio
[    0.004202] Initializing cgroup subsys perf_event
[    0.004222] CPU: Physical Processor ID: 0
[    0.004224] CPU: Processor Core ID: 0
[    0.004227] mce: CPU supports 6 MCE banks
[    0.004233] CPU0: Thermal monitoring enabled (TM2)
[    0.004237] using mwait in idle threads.
[    0.009409] ACPI: Core revision 20110623
[    0.011630] ftrace: allocating 25901 entries in 51 pages
[    0.012039] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016335] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056323] CPU0: Intel Pentium(R) Dual-Core  CPU      E6500  @ 2.93GHz stepping 0a
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f40f2000 soft=f40f4000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148062] Brought up 2 CPUs
[    0.148064] Total of 2 processors activated (11733.68 BogoMIPS).
[    0.149235] devtmpfs: initialized
[    0.149235] EVM: security.selinux
[    0.149235] EVM: security.SMACK64
[    0.149235] EVM: security.capability
[    0.149235] PM: Registering ACPI NVS region at 7fee0000 (8192 bytes)
[    0.149235] print_constraints: dummy: 
[    0.149235] RTC time: 13:56:44, date: 09/29/12
[    0.149235] NET: Registered protocol family 16
[    0.149235] Trying to unpack rootfs image as initramfs...
[    0.149235] EISA bus registered
[    0.149235] ACPI: bus type pci registered
[    0.149235] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.149235] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.149235] PCI: Using MMCONFIG for extended config space
[    0.149235] PCI: Using configuration type 1 for base access
[    0.150021] bio: create slab <bio-0> at 0
[    0.150087] ACPI: Added _OSI(Module Device)
[    0.150089] ACPI: Added _OSI(Processor Device)
[    0.150091] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.150093] ACPI: Added _OSI(Processor Aggregator Device)
[    0.152280] ACPI: EC: Look up EC in DSDT
[    0.155090] ACPI Warning: Incorrect checksum in table [TAMG] - 0xB7, should be 0xB6 (20110623/tbutils-314)
[    0.155210] ACPI: SSDT 7feedb30 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.155376] ACPI: Dynamic OEM Table Load:
[    0.155379] ACPI: SSDT   (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.155489] ACPI: SSDT 7feedff0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.155648] ACPI: Dynamic OEM Table Load:
[    0.155650] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.155776] ACPI: Interpreter enabled
[    0.155790] ACPI: (supports S0 S3 S4 S5)
[    0.155806] ACPI: Using IOAPIC for interrupt routing
[    0.159604] ACPI: No dock devices found.
[    0.159606] HEST: Table not found.
[    0.159612] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.159657] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.159753] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.159755] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.159757] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.159759] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.159761] pci_root PNP0A03:00: host bridge window [mem 0x7ff00000-0xfebfffff]
[    0.159773] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.159811] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.159851] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.159855] pci 0000:00:01.0: PME# disabled
[    0.159888] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.159928] pci 0000:00:1a.0: reg 20: [io  0xff00-0xff1f]
[    0.159974] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.160017] pci 0000:00:1a.1: reg 20: [io  0xfe00-0xfe1f]
[    0.160070] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.160109] pci 0000:00:1a.2: reg 20: [io  0xfd00-0xfd1f]
[    0.160160] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.160175] pci 0000:00:1a.7: reg 10: [mem 0xfdfff000-0xfdfff3ff]
[    0.160257] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.160270] pci 0000:00:1b.0: reg 10: [mem 0xfdff8000-0xfdffbfff 64bit]
[    0.160332] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.160336] pci 0000:00:1b.0: PME# disabled
[    0.160353] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.160416] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.160420] pci 0000:00:1c.0: PME# disabled
[    0.160441] pci 0000:00:1c.4: [8086:3a48] type 1 class 0x000604
[    0.160503] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.160506] pci 0000:00:1c.4: PME# disabled
[    0.160525] pci 0000:00:1c.5: [8086:3a4a] type 1 class 0x000604
[    0.160588] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.160591] pci 0000:00:1c.5: PME# disabled
[    0.160611] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.160650] pci 0000:00:1d.0: reg 20: [io  0xfc00-0xfc1f]
[    0.160697] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.160735] pci 0000:00:1d.1: reg 20: [io  0xfb00-0xfb1f]
[    0.160780] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.160818] pci 0000:00:1d.2: reg 20: [io  0xfa00-0xfa1f]
[    0.160870] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.160885] pci 0000:00:1d.7: reg 10: [mem 0xfdffe000-0xfdffe3ff]
[    0.160963] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.161019] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.161125] pci 0000:00:1f.2: [8086:3a20] type 0 class 0x000101
[    0.161138] pci 0000:00:1f.2: reg 10: [io  0xf900-0xf907]
[    0.161145] pci 0000:00:1f.2: reg 14: [io  0xf800-0xf803]
[    0.161152] pci 0000:00:1f.2: reg 18: [io  0xf700-0xf707]
[    0.161159] pci 0000:00:1f.2: reg 1c: [io  0xf600-0xf603]
[    0.161167] pci 0000:00:1f.2: reg 20: [io  0xf500-0xf50f]
[    0.161175] pci 0000:00:1f.2: reg 24: [io  0xf400-0xf40f]
[    0.161216] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.161229] pci 0000:00:1f.3: reg 10: [mem 0xfdffd000-0xfdffd0ff 64bit]
[    0.161248] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.161278] pci 0000:00:1f.5: [8086:3a26] type 0 class 0x000101
[    0.161291] pci 0000:00:1f.5: reg 10: [io  0xf200-0xf207]
[    0.161298] pci 0000:00:1f.5: reg 14: [io  0xf100-0xf103]
[    0.161305] pci 0000:00:1f.5: reg 18: [io  0xf000-0xf007]
[    0.161312] pci 0000:00:1f.5: reg 1c: [io  0xef00-0xef03]
[    0.161319] pci 0000:00:1f.5: reg 20: [io  0xee00-0xee0f]
[    0.161326] pci 0000:00:1f.5: reg 24: [io  0xed00-0xed0f]
[    0.161396] pci 0000:01:00.0: [10de:06e4] type 0 class 0x000300
[    0.161406] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.161416] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.161426] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.161433] pci 0000:01:00.0: reg 24: [io  0xbf00-0xbf7f]
[    0.161440] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.161491] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.161494] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.161497] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.161500] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.161535] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.161594] pci 0000:03:00.0: [197b:2368] type 0 class 0x000101
[    0.161622] pci 0000:03:00.0: reg 10: [io  0xdf00-0xdf07]
[    0.161635] pci 0000:03:00.0: reg 14: [io  0xde00-0xde03]
[    0.161648] pci 0000:03:00.0: reg 18: [io  0xdd00-0xdd07]
[    0.161661] pci 0000:03:00.0: reg 1c: [io  0xdc00-0xdc03]
[    0.161674] pci 0000:03:00.0: reg 20: [io  0xdb00-0xdb0f]
[    0.161763] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.161772] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.161776] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.161779] pci 0000:00:1c.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.161835] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
[    0.161850] pci 0000:04:00.0: reg 10: [io  0xce00-0xceff]
[    0.161877] pci 0000:04:00.0: reg 18: [mem 0xfdeff000-0xfdefffff 64bit pref]
[    0.161894] pci 0000:04:00.0: reg 20: [mem 0xfdee0000-0xfdeeffff 64bit pref]
[    0.161906] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.161967] pci 0000:04:00.0: supports D1 D2
[    0.161969] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.161973] pci 0000:04:00.0: PME# disabled
[    0.168029] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.168034] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.168038] pci 0000:00:1c.5:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.168044] pci 0000:00:1c.5:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.168103] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.168112] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.168114] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.168117] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.168119] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.168121] pci 0000:00:1e.0:   bridge window [mem 0x7ff00000-0xfebfffff] (subtractive decode)
[    0.168140] pci_bus 0000:00: on NUMA node 0
[    0.168147] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.168363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.168406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.168440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.168535]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.168537]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.168539] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.176819] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.176860] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.176898] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.176936] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[    0.176974] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.177013] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.177051] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.177089] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[    0.177186] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177189] vgaarb: loaded
[    0.177191] vgaarb: bridge control possible 0000:01:00.0
[    0.177290] i2c-core: driver [aat2870] using legacy suspend method
[    0.177291] i2c-core: driver [aat2870] using legacy resume method
[    0.177363] SCSI subsystem initialized
[    0.177408] libata version 3.00 loaded.
[    0.177448] usbcore: registered new interface driver usbfs
[    0.177458] usbcore: registered new interface driver hub
[    0.177479] usbcore: registered new device driver usb
[    0.177553] PCI: Using ACPI for IRQ routing
[    0.178802] PCI: pci_cache_line_size set to 64 bytes
[    0.178875] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.178878] reserve RAM buffer: 000000007fee0000 - 000000007fffffff 
[    0.178964] NetLabel: Initializing
[    0.178966] NetLabel:  domain hash size = 128
[    0.178967] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.178975] NetLabel:  unlabeled traffic allowed by default
[    0.179014] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.179019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.179023] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.184062] Switching to clocksource hpet
[    0.190674] AppArmor: AppArmor Filesystem Enabled
[    0.190701] pnp: PnP ACPI init
[    0.190716] ACPI: bus type pnp registered
[    0.190799] pnp 00:00: [bus 00-3f]
[    0.190801] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.190803] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.190805] pnp 00:00: [io  0x0d00-0xffff window]
[    0.190807] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.190809] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.190811] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
[    0.190862] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.190928] pnp 00:01: [io  0x0010-0x001f]
[    0.190930] pnp 00:01: [io  0x0022-0x003f]
[    0.190931] pnp 00:01: [io  0x0044-0x005f]
[    0.190933] pnp 00:01: [io  0x0062-0x0063]
[    0.190934] pnp 00:01: [io  0x0065-0x006f]
[    0.190936] pnp 00:01: [io  0x0074-0x007f]
[    0.190938] pnp 00:01: [io  0x0091-0x0093]
[    0.190939] pnp 00:01: [io  0x00a2-0x00bf]
[    0.190941] pnp 00:01: [io  0x00e0-0x00ef]
[    0.190942] pnp 00:01: [io  0x04d0-0x04d1]
[    0.190946] pnp 00:01: [io  0x0290-0x029f]
[    0.190948] pnp 00:01: [io  0x0800-0x087f]
[    0.190949] pnp 00:01: [io  0x0290-0x0294]
[    0.190951] pnp 00:01: [io  0x0880-0x088f]
[    0.191011] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.191013] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.191015] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.191017] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.191020] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.191022] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191032] pnp 00:02: [dma 4]
[    0.191034] pnp 00:02: [io  0x0000-0x000f]
[    0.191035] pnp 00:02: [io  0x0080-0x0090]
[    0.191037] pnp 00:02: [io  0x0094-0x009f]
[    0.191039] pnp 00:02: [io  0x00c0-0x00df]
[    0.191065] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.191104] pnp 00:03: [irq 0 disabled]
[    0.191114] pnp 00:03: [irq 8]
[    0.191116] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.191142] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.191163] pnp 00:04: [io  0x0070-0x0073]
[    0.191192] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.191199] pnp 00:05: [io  0x0061]
[    0.191225] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.191232] pnp 00:06: [io  0x00f0-0x00ff]
[    0.191237] pnp 00:06: [irq 13]
[    0.191264] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.191355] pnp 00:07: [io  0x03f0-0x03f5]
[    0.191357] pnp 00:07: [io  0x03f7]
[    0.191361] pnp 00:07: [irq 6]
[    0.191363] pnp 00:07: [dma 2]
[    0.191402] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.191530] pnp 00:08: [io  0x03f8-0x03ff]
[    0.191535] pnp 00:08: [irq 4]
[    0.191584] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.191729] pnp 00:09: [io  0x0378-0x037f]
[    0.191734] pnp 00:09: [irq 7]
[    0.191778] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.191849] pnp 00:0a: [io  0x0060]
[    0.191851] pnp 00:0a: [io  0x0064]
[    0.191855] pnp 00:0a: [irq 1]
[    0.191884] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.191908] pnp 00:0b: [io  0x0400-0x04cf]
[    0.191910] pnp 00:0b: [io  0x04d2-0x04ff]
[    0.191955] system 00:0b: [io  0x0400-0x04cf] has been reserved
[    0.191958] system 00:0b: [io  0x04d2-0x04ff] has been reserved
[    0.191960] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192140] pnp 00:0c: [mem 0xf4000000-0xf7ffffff]
[    0.192191] system 00:0c: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.192194] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192320] pnp 00:0d: [mem 0x000cde00-0x000cffff]
[    0.192322] pnp 00:0d: [mem 0x000f0000-0x000f7fff]
[    0.192323] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
[    0.192325] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.192327] pnp 00:0d: [mem 0x7fee0000-0x7fefffff]
[    0.192329] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.192331] pnp 00:0d: [mem 0x00100000-0x7fedffff]
[    0.192332] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.192334] pnp 00:0d: [mem 0xfed10000-0xfed1dfff]
[    0.192336] pnp 00:0d: [mem 0xfed20000-0xfed8ffff]
[    0.192337] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.192339] pnp 00:0d: [mem 0xffb00000-0xffb7ffff]
[    0.192341] pnp 00:0d: [mem 0xfff00000-0xffffffff]
[    0.192343] pnp 00:0d: [mem 0x000e0000-0x000effff]
[    0.192402] system 00:0d: [mem 0x000cde00-0x000cffff] has been reserved
[    0.192404] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.192406] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.192409] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.192411] system 00:0d: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.192413] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.192415] system 00:0d: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.192418] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.192420] system 00:0d: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.192422] system 00:0d: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.192424] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.192426] system 00:0d: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.192429] system 00:0d: [mem 0xfff00000-0xffffffff] has been reserved
[    0.192431] system 00:0d: [mem 0x000e0000-0x000effff] has been reserved
[    0.192434] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.192449] pnp 00:0e: [mem 0xffb80000-0xffbfffff]
[    0.192491] pnp 00:0e: Plug and Play ACPI device, IDs INT0800 (active)
[    0.192496] pnp: PnP ACPI: found 15 devices
[    0.192497] ACPI: ACPI bus type pnp unregistered
[    0.192501] PnPBIOS: Disabled by ACPI PNP
[    0.228494] PCI: max bus depth: 1 pci_try_num: 2
[    0.228533] pci 0000:00:1c.4: BAR 15: assigned [mem 0x7ff00000-0x800fffff 64bit pref]
[    0.228536] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80100000-0x802fffff]
[    0.228539] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80300000-0x804fffff 64bit pref]
[    0.228542] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.228545] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
[    0.228547] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.228550] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.228553] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.228556] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.228560] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.228562] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.228566] pci 0000:00:1c.0:   bridge window [mem 0x80100000-0x802fffff]
[    0.228570] pci 0000:00:1c.0:   bridge window [mem 0x80300000-0x804fffff 64bit pref]
[    0.228575] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.228578] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.228582] pci 0000:00:1c.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.228585] pci 0000:00:1c.4:   bridge window [mem 0x7ff00000-0x800fffff 64bit pref]
[    0.228591] pci 0000:04:00.0: BAR 6: assigned [mem 0xfde00000-0xfde0ffff pref]
[    0.228593] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.228595] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.228600] pci 0000:00:1c.5:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.228603] pci 0000:00:1c.5:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.228608] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.228632] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.228636] pci 0000:00:01.0: setting latency timer to 64
[    0.228642] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.228646] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.228650] pci 0000:00:1c.0: setting latency timer to 64
[    0.228655] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.228658] pci 0000:00:1c.4: setting latency timer to 64
[    0.228667] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.228670] pci 0000:00:1c.5: setting latency timer to 64
[    0.228677] pci 0000:00:1e.0: setting latency timer to 64
[    0.228680] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.228682] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.228684] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.228686] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.228688] pci_bus 0000:00: resource 8 [mem 0x7ff00000-0xfebfffff]
[    0.228690] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.228692] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.228694] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.228696] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.228698] pci_bus 0000:02: resource 1 [mem 0x80100000-0x802fffff]
[    0.228700] pci_bus 0000:02: resource 2 [mem 0x80300000-0x804fffff 64bit pref]
[    0.228703] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.228704] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.228706] pci_bus 0000:03: resource 2 [mem 0x7ff00000-0x800fffff 64bit pref]
[    0.228709] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.228710] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.228713] pci_bus 0000:04: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.228715] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.228717] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.228719] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.228720] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.228722] pci_bus 0000:05: resource 8 [mem 0x7ff00000-0xfebfffff]
[    0.228759] NET: Registered protocol family 2
[    0.228819] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.229011] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.229357] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.229538] TCP: Hash tables configured (established 131072 bind 65536)
[    0.229540] TCP reno registered
[    0.229542] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.229548] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.229617] NET: Registered protocol family 1
[    0.229641] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.229657] pci 0000:00:1a.0: PCI INT A disabled
[    0.229670] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.229684] pci 0000:00:1a.1: PCI INT B disabled
[    0.229694] pci 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.229708] pci 0000:00:1a.2: PCI INT C disabled
[    0.229715] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.244036] pci 0000:00:1a.7: PCI INT C disabled
[    0.244063] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.244078] pci 0000:00:1d.0: PCI INT A disabled
[    0.244090] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.244105] pci 0000:00:1d.1: PCI INT B disabled
[    0.244110] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.244125] pci 0000:00:1d.2: PCI INT C disabled
[    0.244132] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.260032] pci 0000:00:1d.7: PCI INT A disabled
[    0.260056] pci 0000:01:00.0: Boot video device
[    0.260064] PCI: CLS 4 bytes, default 64
[    0.260363] audit: initializing netlink socket (disabled)
[    0.260374] type=2000 audit(1348927004.256:1): initialized
[    0.276210] highmem bounce pool size: 64 pages
[    0.276216] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.277815] VFS: Disk quotas dquot_6.5.2
[    0.277864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.278323] fuse init (API version 7.17)
[    0.278395] msgmni has been set to 1664
[    0.278639] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.278659] io scheduler noop registered
[    0.278661] io scheduler deadline registered
[    0.278666] io scheduler cfq registered (default)
[    0.278768] pcieport 0000:00:01.0: setting latency timer to 64
[    0.278796] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.278840] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.278871] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.278920] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.278951] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.278999] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.279032] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.279104] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.279123] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.279198] intel_idle: MWAIT substates: 0x22220
[    0.279200] intel_idle: does not run on family 6 model 23
[    0.279264] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.279268] ACPI: Power Button [PWRB]
[    0.279312] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.279314] ACPI: Power Button [PWRF]
[    0.279482] Marking TSC unstable due to TSC halts in idle
[    0.279486] ACPI: acpi_idle registered with cpuidle
[    0.280630] ERST: Table is not found!
[    0.280632] GHES: HEST is not enabled!
[    0.280695] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.301059] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.301185] isapnp: Scanning for PnP cards...
[    0.491043] Freeing initrd memory: 21024k freed
[    0.654028] isapnp: No Plug & Play device found
[    0.728587] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.744346] Linux agpgart interface v0.103
[    0.745748] brd: module loaded
[    0.746410] loop: module loaded
[    0.746533] ata_piix 0000:00:1f.2: version 2.13
[    0.746546] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.746550] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.746587] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.746838] scsi0 : ata_piix
[    0.746906] scsi1 : ata_piix
[    0.747275] ata1: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    0.747280] ata2: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    0.747296] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.747300] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.747332] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.747505] scsi2 : ata_piix
[    0.747563] scsi3 : ata_piix
[    0.747871] ata3: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[    0.747875] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[    0.747928] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.747951] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.747963] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.748253] Fixed MDIO Bus: probed
[    0.748270] tun: Universal TUN/TAP device driver, 1.6
[    0.748271] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.748313] PPP generic driver version 2.4.2
[    0.748397] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.748408] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.748419] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.748422] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.748454] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.752345] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    0.752358] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    0.768016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.768202] hub 1-0:1.0: USB hub found
[    0.768205] hub 1-0:1.0: 6 ports detected
[    0.768267] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.768276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.768279] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.768312] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.772212] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    0.772224] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    0.788015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.788176] hub 2-0:1.0: USB hub found
[    0.788181] hub 2-0:1.0: 6 ports detected
[    0.788252] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.788263] uhci_hcd: USB Universal Host Controller Interface driver
[    0.788275] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.788281] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.788284] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.788318] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.788347] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    0.788447] hub 3-0:1.0: USB hub found
[    0.788451] hub 3-0:1.0: 2 ports detected
[    0.788503] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.788508] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.788511] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.788544] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.788571] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    0.788672] hub 4-0:1.0: USB hub found
[    0.788674] hub 4-0:1.0: 2 ports detected
[    0.788724] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.788730] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.788732] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.788767] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.788786] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    0.788891] hub 5-0:1.0: USB hub found
[    0.788894] hub 5-0:1.0: 2 ports detected
[    0.788947] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.788953] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.788956] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.788989] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.789010] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    0.789109] hub 6-0:1.0: USB hub found
[    0.789112] hub 6-0:1.0: 2 ports detected
[    0.789164] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.789170] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.789172] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.789205] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.789225] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    0.789326] hub 7-0:1.0: USB hub found
[    0.789329] hub 7-0:1.0: 2 ports detected
[    0.789382] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.789388] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.789390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.789427] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.789447] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    0.789546] hub 8-0:1.0: USB hub found
[    0.789549] hub 8-0:1.0: 2 ports detected
[    0.789649] usbcore: registered new interface driver libusual
[    0.789690] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.789691] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.789844] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.789933] mousedev: PS/2 mouse device common for all mice
[    0.790062] rtc_cmos 00:04: RTC can wake from S4
[    0.790149] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.790170] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.790226] device-mapper: uevent: version 1.0.3
[    0.790286] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.790314] EISA: Probing bus 0 at eisa.0
[    0.790315] EISA: Cannot allocate resource for mainboard
[    0.790317] Cannot allocate resource for EISA slot 1
[    0.790319] Cannot allocate resource for EISA slot 2
[    0.790320] Cannot allocate resource for EISA slot 3
[    0.790321] Cannot allocate resource for EISA slot 4
[    0.790323] Cannot allocate resource for EISA slot 5
[    0.790324] Cannot allocate resource for EISA slot 6
[    0.790326] Cannot allocate resource for EISA slot 7
[    0.790327] Cannot allocate resource for EISA slot 8
[    0.790328] EISA: Detected 0 cards.
[    0.790336] cpufreq-nforce2: No nForce2 chipset.
[    0.790362] cpuidle: using governor ladder
[    0.790405] cpuidle: using governor menu
[    0.790407] EFI Variables Facility v0.08 2004-May-17
[    0.790619] TCP cubic registered
[    0.790717] NET: Registered protocol family 10
[    0.791195] NET: Registered protocol family 17
[    0.791199] Registering the dns_resolver key type
[    0.791213] Using IPI No-Shortcut mode
[    0.791306] PM: Hibernation image not present or could not be loaded.
[    0.791315] registered taskstats version 1
[    0.796477]   Magic number: 12:467:939
[    0.796555] rtc_cmos 00:04: setting system clock to 2012-09-29 13:56:45 UTC (1348927005)
[    0.797249] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.797252] EDD information not available.
[    0.807204] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.074567] ata4: SATA link down (SStatus 0 SControl 300)
[    1.080013] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.085121] ata3: SATA link down (SStatus 0 SControl 300)
[    1.213841] hub 1-1:1.0: USB hub found
[    1.214166] hub 1-1:1.0: 4 ports detected
[    1.324034] usb 1-3: new high-speed USB device number 3 using ehci_hcd
[    1.394686] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.394697] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.540065] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.540078] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.548328] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    1.548332] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.564328] ata1.00: configured for UDMA/133
[    1.564483] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    1.564635] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.564656] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.564673] sd 0:0:0:0: [sda] Write Protect is off
[    1.564676] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.564692] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.568020] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.587366]  sda: sda1
[    1.587598] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.587621] Freeing unused kernel memory: 712k freed
[    1.587809] Write protecting the kernel text: 5620k
[    1.587846] Write protecting the kernel read-only data: 2324k
[    1.600923] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    1.601103] zram: num_devices not specified. Using default: 1
[    1.601105] zram: Creating 1 devices ...
[    1.603879] udevd[100]: starting version 175
[    1.661321] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.661341] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.661365] r8169 0000:04:00.0: setting latency timer to 64
[    1.661418] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.661841] r8169 0000:04:00.0: eth0: RTL8168c/8111c at 0xf8028000, 6c:f0:49:03:fd:6f, XID 1c4000c0 IRQ 44
[    1.661844] r8169 0000:04:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.663222] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.663255] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    1.669677] scsi4 : pata_jmicron
[    1.673633] scsi5 : pata_jmicron
[    1.674189] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 16
[    1.674191] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 16
[    1.675748] Floppy drive(s): fd0 is 1.44M
[    1.695779] FDC 0 is a post-1991 82077
[    1.700780] Adding 1030304k swap on /dev/zram0.  Priority:100 extents:1 across:1030304k SS
[    1.772301] usb 1-1.1: new low-speed USB device number 5 using ehci_hcd
[    1.846093] ata5.00: ATA-7: Maxtor 6B200P0, BAH41B70, max UDMA/133
[    1.846099] ata5.00: 398297088 sectors, multi 16: LBA48 
[    1.846106] ata5.01: ATAPI: HL-DT-STDVD-RAM GSA-H55L, 1.03, max UDMA/66
[    1.862068] ata5.00: configured for UDMA/100
[    1.876595] ata5.01: configured for UDMA/66
[    1.877932] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6B200P0   BAH4 PQ: 0 ANSI: 5
[    1.878044] sd 4:0:0:0: [sdb] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    1.878064] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.878082] sd 4:0:0:0: [sdb] Write Protect is off
[    1.878085] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.878102] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.896432] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55L 1.03 PQ: 0 ANSI: 5
[    1.923491] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.923495] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.923636] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    1.923693] sr 4:0:1:0: Attached scsi generic sg2 type 5
[    1.940632]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 >
[    1.941481] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.984363] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1:1.0/input/input3
[    1.984445] generic-usb 0003:046D:C518.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.7-1.1/input0
[    1.990041] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1:1.1/input/input4
[    1.990184] generic-usb 0003:046D:C518.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.7-1.1/input1
[    1.990196] usbcore: registered new interface driver usbhid
[    1.990197] usbhid: USB HID core driver
[    3.757818] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    3.757820] vesafb: scrolling: redraw
[    3.757822] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.759046] vesafb: framebuffer at 0xf9000000, mapped to 0xf8300000, using 5120k, total 5120k
[    3.759109] fbcon: VESA VGA (fb0) is primary device
[    3.759151] Console: switching to colour frame buffer device 160x64
[    3.759177] fb0: VESA VGA frame buffer device
[    4.432441] Btrfs loaded
[    4.436722] xor: automatically using best checksumming function: pIII_sse
[    4.456006]    pIII_sse  : 11192.000 MB/sec
[    4.456007] xor: using function: pIII_sse (11192.000 MB/sec)
[    4.456461] device-mapper: dm-raid45: initialized v0.2594b
[    4.820022] end_request: I/O error, dev fd0, sector 0
[    4.900036] kjournald starting.  Commit interval 5 seconds
[    4.900067] EXT3-fs (sdb5): mounted filesystem with ordered data mode
[   20.123999] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.161974] udevd[440]: starting version 175
[   20.191768] lp: driver loaded but no devices found
[   20.234405] Adding 2931824k swap on /dev/sdb6.  Priority:-1 extents:1 across:2931824k 
[   20.250462] udevd[475]: renamed network interface eth0 to eth1
[   20.280136] type=1400 audit(1348927024.982:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=539 comm="apparmor_parser"
[   20.280463] type=1400 audit(1348927024.982:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=539 comm="apparmor_parser"
[   20.280653] type=1400 audit(1348927024.982:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=539 comm="apparmor_parser"
[   20.300688] nvidia: module license 'NVIDIA' taints kernel.
[   20.300691] Disabling lock debugging due to kernel taint
[   20.463841] parport_pc 00:09: reported by Plug and Play ACPI
[   20.463882] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.473420] device-mapper: multipath: version 1.3.0 loaded
[   20.569741] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.569750] nvidia 0000:01:00.0: setting latency timer to 64
[   20.569755] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.569900] lp0: using parport0 (interrupt-driven).
[   20.570601] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
[   20.661491] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.661534] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.661556] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.682693] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   20.705842] hda_codec: ALC888: BIOS auto-probing.
[   20.707020] ppdev: user-space parallel port driver
[   20.708117] r8712u: DriverVersion: v7_0.20100831
[   20.708130] r8712u: register rtl8712_netdev_ops to netdev_ops
[   20.708132] r8712u: USB_SPEED_HIGH with 4 endpoints
[   20.711157] r8712u: Boot from EFUSE: Autoload OK
[   20.722696] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   20.722868] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   20.723018] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.723176] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.723333] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.728787] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.728986] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.729123] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8C11
[   20.729139] usbcore: registered new interface driver usblp
[   20.729495] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.103169] r8712u: CustomerID = 0x0000
[   21.103177] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   21.103952] usbcore: registered new interface driver r8712u
[   21.940244] EXT3-fs (sdb5): using internal journal
[   22.373424] kjournald starting.  Commit interval 5 seconds
[   22.381120] EXT3-fs (sdb1): using internal journal
[   22.381126] EXT3-fs (sdb1): mounted filesystem with ordered data mode
[   23.176779] kjournald starting.  Commit interval 5 seconds
[   23.177264] EXT3-fs (sdb7): using internal journal
[   23.177270] EXT3-fs (sdb7): mounted filesystem with ordered data mode
[   24.078110] init: failsafe main process (1051) killed by TERM signal
[   24.185963] type=1400 audit(1348927028.886:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1113 comm="apparmor_parser"
[   24.186370] type=1400 audit(1348927028.886:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1113 comm="apparmor_parser"
[   24.187474] Bluetooth: Core ver 2.16
[   24.187500] NET: Registered protocol family 31
[   24.187502] Bluetooth: HCI device and connection manager initialized
[   24.187504] Bluetooth: HCI socket layer initialized
[   24.187506] Bluetooth: L2CAP socket layer initialized
[   24.187834] Bluetooth: SCO socket layer initialized
[   24.191110] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.191113] Bluetooth: BNEP filters: protocol multicast
[   24.217886] type=1400 audit(1348927028.918:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1150 comm="apparmor_parser"
[   24.218234] type=1400 audit(1348927028.918:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1150 comm="apparmor_parser"
[   24.218427] type=1400 audit(1348927028.918:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1150 comm="apparmor_parser"
[   24.221466] type=1400 audit(1348927028.922:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1153 comm="apparmor_parser"
[   24.223010] type=1400 audit(1348927028.922:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1154 comm="apparmor_parser"
[   24.288933] Bluetooth: RFCOMM TTY layer initialized
[   24.288937] Bluetooth: RFCOMM socket layer initialized
[   24.288939] Bluetooth: RFCOMM ver 1.11
[   24.643931] vboxdrv: Found 2 processor cores.
[   24.644568] vboxdrv: fAsync=0 offMin=0x27e offMax=0xf0a
[   24.644616] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.644618] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   24.656887] vboxpci: IOMMU not found (not registered)
[   25.204416] r8712u: 1 RCR=0x153f00e
[   25.205164] r8712u: 2 RCR=0x553f00e
[   25.312433] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.312646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.317718] r8169 0000:04:00.0: eth1: link down
[   25.320779] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.360023] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.015853] r8712u: wpa_set_encryption, crypt.alg = WEP
[   36.379154] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.248011] wlan0: no IPv6 routers present
[  249.267125] audit_printk_skb: 9 callbacks suppressed
[  249.267129] type=1701 audit(1348927253.966:15): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2381 comm="chrome" reason="seccomp" sig=0 syscall=20 ip=0xbbc416 code=0x50001
[  256.060769] type=1701 audit(1348927260.763:16): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2421 comm="chrome" reason="seccomp" sig=0 syscall=20 ip=0xc4b416 code=0x50001
[  423.168357] usb 1-1.3: new high-speed USB device number 6 using ehci_hcd
[  423.284712] Initializing USB Mass Storage driver...
[  423.284943] scsi6 : usb-storage 1-1.3:1.0
[  423.285059] usbcore: registered new interface driver usb-storage
[  423.285062] USB Mass Storage support registered.
[  423.285530] usbcore: registered new interface driver uas
[  424.306186] scsi 6:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 4
[  424.306964] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  424.307411] sd 6:0:0:0: [sdc] 7567964 512-byte logical blocks: (3.87 GB/3.60 GiB)
[  424.308097] sd 6:0:0:0: [sdc] Write Protect is off
[  424.308102] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 00
[  424.308942] sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  424.313360]  sdc: sdc1
[  424.315779] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  481.845881] usb 1-1.3: USB disconnect, device number 6
[  555.200332] usb 1-1.4: new high-speed USB device number 7 using ehci_hcd
[  555.296116] scsi7 : usb-storage 1-1.4:1.0
[  556.359032] scsi 7:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 4
[  556.359880] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  556.362222] sd 7:0:0:0: [sdc] 7567964 512-byte logical blocks: (3.87 GB/3.60 GiB)
[  556.362753] sd 7:0:0:0: [sdc] Write Protect is off
[  556.362758] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 00
[  556.363384] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  556.367696]  sdc: sdc1
[  556.369997] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  676.795897] usb 1-1.4: USB disconnect, device number 7
[  684.928338] usb 1-1.4: new high-speed USB device number 8 using ehci_hcd
[  685.024122] scsi8 : usb-storage 1-1.4:1.0
[  686.040311] scsi 8:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 4
[  686.041098] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  686.041654] sd 8:0:0:0: [sdc] 7567964 512-byte logical blocks: (3.87 GB/3.60 GiB)
[  686.042280] sd 8:0:0:0: [sdc] Write Protect is off
[  686.042285] sd 8:0:0:0: [sdc] Mode Sense: 45 00 00 00
[  686.042905] sd 8:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  686.048480]  sdc: sdc1
[  686.050775] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 1530.287299] usb 1-1.4: USB disconnect, device number 8
[ 1533.556304] usb 1-1.4: new high-speed USB device number 9 using ehci_hcd
[ 1533.653297] scsi9 : usb-storage 1-1.4:1.0
[ 1534.668459] scsi 9:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 4
[ 1534.669306] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 1534.672325] sd 9:0:0:0: [sdc] 7567964 512-byte logical blocks: (3.87 GB/3.60 GiB)
[ 1534.672807] sd 9:0:0:0: [sdc] Write Protect is off
[ 1534.672812] sd 9:0:0:0: [sdc] Mode Sense: 45 00 00 00
[ 1534.673427] sd 9:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1534.677627]  sdc: sdc1
[ 1534.679929] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 1652.729881] r8712u: wpa_set_encryption, crypt.alg = WEP
[ 2050.081437] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 6078.164096] type=1701 audit(1348933082.864:17): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=5143 comm="chrome" reason="seccomp" sig=0 syscall=20 ip=0x8af416 code=0x50001
[ 6085.106341] type=1701 audit(1348933089.804:18): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=5183 comm="chrome" reason="seccomp" sig=0 syscall=20 ip=0x5d1416 code=0x50001
[11252.764569] r8712u: wpa_set_encryption, crypt.alg = WEP
[14723.532140] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[14723.536267] SGI XFS Quota Management subsystem
[14723.584706] JFS: nTxBlock = 8192, nTxLock = 65536
[14723.626952] NTFS driver 2.1.30 [Flags: R/O MODULE].
[14723.659918] QNX4 filesystem 0.2.3 registered.
[21406.899081] usb 1-1.4: USB disconnect, device number 9
[22892.817774] r8712u: wpa_set_encryption, crypt.alg = WEP
[24760.188372] usb 1-1.2: new high-speed USB device number 10 using ehci_hcd
[24760.307169] scsi10 : usb-storage 1-1.2:1.0
[24761.380521] scsi 10:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 4
[24761.382875] sd 10:0:0:0: Attached scsi generic sg3 type 0
[24761.384000] sd 10:0:0:0: [sdc] 7567964 512-byte logical blocks: (3.87 GB/3.60 GiB)
[24761.384635] sd 10:0:0:0: [sdc] Write Protect is off
[24761.384639] sd 10:0:0:0: [sdc] Mode Sense: 45 00 00 00
[24761.385254] sd 10:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[24761.389298]  sdc: sdc1
[24761.392499] sd 10:0:0:0: [sdc] Attached SCSI removable disk

---

### Post by wgarcia on 2012-09-30
Sols es necessitaven les últimes línies dels missatges "dmesg", i en tot cas si en un futur has d'enganxar un resultat tan llarg pots fer servir:

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

i enganxar aquí únicament l'enllaç.

Ara bé, les últimes línies que hi ha al "dmesg" diuen que sí que el sistema veu el disc, perquè respon amb els missatges adequats quan es torna a endollar. Ara aniria bé veure que donen les següents comandes:

```
sudo fdisk -l
sudo mount
```

La primera mostra les particions que reconeix el sistema, i la segona mostra com estan muntades aquestes particions.

---

### Post by vallibona on 2012-09-30
Perdoneu el "totxo", no coneixia paste.ubuntu.com i he pensat que igual trobàveu alguna cosa útil a altres línies del dmesg

A [http://paste.ubuntu.com/1251541/](http://paste.ubuntu.com/1251541/) hi ha el resultat del fdisk -l i a [http://paste.ubuntu.com/1251552/](http://paste.ubuntu.com/1251552/) el resultat de mount.

Dins de la torre del PC tinc 2 discos físics (un per a dades i un per al sistema) i connectat al hub usb el receptor del mouse (que funciona), un pendrive Kingston (que veig al mount i al fdisk) i el disc dur extern WD, que no trobo.
A [http://paste.ubuntu.com/1251560/](http://paste.ubuntu.com/1251560/) teniu el resultat de lsusb

Gràcies per la vostra ajuda!

---

### Post by wgarcia on 2012-09-30
> **wgarcia said:**
> 
Ara bé, les últimes línies que hi ha al "dmesg" diuen que sí que el sistema veu el disc, perquè respon amb els missatges adequats quan es torna a endollar..

Retiro això, d'acord amb els resultats de fdisk, mount i lsusb que enganxes, el que veu el sistema és el disc Kingston, no el WD.

Pots mirar si tens "ntfs-3g" instal·lat? O sigui:

```
sudo apt-get install ntfs-3g
```

---

### Post by vallibona on 2012-09-30
Hola 
Resultat d'apt-get install ntfs-3g

S'està llegint la llista de paquets&#8230; Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet%
ntfs-3g ja es troba en la versió més recent

Salutacions,

---

### Post by vallibona on 2012-10-03
Hola!
Continuo sense trobar el disc, alguna idea?
Moltes gràcies per endavant.

Salutacions,

---

### Post by wgarcia on 2012-10-04
Jo m'he quedat sense idees, és molt estrany perquè aquestes coses ja són estàndard a Linux fa molt de temps. Però segons el que hem vist en el que has enviat, el sistema ni s'entera que s'ha endollat aquest disc.

---

### Post by wgarcia on 2012-10-06
No se m'acut res mes que provar algun nucli més recent , a veure si el problema de reconeixement del disc té a veure amb la versió de nucli particular que porta la teva instal·lació. Aquí ha ha dos opcions, una és esperar que vingui alguna actualització de nucli, una altra és provar d'instal·lar alguna versió més recent, tot i que aquesta segona opció no és senzilla i seria sota el teu compte i risc. No és massa complicat instal·lar una nova versió de nucli, is no no et permet arrencar el sistema un cop instal·lada sempre tens versions anteriors per entrar i desintal·lar el nucli que no funciona. 

Però si vols seguir aquesta segona opció es poden trobar els últims nuclis per a Ubuntu a:

[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

Per instal·lar un nucli s'han de baixar els "headers" communs, els "headers" específic per a la teva arquitectura, i la imatge específica per a la teva arquitectura. Per exemple per a  2.6.27.15 el total de fitxers serien: 

      A       linux-headers-2.6.27-02062715-generic_2.6.27-02062715_amd64.deb
      B       linux-headers-2.6.27-02062715-generic_2.6.27-02062715_i386.deb
      C       linux-headers-2.6.27-02062715_2.6.27-02062715_all.deb
      D       linux-image-2.6.27-02062715-generic_2.6.27-02062715_amd64.deb
      E       linux-image-2.6.27-02062715-generic_2.6.27-02062715_i386.deb

per a 64 bits se necessitaria baixar A, C i D. 

Per instal·lar-los s'ha d'obrir una terminal all lloc s'hagin baixat els fitxers i entrar

```
sudo dpkg -i *.deb
```
     sudo dpkg -i *.deb

Per desintal·lar-lo, es buscar el nucli instal·lat:
```
dpkg -l | grep "linux\-[a-z]*\-"

```
   
i un cop trobada la versió exacta del nucli instal·lat, 


```
 sudo apt-get remove PAQUETS_DE_NUCLI A_REMOURE
```

---

### Post by vallibona on 2012-10-22
Hola
Moltes gràcies per la teua ajuda. 
Pel que fa a instal·lar un nou nucli... no sé si me'n sortiré, i tinc por de no fer malbé alguna altra cosa que funcionava...

El cas és que al portàtil amb Kubuntu 9.10 amb nucli  2.6.32.28 funciona perfectament....

Salutacions,

---

### Post by wgarcia on 2012-10-22
De totes maneres és estrany, a veure si amb alguna actualització de nucli torna a funcionar.

---

### Post by kimet on 2012-10-22
Segons el que adjuntes si es veu un disc ntfs de 500gb muntat a /media/sda1-dades.
No pots accedir-hi?

SaLut.

---

### Post by wgarcia on 2012-10-23
Hi ha dos discos, el que es veu em sembla que no és el que presenta problemes.

---

