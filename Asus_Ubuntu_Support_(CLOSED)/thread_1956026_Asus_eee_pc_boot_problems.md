---
title: "Asus eee pc boot problems"
date: 2012-04-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by loganrah on 2012-04-10
I've been having problems with booting my Asus eee pc recently. Grub loads fine and gives me the right options (linux install, memtest, windows 7 (separate partition) and windows 7 recovery). But then when booting into lubuntu (11.10) the boot seems to freaze up with a blinking curser in the top left corner of the screen. 
This happens on most boots, every now and then it will fully boot into lubuntu, sometimes with the keyboard and touch pad working, sometimes not. I was able to boot from a usb and format the lubuntu partition and re-install today, which seems to have made the problem less likely but not go away completely (it still frezes up on some boots but is doing better). 

EDIT: I've now upgraded to 12.04 and am having the same problem. Its an Asus eee pc 1015px and I've installed the latest firmware. Below I've posted /var/log/dmesg up to the point it usually freezes (this is copied from a boot where it worked, I can't see how to get the logs from a boot that fails and requires hard reset).

---

### Post by 2F4U on 2012-04-10
There is not much info to work with at the moment. You could remove the quiet splash from the grub kernel parameters, so that you will see the kernel messages during boot. When it freezes, there is a chance to see where it happens.

---

### Post by loganrah on 2012-04-10
Couldn't work out how t do spoiler tags sorry.

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f680000 (usable)
[    0.000000]  BIOS-e820: 000000007f680000 - 000000007f68e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f68e000 - 000000007f6d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: ASUSTeK Computer INC. 1015PX/1015PE, BIOS 1401    08/30/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f680 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36506000 - 3727b000
[    0.000000] ACPI: RSDP 000fbe90 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7f680100 0006C (v01 _ASUS_ Notebook 08001130 MSFT 00000097)
[    0.000000] ACPI: FACP 7f680290 000F4 (v04 A_M_I_ OEMFACP  08001130 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f6804a0 085B1 (v02  A1563 A1563000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7f68e000 00040
[    0.000000] ACPI: APIC 7f680390 0006C (v02 A_M_I_ OEMAPIC  08001130 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f680400 0003C (v01 A_M_I_ OEMMCFG  08001130 MSFT 00000097)
[    0.000000] ACPI: ECDT 7f680440 00055 (v01 A_M_I_ OEMECDT  08001130 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f68e040 00061 (v01 A_M_I_ AMI_OEM  08001130 MSFT 00000097)
[    0.000000] ACPI: HPET 7f688a60 00038 (v01 A_M_I_ OEMHPET  08001130 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f68e0b0 02024 (v01 A_M_I_ GMCHSCI  08001130 MSFT 00000097)
[    0.000000] ACPI: SSDT 7f691360 00999 (v01  PmRef   CpuPm4 00003000 INTL 20051117)
[    0.000000] ACPI: SLIC 7f688aa0 00176 (v01 _ASUS_ Notebook 08001130 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f680
[    0.000000] On node 0 totalpages: 521743
[    0.000000] free_area_init_node: node 0, pgdat c1827880, node_mem_map f5516200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292228 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s31616 r0 d21632 u1048576
[    0.000000] pcpu-alloc: s31616 r0 d21632 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517665
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=7b1fad0d-0ff4-4358-8c15-2972acbde0c7 ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8349440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f680)
[    0.000000] Memory: 2037620k/2087424k available (5628k kernel code, 49352k reserved, 2771k data, 712k init, 1178120k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1835000 - 0xc18e7000   ( 712 kB)
[    0.000000]       .data : 0xc157f204 - 0xc1834040   (2771 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157f204   (5628 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f440a000 soft=f440c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1666.412 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3332.82 BogoMIPS (lpj=6665648)
[    0.004151] pid_max: default: 32768 minimum: 301
[    0.004268] Security Framework initialized
[    0.004371] AppArmor: AppArmor initialized
[    0.004439] Yama: becoming mindful.
[    0.004624] Mount-cache hash table entries: 512
[    0.004966] Initializing cgroup subsys cpuacct
[    0.005048] Initializing cgroup subsys memory
[    0.005131] Initializing cgroup subsys devices
[    0.005201] Initializing cgroup subsys freezer
[    0.005272] Initializing cgroup subsys blkio
[    0.005352] Initializing cgroup subsys perf_event
[    0.005468] CPU: Physical Processor ID: 0
[    0.005536] CPU: Processor Core ID: 0
[    0.005605] mce: CPU supports 5 MCE banks
[    0.005681] CPU0: Thermal monitoring enabled (TM2)
[    0.005755] using mwait in idle threads.
[    0.010641] ACPI: Core revision 20110623
[    0.024027] ftrace: allocating 25955 entries in 51 pages
[    0.028098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028654] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069336] CPU0: Intel(R) Atom(TM) CPU N570   @ 1.66GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f4512000 soft=f4514000
[    0.072003] Booting Node   0, Processors  #1
[    0.072003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.164009] TSC synchronization [CPU#0 -> CPU#1]:
[    0.164009] Measured 200 cycles TSC warp between CPUs, turning off TSC clock.
[    0.164009] Marking TSC unstable due to check_tsc_sync_source failed
[    0.164063] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164352] CPU 2 irqstacks, hard=f4520000 soft=f4522000
[    0.164358]  #2
[    0.164393] smpboot cpu 2: start_ip = 9b000
[    0.008000] Initializing CPU#2
[    0.008000] Disabled fast string operations
[    0.252178] NMI watchdog enabled, takes one hw-pmu counter.
[    0.252625] CPU 3 irqstacks, hard=f452e000 soft=f4538000
[    0.252631]  #3 Ok.
[    0.252691] smpboot cpu 3: start_ip = 9b000
[    0.008000] Initializing CPU#3
[    0.008000] Disabled fast string operations
[    0.340196] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340443] Brought up 4 CPUs
[    0.340512] Total of 4 processors activated (13331.68 BogoMIPS).
[    0.343034] devtmpfs: initialized
[    0.343034] EVM: security.selinux
[    0.343034] EVM: security.SMACK64
[    0.343034] EVM: security.capability
[    0.343034] PM: Registering ACPI NVS region at 7f68e000 (270336 bytes)
[    0.347050] print_constraints: dummy: 
[    0.347166] RTC time: 12:39:53, date: 06/13/12
[    0.347319] NET: Registered protocol family 16
[    0.347409] Trying to unpack rootfs image as initramfs...
[    0.347775] EISA bus registered
[    0.347865] ACPI: bus type pci registered
[    0.348158] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348281] PCI: not using MMCONFIG
[    0.348618] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.348701] PCI: Using configuration type 1 for base access
[    0.352813] bio: create slab <bio-0> at 0
[    0.352813] ACPI: Added _OSI(Module Device)
[    0.352813] ACPI: Added _OSI(Processor Device)
[    0.352813] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.352813] ACPI: Added _OSI(Processor Aggregator Device)
[    0.358424] ACPI: EC: EC description table is found, configuring boot EC
[    0.363812] ACPI: Executed 1 blocks of module-level executable AML code
[    0.373136] ACPI: SSDT 7f690740 0033A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.374631] ACPI: Dynamic OEM Table Load:
[    0.375714] ACPI: SSDT   (null) 0033A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.376619] ACPI: SSDT 7f690c30 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.377966] ACPI: Dynamic OEM Table Load:
[    0.378097] ACPI: SSDT   (null) 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.379101] ACPI: SSDT 7f690520 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.380660] ACPI: Dynamic OEM Table Load:
[    0.380794] ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.381292] ACPI: SSDT 7f690ba0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.382645] ACPI: Dynamic OEM Table Load:
[    0.382775] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.383802] ACPI: SSDT 7f690300 00217 (v01  PmRef  Cpu2Ist 00003000 INTL 20051117)
[    0.385329] ACPI: Dynamic OEM Table Load:
[    0.385477] ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu2Ist 00003000 INTL 20051117)
[    0.385976] ACPI: SSDT 7f690b10 00085 (v01  PmRef  Cpu2Cst 00003000 INTL 20051117)
[    0.387345] ACPI: Dynamic OEM Table Load:
[    0.387476] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu2Cst 00003000 INTL 20051117)
[    0.388535] ACPI: SSDT 7f6900e0 00217 (v01  PmRef  Cpu3Ist 00003000 INTL 20051117)
[    0.390056] ACPI: Dynamic OEM Table Load:
[    0.390189] ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu3Ist 00003000 INTL 20051117)
[    0.390713] ACPI: SSDT 7f690a80 00085 (v01  PmRef  Cpu3Cst 00003000 INTL 20051117)
[    0.392123] ACPI: Dynamic OEM Table Load:
[    0.392260] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu3Cst 00003000 INTL 20051117)
[    0.393065] ACPI: Interpreter enabled
[    0.393156] ACPI: (supports S0 S3 S4 S5)
[    0.393402] ACPI: Using IOAPIC for interrupt routing
[    0.393565] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.395359] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.395480] PCI: Using MMCONFIG for extended config space
[    0.410070] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.413769] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.414444] ACPI: No dock devices found.
[    0.414519] HEST: Table not found.
[    0.414596] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.414991] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.415589] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.415679] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.415764] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.415875] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.415986] pci_root PNP0A08:00: host bridge window [mem 0x7f700000-0xfed8ffff]
[    0.416089] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.416170] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.416193] pci 0000:00:02.0: reg 10: [mem 0xf7e00000-0xf7e7ffff]
[    0.416208] pci 0000:00:02.0: reg 14: [io  0xdc00-0xdc07]
[    0.416223] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.416237] pci 0000:00:02.0: reg 1c: [mem 0xf7d00000-0xf7dfffff]
[    0.416308] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.416330] pci 0000:00:02.1: reg 10: [mem 0xf7e80000-0xf7efffff]
[    0.416483] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.416520] pci 0000:00:1b.0: reg 10: [mem 0xf7cf8000-0xf7cfbfff 64bit]
[    0.416656] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.416669] pci 0000:00:1b.0: PME# disabled
[    0.416716] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.416860] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.416872] pci 0000:00:1c.0: PME# disabled
[    0.416922] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.417065] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.417077] pci 0000:00:1c.1: PME# disabled
[    0.417131] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.417280] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.417292] pci 0000:00:1c.3: PME# disabled
[    0.417344] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.417419] pci 0000:00:1d.0: reg 20: [io  0xd400-0xd41f]
[    0.417484] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.417559] pci 0000:00:1d.1: reg 20: [io  0xd480-0xd49f]
[    0.417624] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.417700] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.417770] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.417846] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.417928] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.417965] pci 0000:00:1d.7: reg 10: [mem 0xf7cf7c00-0xf7cf7fff]
[    0.418107] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.418119] pci 0000:00:1d.7: PME# disabled
[    0.418158] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.418296] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.418491] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.418532] pci 0000:00:1f.2: reg 10: [io  0xd080-0xd087]
[    0.418554] pci 0000:00:1f.2: reg 14: [io  0xd000-0xd003]
[    0.418575] pci 0000:00:1f.2: reg 18: [io  0xcc00-0xcc07]
[    0.418595] pci 0000:00:1f.2: reg 1c: [io  0xc880-0xc883]
[    0.418616] pci 0000:00:1f.2: reg 20: [io  0xc800-0xc81f]
[    0.418637] pci 0000:00:1f.2: reg 24: [mem 0xf7cf7800-0xf7cf7bff]
[    0.418727] pci 0000:00:1f.2: PME# supported from D3hot
[    0.418739] pci 0000:00:1f.2: PME# disabled
[    0.418850] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.419095] pci 0000:02:00.0: [14e4:4727] type 0 class 0x000280
[    0.419142] pci 0000:02:00.0: reg 10: [mem 0xfbffc000-0xfbffffff 64bit]
[    0.419353] pci 0000:02:00.0: supports D1 D2
[    0.419362] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.419375] pci 0000:02:00.0: PME# disabled
[    0.424127] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.424226] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.424244] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.424381] pci 0000:01:00.0: [1969:2062] type 0 class 0x000200
[    0.424430] pci 0000:01:00.0: reg 10: [mem 0xf7fc0000-0xf7ffffff 64bit]
[    0.424456] pci 0000:01:00.0: reg 18: [io  0xec00-0xec7f]
[    0.424637] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.424652] pci 0000:01:00.0: PME# disabled
[    0.432098] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.432194] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.432208] pci 0000:00:1c.3:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    0.432336] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.432440] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.432450] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.432460] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.432470] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.432481] pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xfed8ffff] (subtractive decode)
[    0.432524] pci_bus 0000:00: on NUMA node 0
[    0.432539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.432942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.433074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.433158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.433241]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.433329]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.433443] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.452449] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.453045] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.453625] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.454196] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.454774] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.455435] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.456057] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.456650] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.457352] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.457352] vgaarb: loaded
[    0.457352] vgaarb: bridge control possible 0000:00:02.0
[    0.457352] i2c-core: driver [aat2870] using legacy suspend method
[    0.457352] i2c-core: driver [aat2870] using legacy resume method
[    0.457352] SCSI subsystem initialized
[    0.457421] libata version 3.00 loaded.
[    0.457586] usbcore: registered new interface driver usbfs
[    0.457715] usbcore: registered new interface driver hub
[    0.457885] usbcore: registered new device driver usb
[    0.458284] PCI: Using ACPI for IRQ routing
[    0.458469] PCI: pci_cache_line_size set to 64 bytes
[    0.458611] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.460050] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.460060] reserve RAM buffer: 000000007f680000 - 000000007fffffff 
[    0.460382] NetLabel: Initializing
[    0.460463] NetLabel:  domain hash size = 128
[    0.460540] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.460641] NetLabel:  unlabeled traffic allowed by default
[    0.460790] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.460790] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.460790] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.472215] Switching to clocksource hpet
[    0.495068] AppArmor: AppArmor Filesystem Enabled
[    0.495216] pnp: PnP ACPI init
[    0.495329] ACPI: bus type pnp registered
[    0.495679] pnp 00:00: [bus 00-ff]
[    0.495689] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.495698] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.495706] pnp 00:00: [io  0x0d00-0xffff window]
[    0.495715] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.495724] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.495732] pnp 00:00: [mem 0x7f700000-0xfed8ffff window]
[    0.495909] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.495946] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.495955] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.496140] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.496232] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.496330] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.496455] pnp 00:02: [dma 4]
[    0.496464] pnp 00:02: [io  0x0000-0x000f]
[    0.496472] pnp 00:02: [io  0x0081-0x0083]
[    0.496479] pnp 00:02: [io  0x0087]
[    0.496486] pnp 00:02: [io  0x0089-0x008b]
[    0.496494] pnp 00:02: [io  0x008f]
[    0.496501] pnp 00:02: [io  0x00c0-0x00df]
[    0.496614] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.496656] pnp 00:03: [io  0x0070-0x0071]
[    0.496678] pnp 00:03: [irq 8]
[    0.496770] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.496875] pnp 00:04: [io  0x0060]
[    0.496884] pnp 00:04: [io  0x0064]
[    0.496899] pnp 00:04: [irq 1]
[    0.496998] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.497106] pnp 00:05: [irq 12]
[    0.497201] pnp 00:05: Plug and Play ACPI device, IDs SYN0a13 SYN0a00 SYN0002 PNP0f13 (active)
[    0.497236] pnp 00:06: [io  0x0061]
[    0.497330] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.497365] pnp 00:07: [io  0x00f0-0x00ff]
[    0.497382] pnp 00:07: [irq 13]
[    0.497472] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.497896] pnp 00:08: [io  0x0010-0x001f]
[    0.497906] pnp 00:08: [io  0x0022-0x003f]
[    0.497913] pnp 00:08: [io  0x0044-0x004d]
[    0.497921] pnp 00:08: [io  0x0050-0x005e]
[    0.497928] pnp 00:08: [io  0x0063]
[    0.497935] pnp 00:08: [io  0x0065]
[    0.497942] pnp 00:08: [io  0x0067-0x006f]
[    0.497949] pnp 00:08: [io  0x0072-0x007f]
[    0.497956] pnp 00:08: [io  0x0080]
[    0.497963] pnp 00:08: [io  0x0084-0x0086]
[    0.497970] pnp 00:08: [io  0x0088]
[    0.497977] pnp 00:08: [io  0x008c-0x008e]
[    0.497984] pnp 00:08: [io  0x0090-0x009f]
[    0.497992] pnp 00:08: [io  0x00a2-0x00bf]
[    0.497999] pnp 00:08: [io  0x00e0-0x00ef]
[    0.498007] pnp 00:08: [io  0x025c-0x025f]
[    0.498014] pnp 00:08: [io  0x0380-0x0383]
[    0.498021] pnp 00:08: [io  0x0400-0x041f]
[    0.498029] pnp 00:08: [io  0x04d0-0x04d1]
[    0.498036] pnp 00:08: [io  0x0800-0x087f]
[    0.498044] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.498057] pnp 00:08: [io  0x0480-0x04bf]
[    0.498065] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.498073] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.498081] pnp 00:08: [mem 0xfed50000-0xfed8ffff]
[    0.498089] pnp 00:08: [mem 0xffb00000-0xffbfffff]
[    0.498097] pnp 00:08: [mem 0xfff00000-0xffffffff]
[    0.498297] system 00:08: [io  0x025c-0x025f] has been reserved
[    0.498387] system 00:08: [io  0x0380-0x0383] has been reserved
[    0.498480] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.498564] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.498647] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.498730] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.498814] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.498899] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.498985] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.499070] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.499162] system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
[    0.499255] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.499475] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.499603] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.499772] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.499782] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.499920] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.500048] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.500149] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.500283] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.500445] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.500536] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.501247] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.501258] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.501266] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.501274] pnp 00:0c: [mem 0x00100000-0x7f6fffff]
[    0.501282] pnp 00:0c: [mem 0xfed90000-0xffffffff]
[    0.501478] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.501573] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.501671] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.501760] system 00:0c: [mem 0x00100000-0x7f6fffff] could not be reserved
[    0.501848] system 00:0c: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.501937] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.502514] pnp: PnP ACPI: found 13 devices
[    0.502596] ACPI: ACPI bus type pnp unregistered
[    0.502681] PnPBIOS: Disabled by ACPI PNP
[    0.545991] PCI: max bus depth: 1 pci_try_num: 2
[    0.546084] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.546219] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.546313] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.546405] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.546521] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.546606] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.546686] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.546778] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff]
[    0.546875] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.547006] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.547088] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.547178] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.547268] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.547388] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.547469] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.547555] pci 0000:00:1c.3:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    0.547646] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.547774] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.547886] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.547998] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.548120] pci 0000:00:1c.0: setting latency timer to 64
[    0.548139] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.548239] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.548329] pci 0000:00:1c.1: setting latency timer to 64
[    0.548360] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.548449] pci 0000:00:1c.3: setting latency timer to 64
[    0.548468] pci 0000:00:1e.0: setting latency timer to 64
[    0.548480] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.548489] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.548499] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.548508] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.548518] pci_bus 0000:00: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.548527] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.548536] pci_bus 0000:04: resource 1 [mem 0x80200000-0x803fffff]
[    0.548547] pci_bus 0000:04: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.548558] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.548567] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.548577] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.548586] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.548595] pci_bus 0000:01: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    0.548604] pci_bus 0000:01: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.548614] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.548623] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.548632] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.548641] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.548650] pci_bus 0000:05: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.548763] NET: Registered protocol family 2
[    0.549039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.549784] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.550952] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.551567] TCP: Hash tables configured (established 131072 bind 65536)
[    0.551679] TCP reno registered
[    0.551776] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.551892] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.552243] NET: Registered protocol family 1
[    0.552362] pci 0000:00:02.0: Boot video device
[    0.552434] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.552543] pci 0000:00:1d.0: PCI INT A disabled
[    0.552648] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.552765] pci 0000:00:1d.1: PCI INT B disabled
[    0.552874] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.552979] pci 0000:00:1d.2: PCI INT C disabled
[    0.553068] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.553171] pci 0000:00:1d.3: PCI INT D disabled
[    0.553263] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.553392] pci 0000:00:1d.7: PCI INT A disabled
[    0.553540] PCI: CLS 32 bytes, default 64
[    0.554991] audit: initializing netlink socket (disabled)
[    0.555094] type=2000 audit(1339591192.548:1): initialized
[    0.617557] highmem bounce pool size: 64 pages
[    0.617648] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.633740] VFS: Disk quotas dquot_6.5.2
[    0.634017] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.636065] fuse init (API version 7.17)
[    0.636500] msgmni has been set to 1678
[    0.638825] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.639034] io scheduler noop registered
[    0.639109] io scheduler deadline registered
[    0.639201] io scheduler cfq registered (default)
[    0.639614] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.639709] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.639868] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.639952] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.640138] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.640228] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.640464] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640628] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640912] intel_idle: MWAIT substates: 0x20220
[    0.640938] intel_idle: v0.4 model 0x1C
[    0.640944] intel_idle: lapic_timer_reliable_states 0x2
[    0.641152] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.641425] ACPI: AC Adapter [AC0] (on-line)
[    0.641847] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.646856] ACPI: Lid Switch [LID]
[    0.647116] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.647238] ACPI: Sleep Button [SLPB]
[    0.647459] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.647578] ACPI: Power Button [PWRB]
[    0.647805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.647920] ACPI: Power Button [PWRF]
[    0.665934] thermal LNXTHERM:00: registered as thermal_zone0
[    0.666015] ACPI: Thermal Zone [TZ00] (68 C)
[    0.666140] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.666272] ACPI: Battery Slot [BAT0] (battery present)
[    0.666474] ERST: Table is not found!
[    0.666548] GHES: HEST is not enabled!
[    0.666803] isapnp: Scanning for PnP cards...
[    0.666885] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.767885] ACPI: Battery Slot [BAT0] (battery present)
[    1.020894] isapnp: No Plug & Play device found
[    1.043595] Freeing initrd memory: 13780k freed
[    1.260855] Linux agpgart interface v0.103
[    1.261101] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.261343] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.261815] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.262172] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.266511] brd: module loaded
[    1.268834] loop: module loaded
[    1.269196] ahci 0000:00:1f.2: version 3.0
[    1.269243] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.269401] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.269505] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.269615] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.269696] ahci 0000:00:1f.2: setting latency timer to 64
[    1.270921] scsi0 : ahci
[    1.271223] scsi1 : ahci
[    1.271489] scsi2 : ahci
[    1.271753] scsi3 : ahci
[    1.272336] ata1: SATA max UDMA/133 abar m1024@0xf7cf7800 port 0xf7cf7900 irq 43
[    1.272441] ata2: DUMMY
[    1.272500] ata3: DUMMY
[    1.272559] ata4: DUMMY
[    1.273862] Fixed MDIO Bus: probed
[    1.273987] tun: Universal TUN/TAP device driver, 1.6
[    1.274057] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.274301] PPP generic driver version 2.4.2
[    1.274661] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.274780] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.274890] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.274898] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.275093] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.275228] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.275317] ehci_hcd 0000:00:1d.7: debug port 1
[    1.279273] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.279314] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7cf7c00
[    1.292036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.292436] hub 1-0:1.0: USB hub found
[    1.292511] hub 1-0:1.0: 8 ports detected
[    1.292753] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.292862] uhci_hcd: USB Universal Host Controller Interface driver
[    1.292986] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.293077] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.293084] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.293300] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.293442] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.293849] hub 2-0:1.0: USB hub found
[    1.293922] hub 2-0:1.0: 2 ports detected
[    1.294128] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.294220] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.294227] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.294425] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.294584] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.294987] hub 3-0:1.0: USB hub found
[    1.295060] hub 3-0:1.0: 2 ports detected
[    1.295265] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.295357] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.295364] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.295563] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.295719] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.296163] hub 4-0:1.0: USB hub found
[    1.296237] hub 4-0:1.0: 2 ports detected

---

