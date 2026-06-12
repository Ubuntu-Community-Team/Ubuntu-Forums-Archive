---
title: "System freeze 12.04 64bit on ASUS laptop"
date: 2013-12-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by fekioh2 on 2013-12-09
Hi all, 

I know there other threads with similar problems but I still can't figure out what's giong wrong...

My system freezes completely at random times. Then if I don't power off the machine, after a few minutes logs me out and when I log back in there is an "internal error detected" message. 

I am running a fresh installation of 12.04 64bit (kernel 3.8.0-34-generic) on an ASUS:
 PRO5MS series, 
CPU: Intel Core i7-2630QM, 2GHz
Memory: 8GB

I am pasting below a dump of my /var/log/dmesg.0:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-34-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 (Ubuntu 3.8.0-34.49~precise1-generic 3.8.13.12)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-34-generic root=UUID=fdc5a319-6b27-4dff-8111-908b77024a87 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000aac0cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aac0d000-0x00000000aad8dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aad8e000-0x00000000aad94fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aad95000-0x00000000aad95fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aad96000-0x00000000aad96fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aad97000-0x00000000aadb7fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aadb8000-0x00000000aadc5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aadc6000-0x00000000aade7fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aade8000-0x00000000aaf12fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaf13000-0x00000000aafe7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafe8000-0x00000000aaffcfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaffd000-0x00000000aaffffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000afffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024f7fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc. N53SN/N53SN, BIOS N53SN.207 07/15/2011
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x24f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF8000000 write-back
[    0.000000]   3 base 0A8000000 mask FFC000000 write-back
[    0.000000]   4 base 0AB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 240000000 mask FF0000000 write-back
[    0.000000]   8 base 24F800000 mask FFF800000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2688MB, range: 64MB, type WB
[    0.000000] reg 4, base: 2736MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 1GB, type WB
[    0.000000] reg 7, base: 9GB, range: 256MB, type WB
[    0.000000] reg 8, base: 9464MB, range: 8MB, type UC
[    0.000000] total RAM covered: 8104M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2688MB, range: 32MB, type WB
[    0.000000] reg 4, base: 2720MB, range: 16MB, type WB
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 1GB, type WB
[    0.000000] reg 7, base: 9GB, range: 256MB, type WB
[    0.000000] reg 8, base: 9464MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xab000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xaaffd max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcc80-0x000fcc8f] mapped at [ffff8800000fcc80]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0xaaffcfff]
[    0.000000]  [mem 0x00000000-0xaadfffff] page 2M
[    0.000000]  [mem 0xaae00000-0xaaffcfff] page 4k
[    0.000000] kernel direct mapping tables up to 0xaaffcfff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x24f7fffff]
[    0.000000]  [mem 0x100000000-0x24f7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x24f7fffff @ [mem 0xaaff6000-0xaaffcfff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000aaffee18 00074 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000aaf9ad98 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20121018/tbfadt-394)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X FACS address mismatch in FADT - 0xAAFE4E40/0x00000000AAFE4D40, using 32 (20121018/tbfadt-521)
[    0.000000] ACPI: DSDT 00000000aaf86018 13833 (v01 _ASUS_ Notebook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 00000000aafe4e40 00040
[    0.000000] ACPI: APIC 00000000aaffdf18 000CC (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: DBGP 00000000aaffff18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000aafe4b18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: SLIC 00000000aaf9be18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
[    0.000000] ACPI: HPET 00000000aafe5d18 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: MCFG 00000000aafe5c98 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000aaf85018 00913 (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000aaf84018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: ASF! 00000000aafe4a18 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024f7fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x24f7fffff]
[    0.000000]   NODE_DATA [mem 0x24f7fb000-0x24f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024edfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x24f7fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0xaac0cfff]
[    0.000000]   node   0: [mem 0xaad8e000-0xaad94fff]
[    0.000000]   node   0: [mem 0xaad96000-0xaad96fff]
[    0.000000]   node   0: [mem 0xaadb8000-0xaadc5fff]
[    0.000000]   node   0: [mem 0xaade8000-0xaaf12fff]
[    0.000000]   node   0: [mem 0xaafe8000-0xaaffcfff]
[    0.000000]   node   0: [mem 0x100000000-0x24f7fffff]
[    0.000000] On node 0 totalpages: 2072817
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 142 pages reserved
[    0.000000]   DMA zone: 3776 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10854 pages used for memmap
[    0.000000]   DMA32 zone: 683773 pages, LIFO batch:31
[    0.000000]   Normal zone: 21472 pages used for memmap
[    0.000000]   Normal zone: 1352736 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000aac0d000 - 00000000aad8e000
[    0.000000] PM: Registered nosave memory: 00000000aad95000 - 00000000aad96000
[    0.000000] PM: Registered nosave memory: 00000000aad97000 - 00000000aadb8000
[    0.000000] PM: Registered nosave memory: 00000000aadc6000 - 00000000aade8000
[    0.000000] PM: Registered nosave memory: 00000000aaf13000 - 00000000aafe8000
[    0.000000] PM: Registered nosave memory: 00000000aaffd000 - 00000000ab000000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000b0000000
[    0.000000] PM: Registered nosave memory: 00000000b0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff980000
[    0.000000] PM: Registered nosave memory: 00000000ff980000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] e820: [mem 0xb0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024f400000 s84928 r8192 d21568 u131072
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2040285
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-34-generic root=UUID=fdc5a319-6b27-4dff-8111-908b77024a87 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8060100k/9691136k available (7172k kernel code, 1399868k absent, 231168k reserved, 6071k data, 1016k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=16.
[    0.000000] NR_IRQS:16640 nr_irqs:808 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1995.581 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3991.16 BogoMIPS (lpj=7982324)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.000687] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002625] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003439] Mount-cache hash table entries: 256
[    0.003629] Initializing cgroup subsys cpuacct
[    0.003632] Initializing cgroup subsys memory
[    0.003639] Initializing cgroup subsys devices
[    0.003640] Initializing cgroup subsys freezer
[    0.003642] Initializing cgroup subsys blkio
[    0.003644] Initializing cgroup subsys perf_event
[    0.003646] Initializing cgroup subsys hugetlb
[    0.003673] CPU: Physical Processor ID: 0
[    0.003675] CPU: Processor Core ID: 0
[    0.003680] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003680] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003683] mce: CPU supports 9 MCE banks
[    0.003699] CPU0: Thermal monitoring enabled (TM1)
[    0.003709] process: using mwait in idle threads
[    0.003713] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.003713] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003713] tlb_flushall_shift: 5
[    0.003866] Freeing SMP alternatives: 24k freed
[    0.006912] ACPI: Core revision 20121018
[    0.176649] ftrace: allocating 29364 entries in 115 pages
[    0.194180] Switched APIC routing to physical flat.
[    0.194606] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.234281] smpboot: CPU0: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz (fam: 06, model: 2a, stepping: 07)
[    0.234290] TSC deadline timer enabled
[    0.234294] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.234301] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.234303] ... version:                3
[    0.234304] ... bit width:              48
[    0.234306] ... generic registers:      4
[    0.234307] ... value mask:             0000ffffffffffff
[    0.234308] ... max period:             000000007fffffff
[    0.234309] ... fixed-purpose events:   3
[    0.234311] ... event mask:             000000070000000f
[    0.248941] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.235664] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7
[    0.328354] Brought up 8 CPUs
[    0.328359] smpboot: Total of 8 processors activated (31929.29 BogoMIPS)
[    0.337398] devtmpfs: initialized
[    0.338551] EVM: security.selinux
[    0.338552] EVM: security.SMACK64
[    0.338554] EVM: security.capability
[    0.338598] PM: Registering ACPI NVS region [mem 0xaaf13000-0xaafe7fff] (872448 bytes)
[    0.339470] regulator-dummy: no parameters
[    0.339527] NET: Registered protocol family 16
[    0.339681] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.339683] ACPI: bus type pci registered
[    0.339751] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.339754] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.349727] PCI: Using configuration type 1 for base access
[    0.350800] bio: create slab <bio-0> at 0
[    0.350892] ACPI: Added _OSI(Module Device)
[    0.350894] ACPI: Added _OSI(Processor Device)
[    0.350895] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.350897] ACPI: Added _OSI(Processor Aggregator Device)
[    0.353556] ACPI: EC: EC description table is found, configuring boot EC
[    0.353561] ACPI: EC: Look up EC in DSDT
[    0.356400] ACPI: Executed 1 blocks of module-level executable AML code
[    0.360348] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.469918] ACPI: SSDT 00000000aadca798 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.470588] ACPI: Dynamic OEM Table Load:
[    0.470591] ACPI: SSDT           (null) 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.470924] ACPI: SSDT 00000000aadcba98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.471627] ACPI: Dynamic OEM Table Load:
[    0.471630] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.471813] ACPI: SSDT 00000000aadc9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.472481] ACPI: Dynamic OEM Table Load:
[    0.472484] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.473827] ACPI: Interpreter enabled
[    0.473832] ACPI: (supports S0 S3 S4 S5)
[    0.473854] ACPI: Using IOAPIC for interrupt routing
[    0.583379] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.583557] ACPI: No dock devices found.
[    0.583562] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.583804] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.583807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.584422] PCI host bridge to bus 0000:00
[    0.584426] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.584428] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.584430] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.584433] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.584435] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.584437] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.584439] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.584441] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.584443] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.584445] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.584447] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xfeafffff]
[    0.584449] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.584459] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.584502] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.584538] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.584561] pci 0000:00:02.0: [8086:0116] type 00 class 0x030000
[    0.584573] pci 0000:00:02.0: reg 10: [mem 0xdc400000-0xdc7fffff 64bit]
[    0.584581] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.584586] pci 0000:00:02.0: reg 20: [io  0xe000-0xe03f]
[    0.584647] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.584673] pci 0000:00:16.0: reg 10: [mem 0xdf00b000-0xdf00b00f 64bit]
[    0.584756] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.584795] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.584819] pci 0000:00:1a.0: reg 10: [mem 0xdf008000-0xdf0083ff]
[    0.584917] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.584947] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.584965] pci 0000:00:1b.0: reg 10: [mem 0xdf000000-0xdf003fff 64bit]
[    0.585040] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.585066] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.585161] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.585193] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.585279] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.585311] pci 0000:00:1c.3: [8086:1c16] type 01 class 0x060400
[    0.585399] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.585430] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.585516] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.585553] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.585577] pci 0000:00:1d.0: reg 10: [mem 0xdf007000-0xdf0073ff]
[    0.585675] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.585705] pci 0000:00:1f.0: [8086:1c49] type 00 class 0x060100
[    0.585839] pci 0000:00:1f.2: [8086:1c03] type 00 class 0x010601
[    0.585861] pci 0000:00:1f.2: reg 10: [io  0xe0b0-0xe0b7]
[    0.585870] pci 0000:00:1f.2: reg 14: [io  0xe0a0-0xe0a3]
[    0.585879] pci 0000:00:1f.2: reg 18: [io  0xe090-0xe097]
[    0.585889] pci 0000:00:1f.2: reg 1c: [io  0xe080-0xe083]
[    0.585898] pci 0000:00:1f.2: reg 20: [io  0xe060-0xe07f]
[    0.585908] pci 0000:00:1f.2: reg 24: [mem 0xdf006000-0xdf0067ff]
[    0.585959] pci 0000:00:1f.2: PME# supported from D3hot
[    0.585980] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.585998] pci 0000:00:1f.3: reg 10: [mem 0xdf005000-0xdf0050ff 64bit]
[    0.586021] pci 0000:00:1f.3: reg 20: [io  0xe040-0xe05f]
[    0.586092] pci 0000:01:00.0: [10de:0df6] type 00 class 0x030000
[    0.586105] pci 0000:01:00.0: reg 10: [mem 0xdb000000-0xdbffffff]
[    0.586119] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.586133] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.586142] pci 0000:01:00.0: reg 24: [io  0xd000-0xd07f]
[    0.586152] pci 0000:01:00.0: reg 30: [mem 0xdc000000-0xdc07ffff pref]
[    0.597189] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.597197] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.597205] pci 0000:00:01.0:   bridge window [mem 0xdb000000-0xdc0fffff]
[    0.597215] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.597310] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.597315] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.597320] pci 0000:00:1c.0:   bridge window [mem 0xde600000-0xdeffffff]
[    0.597327] pci 0000:00:1c.0:   bridge window [mem 0xd4200000-0xd4bfffff 64bit pref]
[    0.597398] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.597428] pci 0000:03:00.0: reg 10: [mem 0xddc00000-0xddc0ffff 64bit]
[    0.597565] pci 0000:03:00.0: supports D1
[    0.597568] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.609199] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.609209] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.609219] pci 0000:00:1c.1:   bridge window [mem 0xddc00000-0xde5fffff]
[    0.609233] pci 0000:00:1c.1:   bridge window [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.609348] pci 0000:04:00.0: [1b73:1000] type 00 class 0x0c0330
[    0.609371] pci 0000:04:00.0: reg 10: [mem 0xdd200000-0xdd20ffff]
[    0.609526] pci 0000:04:00.0: PME# supported from D0 D3hot
[    0.621205] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.621214] pci 0000:00:1c.3:   bridge window [io  0xa000-0xafff]
[    0.621224] pci 0000:00:1c.3:   bridge window [mem 0xdd200000-0xddbfffff]
[    0.621237] pci 0000:00:1c.3:   bridge window [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.621407] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    0.621477] pci 0000:05:00.0: reg 10: [io  0x9000-0x90ff]
[    0.621594] pci 0000:05:00.0: reg 18: [mem 0xd2104000-0xd2104fff 64bit pref]
[    0.621670] pci 0000:05:00.0: reg 20: [mem 0xd2100000-0xd2103fff 64bit pref]
[    0.622000] pci 0000:05:00.0: supports D1 D2
[    0.622002] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.633236] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    0.633246] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.633256] pci 0000:00:1c.5:   bridge window [mem 0xdc800000-0xdd1fffff]
[    0.633270] pci 0000:00:1c.5:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.633327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.633414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.633449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.633489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.633526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.633630]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.634051]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.634918] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.634968] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 12)
[    0.635014] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    0.635059] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    0.635105] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.635152] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.635197] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    0.635243] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    0.635342] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.635347] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.635349] vgaarb: loaded
[    0.635350] vgaarb: bridge control possible 0000:01:00.0
[    0.635352] vgaarb: no bridge control possible 0000:00:02.0
[    0.635519] SCSI subsystem initialized
[    0.635521] ACPI: bus type scsi registered
[    0.635568] libata version 3.00 loaded.
[    0.635586] ACPI: bus type usb registered
[    0.635602] usbcore: registered new interface driver usbfs
[    0.635610] usbcore: registered new interface driver hub
[    0.635630] usbcore: registered new device driver usb
[    0.635707] PCI: Using ACPI for IRQ routing
[    0.637292] PCI: pci_cache_line_size set to 64 bytes
[    0.637370] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.637372] e820: reserve RAM buffer [mem 0xaac0d000-0xabffffff]
[    0.637375] e820: reserve RAM buffer [mem 0xaad95000-0xabffffff]
[    0.637377] e820: reserve RAM buffer [mem 0xaad97000-0xabffffff]
[    0.637379] e820: reserve RAM buffer [mem 0xaadc6000-0xabffffff]
[    0.637381] e820: reserve RAM buffer [mem 0xaaf13000-0xabffffff]
[    0.637383] e820: reserve RAM buffer [mem 0xaaffd000-0xabffffff]
[    0.637385] e820: reserve RAM buffer [mem 0x24f800000-0x24fffffff]
[    0.637469] NetLabel: Initializing
[    0.637471] NetLabel:  domain hash size = 128
[    0.637472] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.637482] NetLabel:  unlabeled traffic allowed by default
[    0.637532] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.637539] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.639549] Switching to clocksource hpet
[    0.644929] AppArmor: AppArmor Filesystem Enabled
[    0.644954] pnp: PnP ACPI init
[    0.644966] ACPI: bus type pnp registered
[    0.695684] pnp 00:00: [dma 4]
[    0.695707] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.695730] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.695834] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.695868] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.695914] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.695917] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.695920] system 00:04: [io  0xffff] has been reserved
[    0.695922] system 00:04: [io  0xffff] has been reserved
[    0.695924] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.695927] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.695929] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.695931] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.695934] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.695962] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.696004] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.696007] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.696038] system 00:07: [io  0x0240-0x0259] has been reserved
[    0.696041] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.696097] pnp 00:08: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.696133] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.696390] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.696393] system 00:0a: [mem 0xfed10000-0xfed17fff] could not be reserved
[    0.696396] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.696398] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.696401] system 00:0a: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.696403] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.696406] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.696408] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.696410] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.696413] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.696416] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.696491] system 00:0b: [mem 0xd4c00000-0xd4c00fff] has been reserved
[    0.696494] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.696636] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.696638] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    0.696641] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.696665] pnp: PnP ACPI: found 13 devices
[    0.696666] ACPI: ACPI bus type pnp unregistered
[    0.702896] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.702899] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.702903] pci 0000:00:01.0:   bridge window [mem 0xdb000000-0xdc0fffff]
[    0.702906] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.702910] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.702914] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.702920] pci 0000:00:1c.0:   bridge window [mem 0xde600000-0xdeffffff]
[    0.702925] pci 0000:00:1c.0:   bridge window [mem 0xd4200000-0xd4bfffff 64bit pref]
[    0.702933] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.702936] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.702942] pci 0000:00:1c.1:   bridge window [mem 0xddc00000-0xde5fffff]
[    0.702947] pci 0000:00:1c.1:   bridge window [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.702954] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.702958] pci 0000:00:1c.3:   bridge window [io  0xa000-0xafff]
[    0.702964] pci 0000:00:1c.3:   bridge window [mem 0xdd200000-0xddbfffff]
[    0.702969] pci 0000:00:1c.3:   bridge window [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.702976] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    0.702980] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.702986] pci 0000:00:1c.5:   bridge window [mem 0xdc800000-0xdd1fffff]
[    0.702991] pci 0000:00:1c.5:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.703036] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.703038] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.703041] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.703043] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.703045] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.703047] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.703049] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.703051] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.703053] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.703055] pci_bus 0000:00: resource 13 [mem 0xb0000000-0xfeafffff]
[    0.703057] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    0.703059] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.703062] pci_bus 0000:01: resource 1 [mem 0xdb000000-0xdc0fffff]
[    0.703064] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.703066] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.703068] pci_bus 0000:02: resource 1 [mem 0xde600000-0xdeffffff]
[    0.703070] pci_bus 0000:02: resource 2 [mem 0xd4200000-0xd4bfffff 64bit pref]
[    0.703072] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.703075] pci_bus 0000:03: resource 1 [mem 0xddc00000-0xde5fffff]
[    0.703077] pci_bus 0000:03: resource 2 [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.703079] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.703081] pci_bus 0000:04: resource 1 [mem 0xdd200000-0xddbfffff]
[    0.703083] pci_bus 0000:04: resource 2 [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.703085] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    0.703087] pci_bus 0000:05: resource 1 [mem 0xdc800000-0xdd1fffff]
[    0.703089] pci_bus 0000:05: resource 2 [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.703121] NET: Registered protocol family 2
[    0.703316] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.703562] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.703698] TCP: Hash tables configured (established 65536 bind 65536)
[    0.703718] TCP: reno registered
[    0.703732] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.703768] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.703850] NET: Registered protocol family 1
[    0.703862] pci 0000:00:02.0: Boot video device
[    0.951650] PCI: CLS 64 bytes, default 64
[    0.951690] Trying to unpack rootfs image as initramfs...
[    1.250311] Freeing initrd memory: 15832k freed
[    1.252497] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.252503] software IO TLB [mem 0xa6c0d000-0xaac0d000] (64MB) mapped at [ffff8800a6c0d000-ffff8800aac0cfff]
[    1.253020] Initialise module verification
[    1.253068] audit: initializing netlink socket (disabled)
[    1.253078] type=2000 audit(1386489581.084:1): initialized
[    1.288326] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.289842] VFS: Disk quotas dquot_6.5.2
[    1.289888] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.290350] fuse init (API version 7.20)
[    1.290422] msgmni has been set to 15773
[    1.290788] Key type asymmetric registered
[    1.290790] Asymmetric key parser 'x509' registered
[    1.290821] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.290848] io scheduler noop registered
[    1.290850] io scheduler deadline registered (default)
[    1.290855] io scheduler cfq registered
[    1.290962] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.291057] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.291162] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.291268] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.291389] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    1.291472] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.291474] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.291477] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.291498] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.291503] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.291521] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.291523] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.291528] pcie_pme 0000:00:1c.1cie01: service driver pcie_pme loaded
[    1.291546] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.291548] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.291553] pcie_pme 0000:00:1c.3cie01: service driver pcie_pme loaded
[    1.291571] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    1.291573] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    1.291578] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    1.291590] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.291604] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.291644] intel_idle: MWAIT substates: 0x21120
[    1.291645] intel_idle: v0.4 model 0x2A
[    1.291646] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.291842] ACPI: AC Adapter [AC0] (on-line)
[    1.291942] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.307558] ACPI: Lid Switch [LID]
[    1.307595] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.307600] ACPI: Sleep Button [SLPB]
[    1.307629] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.307632] ACPI: Power Button [PWRF]
[    1.307705] ACPI: Requesting acpi_cpufreq
[    1.413144] thermal LNXTHERM:00: registered as thermal_zone0
[    1.413148] ACPI: Thermal Zone [THRM] (51 C)
[    1.413185] GHES: HEST is not enabled!
[    1.413250] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.414584] Linux agpgart interface v0.103
[    1.416801] brd: module loaded
[    1.417919] loop: module loaded
[    1.418220] libphy: Fixed MDIO Bus: probed
[    1.418277] tun: Universal TUN/TAP device driver, 1.6
[    1.418278] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.418313] PPP generic driver version 2.4.2
[    1.418359] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.418360] ehci-pci: EHCI PCI platform driver
[    1.418404] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.418408] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.418414] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.418430] ehci-pci 0000:00:1a.0: debug port 2
[    1.422322] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.422387] ehci-pci 0000:00:1a.0: irq 16, io mem 0xdf008000
[    1.425821] ACPI: Battery Slot [BAT0] (battery present)
[    1.431344] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.431399] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.431405] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.431410] usb usb1: Product: EHCI Host Controller
[    1.431415] usb usb1: Manufacturer: Linux 3.8.0-34-generic ehci_hcd
[    1.431420] usb usb1: SerialNumber: 0000:00:1a.0
[    1.431526] hub 1-0:1.0: USB hub found
[    1.431530] hub 1-0:1.0: 2 ports detected
[    1.431618] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.431622] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.431626] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.431639] ehci-pci 0000:00:1d.0: debug port 2
[    1.435532] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.435548] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdf007000
[    1.447335] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.447378] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.447384] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.447389] usb usb2: Product: EHCI Host Controller
[    1.447394] usb usb2: Manufacturer: Linux 3.8.0-34-generic ehci_hcd
[    1.447398] usb usb2: SerialNumber: 0000:00:1d.0
[    1.447501] hub 2-0:1.0: USB hub found
[    1.447504] hub 2-0:1.0: 2 ports detected
[    1.447573] ehci-platform: EHCI generic platform driver
[    1.447580] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.447592] uhci_hcd: USB Universal Host Controller Interface driver
[    1.447642] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.447647] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    1.588981] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.588984] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.588986] usb usb3: Product: xHCI Host Controller
[    1.588988] usb usb3: Manufacturer: Linux 3.8.0-34-generic xhci_hcd
[    1.588990] usb usb3: SerialNumber: 0000:04:00.0
[    1.589050] xHCI xhci_add_endpoint called for root hub
[    1.589052] xHCI xhci_check_bandwidth called for root hub
[    1.589071] hub 3-0:1.0: USB hub found
[    1.589076] hub 3-0:1.0: 1 port detected
[    1.589122] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.589126] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    1.589154] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.589157] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.589158] usb usb4: Product: xHCI Host Controller
[    1.589161] usb usb4: Manufacturer: Linux 3.8.0-34-generic xhci_hcd
[    1.589162] usb usb4: SerialNumber: 0000:04:00.0
[    1.589215] xHCI xhci_add_endpoint called for root hub
[    1.589217] xHCI xhci_check_bandwidth called for root hub
[    1.589233] hub 4-0:1.0: USB hub found
[    1.589239] hub 4-0:1.0: 1 port detected
[    1.589372] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.591031] i8042: Detected active multiplexing controller, rev 1.1
[    1.591830] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.591835] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.591856] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.591874] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.591888] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.591998] mousedev: PS/2 mouse device common for all mice
[    1.592137] rtc_cmos 00:05: RTC can wake from S4
[    1.592262] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.592290] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.592374] device-mapper: uevent: version 1.0.3
[    1.592436] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.592580] cpuidle: using governor ladder
[    1.592770] cpuidle: using governor menu
[    1.592778] ledtrig-cpu: registered to indicate activity on CPUs
[    1.592780] EFI Variables Facility v0.08 2004-May-17
[    1.592936] ashmem: initialized
[    1.593050] TCP: cubic registered
[    1.593136] NET: Registered protocol family 10
[    1.593304] NET: Registered protocol family 17
[    1.593327] Key type dns_resolver registered
[    1.593585] Loading module verification certificates
[    1.594655] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 253c4f779a04eefe395aecbd137448018b69410b'
[    1.594665] registered taskstats version 1
[    1.596864] Key type trusted registered
[    1.598665] Key type encrypted registered
[    1.600999] rtc_cmos 00:05: setting system clock to 2013-12-08 07:59:41 UTC (1386489581)
[    1.602545] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.602546] EDD information not available.
[    1.604016] Freeing unused kernel memory: 1016k freed
[    1.604129] Write protecting the kernel read-only data: 12288k
[    1.606855] Freeing unused kernel memory: 1008k freed
[    1.609445] Freeing unused kernel memory: 1008k freed
[    1.623363] udevd[130]: starting version 175
[    1.627285] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.646228] Disabling lock debugging due to kernel taint
[    1.646635] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.646853] r8169 0000:05:00.0: irq 45 for MSI/MSI-X
[    1.647047] r8169 0000:05:00.0 eth0: RTL8168e/8111e at 0xffffc90004e88000, 14:da:e9:c1:9c:82, XID 0c200000 IRQ 45
[    1.647051] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.647582] ahci 0000:00:1f.2: version 3.0
[    1.647641] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.663327] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.663347] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.663362] ahci 0000:00:1f.2: setting latency timer to 64
[    1.671692] scsi0 : ahci
[    1.671763] scsi1 : ahci
[    1.671811] scsi2 : ahci
[    1.671857] scsi3 : ahci
[    1.671904] scsi4 : ahci
[    1.671949] scsi5 : ahci
[    1.672017] ata1: SATA max UDMA/133 abar m2048@0xdf006000 port 0xdf006100 irq 46
[    1.672019] ata2: DUMMY
[    1.672022] ata3: SATA max UDMA/133 abar m2048@0xdf006000 port 0xdf006200 irq 46
[    1.672023] ata4: DUMMY
[    1.672024] ata5: DUMMY
[    1.672025] ata6: DUMMY
[    1.799277] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.931791] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.931800] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.932198] hub 1-1:1.0: USB hub found
[    1.932291] hub 1-1:1.0: 6 ports detected
[    1.991255] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.991300] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.994027] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.994041] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.994737] ata3.00: ATAPI: Slimtype BD  E  DS4E1S, EA2B, max UDMA/100
[    1.996907] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.996919] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.997589] ata3.00: configured for UDMA/100
[    2.001950] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.010406] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.010419] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.028057] ata1.00: ATA-8: ST9750420AS, 0002SDM1, max UDMA/133
[    2.028068] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.043238] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.071413] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.071670] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.071681] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.072523] ata1.00: configured for UDMA/133
[    2.072832] scsi 0:0:0:0: Direct-Access     ATA      ST9750420AS      0002 PQ: 0 ANSI: 5
[    2.072993] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.072997] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.073033] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.073044] sd 0:0:0:0: [sda] Write Protect is off
[    2.073047] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.073067] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.076279] scsi 2:0:0:0: CD-ROM            Slimtype BD  E  DS4E1S    EA2B PQ: 0 ANSI: 5
[    2.080724] sr0: scsi3-mmc drive: 24x/1x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    2.080733] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.080948] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.081089] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.127433]  sda: sda1 sda2 < sda5 >
[    2.127944] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.175580] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.175590] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.175962] hub 2-1:1.0: USB hub found
[    2.176065] hub 2-1:1.0: 6 ports detected
[    2.247203] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.251103] tsc: Refined TSC clocksource calibration: 1995.466 MHz
[    2.251116] Switching to clocksource tsc
[    2.339955] usb 1-1.1: New USB device found, idVendor=13d3, idProduct=3304
[    2.339967] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.411121] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[    2.541577] usb 1-1.2: New USB device found, idVendor=13d3, idProduct=5122
[    2.541585] usb 1-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.541591] usb 1-1.2: Product: USB2.0 UVC 2M WebCam
[    2.541596] usb 1-1.2: Manufacturer: USB2.0 UVC 2M WebCam
[    2.541601] usb 1-1.2: SerialNumber: USB2.0 UVC 2M WebCam
[    2.979187] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.979190] EXT4-fs (sda1): write access will be enabled during recovery
[    5.288464] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.288472] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 12058642
[    5.288519] EXT4-fs (sda1): 1 orphan inode deleted
[    5.288520] EXT4-fs (sda1): recovery complete
[    5.565404] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.641770] init: ureadahead main process (319) terminated with status 5
[    7.483398] Adding 8289276k swap on /dev/sda5.  Priority:-1 extents:1 across:8289276k 
[    8.328208] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.735082] udevd[502]: starting version 175
[    9.424776] lp: driver loaded but no devices found
[    9.643754] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20121018/utaddress-251)
[    9.643762] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 2 (20121018/utaddress-251)
[    9.643768] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.643771] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.643774] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.643777] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.643778] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.643780] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.643783] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.643784] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.643786] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.643789] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.643790] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.934238] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x1a
[   10.009033] wmi: Mapper loaded
[   10.021697] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x1a
[   10.022656] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x1a
[   10.023512] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x1a
[   10.024416] microcode: CPU4 sig=0x206a7, pf=0x10, revision=0x1a
[   10.025335] microcode: CPU5 sig=0x206a7, pf=0x10, revision=0x1a
[   10.026210] microcode: CPU6 sig=0x206a7, pf=0x10, revision=0x1a
[   10.027131] microcode: CPU7 sig=0x206a7, pf=0x10, revision=0x1a
[   10.028036] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.035796] asus_wmi: ASUS WMI generic driver loaded
[   10.052987] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.6
[   10.053039] asus_wmi: SFUN value: 0x1a0877<6>[   10.053458] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[   10.117999] asus_wmi: Backlight controlled by ACPI video driver
[   10.172453] mei 0000:00:16.0: setting latency timer to 64
[   10.172512] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[   10.219450] Bluetooth: Core ver 2.16
[   10.219465] NET: Registered protocol family 31
[   10.219467] Bluetooth: HCI device and connection manager initialized
[   10.219472] Bluetooth: HCI socket layer initialized
[   10.219474] Bluetooth: L2CAP socket layer initialized
[   10.219478] Bluetooth: SCO socket layer initialized
[   10.270518] [drm] Initialized drm 1.1.0 20060810
[   10.306544] Linux video capture interface: v2.00
[   10.395482] cfg80211: Calling CRDA to update world regulatory domain
[   10.708955] usbcore: registered new interface driver btusb
[   11.023500] uvcvideo: Found UVC 1.00 device USB2.0 UVC 2M WebCam (13d3:5122)
[   11.034626] input: USB2.0 UVC 2M WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[   11.034679] usbcore: registered new interface driver uvcvideo
[   11.034680] USB Video Class driver (1.1.1)
[   11.100046] [drm] Memory usable by graphics device = 2048M
[   11.100053] i915 0000:00:02.0: setting latency timer to 64
[   11.137499] i915 0000:00:02.0: irq 48 for MSI/MSI-X
[   11.137506] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.137507] [drm] Driver supports precise vblank timestamp query.
[   11.137677] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.137679] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   11.200997] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[   11.203126] usbcore: registered new interface driver ath3k
[   11.229409] psmouse serio4: elantech: Synaptics capabilities query result 0x78, 0x14, 0x0b.
[   11.337436] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input6
[   11.359740] fbcon: inteldrmfb (fb0) is primary device
[   11.404449] usb 1-1.1: USB disconnect, device number 3
[   11.547552] ath: EEPROM regdomain: 0x60
[   11.547553] ath: EEPROM indicates we should expect a direct regpair map
[   11.547554] ath: Country alpha2 being used: 00
[   11.547554] ath: Regpair used: 0x60
[   11.591308] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.591552] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90005de0000, irq=17
[   11.720852] type=1400 audit(1386489591.618:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=787 comm="apparmor_parser"
[   11.720872] type=1400 audit(1386489591.618:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=712 comm="apparmor_parser"
[   11.720890] type=1400 audit(1386489591.618:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=707 comm="apparmor_parser"
[   11.721154] type=1400 audit(1386489591.618:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=787 comm="apparmor_parser"
[   11.721172] type=1400 audit(1386489591.618:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
[   11.721191] type=1400 audit(1386489591.618:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=707 comm="apparmor_parser"
[   11.721323] type=1400 audit(1386489591.618:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=787 comm="apparmor_parser"
[   11.721342] type=1400 audit(1386489591.618:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=712 comm="apparmor_parser"
[   11.721360] type=1400 audit(1386489591.618:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=707 comm="apparmor_parser"
[   11.860182] usb 1-1.1: new full-speed USB device number 5 using ehci-pci
[   11.952908] usb 1-1.1: New USB device found, idVendor=0cf3, idProduct=3005
[   11.952913] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   12.067943] Console: switching to colour frame buffer device 240x67
[   12.071756] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.071758] i915 0000:00:02.0: registered panic notifier
[   12.072561] ACPI Warning: _BQC returned an invalid level (20121018/video-534)
[   12.072848] acpi device:03: registered as cooling_device8
[   12.072866] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   12.072900] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input7
[   12.077079] ACPI Warning: _BQC returned an invalid level (20121018/video-534)
[   12.077370] acpi device:47: registered as cooling_device9
[   12.077674] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.077708] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   12.077781] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.077896] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   12.294864] nvidia: module license 'NVIDIA' taints kernel.
[   12.300780] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   12.300794] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   12.300956] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[   12.300962] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[   12.485272] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.485334] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.485381] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.936057] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   13.011045] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.267899] init: failsafe main process (892) killed by TERM signal
[   15.010581] ppdev: user-space parallel port driver
[   15.292991] Bluetooth: RFCOMM TTY layer initialized
[   15.293001] Bluetooth: RFCOMM socket layer initialized
[   15.293003] Bluetooth: RFCOMM ver 1.11
[   15.399489] type=1400 audit(1386489595.302:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=976 comm="apparmor_parser"
[   15.425956] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.425959] Bluetooth: BNEP filters: protocol multicast
[   15.425966] Bluetooth: BNEP socket layer initialized
[   17.290798] audit_printk_skb: 3 callbacks suppressed
[   17.290803] type=1400 audit(1386489597.190:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1029 comm="apparmor_parser"
[   17.291209] type=1400 audit(1386489597.190:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1029 comm="apparmor_parser"
[   17.291439] type=1400 audit(1386489597.190:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1029 comm="apparmor_parser"
[   17.291813] type=1400 audit(1386489597.190:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1033 comm="apparmor_parser"
[   17.292171] type=1400 audit(1386489597.190:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1033 comm="apparmor_parser"
[   17.347909] type=1400 audit(1386489597.246:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1028 comm="apparmor_parser"
[   17.348166] type=1400 audit(1386489597.246:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1028 comm="apparmor_parser"
[   17.365621] type=1400 audit(1386489597.266:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1032 comm="apparmor_parser"
[   17.365970] type=1400 audit(1386489597.266:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1032 comm="apparmor_parser"
[   17.394465] type=1400 audit(1386489597.294:22): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1035 comm="apparmor_parser"
[   18.103936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.106998] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by mörgæs on 2013-12-09
Hi, welcome to the fora.
The general approach to troubleshooting an unexplainable problem like yours is often: How does it work in a fresh install of 13.10?

---

