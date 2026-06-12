---
title: "Window freezes (hardware issue)"
date: 2011-08-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by M4r5h4ll on 2011-08-22
Hello,

i have a A42F Asus laptop i just bought & i installed Ubuntu 11.04 on it
i noticed sometimes window freezes & i can't move them... i wait for few mins then i can move them or i have to kill x then start it again to sort it.

i tried metacity & openbox & compiz still the same.

i checked logs didn't find anything werid. also i checked all drivers found none needs updates & my vga is working directly from the kernel.

i even did update to kernel 3 & still the same issue. so i donno what to do.
hope someone here can help me out.


Thank u guys.
---------- all info ---------------

Linux C0r3 3.0.3-030003-generic #201108180913 SMP Thu Aug 18 10:51:58 UTC 2011 i686 i686 i386 GNU/Linux


marshall@C0r3:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.3-030003-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201108180913 SMP Thu Aug 18 10:51:58 UTC 2011
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000076e07000 (usable)
[    0.000000]  BIOS-e820: 0000000076e07000 - 0000000076e8c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076e8c000 - 0000000076e8e000 (reserved)
[    0.000000]  BIOS-e820: 0000000076e8e000 - 0000000076e91000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076e91000 - 0000000076ea2000 (reserved)
[    0.000000]  BIOS-e820: 0000000076ea2000 - 0000000076eb5000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076eb5000 - 0000000076edc000 (reserved)
[    0.000000]  BIOS-e820: 0000000076edc000 - 0000000076eed000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076eed000 - 0000000076ef0000 (reserved)
[    0.000000]  BIOS-e820: 0000000076ef0000 - 0000000076ef1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076ef1000 - 0000000076f07000 (reserved)
[    0.000000]  BIOS-e820: 0000000076f07000 - 0000000076f08000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076f08000 - 0000000076f0c000 (reserved)
[    0.000000]  BIOS-e820: 0000000076f0c000 - 0000000076f0f000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000076f0f000 - 0000000076f14000 (reserved)
[    0.000000]  BIOS-e820: 0000000076f14000 - 0000000076f23000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000076f23000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 0000000079e00000 - 000000007c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
     0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc. K42F/K42F, BIOS 422 12/08/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x76e07 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 078000000 mask FF8000000 uncachable
[    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00fcaa0] fcaa0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0097000] 97000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36e08000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 35c20000 - 36e071c1
[    0.000000] Move RAMDISK from 0000000036e08000 - 0000000037fef1c0 to 35c20000 - 36e071c0
[    0.000000] ACPI: RSDP 000f0410 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 76f0de18 0005C (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 76ef0c18 000F4 (v04 _ASUS_   _ASUS_ 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0x76F1FF40/0x0000000076F22D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 76eaa018 0AF38 (v01 _ASUS_   _ASUS_ 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 76f1ff40 00040
[    0.000000] ACPI: APIC 76f0cf18 0008C (v02 _ASUS_   _ASUS_ 06222004 MSFT 00010013)
[    0.000000] ACPI: MCFG 76f21d18 0003C (v01 _ASUS_   _ASUS_ 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET 76f21c98 00038 (v01 _ASUS_   _ASUS_ 06222004 AMI. 00000003)
[    0.000000] ACPI: ECDT 76f22b18 000C1 (v01 _ASUS_   _ASUS_ 06222004 AMI  00000000)
[    0.000000] ACPI: SLIC 76f1aa18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
[    0.000000] ACPI: SSDT 76f07018 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1014MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00076e07
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x00076e07
[    0.000000] On node 0 totalpages: 486802
[    0.000000] free_area_init_node: node 0, pgdat c17bc800, node_mem_map f4d40200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2029 pages used for memmap
[    0.000000]   HighMem zone: 257564 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7c000000 (gap: 7c000000:7c000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f7000000 s26176 r0 d22976 u524288
[    0.000000] pcpu-alloc: s26176 r0 d22976 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 482997
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.3-030003-generic root=UUID=8da182f0-1906-4664-a0ae-f240c53fdbf2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7790448 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00076e07)
[    0.000000] Memory: 1895180k/1947676k available (5329k kernel code, 52028k reserved, 2629k data, 748k init, 1038372k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c6000 - 0xc1881000   ( 748 kB)
[    0.000000]       .data : 0xc153462f - 0xc17c5a80   (2629 kB)
[    0.000000]       .text : 0xc1000000 - 0xc153462f   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f400a000 soft=f400c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2260.613 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.22 BogoMIPS (lpj=9042452)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000032] Security Framework initialized
[    0.000050] AppArmor: AppArmor initialized
[    0.000097] Mount-cache hash table entries: 512
[    0.000235] Initializing cgroup subsys cpuacct
[    0.000241] Initializing cgroup subsys memory
[    0.000249] Initializing cgroup subsys devices
[    0.000251] Initializing cgroup subsys freezer
[    0.000253] Initializing cgroup subsys net_cls
[    0.000255] Initializing cgroup subsys blkio
[    0.000261] Initializing cgroup subsys perf_event
[    0.000290] CPU: Physical Processor ID: 0
[    0.000292] CPU: Processor Core ID: 0
[    0.000298] mce: CPU supports 9 MCE banks
[    0.000309] CPU0: Thermal monitoring enabled (TM1)
[    0.000318] using mwait in idle threads.
[    0.002782] ACPI: Core revision 20110413
[    0.010823] ftrace: allocating 28069 entries in 55 pages
[    0.020397] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020712] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.060311] CPU0: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz stepping 02
[    0.166904] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.166912] ... version:                3
[    0.166913] ... bit width:              48
[    0.166915] ... generic registers:      4
[    0.166916] ... value mask:             0000ffffffffffff
[    0.166918] ... max period:             000000007fffffff
[    0.166919] ... fixed-purpose events:   3
[    0.166921] ... event mask:             000000070000000f
[    0.167097] CPU 1 irqstacks, hard=f40ce000 soft=f40d8000
[    0.167099] Booting Node   0, Processors  #1
[    0.167102] smpboot cpu 1: start_ip = 97000
[    0.177386] Initializing CPU#1
[    0.274918] CPU 2 irqstacks, hard=f40e2000 soft=f40e4000
[    0.274920]  #2
[    0.274922] smpboot cpu 2: start_ip = 97000
[    0.285052] Initializing CPU#2
[    0.382641] CPU 3 irqstacks, hard=f410e000 soft=f4110000
[    0.382644]  #3
[    0.382645] smpboot cpu 3: start_ip = 97000
[    0.392776] Initializing CPU#3
[    0.490371] Brought up 4 CPUs
[    0.490374] Total of 4 processors activated (18086.94 BogoMIPS).
[    0.493440] devtmpfs: initialized
[    0.493594] PM: Registering ACPI NVS region at 76e07000 (544768 bytes)
[    0.493609] PM: Registering ACPI NVS region at 76e8e000 (12288 bytes)
[    0.493611] PM: Registering ACPI NVS region at 76ea2000 (77824 bytes)
[    0.493614] PM: Registering ACPI NVS region at 76edc000 (69632 bytes)
[    0.493617] PM: Registering ACPI NVS region at 76ef0000 (4096 bytes)
[    0.493619] PM: Registering ACPI NVS region at 76f07000 (4096 bytes)
[    0.493621] PM: Registering ACPI NVS region at 76f14000 (61440 bytes)
[    0.494588] print_constraints: dummy: 
[    0.494617] Time:  3:57:32  Date: 08/22/11
[    0.494656] NET: Registered protocol family 16
[    0.494752] EISA bus registered
[    0.494759] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.494762] ACPI: bus type pci registered
[    0.494831] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.494835] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.494837] PCI: Using MMCONFIG for extended config space
[    0.494838] PCI: Using configuration type 1 for base access
[    0.495665] bio: create slab <bio-0> at 0
[    0.497826] ACPI: EC: EC description table is found, configuring boot EC
[    0.497832] ACPI: EC: Look up EC in DSDT
[    0.500072] ACPI: Executed 1 blocks of module-level executable AML code
[    0.514256] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.514697] ACPI: SSDT 76f0b918 003FB (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.515208] ACPI: Dynamic OEM Table Load:
[    0.515211] ACPI: SSDT   (null) 003FB (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.515342] ACPI: SSDT 76f09618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.515837] ACPI: Dynamic OEM Table Load:
[    0.515840] ACPI: SSDT   (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.538475] ACPI: SSDT 76f0aa98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.539045] ACPI: Dynamic OEM Table Load:
[    0.539048] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.550297] ACPI: SSDT 76f08d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.550825] ACPI: Dynamic OEM Table Load:
[    0.550828] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.562769] ACPI: Interpreter enabled
[    0.562777] ACPI: (supports S0 S3 S4 S5)
[    0.562800] ACPI: Using IOAPIC for interrupt routing
[    0.569768] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.569968] ACPI: No dock devices found.
[    0.569970] HEST: Table not found.
[    0.569973] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.570349] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.570983] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.570986] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.570989] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.570992] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.570994] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.570996] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.570999] pci_root PNP0A08:00: host bridge window [mem 0x7c000000-0xfeafffff]
[    0.571012] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.571033] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.571052] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
[    0.571081] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.571084] pci 0000:00:01.0: PME# disabled
[    0.571097] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.571110] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.571117] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.571123] pci 0000:00:02.0: reg 20: [io  0xe080-0xe087]
[    0.571186] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.571218] pci 0000:00:16.0: reg 10: [mem 0xf7c0a000-0xf7c0a00f 64bit]
[    0.571301] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.571306] pci 0000:00:16.0: PME# disabled
[    0.571347] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.571374] pci 0000:00:1a.0: reg 10: [mem 0xf7c08000-0xf7c083ff]
[    0.571466] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.571471] pci 0000:00:1a.0: PME# disabled
[    0.571501] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.571523] pci 0000:00:1b.0: reg 10: [mem 0xf7c00000-0xf7c03fff 64bit]
[    0.571603] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.571608] pci 0000:00:1b.0: PME# disabled
[    0.571636] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.571717] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.571722] pci 0000:00:1c.0: PME# disabled
[    0.571750] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.571831] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.571836] pci 0000:00:1c.1: PME# disabled
[    0.571865] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.571946] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.571951] pci 0000:00:1c.2: PME# disabled
[    0.571980] pci 0000:00:1c.3: [8086:3b48] type 1 class 0x000604
[    0.572064] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.572068] pci 0000:00:1c.3: PME# disabled
[    0.572095] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.572178] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.572183] pci 0000:00:1c.4: PME# disabled
[    0.572212] pci 0000:00:1c.5: [8086:3b4c] type 1 class 0x000604
[    0.572295] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.572300] pci 0000:00:1c.5: PME# disabled
[    0.572336] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.572363] pci 0000:00:1d.0: reg 10: [mem 0xf7c07000-0xf7c073ff]
[    0.572453] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.572458] pci 0000:00:1d.0: PME# disabled
[    0.572483] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.572563] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    0.572688] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    0.572715] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    0.572727] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    0.572738] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    0.572750] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    0.572762] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.572774] pci 0000:00:1f.2: reg 24: [mem 0xf7c06000-0xf7c067ff]
[    0.572824] pci 0000:00:1f.2: PME# supported from D3hot
[    0.572829] pci 0000:00:1f.2: PME# disabled
[    0.572852] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.572874] pci 0000:00:1f.3: reg 10: [mem 0xf7c05000-0xf7c050ff 64bit]
[    0.572905] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.572953] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.572982] pci 0000:00:1f.6: reg 10: [mem 0xf7c04000-0xf7c04fff 64bit]
[    0.573091] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.573094] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.573097] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.573102] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573159] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.573164] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.573170] pci 0000:00:1c.0:   bridge window [mem 0xf6800000-0xf7bfffff]
[    0.573178] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573262] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.573293] pci 0000:03:00.0: reg 10: [mem 0xf5400000-0xf540ffff 64bit]
[    0.573407] pci 0000:03:00.0: supports D1
[    0.573409] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.573416] pci 0000:03:00.0: PME# disabled
[    0.573464] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.573469] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.573474] pci 0000:00:1c.1:   bridge window [mem 0xf5400000-0xf67fffff]
[    0.573482] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573540] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.573545] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.573551] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf53fffff]
[    0.573559] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573616] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.573621] pci 0000:00:1c.3:   bridge window [io  0xa000-0xafff]
[    0.573626] pci 0000:00:1c.3:   bridge window [mem 0xf2c00000-0xf3ffffff]
[    0.573634] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573692] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.573697] pci 0000:00:1c.4:   bridge window [io  0x9000-0x9fff]
[    0.573702] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf2bfffff]
[    0.573710] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.573788] pci 0000:07:00.0: [197b:2382] type 0 class 0x000880
[    0.573812] pci 0000:07:00.0: reg 10: [mem 0xf0405000-0xf04050ff]
[    0.573992] pci 0000:07:00.2: [197b:2381] type 0 class 0x000805
[    0.574017] pci 0000:07:00.2: reg 10: [mem 0xf0404000-0xf04040ff]
[    0.574204] pci 0000:07:00.5: [197b:0250] type 0 class 0x000200
[    0.574230] pci 0000:07:00.5: reg 10: [mem 0xf0400000-0xf0403fff]
[    0.574263] pci 0000:07:00.5: reg 18: [io  0x8100-0x817f]
[    0.574281] pci 0000:07:00.5: reg 1c: [io  0x8000-0x80ff]
[    0.574376] pci 0000:07:00.5: PME# supported from D0 D3hot D3cold
[    0.574383] pci 0000:07:00.5: PME# disabled
[    0.574432] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.574437] pci 0000:00:1c.5:   bridge window [io  0x8000-0x8fff]
[    0.574441] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf17fffff]
[    0.574449] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.574526] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.574532] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.574537] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.574545] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.574548] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.574550] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.574553] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.574555] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.574558] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.574561] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.574563] pci 0000:00:1e.0:   bridge window [mem 0x7c000000-0xfeafffff] (subtractive decode)
[    0.574607] pci_bus 0000:00: on NUMA node 0
[    0.574610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.574846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.574978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.575038] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.575100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.575160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.575220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.575284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.575343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGR._PRT]
[    0.575451]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.575454]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.575456] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.582746] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    0.582811] pci 0000:3f:00.0: [8086:2c62] type 0 class 0x000600
[    0.582832] pci 0000:3f:00.1: [8086:2d01] type 0 class 0x000600
[    0.582854] pci 0000:3f:02.0: [8086:2d10] type 0 class 0x000600
[    0.582873] pci 0000:3f:02.1: [8086:2d11] type 0 class 0x000600
[    0.582891] pci 0000:3f:02.2: [8086:2d12] type 0 class 0x000600
[    0.582912] pci 0000:3f:02.3: [8086:2d13] type 0 class 0x000600
[    0.582941] pci_bus 0000:3f: on NUMA node 0
[    0.582948]  pci0000:3f: Requesting ACPI _OSC control (0x1d)
[    0.582951]  pci0000:3f: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.582953] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.583182] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.583232] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.583280] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.583328] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.583377] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.583425] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.583474] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.583522] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.583603] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.583615] vgaarb: loaded
[    0.583616] vgaarb: bridge control possible 0000:00:02.0
[    0.583799] SCSI subsystem initialized
[    0.583841] libata version 3.00 loaded.
[    0.583880] usbcore: registered new interface driver usbfs
[    0.583891] usbcore: registered new interface driver hub
[    0.583915] usbcore: registered new device driver usb
[    0.583995] PCI: Using ACPI for IRQ routing
[    0.586145] PCI: pci_cache_line_size set to 64 bytes
[    0.586256] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.586259] reserve RAM buffer: 0000000076e07000 - 0000000077ffffff 
[    0.586357] NetLabel: Initializing
[    0.586359] NetLabel:  domain hash size = 128
[    0.586360] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.586373] NetLabel:  unlabeled traffic allowed by default
[    0.586418] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.586424] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.588443] Switching to clocksource hpet
[    0.590067] Switched to NOHz mode on CPU #0
[    0.590142] Switched to NOHz mode on CPU #2
[    0.590180] Switched to NOHz mode on CPU #3
[    0.590203] Switched to NOHz mode on CPU #1
[    0.594971] AppArmor: AppArmor Filesystem Enabled
[    0.595001] pnp: PnP ACPI init
[    0.595019] ACPI: bus type pnp registered
[    0.595381] pnp 00:00: [bus 00-3e]
[    0.595384] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.595386] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.595388] pnp 00:00: [io  0x0d00-0xffff window]
[    0.595391] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.595393] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.595395] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.595397] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.595399] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.595401] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.595405] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.595407] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.595409] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.595411] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.595413] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.595415] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.595418] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.595420] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.595422] pnp 00:00: [mem 0x7c000000-0xfeafffff window]
[    0.595503] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.595581] pnp 00:01: [io  0x0000-0x001f]
[    0.595583] pnp 00:01: [io  0x0081-0x0091]
[    0.595585] pnp 00:01: [io  0x0093-0x009f]
[    0.595587] pnp 00:01: [io  0x00c0-0x00df]
[    0.595589] pnp 00:01: [dma 4]
[    0.595619] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.595628] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.595658] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.595733] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.595767] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.595778] pnp 00:04: [io  0x00f0]
[    0.595791] pnp 00:04: [irq 13]
[    0.595822] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.595833] pnp 00:05: [io  0x002e-0x002f]
[    0.595835] pnp 00:05: [io  0x004e-0x004f]
[    0.595837] pnp 00:05: [io  0x0061]
[    0.595839] pnp 00:05: [io  0x0063]
[    0.595840] pnp 00:05: [io  0x0065]
[    0.595842] pnp 00:05: [io  0x0067]
[    0.595843] pnp 00:05: [io  0x0070]
[    0.595845] pnp 00:05: [io  0x0080]
[    0.595847] pnp 00:05: [io  0x0092]
[    0.595848] pnp 00:05: [io  0x00b2-0x00b3]
[    0.595850] pnp 00:05: [io  0x0680-0x069f]
[    0.595852] pnp 00:05: [io  0xff00-0xff0f]
[    0.595854] pnp 00:05: [io  0xffff]
[    0.595856] pnp 00:05: [io  0xffff]
[    0.595857] pnp 00:05: [io  0x0400-0x047f]
[    0.595859] pnp 00:05: [io  0x0500-0x057f]
[    0.595861] pnp 00:05: [io  0x164e-0x164f]
[    0.595936] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.595939] system 00:05: [io  0xff00-0xff0f] has been reserved
[    0.595942] system 00:05: [io  0xffff] has been reserved
[    0.595944] system 00:05: [io  0xffff] has been reserved
[    0.595947] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.595949] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.595952] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.595955] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.595964] pnp 00:06: [io  0x0070-0x0077]
[    0.595970] pnp 00:06: [irq 8]
[    0.596002] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.596054] pnp 00:07: [irq 12]
[    0.596092] pnp 00:07: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.596117] pnp 00:08: [io  0x0060]
[    0.596119] pnp 00:08: [io  0x0064]
[    0.596124] pnp 00:08: [irq 1]
[    0.596159] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.596445] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.596447] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    0.596449] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.596451] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.596453] pnp 00:09: [mem 0xf8000000-0xfbffffff]
[    0.596455] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.596458] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    0.596460] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.596462] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.596464] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.596466] pnp 00:09: [mem 0xf7fff000-0xf7ffffff]
[    0.596540] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.596543] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.596546] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.596549] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.596552] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.596554] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.596557] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.596560] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.596563] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.596565] system 00:09: [mem 0xf7fff000-0xf7ffffff] has been reserved
[    0.596569] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.596729] pnp 00:0a: [bus 3f]
[    0.596776] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.596789] pnp: PnP ACPI: found 11 devices
[    0.596790] ACPI: ACPI bus type pnp unregistered
[    0.596793] PnPBIOS: Disabled by ACPI PNP
[    0.632579] PCI: max bus depth: 1 pci_try_num: 2
[    0.632656] pci 0000:00:1c.5: BAR 15: assigned [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.632661] pci 0000:00:1c.4: BAR 15: assigned [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.632665] pci 0000:00:1c.3: BAR 15: assigned [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.632670] pci 0000:00:1c.2: BAR 15: assigned [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.632675] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.632680] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.632683] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.632685] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.632688] pci 0000:00:01.0:   bridge window [mem disabled]
[    0.632691] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    0.632695] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.632699] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.632705] pci 0000:00:1c.0:   bridge window [mem 0xf6800000-0xf7bfffff]
[    0.632710] pci 0000:00:1c.0:   bridge window [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.632719] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.632722] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.632729] pci 0000:00:1c.1:   bridge window [mem 0xf5400000-0xf67fffff]
[    0.632735] pci 0000:00:1c.1:   bridge window [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.632743] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.632746] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.632753] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf53fffff]
[    0.632758] pci 0000:00:1c.2:   bridge window [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.632767] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.632770] pci 0000:00:1c.3:   bridge window [io  0xa000-0xafff]
[    0.632777] pci 0000:00:1c.3:   bridge window [mem 0xf2c00000-0xf3ffffff]
[    0.632782] pci 0000:00:1c.3:   bridge window [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.632791] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.632795] pci 0000:00:1c.4:   bridge window [io  0x9000-0x9fff]
[    0.632801] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf2bfffff]
[    0.632807] pci 0000:00:1c.4:   bridge window [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.632815] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.632819] pci 0000:00:1c.5:   bridge window [io  0x8000-0x8fff]
[    0.632825] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf17fffff]
[    0.632830] pci 0000:00:1c.5:   bridge window [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.632839] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.632840] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.632846] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.632851] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.632872] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.632876] pci 0000:00:01.0: setting latency timer to 64
[    0.632883] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.632888] pci 0000:00:1c.0: setting latency timer to 64
[    0.632900] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.632905] pci 0000:00:1c.1: setting latency timer to 64
[    0.632916] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.632921] pci 0000:00:1c.2: setting latency timer to 64
[    0.632932] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.632937] pci 0000:00:1c.3: setting latency timer to 64
[    0.632945] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.632949] pci 0000:00:1c.4: setting latency timer to 64
[    0.632957] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.632962] pci 0000:00:1c.5: setting latency timer to 64
[    0.632970] pci 0000:00:1e.0: setting latency timer to 64
[    0.632975] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.632977] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.632980] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.632982] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.632984] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.632986] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.632989] pci_bus 0000:00: resource 10 [mem 0x7c000000-0xfeafffff]
[    0.632991] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.632993] pci_bus 0000:02: resource 1 [mem 0xf6800000-0xf7bfffff]
[    0.632996] pci_bus 0000:02: resource 2 [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.632998] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.633001] pci_bus 0000:03: resource 1 [mem 0xf5400000-0xf67fffff]
[    0.633003] pci_bus 0000:03: resource 2 [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.633005] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.633008] pci_bus 0000:04: resource 1 [mem 0xf4000000-0xf53fffff]
[    0.633010] pci_bus 0000:04: resource 2 [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.633012] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.633015] pci_bus 0000:05: resource 1 [mem 0xf2c00000-0xf3ffffff]
[    0.633017] pci_bus 0000:05: resource 2 [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.633019] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    0.633022] pci_bus 0000:06: resource 1 [mem 0xf1800000-0xf2bfffff]
[    0.633024] pci_bus 0000:06: resource 2 [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.633026] pci_bus 0000:07: resource 0 [io  0x8000-0x8fff]
[    0.633029] pci_bus 0000:07: resource 1 [mem 0xf0400000-0xf17fffff]
[    0.633031] pci_bus 0000:07: resource 2 [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.633034] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.633036] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.633038] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.633040] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.633043] pci_bus 0000:08: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.633045] pci_bus 0000:08: resource 9 [mem 0x000dc000-0x000dffff]
[    0.633047] pci_bus 0000:08: resource 10 [mem 0x7c000000-0xfeafffff]
[    0.633079] NET: Registered protocol family 2
[    0.633139] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.633325] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.633980] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.634307] TCP: Hash tables configured (established 131072 bind 65536)
[    0.634310] TCP reno registered
[    0.634313] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.634323] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.634411] NET: Registered protocol family 1
[    0.634425] pci 0000:00:02.0: Boot video device
[    0.676342] PCI: CLS 64 bytes, default 64
[    0.676396] Trying to unpack rootfs image as initramfs...
[    1.149702] Freeing initrd memory: 18336k freed
[    1.154583] audit: initializing netlink socket (disabled)
[    1.154596] type=2000 audit(1313985451.992:1): initialized
[    1.182272] highmem bounce pool size: 64 pages
[    1.182279] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.188378] VFS: Disk quotas dquot_6.5.2
[    1.188447] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.189063] fuse init (API version 7.16)
[    1.189149] msgmni has been set to 1709
[    1.189437] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.189472] io scheduler noop registered
[    1.189474] io scheduler deadline registered
[    1.189488] io scheduler cfq registered (default)
[    1.189605] pcieport 0000:00:01.0: setting latency timer to 64
[    1.189637] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.190021] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.190043] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.190104] intel_idle: MWAIT substates: 0x1120
[    1.190106] intel_idle: v0.4 model 0x25
[    1.190108] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.190196] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.190235] ACPI: AC Adapter [AC0] (on-line)
[    1.190336] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.191594] ACPI: Lid Switch [LID]
[    1.191642] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.191648] ACPI: Sleep Button [SLPB]
[    1.191692] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.191695] ACPI: Power Button [PWRB]
[    1.191729] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.191732] ACPI: Power Button [PWRF]
[    1.191761] ACPI: acpi_idle yielding to intel_idle
[    1.193673] thermal LNXTHERM:00: registered as thermal_zone0
[    1.193675] ACPI: Thermal Zone [TZ00] (61 C)
[    1.193687] ERST: Table is not found!
[    1.193699] isapnp: Scanning for PnP cards...
[    1.194342] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.194349] ACPI: Battery Slot [BAT0] (battery present)
[    1.547394] isapnp: No Plug & Play device found
[    1.547457] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.563177] Linux agpgart interface v0.103
[    1.563288] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.563362] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.564067] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.564212] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.565321] brd: module loaded
[    1.565832] loop: module loaded
[    1.566254] Fixed MDIO Bus: probed
[    1.566276] PPP generic driver version 2.4.2
[    1.566309] tun: Universal TUN/TAP device driver, 1.6
[    1.566311] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.566376] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.566398] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.566416] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.566421] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.566451] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.566483] ehci_hcd 0000:00:1a.0: debug port 2
[    1.570389] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.570411] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7c08000
[    1.582480] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.582628] hub 1-0:1.0: USB hub found
[    1.582632] hub 1-0:1.0: 2 ports detected
[    1.582706] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.582718] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.582722] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.582754] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.582783] ehci_hcd 0000:00:1d.0: debug port 2
[    1.586666] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.586681] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7c07000
[    1.602441] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.602588] hub 2-0:1.0: USB hub found
[    1.602592] hub 2-0:1.0: 2 ports detected
[    1.602649] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.602661] uhci_hcd: USB Universal Host Controller Interface driver
[    1.602739] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.604253] i8042: Detected active multiplexing controller, rev 1.1
[    1.605034] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.605042] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.605053] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.605055] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.605057] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.605203] mousedev: PS/2 mouse device common for all mice
[    1.605361] rtc_cmos 00:06: RTC can wake from S4
[    1.605465] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.605496] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.605576] device-mapper: uevent: version 1.0.3
[    1.605639] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.605711] device-mapper: multipath: version 1.3.0 loaded
[    1.605715] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.605803] EISA: Probing bus 0 at eisa.0
[    1.605807] EISA: Cannot allocate resource for mainboard
[    1.605809] Cannot allocate resource for EISA slot 1
[    1.605811] Cannot allocate resource for EISA slot 2
[    1.605812] Cannot allocate resource for EISA slot 3
[    1.605814] Cannot allocate resource for EISA slot 4
[    1.605816] Cannot allocate resource for EISA slot 5
[    1.605817] Cannot allocate resource for EISA slot 6
[    1.605819] Cannot allocate resource for EISA slot 7
[    1.605820] Cannot allocate resource for EISA slot 8
[    1.605822] EISA: Detected 0 cards.
[    1.605832] cpufreq-nforce2: No nForce2 chipset.
[    1.605926] cpuidle: using governor ladder
[    1.606077] cpuidle: using governor menu
[    1.606079] EFI Variables Facility v0.08 2004-May-17
[    1.606337] TCP cubic registered
[    1.606546] NET: Registered protocol family 10
[    1.607722] NET: Registered protocol family 17
[    1.607751] Registering the dns_resolver key type
[    1.607800] Using IPI No-Shortcut mode
[    1.607948] PM: Hibernation image not present or could not be loaded.
[    1.607967] registered taskstats version 1
[    1.611699]   Magic number: 7:423:968
[    1.611908] rtc_cmos 00:06: setting system clock to 2011-08-22 03:57:33 UTC (1313985453)
[    1.613741] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.613743] EDD information not available.
[    1.613937] Freeing unused kernel memory: 748k freed
[    1.614126] Write protecting the kernel text: 5332k
[    1.614199] Write protecting the kernel read-only data: 2224k
[    1.638461] udev[68]: starting version 167
[    1.639464] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.664135] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.664184] jme 0000:07:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.664200] jme 0000:07:00.5: setting latency timer to 64
[    1.665477] jme 0000:07:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:bc:ae:c5:59:c3:f7
[    1.666055] sdhci: Secure Digital Host Controller Interface driver
[    1.666059] sdhci: Copyright(c) Pierre Ossman
[    1.666690] sdhci-pci 0000:07:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.666713] sdhci-pci 0000:07:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.666758] sdhci-pci 0000:07:00.0: setting latency timer to 64
[    1.666790] mmc0: no vmmc regulator found
[    1.666834] Registered led device: mmc0::
[    1.666886] mmc0: SDHCI controller on PCI [0000:07:00.0] using ADMA
[    1.666898] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.666915] sdhci-pci 0000:07:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.666922] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
[    1.666932] sdhci-pci 0000:07:00.2: PCI INT B disabled
[    1.668395] [drm] Initialized drm 1.1.0 20060810
[    1.677151] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.677159] i915 0000:00:02.0: setting latency timer to 64
[    1.695293] i915 0000:00:02.0: irq 41 for MSI/MSI-X
[    1.695300] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.695302] [drm] Driver supports precise vblank timestamp query.
[    1.695358] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.905956] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.955837] fbcon: inteldrmfb (fb0) is primary device
[    2.038427] hub 1-1:1.0: USB hub found
[    2.038567] hub 1-1:1.0: 6 ports detected
[    2.123153] fixme: max PWM is zero.
[    2.129917] Console: switching to colour frame buffer device 170x48
[    2.136705] fb0: inteldrmfb frame buffer device
[    2.136707] drm: registered panic notifier
[    2.149450] Refined TSC clocksource calibration: 2260.999 MHz.
[    2.149460] Switching to clocksource tsc
[    2.149620] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.207745] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[    2.209705] acpi device:1b: registered as cooling_device4
[    2.209916] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.209966] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.209997] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.210020] ahci 0000:00:1f.2: version 3.0
[    2.210037] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.210101] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.210151] ahci: SSS flag set, parallel bus scan disabled
[    2.210207] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    2.210212] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    2.210219] ahci 0000:00:1f.2: setting latency timer to 64
[    2.234085] scsi0 : ahci
[    2.234213] scsi1 : ahci
[    2.234303] scsi2 : ahci
[    2.234389] scsi3 : ahci
[    2.234473] scsi4 : ahci
[    2.234562] scsi5 : ahci
[    2.234637] ata1: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06100 irq 42
[    2.234642] ata2: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06180 irq 42
[    2.234644] ata3: DUMMY
[    2.234646] ata4: DUMMY
[    2.234649] ata5: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06300 irq 42
[    2.234653] ata6: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06380 irq 42
[    2.281914] hub 2-1:1.0: USB hub found
[    2.282069] hub 2-1:1.0: 8 ports detected
[    2.353223] usb 1-1.2: new high speed USB device number 3 using ehci_hcd
[    2.552656] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.552796] usb 1-1.5: new full speed USB device number 4 using ehci_hcd
[    2.554858] ata1.00: ATA-8: WDC WD5000BEVT-80A0RT1, 01.01A01, max UDMA/133
[    2.554867] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.557262] ata1.00: configured for UDMA/133
[    2.557557] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-8 01.0 PQ: 0 ANSI: 5
[    2.557794] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.557806] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.557874] sd 0:0:0:0: [sda] Write Protect is off
[    2.557877] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.557899] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.671443]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.672039] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.720466] usb 2-1.2: new low speed USB device number 3 using ehci_hcd
[    2.875991] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.877658] ata2.00: ATAPI: MATSHITADVD-RAM UJ8A0ASW, 1.01, max UDMA/100
[    2.880277] ata2.00: configured for UDMA/100
[    2.884345] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8A0ASW 1.01 PQ: 0 ANSI: 5
[    2.887580] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.887589] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.887795] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.887883] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.207336] ata5: SATA link down (SStatus 0 SControl 300)
[    3.526694] ata6: SATA link down (SStatus 0 SControl 300)
[    3.529187] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6
[    3.529329] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.2/input0
[    3.529350] usbcore: registered new interface driver usbhid
[    3.529352] usbhid: USB HID core driver
[    5.042725] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.488530] udev[432]: starting version 167
[   16.727997] Linux video capture interface: v2.00
[   16.789074] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
[   16.796537] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7
[   16.796694] usbcore: registered new interface driver uvcvideo
[   16.796698] USB Video Class driver (v1.1.0)
[   16.861622] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   16.862073] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.862085] mei 0000:00:16.0: setting latency timer to 64
[   16.889307] cfg80211: Calling CRDA to update world regulatory domain
[   16.895187] cfg80211: World regulatory domain updated:
[   16.895191] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.895196] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.895200] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.895204] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.895208] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.895213] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.046795] type=1400 audit(1313985468.959:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=522 comm="apparmor_parser"
[   17.046869] type=1400 audit(1313985468.959:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor
_parser"
[   17.046934] type=1400 audit(1313985468.959:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_pars
er"
[   17.074849] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   17.074866] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.075001] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   17.083022] asus_laptop: Asus Laptop Support version 0.42
[   17.083181] asus_laptop:   K42F model detected
[   17.088325] lp: driver loaded but no devices found
[   17.104619] type=1400 audit(1313985469.019:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=654 comm="apparmor_parser"
[   17.104697] type=1400 audit(1313985469.019:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=654 comm="appar
mor_parser"
[   17.104764] type=1400 audit(1313985469.019:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=654 comm="apparmor_p
arser"
[   17.120631] asus_laptop: Backlight controlled by ACPI video driver
[   17.120695] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input8
    17.158205] psmouse serio4: ID: 10 00 64
[   17.232853] elantech: assuming hardware version 2, firmware version 4.1.1
[   17.260925] elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   17.276727] Bluetooth: Core ver 2.16
[   17.276761] NET: Registered protocol family 31
[   17.276763] Bluetooth: HCI device and connection manager initialized
[   17.276767] Bluetooth: HCI socket layer initialized
[   17.276769] Bluetooth: L2CAP socket layer initialized
[   17.276849] Bluetooth: SCO socket layer initialized
[   17.302964] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.303170] usbcore: registered new interface driver btusb
[   17.340793] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input9
[   17.446755] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.446771] ath9k 0000:03:00.0: setting latency timer to 64
[   17.497134] ath: EEPROM regdomain: 0x60
[   17.497137] ath: EEPROM indicates we should expect a direct regpair map
[   17.497140] ath: Country alpha2 being used: 00
[   17.497142] ath: Regpair used: 0x60
[   17.497146] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.497148] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497151] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.497153] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497155] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.497158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497160] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.497163] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497165] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.497167] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497169] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.497172] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497174] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.497176] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497178] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.497181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497183] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.497186] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497188] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.497190] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497192] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.497195] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497197] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.497200] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.497202] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.497204] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[
    17.497206] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.497209] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.498680] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   17.628714] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.629407] Registered led device: ath9k-phy0
[   17.629415] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8da0000, irq=17
[   18.584719] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.584780] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   18.584813] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.758595] hda_codec: ALC269VB: BIOS auto-probing.
[   18.783042] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.785239] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.785327] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.084628] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.227876] Intel AES-NI instructions are not detected.
[   19.297859] padlock_aes: VIA PadLock not detected.
[   19.386729] padlock_sha: VIA PadLock Hash Engine not detected.
[   19.615273] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   20.048677] jme 0000:07:00.5: irq 44 for MSI/MSI-X
[   20.049272] jme 0000:07:00.5: eth0: Link is down
[   20.049527] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.115108] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.194935] ppdev: user-space parallel port driver
[   20.259697] type=1400 audit(1313985472.179:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=962 comm="apparmor_parser"
[   20.429666] Adding 3999740k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:3999740k 
[   20.792234] type=1400 audit(1313985472.711:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1076 comm="apparmor_parser"
[   21.062781] type=1400 audit(1313985472.983:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=963 comm="apparmor_parser"
[   21.062899] type=1400 audit(1313985472.983:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="appa
rmor_parser"
[   22.642035] wlan0: authenticate with 5c:d9:98:ef:10:55 (try 1)
[   22.644341] wlan0: authenticated
[   22.663498] wlan0: associate with 5c:d9:98:ef:10:55 (try 1)
[   22.666266] wlan0: RX AssocResp from 5c:d9:98:ef:10:55 (capab=0x411 status=0 aid=1)
[   22.666269] wlan0: associated
[   22.666625] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.196037] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.198665] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   27.019556] audit_printk_skb: 15 callbacks suppressed
[   27.019559] type=1400 audit(1313985478.951:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=964 comm="apparmor_parser"
[   27.020385] type=1400 audit(1313985478.955:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=964 comm="apparmor_parser"
[   27.020878] type=1400 audit(1313985478.955:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=964 comm="apparmor_parser"
[   27.235360] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.235364] Bluetooth: BNEP filters: protocol multicast
[   27.336628] Bluetooth: RFCOMM TTY layer initialized
[   27.336635] Bluetooth: RFCOMM socket layer initialized
[   27.336637] Bluetooth: RFCOMM ver 1.11
[   33.403304] wlan0: no IPv6 routers present
[   50.423238] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2909.726584] compiz[1525]: segfault at 18 ip b71e633d sp bf97aae4 error 4 in libpthread-2.13.so[b71de000+15000]
marshall@C0r3:~$

---

### Post by M4r5h4ll on 2011-08-23
anybody ? guys pls this is important :confused::confused::confused:

---

### Post by heroandtn3 on 2011-09-29
I also have a ASUS A42F Laptop, and when I install Ubuntu 11.04 on it I have a lot of crash like you.

I think you should upgrade to Ubuntu 11.10 or downgrade to Ubuntu 10.04 LTS (recommend 10.04).

---

### Post by TweFoju on 2011-10-01
Its not your hardware

it's 11.04

no matter how you upgrade the Kernel to, it will still crash

either go back to 10.10 or you have to wait until 11.10, because i think 11.04 has no cure for the crash ( yet ) ;)

because i tried on 3 different laptop, all of them crash, so it's no way a hardware issue

---

