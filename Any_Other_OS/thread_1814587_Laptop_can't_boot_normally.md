---
title: "Laptop can't boot normally"
date: 2011-07-29
forum: Any Other OS
---

### Post by darkfeline on 2011-07-29
Sorry if this is in the wrong forum, but I'm not even entirely sure what the problem is.

I have a Linux Mint 11/Windows 7 dual boot on a Dell XPS L1502X. Recently, it stopped booting normally, hanging before the login screen appears.  Booting into recovery mode>failsafeX>Restart X works, without touching anything else.

I suspect this may have someone to do with the nvidia graphics card and/or drivers.  Because my laptop has nvidia optimus (i.e. switches between intel and nvidia graphics card), I use bumblebee to make it work on linux.

Here's the dmesg dump from when I start through recovery mode (I can't get a dump when booting it normally, since it hangs and I can't switch to any of the ttys):

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@yellow) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b1bb5d2d-15b9-469d-b73e-74af1b28f6be ro single
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bac8f000 (usable)
[    0.000000]  BIOS-e820: 00000000bac8f000 - 00000000bacac000 (reserved)
[    0.000000]  BIOS-e820: 00000000bacac000 - 00000000bacba000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bacba000 - 00000000badfa000 (reserved)
[    0.000000]  BIOS-e820: 00000000badfa000 - 00000000badfc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000badfc000 - 00000000badfe000 (reserved)
[    0.000000]  BIOS-e820: 00000000badfe000 - 00000000bae01000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bae01000 - 00000000bae04000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae04000 - 00000000bae05000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bae05000 - 00000000bae0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae0a000 - 00000000bae1b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bae1b000 - 00000000baf18000 (reserved)
[    0.000000]  BIOS-e820: 00000000baf18000 - 00000000baf1c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000baf1c000 - 00000000baf1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000baf1f000 - 00000000baf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000baf9f000 - 00000000bafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bafff000 - 00000000bb000000 (usable)
[    0.000000]  BIOS-e820: 00000000bb000000 - 00000000bfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001bfe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc.          Dell System XPS L502X/0YR8NN, BIOS A05 05/04/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x1bfe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 180000000 mask FC0000000 write-back
[    0.000000]   7 base 1BFE00000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
[    0.000000]  0000000000 - 00bb000000 page 2M
[    0.000000] kernel direct mapping tables up to bb000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-00000001bfe00000
[    0.000000]  0100000000 - 01bfe00000 page 2M
[    0.000000] kernel direct mapping tables up to 1bfe00000 @ bac87000-bac8f000
[    0.000000] RAMDISK: 35aca000 - 36d5d000
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000baffe120 0008C (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: FACP 00000000bafef000 000F4 (v03 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000baff2000 08C93 (v02 DELL    SNB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf3f000 00040
[    0.000000] ACPI: SLIC 00000000baffd000 00176 (v01 DELL    QA09    00000002 LOHR 00000001)
[    0.000000] ACPI: SSDT 00000000baffb000 01068 (v01 DELL   PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000baff1000 000A5 (v32 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: HPET 00000000bafee000 00038 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: APIC 00000000bafed000 00098 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000bafec000 0003C (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: SSDT 00000000bafea000 0124D (v01 NvORef NvOptTbl 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe9000 0090C (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe8000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000bafe7000 0003E (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafe5000 0026A (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000001bfe00000
[    0.000000] Initmem setup node 0 0000000000000000-00000001bfe00000
[    0.000000]   NODE_DATA [00000001bfdfb000 - 00000001bfdfffff]
[    0.000000]  [ffffea0000000000-ffffea00061fffff] PMD -> [ffff8801b9c00000-ffff8801beffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bac8f
[    0.000000]     0: 0x000bafff -> 0x000bb000
[    0.000000]     0: 0x00100000 -> 0x001bfe00
[    0.000000] On node 0 totalpages: 1550877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 746696 pages, LIFO batch:31
[    0.000000]   Normal zone: 10745 pages used for memmap
[    0.000000]   Normal zone: 775175 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bac8f000 - 00000000bacac000
[    0.000000] PM: Registered nosave memory: 00000000bacac000 - 00000000bacba000
[    0.000000] PM: Registered nosave memory: 00000000bacba000 - 00000000badfa000
[    0.000000] PM: Registered nosave memory: 00000000badfa000 - 00000000badfc000
[    0.000000] PM: Registered nosave memory: 00000000badfc000 - 00000000badfe000
[    0.000000] PM: Registered nosave memory: 00000000badfe000 - 00000000bae01000
[    0.000000] PM: Registered nosave memory: 00000000bae01000 - 00000000bae04000
[    0.000000] PM: Registered nosave memory: 00000000bae04000 - 00000000bae05000
[    0.000000] PM: Registered nosave memory: 00000000bae05000 - 00000000bae0a000
[    0.000000] PM: Registered nosave memory: 00000000bae0a000 - 00000000bae1b000
[    0.000000] PM: Registered nosave memory: 00000000bae1b000 - 00000000baf18000
[    0.000000] PM: Registered nosave memory: 00000000baf18000 - 00000000baf1c000
[    0.000000] PM: Registered nosave memory: 00000000baf1c000 - 00000000baf1f000
[    0.000000] PM: Registered nosave memory: 00000000baf1f000 - 00000000baf9f000
[    0.000000] PM: Registered nosave memory: 00000000baf9f000 - 00000000bafff000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
[    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
[    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:38600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800baa00000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1525790
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b1bb5d2d-15b9-469d-b73e-74af1b28f6be ro single
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 6017992k/7337984k available (5941k kernel code, 1134476k absent, 185516k reserved, 5016k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 62914560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 1995.318 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.63 BogoMIPS (lpj=19953180)
[    0.000083] pid_max: default: 32768 minimum: 301
[    0.000143] Security Framework initialized
[    0.000191] AppArmor: AppArmor initialized
[    0.000228] Yama: becoming mindful.
[    0.001134] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003255] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004111] Mount-cache hash table entries: 256
[    0.004252] Initializing cgroup subsys ns
[    0.004290] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004348] Initializing cgroup subsys cpuacct
[    0.004387] Initializing cgroup subsys memory
[    0.004429] Initializing cgroup subsys devices
[    0.004468] Initializing cgroup subsys freezer
[    0.004505] Initializing cgroup subsys net_cls
[    0.004543] Initializing cgroup subsys blkio
[    0.004608] CPU: Physical Processor ID: 0
[    0.004644] CPU: Processor Core ID: 0
[    0.004684] mce: CPU supports 9 MCE banks
[    0.004732] CPU0: Thermal monitoring handled by SMI
[    0.004740] using mwait in idle threads.
[    0.007626] ACPI: Core revision 20110112
[    0.064978] ftrace: allocating 24323 entries in 96 pages
[    0.076164] Not enabling x2apic, Intr-remapping init failed.
[    0.076207] Setting APIC routing to flat
[    0.076595] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.177099] CPU0: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz stepping 07
[    0.287790] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.287899] ... version:                3
[    0.287936] ... bit width:              48
[    0.287973] ... generic registers:      4
[    0.288009] ... value mask:             0000ffffffffffff
[    0.288048] ... max period:             000000007fffffff
[    0.288087] ... fixed-purpose events:   3
[    0.288123] ... event mask:             000000070000000f
[    0.288631] Booting Node   0, Processors  #1
[    0.447766] CPU1: Thermal monitoring handled by SMI
[    0.467893]  #2
[    0.627707] CPU2: Thermal monitoring handled by SMI
[    0.647825]  #3
[    0.807646] CPU3: Thermal monitoring handled by SMI
[    0.827755]  #4
[    0.987590] CPU4: Thermal monitoring handled by SMI
[    1.007783]  #5
[    1.167530] CPU5: Thermal monitoring handled by SMI
[    1.187720]  #6
[    1.347474] CPU6: Thermal monitoring handled by SMI
[    1.367655]  #7 Ok.
[    1.527414] CPU7: Thermal monitoring handled by SMI
[    1.547530] Brought up 8 CPUs
[    1.547567] Total of 8 processors activated (31927.25 BogoMIPS).
[    1.553884] devtmpfs: initialized
[    1.554898] print_constraints: dummy: 
[    1.554961] Time: 12:45:17  Date: 07/29/11
[    1.555026] NET: Registered protocol family 16
[    1.555155] Trying to unpack rootfs image as initramfs...
[    1.555164] ACPI: bus type pci registered
[    1.555235] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.555238] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    1.572263] PCI: Using configuration type 1 for base access
[    1.573038] bio: create slab <bio-0> at 0
[    1.575043] ACPI: EC: Look up EC in DSDT
[    1.576841] ACPI: Executed 1 blocks of module-level executable AML code
[    1.727389] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.728420] ACPI: SSDT 00000000bae06718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    1.728992] ACPI: Dynamic OEM Table Load:
[    1.729062] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    1.787615] ACPI: SSDT 00000000bae07a98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    1.788231] ACPI: Dynamic OEM Table Load:
[    1.788301] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    1.827433] ACPI: SSDT 00000000bae05d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    1.828005] ACPI: Dynamic OEM Table Load:
[    1.828075] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    1.891947] ACPI: Interpreter enabled
[    1.891988] ACPI: (supports S0 S3 S4 S5)
[    1.892113] ACPI: Using IOAPIC for interrupt routing
[    1.898420] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.920019] Freeing initrd memory: 19020k freed
[    1.967519] ACPI: No dock devices found.
[    1.967560] HEST: Table not found.
[    1.967597] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.968075] \_SB_.PCI0:_OSC invalid UUID
[    1.968076] _OSC request data:1 8 1f 
[    1.968081] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.968794] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.968837] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.968879] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.968935] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfeafffff]
[    1.968990] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.969057] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.969097] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    1.969126] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.969129] pci 0000:00:01.0: PME# disabled
[    1.969150] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    1.969163] pci 0000:00:02.0: reg 10: [mem 0xf1400000-0xf17fffff 64bit]
[    1.969170] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.969175] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    1.969232] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.969257] pci 0000:00:16.0: reg 10: [mem 0xf1c05000-0xf1c0500f 64bit]
[    1.969324] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.969329] pci 0000:00:16.0: PME# disabled
[    1.969366] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.969389] pci 0000:00:1a.0: reg 10: [mem 0xf1c0a000-0xf1c0a3ff]
[    1.969469] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.969474] pci 0000:00:1a.0: PME# disabled
[    1.969500] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.969517] pci 0000:00:1b.0: reg 10: [mem 0xf1c00000-0xf1c03fff 64bit]
[    1.969576] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.969580] pci 0000:00:1b.0: PME# disabled
[    1.969606] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.969709] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.969714] pci 0000:00:1c.0: PME# disabled
[    1.969748] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.969850] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.969855] pci 0000:00:1c.1: PME# disabled
[    1.969892] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    1.969994] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.969999] pci 0000:00:1c.3: PME# disabled
[    1.970032] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    1.970100] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.970104] pci 0000:00:1c.4: PME# disabled
[    1.970129] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    1.970198] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.970202] pci 0000:00:1c.5: PME# disabled
[    1.970235] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.970259] pci 0000:00:1d.0: reg 10: [mem 0xf1c09000-0xf1c093ff]
[    1.970337] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.970342] pci 0000:00:1d.0: PME# disabled
[    1.970369] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    1.970492] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.970513] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    1.970523] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    1.970532] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    1.970541] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    1.970550] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    1.970559] pci 0000:00:1f.2: reg 24: [mem 0xf1c08000-0xf1c087ff]
[    1.970595] pci 0000:00:1f.2: PME# supported from D3hot
[    1.970599] pci 0000:00:1f.2: PME# disabled
[    1.970619] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.970637] pci 0000:00:1f.3: reg 10: [mem 0xf1c04000-0xf1c040ff 64bit]
[    1.970660] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    1.970723] pci 0000:01:00.0: [10de:0df5] type 0 class 0x000300
[    1.970732] pci 0000:01:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    1.970742] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.970752] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    1.970759] pci 0000:01:00.0: reg 24: [io  0x3000-0x307f]
[    1.970766] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    1.987267] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.987346] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.987353] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    1.987363] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    1.987449] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.987493] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.987499] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.987508] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.987731] pci 0000:03:00.0: [8086:008a] type 0 class 0x000280
[    1.987898] pci 0000:03:00.0: reg 10: [mem 0xf1b00000-0xf1b01fff 64bit]
[    1.988496] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.988532] pci 0000:03:00.0: PME# disabled
[    2.007387] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.007430] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    2.007436] pci 0000:00:1c.1:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    2.007445] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.007592] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    2.007621] pci 0000:04:00.0: reg 10: [mem 0xf1a00000-0xf1a01fff 64bit]
[    2.007734] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    2.007740] pci 0000:04:00.0: PME# disabled
[    2.027308] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    2.027384] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    2.027389] pci 0000:00:1c.3:   bridge window [mem 0xf1a00000-0xf1afffff]
[    2.027396] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.027445] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    2.027487] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    2.027492] pci 0000:00:1c.4:   bridge window [mem 0xf1900000-0xf19fffff]
[    2.027499] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.027570] pci 0000:06:00.0: [10ec:8168] type 0 class 0x000200
[    2.027591] pci 0000:06:00.0: reg 10: [io  0x2000-0x20ff]
[    2.027627] pci 0000:06:00.0: reg 18: [mem 0xf1804000-0xf1804fff 64bit pref]
[    2.027651] pci 0000:06:00.0: reg 20: [mem 0xf1800000-0xf1803fff 64bit pref]
[    2.027715] pci 0000:06:00.0: supports D1 D2
[    2.027717] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.027723] pci 0000:06:00.0: PME# disabled
[    2.047253] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    2.047333] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    2.047343] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.047364] pci 0000:00:1c.5:   bridge window [mem 0xf1800000-0xf18fffff 64bit pref]
[    2.047402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.047545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.047584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    2.047625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    2.047662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    2.047717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    2.047767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    2.047846] \_SB_.PCI0:_OSC invalid UUID
[    2.047847] _OSC request data:1 1f 1f 
[    2.047852]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.047926] \_SB_.PCI0:_OSC invalid UUID
[    2.047927] _OSC request data:1 0 1d 
[    2.051391] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    2.051680] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    2.051965] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    2.052250] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    2.052535] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.052868] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.053203] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    2.053487] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    2.053818] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    2.053882] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    2.053940] vgaarb: loaded
[    2.054126] SCSI subsystem initialized
[    2.054213] libata version 3.00 loaded.
[    2.054250] usbcore: registered new interface driver usbfs
[    2.054297] usbcore: registered new interface driver hub
[    2.054359] usbcore: registered new device driver usb
[    2.054607] wmi: Mapper loaded
[    2.054643] PCI: Using ACPI for IRQ routing
[    2.054680] PCI: pci_cache_line_size set to 64 bytes
[    2.054866] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    2.054869] reserve RAM buffer: 00000000bac8f000 - 00000000bbffffff 
[    2.054873] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
[    2.054875] reserve RAM buffer: 00000001bfe00000 - 00000001bfffffff 
[    2.054961] NetLabel: Initializing
[    2.054996] NetLabel:  domain hash size = 128
[    2.055033] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.055080] NetLabel:  unlabeled traffic allowed by default
[    2.055152] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    2.055342] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.057399] Switching to clocksource hpet
[    2.063155] AppArmor: AppArmor Filesystem Enabled
[    2.063212] pnp: PnP ACPI init
[    2.063259] ACPI: bus type pnp registered
[    2.063658] pnp 00:00: [bus 00-3e]
[    2.063660] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.063662] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.063664] pnp 00:00: [io  0x0d00-0xffff window]
[    2.063666] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.063668] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    2.063670] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    2.063672] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    2.063674] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    2.063676] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    2.063678] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    2.063680] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    2.063682] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    2.063684] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    2.063686] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    2.063688] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    2.063690] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    2.063691] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    2.063693] pnp 00:00: [mem 0xbfa00000-0xfeafffff window]
[    2.063695] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    2.063758] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.063772] pnp 00:01: [io  0x0000-0x001f]
[    2.063773] pnp 00:01: [io  0x0081-0x0091]
[    2.063775] pnp 00:01: [io  0x0093-0x009f]
[    2.063777] pnp 00:01: [io  0x00c0-0x00df]
[    2.063779] pnp 00:01: [dma 4]
[    2.063800] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.063882] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    2.063904] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.063914] pnp 00:03: [io  0x00f0]
[    2.063923] pnp 00:03: [irq 13]
[    2.063944] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.063955] pnp 00:04: [io  0x002e-0x002f]
[    2.063957] pnp 00:04: [io  0x004e-0x004f]
[    2.063959] pnp 00:04: [io  0x0061]
[    2.063960] pnp 00:04: [io  0x0063]
[    2.063963] pnp 00:04: [io  0x0065]
[    2.063965] pnp 00:04: [io  0x0067]
[    2.063966] pnp 00:04: [io  0x0068]
[    2.063968] pnp 00:04: [io  0x006c]
[    2.063969] pnp 00:04: [io  0x0070]
[    2.063971] pnp 00:04: [io  0x0080]
[    2.063972] pnp 00:04: [io  0x0092]
[    2.063974] pnp 00:04: [io  0x00b2-0x00b3]
[    2.063976] pnp 00:04: [io  0x0680-0x069f]
[    2.063977] pnp 00:04: [io  0x1000-0x1003]
[    2.063979] pnp 00:04: [io  0x1004-0x1013]
[    2.063980] pnp 00:04: [io  0xffff]
[    2.063982] pnp 00:04: [io  0x0400-0x0453]
[    2.063984] pnp 00:04: [io  0x0458-0x047f]
[    2.063985] pnp 00:04: [io  0x0500-0x057f]
[    2.063987] pnp 00:04: [io  0x164e-0x164f]
[    2.064038] system 00:04: [io  0x0680-0x069f] has been reserved
[    2.064080] system 00:04: [io  0x1000-0x1003] has been reserved
[    2.064121] system 00:04: [io  0x1004-0x1013] has been reserved
[    2.064162] system 00:04: [io  0xffff] has been reserved
[    2.064202] system 00:04: [io  0x0400-0x0453] has been reserved
[    2.064242] system 00:04: [io  0x0458-0x047f] has been reserved
[    2.064283] system 00:04: [io  0x0500-0x057f] has been reserved
[    2.064324] system 00:04: [io  0x164e-0x164f] has been reserved
[    2.064366] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.064374] pnp 00:05: [io  0x0070-0x0077]
[    2.064379] pnp 00:05: [irq 8]
[    2.064401] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.064428] pnp 00:06: [io  0x0454-0x0457]
[    2.064469] system 00:06: [io  0x0454-0x0457] has been reserved
[    2.064510] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    2.064549] pnp 00:07: [io  0x0060]
[    2.064550] pnp 00:07: [io  0x0064]
[    2.064555] pnp 00:07: [irq 1]
[    2.064580] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.064613] pnp 00:08: [irq 12]
[    2.064639] pnp 00:08: Plug and Play ACPI device, IDs DLL04b6 PNP0f13 (active)
[    2.064748] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    2.064750] pnp 00:09: [mem 0xfed10000-0xfed17fff]
[    2.064752] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    2.064754] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    2.064756] pnp 00:09: [mem 0xf8000000-0xfbffffff]
[    2.064757] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    2.064759] pnp 00:09: [mem 0xfed90000-0xfed93fff]
[    2.064761] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    2.064763] pnp 00:09: [mem 0xff000000-0xffffffff]
[    2.064764] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    2.064766] pnp 00:09: [mem 0xfffff000-0xffffffff]
[    2.064784] pnp 00:09: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    2.064876] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.064918] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    2.064960] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.065002] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.065044] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    2.065087] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.065128] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    2.065170] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.065213] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    2.065255] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    2.065299] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.065423] pnp 00:0a: [irq 20]
[    2.065464] pnp 00:0a: Plug and Play ACPI device, IDs SMO8800 (active)
[    2.065604] pnp: PnP ACPI: found 11 devices
[    2.065641] ACPI: ACPI bus type pnp unregistered
[    2.067225] Switched to NOHz mode on CPU #0
[    2.067290] Switched to NOHz mode on CPU #3
[    2.067297] Switched to NOHz mode on CPU #2
[    2.067305] Switched to NOHz mode on CPU #1
[    2.067365] Switched to NOHz mode on CPU #5
[    2.067368] Switched to NOHz mode on CPU #7
[    2.067370] Switched to NOHz mode on CPU #6
[    2.067377] Switched to NOHz mode on CPU #4
[    2.071698] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    2.071817] pci 0000:01:00.0: BAR 6: assigned [mem 0xf1000000-0xf107ffff pref]
[    2.071873] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.071912] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    2.071954] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    2.071998] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    2.072056] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.072095] pci 0000:00:1c.0:   bridge window [io  disabled]
[    2.072141] pci 0000:00:1c.0:   bridge window [mem disabled]
[    2.072184] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    2.072232] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.072271] pci 0000:00:1c.1:   bridge window [io  disabled]
[    2.072317] pci 0000:00:1c.1:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    2.072363] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    2.072411] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    2.072450] pci 0000:00:1c.3:   bridge window [io  disabled]
[    2.072495] pci 0000:00:1c.3:   bridge window [mem 0xf1a00000-0xf1afffff]
[    2.072540] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    2.072588] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    2.072627] pci 0000:00:1c.4:   bridge window [io  disabled]
[    2.072671] pci 0000:00:1c.4:   bridge window [mem 0xf1900000-0xf19fffff]
[    2.072715] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    2.072762] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    2.072801] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    2.072846] pci 0000:00:1c.5:   bridge window [mem disabled]
[    2.072889] pci 0000:00:1c.5:   bridge window [mem 0xf1800000-0xf18fffff 64bit pref]
[    2.072960] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.073003] pci 0000:00:01.0: setting latency timer to 64
[    2.073011] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.073058] pci 0000:00:1c.0: setting latency timer to 64
[    2.073070] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.073115] pci 0000:00:1c.1: setting latency timer to 64
[    2.073126] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.073172] pci 0000:00:1c.3: setting latency timer to 64
[    2.073180] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.073224] pci 0000:00:1c.4: setting latency timer to 64
[    2.073232] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.073276] pci 0000:00:1c.5: setting latency timer to 64
[    2.073281] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.073283] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.073285] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.073287] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    2.073289] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    2.073291] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    2.073293] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf10fffff]
[    2.073296] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    2.073298] pci_bus 0000:03: resource 1 [mem 0xf1b00000-0xf1bfffff]
[    2.073300] pci_bus 0000:04: resource 1 [mem 0xf1a00000-0xf1afffff]
[    2.073302] pci_bus 0000:05: resource 1 [mem 0xf1900000-0xf19fffff]
[    2.073304] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    2.073306] pci_bus 0000:06: resource 2 [mem 0xf1800000-0xf18fffff 64bit pref]
[    2.073333] NET: Registered protocol family 2
[    2.073617] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    2.075775] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.077240] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.077419] TCP: Hash tables configured (established 524288 bind 65536)
[    2.077478] TCP reno registered
[    2.077528] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.077607] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.078248] NET: Registered protocol family 1
[    2.078299] pci 0000:00:02.0: Boot video device
[    2.079789] PCI: CLS 64 bytes, default 64
[    2.079791] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.079833] Placing 64MB software IO TLB between ffff8800b6a00000 - ffff8800baa00000
[    2.079889] software IO TLB at phys 0xb6a00000 - 0xbaa00000
[    2.080532] audit: initializing netlink socket (disabled)
[    2.080580] type=2000 audit(1311943516.860:1): initialized
[    2.095700] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.097326] VFS: Disk quotas dquot_6.5.2
[    2.097413] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.098034] fuse init (API version 7.16)
[    2.098154] msgmni has been set to 11791
[    2.098403] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.098482] io scheduler noop registered
[    2.098520] io scheduler deadline registered
[    2.098592] io scheduler cfq registered (default)
[    2.098710] pcieport 0000:00:01.0: setting latency timer to 64
[    2.098739] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.099024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.099084] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.099162] intel_idle: MWAIT substates: 0x21120
[    2.099163] intel_idle: v0.4 model 0x2A
[    2.099165] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.197459] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.297443] ACPI: AC Adapter [ADP0] (off-line)
[    2.297601] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.297661] ACPI: Power Button [PWRB]
[    2.297731] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.297789] ACPI: Sleep Button [SLPB]
[    2.297859] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.298868] ACPI: Lid Switch [LID0]
[    2.298946] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.299003] ACPI: Power Button [PWRF]
[    2.299216] ACPI: acpi_idle yielding to intel_idle
[    2.301046] thermal LNXTHERM:00: registered as thermal_zone0
[    2.301089] ACPI: Thermal Zone [TZ00] (59 C)
[    2.301322] thermal LNXTHERM:01: registered as thermal_zone1
[    2.301363] ACPI: Thermal Zone [TZ01] (59 C)
[    2.301449] ERST: Table is not found!
[    2.301544] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.314584] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.314677] ACPI: Battery Slot [BAT0] (battery present)
[    2.329468] Linux agpgart interface v0.103
[    2.329588] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    2.329790] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.331517] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    2.331672] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.332688] brd: module loaded
[    2.333164] loop: module loaded
[    2.333282] i2c-core: driver [adp5520] using legacy suspend method
[    2.333323] i2c-core: driver [adp5520] using legacy resume method
[    2.333702] Fixed MDIO Bus: probed
[    2.333762] PPP generic driver version 2.4.2
[    2.333831] tun: Universal TUN/TAP device driver, 1.6
[    2.333870] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.333978] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.334035] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.334094] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.334098] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.334173] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.334293] ehci_hcd 0000:00:1a.0: debug port 2
[    2.338212] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.338231] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf1c0a000
[    2.357381] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.357600] hub 1-0:1.0: USB hub found
[    2.357639] hub 1-0:1.0: 2 ports detected
[    2.357743] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.357798] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.357801] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.357875] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.357983] ehci_hcd 0000:00:1d.0: debug port 2
[    2.361915] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.361929] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf1c09000
[    2.377377] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.377567] hub 2-0:1.0: USB hub found
[    2.377605] hub 2-0:1.0: 2 ports detected
[    2.377695] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.377745] uhci_hcd: USB Universal Host Controller Interface driver
[    2.377878] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.382396] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.382440] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.382590] mousedev: PS/2 mouse device common for all mice
[    2.382774] rtc_cmos 00:05: RTC can wake from S4
[    2.382872] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.382941] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.383074] device-mapper: uevent: version 1.0.3
[    2.383180] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.383286] device-mapper: multipath: version 1.2.0 loaded
[    2.383337] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.383686] cpuidle: using governor ladder
[    2.384082] cpuidle: using governor menu
[    2.384321] TCP cubic registered
[    2.384460] NET: Registered protocol family 10
[    2.384900] NET: Registered protocol family 17
[    2.384949] Registering the dns_resolver key type
[    2.386603] PM: Hibernation image not present or could not be loaded.
[    2.386612] registered taskstats version 1
[    2.386929]   Magic number: 3:693:785
[    2.387076] rtc_cmos 00:05: setting system clock to 2011-07-29 12:45:18 UTC (1311943518)
[    2.387135] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.387172] EDD information not available.
[    2.388592] Freeing unused kernel memory: 956k freed
[    2.388734] Write protecting the kernel read-only data: 10240k
[    2.389027] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.389637] Freeing unused kernel memory: 184k freed
[    2.393396] Freeing unused kernel memory: 1440k freed
[    2.407325] <30>udev[84]: starting version 167
[    2.608196] Btrfs loaded
[    2.615388] xor: automatically using best checksumming function: generic_sse
[    2.617901] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.617938] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    2.617943] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.618013] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    2.621510] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.621542] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.621598] r8169 0000:06:00.0: setting latency timer to 64
[    2.621605] r8169 0000:06:00.0: (unregistered net_device): unknown MAC, using family default
[    2.621690] r8169 0000:06:00.0: irq 41 for MSI/MSI-X
[    2.622174] r8169 0000:06:00.0: eth0: RTL8168b/8111b at 0xffffc900057e2000, 14:fe:b5:ab:b1:a5, XID 0c200000 IRQ 41
[    2.623913] ahci 0000:00:1f.2: version 3.0
[    2.623926] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.623988] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.624022] ahci: SSS flag set, parallel bus scan disabled
[    2.637331] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    2.637360] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    2.637379] ahci 0000:00:1f.2: setting latency timer to 64
[    2.657264]    generic_sse: 12904.400 MB/sec
[    2.657297] xor: using function: generic_sse (12904.400 MB/sec)
[    2.659211] device-mapper: dm-raid45: initialized v0.2594b
[    2.667588] xhci_hcd 0000:04:00.0: irq 19, io mem 0xf1a00000
[    2.667738] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    2.667742] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    2.667746] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    2.667757] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    2.667761] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    2.667764] xhci_hcd 0000:04:00.0: irq 48 for MSI/MSI-X
[    2.667768] xhci_hcd 0000:04:00.0: irq 49 for MSI/MSI-X
[    2.667771] xhci_hcd 0000:04:00.0: irq 50 for MSI/MSI-X
[    2.670977] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    2.671104] xHCI xhci_add_endpoint called for root hub
[    2.671106] xHCI xhci_check_bandwidth called for root hub
[    2.671137] hub 3-0:1.0: USB hub found
[    2.671161] hub 3-0:1.0: 4 ports detected
[    2.677418] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.677905] scsi0 : ahci
[    2.678118] scsi1 : ahci
[    2.678336] scsi2 : ahci
[    2.678482] scsi3 : ahci
[    2.678626] scsi4 : ahci
[    2.678764] scsi5 : ahci
[    2.678871] ata1: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08100 irq 42
[    2.678909] ata2: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08180 irq 42
[    2.678944] ata3: DUMMY
[    2.678961] ata4: DUMMY
[    2.678978] ata5: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08300 irq 42
[    2.679013] ata6: DUMMY
[    2.828027] hub 1-1:1.0: USB hub found
[    2.828208] hub 1-1:1.0: 6 ports detected
[    2.947298] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.027256] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.029865] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.030243] ata1.00: ATA-8: WDC WD7500BPKT-75PK4T0, 01.01A01, max UDMA/133
[    3.030297] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.033021] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.033407] ata1.00: configured for UDMA/133
[    3.033594] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPKT-7 01.0 PQ: 0 ANSI: 5
[    3.033810] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.033942] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    3.034001] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.034053] sd 0:0:0:0: [sda] Write Protect is off
[    3.034073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.034086] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.077221] Refined TSC clocksource calibration: 1995.470 MHz.
[    3.077277] Switching to clocksource tsc
[    3.097844] hub 2-1:1.0: USB hub found
[    3.097933] hub 2-1:1.0: 8 ports detected
[    3.116186]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    3.116624] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.177365] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
[    3.377147] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.377235] usb 2-1.2: new low speed USB device using ehci_hcd and address 3
[    3.380320] ata2.00: ATAPI: PLDS DVD+/-RW DS-8A5SH, XD12, max UDMA/100
[    3.381683] ata2.00: configured for UDMA/100
[    3.385749] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A5SH XD12 PQ: 0 ANSI: 5
[    3.391076] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.391134] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.391287] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.391358] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.567238] usb 2-1.5: new full speed USB device using ehci_hcd and address 4
[    3.737024] ata5: SATA link down (SStatus 0 SControl 300)
[    3.745974] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    3.746126] generic-usb 0003:04B3:310C.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    3.746185] usbcore: registered new interface driver usbhid
[    3.746209] usbhid: USB HID core driver
[    3.755618] [drm] Initialized drm 1.1.0 20060810
[    3.771111] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.771139] i915 0000:00:02.0: setting latency timer to 64
[    3.831003] i915 0000:00:02.0: irq 51 for MSI/MSI-X
[    3.831007] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.831040] [drm] Driver supports precise vblank timestamp query.
[    3.859461] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    3.859530] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    3.922802] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    3.922841] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    4.003957] fbcon: inteldrmfb (fb0) is primary device
[    4.062001] Console: switching to colour frame buffer device 170x48
[    4.064132] fb0: inteldrmfb frame buffer device
[    4.064146] drm: registered panic notifier
[    4.064323] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20110112/video-1139)
[    4.064386] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:33/LNXVIDEO:00/input/input6
[    4.064445] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    4.137780] acpi device:35: registered as cooling_device8
[    4.137954] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[    4.138022] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.138125] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.557400] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    9.557426] EXT4-fs (sda5): write access will be enabled during recovery
[    9.605548] EXT4-fs (sda5): recovery complete
[    9.607432] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   15.940657] <30>udev[373]: starting version 167
[   15.948363] lp: driver loaded but no devices found
[   16.179558] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.181434] Linux video capture interface: v2.00
[   16.188617] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2HDM (0408:2fb1)
[   16.198706] cfg80211: Calling CRDA to update world regulatory domain
[   16.209164] Bluetooth: Core ver 2.15
[   16.209188] NET: Registered protocol family 31
[   16.209190] Bluetooth: HCI device and connection manager initialized
[   16.209193] Bluetooth: HCI socket layer initialized
[   16.217528] uvcvideo: No streaming interface found for terminal 6.
[   16.217596] input: Laptop_Integrated_Webcam_2HDM as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8
[   16.217679] usbcore: registered new interface driver uvcvideo
[   16.217682] USB Video Class driver (v1.0.0)
[   16.245702] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.246653] VGA switcheroo: detected DSM switching method \_SB_.PCI0.PEG0.PEGP handle
[   16.246675] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   16.246678] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   16.246682] nouveau 0000:01:00.0: enabling device (0004 -> 0007)
[   16.246687] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.246691] nouveau 0000:01:00.0: setting latency timer to 64
[   16.251513] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.252807] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0c1a80a1)
[   16.253840] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.257409] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   16.258520] usbcore: registered new interface driver btusb
[   16.263600] vga_switcheroo: enabled
[   16.263619] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   16.273381] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   16.273384] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[   16.273393] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   16.273395] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PCIROM
[   16.279373] cfg80211: World regulatory domain updated:
[   16.279376] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.279380] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.279383] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.279386] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.279389] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.279392] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.284650] nouveau 0000:01:00.0: Invalid ROM contents
[   16.284831] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   16.284833] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from ACPI
[   16.295973] Bluetooth: L2CAP ver 2.15
[   16.295977] Bluetooth: L2CAP socket layer initialized
[   16.304291] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.308101] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.308103] Bluetooth: BNEP filters: protocol multicast
[   16.324218] Bluetooth: SCO (Voice Link) ver 0.6
[   16.324222] Bluetooth: SCO socket layer initialized
[   16.339457] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.339460] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.339551] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.339588] iwlagn 0000:03:00.0: setting latency timer to 64
[   16.339662] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   16.355029] iwlagn 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6
[   16.355032] iwlagn 0000:03:00.0: Device SKU: 0X9
[   16.355035] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   16.355052] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   16.355227] iwlagn 0000:03:00.0: irq 52 for MSI/MSI-X
[   16.363851] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.363904] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   16.363929] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.387340] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[   16.387552] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   16.391172] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.470034] Bluetooth: RFCOMM TTY layer initialized
[   16.470038] Bluetooth: RFCOMM socket layer initialized
[   16.470039] Bluetooth: RFCOMM ver 1.11
[   16.638786] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.733949] r8169 0000:06:00.0: eth0: link down
[   16.734399] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.989438] hda_codec: ALC665: SKU not ready 0x598301f0
[   16.989610] hda_codec: ALC665: BIOS auto-probing.
[   17.000034] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.000111] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.084400] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400
[   17.132184] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   28.879568] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   28.879572] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   28.879574] [drm] nouveau 0000:01:00.0: Bios version 70.08.53.00
[   28.879576] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[   28.879579] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[   28.879581] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   28.879583] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02014300 00000000
[   28.879584] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02021362 00020010
[   28.879586] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 0000000e 00000000
[   28.879588] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   28.879590] [drm] nouveau 0000:01:00.0:   0: 0x00000340: type 0x40 idx 0 tag 0xff
[   28.879592] [drm] nouveau 0000:01:00.0:   1: 0x00001061: type 0x61 idx 1 tag 0x07
[   28.879593] [drm] nouveau 0000:01:00.0:   2: 0x00000147: type 0x47 idx 2 tag 0xff
[   28.879595] [drm] nouveau 0000:01:00.0:   3: 0x00002346: type 0x46 idx 3 tag 0x08
[   28.879597] [drm] nouveau 0000:01:00.0:   4: 0x00000400: type 0x00 idx 4 tag 0xff
[   28.879598] [drm] nouveau 0000:01:00.0:   5: 0x00000210: type 0x10 idx 5 tag 0xff
[   28.879600] [drm] nouveau 0000:01:00.0:   6: 0x00000211: type 0x11 idx 6 tag 0xff
[   28.879601] [drm] nouveau 0000:01:00.0:   7: 0x00000213: type 0x13 idx 7 tag 0xff
[   28.879615] [drm] nouveau 0000:01:00.0: Adaptor not initialised, running VBIOS init tables.
[   28.879617] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD5D7
[   28.903824] [drm] nouveau 0000:01:00.0: 0xD581: i2c wr fail: -6
[   28.959044] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDC33
[   29.068938] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xEE39
[   29.068945] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE3D
[   29.069005] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEF25
[   29.069007] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEF8A
[   29.117826] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[   29.117830] [drm] nouveau 0000:01:00.0: 0: memory 135MHz core 270MHz shader 540MHz voltage 850mV
[   29.117832] [drm] nouveau 0000:01:00.0: 1: memory 405MHz core 270MHz shader 810MHz voltage 850mV
[   29.117834] [drm] nouveau 0000:01:00.0: 3: memory 405MHz core 960MHz shader 1200MHz voltage 950mV
[   29.117982] [TTM] Zone  kernel: Available graphics memory: 3019796 kiB.
[   29.117984] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   29.117985] [TTM] Initializing pool allocator.
[   29.118003] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[   29.136729] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   29.136737] [drm] nouveau 0000:01:00.0: PGRAPH: unsupported chipset, please report!
[   29.136868] [drm] nouveau 0000:01:00.0: PGRAPH: unknown config: 2/0/0/0, 1
[   29.138114] [drm] nouveau 0000:01:00.0: failed to load fuc409d
[   29.145814] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   29.145816] [drm] No driver support for vblank timestamp query.
[   29.145822] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
[   29.200653] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x30000000, bo ffff8801b2cb4400
[   29.200699] fb1: nouveaufb frame buffer device
[   29.200702] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 1
[   29.326324] nvidia: module license 'NVIDIA' taints kernel.
[   29.326327] Disabling lock debugging due to kernel taint
[   29.611438] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   29.611441] NVRM: This can occur when a driver such as nouveau, rivafb,
[   29.611443] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[   29.611444] NVRM: the NVIDIA device(s).
[   29.611446] NVRM: Try unloading the conflicting kernel module (and/or
[   29.611447] NVRM: reconfigure your kernel without the conflicting
[   29.611448] NVRM: driver(s)), then try loading the NVIDIA kernel module
[   29.611449] NVRM: again.
[   29.611451] NVRM: No NVIDIA graphics adapter probed!
[   30.023518] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   30.023521] NVRM: This can occur when a driver such as nouveau, rivafb,
[   30.023522] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[   30.023523] NVRM: the NVIDIA device(s).
[   30.023525] NVRM: Try unloading the conflicting kernel module (and/or
[   30.023526] NVRM: reconfigure your kernel without the conflicting
[   30.023527] NVRM: driver(s)), then try loading the NVIDIA kernel module
[   30.023528] NVRM: again.
[   30.023530] NVRM: No NVIDIA graphics adapter probed!
[   30.168654] ppdev: user-space parallel port driver
[   30.380943] Intel AES-NI instructions are not detected.
[   30.459652] padlock_aes: VIA PadLock not detected.
[   30.574626] padlock_sha: VIA PadLock Hash Engine not detected.
[   40.649213] acpi_call: Module loaded successfully
[   40.650743] acpi_call: Calling \_SB.PCI0.PEG0.PEGP._ON
[   41.195378] acpi_call: Call successful: {0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   41.559571] NVRM: This can occur when a driver such as nouveau, rivafb,
[   41.559572] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[   41.559572] NVRM: the NVIDIA device(s).
[   41.559574] NVRM: Try unloading the conflicting kernel module (and/or
[   41.559575] NVRM: reconfigure your kernel without the conflicting
[   41.559575] NVRM: driver(s)), then try loading the NVIDIA kernel module
[   41.559576] NVRM: again.
[   41.559577] NVRM: No NVIDIA graphics adapter probed!
[   41.614790] acpi_call: Calling \_SB.PCI0.PEG0.PEGP._OFF
[   41.735022] acpi_call: Call successful: 0x0
[   42.293206] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   47.061486] acpi_call: Calling \_SB.PCI0.PEG0.PEGP._OFF
[   47.061520] acpi_call: Call successful: 0x0
[  112.050704] wlan0: authenticate with 00:23:33:a2:81:30 (try 1)
[  112.052906] wlan0: authenticated
[  112.053117] wlan0: waiting for beacon from 00:23:33:a2:81:30
[  112.056933] wlan0: beacon received
[  112.122751] wlan0: associate with 00:23:33:a2:81:30 (try 1)
[  112.124830] wlan0: RX AssocResp from 00:23:33:a2:81:30 (capab=0x431 status=0 aid=6)
[  112.124848] wlan0: associated
[  112.128249] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  122.859284] wlan0: no IPv6 routers present

```

Some strange things I have noticed: 

The line in dmesg```
 [   16.284650] nouveau 0000:01:00.0: Invalid ROM contents
```
I don't know what that means but it doesn't seem like a good thing.

Also, even though I have nvidia-current installed, modprobe nvidia complains that there's no nvidia module. Since my kernel appears to be missing the nvidia module, that's a problem, isn't it? How do I fix this?

---

### Post by Perfect Storm on 2011-07-29
Moved to Other OS/Distro Talk.

---

### Post by RomeoJava on 2011-07-31
Have you found a solution to this yet? I've hit the exact same problem but using the official Ubuntu rather than Mint.

It gets quite confusing when the device has two graphics cards: Intel and Nvidia. Add to this the Nvidia card appearing to be using two drivers the official Nivdia one and this reference to Nouveau (which I had previously assumed had been completely disabed when the Nvidia one was installed).

I'm wondering whether the problem relates to this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/770650](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/770650)

Rj

---

### Post by darkfeline on 2011-07-31
I'm assuming by exact same problem you mean same laptop and using bumblebee to deal with the intel/nvidia setup?

I have manually added nouveau to /etc/modprobe.d/blacklist.conf and lsmod no longer shows the nouveau module, but this doesn't seem to fix anything.

My laptop hangs after 'Checking battery state  [OK]', which seems to be an ambiguous error since it can mean different things, but a bit of googling seems to nail it as a graphics driver problem.

What really gets me is that my laptop doesn't hang if I go through the recovery mode->failsafex->restart X.  How does this differ from booting normally such that a normal boot hangs?

---

### Post by sunkinguk on 2011-08-04
I have a similar setup, i.e. Linux Mint 11/Windows 7 on an Dell XPS L502X, and I have the 
same problem. It started after the last update of bumblebee (and the nvidia driver) a few 
days ago (about 30 July I think).

I think a bug (at least for this configuration) has been introduced with the update. I'm still
trying to resolve it. [This discussion]("https://github.com/MrMEEE/bumblebee/issues/552") might have a few clues about how to resolve the
problem.

---

### Post by darkfeline on 2011-08-04
I noticed this problem about five days ago too.

I tried a workaround in the discussion you linked: comment out the $ENABLECARD line in /etc/pm/power.d/bumblebee-disablecard-on-powerup

My laptop still hangs on boot and sudo modprobe nvidia-current still doesn't work, but oddly enough, optirun/bumblebee-*ablecard now works.

---

### Post by darkfeline on 2011-08-09
I managed to fix this problem after a soft re-install of Linux Mint (reinstalled over same partition without formatting).

I did the following, rebooting between each step:
-Install bumblebee through PPA. bumblebee doesn't work
-Comment out $ENABLECARD in bumblebee-disablecard-on-powerup.  Still nothing.
-sudo dpkg-reconfigure bumblebee.  I chose one of the provided setups (by Brad someone, I think) and used XV, the default transport thing. Laptop now hangs on boot, so I used the failsafeX fallback.
-echo blacklist nouveau > /etc/modprobe.d/blacklist-nouveau.conf. Laptop now boots normally and bumblebee works.

In the end, I'm not sure what the original problem was, though it is definitely related to bumblebee/optimus.

---

### Post by hlayhel on 2011-08-11
hi
not so sure about what the problem is,
but if it's a grub problem you would like to check this site

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

personally **[B]Super Grub2 Disk **worked fine with me.
[/B]

---

### Post by maildcastro on 2011-08-26
Hi,



I have edited: /etc/pm/power.d/bumblebee-disablecard-on-powerup


  and commented the lines $ENABLECARD AND $DISABLECARD and this has solved the 

problem. 



Regards,

---

