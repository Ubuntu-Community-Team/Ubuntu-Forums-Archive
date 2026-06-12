---
title: "Srange boot behaviour Ubuntu on iMac"
date: 2012-08-13
forum: Apple Hardware Users
---

### Post by LtTuvok on 2012-08-13
I have Ubuntu 12.04 installed on my Intel iMac. Except the keyboard everything is working fine out of the box. There is however one thing I like to be solved, that is strange startup behaviour. When I start the iMac Ubuntu will startup and failed to startup turn by turn. When it starts I see a underscore blinker for a few seconds afterwards the graphical startup screens is displayed and Ubuntu loads. The next time I start the iMac I only get a black screen. After I restart the iMac Ubuntu loads again. It is on a turn by turn basis. Strange is it not?

Does anyone know what to do?

---

### Post by 2F4U on 2012-08-13
I don't have an iMac but on my MacBook 4,1 Ubuntu 12.04 runs without problems. What is your hardware configuration? The black screen during startup may be an indication of problems with the graphics card. What is the graphics card and what driver do you use?
Did you take a look into the system log file after a failed startup? It may contain hints on what exactly caused the failure.

---

### Post by LtTuvok on 2012-08-13
Thank you for your reply.

I have a Radeon HD 4670 with 256 MB. I use the hardware driver that is available from the hardware installation tool in system settings. I will look into the logfiles and post some rows in this thread. 

What is odd, is that it works well after a restart from a failed start. So for every new startup the cycle is: working - not working - working - not working and so on.

---

### Post by LtTuvok on 2012-08-13
Here is my logfile in the startup that failed.

Aug 13 18:50:21 MARS kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 13 18:50:21 MARS rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="898" x-info="http://www.rsyslog.com"] start
Aug 13 18:50:21 MARS rsyslogd: rsyslogd's groupid changed to 103
Aug 13 18:50:21 MARS rsyslogd: rsyslogd's userid changed to 101
Aug 13 18:50:21 MARS rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 13 18:50:21 MARS kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 13 18:50:21 MARS kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 13 18:50:21 MARS kernel: [    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
Aug 13 18:50:21 MARS kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=a964a96b-e720-470e-94a6-e7016807e850 ro quiet splash vt.handoff=7
Aug 13 18:50:21 MARS kernel: [    0.000000] KERNEL supported cpus:
Aug 13 18:50:21 MARS kernel: [    0.000000]   Intel GenuineIntel
Aug 13 18:50:21 MARS kernel: [    0.000000]   AMD AuthenticAMD
Aug 13 18:50:21 MARS kernel: [    0.000000]   Centaur CentaurHauls
Aug 13 18:50:21 MARS kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000be7bf000 (usable)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000be7bf000 - 00000000be7c3000 (ACPI NVS)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000be7c3000 - 00000000be822000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000be822000 - 00000000bea23000 (ACPI NVS)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bea23000 - 00000000bfec3000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfec3000 - 00000000bfec5000 (ACPI NVS)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfec5000 - 00000000bfec6000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfec6000 - 00000000bfec9000 (ACPI NVS)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfec9000 - 00000000bfecd000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfecd000 - 00000000bfedf000 (ACPI NVS)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000bfef9000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000d0400000 - 00000000d0401000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000340000000 (usable)
Aug 13 18:50:21 MARS kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 13 18:50:21 MARS kernel: [    0.000000] DMI 2.4 present.
Aug 13 18:50:21 MARS kernel: [    0.000000] DMI: Apple Inc. iMac10,1/Mac-F2268CC8, BIOS    IM101.88Z.00CC.B00.0909031926 09/03/09
Aug 13 18:50:21 MARS kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 13 18:50:21 MARS kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 13 18:50:21 MARS kernel: [    0.000000] No AGP bridge found
Aug 13 18:50:21 MARS kernel: [    0.000000] last_pfn = 0x340000 max_arch_pfn = 0x400000000
Aug 13 18:50:21 MARS kernel: [    0.000000] MTRR default type: write-back
Aug 13 18:50:21 MARS kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 13 18:50:21 MARS kernel: [    0.000000]   00000-9FFFF write-back
Aug 13 18:50:21 MARS kernel: [    0.000000]   A0000-FFFFF uncachable
Aug 13 18:50:21 MARS kernel: [    0.000000] MTRR variable ranges enabled:
Aug 13 18:50:21 MARS kernel: [    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
Aug 13 18:50:21 MARS kernel: [    0.000000]   1 base 0BFF00000 mask FFFF00000 uncachable
Aug 13 18:50:21 MARS kernel: [    0.000000]   2 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000]   3 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000]   4 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000]   5 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000]   6 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000]   7 disabled
Aug 13 18:50:21 MARS kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 13 18:50:21 MARS kernel: [    0.000000] last_pfn = 0xbe7bf max_arch_pfn = 0x400000000
Aug 13 18:50:21 MARS kernel: [    0.000000] initial memory mapped : 0 - 20000000
Aug 13 18:50:21 MARS kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Aug 13 18:50:21 MARS kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000be7bf000
Aug 13 18:50:21 MARS kernel: [    0.000000]  0000000000 - 00be600000 page 2M
Aug 13 18:50:21 MARS kernel: [    0.000000]  00be600000 - 00be7bf000 page 4k
Aug 13 18:50:21 MARS kernel: [    0.000000] kernel direct mapping tables up to be7bf000 @ 1fffb000-20000000
Aug 13 18:50:21 MARS kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000340000000
Aug 13 18:50:21 MARS kernel: [    0.000000]  0100000000 - 0340000000 page 2M
Aug 13 18:50:21 MARS kernel: [    0.000000] kernel direct mapping tables up to 340000000 @ be7b1000-be7bf000
Aug 13 18:50:21 MARS kernel: [    0.000000] RAMDISK: 364ea000 - 3726d000
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: XSDT 00000000bfeee1c0 0007C (v01 APPLE   Apple00 000000CC      01000013)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: FACP 00000000bfeec000 000F4 (v04 APPLE   Apple00 000000CC Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: DSDT 00000000bfedf000 05EB9 (v01 APPLE      iMac 00100001 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: FACS 00000000bfecd000 00040
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: HPET 00000000bfeeb000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: APIC 00000000bfeea000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: APIC 00000000bfee9000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: MCFG 00000000bfee8000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: ASF! 00000000bfee7000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: SBST 00000000bfee6000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: ECDT 00000000bfee5000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: SSDT 00000000bfec5000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: SSDT 00000000bfecc000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: SSDT 00000000bfecb000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 13 18:50:21 MARS kernel: [    0.000000] No NUMA configuration found
Aug 13 18:50:21 MARS kernel: [    0.000000] Faking a node at 0000000000000000-0000000340000000
Aug 13 18:50:21 MARS kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000340000000
Aug 13 18:50:21 MARS kernel: [    0.000000]   NODE_DATA [000000033fffb000 - 000000033fffffff]
Aug 13 18:50:21 MARS kernel: [    0.000000]  [ffffea0000000000-ffffea000cffffff] PMD -> [ffff880333600000-ffff88033f5fffff] on node 0
Aug 13 18:50:21 MARS kernel: [    0.000000] Zone PFN ranges:
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Aug 13 18:50:21 MARS kernel: [    0.000000]   Normal   0x00100000 -> 0x00340000
Aug 13 18:50:21 MARS kernel: [    0.000000] Movable zone start PFN for each node
Aug 13 18:50:21 MARS kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug 13 18:50:21 MARS kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 13 18:50:21 MARS kernel: [    0.000000]     0: 0x00000100 -> 0x000be7bf
Aug 13 18:50:21 MARS kernel: [    0.000000]     0: 0x00100000 -> 0x00340000
Aug 13 18:50:21 MARS kernel: [    0.000000] On node 0 totalpages: 3139406
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA zone: 5 pages reserved
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Aug 13 18:50:21 MARS kernel: [    0.000000]   DMA32 zone: 759807 pages, LIFO batch:31
Aug 13 18:50:21 MARS kernel: [    0.000000]   Normal zone: 36864 pages used for memmap
Aug 13 18:50:21 MARS kernel: [    0.000000]   Normal zone: 2322432 pages, LIFO batch:31
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug 13 18:50:21 MARS kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 13 18:50:21 MARS kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 13 18:50:21 MARS kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Aug 13 18:50:21 MARS kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 13 18:50:21 MARS kernel: [    0.000000] nr_irqs_gsi: 40
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000be7bf000 - 00000000be7c3000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000be7c3000 - 00000000be822000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000be822000 - 00000000bea23000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bea23000 - 00000000bfec3000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfec3000 - 00000000bfec5000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfec5000 - 00000000bfec6000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfec6000 - 00000000bfec9000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfec9000 - 00000000bfecd000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfecd000 - 00000000bfedf000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfedf000 - 00000000bfef9000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef9000 - 00000000bfeff000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bfeff000 - 00000000bff00000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000d0400000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000d0400000 - 00000000d0401000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000d0401000 - 00000000f0000000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
Aug 13 18:50:21 MARS kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
Aug 13 18:50:21 MARS kernel: [    0.000000] Allocating PCI resources starting at d0401000 (gap: d0401000:1fbff000)
Aug 13 18:50:21 MARS kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 13 18:50:21 MARS kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Aug 13 18:50:21 MARS kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88033fc00000 s83072 r8192 d23424 u1048576
Aug 13 18:50:21 MARS kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
Aug 13 18:50:21 MARS kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Aug 13 18:50:21 MARS kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3086153
Aug 13 18:50:21 MARS kernel: [    0.000000] Policy zone: Normal
Aug 13 18:50:21 MARS kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=a964a96b-e720-470e-94a6-e7016807e850 ro quiet splash vt.handoff=7
Aug 13 18:50:21 MARS kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug 13 18:50:21 MARS kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Aug 13 18:50:21 MARS kernel: [    0.000000] Checking aperture...
Aug 13 18:50:21 MARS kernel: [    0.000000] No AGP bridge found
Aug 13 18:50:21 MARS kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Aug 13 18:50:21 MARS kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Aug 13 18:50:21 MARS kernel: [    0.000000] Memory: 12265036k/13631488k available (6566k kernel code, 1073864k absent, 292588k reserved, 6637k data, 920k init)
Aug 13 18:50:21 MARS kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 13 18:50:21 MARS kernel: [    0.000000] Hierarchical RCU implementation.
Aug 13 18:50:21 MARS kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 13 18:50:21 MARS kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Aug 13 18:50:21 MARS kernel: [    0.000000] Extended CMOS year: 2000
Aug 13 18:50:21 MARS kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 13 18:50:21 MARS kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug 13 18:50:21 MARS kernel: [    0.000000] Console: colour dummy device 80x25
Aug 13 18:50:21 MARS kernel: [    0.000000] console [tty0] enabled
Aug 13 18:50:21 MARS kernel: [    0.000000] allocated 100663296 bytes of page_cgroup
Aug 13 18:50:21 MARS kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 13 18:50:21 MARS kernel: [    0.000000] hpet clockevent registered
Aug 13 18:50:21 MARS kernel: [    0.000000] Fast TSC calibration using PIT
Aug 13 18:50:21 MARS kernel: [    0.000000] Detected 3051.432 MHz processor.
Aug 13 18:50:21 MARS kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6102.86 BogoMIPS (lpj=12205728)
Aug 13 18:50:21 MARS kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Aug 13 18:50:21 MARS kernel: [    0.004027] Security Framework initialized
Aug 13 18:50:21 MARS kernel: [    0.004043] AppArmor: AppArmor initialized
Aug 13 18:50:21 MARS kernel: [    0.004044] Yama: becoming mindful.
Aug 13 18:50:21 MARS kernel: [    0.005145] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Aug 13 18:50:21 MARS kernel: [    0.014819] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Aug 13 18:50:21 MARS kernel: [    0.018243] Mount-cache hash table entries: 256
Aug 13 18:50:21 MARS kernel: [    0.018370] Initializing cgroup subsys cpuacct
Aug 13 18:50:21 MARS kernel: [    0.018374] Initializing cgroup subsys memory
Aug 13 18:50:21 MARS kernel: [    0.018384] Initializing cgroup subsys devices
Aug 13 18:50:21 MARS kernel: [    0.018385] Initializing cgroup subsys freezer
Aug 13 18:50:21 MARS kernel: [    0.018387] Initializing cgroup subsys blkio
Aug 13 18:50:21 MARS kernel: [    0.018393] Initializing cgroup subsys perf_event
Aug 13 18:50:21 MARS kernel: [    0.018419] CPU: Physical Processor ID: 0
Aug 13 18:50:21 MARS kernel: [    0.018420] CPU: Processor Core ID: 0
Aug 13 18:50:21 MARS kernel: [    0.018422] mce: CPU supports 6 MCE banks
Aug 13 18:50:21 MARS kernel: [    0.018429] CPU0: Thermal monitoring enabled (TM2)
Aug 13 18:50:21 MARS kernel: [    0.018433] using mwait in idle threads.
Aug 13 18:50:21 MARS kernel: [    0.020531] ACPI: Core revision 20110623
Aug 13 18:50:21 MARS kernel: [    0.023830] ftrace: allocating 27049 entries in 107 pages
Aug 13 18:50:21 MARS kernel: [    0.028496] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 13 18:50:21 MARS kernel: [    0.068926] CPU0: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz stepping 0a
Aug 13 18:50:21 MARS kernel: [    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Aug 13 18:50:21 MARS kernel: [    0.072003] ... version:                2
Aug 13 18:50:21 MARS kernel: [    0.072003] ... bit width:              40
Aug 13 18:50:21 MARS kernel: [    0.072003] ... generic registers:      2
Aug 13 18:50:21 MARS kernel: [    0.072003] ... value mask:             000000ffffffffff
Aug 13 18:50:21 MARS kernel: [    0.072003] ... max period:             000000007fffffff
Aug 13 18:50:21 MARS kernel: [    0.072003] ... fixed-purpose events:   3
Aug 13 18:50:21 MARS kernel: [    0.072003] ... event mask:             0000000700000003
Aug 13 18:50:21 MARS kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Aug 13 18:50:21 MARS kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Aug 13 18:50:21 MARS kernel: [    0.072003] smpboot cpu 1: start_ip = 9a000
Aug 13 18:50:21 MARS kernel: [    0.160033] NMI watchdog enabled, takes one hw-pmu counter.
Aug 13 18:50:21 MARS kernel: [    0.160067] Brought up 2 CPUs
Aug 13 18:50:21 MARS kernel: [    0.160069] Total of 2 processors activated (12205.45 BogoMIPS).
Aug 13 18:50:21 MARS kernel: [    0.161552] devtmpfs: initialized
Aug 13 18:50:21 MARS kernel: [    0.161552] EVM: security.selinux
Aug 13 18:50:21 MARS kernel: [    0.161552] EVM: security.SMACK64
Aug 13 18:50:21 MARS kernel: [    0.161552] EVM: security.capability
Aug 13 18:50:21 MARS kernel: [    0.161552] PM: Registering ACPI NVS region at be7bf000 (16384 bytes)
Aug 13 18:50:21 MARS kernel: [    0.161552] PM: Registering ACPI NVS region at be822000 (2101248 bytes)
Aug 13 18:50:21 MARS kernel: [    0.161552] PM: Registering ACPI NVS region at bfec3000 (8192 bytes)
Aug 13 18:50:21 MARS kernel: [    0.161552] PM: Registering ACPI NVS region at bfec6000 (12288 bytes)
Aug 13 18:50:21 MARS kernel: [    0.161552] PM: Registering ACPI NVS region at bfecd000 (73728 bytes)
Aug 13 18:50:21 MARS kernel: [    0.161552] print_constraints: dummy: 
Aug 13 18:50:21 MARS kernel: [    0.161552] RTC time: 16:50:14, date: 08/13/12
Aug 13 18:50:21 MARS kernel: [    0.161552] NET: Registered protocol family 16
Aug 13 18:50:21 MARS kernel: [    0.161552] Trying to unpack rootfs image as initramfs...
Aug 13 18:50:21 MARS kernel: [    0.161552] ACPI: bus type pci registered
Aug 13 18:50:21 MARS kernel: [    0.161552] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
Aug 13 18:50:21 MARS kernel: [    0.161552] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in E820
Aug 13 18:50:21 MARS kernel: [    0.161552] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
Aug 13 18:50:21 MARS kernel: [    0.177032] PCI: Using configuration type 1 for base access
Aug 13 18:50:21 MARS kernel: [    0.188195] bio: create slab <bio-0> at 0
Aug 13 18:50:21 MARS kernel: [    0.188195] ACPI: Added _OSI(Module Device)
Aug 13 18:50:21 MARS kernel: [    0.188195] ACPI: Added _OSI(Processor Device)
Aug 13 18:50:21 MARS kernel: [    0.188195] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug 13 18:50:21 MARS kernel: [    0.188195] ACPI: Added _OSI(Processor Aggregator Device)
Aug 13 18:50:21 MARS kernel: [    0.189327] ACPI: EC: EC description table is found, configuring boot EC
Aug 13 18:50:21 MARS kernel: [    0.189767] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Aug 13 18:50:21 MARS kernel: [    0.190001] ACPI: SSDT 00000000bfec8a98 002FE (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.190250] ACPI: Dynamic OEM Table Load:
Aug 13 18:50:21 MARS kernel: [    0.190252] ACPI: SSDT           (null) 002FE (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.190333] ACPI: SSDT 00000000bfec6618 005B0 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.192163] ACPI: Dynamic OEM Table Load:
Aug 13 18:50:21 MARS kernel: [    0.192166] ACPI: SSDT           (null) 005B0 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.244208] ACPI: SSDT 00000000bfec7f18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.244460] ACPI: Dynamic OEM Table Load:
Aug 13 18:50:21 MARS kernel: [    0.244462] ACPI: SSDT           (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.244522] ACPI: SSDT 00000000bfec7e18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.244761] ACPI: Dynamic OEM Table Load:
Aug 13 18:50:21 MARS kernel: [    0.244763] ACPI: SSDT           (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Aug 13 18:50:21 MARS kernel: [    0.256208] ACPI: Interpreter enabled
Aug 13 18:50:21 MARS kernel: [    0.256214] ACPI: (supports S0 S3 S4 S5)
Aug 13 18:50:21 MARS kernel: [    0.256228] ACPI: Using IOAPIC for interrupt routing
Aug 13 18:50:21 MARS kernel: [    0.261013] ACPI: EC: GPE = 0x3f, I/O: command/status = 0x66, data = 0x62
Aug 13 18:50:21 MARS kernel: [    0.261161] ACPI: No dock devices found.
Aug 13 18:50:21 MARS kernel: [    0.261163] HEST: Table not found.
Aug 13 18:50:21 MARS kernel: [    0.261166] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 13 18:50:21 MARS kernel: [    0.261280] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug 13 18:50:21 MARS kernel: [    0.261367] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Aug 13 18:50:21 MARS kernel: [    0.261370] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Aug 13 18:50:21 MARS kernel: [    0.261371] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug 13 18:50:21 MARS kernel: [    0.261373] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Aug 13 18:50:21 MARS kernel: [    0.261375] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Aug 13 18:50:21 MARS kernel: [    0.261377] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Aug 13 18:50:21 MARS kernel: [    0.261379] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Aug 13 18:50:21 MARS kernel: [    0.261380] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Aug 13 18:50:21 MARS kernel: [    0.261382] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Aug 13 18:50:21 MARS kernel: [    0.261384] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Aug 13 18:50:21 MARS kernel: [    0.261386] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Aug 13 18:50:21 MARS kernel: [    0.261388] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Aug 13 18:50:21 MARS kernel: [    0.261389] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Aug 13 18:50:21 MARS kernel: [    0.261391] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Aug 13 18:50:21 MARS kernel: [    0.261393] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Aug 13 18:50:21 MARS kernel: [    0.261395] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
Aug 13 18:50:21 MARS kernel: [    0.261396] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
Aug 13 18:50:21 MARS kernel: [    0.261401] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf9ff])
Aug 13 18:50:21 MARS kernel: [    0.261418] pci 0000:00:00.0: [10de:0a84] type 0 class 0x000600
Aug 13 18:50:21 MARS kernel: [    0.261518] pci 0000:00:00.1: [10de:0a88] type 0 class 0x000500
Aug 13 18:50:21 MARS kernel: [    0.261658] pci 0000:00:03.0: [10de:0aac] type 0 class 0x000601
Aug 13 18:50:21 MARS kernel: [    0.261665] pci 0000:00:03.0: reg 10: [io  0x2000-0x20ff]
Aug 13 18:50:21 MARS kernel: [    0.261707] pci 0000:00:03.1: [10de:0aa4] type 0 class 0x000500
Aug 13 18:50:21 MARS kernel: [    0.261784] pci 0000:00:03.2: [10de:0aa2] type 0 class 0x000c05
Aug 13 18:50:21 MARS kernel: [    0.261797] pci 0000:00:03.2: reg 10: [io  0x2180-0x21bf]
Aug 13 18:50:21 MARS kernel: [    0.261816] pci 0000:00:03.2: reg 20: [io  0x2140-0x217f]
Aug 13 18:50:21 MARS kernel: [    0.261822] pci 0000:00:03.2: reg 24: [io  0x2100-0x213f]
Aug 13 18:50:21 MARS kernel: [    0.261854] pci 0000:00:03.2: PME# supported from D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.261860] pci 0000:00:03.2: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.261878] pci 0000:00:03.3: [10de:0a89] type 0 class 0x000500
Aug 13 18:50:21 MARS kernel: [    0.262012] pci 0000:00:03.4: [10de:0a98] type 0 class 0x000500
Aug 13 18:50:21 MARS kernel: [    0.262066] pci 0000:00:03.5: [10de:0aa3] type 0 class 0x000b40
Aug 13 18:50:21 MARS kernel: [    0.262084] pci 0000:00:03.5: reg 10: [mem 0xd0400000-0xd047ffff]
Aug 13 18:50:21 MARS kernel: [    0.262203] pci 0000:00:04.0: [10de:0aa5] type 0 class 0x000c03
Aug 13 18:50:21 MARS kernel: [    0.262213] pci 0000:00:04.0: reg 10: [mem 0xd0488000-0xd0488fff]
Aug 13 18:50:21 MARS kernel: [    0.262256] pci 0000:00:04.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.262258] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262261] pci 0000:00:04.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262274] pci 0000:00:04.1: [10de:0aa6] type 0 class 0x000c03
Aug 13 18:50:21 MARS kernel: [    0.262286] pci 0000:00:04.1: reg 10: [mem 0xd0489200-0xd04892ff]
Aug 13 18:50:21 MARS kernel: [    0.262336] pci 0000:00:04.1: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.262338] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262341] pci 0000:00:04.1: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262361] pci 0000:00:06.0: [10de:0aa7] type 0 class 0x000c03
Aug 13 18:50:21 MARS kernel: [    0.262371] pci 0000:00:06.0: reg 10: [mem 0xd0487000-0xd0487fff]
Aug 13 18:50:21 MARS kernel: [    0.262415] pci 0000:00:06.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.262417] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262420] pci 0000:00:06.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262433] pci 0000:00:06.1: [10de:0aa9] type 0 class 0x000c03
Aug 13 18:50:21 MARS kernel: [    0.262445] pci 0000:00:06.1: reg 10: [mem 0xd0489100-0xd04891ff]
Aug 13 18:50:21 MARS kernel: [    0.262498] pci 0000:00:06.1: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.262499] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262502] pci 0000:00:06.1: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262522] pci 0000:00:08.0: [10de:0ac0] type 0 class 0x000403
Aug 13 18:50:21 MARS kernel: [    0.262532] pci 0000:00:08.0: reg 10: [mem 0xd0480000-0xd0483fff]
Aug 13 18:50:21 MARS kernel: [    0.262575] pci 0000:00:08.0: PME# supported from D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262578] pci 0000:00:08.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262588] pci 0000:00:09.0: [10de:0aab] type 1 class 0x000604
Aug 13 18:50:21 MARS kernel: [    0.262628] pci 0000:00:0a.0: [10de:0ab0] type 0 class 0x000200
Aug 13 18:50:21 MARS kernel: [    0.262639] pci 0000:00:0a.0: reg 10: [mem 0xd0486000-0xd0486fff]
Aug 13 18:50:21 MARS kernel: [    0.262644] pci 0000:00:0a.0: reg 14: [io  0x21e0-0x21e7]
Aug 13 18:50:21 MARS kernel: [    0.262649] pci 0000:00:0a.0: reg 18: [mem 0xd0489000-0xd04890ff]
Aug 13 18:50:21 MARS kernel: [    0.262654] pci 0000:00:0a.0: reg 1c: [mem 0xd0489300-0xd048930f]
Aug 13 18:50:21 MARS kernel: [    0.262689] pci 0000:00:0a.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.262691] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.262695] pci 0000:00:0a.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.262708] pci 0000:00:0b.0: [10de:0ab5] type 0 class 0x000101
Aug 13 18:50:21 MARS kernel: [    0.262720] pci 0000:00:0b.0: reg 10: [io  0x21d8-0x21df]
Aug 13 18:50:21 MARS kernel: [    0.262726] pci 0000:00:0b.0: reg 14: [io  0x21ec-0x21ef]
Aug 13 18:50:21 MARS kernel: [    0.262731] pci 0000:00:0b.0: reg 18: [io  0x21d0-0x21d7]
Aug 13 18:50:21 MARS kernel: [    0.262736] pci 0000:00:0b.0: reg 1c: [io  0x21e8-0x21eb]
Aug 13 18:50:21 MARS kernel: [    0.262741] pci 0000:00:0b.0: reg 20: [io  0x21c0-0x21cf]
Aug 13 18:50:21 MARS kernel: [    0.262746] pci 0000:00:0b.0: reg 24: [mem 0xd0484000-0xd0485fff]
Aug 13 18:50:21 MARS kernel: [    0.262816] pci 0000:00:0c.0: [10de:0ac4] type 1 class 0x000604
Aug 13 18:50:21 MARS kernel: [    0.263034] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.263041] pci 0000:00:0c.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.263125] pci 0000:00:15.0: [10de:0ac6] type 1 class 0x000604
Aug 13 18:50:21 MARS kernel: [    0.263342] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.263350] pci 0000:00:15.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.263426] pci 0000:00:16.0: [10de:0ac7] type 1 class 0x000604
Aug 13 18:50:21 MARS kernel: [    0.263642] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.263649] pci 0000:00:16.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.263740] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263744] pci 0000:00:09.0:   bridge window [mem 0xd0300000-0xd03fffff]
Aug 13 18:50:21 MARS kernel: [    0.263747] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263749] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263751] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263753] pci 0000:00:09.0:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263754] pci 0000:00:09.0:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263756] pci 0000:00:09.0:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263758] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263760] pci 0000:00:09.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263762] pci 0000:00:09.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263764] pci 0000:00:09.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263766] pci 0000:00:09.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263768] pci 0000:00:09.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263770] pci 0000:00:09.0:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263771] pci 0000:00:09.0:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263773] pci 0000:00:09.0:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263775] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
Aug 13 18:50:21 MARS kernel: [    0.263916] pci 0000:02:00.0: [1002:9488] type 0 class 0x000300
Aug 13 18:50:21 MARS kernel: [    0.263927] pci 0000:02:00.0: reg 10: [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 13 18:50:21 MARS kernel: [    0.263936] pci 0000:02:00.0: reg 18: [mem 0xd0220000-0xd022ffff 64bit]
Aug 13 18:50:21 MARS kernel: [    0.263942] pci 0000:02:00.0: reg 20: [io  0x1000-0x10ff]
Aug 13 18:50:21 MARS kernel: [    0.263953] pci 0000:02:00.0: reg 30: [mem 0xd0200000-0xd021ffff pref]
Aug 13 18:50:21 MARS kernel: [    0.263979] pci 0000:02:00.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.263995] pci 0000:02:00.1: [1002:aa38] type 0 class 0x000403
Aug 13 18:50:21 MARS kernel: [    0.264006] pci 0000:02:00.1: reg 10: [mem 0xd0230000-0xd0233fff 64bit]
Aug 13 18:50:21 MARS kernel: [    0.264066] pci 0000:02:00.1: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.264106] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
Aug 13 18:50:21 MARS kernel: [    0.264120] pci 0000:00:0c.0:   bridge window [io  0x1000-0x1fff]
Aug 13 18:50:21 MARS kernel: [    0.264127] pci 0000:00:0c.0:   bridge window [mem 0xd0200000-0xd02fffff]
Aug 13 18:50:21 MARS kernel: [    0.264140] pci 0000:00:0c.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 13 18:50:21 MARS kernel: [    0.264288] pci 0000:03:00.0: [168c:002a] type 0 class 0x000280
Aug 13 18:50:21 MARS kernel: [    0.264304] pci 0000:03:00.0: reg 10: [mem 0xd0100000-0xd010ffff 64bit]
Aug 13 18:50:21 MARS kernel: [    0.264384] pci 0000:03:00.0: supports D1
Aug 13 18:50:21 MARS kernel: [    0.264386] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
Aug 13 18:50:21 MARS kernel: [    0.264390] pci 0000:03:00.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.264407] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Aug 13 18:50:21 MARS kernel: [    0.264418] pci 0000:00:15.0: PCI bridge to [bus 03-03]
Aug 13 18:50:21 MARS kernel: [    0.264437] pci 0000:00:15.0:   bridge window [mem 0xd0100000-0xd01fffff]
Aug 13 18:50:21 MARS kernel: [    0.264601] pci 0000:04:00.0: [104c:823e] type 1 class 0x000604
Aug 13 18:50:21 MARS kernel: [    0.264695] pci 0000:04:00.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.272041] pci 0000:00:16.0: PCI bridge to [bus 04-05]
Aug 13 18:50:21 MARS kernel: [    0.272061] pci 0000:00:16.0:   bridge window [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.272145] pci 0000:05:00.0: [104c:823f] type 0 class 0x000c00
Aug 13 18:50:21 MARS kernel: [    0.272169] pci 0000:05:00.0: reg 10: [mem 0xd0004000-0xd00047ff]
Aug 13 18:50:21 MARS kernel: [    0.272180] pci 0000:05:00.0: reg 14: [mem 0xd0000000-0xd0003fff]
Aug 13 18:50:21 MARS kernel: [    0.272265] pci 0000:05:00.0: supports D1 D2
Aug 13 18:50:21 MARS kernel: [    0.272267] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
Aug 13 18:50:21 MARS kernel: [    0.272272] pci 0000:05:00.0: PME# disabled
Aug 13 18:50:21 MARS kernel: [    0.272325] pci 0000:04:00.0: PCI bridge to [bus 05-05]
Aug 13 18:50:21 MARS kernel: [    0.272334] pci 0000:04:00.0:   bridge window [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.272397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 13 18:50:21 MARS kernel: [    0.272667]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug 13 18:50:21 MARS kernel: [    0.272767]  pci0000:00: ACPI _OSC control (0x1d) granted
Aug 13 18:50:21 MARS kernel: [    0.287324] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287388] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287448] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287507] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287565] ACPI: PCI Interrupt Link [Z003] (IRQs 16 17 18 19 20 21 22 23) *11
Aug 13 18:50:21 MARS kernel: [    0.287623] ACPI: PCI Interrupt Link [Z004] (IRQs 16 17 18 19 20 21 22 23) *10
Aug 13 18:50:21 MARS kernel: [    0.287681] ACPI: PCI Interrupt Link [Z005] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287741] ACPI: PCI Interrupt Link [Z006] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287799] ACPI: PCI Interrupt Link [Z007] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287858] ACPI: PCI Interrupt Link [Z008] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287918] ACPI: PCI Interrupt Link [Z009] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.287978] ACPI: PCI Interrupt Link [Z00A] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288052] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288114] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288172] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288233] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288291] ACPI: PCI Interrupt Link [Z00F] (IRQs 16 17 18 19 20 21 22 23) *7
Aug 13 18:50:21 MARS kernel: [    0.288349] ACPI: PCI Interrupt Link [Z00G] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288407] ACPI: PCI Interrupt Link [Z00H] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288466] ACPI: PCI Interrupt Link [Z00I] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288524] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *5
Aug 13 18:50:21 MARS kernel: [    0.288582] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288639] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288697] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288755] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288814] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288872] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288930] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.288988] ACPI: PCI Interrupt Link [Z00R] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289049] ACPI: PCI Interrupt Link [Z00S] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289107] ACPI: PCI Interrupt Link [Z00T] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289165] ACPI: PCI Interrupt Link [Z00U] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289224] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
Aug 13 18:50:21 MARS kernel: [    0.289282] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
Aug 13 18:50:21 MARS kernel: [    0.289339] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
Aug 13 18:50:21 MARS kernel: [    0.289397] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *14
Aug 13 18:50:21 MARS kernel: [    0.289454] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
Aug 13 18:50:21 MARS kernel: [    0.289511] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289569] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289627] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
Aug 13 18:50:21 MARS kernel: [    0.289684] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Aug 13 18:50:21 MARS kernel: [    0.289743] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
Aug 13 18:50:21 MARS kernel: [    0.289800] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
Aug 13 18:50:21 MARS kernel: [    0.289860] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
Aug 13 18:50:21 MARS kernel: [    0.289980] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 13 18:50:21 MARS kernel: [    0.289984] vgaarb: loaded
Aug 13 18:50:21 MARS kernel: [    0.289985] vgaarb: bridge control possible 0000:02:00.0
Aug 13 18:50:21 MARS kernel: [    0.290073] i2c-core: driver [aat2870] using legacy suspend method
Aug 13 18:50:21 MARS kernel: [    0.290075] i2c-core: driver [aat2870] using legacy resume method
Aug 13 18:50:21 MARS kernel: [    0.290131] SCSI subsystem initialized
Aug 13 18:50:21 MARS kernel: [    0.290185] libata version 3.00 loaded.
Aug 13 18:50:21 MARS kernel: [    0.290229] usbcore: registered new interface driver usbfs
Aug 13 18:50:21 MARS kernel: [    0.290238] usbcore: registered new interface driver hub
Aug 13 18:50:21 MARS kernel: [    0.290261] usbcore: registered new device driver usb
Aug 13 18:50:21 MARS kernel: [    0.290333] PCI: Using ACPI for IRQ routing
Aug 13 18:50:21 MARS kernel: [    0.291991] PCI: pci_cache_line_size set to 64 bytes
Aug 13 18:50:21 MARS kernel: [    0.292104] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Aug 13 18:50:21 MARS kernel: [    0.292106] reserve RAM buffer: 00000000be7bf000 - 00000000bfffffff 
Aug 13 18:50:21 MARS kernel: [    0.292192] NetLabel: Initializing
Aug 13 18:50:21 MARS kernel: [    0.292194] NetLabel:  domain hash size = 128
Aug 13 18:50:21 MARS kernel: [    0.292195] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 13 18:50:21 MARS kernel: [    0.292206] NetLabel:  unlabeled traffic allowed by default
Aug 13 18:50:21 MARS kernel: [    0.292241] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Aug 13 18:50:21 MARS kernel: [    0.292247] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
Aug 13 18:50:21 MARS kernel: [    0.292250] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
Aug 13 18:50:21 MARS kernel: [    0.296064] Switching to clocksource hpet
Aug 13 18:50:21 MARS kernel: [    0.302270] AppArmor: AppArmor Filesystem Enabled
Aug 13 18:50:21 MARS kernel: [    0.302300] pnp: PnP ACPI init
Aug 13 18:50:21 MARS kernel: [    0.302315] ACPI: bus type pnp registered
Aug 13 18:50:21 MARS kernel: [    0.302407] pnp 00:00: [bus 00-ff]
Aug 13 18:50:21 MARS kernel: [    0.302409] pnp 00:00: [io  0x0cf8-0x0cff]
Aug 13 18:50:21 MARS kernel: [    0.302410] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug 13 18:50:21 MARS kernel: [    0.302412] pnp 00:00: [io  0x0d00-0xffff window]
Aug 13 18:50:21 MARS kernel: [    0.302414] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug 13 18:50:21 MARS kernel: [    0.302415] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Aug 13 18:50:21 MARS kernel: [    0.302417] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Aug 13 18:50:21 MARS kernel: [    0.302418] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Aug 13 18:50:21 MARS kernel: [    0.302420] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Aug 13 18:50:21 MARS kernel: [    0.302422] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Aug 13 18:50:21 MARS kernel: [    0.302423] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Aug 13 18:50:21 MARS kernel: [    0.302425] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Aug 13 18:50:21 MARS kernel: [    0.302426] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Aug 13 18:50:21 MARS kernel: [    0.302428] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Aug 13 18:50:21 MARS kernel: [    0.302429] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Aug 13 18:50:21 MARS kernel: [    0.302431] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Aug 13 18:50:21 MARS kernel: [    0.302433] pnp 00:00: [mem 0x000ec000-0x000effff window]
Aug 13 18:50:21 MARS kernel: [    0.302434] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Aug 13 18:50:21 MARS kernel: [    0.302436] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
Aug 13 18:50:21 MARS kernel: [    0.302507] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Aug 13 18:50:21 MARS kernel: [    0.302521] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Aug 13 18:50:21 MARS kernel: [    0.302523] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
Aug 13 18:50:21 MARS kernel: [    0.302571] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302573] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 13 18:50:21 MARS kernel: [    0.302582] pnp 00:02: [io  0x0300-0x031f]
Aug 13 18:50:21 MARS kernel: [    0.302593] pnp 00:02: [irq 6]
Aug 13 18:50:21 MARS kernel: [    0.302613] pnp 00:02: Plug and Play ACPI device, IDs APP0001 (active)
Aug 13 18:50:21 MARS kernel: [    0.302622] pnp 00:03: [io  0x0000-0x0008]
Aug 13 18:50:21 MARS kernel: [    0.302623] pnp 00:03: [io  0x000a-0x000f]
Aug 13 18:50:21 MARS kernel: [    0.302625] pnp 00:03: [io  0x0081-0x0083]
Aug 13 18:50:21 MARS kernel: [    0.302626] pnp 00:03: [io  0x0087]
Aug 13 18:50:21 MARS kernel: [    0.302627] pnp 00:03: [io  0x0089-0x008b]
Aug 13 18:50:21 MARS kernel: [    0.302629] pnp 00:03: [io  0x008f]
Aug 13 18:50:21 MARS kernel: [    0.302630] pnp 00:03: [io  0x00c0-0x00d1]
Aug 13 18:50:21 MARS kernel: [    0.302631] pnp 00:03: [io  0x00d4-0x00df]
Aug 13 18:50:21 MARS kernel: [    0.302633] pnp 00:03: [dma 4]
Aug 13 18:50:21 MARS kernel: [    0.302654] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 13 18:50:21 MARS kernel: [    0.302703] pnp 00:04: [irq 0 disabled]
Aug 13 18:50:21 MARS kernel: [    0.302708] pnp 00:04: [irq 8]
Aug 13 18:50:21 MARS kernel: [    0.302712] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Aug 13 18:50:21 MARS kernel: [    0.302745] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302748] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Aug 13 18:50:21 MARS kernel: [    0.302756] pnp 00:05: [io  0x00f0-0x00f1]
Aug 13 18:50:21 MARS kernel: [    0.302760] pnp 00:05: [irq 13]
Aug 13 18:50:21 MARS kernel: [    0.302779] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 13 18:50:21 MARS kernel: [    0.302842] pnp 00:06: [io  0x0400-0x047f]
Aug 13 18:50:21 MARS kernel: [    0.302844] pnp 00:06: [io  0x0480-0x04ff]
Aug 13 18:50:21 MARS kernel: [    0.302845] pnp 00:06: [io  0x0500-0x057f]
Aug 13 18:50:21 MARS kernel: [    0.302847] pnp 00:06: [io  0x0580-0x05ff]
Aug 13 18:50:21 MARS kernel: [    0.302848] pnp 00:06: [io  0x0800-0x087f]
Aug 13 18:50:21 MARS kernel: [    0.302850] pnp 00:06: [io  0x0880-0x08ff]
Aug 13 18:50:21 MARS kernel: [    0.302851] pnp 00:06: [io  0x0010-0x001f]
Aug 13 18:50:21 MARS kernel: [    0.302852] pnp 00:06: [io  0x0022-0x003f]
Aug 13 18:50:21 MARS kernel: [    0.302854] pnp 00:06: [io  0x0044-0x005f]
Aug 13 18:50:21 MARS kernel: [    0.302855] pnp 00:06: [io  0x0063]
Aug 13 18:50:21 MARS kernel: [    0.302856] pnp 00:06: [io  0x0065]
Aug 13 18:50:21 MARS kernel: [    0.302858] pnp 00:06: [io  0x0067-0x006f]
Aug 13 18:50:21 MARS kernel: [    0.302859] pnp 00:06: [io  0x0072-0x0073]
Aug 13 18:50:21 MARS kernel: [    0.302860] pnp 00:06: [io  0x0074-0x007f]
Aug 13 18:50:21 MARS kernel: [    0.302862] pnp 00:06: [io  0x0091-0x0093]
Aug 13 18:50:21 MARS kernel: [    0.302863] pnp 00:06: [io  0x0097-0x009f]
Aug 13 18:50:21 MARS kernel: [    0.302864] pnp 00:06: [io  0x00a2-0x00bf]
Aug 13 18:50:21 MARS kernel: [    0.302866] pnp 00:06: [io  0x00e0-0x00ef]
Aug 13 18:50:21 MARS kernel: [    0.302867] pnp 00:06: [io  0x04d0-0x04d1]
Aug 13 18:50:21 MARS kernel: [    0.302868] pnp 00:06: [io  0x0080]
Aug 13 18:50:21 MARS kernel: [    0.302870] pnp 00:06: [io  0x0295-0x0296]
Aug 13 18:50:21 MARS kernel: [    0.302911] system 00:06: [io  0x0400-0x047f] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302914] system 00:06: [io  0x0480-0x04ff] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302916] system 00:06: [io  0x0500-0x057f] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302917] system 00:06: [io  0x0580-0x05ff] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302919] system 00:06: [io  0x0800-0x087f] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302921] system 00:06: [io  0x0880-0x08ff] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302923] system 00:06: [io  0x04d0-0x04d1] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302925] system 00:06: [io  0x0295-0x0296] has been reserved
Aug 13 18:50:21 MARS kernel: [    0.302928] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 13 18:50:21 MARS kernel: [    0.302934] pnp 00:07: [io  0x0070-0x0077]
Aug 13 18:50:21 MARS kernel: [    0.302955] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 13 18:50:21 MARS kernel: [    0.303415] pnp: PnP ACPI: found 8 devices
Aug 13 18:50:21 MARS kernel: [    0.303416] ACPI: ACPI bus type pnp unregistered
Aug 13 18:50:21 MARS kernel: [    0.309358] PCI: max bus depth: 2 pci_try_num: 3
Aug 13 18:50:21 MARS kernel: [    0.309432] pci 0000:00:09.0: PCI bridge to [bus 01-01]
Aug 13 18:50:21 MARS kernel: [    0.309436] pci 0000:00:09.0:   bridge window [mem 0xd0300000-0xd03fffff]
Aug 13 18:50:21 MARS kernel: [    0.309442] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
Aug 13 18:50:21 MARS kernel: [    0.309446] pci 0000:00:0c.0:   bridge window [io  0x1000-0x1fff]
Aug 13 18:50:21 MARS kernel: [    0.309456] pci 0000:00:0c.0:   bridge window [mem 0xd0200000-0xd02fffff]
Aug 13 18:50:21 MARS kernel: [    0.309463] pci 0000:00:0c.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 13 18:50:21 MARS kernel: [    0.309476] pci 0000:00:15.0: PCI bridge to [bus 03-03]
Aug 13 18:50:21 MARS kernel: [    0.309485] pci 0000:00:15.0:   bridge window [mem 0xd0100000-0xd01fffff]
Aug 13 18:50:21 MARS kernel: [    0.309503] pci 0000:04:00.0: PCI bridge to [bus 05-05]
Aug 13 18:50:21 MARS kernel: [    0.309509] pci 0000:04:00.0:   bridge window [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.309518] pci 0000:00:16.0: PCI bridge to [bus 04-05]
Aug 13 18:50:21 MARS kernel: [    0.309527] pci 0000:00:16.0:   bridge window [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.309547] pci 0000:00:09.0: enabling device (0000 -> 0002)
Aug 13 18:50:21 MARS kernel: [    0.309553] pci 0000:00:09.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.309681] ACPI: PCI Interrupt Link [Z003] enabled at IRQ 23
Aug 13 18:50:21 MARS kernel: [    0.309692] pci 0000:00:0c.0: PCI INT A -> Link[Z003] -> GSI 23 (level, low) -> IRQ 23
Aug 13 18:50:21 MARS kernel: [    0.309700] pci 0000:00:0c.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.309795] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 22
Aug 13 18:50:21 MARS kernel: [    0.309801] pci 0000:00:15.0: PCI INT A -> Link[Z00F] -> GSI 22 (level, low) -> IRQ 22
Aug 13 18:50:21 MARS kernel: [    0.309809] pci 0000:00:15.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.309903] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 21
Aug 13 18:50:21 MARS kernel: [    0.309908] pci 0000:00:16.0: PCI INT A -> Link[Z00J] -> GSI 21 (level, low) -> IRQ 21
Aug 13 18:50:21 MARS kernel: [    0.309916] pci 0000:00:16.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.309926] pci 0000:04:00.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.309930] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 13 18:50:21 MARS kernel: [    0.309932] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 13 18:50:21 MARS kernel: [    0.309934] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 13 18:50:21 MARS kernel: [    0.309936] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Aug 13 18:50:21 MARS kernel: [    0.309937] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Aug 13 18:50:21 MARS kernel: [    0.309939] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Aug 13 18:50:21 MARS kernel: [    0.309941] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
Aug 13 18:50:21 MARS kernel: [    0.309942] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
Aug 13 18:50:21 MARS kernel: [    0.309944] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
Aug 13 18:50:21 MARS kernel: [    0.309945] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
Aug 13 18:50:21 MARS kernel: [    0.309947] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
Aug 13 18:50:21 MARS kernel: [    0.309949] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
Aug 13 18:50:21 MARS kernel: [    0.309951] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
Aug 13 18:50:21 MARS kernel: [    0.309952] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
Aug 13 18:50:21 MARS kernel: [    0.309954] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
Aug 13 18:50:21 MARS kernel: [    0.309956] pci_bus 0000:00: resource 19 [mem 0xc0000000-0xfebfffff]
Aug 13 18:50:21 MARS kernel: [    0.309958] pci_bus 0000:01: resource 1 [mem 0xd0300000-0xd03fffff]
Aug 13 18:50:21 MARS kernel: [    0.309960] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
Aug 13 18:50:21 MARS kernel: [    0.309962] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
Aug 13 18:50:21 MARS kernel: [    0.309965] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
Aug 13 18:50:21 MARS kernel: [    0.309967] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff]
Aug 13 18:50:21 MARS kernel: [    0.309969] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff]
Aug 13 18:50:21 MARS kernel: [    0.309971] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff]
Aug 13 18:50:21 MARS kernel: [    0.309974] pci_bus 0000:01: resource 10 [mem 0x000d0000-0x000d3fff]
Aug 13 18:50:21 MARS kernel: [    0.309976] pci_bus 0000:01: resource 11 [mem 0x000d4000-0x000d7fff]
Aug 13 18:50:21 MARS kernel: [    0.309978] pci_bus 0000:01: resource 12 [mem 0x000d8000-0x000dbfff]
Aug 13 18:50:21 MARS kernel: [    0.309981] pci_bus 0000:01: resource 13 [mem 0x000dc000-0x000dffff]
Aug 13 18:50:21 MARS kernel: [    0.309983] pci_bus 0000:01: resource 14 [mem 0x000e0000-0x000e3fff]
Aug 13 18:50:21 MARS kernel: [    0.309985] pci_bus 0000:01: resource 15 [mem 0x000e4000-0x000e7fff]
Aug 13 18:50:21 MARS kernel: [    0.309987] pci_bus 0000:01: resource 16 [mem 0x000e8000-0x000ebfff]
Aug 13 18:50:21 MARS kernel: [    0.309990] pci_bus 0000:01: resource 17 [mem 0x000ec000-0x000effff]
Aug 13 18:50:21 MARS kernel: [    0.309992] pci_bus 0000:01: resource 18 [mem 0x000f0000-0x000fffff]
Aug 13 18:50:21 MARS kernel: [    0.309994] pci_bus 0000:01: resource 19 [mem 0xc0000000-0xfebfffff]
Aug 13 18:50:21 MARS kernel: [    0.309997] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
Aug 13 18:50:21 MARS kernel: [    0.309999] pci_bus 0000:02: resource 1 [mem 0xd0200000-0xd02fffff]
Aug 13 18:50:21 MARS kernel: [    0.310002] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 13 18:50:21 MARS kernel: [    0.310004] pci_bus 0000:03: resource 1 [mem 0xd0100000-0xd01fffff]
Aug 13 18:50:21 MARS kernel: [    0.310007] pci_bus 0000:04: resource 1 [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.310009] pci_bus 0000:05: resource 1 [mem 0xd0000000-0xd00fffff]
Aug 13 18:50:21 MARS kernel: [    0.310046] NET: Registered protocol family 2
Aug 13 18:50:21 MARS kernel: [    0.310349] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug 13 18:50:21 MARS kernel: [    0.312584] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Aug 13 18:50:21 MARS kernel: [    0.316291] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug 13 18:50:21 MARS kernel: [    0.316734] TCP: Hash tables configured (established 524288 bind 65536)
Aug 13 18:50:21 MARS kernel: [    0.316736] TCP reno registered
Aug 13 18:50:21 MARS kernel: [    0.316757] UDP hash table entries: 8192 (order: 6, 262144 bytes)
Aug 13 18:50:21 MARS kernel: [    0.316892] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
Aug 13 18:50:21 MARS kernel: [    0.317103] NET: Registered protocol family 1
Aug 13 18:50:21 MARS kernel: [    0.317296] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
Aug 13 18:50:21 MARS kernel: [    0.317310] pci 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
Aug 13 18:50:21 MARS kernel: [    0.366800] Freeing initrd memory: 13836k freed
Aug 13 18:50:21 MARS kernel: [    0.388041] pci 0000:00:04.0: PCI INT A disabled
Aug 13 18:50:21 MARS kernel: [    0.388197] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
Aug 13 18:50:21 MARS kernel: [    0.388214] pci 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
Aug 13 18:50:21 MARS kernel: [    0.388245] pci 0000:00:04.1: PCI INT B disabled
Aug 13 18:50:21 MARS kernel: [    0.388337] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 18
Aug 13 18:50:21 MARS kernel: [    0.388343] pci 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
Aug 13 18:50:21 MARS kernel: [    0.444018] pci 0000:00:06.0: PCI INT A disabled
Aug 13 18:50:21 MARS kernel: [    0.444113] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 17
Aug 13 18:50:21 MARS kernel: [    0.444119] pci 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
Aug 13 18:50:21 MARS kernel: [    0.444134] pci 0000:00:06.1: PCI INT B disabled
Aug 13 18:50:21 MARS kernel: [    0.444257] pci 0000:02:00.0: Boot video device
Aug 13 18:50:21 MARS kernel: [    0.444267] PCI: CLS mismatch (256 != 64), using 64 bytes
Aug 13 18:50:21 MARS kernel: [    0.444270] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug 13 18:50:21 MARS kernel: [    0.444272] Placing 64MB software IO TLB between ffff8800ba7b1000 - ffff8800be7b1000
Aug 13 18:50:21 MARS kernel: [    0.444274] software IO TLB at phys 0xba7b1000 - 0xbe7b1000
Aug 13 18:50:21 MARS kernel: [    0.444586] audit: initializing netlink socket (disabled)
Aug 13 18:50:21 MARS kernel: [    0.444599] type=2000 audit(1344876613.440:1): initialized
Aug 13 18:50:21 MARS kernel: [    0.487446] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug 13 18:50:21 MARS kernel: [    0.541152] VFS: Disk quotas dquot_6.5.2
Aug 13 18:50:21 MARS kernel: [    0.541198] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug 13 18:50:21 MARS kernel: [    0.541598] fuse init (API version 7.17)
Aug 13 18:50:21 MARS kernel: [    0.541671] msgmni has been set to 23982
Aug 13 18:50:21 MARS kernel: [    0.541995] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 13 18:50:21 MARS kernel: [    0.542020] io scheduler noop registered
Aug 13 18:50:21 MARS kernel: [    0.542021] io scheduler deadline registered
Aug 13 18:50:21 MARS kernel: [    0.542048] io scheduler cfq registered (default)
Aug 13 18:50:21 MARS kernel: [    0.542160] pcieport 0000:00:0c.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.542286] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    0.542441] pcieport 0000:00:15.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.542562] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    0.542714] pcieport 0000:00:16.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.542835] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    0.543005] pcieport 0000:00:0c.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543008] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543009] pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543017] pcie_pme 0000:00:0c.0:pcie01: service driver pcie_pme loaded
Aug 13 18:50:21 MARS kernel: [    0.543050] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543051] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543059] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
Aug 13 18:50:21 MARS kernel: [    0.543090] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543092] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543093] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
Aug 13 18:50:21 MARS kernel: [    0.543101] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
Aug 13 18:50:21 MARS kernel: [    0.543114] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 13 18:50:21 MARS kernel: [    0.543131] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 13 18:50:21 MARS kernel: [    0.543171] efifb: dmi detected iMac10,1 - framebuffer at 0xc0000000 (1400x1050, stride 5632)
Aug 13 18:50:21 MARS kernel: [    0.543173] intel_idle: MWAIT substates: 0x22220
Aug 13 18:50:21 MARS kernel: [    0.543175] intel_idle: does not run on family 6 model 23
Aug 13 18:50:21 MARS kernel: [    0.543242] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Aug 13 18:50:21 MARS kernel: [    0.543246] ACPI: Power Button [PWRB]
Aug 13 18:50:21 MARS kernel: [    0.543280] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Aug 13 18:50:21 MARS kernel: [    0.543282] ACPI: Sleep Button [SLPB]
Aug 13 18:50:21 MARS kernel: [    0.543329] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 13 18:50:21 MARS kernel: [    0.543332] ACPI: Power Button [PWRF]
Aug 13 18:50:21 MARS kernel: [    0.543461] Monitor-Mwait will be used to enter C-1 state
Aug 13 18:50:21 MARS kernel: [    0.543486] Monitor-Mwait will be used to enter C-2 state
Aug 13 18:50:21 MARS kernel: [    0.543512] Monitor-Mwait will be used to enter C-3 state
Aug 13 18:50:21 MARS kernel: [    0.543518] Marking TSC unstable due to TSC halts in idle
Aug 13 18:50:21 MARS kernel: [    0.543531] ACPI: acpi_idle registered with cpuidle
Aug 13 18:50:21 MARS kernel: [    0.544892] ERST: Table is not found!
Aug 13 18:50:21 MARS kernel: [    0.544893] GHES: HEST is not enabled!
Aug 13 18:50:21 MARS kernel: [    0.544952] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 13 18:50:21 MARS kernel: [    0.656225] Linux agpgart interface v0.103
Aug 13 18:50:21 MARS kernel: [    0.657368] brd: module loaded
Aug 13 18:50:21 MARS kernel: [    0.657974] loop: module loaded
Aug 13 18:50:21 MARS kernel: [    0.658067] ahci 0000:00:0b.0: version 3.0
Aug 13 18:50:21 MARS kernel: [    0.658168] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 16
Aug 13 18:50:21 MARS kernel: [    0.658178] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
Aug 13 18:50:21 MARS kernel: [    0.658213] ahci 0000:00:0b.0: irq 43 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    0.658219] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
Aug 13 18:50:21 MARS kernel: [    0.658260] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
Aug 13 18:50:21 MARS kernel: [    0.658262] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pio slum part boh 
Aug 13 18:50:21 MARS kernel: [    0.658265] ahci 0000:00:0b.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.658764] scsi0 : ahci
Aug 13 18:50:21 MARS kernel: [    0.658832] scsi1 : ahci
Aug 13 18:50:21 MARS kernel: [    0.658892] scsi2 : ahci
Aug 13 18:50:21 MARS kernel: [    0.658950] scsi3 : ahci
Aug 13 18:50:21 MARS kernel: [    0.659008] scsi4 : ahci
Aug 13 18:50:21 MARS kernel: [    0.659066] scsi5 : ahci
Aug 13 18:50:21 MARS kernel: [    0.659160] ata1: SATA max UDMA/133 abar m8192@0xd0484000 port 0xd0484100 irq 43
Aug 13 18:50:21 MARS kernel: [    0.659162] ata2: SATA max UDMA/133 abar m8192@0xd0484000 port 0xd0484180 irq 43
Aug 13 18:50:21 MARS kernel: [    0.659164] ata3: DUMMY
Aug 13 18:50:21 MARS kernel: [    0.659165] ata4: DUMMY
Aug 13 18:50:21 MARS kernel: [    0.659166] ata5: DUMMY
Aug 13 18:50:21 MARS kernel: [    0.659167] ata6: DUMMY
Aug 13 18:50:21 MARS kernel: [    0.659457] Fixed MDIO Bus: probed
Aug 13 18:50:21 MARS kernel: [    0.659471] tun: Universal TUN/TAP device driver, 1.6
Aug 13 18:50:21 MARS kernel: [    0.659472] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 13 18:50:21 MARS kernel: [    0.659520] PPP generic driver version 2.4.2
Aug 13 18:50:21 MARS kernel: [    0.659618] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 13 18:50:21 MARS kernel: [    0.659631] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
Aug 13 18:50:21 MARS kernel: [    0.659641] ehci_hcd 0000:00:04.1: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.659644] ehci_hcd 0000:00:04.1: EHCI Host Controller
Aug 13 18:50:21 MARS kernel: [    0.659678] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
Aug 13 18:50:21 MARS kernel: [    0.659699] ehci_hcd 0000:00:04.1: debug port 1
Aug 13 18:50:21 MARS kernel: [    0.659706] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Aug 13 18:50:21 MARS kernel: [    0.659718] ehci_hcd 0000:00:04.1: irq 19, io mem 0xd0489200
Aug 13 18:50:21 MARS kernel: [    0.668015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Aug 13 18:50:21 MARS kernel: [    0.668111] hub 1-0:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    0.668115] hub 1-0:1.0: 7 ports detected
Aug 13 18:50:21 MARS kernel: [    0.668171] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
Aug 13 18:50:21 MARS kernel: [    0.668183] ehci_hcd 0000:00:06.1: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.668185] ehci_hcd 0000:00:06.1: EHCI Host Controller
Aug 13 18:50:21 MARS kernel: [    0.668222] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
Aug 13 18:50:21 MARS kernel: [    0.668236] ehci_hcd 0000:00:06.1: debug port 1
Aug 13 18:50:21 MARS kernel: [    0.668243] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
Aug 13 18:50:21 MARS kernel: [    0.668255] ehci_hcd 0000:00:06.1: irq 17, io mem 0xd0489100
Aug 13 18:50:21 MARS kernel: [    0.680015] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
Aug 13 18:50:21 MARS kernel: [    0.680092] hub 2-0:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    0.680095] hub 2-0:1.0: 5 ports detected
Aug 13 18:50:21 MARS kernel: [    0.680151] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 13 18:50:21 MARS kernel: [    0.680162] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
Aug 13 18:50:21 MARS kernel: [    0.680172] ohci_hcd 0000:00:04.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.680174] ohci_hcd 0000:00:04.0: OHCI Host Controller
Aug 13 18:50:21 MARS kernel: [    0.680205] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
Aug 13 18:50:21 MARS kernel: [    0.680223] ohci_hcd 0000:00:04.0: irq 20, io mem 0xd0488000
Aug 13 18:50:21 MARS kernel: [    0.738082] hub 3-0:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    0.738086] hub 3-0:1.0: 7 ports detected
Aug 13 18:50:21 MARS kernel: [    0.738141] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
Aug 13 18:50:21 MARS kernel: [    0.738150] ohci_hcd 0000:00:06.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    0.738152] ohci_hcd 0000:00:06.0: OHCI Host Controller
Aug 13 18:50:21 MARS kernel: [    0.738189] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
Aug 13 18:50:21 MARS kernel: [    0.738207] ohci_hcd 0000:00:06.0: irq 18, io mem 0xd0487000
Aug 13 18:50:21 MARS kernel: [    0.794085] hub 4-0:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    0.794089] hub 4-0:1.0: 5 ports detected
Aug 13 18:50:21 MARS kernel: [    0.794140] uhci_hcd: USB Universal Host Controller Interface driver
Aug 13 18:50:21 MARS kernel: [    0.794181] usbcore: registered new interface driver libusual
Aug 13 18:50:21 MARS kernel: [    0.794205] i8042: PNP: No PS/2 controller found. Probing ports directly.
Aug 13 18:50:21 MARS kernel: [    0.795058] i8042: No controller found
Aug 13 18:50:21 MARS kernel: [    0.795120] mousedev: PS/2 mouse device common for all mice
Aug 13 18:50:21 MARS kernel: [    0.795272] rtc_cmos 00:07: RTC can wake from S4
Aug 13 18:50:21 MARS kernel: [    0.795457] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Aug 13 18:50:21 MARS kernel: [    0.795505] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Aug 13 18:50:21 MARS kernel: [    0.795560] device-mapper: uevent: version 1.0.3
Aug 13 18:50:21 MARS kernel: [    0.795620] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Aug 13 18:50:21 MARS kernel: [    0.795670] cpuidle: using governor ladder
Aug 13 18:50:21 MARS kernel: [    0.795734] cpuidle: using governor menu
Aug 13 18:50:21 MARS kernel: [    0.795735] EFI Variables Facility v0.08 2004-May-17
Aug 13 18:50:21 MARS kernel: [    0.795908] TCP cubic registered
Aug 13 18:50:21 MARS kernel: [    0.795986] NET: Registered protocol family 10
Aug 13 18:50:21 MARS kernel: [    0.796337] NET: Registered protocol family 17
Aug 13 18:50:21 MARS kernel: [    0.796350] Registering the dns_resolver key type
Aug 13 18:50:21 MARS kernel: [    0.796496] PM: Hibernation image not present or could not be loaded.
Aug 13 18:50:21 MARS kernel: [    0.796509] registered taskstats version 1
Aug 13 18:50:21 MARS kernel: [    0.827864]   Magic number: 8:473:843
Aug 13 18:50:21 MARS kernel: [    0.827996] rtc_cmos 00:07: setting system clock to 2012-08-13 16:50:14 UTC (1344876614)
Aug 13 18:50:21 MARS kernel: [    0.828341] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 13 18:50:21 MARS kernel: [    0.828343] EDD information not available.
Aug 13 18:50:21 MARS kernel: [    0.976041] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 13 18:50:21 MARS kernel: [    0.976061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 13 18:50:21 MARS kernel: [    0.977153] ata1.00: ATA-8: ST31000528ASQ, AP24, max UDMA/133
Aug 13 18:50:21 MARS kernel: [    0.977157] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 13 18:50:21 MARS kernel: [    0.977698] ata2.00: ATAPI: OPTIARC DVD RW AD-5680H, 3AHB, max UDMA/100
Aug 13 18:50:21 MARS kernel: [    0.978400] ata1.00: configured for UDMA/133
Aug 13 18:50:21 MARS kernel: [    0.978527] scsi 0:0:0:0: Direct-Access     ATA      ST31000528ASQ    AP24 PQ: 0 ANSI: 5
Aug 13 18:50:21 MARS kernel: [    0.978620] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Aug 13 18:50:21 MARS kernel: [    0.978641] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 13 18:50:21 MARS kernel: [    0.978657] sd 0:0:0:0: [sda] Write Protect is off
Aug 13 18:50:21 MARS kernel: [    0.978659] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 13 18:50:21 MARS kernel: [    0.978676] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 18:50:21 MARS kernel: [    0.979700] ata2.00: configured for UDMA/100
Aug 13 18:50:21 MARS kernel: [    0.982629] scsi 1:0:0:0: CD-ROM            OPTIARC  DVD RW AD-5680H  3AHB PQ: 0 ANSI: 5
Aug 13 18:50:21 MARS kernel: [    0.984649] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda caddy
Aug 13 18:50:21 MARS kernel: [    0.984653] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 13 18:50:21 MARS kernel: [    0.984809] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 13 18:50:21 MARS kernel: [    0.984888] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 13 18:50:21 MARS kernel: [    1.015658]  sda: sda1 sda2 sda3 < sda5 sda6 >
Aug 13 18:50:21 MARS kernel: [    1.016235] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 13 18:50:21 MARS kernel: [    1.017444] Freeing unused kernel memory: 920k freed
Aug 13 18:50:21 MARS kernel: [    1.017697] Write protecting the kernel read-only data: 12288k
Aug 13 18:50:21 MARS kernel: [    1.021794] Freeing unused kernel memory: 1608k freed
Aug 13 18:50:21 MARS kernel: [    1.025245] Freeing unused kernel memory: 1196k freed
Aug 13 18:50:21 MARS kernel: [    1.087322] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Aug 13 18:50:21 MARS kernel: [    1.087466] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
Aug 13 18:50:21 MARS kernel: [    1.087471] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
Aug 13 18:50:21 MARS kernel: [    1.087475] forcedeth 0000:00:0a.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    1.092074] usb 1-4: new high-speed USB device number 3 using ehci_hcd
Aug 13 18:50:21 MARS kernel: [    1.098601] firewire_ohci 0000:05:00.0: PCI INT A -> Link[Z00J] -> GSI 21 (level, low) -> IRQ 21
Aug 13 18:50:21 MARS kernel: [    1.149452] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:26:bb:51:c2:a2
Aug 13 18:50:21 MARS kernel: [    1.149455] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
Aug 13 18:50:21 MARS kernel: [    1.152143] firewire_ohci: Added fw-ohci device 0000:05:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x2
Aug 13 18:50:21 MARS kernel: [    1.458429] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Aug 13 18:50:21 MARS kernel: [    1.584041] usb 2-5: new high-speed USB device number 4 using ehci_hcd
Aug 13 18:50:21 MARS kernel: [    1.652149] firewire_core: created device fw0: GUID 0026bbfffe51c2a2, S800
Aug 13 18:50:21 MARS kernel: [    1.957310] Initializing USB Mass Storage driver...
Aug 13 18:50:21 MARS kernel: [    1.957433] scsi6 : usb-storage 2-5:1.0
Aug 13 18:50:21 MARS kernel: [    1.957486] usbcore: registered new interface driver usb-storage
Aug 13 18:50:21 MARS kernel: [    1.957487] USB Mass Storage support registered.
Aug 13 18:50:21 MARS kernel: [    2.024040] usb 4-1: new full-speed USB device number 2 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    2.249080] hub 4-1:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    2.252040] hub 4-1:1.0: 3 ports detected
Aug 13 18:50:21 MARS kernel: [    2.568032] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    2.958560] scsi 6:0:0:0: Direct-Access     APPLE    SD Card Reader   1.00 PQ: 0 ANSI: 0
Aug 13 18:50:21 MARS kernel: [    2.959015] sd 6:0:0:0: Attached scsi generic sg2 type 0
Aug 13 18:50:21 MARS kernel: [    2.960295] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug 13 18:50:21 MARS kernel: [    3.088059] usb 3-1: new full-speed USB device number 2 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    3.274790] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 13 18:50:21 MARS kernel: [    3.308052] hub 3-1:1.0: USB hub found
Aug 13 18:50:21 MARS kernel: [    3.311027] hub 3-1:1.0: 3 ports detected
Aug 13 18:50:21 MARS kernel: [    3.628056] usb 3-5: new low-speed USB device number 3 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    3.689559] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
Aug 13 18:50:21 MARS kernel: [    3.707619] applesmc: key=274 fan=3 temp=33 acc=0 lux=2 kbd=0
Aug 13 18:50:21 MARS kernel: [    3.781731] lp: driver loaded but no devices found
Aug 13 18:50:21 MARS kernel: [    3.787293] [drm] Initialized drm 1.1.0 20060810
Aug 13 18:50:21 MARS kernel: [    3.856637] i2c i2c-0: nForce2 SMBus adapter at 0x2140
Aug 13 18:50:21 MARS kernel: [    3.856657] i2c i2c-1: nForce2 SMBus adapter at 0x2100
Aug 13 18:50:21 MARS kernel: [    3.926040] usb 4-1.1: new full-speed USB device number 4 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    4.003804] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 13 18:50:21 MARS kernel: [    4.099682] Bluetooth: Core ver 2.16
Aug 13 18:50:21 MARS kernel: [    4.099703] NET: Registered protocol family 31
Aug 13 18:50:21 MARS kernel: [    4.099705] Bluetooth: HCI device and connection manager initialized
Aug 13 18:50:21 MARS kernel: [    4.099707] Bluetooth: HCI socket layer initialized
Aug 13 18:50:21 MARS kernel: [    4.099708] Bluetooth: L2CAP socket layer initialized
Aug 13 18:50:21 MARS kernel: [    4.099964] Bluetooth: SCO socket layer initialized
Aug 13 18:50:21 MARS kernel: [    4.100930] Bluetooth: Generic Bluetooth USB driver ver 0.6
Aug 13 18:50:21 MARS kernel: [    4.101107] usbcore: registered new interface driver btusb
Aug 13 18:50:21 MARS kernel: [    4.138032] usb 4-1.2: new full-speed USB device number 5 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    4.142100] cfg80211: Calling CRDA to update world regulatory domain
Aug 13 18:50:21 MARS kernel: [    4.148088] [drm] radeon defaulting to kernel modesetting.
Aug 13 18:50:21 MARS kernel: [    4.148091] [drm] radeon kernel modesetting enabled.
Aug 13 18:50:21 MARS kernel: [    4.148208] radeon 0000:02:00.0: power state changed by ACPI to D0
Aug 13 18:50:21 MARS kernel: [    4.148212] radeon 0000:02:00.0: power state changed by ACPI to D0
Aug 13 18:50:21 MARS kernel: [    4.148220] radeon 0000:02:00.0: PCI INT A -> Link[Z003] -> GSI 23 (level, low) -> IRQ 23
Aug 13 18:50:21 MARS kernel: [    4.148223] radeon 0000:02:00.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    4.148440] [drm] initializing kernel modesetting (RV730 0x1002:0x9488 0x106B:0x00B6).
Aug 13 18:50:21 MARS kernel: [    4.148470] [drm] register mmio base: 0xD0220000
Aug 13 18:50:21 MARS kernel: [    4.148472] [drm] register mmio size: 65536
Aug 13 18:50:21 MARS kernel: [    4.148575] radeon 0000:02:00.0: Invalid ROM contents
Aug 13 18:50:21 MARS kernel: [    4.149145] ATOM BIOS: 113
Aug 13 18:50:21 MARS kernel: [    4.149165] radeon 0000:02:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
Aug 13 18:50:21 MARS kernel: [    4.149168] radeon 0000:02:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
Aug 13 18:50:21 MARS kernel: [    4.150373] [drm] Detected VRAM RAM=256M, BAR=256M
Aug 13 18:50:21 MARS kernel: [    4.150377] [drm] RAM width 128bits DDR
Aug 13 18:50:21 MARS kernel: [    4.150437] [TTM] Zone  kernel: Available graphics memory: 6141298 kiB.
Aug 13 18:50:21 MARS kernel: [    4.150439] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Aug 13 18:50:21 MARS kernel: [    4.150440] [TTM] Initializing pool allocator.
Aug 13 18:50:21 MARS kernel: [    4.150463] [drm] radeon: 256M of VRAM memory ready
Aug 13 18:50:21 MARS kernel: [    4.150465] [drm] radeon: 512M of GTT memory ready.
Aug 13 18:50:21 MARS kernel: [    4.150481] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 13 18:50:21 MARS kernel: [    4.150482] [drm] Driver supports precise vblank timestamp query.
Aug 13 18:50:21 MARS kernel: [    4.150521] radeon 0000:02:00.0: irq 44 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    4.150526] radeon 0000:02:00.0: radeon: using MSI.
Aug 13 18:50:21 MARS kernel: [    4.150554] [drm] radeon: irq initialized.
Aug 13 18:50:21 MARS kernel: [    4.150557] [drm] GART: num cpu pages 131072, num gpu pages 131072
Aug 13 18:50:21 MARS kernel: [    4.151420] [drm] Loading RV730 Microcode
Aug 13 18:50:21 MARS kernel: [    4.168040] hub 4-1:1.0: unable to enumerate USB device on port 2
Aug 13 18:50:21 MARS kernel: [    4.169328] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2:1.0/input/input3
Aug 13 18:50:21 MARS kernel: [    4.169414] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:06.0-2/input0
Aug 13 18:50:21 MARS kernel: [    4.169465] usbcore: registered new interface driver usbhid
Aug 13 18:50:21 MARS kernel: [    4.169466] usbhid: USB HID core driver
Aug 13 18:50:21 MARS kernel: [    4.321050] Linux video capture interface: v2.00
Aug 13 18:50:21 MARS kernel: [    4.335395] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8502)
Aug 13 18:50:21 MARS kernel: [    4.340275] input: Built-in iSight as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.0/input/input4
Aug 13 18:50:21 MARS kernel: [    4.340377] usbcore: registered new interface driver uvcvideo
Aug 13 18:50:21 MARS kernel: [    4.340380] USB Video Class driver (1.1.1)
Aug 13 18:50:21 MARS kernel: [    4.350164] apple 0003:05AC:8242.0002: hiddev0,hidraw1: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
Aug 13 18:50:21 MARS kernel: [    4.382030] usb 3-1.1: new full-speed USB device number 4 using ohci_hcd
Aug 13 18:50:21 MARS kernel: [    4.429560] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
Aug 13 18:50:21 MARS kernel: [    4.429612] radeon 0000:02:00.0: WB enabled
Aug 13 18:50:21 MARS kernel: [    4.475455] [drm] ring test succeeded in 1 usecs
Aug 13 18:50:21 MARS kernel: [    4.475532] [drm] radeon: ib pool ready.
Aug 13 18:50:21 MARS kernel: [    4.475590] [drm] ib test succeeded in 0 usecs
Aug 13 18:50:21 MARS kernel: [    4.476654] [drm] Radeon Display Connectors
Aug 13 18:50:21 MARS kernel: [    4.476656] [drm] Connector 0:
Aug 13 18:50:21 MARS kernel: [    4.476657] [drm]   LVDS
Aug 13 18:50:21 MARS kernel: [    4.476659] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
Aug 13 18:50:21 MARS kernel: [    4.476660] [drm]   Encoders:
Aug 13 18:50:21 MARS kernel: [    4.476661] [drm]     LCD1: INTERNAL_UNIPHY2
Aug 13 18:50:21 MARS kernel: [    4.476662] [drm] Connector 1:
Aug 13 18:50:21 MARS kernel: [    4.476663] [drm]   DisplayPort
Aug 13 18:50:21 MARS kernel: [    4.476664] [drm]   HPD1
Aug 13 18:50:21 MARS kernel: [    4.476666] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Aug 13 18:50:21 MARS kernel: [    4.476667] [drm]   Encoders:
Aug 13 18:50:21 MARS kernel: [    4.476668] [drm]     DFP1: INTERNAL_UNIPHY
Aug 13 18:50:21 MARS kernel: [    4.476669] [drm] Connector 2:
Aug 13 18:50:21 MARS kernel: [    4.476670] [drm]   DisplayPort
Aug 13 18:50:21 MARS kernel: [    4.476671] [drm]   HPD2
Aug 13 18:50:21 MARS kernel: [    4.476672] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
Aug 13 18:50:21 MARS kernel: [    4.476674] [drm]   Encoders:
Aug 13 18:50:21 MARS kernel: [    4.476675] [drm]     DFP2: INTERNAL_UNIPHY
Aug 13 18:50:21 MARS kernel: [    4.476676] [drm] Connector 3:
Aug 13 18:50:21 MARS kernel: [    4.476677] [drm]   VGA
Aug 13 18:50:21 MARS kernel: [    4.476678] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
Aug 13 18:50:21 MARS kernel: [    4.476679] [drm]   Encoders:
Aug 13 18:50:21 MARS kernel: [    4.476680] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
Aug 13 18:50:21 MARS kernel: [    4.476703] [drm] Special thermal controller config
Aug 13 18:50:21 MARS kernel: [    4.476717] [drm] radeon: power management initialized
Aug 13 18:50:21 MARS kernel: [    4.502263] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
Aug 13 18:50:21 MARS kernel: [    4.502330] generic-usb 0003:05AC:0205.0003: input,hidraw2: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:04.0-1.1/input0
Aug 13 18:50:21 MARS kernel: [    4.512062] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1.1/3-1.1:1.1/input/input6
Aug 13 18:50:21 MARS kernel: [    4.512115] generic-usb 0003:05AC:0205.0004: input,hidraw3: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:04.0-1.1/input1
Aug 13 18:50:21 MARS kernel: [    4.586151] cfg80211: World regulatory domain updated:
Aug 13 18:50:21 MARS kernel: [    4.586153] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 13 18:50:21 MARS kernel: [    4.586156] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    4.586158] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    4.586160] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    4.586162] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    4.586164] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    4.717897] ath9k 0000:03:00.0: power state changed by ACPI to D0
Aug 13 18:50:21 MARS kernel: [    4.717902] ath9k 0000:03:00.0: power state changed by ACPI to D0
Aug 13 18:50:21 MARS kernel: [    4.717911] ath9k 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 22 (level, low) -> IRQ 22
Aug 13 18:50:21 MARS kernel: [    4.717919] ath9k 0000:03:00.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    4.812116] [drm] fb mappable at 0xC0142000
Aug 13 18:50:21 MARS kernel: [    4.812118] [drm] vram apper at 0xC0000000
Aug 13 18:50:21 MARS kernel: [    4.812119] [drm] size 8294400
Aug 13 18:50:21 MARS kernel: [    4.812121] [drm] fb depth is 24
Aug 13 18:50:21 MARS kernel: [    4.812122] [drm]    pitch is 7680
Aug 13 18:50:21 MARS kernel: [    4.812222] fbcon: radeondrmfb (fb0) is primary device
Aug 13 18:50:21 MARS kernel: [    4.812676] Console: switching to colour frame buffer device 240x67
Aug 13 18:50:21 MARS kernel: [    4.812704] fb0: radeondrmfb frame buffer device
Aug 13 18:50:21 MARS kernel: [    4.812705] drm: registered panic notifier
Aug 13 18:50:21 MARS kernel: [    4.812711] [drm] Initialized radeon 2.12.0 20080528 for 0000:02:00.0 on minor 0
Aug 13 18:50:21 MARS kernel: [    5.147444] ath: EEPROM regdomain: 0x37
Aug 13 18:50:21 MARS kernel: [    5.147446] ath: EEPROM indicates we should expect a direct regpair map
Aug 13 18:50:21 MARS kernel: [    5.147448] ath: Country alpha2 being used: AW
Aug 13 18:50:21 MARS kernel: [    5.147449] ath: Regpair used: 0x37
Aug 13 18:50:21 MARS kernel: [    5.147452] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147454] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147456] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147458] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147460] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147462] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147464] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147466] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147467] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147469] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147471] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147473] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147475] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147477] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147478] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147481] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147482] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147484] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147486] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147488] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147489] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147491] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147493] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147495] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147496] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147498] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147500] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147502] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147504] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147506] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147508] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147509] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147511] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147513] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147515] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147516] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147518] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147520] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147522] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147524] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147526] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147527] cfg80211: Disabling freq 5500 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147529] cfg80211: Disabling freq 5520 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147531] cfg80211: Disabling freq 5540 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147532] cfg80211: Disabling freq 5560 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147534] cfg80211: Disabling freq 5580 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147536] cfg80211: Disabling freq 5600 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147537] cfg80211: Disabling freq 5620 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147539] cfg80211: Disabling freq 5640 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147541] cfg80211: Disabling freq 5660 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147542] cfg80211: Disabling freq 5680 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147544] cfg80211: Disabling freq 5700 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 13 18:50:21 MARS kernel: [    5.147546] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147548] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147550] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147552] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147553] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147555] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147557] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147559] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.147561] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.147563] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153762] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153766] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153768] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153770] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153774] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153776] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153777] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153780] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153781] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153784] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153785] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153789] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153791] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153793] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153797] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153799] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153801] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153803] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153804] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153807] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153808] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153810] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153812] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153814] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153816] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153818] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153820] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153822] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153824] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153826] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153828] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153830] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153832] cfg80211: Disabling freq 5260 MHz
Aug 13 18:50:21 MARS kernel: [    5.153833] cfg80211: Disabling freq 5280 MHz
Aug 13 18:50:21 MARS kernel: [    5.153834] cfg80211: Disabling freq 5300 MHz
Aug 13 18:50:21 MARS kernel: [    5.153835] cfg80211: Disabling freq 5320 MHz
Aug 13 18:50:21 MARS kernel: [    5.153836] cfg80211: Disabling freq 5500 MHz
Aug 13 18:50:21 MARS kernel: [    5.153837] cfg80211: Disabling freq 5520 MHz
Aug 13 18:50:21 MARS kernel: [    5.153838] cfg80211: Disabling freq 5540 MHz
Aug 13 18:50:21 MARS kernel: [    5.153839] cfg80211: Disabling freq 5560 MHz
Aug 13 18:50:21 MARS kernel: [    5.153841] cfg80211: Disabling freq 5580 MHz
Aug 13 18:50:21 MARS kernel: [    5.153842] cfg80211: Disabling freq 5600 MHz
Aug 13 18:50:21 MARS kernel: [    5.153843] cfg80211: Disabling freq 5620 MHz
Aug 13 18:50:21 MARS kernel: [    5.153844] cfg80211: Disabling freq 5640 MHz
Aug 13 18:50:21 MARS kernel: [    5.153845] cfg80211: Disabling freq 5660 MHz
Aug 13 18:50:21 MARS kernel: [    5.153846] cfg80211: Disabling freq 5680 MHz
Aug 13 18:50:21 MARS kernel: [    5.153847] cfg80211: Disabling freq 5700 MHz
Aug 13 18:50:21 MARS kernel: [    5.153849] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153851] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153852] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153855] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153856] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153858] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153860] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153862] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.153864] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.153866] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.180167] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 13 18:50:21 MARS kernel: [    5.180594] Registered led device: ath9k-phy0
Aug 13 18:50:21 MARS kernel: [    5.180598] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xffffc90006720000, irq=22
Aug 13 18:50:21 MARS kernel: [    5.180809] cfg80211: Calling CRDA for country: AW
Aug 13 18:50:21 MARS kernel: [    5.185287] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185291] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185293] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185295] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185296] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185298] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185300] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185302] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185304] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185306] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185308] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185310] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185311] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185313] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185315] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185317] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185319] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185321] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185322] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185324] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185326] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185328] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185329] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185332] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185333] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185335] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185337] cfg80211: Disabling freq 2484 MHz
Aug 13 18:50:21 MARS kernel: [    5.185338] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185340] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185342] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185344] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185346] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185348] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185349] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185351] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185353] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185355] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185356] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185358] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185360] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185362] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185364] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185366] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185367] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185369] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185371] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185373] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185375] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185377] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185378] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185380] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185382] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185384] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185385] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185388] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185389] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185391] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185393] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185395] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185396] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185398] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185400] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185402] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185404] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Aug 13 18:50:21 MARS kernel: [    5.185406] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185407] cfg80211: Disabling freq 5745 MHz
Aug 13 18:50:21 MARS kernel: [    5.185408] cfg80211: Disabling freq 5765 MHz
Aug 13 18:50:21 MARS kernel: [    5.185410] cfg80211: Disabling freq 5785 MHz
Aug 13 18:50:21 MARS kernel: [    5.185411] cfg80211: Disabling freq 5805 MHz
Aug 13 18:50:21 MARS kernel: [    5.185412] cfg80211: Disabling freq 5825 MHz
Aug 13 18:50:21 MARS kernel: [    5.185416] cfg80211: Regulatory domain changed to country: AW
Aug 13 18:50:21 MARS kernel: [    5.185417] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 13 18:50:21 MARS kernel: [    5.185419] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185420] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185422] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 13 18:50:21 MARS kernel: [    5.185424] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 13 18:50:21 MARS kernel: [    5.243971] type=1400 audit(1344876618.910:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=637 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.243981] type=1400 audit(1344876618.910:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=630 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.244278] type=1400 audit(1344876618.914:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.244284] type=1400 audit(1344876618.914:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.244438] type=1400 audit(1344876618.914:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=637 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.244447] type=1400 audit(1344876618.914:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=630 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.246323] type=1400 audit(1344876618.914:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=753 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.248117] type=1400 audit(1344876618.918:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=753 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.249865] type=1400 audit(1344876618.918:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=753 comm="apparmor_parser"
Aug 13 18:50:21 MARS kernel: [    5.252980] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
Aug 13 18:50:21 MARS kernel: [    5.252985] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
Aug 13 18:50:21 MARS kernel: [    5.252988] hda_intel: Disabling MSI
Aug 13 18:50:21 MARS kernel: [    5.253013] snd_hda_intel 0000:00:08.0: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    6.012172] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input7
Aug 13 18:50:21 MARS kernel: [    6.012505] ACPI: PCI Interrupt Link [Z004] enabled at IRQ 21
Aug 13 18:50:21 MARS kernel: [    6.012510] snd_hda_intel 0000:02:00.1: PCI INT B -> Link[Z004] -> GSI 21 (level, low) -> IRQ 21
Aug 13 18:50:21 MARS kernel: [    6.012567] snd_hda_intel 0000:02:00.1: irq 45 for MSI/MSI-X
Aug 13 18:50:21 MARS kernel: [    6.012589] snd_hda_intel 0000:02:00.1: setting latency timer to 64
Aug 13 18:50:21 MARS kernel: [    6.126478] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
Aug 13 18:50:21 MARS kernel: [    6.126553] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input8
Aug 13 18:50:21 MARS kernel: [    7.106905] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Aug 13 18:50:21 MARS kernel: [    7.489125] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 13 18:50:21 MARS kernel: [    7.643056] init: failsafe main process (878) killed by TERM signal
Aug 13 18:50:21 MARS kernel: [    8.223193] ppdev: user-space parallel port driver
Aug 13 18:50:21 MARS avahi-daemon[940]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Aug 13 18:50:21 MARS avahi-daemon[940]: Successfully dropped root privileges.
Aug 13 18:50:21 MARS avahi-daemon[940]: avahi-daemon 0.6.30 starting up.
Aug 13 18:50:22 MARS bluetoothd[942]: Bluetooth daemon 4.98
Aug 13 18:50:22 MARS bluetoothd[942]: Starting SDP server
Aug 13 18:50:22 MARS bluetoothd[942]: Failed to init alert plugin
Aug 13 18:50:22 MARS bluetoothd[942]: Failed to init time plugin
Aug 13 18:50:22 MARS bluetoothd[942]: Failed to init proximity plugin
Aug 13 18:50:22 MARS avahi-daemon[940]: Successfully called chroot().
Aug 13 18:50:22 MARS avahi-daemon[940]: Successfully dropped remaining capabilities.
Aug 13 18:50:22 MARS avahi-daemon[940]: Loading service file /services/udisks.service.
Aug 13 18:50:22 MARS kernel: [    8.419337] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 13 18:50:22 MARS kernel: [    8.419340] Bluetooth: BNEP filters: protocol multicast
Aug 13 18:50:22 MARS kernel: [    8.438388] Bluetooth: RFCOMM TTY layer initialized
Aug 13 18:50:22 MARS kernel: [    8.438392] Bluetooth: RFCOMM socket layer initialized
Aug 13 18:50:22 MARS kernel: [    8.438394] Bluetooth: RFCOMM ver 1.11
Aug 13 18:50:22 MARS avahi-daemon[940]: Network interface enumeration completed.
Aug 13 18:50:22 MARS avahi-daemon[940]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug 13 18:50:22 MARS avahi-daemon[940]: Server startup complete. Host name is MARS.local. Local service cookie is 3446763436.
Aug 13 18:50:22 MARS avahi-daemon[940]: Service "MARS" (/services/udisks.service) successfully established.
Aug 13 18:50:22 MARS bluetoothd[942]: Failed to init gatt_example plugin
Aug 13 18:50:22 MARS bluetoothd[942]: Listening for HCI events on hci0
Aug 13 18:50:22 MARS kernel: [    8.458910] type=1400 audit(1344876622.126:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=978 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.459220] type=1400 audit(1344876622.126:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=978 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.459385] type=1400 audit(1344876622.126:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=978 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.481567] type=1400 audit(1344876622.150:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=977 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.504309] type=1400 audit(1344876622.174:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=981 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.504721] type=1400 audit(1344876622.174:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=981 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.507814] type=1400 audit(1344876622.174:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=982 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.507821] type=1400 audit(1344876622.174:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=938 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.508202] type=1400 audit(1344876622.178:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=938 comm="apparmor_parser"
Aug 13 18:50:22 MARS kernel: [    8.508328] type=1400 audit(1344876622.178:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=982 comm="apparmor_parser"
Aug 13 18:50:22 MARS bluetoothd[942]: HCI dev 0 up
Aug 13 18:50:22 MARS modem-manager[920]: <info>  ModemManager (version 0.5.2.0) starting...
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin AnyData
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin MotoC
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Ericsson MBM
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Sierra
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Gobi
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Wavecom
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin ZTE
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Linktop
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Huawei
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Novatel
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Option High-Speed
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin X22X
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Samsung
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Nokia
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Longcheer
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Option
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin Generic
Aug 13 18:50:22 MARS modem-manager[920]: <info>  Loaded plugin SimTech
Aug 13 18:50:22 MARS NetworkManager[986]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 13 18:50:22 MARS NetworkManager[986]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 13 18:50:22 MARS bluetoothd[942]: Adapter /org/bluez/942/hci0 has been enabled
Aug 13 18:50:22 MARS NetworkManager[986]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 13 18:50:22 MARS NetworkManager[986]: <info> DNS: loaded plugin dnsmasq
Aug 13 18:50:22 MARS dbus[903]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug 13 18:50:23 MARS polkitd[991]: started daemon version 0.104 using authority implementation `local' version `0.104'
Aug 13 18:50:23 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: init!
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: update_system_hostname
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPluginIfupdown: management mode: unmanaged
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0)
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/wlan0, iface: wlan0)
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: end _init.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 13 18:50:23 MARS NetworkManager[986]:    Ifupdown: get unmanaged devices count: 0
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: (20507440) ... get_connections.
Aug 13 18:50:23 MARS NetworkManager[986]:    SCPlugin-Ifupdown: (20507440) ... get_connections (managed=false): return empty list.
Aug 13 18:50:23 MARS NetworkManager[986]:    Ifupdown: get unmanaged devices count: 0
Aug 13 18:50:23 MARS NetworkManager[986]: <info> modem-manager is now available
Aug 13 18:50:23 MARS NetworkManager[986]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Aug 13 18:50:23 MARS NetworkManager[986]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 13 18:50:23 MARS NetworkManager[986]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 13 18:50:23 MARS NetworkManager[986]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 13 18:50:23 MARS NetworkManager[986]: <info> Networking is enabled by state file
Aug 13 18:50:23 MARS NetworkManager[986]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): carrier is OFF
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): now managed
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): bringing up device.
Aug 13 18:50:23 MARS kernel: [    9.425890] forcedeth 0000:00:0a.0: irq 46 for MSI/MSI-X
Aug 13 18:50:23 MARS kernel: [    9.426081] forcedeth 0000:00:0a.0: eth0: no link during initialization
Aug 13 18:50:23 MARS kernel: [    9.427662] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): preparing device.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 13 18:50:23 MARS NetworkManager[986]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/net/eth0
Aug 13 18:50:23 MARS NetworkManager[986]: <error> [1344876623.102617] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): using nl80211 for WiFi device control
Aug 13 18:50:23 MARS NetworkManager[986]: <warn> (wlan0): driver supports Access Point (AP) mode
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): now managed
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): bringing up device.
Aug 13 18:50:23 MARS kernel: [    9.429198] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): preparing device.
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug 13 18:50:23 MARS dbus[903]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Aug 13 18:50:23 MARS kernel: [    9.472323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 13 18:50:23 MARS kernel: [    9.475513] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 13 18:50:23 MARS dbus[903]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Aug 13 18:50:23 MARS NetworkManager[986]: <info> wpa_supplicant started
Aug 13 18:50:23 MARS udev-configure-printer: add /module/lp
Aug 13 18:50:23 MARS udev-configure-printer: Failed to get parent
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): supplicant interface state: starting -> ready
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug 13 18:50:23 MARS NetworkManager[986]: <info> (wlan0): supplicant interface state: ready -> inactive
Aug 13 18:50:23 MARS NetworkManager[986]: <warn> Trying to remove a non-existant call id.
Aug 13 18:50:23 MARS kernel: [    9.843876] init: alsa-restore main process (1031) terminated with status 99
Aug 13 18:50:23 MARS anacron[1058]: Anacron 2.3 started on 2012-08-13
Aug 13 18:50:23 MARS acpid: starting up with proc fs
Aug 13 18:50:23 MARS cron[1032]: (CRON) INFO (pidfile fd = 3)
Aug 13 18:50:23 MARS anacron[1058]: Will run job `cron.daily' in 5 min.
Aug 13 18:50:23 MARS anacron[1058]: Will run job `cron.weekly' in 10 min.
Aug 13 18:50:23 MARS anacron[1058]: Will run job `cron.monthly' in 15 min.
Aug 13 18:50:23 MARS anacron[1058]: Jobs will be executed sequentially
Aug 13 18:50:23 MARS cron[1060]: (CRON) STARTUP (fork ok)
Aug 13 18:50:23 MARS cron[1060]: (CRON) INFO (Running @reboot jobs)
Aug 13 18:50:23 MARS acpid: 35 rules loaded
Aug 13 18:50:23 MARS acpid: waiting for events: event logging is off
Aug 13 18:50:23 MARS acpid: client connected from 1091[0:0]
Aug 13 18:50:23 MARS acpid: 1 client rule loaded
Aug 13 18:50:25 MARS dbus[903]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Aug 13 18:50:25 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug 13 18:50:25 MARS accounts-daemon[1269]: started daemon version 0.6.15
Aug 13 18:50:25 MARS dbus[903]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug 13 18:50:25 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug 13 18:50:27 MARS dbus[903]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug 13 18:50:27 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug 13 18:50:30 MARS dbus[903]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug 13 18:50:30 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug 13 18:50:31 MARS dbus[903]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 13 18:50:31 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully called chroot.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully dropped privileges.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully limited resources.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Running.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Canary thread running.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Watchdog thread running.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully made thread 1613 of process 1613 (n/a) owned by '104' high priority at nice level -11.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Supervising 1 threads of 1 processes of 1 users.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully made thread 1618 of process 1613 (n/a) owned by '104' RT at priority 5.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Supervising 2 threads of 1 processes of 1 users.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Successfully made thread 1619 of process 1613 (n/a) owned by '104' RT at priority 5.
Aug 13 18:50:31 MARS rtkit-daemon[1615]: Supervising 3 threads of 1 processes of 1 users.
Aug 13 18:50:32 MARS rtkit-daemon[1615]: Successfully made thread 1620 of process 1613 (n/a) owned by '104' RT at priority 5.
Aug 13 18:50:32 MARS rtkit-daemon[1615]: Supervising 4 threads of 1 processes of 1 users.
Aug 13 18:50:32 MARS bluetoothd[942]: Endpoint registered: sender=:1.32 path=/MediaEndpoint/HFPAG
Aug 13 18:50:32 MARS bluetoothd[942]: Endpoint registered: sender=:1.32 path=/MediaEndpoint/A2DPSource
Aug 13 18:50:32 MARS bluetoothd[942]: Endpoint registered: sender=:1.32 path=/MediaEndpoint/A2DPSink
Aug 13 18:50:32 MARS rtkit-daemon[1615]: Successfully made thread 1623 of process 1623 (n/a) owned by '104' high priority at nice level -11.
Aug 13 18:50:32 MARS rtkit-daemon[1615]: Supervising 5 threads of 2 processes of 1 users.
Aug 13 18:50:32 MARS pulseaudio[1623]: [pulseaudio] pid.c: Daemon already running.
Aug 13 18:55:23 MARS anacron[1058]: Job `cron.daily' started
Aug 13 18:55:23 MARS anacron[1648]: Updated timestamp for job `cron.daily' to 2012-08-13
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Successfully made thread 1823 of process 1823 (n/a) owned by '1000' high priority at nice level -11.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Supervising 5 threads of 2 processes of 2 users.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Successfully made thread 1826 of process 1823 (n/a) owned by '1000' RT at priority 5.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Supervising 6 threads of 2 processes of 2 users.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Successfully made thread 1827 of process 1823 (n/a) owned by '1000' RT at priority 5.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Supervising 7 threads of 2 processes of 2 users.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Successfully made thread 1828 of process 1823 (n/a) owned by '1000' RT at priority 5.
Aug 13 18:59:43 MARS rtkit-daemon[1615]: Supervising 8 threads of 2 processes of 2 users.
Aug 13 18:59:43 MARS bluetoothd[942]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/HFPAG
Aug 13 18:59:43 MARS bluetoothd[942]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSource
Aug 13 18:59:43 MARS bluetoothd[942]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSink
Aug 13 18:59:46 MARS dbus[903]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Aug 13 18:59:46 MARS dbus[903]: [system] Successfully activated service 'org.freedesktop.UDisks'
Aug 13 18:59:46 MARS kernel: [  573.111734] ISO 9660 Extensions: Microsoft Joliet Level 1
Aug 13 18:59:46 MARS kernel: [  573.162752] ISO 9660 Extensions: IEEE_P1282
Aug 13 19:00:01 MARS kernel: [  588.204595] audit_printk_skb: 27 callbacks suppressed
Aug 13 19:00:01 MARS kernel: [  588.204598] type=1400 audit(1344877201.874:30): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2020 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 13 19:00:02 MARS bluetoothd[942]: Endpoint unregistered: sender=:1.32 path=/MediaEndpoint/HFPAG
Aug 13 19:00:02 MARS bluetoothd[942]: Endpoint unregistered: sender=:1.32 path=/MediaEndpoint/A2DPSource
Aug 13 19:00:02 MARS bluetoothd[942]: Endpoint unregistered: sender=:1.32 path=/MediaEndpoint/A2DPSink
Aug 13 19:00:02 MARS goa[2025]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Aug 13 19:00:47 MARS dbus[903]: [system] Activating service name='com.ubuntu.DeviceDriver' (using servicehelper)
Aug 13 19:00:47 MARS dbus[903]: [system] Successfully activated service 'com.ubuntu.DeviceDriver'

---

### Post by LtTuvok on 2012-08-13
I made Grub visible on every startup and noticed that the problem resides before Grub loads. 

I installed a efi partition as first partition with 100 MB size and FAT32.

---

### Post by LtTuvok on 2012-08-13
I seems that I solved my issue. I disconnected my mouse during a startup and the startup continued. I tried multiple times and I placed my mouse back in and the same issue occured.

---

