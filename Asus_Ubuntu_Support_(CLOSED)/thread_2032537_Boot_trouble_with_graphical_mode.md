---
title: "Boot trouble with graphical mode"
date: 2012-07-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by maminyana on 2012-07-24
Since I updated to the new version 12.04 my laptop, sometimes it does not start in graphical mode.
It's strange because the computer sometimes starts in graphical mode without problems, and other times remains in tty1.
When it starts in tty1, I press CTRL + ALT + DEL and the computer restarts and then it enters in graphical mode.

What logs should I look to see what's going on? Any ideas?

---------------------------------
Computer: ASUS X5DI Series

Intel® Pentium® Dual Core  T4500 : 2.3 GHz
OS: Ubuntu 12.04, Using Unity and Xubuntu
Chipset	NVIDIA MCP79D
Memory:	4gb DDR3 1066 MHz SDRAM
Screen:	 15.6" HD (1366x768) LED Asus Splendid Video Intelligent
Video Card	NVIDIA® GeForce® G 310M, 512MB VRAM
HD	 2.5" 9.5mm SATA 640GB

---

### Post by apennington on 2012-07-30
On the time when it boots to tty1, login via the terminal and run these commands

dmesg
cat /var/log/syslog


post the output back here :)

---

### Post by maminyana on 2012-08-05
I've been studying dmesg and syslog

I find in /var/log/syslog: 

Aug  5 18:20:41 portatil failsafe: Failsafe of 120 seconds reached.
Aug  5 18:20:41 portatil kernel: [   35.946598] init: failsafe main process (870) killed by TERM signal


Does this mean that the computer starts in failsafe mode?. Why would it do that?

---

### Post by maminyana on 2012-08-05
I send syslog
/var/log/syslog

######################################3
Aug  5 18:20:41 portatil kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug  5 18:20:41 portatil rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="781" x-info="http://www.rsyslog.com"] start
Aug  5 18:20:41 portatil rsyslogd: rsyslogd's groupid changed to 103
Aug  5 18:20:41 portatil rsyslogd: rsyslogd's userid changed to 101
Aug  5 18:20:41 portatil rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug  5 18:20:41 portatil bluetoothd[774]: Failed to init gatt_example plugin
Aug  5 18:20:41 portatil kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  5 18:20:41 portatil kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  5 18:20:41 portatil kernel: [    0.000000] Linux version 3.2.0-27-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 (Ubuntu 3.2.0-27.43-generic 3.2.21)
Aug  5 18:20:41 portatil kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=cef6db15-dbf1-4b34-9536-037319100792 ro quiet splash vt.handoff=7
Aug  5 18:20:41 portatil kernel: [    0.000000] KERNEL supported cpus:
Aug  5 18:20:41 portatil kernel: [    0.000000]   Intel GenuineIntel
Aug  5 18:20:41 portatil kernel: [    0.000000]   AMD AuthenticAMD
Aug  5 18:20:41 portatil kernel: [    0.000000]   Centaur CentaurHauls
Aug  5 18:20:41 portatil kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dffa8000 (usable)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000dffa8000 - 00000000dffb0000 (ACPI NVS)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000dffb0000 - 00000000dffbff00 (ACPI data)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000dffbff00 - 00000000dfff0000 (ACPI NVS)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000dfff0000 - 00000000e0000000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Aug  5 18:20:41 portatil kernel: [    0.000000] NX (Execute Disable) protection: active
Aug  5 18:20:41 portatil kernel: [    0.000000] DMI 2.5 present.
Aug  5 18:20:41 portatil kernel: [    0.000000] DMI: ASUSTeK Computer Inc.  K50IE               /K50IE     , BIOS 215     06/22/2010
Aug  5 18:20:41 portatil kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug  5 18:20:41 portatil kernel: [    0.000000] No AGP bridge found
Aug  5 18:20:41 portatil kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Aug  5 18:20:41 portatil kernel: [    0.000000] MTRR default type: uncachable
Aug  5 18:20:41 portatil kernel: [    0.000000] MTRR fixed ranges enabled:
Aug  5 18:20:41 portatil kernel: [    0.000000]   00000-9FFFF write-back
Aug  5 18:20:41 portatil kernel: [    0.000000]   A0000-BFFFF uncachable
Aug  5 18:20:41 portatil kernel: [    0.000000]   C0000-CFFFF write-protect
Aug  5 18:20:41 portatil kernel: [    0.000000]   D0000-DFFFF uncachable
Aug  5 18:20:41 portatil kernel: [    0.000000]   E0000-EFFFF write-through
Aug  5 18:20:41 portatil kernel: [    0.000000]   F0000-FFFFF write-protect
Aug  5 18:20:41 portatil kernel: [    0.000000] MTRR variable ranges enabled:
Aug  5 18:20:41 portatil kernel: [    0.000000]   0 base 0E0000000 mask FE0000000 uncachable
Aug  5 18:20:41 portatil kernel: [    0.000000]   1 base 000000000 mask F00000000 write-back
Aug  5 18:20:41 portatil kernel: [    0.000000]   2 base 100000000 mask FE0000000 write-back
Aug  5 18:20:41 portatil kernel: [    0.000000]   3 disabled
Aug  5 18:20:41 portatil kernel: [    0.000000]   4 disabled
Aug  5 18:20:41 portatil kernel: [    0.000000]   5 disabled
Aug  5 18:20:41 portatil kernel: [    0.000000]   6 disabled
Aug  5 18:20:41 portatil kernel: [    0.000000]   7 disabled
Aug  5 18:20:41 portatil kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  5 18:20:41 portatil kernel: [    0.000000] original variable MTRRs
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 0, base: 3584MB, range: 512MB, type UC
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 1, base: 0GB, range: 4GB, type WB
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 2, base: 4GB, range: 512MB, type WB
Aug  5 18:20:41 portatil kernel: [    0.000000] total RAM covered: 4096M
Aug  5 18:20:41 portatil kernel: [    0.000000] Found optimal setting for mtrr clean up
Aug  5 18:20:41 portatil kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 3  	lose cover RAM: 0G
Aug  5 18:20:41 portatil kernel: [    0.000000] New variable MTRRs
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
Aug  5 18:20:41 portatil kernel: [    0.000000] reg 2, base: 4GB, range: 512MB, type WB
Aug  5 18:20:41 portatil kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Aug  5 18:20:41 portatil kernel: [    0.000000] last_pfn = 0xdffa8 max_arch_pfn = 0x400000000
Aug  5 18:20:41 portatil kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Aug  5 18:20:41 portatil kernel: [    0.000000] initial memory mapped : 0 - 20000000
Aug  5 18:20:41 portatil kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Aug  5 18:20:41 portatil kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dffa8000
Aug  5 18:20:41 portatil kernel: [    0.000000]  0000000000 - 00dfe00000 page 2M
Aug  5 18:20:41 portatil kernel: [    0.000000]  00dfe00000 - 00dffa8000 page 4k
Aug  5 18:20:41 portatil kernel: [    0.000000] kernel direct mapping tables up to dffa8000 @ 1fffa000-20000000
Aug  5 18:20:41 portatil kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Aug  5 18:20:41 portatil kernel: [    0.000000]  0100000000 - 0120000000 page 2M
Aug  5 18:20:41 portatil kernel: [    0.000000] kernel direct mapping tables up to 120000000 @ dffa2000-dffa8000
Aug  5 18:20:41 portatil kernel: [    0.000000] RAMDISK: 357aa000 - 36bcd000
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: RSDP 00000000000fa510 00024 (v02 ACPIAM)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: XSDT 00000000dffb0100 0007C (v01 _ASUS_ Notebook 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: FACP 00000000dffb0290 000F4 (v03 062210 FACP1140 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: DSDT 00000000dffb06f0 0E698 (v01  A1559 A1559215 00000215 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: FACS 00000000dffbff00 00040
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: APIC 00000000dffb0390 00080 (v01 062210 APIC1140 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: MCFG 00000000dffb0450 0003C (v01 062210 OEMMCFG  20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: SLIC 00000000dffb0490 00176 (v01 _ASUS_ Notebook 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: WDRT 00000000dffb0610 00047 (v01 062210 NV-WDRT  20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: ECDT 00000000dffb0690 00054 (v01 062210 OEMECDT  20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: DBGP 00000000dffb0410 00034 (v01 062210 DBGP1140 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: BOOT 00000000dffb0660 00028 (v01 062210 BOOT1140 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: OEMB 00000000dffbff40 00079 (v01 062210 OEMB1140 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: HPET 00000000dffbf6f0 00038 (v01 062210 OEMHPET0 20100622 MSFT 00000097)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: SSDT 00000000dffc0cf0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  5 18:20:41 portatil kernel: [    0.000000] No NUMA configuration found
Aug  5 18:20:41 portatil kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Aug  5 18:20:41 portatil kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
Aug  5 18:20:41 portatil kernel: [    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
Aug  5 18:20:41 portatil kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
Aug  5 18:20:41 portatil kernel: [    0.000000] Zone PFN ranges:
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Aug  5 18:20:41 portatil kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Aug  5 18:20:41 portatil kernel: [    0.000000] Movable zone start PFN for each node
Aug  5 18:20:41 portatil kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug  5 18:20:41 portatil kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Aug  5 18:20:41 portatil kernel: [    0.000000]     0: 0x00000100 -> 0x000dffa8
Aug  5 18:20:41 portatil kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Aug  5 18:20:41 portatil kernel: [    0.000000] On node 0 totalpages: 1048374
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA zone: 5 pages reserved
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Aug  5 18:20:41 portatil kernel: [    0.000000]   DMA32 zone: 897000 pages, LIFO batch:31
Aug  5 18:20:41 portatil kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
Aug  5 18:20:41 portatil kernel: [    0.000000]   Normal zone: 129024 pages, LIFO batch:31
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug  5 18:20:41 portatil kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IRQ14 used by override.
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: IRQ15 used by override.
Aug  5 18:20:41 portatil kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  5 18:20:41 portatil kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Aug  5 18:20:41 portatil kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Aug  5 18:20:41 portatil kernel: [    0.000000] nr_irqs_gsi: 40
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000dffa8000 - 00000000dffb0000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000dffb0000 - 00000000dffbf000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000dffbf000 - 00000000dffc0000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000dffc0000 - 00000000dfff0000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000dfff0000 - 00000000e0000000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fec00000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff700000
Aug  5 18:20:41 portatil kernel: [    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
Aug  5 18:20:41 portatil kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
Aug  5 18:20:41 portatil kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug  5 18:20:41 portatil kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Aug  5 18:20:41 portatil kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011fc00000 s83072 r8192 d23424 u524288
Aug  5 18:20:41 portatil kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
Aug  5 18:20:41 portatil kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug  5 18:20:41 portatil kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029937
Aug  5 18:20:41 portatil kernel: [    0.000000] Policy zone: Normal
Aug  5 18:20:41 portatil kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=cef6db15-dbf1-4b34-9536-037319100792 ro quiet splash vt.handoff=7
Aug  5 18:20:41 portatil kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug  5 18:20:41 portatil kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Aug  5 18:20:41 portatil kernel: [    0.000000] Checking aperture...
Aug  5 18:20:41 portatil kernel: [    0.000000] No AGP bridge found
Aug  5 18:20:41 portatil kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Aug  5 18:20:41 portatil kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Aug  5 18:20:41 portatil kernel: [    0.000000] Memory: 4025004k/4718592k available (6556k kernel code, 525096k absent, 168492k reserved, 6644k data, 920k init)
Aug  5 18:20:41 portatil kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug  5 18:20:41 portatil kernel: [    0.000000] Hierarchical RCU implementation.
Aug  5 18:20:41 portatil kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Aug  5 18:20:41 portatil kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Aug  5 18:20:41 portatil kernel: [    0.000000] Extended CMOS year: 2000
Aug  5 18:20:41 portatil kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug  5 18:20:41 portatil kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug  5 18:20:41 portatil kernel: [    0.000000] Console: colour dummy device 80x25
Aug  5 18:20:41 portatil kernel: [    0.000000] console [tty0] enabled
Aug  5 18:20:41 portatil kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Aug  5 18:20:41 portatil kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug  5 18:20:41 portatil kernel: [    0.000000] hpet clockevent registered
Aug  5 18:20:41 portatil kernel: [    0.000000] Fast TSC calibration using PIT
Aug  5 18:20:41 portatil kernel: [    0.000000] Detected 2300.084 MHz processor.
Aug  5 18:20:41 portatil kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4600.16 BogoMIPS (lpj=9200336)
Aug  5 18:20:41 portatil kernel: [    0.004010] pid_max: default: 32768 minimum: 301
Aug  5 18:20:41 portatil kernel: [    0.004041] Security Framework initialized
Aug  5 18:20:41 portatil kernel: [    0.004063] AppArmor: AppArmor initialized
Aug  5 18:20:41 portatil kernel: [    0.004064] Yama: becoming mindful.
Aug  5 18:20:41 portatil kernel: [    0.008228] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug  5 18:20:41 portatil kernel: [    0.010861] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Aug  5 18:20:41 portatil kernel: [    0.012156] Mount-cache hash table entries: 256
Aug  5 18:20:41 portatil kernel: [    0.012351] Initializing cgroup subsys cpuacct
Aug  5 18:20:41 portatil kernel: [    0.012358] Initializing cgroup subsys memory
Aug  5 18:20:41 portatil kernel: [    0.012370] Initializing cgroup subsys devices
Aug  5 18:20:41 portatil kernel: [    0.012373] Initializing cgroup subsys freezer
Aug  5 18:20:41 portatil kernel: [    0.012375] Initializing cgroup subsys blkio
Aug  5 18:20:41 portatil kernel: [    0.012384] Initializing cgroup subsys perf_event
Aug  5 18:20:41 portatil kernel: [    0.012420] CPU: Physical Processor ID: 0
Aug  5 18:20:41 portatil kernel: [    0.012421] CPU: Processor Core ID: 0
Aug  5 18:20:41 portatil kernel: [    0.012424] mce: CPU supports 6 MCE banks
Aug  5 18:20:41 portatil kernel: [    0.012435] CPU0: Thermal monitoring enabled (TM2)
Aug  5 18:20:41 portatil kernel: [    0.012439] using mwait in idle threads.
Aug  5 18:20:41 portatil kernel: [    0.015164] ACPI: Core revision 20110623
Aug  5 18:20:41 portatil kernel: [    0.024016] ftrace: allocating 26993 entries in 106 pages
Aug  5 18:20:41 portatil kernel: [    0.028539] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  5 18:20:41 portatil kernel: [    0.068898] CPU0: Intel Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz stepping 0a
Aug  5 18:20:41 portatil kernel: [    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Aug  5 18:20:41 portatil kernel: [    0.072003] ... version:                2
Aug  5 18:20:41 portatil kernel: [    0.072003] ... bit width:              40
Aug  5 18:20:41 portatil kernel: [    0.072003] ... generic registers:      2
Aug  5 18:20:41 portatil kernel: [    0.072003] ... value mask:             000000ffffffffff
Aug  5 18:20:41 portatil kernel: [    0.072003] ... max period:             000000007fffffff
Aug  5 18:20:41 portatil kernel: [    0.072003] ... fixed-purpose events:   3
Aug  5 18:20:41 portatil kernel: [    0.072003] ... event mask:             0000000700000003
Aug  5 18:20:41 portatil kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Aug  5 18:20:41 portatil kernel: [    0.072003] Booting Node   0, Processors  #1
Aug  5 18:20:41 portatil kernel: [    0.072003] smpboot cpu 1: start_ip = 99000
Aug  5 18:20:41 portatil kernel: [    0.160045] NMI watchdog enabled, takes one hw-pmu counter.
Aug  5 18:20:41 portatil kernel: [    0.160094] Brought up 2 CPUs
Aug  5 18:20:41 portatil kernel: [    0.160097] Total of 2 processors activated (9200.11 BogoMIPS).
Aug  5 18:20:41 portatil kernel: [    0.161206] devtmpfs: initialized
Aug  5 18:20:41 portatil kernel: [    0.161206] EVM: security.selinux
Aug  5 18:20:41 portatil kernel: [    0.161206] EVM: security.SMACK64
Aug  5 18:20:41 portatil kernel: [    0.161206] EVM: security.capability
Aug  5 18:20:41 portatil kernel: [    0.161206] PM: Registering ACPI NVS region at dffa8000 (32768 bytes)
Aug  5 18:20:41 portatil kernel: [    0.161206] PM: Registering ACPI NVS region at dffbff00 (196864 bytes)
Aug  5 18:20:41 portatil kernel: [    0.161206] print_constraints: dummy: 
Aug  5 18:20:41 portatil kernel: [    0.161206] RTC time: 18:20:05, date: 08/05/12
Aug  5 18:20:41 portatil kernel: [    0.161206] NET: Registered protocol family 16
Aug  5 18:20:41 portatil kernel: [    0.161206] Trying to unpack rootfs image as initramfs...
Aug  5 18:20:41 portatil kernel: [    0.161206] ACPI: bus type pci registered
Aug  5 18:20:41 portatil kernel: [    0.161206] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Aug  5 18:20:41 portatil kernel: [    0.161206] PCI: not using MMCONFIG
Aug  5 18:20:41 portatil kernel: [    0.161206] PCI: Using configuration type 1 for base access
Aug  5 18:20:41 portatil kernel: [    0.164707] bio: create slab <bio-0> at 0
Aug  5 18:20:41 portatil kernel: [    0.164812] ACPI: Added _OSI(Module Device)
Aug  5 18:20:41 portatil kernel: [    0.164814] ACPI: Added _OSI(Processor Device)
Aug  5 18:20:41 portatil kernel: [    0.164816] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug  5 18:20:41 portatil kernel: [    0.164818] ACPI: Added _OSI(Processor Aggregator Device)
Aug  5 18:20:41 portatil kernel: [    0.167062] ACPI: EC: EC description table is found, configuring boot EC
Aug  5 18:20:41 portatil kernel: [    0.167069] ACPI: EC: Look up EC in DSDT
Aug  5 18:20:41 portatil kernel: [    0.169444] ACPI: Executed 1 blocks of module-level executable AML code
Aug  5 18:20:41 portatil kernel: [    0.172440] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Aug  5 18:20:41 portatil kernel: [    0.176292] ACPI: SSDT 00000000dffc0290 00206 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.176819] ACPI: Dynamic OEM Table Load:
Aug  5 18:20:41 portatil kernel: [    0.176822] ACPI: SSDT           (null) 00206 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.176945] ACPI: SSDT 00000000dffc0530 007BF (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.177455] ACPI: Dynamic OEM Table Load:
Aug  5 18:20:41 portatil kernel: [    0.177458] ACPI: SSDT           (null) 007BF (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.177648] ACPI: SSDT 00000000dffc01c0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.178167] ACPI: Dynamic OEM Table Load:
Aug  5 18:20:41 portatil kernel: [    0.178170] ACPI: SSDT           (null) 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.178248] ACPI: SSDT 00000000dffc04a0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.178760] ACPI: Dynamic OEM Table Load:
Aug  5 18:20:41 portatil kernel: [    0.178763] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Aug  5 18:20:41 portatil kernel: [    0.179067] ACPI: Interpreter enabled
Aug  5 18:20:41 portatil kernel: [    0.179073] ACPI: (supports S0 S3 S4 S5)
Aug  5 18:20:41 portatil kernel: [    0.179095] ACPI: Using IOAPIC for interrupt routing
Aug  5 18:20:41 portatil kernel: [    0.179125] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Aug  5 18:20:41 portatil kernel: [    0.180166] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
Aug  5 18:20:41 portatil kernel: [    0.194027] ACPI: EC: GPE = 0x27, I/O: command/status = 0x66, data = 0x62
Aug  5 18:20:41 portatil kernel: [    0.194325] ACPI: No dock devices found.
Aug  5 18:20:41 portatil kernel: [    0.194328] HEST: Table not found.
Aug  5 18:20:41 portatil kernel: [    0.194332] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug  5 18:20:41 portatil kernel: [    0.194570] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug  5 18:20:41 portatil kernel: [    0.194782] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Aug  5 18:20:41 portatil kernel: [    0.194785] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Aug  5 18:20:41 portatil kernel: [    0.194788] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug  5 18:20:41 portatil kernel: [    0.194790] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Aug  5 18:20:41 portatil kernel: [    0.194793] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.194795] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.194817] pci 0000:00:00.0: [10de:0a86] type 0 class 0x000600
Aug  5 18:20:41 portatil kernel: [    0.194926] pci 0000:00:00.1: [10de:0a88] type 0 class 0x000500
Aug  5 18:20:41 portatil kernel: [    0.195082] pci 0000:00:03.0: [10de:0aae] type 0 class 0x000601
Aug  5 18:20:41 portatil kernel: [    0.195091] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
Aug  5 18:20:41 portatil kernel: [    0.195140] pci 0000:00:03.1: [10de:0aa4] type 0 class 0x000500
Aug  5 18:20:41 portatil kernel: [    0.195226] pci 0000:00:03.2: [10de:0aa2] type 0 class 0x000c05
Aug  5 18:20:41 portatil kernel: [    0.195240] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
Aug  5 18:20:41 portatil kernel: [    0.195264] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
Aug  5 18:20:41 portatil kernel: [    0.195271] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
Aug  5 18:20:41 portatil kernel: [    0.195310] pci 0000:00:03.2: PME# supported from D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.195316] pci 0000:00:03.2: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.195336] pci 0000:00:03.3: [10de:0a89] type 0 class 0x000500
Aug  5 18:20:41 portatil kernel: [    0.195486] pci 0000:00:03.5: [10de:0aa3] type 0 class 0x000b40
Aug  5 18:20:41 portatil kernel: [    0.195506] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
Aug  5 18:20:41 portatil kernel: [    0.195634] pci 0000:00:04.0: [10de:0aa5] type 0 class 0x000c03
Aug  5 18:20:41 portatil kernel: [    0.195646] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
Aug  5 18:20:41 portatil kernel: [    0.195697] pci 0000:00:04.0: supports D1 D2
Aug  5 18:20:41 portatil kernel: [    0.195699] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.195703] pci 0000:00:04.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.195719] pci 0000:00:04.1: [10de:0aa6] type 0 class 0x000c03
Aug  5 18:20:41 portatil kernel: [    0.195735] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
Aug  5 18:20:41 portatil kernel: [    0.195796] pci 0000:00:04.1: supports D1 D2
Aug  5 18:20:41 portatil kernel: [    0.195798] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.195802] pci 0000:00:04.1: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.195825] pci 0000:00:06.0: [10de:0aa7] type 0 class 0x000c03
Aug  5 18:20:41 portatil kernel: [    0.195837] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
Aug  5 18:20:41 portatil kernel: [    0.195889] pci 0000:00:06.0: supports D1 D2
Aug  5 18:20:41 portatil kernel: [    0.195891] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.195894] pci 0000:00:06.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.195916] pci 0000:00:06.1: [10de:0aa9] type 0 class 0x000c03
Aug  5 18:20:41 portatil kernel: [    0.195933] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
Aug  5 18:20:41 portatil kernel: [    0.196022] pci 0000:00:06.1: supports D1 D2
Aug  5 18:20:41 portatil kernel: [    0.196025] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.196029] pci 0000:00:06.1: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.196053] pci 0000:00:08.0: [10de:0ac0] type 0 class 0x000403
Aug  5 18:20:41 portatil kernel: [    0.196066] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
Aug  5 18:20:41 portatil kernel: [    0.196118] pci 0000:00:08.0: PME# supported from D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.196122] pci 0000:00:08.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.196135] pci 0000:00:09.0: [10de:0aab] type 1 class 0x000604
Aug  5 18:20:41 portatil kernel: [    0.196186] pci 0000:00:0b.0: [10de:0ab9] type 0 class 0x000106
Aug  5 18:20:41 portatil kernel: [    0.196198] pci 0000:00:0b.0: reg 10: [io  0xc080-0xc087]
Aug  5 18:20:41 portatil kernel: [    0.196205] pci 0000:00:0b.0: reg 14: [io  0xc000-0xc003]
Aug  5 18:20:41 portatil kernel: [    0.196212] pci 0000:00:0b.0: reg 18: [io  0xbc00-0xbc07]
Aug  5 18:20:41 portatil kernel: [    0.196218] pci 0000:00:0b.0: reg 1c: [io  0xb880-0xb883]
Aug  5 18:20:41 portatil kernel: [    0.196225] pci 0000:00:0b.0: reg 20: [io  0xb800-0xb80f]
Aug  5 18:20:41 portatil kernel: [    0.196231] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
Aug  5 18:20:41 portatil kernel: [    0.196318] pci 0000:00:0c.0: [10de:0ac4] type 1 class 0x000604
Aug  5 18:20:41 portatil kernel: [    0.196548] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.196556] pci 0000:00:0c.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.196647] pci 0000:00:15.0: [10de:0ac6] type 1 class 0x000604
Aug  5 18:20:41 portatil kernel: [    0.196875] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.196883] pci 0000:00:15.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.196963] pci 0000:00:16.0: [10de:0ac7] type 1 class 0x000604
Aug  5 18:20:41 portatil kernel: [    0.197191] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.197199] pci 0000:00:16.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.197301] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197308] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197311] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197313] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197316] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197318] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xfbffffff] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197321] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
Aug  5 18:20:41 portatil kernel: [    0.197486] pci 0000:02:00.0: [10de:0a75] type 0 class 0x000300
Aug  5 18:20:41 portatil kernel: [    0.197506] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.197525] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.197544] pci 0000:02:00.0: reg 1c: [mem 0xf6000000-0xf7ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.197557] pci 0000:02:00.0: reg 24: [io  0xdc00-0xdc7f]
Aug  5 18:20:41 portatil kernel: [    0.197570] pci 0000:02:00.0: reg 30: [mem 0xfaf80000-0xfaffffff pref]
Aug  5 18:20:41 portatil kernel: [    0.197690] pci 0000:02:00.1: [10de:0be3] type 0 class 0x000403
Aug  5 18:20:41 portatil kernel: [    0.197706] pci 0000:02:00.1: reg 10: [mem 0xfaf7c000-0xfaf7ffff]
Aug  5 18:20:41 portatil kernel: [    0.204062] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
Aug  5 18:20:41 portatil kernel: [    0.204078] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
Aug  5 18:20:41 portatil kernel: [    0.204086] pci 0000:00:0c.0:   bridge window [mem 0xfaf00000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.204101] pci 0000:00:0c.0:   bridge window [mem 0xe0000000-0xf7ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.204267] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
Aug  5 18:20:41 portatil kernel: [    0.204282] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
Aug  5 18:20:41 portatil kernel: [    0.204306] pci 0000:03:00.0: reg 18: [mem 0xf9fff000-0xf9ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.204322] pci 0000:03:00.0: reg 20: [mem 0xf9ff8000-0xf9ffbfff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.204333] pci 0000:03:00.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
Aug  5 18:20:41 portatil kernel: [    0.204395] pci 0000:03:00.0: supports D1 D2
Aug  5 18:20:41 portatil kernel: [    0.204397] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.204402] pci 0000:03:00.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.212050] pci 0000:00:15.0: PCI bridge to [bus 03-03]
Aug  5 18:20:41 portatil kernel: [    0.212066] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
Aug  5 18:20:41 portatil kernel: [    0.212075] pci 0000:00:15.0:   bridge window [mem 0xfea00000-0xfeafffff]
Aug  5 18:20:41 portatil kernel: [    0.212090] pci 0000:00:15.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.212258] pci 0000:04:00.0: [168c:002b] type 0 class 0x000280
Aug  5 18:20:41 portatil kernel: [    0.212279] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
Aug  5 18:20:41 portatil kernel: [    0.212373] pci 0000:04:00.0: supports D1
Aug  5 18:20:41 portatil kernel: [    0.212376] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
Aug  5 18:20:41 portatil kernel: [    0.212381] pci 0000:04:00.0: PME# disabled
Aug  5 18:20:41 portatil kernel: [    0.220049] pci 0000:00:16.0: PCI bridge to [bus 04-04]
Aug  5 18:20:41 portatil kernel: [    0.220072] pci 0000:00:16.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.220139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  5 18:20:41 portatil kernel: [    0.220285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
Aug  5 18:20:41 portatil kernel: [    0.220347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
Aug  5 18:20:41 portatil kernel: [    0.220394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
Aug  5 18:20:41 portatil kernel: [    0.220433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Aug  5 18:20:41 portatil kernel: [    0.220599]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug  5 18:20:41 portatil kernel: [    0.220770]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
Aug  5 18:20:41 portatil kernel: [    0.220772] ACPI _OSC control for PCIe not granted, disabling ASPM
Aug  5 18:20:41 portatil kernel: [    0.227405] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.227499] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.227596] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.227684] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.227782] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *15
Aug  5 18:20:41 portatil kernel: [    0.227873] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.227962] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228068] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228158] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228247] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228336] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228424] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228514] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228602] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228691] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228779] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.228876] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
Aug  5 18:20:41 portatil kernel: [    0.228965] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229053] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229142] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229235] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *9
Aug  5 18:20:41 portatil kernel: [    0.229323] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229412] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229501] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229591] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229680] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229770] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229859] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.229948] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230037] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230132] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230220] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230312] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
Aug  5 18:20:41 portatil kernel: [    0.230402] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
Aug  5 18:20:41 portatil kernel: [    0.230490] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230580] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Aug  5 18:20:41 portatil kernel: [    0.230668] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.230760] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *14
Aug  5 18:20:41 portatil kernel: [    0.230850] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
Aug  5 18:20:41 portatil kernel: [    0.230940] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Aug  5 18:20:41 portatil kernel: [    0.231040] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.231130] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *9
Aug  5 18:20:41 portatil kernel: [    0.231221] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *15
Aug  5 18:20:41 portatil kernel: [    0.231312] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
Aug  5 18:20:41 portatil kernel: [    0.231405] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.231495] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.231586] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
Aug  5 18:20:41 portatil kernel: [    0.231677] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
Aug  5 18:20:41 portatil kernel: [    0.231766] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.231855] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *0, disabled.
Aug  5 18:20:41 portatil kernel: [    0.232065] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug  5 18:20:41 portatil kernel: [    0.232070] vgaarb: loaded
Aug  5 18:20:41 portatil kernel: [    0.232071] vgaarb: bridge control possible 0000:02:00.0
Aug  5 18:20:41 portatil kernel: [    0.232183] i2c-core: driver [aat2870] using legacy suspend method
Aug  5 18:20:41 portatil kernel: [    0.232185] i2c-core: driver [aat2870] using legacy resume method
Aug  5 18:20:41 portatil kernel: [    0.232264] SCSI subsystem initialized
Aug  5 18:20:41 portatil kernel: [    0.232351] libata version 3.00 loaded.
Aug  5 18:20:41 portatil kernel: [    0.232404] usbcore: registered new interface driver usbfs
Aug  5 18:20:41 portatil kernel: [    0.232418] usbcore: registered new interface driver hub
Aug  5 18:20:41 portatil kernel: [    0.232451] usbcore: registered new device driver usb
Aug  5 18:20:41 portatil kernel: [    0.232565] PCI: Using ACPI for IRQ routing
Aug  5 18:20:41 portatil kernel: [    0.233453] PCI: pci_cache_line_size set to 64 bytes
Aug  5 18:20:41 portatil kernel: [    0.233578] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
Aug  5 18:20:41 portatil kernel: [    0.233581] reserve RAM buffer: 00000000dffa8000 - 00000000dfffffff 
Aug  5 18:20:41 portatil kernel: [    0.233714] NetLabel: Initializing
Aug  5 18:20:41 portatil kernel: [    0.233716] NetLabel:  domain hash size = 128
Aug  5 18:20:41 portatil kernel: [    0.233718] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  5 18:20:41 portatil kernel: [    0.233732] NetLabel:  unlabeled traffic allowed by default
Aug  5 18:20:41 portatil kernel: [    0.233810] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Aug  5 18:20:41 portatil kernel: [    0.233818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
Aug  5 18:20:41 portatil kernel: [    0.233823] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
Aug  5 18:20:41 portatil kernel: [    0.240144] Switching to clocksource hpet
Aug  5 18:20:41 portatil kernel: [    0.249035] AppArmor: AppArmor Filesystem Enabled
Aug  5 18:20:41 portatil kernel: [    0.249090] pnp: PnP ACPI init
Aug  5 18:20:41 portatil kernel: [    0.249112] ACPI: bus type pnp registered
Aug  5 18:20:41 portatil kernel: [    0.249278] pnp 00:00: [bus 00-ff]
Aug  5 18:20:41 portatil kernel: [    0.249281] pnp 00:00: [io  0x0cf8-0x0cff]
Aug  5 18:20:41 portatil kernel: [    0.249283] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug  5 18:20:41 portatil kernel: [    0.249286] pnp 00:00: [io  0x0d00-0xffff window]
Aug  5 18:20:41 portatil kernel: [    0.249288] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug  5 18:20:41 portatil kernel: [    0.249290] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Aug  5 18:20:41 portatil kernel: [    0.249292] pnp 00:00: [mem 0xe0000000-0xfbffffff window]
Aug  5 18:20:41 portatil kernel: [    0.249294] pnp 00:00: [mem 0xfe000000-0xfebfffff window]
Aug  5 18:20:41 portatil kernel: [    0.249404] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Aug  5 18:20:41 portatil kernel: [    0.249435] pnp 00:01: [dma 4]
Aug  5 18:20:41 portatil kernel: [    0.249437] pnp 00:01: [io  0x0000-0x000f]
Aug  5 18:20:41 portatil kernel: [    0.249439] pnp 00:01: [io  0x0081-0x0083]
Aug  5 18:20:41 portatil kernel: [    0.249441] pnp 00:01: [io  0x0087]
Aug  5 18:20:41 portatil kernel: [    0.249443] pnp 00:01: [io  0x0089-0x008b]
Aug  5 18:20:41 portatil kernel: [    0.249444] pnp 00:01: [io  0x008f]
Aug  5 18:20:41 portatil kernel: [    0.249446] pnp 00:01: [io  0x00c0-0x00df]
Aug  5 18:20:41 portatil kernel: [    0.249476] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Aug  5 18:20:41 portatil kernel: [    0.249507] pnp 00:02: [io  0x0060]
Aug  5 18:20:41 portatil kernel: [    0.249509] pnp 00:02: [io  0x0064]
Aug  5 18:20:41 portatil kernel: [    0.249522] pnp 00:02: [irq 1]
Aug  5 18:20:41 portatil kernel: [    0.249547] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Aug  5 18:20:41 portatil kernel: [    0.249593] pnp 00:03: [irq 12]
Aug  5 18:20:41 portatil kernel: [    0.249626] pnp 00:03: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Aug  5 18:20:41 portatil kernel: [    0.249636] pnp 00:04: [io  0x0061]
Aug  5 18:20:41 portatil kernel: [    0.249662] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Aug  5 18:20:41 portatil kernel: [    0.249671] pnp 00:05: [io  0x00f0-0x00ff]
Aug  5 18:20:41 portatil kernel: [    0.249676] pnp 00:05: [irq 13]
Aug  5 18:20:41 portatil kernel: [    0.249699] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug  5 18:20:41 portatil kernel: [    0.249950] pnp 00:06: [mem 0x000d0000-0x000d3fff window]
Aug  5 18:20:41 portatil kernel: [    0.249953] pnp 00:06: [mem 0x000d4000-0x000d7fff window]
Aug  5 18:20:41 portatil kernel: [    0.249955] pnp 00:06: [mem 0x000de000-0x000dffff window]
Aug  5 18:20:41 portatil kernel: [    0.249958] pnp 00:06: [io  0x0010-0x001f]
Aug  5 18:20:41 portatil kernel: [    0.249959] pnp 00:06: [io  0x0022-0x003f]
Aug  5 18:20:41 portatil kernel: [    0.249961] pnp 00:06: [io  0x0044-0x004d]
Aug  5 18:20:41 portatil kernel: [    0.249963] pnp 00:06: [io  0x0050-0x005f]
Aug  5 18:20:41 portatil kernel: [    0.249965] pnp 00:06: [io  0x0062-0x0063]
Aug  5 18:20:41 portatil kernel: [    0.249967] pnp 00:06: [io  0x0065-0x006f]
Aug  5 18:20:41 portatil kernel: [    0.249971] pnp 00:06: [io  0x0072-0x007f]
Aug  5 18:20:41 portatil kernel: [    0.249973] pnp 00:06: [io  0x0080]
Aug  5 18:20:41 portatil kernel: [    0.249975] pnp 00:06: [io  0x0084-0x0086]
Aug  5 18:20:41 portatil kernel: [    0.249976] pnp 00:06: [io  0x0088]
Aug  5 18:20:41 portatil kernel: [    0.249978] pnp 00:06: [io  0x008c-0x008e]
Aug  5 18:20:41 portatil kernel: [    0.249980] pnp 00:06: [io  0x0090-0x009f]
Aug  5 18:20:41 portatil kernel: [    0.249981] pnp 00:06: [io  0x00a2-0x00bf]
Aug  5 18:20:41 portatil kernel: [    0.249983] pnp 00:06: [io  0x00e0-0x00ef]
Aug  5 18:20:41 portatil kernel: [    0.249985] pnp 00:06: [io  0x04d0-0x04d1]
Aug  5 18:20:41 portatil kernel: [    0.249987] pnp 00:06: [io  0x0800-0x080f]
Aug  5 18:20:41 portatil kernel: [    0.249988] pnp 00:06: [io  0x4000-0x407f]
Aug  5 18:20:41 portatil kernel: [    0.249990] pnp 00:06: [io  0x4080-0x40ff]
Aug  5 18:20:41 portatil kernel: [    0.249992] pnp 00:06: [io  0x4400-0x447f]
Aug  5 18:20:41 portatil kernel: [    0.249993] pnp 00:06: [io  0x4480-0x44ff]
Aug  5 18:20:41 portatil kernel: [    0.249995] pnp 00:06: [io  0x4800-0x487f]
Aug  5 18:20:41 portatil kernel: [    0.249997] pnp 00:06: [io  0x4880-0x48ff]
Aug  5 18:20:41 portatil kernel: [    0.249999] pnp 00:06: [mem 0x00000000-0xffffffffffffffff disabled]
Aug  5 18:20:41 portatil kernel: [    0.250002] pnp 00:06: [mem 0xfefe2000-0xfefe3fff]
Aug  5 18:20:41 portatil kernel: [    0.250003] pnp 00:06: [mem 0x00000000-0xffffffffffffffff disabled]
Aug  5 18:20:41 portatil kernel: [    0.250005] pnp 00:06: [mem 0xfee01000-0xfeefffff]
Aug  5 18:20:41 portatil kernel: [    0.250007] pnp 00:06: [mem 0xfed01000-0xfed01fff]
Aug  5 18:20:41 portatil kernel: [    0.250097] system 00:06: [io  0x04d0-0x04d1] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250100] system 00:06: [io  0x0800-0x080f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250103] system 00:06: [io  0x4000-0x407f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250105] system 00:06: [io  0x4080-0x40ff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250107] system 00:06: [io  0x4400-0x447f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250110] system 00:06: [io  0x4480-0x44ff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250112] system 00:06: [io  0x4800-0x487f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250115] system 00:06: [io  0x4880-0x48ff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250118] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250121] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250123] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250127] system 00:06: [mem 0xfefe2000-0xfefe3fff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250129] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250132] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250135] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  5 18:20:41 portatil kernel: [    0.250238] pnp 00:07: [mem 0xfed00000-0xfed00fff]
Aug  5 18:20:41 portatil kernel: [    0.250241] pnp 00:07: [irq 2 disabled]
Aug  5 18:20:41 portatil kernel: [    0.250249] pnp 00:07: [irq 8]
Aug  5 18:20:41 portatil kernel: [    0.250286] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Aug  5 18:20:41 portatil kernel: [    0.250310] pnp 00:08: [io  0x0070-0x0071]
Aug  5 18:20:41 portatil kernel: [    0.250338] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug  5 18:20:41 portatil kernel: [    0.250380] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Aug  5 18:20:41 portatil kernel: [    0.250382] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Aug  5 18:20:41 portatil kernel: [    0.250384] pnp 00:09: [io  0x0250-0x0253]
Aug  5 18:20:41 portatil kernel: [    0.250386] pnp 00:09: [io  0x0256-0x025f]
Aug  5 18:20:41 portatil kernel: [    0.250432] system 00:09: [io  0x0250-0x0253] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250435] system 00:09: [io  0x0256-0x025f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250438] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.250441] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250444] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  5 18:20:41 portatil kernel: [    0.250484] pnp 00:0a: [io  0x0260-0x026f]
Aug  5 18:20:41 portatil kernel: [    0.250533] system 00:0a: [io  0x0260-0x026f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250537] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  5 18:20:41 portatil kernel: [    0.250574] pnp 00:0b: [io  0x5000-0x507f]
Aug  5 18:20:41 portatil kernel: [    0.250576] pnp 00:0b: [io  0x5080-0x50ff]
Aug  5 18:20:41 portatil kernel: [    0.250622] system 00:0b: [io  0x5000-0x507f] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250625] system 00:0b: [io  0x5080-0x50ff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250628] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  5 18:20:41 portatil kernel: [    0.250676] pnp 00:0c: [mem 0xfc000000-0xfdffffff]
Aug  5 18:20:41 portatil kernel: [    0.250721] system 00:0c: [mem 0xfc000000-0xfdffffff] has been reserved
Aug  5 18:20:41 portatil kernel: [    0.250724] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  5 18:20:41 portatil kernel: [    0.250938] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Aug  5 18:20:41 portatil kernel: [    0.250940] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Aug  5 18:20:41 portatil kernel: [    0.250943] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Aug  5 18:20:41 portatil kernel: [    0.250945] pnp 00:0d: [mem 0x00100000-0xdfffffff]
Aug  5 18:20:41 portatil kernel: [    0.250947] pnp 00:0d: [mem 0xfc000000-0xffffffff]
Aug  5 18:20:41 portatil kernel: [    0.251023] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.251026] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.251029] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.251032] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.251034] system 00:0d: [mem 0xfc000000-0xffffffff] could not be reserved
Aug  5 18:20:41 portatil kernel: [    0.251038] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Aug  5 18:20:41 portatil kernel: [    0.251701] pnp: PnP ACPI: found 14 devices
Aug  5 18:20:41 portatil kernel: [    0.251704] ACPI: ACPI bus type pnp unregistered
Aug  5 18:20:41 portatil kernel: [    0.258220] PCI: max bus depth: 1 pci_try_num: 2
Aug  5 18:20:41 portatil kernel: [    0.258302] pci 0000:00:09.0: PCI bridge to [bus 01-01]
Aug  5 18:20:41 portatil kernel: [    0.258312] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
Aug  5 18:20:41 portatil kernel: [    0.258318] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
Aug  5 18:20:41 portatil kernel: [    0.258329] pci 0000:00:0c.0:   bridge window [mem 0xfaf00000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.258337] pci 0000:00:0c.0:   bridge window [mem 0xe0000000-0xf7ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.258351] pci 0000:00:15.0: PCI bridge to [bus 03-03]
Aug  5 18:20:41 portatil kernel: [    0.258357] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
Aug  5 18:20:41 portatil kernel: [    0.258367] pci 0000:00:15.0:   bridge window [mem 0xfea00000-0xfeafffff]
Aug  5 18:20:41 portatil kernel: [    0.258375] pci 0000:00:15.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.258388] pci 0000:00:16.0: PCI bridge to [bus 04-04]
Aug  5 18:20:41 portatil kernel: [    0.258399] pci 0000:00:16.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.258427] pci 0000:00:09.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.258636] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
Aug  5 18:20:41 portatil kernel: [    0.258656] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
Aug  5 18:20:41 portatil kernel: [    0.258665] pci 0000:00:0c.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.258808] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
Aug  5 18:20:41 portatil kernel: [    0.258816] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
Aug  5 18:20:41 portatil kernel: [    0.258825] pci 0000:00:15.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.258966] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
Aug  5 18:20:41 portatil kernel: [    0.258974] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
Aug  5 18:20:41 portatil kernel: [    0.258983] pci 0000:00:16.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.258989] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug  5 18:20:41 portatil kernel: [    0.258992] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug  5 18:20:41 portatil kernel: [    0.258994] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug  5 18:20:41 portatil kernel: [    0.258996] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Aug  5 18:20:41 portatil kernel: [    0.258999] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.259001] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.259004] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
Aug  5 18:20:41 portatil kernel: [    0.259007] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
Aug  5 18:20:41 portatil kernel: [    0.259010] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
Aug  5 18:20:41 portatil kernel: [    0.259013] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
Aug  5 18:20:41 portatil kernel: [    0.259016] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.259019] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.259023] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Aug  5 18:20:41 portatil kernel: [    0.259026] pci_bus 0000:02: resource 1 [mem 0xfaf00000-0xfbffffff]
Aug  5 18:20:41 portatil kernel: [    0.259029] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xf7ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.259033] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Aug  5 18:20:41 portatil kernel: [    0.259036] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
Aug  5 18:20:41 portatil kernel: [    0.259039] pci_bus 0000:03: resource 2 [mem 0xf9f00000-0xf9ffffff 64bit pref]
Aug  5 18:20:41 portatil kernel: [    0.259042] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
Aug  5 18:20:41 portatil kernel: [    0.259101] NET: Registered protocol family 2
Aug  5 18:20:41 portatil kernel: [    0.259267] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Aug  5 18:20:41 portatil kernel: [    0.260707] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Aug  5 18:20:41 portatil kernel: [    0.266650] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug  5 18:20:41 portatil kernel: [    0.267378] TCP: Hash tables configured (established 524288 bind 65536)
Aug  5 18:20:41 portatil kernel: [    0.267382] TCP reno registered
Aug  5 18:20:41 portatil kernel: [    0.267398] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Aug  5 18:20:41 portatil kernel: [    0.267446] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Aug  5 18:20:41 portatil kernel: [    0.267655] NET: Registered protocol family 1
Aug  5 18:20:41 portatil kernel: [    0.267933] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
Aug  5 18:20:41 portatil kernel: [    0.267955] pci 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
Aug  5 18:20:41 portatil kernel: [    0.356066] pci 0000:00:04.0: PCI INT A disabled
Aug  5 18:20:41 portatil kernel: [    0.356285] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
Aug  5 18:20:41 portatil kernel: [    0.356291] pci 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
Aug  5 18:20:41 portatil kernel: [    0.356327] pci 0000:00:04.1: PCI INT B disabled
Aug  5 18:20:41 portatil kernel: [    0.356468] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
Aug  5 18:20:41 portatil kernel: [    0.356473] pci 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
Aug  5 18:20:41 portatil kernel: [    0.428057] pci 0000:00:06.0: PCI INT A disabled
Aug  5 18:20:41 portatil kernel: [    0.428288] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
Aug  5 18:20:41 portatil kernel: [    0.428295] pci 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
Aug  5 18:20:41 portatil kernel: [    0.428332] pci 0000:00:06.1: PCI INT B disabled
Aug  5 18:20:41 portatil kernel: [    0.428488] pci 0000:02:00.0: Boot video device
Aug  5 18:20:41 portatil kernel: [    0.428511] PCI: CLS 64 bytes, default 64
Aug  5 18:20:41 portatil kernel: [    0.428515] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug  5 18:20:41 portatil kernel: [    0.428517] Placing 64MB software IO TLB between ffff8800dbfa2000 - ffff8800dffa2000
Aug  5 18:20:41 portatil kernel: [    0.428520] software IO TLB at phys 0xdbfa2000 - 0xdffa2000
Aug  5 18:20:41 portatil kernel: [    0.428533] Simple Boot Flag at 0xef set to 0x1
Aug  5 18:20:41 portatil kernel: [    0.428950] audit: initializing netlink socket (disabled)
Aug  5 18:20:41 portatil kernel: [    0.428964] type=2000 audit(1344190805.424:1): initialized
Aug  5 18:20:41 portatil kernel: [    0.468359] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug  5 18:20:41 portatil kernel: [    0.505493] VFS: Disk quotas dquot_6.5.2
Aug  5 18:20:41 portatil kernel: [    0.505560] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug  5 18:20:41 portatil kernel: [    0.506125] fuse init (API version 7.17)
Aug  5 18:20:41 portatil kernel: [    0.506226] msgmni has been set to 7861
Aug  5 18:20:41 portatil kernel: [    0.506610] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug  5 18:20:41 portatil kernel: [    0.506645] io scheduler noop registered
Aug  5 18:20:41 portatil kernel: [    0.506647] io scheduler deadline registered
Aug  5 18:20:41 portatil kernel: [    0.506690] io scheduler cfq registered (default)
Aug  5 18:20:41 portatil kernel: [    0.507196] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  5 18:20:41 portatil kernel: [    0.507221] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  5 18:20:41 portatil kernel: [    0.507287] intel_idle: MWAIT substates: 0x2220
Aug  5 18:20:41 portatil kernel: [    0.507289] intel_idle: does not run on family 6 model 23
Aug  5 18:20:41 portatil kernel: [    0.507398] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug  5 18:20:41 portatil kernel: [    0.507460] ACPI: AC Adapter [AC0] (on-line)
Aug  5 18:20:41 portatil kernel: [    0.507572] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Aug  5 18:20:41 portatil kernel: [    0.507579] ACPI: Power Button [PWRB]
Aug  5 18:20:41 portatil kernel: [    0.507623] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Aug  5 18:20:41 portatil kernel: [    0.507626] ACPI: Sleep Button [SLPB]
Aug  5 18:20:41 portatil kernel: [    0.507674] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Aug  5 18:20:41 portatil kernel: [    0.509620] ACPI: Lid Switch [LID]
Aug  5 18:20:41 portatil kernel: [    0.509695] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug  5 18:20:41 portatil kernel: [    0.509701] ACPI: Power Button [PWRF]
Aug  5 18:20:41 portatil kernel: [    0.512308] Monitor-Mwait will be used to enter C-1 state
Aug  5 18:20:41 portatil kernel: [    0.512658] Monitor-Mwait will be used to enter C-2 state
Aug  5 18:20:41 portatil kernel: [    0.513165] Monitor-Mwait will be used to enter C-3 state
Aug  5 18:20:41 portatil kernel: [    0.513175] Marking TSC unstable due to TSC halts in idle
Aug  5 18:20:41 portatil kernel: [    0.513189] ACPI: acpi_idle registered with cpuidle
Aug  5 18:20:41 portatil kernel: [    0.521011] thermal LNXTHERM:00: registered as thermal_zone0
Aug  5 18:20:41 portatil kernel: [    0.521015] ACPI: Thermal Zone [THRM] (46 C)
Aug  5 18:20:41 portatil kernel: [    0.521064] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug  5 18:20:41 portatil kernel: [    0.521075] ACPI: Battery Slot [BAT0] (battery absent)
Aug  5 18:20:41 portatil kernel: [    0.521165] ERST: Table is not found!
Aug  5 18:20:41 portatil kernel: [    0.521167] GHES: HEST is not enabled!
Aug  5 18:20:41 portatil kernel: [    0.521288] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug  5 18:20:41 portatil kernel: [    0.521524] ACPI: Battery Slot [BAT0] (battery absent)
Aug  5 18:20:41 portatil kernel: [    0.617919] Freeing initrd memory: 20620k freed
Aug  5 18:20:41 portatil kernel: [    0.700490] Linux agpgart interface v0.103
Aug  5 18:20:41 portatil kernel: [    0.702136] brd: module loaded
Aug  5 18:20:41 portatil kernel: [    0.703020] loop: module loaded
Aug  5 18:20:41 portatil kernel: [    0.703185] ahci 0000:00:0b.0: version 3.0
Aug  5 18:20:41 portatil kernel: [    0.703373] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
Aug  5 18:20:41 portatil kernel: [    0.703379] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
Aug  5 18:20:41 portatil kernel: [    0.703448] ahci 0000:00:0b.0: irq 40 for MSI/MSI-X
Aug  5 18:20:41 portatil kernel: [    0.703518] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl SATA mode
Aug  5 18:20:41 portatil kernel: [    0.703522] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
Aug  5 18:20:41 portatil kernel: [    0.703526] ahci 0000:00:0b.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.704283] scsi0 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704389] scsi1 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704477] scsi2 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704561] scsi3 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704647] scsi4 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704731] scsi5 : ahci
Aug  5 18:20:41 portatil kernel: [    0.704871] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 40
Aug  5 18:20:41 portatil kernel: [    0.704875] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 40
Aug  5 18:20:41 portatil kernel: [    0.704877] ata3: DUMMY
Aug  5 18:20:41 portatil kernel: [    0.704878] ata4: DUMMY
Aug  5 18:20:41 portatil kernel: [    0.704879] ata5: DUMMY
Aug  5 18:20:41 portatil kernel: [    0.704881] ata6: DUMMY
Aug  5 18:20:41 portatil kernel: [    0.705281] Fixed MDIO Bus: probed
Aug  5 18:20:41 portatil kernel: [    0.705301] tun: Universal TUN/TAP device driver, 1.6
Aug  5 18:20:41 portatil kernel: [    0.705303] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  5 18:20:41 portatil kernel: [    0.705410] PPP generic driver version 2.4.2
Aug  5 18:20:41 portatil kernel: [    0.705563] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  5 18:20:41 portatil kernel: [    0.705596] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
Aug  5 18:20:41 portatil kernel: [    0.705622] ehci_hcd 0000:00:04.1: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.705625] ehci_hcd 0000:00:04.1: EHCI Host Controller
Aug  5 18:20:41 portatil kernel: [    0.705676] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
Aug  5 18:20:41 portatil kernel: [    0.705706] ehci_hcd 0000:00:04.1: debug port 1
Aug  5 18:20:41 portatil kernel: [    0.705714] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Aug  5 18:20:41 portatil kernel: [    0.705738] ehci_hcd 0000:00:04.1: irq 23, io mem 0xfae7ec00
Aug  5 18:20:41 portatil kernel: [    0.716014] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Aug  5 18:20:41 portatil kernel: [    0.716178] hub 1-0:1.0: USB hub found
Aug  5 18:20:41 portatil kernel: [    0.716183] hub 1-0:1.0: 11 ports detected
Aug  5 18:20:41 portatil kernel: [    0.716271] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
Aug  5 18:20:41 portatil kernel: [    0.716286] ehci_hcd 0000:00:06.1: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.716289] ehci_hcd 0000:00:06.1: EHCI Host Controller
Aug  5 18:20:41 portatil kernel: [    0.716340] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
Aug  5 18:20:41 portatil kernel: [    0.716359] ehci_hcd 0000:00:06.1: debug port 1
Aug  5 18:20:41 portatil kernel: [    0.716367] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
Aug  5 18:20:41 portatil kernel: [    0.716383] ehci_hcd 0000:00:06.1: irq 21, io mem 0xfae7e800
Aug  5 18:20:41 portatil kernel: [    0.728018] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
Aug  5 18:20:41 portatil kernel: [    0.728147] hub 2-0:1.0: USB hub found
Aug  5 18:20:41 portatil kernel: [    0.728153] hub 2-0:1.0: 1 port detected
Aug  5 18:20:41 portatil kernel: [    0.728222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  5 18:20:41 portatil kernel: [    0.728241] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
Aug  5 18:20:41 portatil kernel: [    0.728257] ohci_hcd 0000:00:04.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.728260] ohci_hcd 0000:00:04.0: OHCI Host Controller
Aug  5 18:20:41 portatil kernel: [    0.728317] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
Aug  5 18:20:41 portatil kernel: [    0.728343] ohci_hcd 0000:00:04.0: irq 20, io mem 0xfae7f000
Aug  5 18:20:41 portatil kernel: [    0.786129] hub 3-0:1.0: USB hub found
Aug  5 18:20:41 portatil kernel: [    0.786135] hub 3-0:1.0: 11 ports detected
Aug  5 18:20:41 portatil kernel: [    0.786211] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
Aug  5 18:20:41 portatil kernel: [    0.786225] ohci_hcd 0000:00:06.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    0.786227] ohci_hcd 0000:00:06.0: OHCI Host Controller
Aug  5 18:20:41 portatil kernel: [    0.786283] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
Aug  5 18:20:41 portatil kernel: [    0.786307] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
Aug  5 18:20:41 portatil kernel: [    0.842133] hub 4-0:1.0: USB hub found
Aug  5 18:20:41 portatil kernel: [    0.842139] hub 4-0:1.0: 1 port detected
Aug  5 18:20:41 portatil kernel: [    0.842200] uhci_hcd: USB Universal Host Controller Interface driver
Aug  5 18:20:41 portatil kernel: [    0.842265] usbcore: registered new interface driver libusual
Aug  5 18:20:41 portatil kernel: [    0.842312] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug  5 18:20:41 portatil kernel: [    0.846275] i8042: Detected active multiplexing controller, rev 1.1
Aug  5 18:20:41 portatil kernel: [    0.848320] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  5 18:20:41 portatil kernel: [    0.848327] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug  5 18:20:41 portatil kernel: [    0.848362] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug  5 18:20:41 portatil kernel: [    0.848388] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug  5 18:20:41 portatil kernel: [    0.848414] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug  5 18:20:41 portatil kernel: [    0.848559] mousedev: PS/2 mouse device common for all mice
Aug  5 18:20:41 portatil kernel: [    0.848807] rtc_cmos 00:08: RTC can wake from S4
Aug  5 18:20:41 portatil kernel: [    0.849018] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Aug  5 18:20:41 portatil kernel: [    0.849069] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Aug  5 18:20:41 portatil kernel: [    0.849155] device-mapper: uevent: version 1.0.3
Aug  5 18:20:41 portatil kernel: [    0.849236] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Aug  5 18:20:41 portatil kernel: [    0.849302] cpuidle: using governor ladder
Aug  5 18:20:41 portatil kernel: [    0.849390] cpuidle: using governor menu
Aug  5 18:20:41 portatil kernel: [    0.849392] EFI Variables Facility v0.08 2004-May-17
Aug  5 18:20:41 portatil kernel: [    0.849639] TCP cubic registered
Aug  5 18:20:41 portatil kernel: [    0.849745] NET: Registered protocol family 10
Aug  5 18:20:41 portatil kernel: [    0.850238] NET: Registered protocol family 17
Aug  5 18:20:41 portatil kernel: [    0.850244] Registering the dns_resolver key type
Aug  5 18:20:41 portatil kernel: [    0.850436] PM: Hibernation image not present or could not be loaded.
Aug  5 18:20:41 portatil kernel: [    0.850452] registered taskstats version 1
Aug  5 18:20:41 portatil kernel: [    0.872878]   Magic number: 8:567:341
Aug  5 18:20:41 portatil kernel: [    0.873064] rtc_cmos 00:08: setting system clock to 2012-08-05 18:20:06 UTC (1344190806)
Aug  5 18:20:41 portatil kernel: [    0.873904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  5 18:20:41 portatil kernel: [    0.873907] EDD information not available.
Aug  5 18:20:41 portatil kernel: [    0.887847] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug  5 18:20:41 portatil kernel: [    1.024043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  5 18:20:41 portatil kernel: [    1.024069] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug  5 18:20:41 portatil kernel: [    1.027489] ata2.00: ATAPI: HL-DT-STDVDRAM GT32N, AS01, max UDMA/100
Aug  5 18:20:41 portatil kernel: [    1.030733] ata2.00: configured for UDMA/100
Aug  5 18:20:41 portatil kernel: [    1.073714] ata1.00: ATA-8: WDC WD6400BEVT-80A0RT0, 01.01A01, max UDMA/133
Aug  5 18:20:41 portatil kernel: [    1.073720] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
Aug  5 18:20:41 portatil kernel: [    1.076190] ata1.00: configured for UDMA/133
Aug  5 18:20:41 portatil kernel: [    1.076433] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BEVT-8 01.0 PQ: 0 ANSI: 5
Aug  5 18:20:41 portatil kernel: [    1.076598] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Aug  5 18:20:41 portatil kernel: [    1.076622] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  5 18:20:41 portatil kernel: [    1.076647] sd 0:0:0:0: [sda] Write Protect is off
Aug  5 18:20:41 portatil kernel: [    1.076651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  5 18:20:41 portatil kernel: [    1.076672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  5 18:20:41 portatil kernel: [    1.078657] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT32N     AS01 PQ: 0 ANSI: 5
Aug  5 18:20:41 portatil kernel: [    1.082784] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug  5 18:20:41 portatil kernel: [    1.082790] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug  5 18:20:41 portatil kernel: [    1.082973] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug  5 18:20:41 portatil kernel: [    1.083056] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug  5 18:20:41 portatil kernel: [    1.084083] usb 1-7: new high-speed USB device number 3 using ehci_hcd
Aug  5 18:20:41 portatil kernel: [    1.172976]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
Aug  5 18:20:41 portatil kernel: [    1.173767] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  5 18:20:41 portatil kernel: [    1.175376] Freeing unused kernel memory: 920k freed
Aug  5 18:20:41 portatil kernel: [    1.175735] Write protecting the kernel read-only data: 12288k
Aug  5 18:20:41 portatil kernel: [    1.181232] Freeing unused kernel memory: 1616k freed
Aug  5 18:20:41 portatil kernel: [    1.186089] Freeing unused kernel memory: 1200k freed
Aug  5 18:20:41 portatil kernel: [    1.352226] acpi device:0c: registered as cooling_device2
Aug  5 18:20:41 portatil kernel: [    1.352320] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/LNXVIDEO:00/input/input5
Aug  5 18:20:41 portatil kernel: [    1.352600] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug  5 18:20:41 portatil kernel: [    1.360847] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  5 18:20:41 portatil kernel: [    1.360872] r8169 0000:03:00.0: enabling device (0001 -> 0003)
Aug  5 18:20:41 portatil kernel: [    1.361081] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
Aug  5 18:20:41 portatil kernel: [    1.361099] r8169 0000:03:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
Aug  5 18:20:41 portatil kernel: [    1.361141] r8169 0000:03:00.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [    1.361188] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
Aug  5 18:20:41 portatil kernel: [    1.361648] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc90000654000, 20:cf:30:4a:d2:6a, XID 083000c0 IRQ 41
Aug  5 18:20:41 portatil kernel: [    1.361652] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug  5 18:20:41 portatil kernel: [    1.544066] usb 3-1: new low-speed USB device number 2 using ohci_hcd
Aug  5 18:20:41 portatil kernel: [    1.772370] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input6
Aug  5 18:20:41 portatil kernel: [    1.772558] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:04.0-1/input0
Aug  5 18:20:41 portatil kernel: [    1.772580] usbcore: registered new interface driver usbhid
Aug  5 18:20:41 portatil kernel: [    1.772582] usbhid: USB HID core driver
Aug  5 18:20:41 portatil kernel: [    3.022975] vesafb: mode is 640x480x32, linelength=2560, pages=0
Aug  5 18:20:41 portatil kernel: [    3.022978] vesafb: scrolling: redraw
Aug  5 18:20:41 portatil kernel: [    3.022980] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Aug  5 18:20:41 portatil kernel: [    3.022990] mtrr: type mismatch for f7000000,200000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.022993] mtrr: type mismatch for f7000000,100000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.022996] mtrr: type mismatch for f7000000,80000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.022999] mtrr: type mismatch for f7000000,40000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023002] mtrr: type mismatch for f7000000,20000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023005] mtrr: type mismatch for f7000000,10000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023008] mtrr: type mismatch for f7000000,8000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023012] mtrr: type mismatch for f7000000,4000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023014] mtrr: type mismatch for f7000000,2000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023017] mtrr: type mismatch for f7000000,1000 old: write-back new: write-combining
Aug  5 18:20:41 portatil kernel: [    3.023323] vesafb: framebuffer at 0xf7000000, mapped to 0xffffc90003100000, using 1216k, total 1216k
Aug  5 18:20:41 portatil kernel: [    3.023459] Console: switching to colour frame buffer device 80x30
Aug  5 18:20:41 portatil kernel: [    3.023473] fb0: VESA VGA frame buffer device
Aug  5 18:20:41 portatil kernel: [    3.464689] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
Aug  5 18:20:41 portatil kernel: [    3.464694] EXT4-fs (sda6): write access will be enabled during recovery
Aug  5 18:20:41 portatil kernel: [   11.861758] EXT4-fs (sda6): recovery complete
Aug  5 18:20:41 portatil kernel: [   11.862266] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug  5 18:20:41 portatil kernel: [   34.655551] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 18:20:41 portatil kernel: [   34.758454] Adding 4206588k swap on /dev/sda7.  Priority:-1 extents:1 across:4206588k 
Aug  5 18:20:41 portatil kernel: [   34.765004] lp: driver loaded but no devices found
Aug  5 18:20:41 portatil kernel: [   34.816146] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
Aug  5 18:20:41 portatil kernel: [   34.816152] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [io 0x4e00-0x4e3f]
Aug  5 18:20:41 portatil kernel: [   34.816155] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug  5 18:20:41 portatil kernel: [   34.849359] asus_laptop: Asus Laptop Support version 0.42
Aug  5 18:20:41 portatil kernel: [   34.849515] asus_laptop: BSTS called, 0xf353 returned
Aug  5 18:20:41 portatil kernel: [   34.849527] asus_laptop:   K50IE model detected
Aug  5 18:20:41 portatil kernel: [   34.860096] asus_laptop: Backlight controlled by ACPI video driver
Aug  5 18:20:41 portatil kernel: [   34.860312] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input7
Aug  5 18:20:41 portatil kernel: [   34.865930] Registered led device: asus::mail
Aug  5 18:20:41 portatil kernel: [   34.867577] Registered led device: asus::touchpad
Aug  5 18:20:41 portatil kernel: [   34.946439] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Aug  5 18:20:41 portatil kernel: [   35.018008] nvidia: module license 'NVIDIA' taints kernel.
Aug  5 18:20:41 portatil kernel: [   35.018014] Disabling lock debugging due to kernel taint
Aug  5 18:20:41 portatil kernel: [   35.091372] wmi: Mapper loaded
Aug  5 18:20:41 portatil kernel: [   35.218767] cfg80211: Calling CRDA to update world regulatory domain
Aug  5 18:20:41 portatil kernel: [   35.270201] Linux video capture interface: v2.00
Aug  5 18:20:41 portatil kernel: [   35.270963] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
Aug  5 18:20:41 portatil kernel: [   35.279099] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:04.1/usb1/1-7/1-7:1.0/input/input8
Aug  5 18:20:41 portatil kernel: [   35.279245] usbcore: registered new interface driver uvcvideo
Aug  5 18:20:41 portatil kernel: [   35.279248] USB Video Class driver (1.1.1)
Aug  5 18:20:41 portatil kernel: [   35.301694] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
Aug  5 18:20:41 portatil kernel: [   35.301700] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
Aug  5 18:20:41 portatil kernel: [   35.301876] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
Aug  5 18:20:41 portatil kernel: [   35.301882] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
Aug  5 18:20:41 portatil kernel: [   35.301885] hda_intel: Disabling MSI
Aug  5 18:20:41 portatil kernel: [   35.301917] snd_hda_intel 0000:00:08.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [   35.410963] Bluetooth: Core ver 2.16
Aug  5 18:20:41 portatil kernel: [   35.411407] NET: Registered protocol family 31
Aug  5 18:20:41 portatil kernel: [   35.411412] Bluetooth: HCI device and connection manager initialized
Aug  5 18:20:41 portatil kernel: [   35.411415] Bluetooth: HCI socket layer initialized
Aug  5 18:20:41 portatil kernel: [   35.411418] Bluetooth: L2CAP socket layer initialized
Aug  5 18:20:41 portatil kernel: [   35.411427] Bluetooth: SCO socket layer initialized
Aug  5 18:20:41 portatil kernel: [   35.422194] ppdev: user-space parallel port driver
Aug  5 18:20:41 portatil kernel: [   35.432861] type=1400 audit(1344183641.058:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=779 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   35.433333] type=1400 audit(1344183641.058:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=779 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   35.433577] type=1400 audit(1344183641.058:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=779 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   35.434173] Bluetooth: RFCOMM TTY layer initialized
Aug  5 18:20:41 portatil kernel: [   35.434180] Bluetooth: RFCOMM socket layer initialized
Aug  5 18:20:41 portatil kernel: [   35.434182] Bluetooth: RFCOMM ver 1.11
Aug  5 18:20:41 portatil kernel: [   35.449429] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug  5 18:20:41 portatil kernel: [   35.449432] Bluetooth: BNEP filters: protocol multicast
Aug  5 18:20:41 portatil kernel: [   35.459860] type=1400 audit(1344183641.082:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   35.460536] type=1400 audit(1344183641.086:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
Aug  5 18:20:41 portatil dbus[706]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug  5 18:20:41 portatil kernel: [   35.571404] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040101)
Aug  5 18:20:41 portatil dbus[706]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug  5 18:20:41 portatil kernel: [   35.603002] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 18
Aug  5 18:20:41 portatil kernel: [   35.603023] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
Aug  5 18:20:41 portatil kernel: [   35.603034] ath9k 0000:04:00.0: setting latency timer to 64
Aug  5 18:20:41 portatil kernel: [   35.674752] ath: EEPROM regdomain: 0x60
Aug  5 18:20:41 portatil kernel: [   35.674755] ath: EEPROM indicates we should expect a direct regpair map
Aug  5 18:20:41 portatil kernel: [   35.674759] ath: Country alpha2 being used: 00
Aug  5 18:20:41 portatil kernel: [   35.674761] ath: Regpair used: 0x60
Aug  5 18:20:41 portatil kernel: [   35.674765] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674770] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674775] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674779] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674784] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674789] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674792] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674794] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674799] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674803] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674808] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674813] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674818] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674821] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674823] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674826] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.674828] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Aug  5 18:20:41 portatil kernel: [   35.674831] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   35.722017] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug  5 18:20:41 portatil kernel: [   35.735959] psmouse serio4: elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
Aug  5 18:20:41 portatil kernel: [   35.783705] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug  5 18:20:41 portatil kernel: [   35.784402] Registered led device: ath9k-phy0
Aug  5 18:20:41 portatil kernel: [   35.784415] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900030e0000, irq=18
Aug  5 18:20:41 portatil failsafe: Failsafe of 120 seconds reached.
Aug  5 18:20:41 portatil kernel: [   35.876649] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input9
Aug  5 18:20:41 portatil kernel: [   35.946598] init: failsafe main process (870) killed by TERM signal
Aug  5 18:20:41 portatil modem-manager[948]: <info>  ModemManager (version 0.5.2.0) starting...
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin AnyData
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin SimTech
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Longcheer
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Ericsson MBM
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Gobi
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Linktop
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin X22X
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin ZTE
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Huawei
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin MotoC
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Generic
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Nokia
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Option High-Speed
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Novatel
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Samsung
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Wavecom
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Option
Aug  5 18:20:41 portatil modem-manager[948]: <info>  Loaded plugin Sierra
Aug  5 18:20:41 portatil NetworkManager[959]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug  5 18:20:41 portatil NetworkManager[959]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug  5 18:20:41 portatil NetworkManager[959]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug  5 18:20:41 portatil NetworkManager[959]: <info> DNS: loaded plugin dnsmasq
Aug  5 18:20:41 portatil dbus[706]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug  5 18:20:41 portatil udev-configure-printer: add /module/lp
Aug  5 18:20:41 portatil udev-configure-printer: Failed to get parent
Aug  5 18:20:41 portatil polkitd[976]: started daemon version 0.104 using authority implementation `local' version `0.104'
Aug  5 18:20:41 portatil dbus[706]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: init!
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: update_system_hostname
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPluginIfupdown: management mode: unmanaged
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/eth0, iface: eth0)
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: end _init.
Aug  5 18:20:41 portatil NetworkManager[959]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug  5 18:20:41 portatil NetworkManager[959]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug  5 18:20:41 portatil NetworkManager[959]:    Ifupdown: get unmanaged devices count: 0
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: (39790752) ... get_connections.
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: (39790752) ... get_connections (managed=false): return empty list.
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing Simyo Predeterminado ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'Simyo Predeterminado'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing WLAN-MA ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'WLAN-MA'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing Auto WLAN_5C12 ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'Auto WLAN_5C12'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing Auto eth0 ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'Auto eth0'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing WLAN_2FE5 ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'WLAN_2FE5'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing Simyo Predeterminado-75471036-c63f-4148-b5c5-418f0fdc69d3 ... 
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'Simyo Predeterminado'
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile: parsing Auto WLAN_CF5E ... 
Aug  5 18:20:41 portatil kernel: [   36.067868] type=1400 audit(1344183641.690:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1000 comm="apparmor_parser"
Aug  5 18:20:41 portatil NetworkManager[959]:    keyfile:     read connection 'Auto WLAN_CF5E'
Aug  5 18:20:41 portatil NetworkManager[959]:    Ifupdown: get unmanaged devices count: 0
Aug  5 18:20:41 portatil NetworkManager[959]: <info> modem-manager is now available
Aug  5 18:20:41 portatil NetworkManager[959]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug  5 18:20:41 portatil kernel: [   36.073212] type=1400 audit(1344183641.698:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1001 comm="apparmor_parser"
Aug  5 18:20:41 portatil NetworkManager[959]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Aug  5 18:20:41 portatil kernel: [   36.077664] type=1400 audit(1344183641.702:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1002 comm="apparmor_parser"
Aug  5 18:20:41 portatil NetworkManager[959]: <info> WiFi enabled by radio killswitch; disabled by state file
Aug  5 18:20:41 portatil NetworkManager[959]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug  5 18:20:41 portatil NetworkManager[959]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug  5 18:20:41 portatil NetworkManager[959]: <info> Networking is enabled by state file
Aug  5 18:20:41 portatil NetworkManager[959]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): carrier is OFF
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): now managed
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): bringing up device.
Aug  5 18:20:41 portatil kernel: [   36.088596] type=1400 audit(1344183641.714:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1002 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   36.088839] type=1400 audit(1344183641.714:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1002 comm="apparmor_parser"
Aug  5 18:20:41 portatil kernel: [   36.135032] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug  5 18:20:41 portatil kernel: [   36.135037] cfg80211: World regulatory domain updated:
Aug  5 18:20:41 portatil kernel: [   36.135039] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug  5 18:20:41 portatil kernel: [   36.135042] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   36.135044] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   36.135047] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   36.135049] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   36.135052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  5 18:20:41 portatil kernel: [   36.262650] r8169 0000:03:00.0: eth0: link down
Aug  5 18:20:41 portatil kernel: [   36.262660] r8169 0000:03:00.0: eth0: link down
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): preparing device.
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug  5 18:20:41 portatil NetworkManager[959]: <error> [1344183641.894474] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): using nl80211 for WiFi device control
Aug  5 18:20:41 portatil NetworkManager[959]: <warn> (wlan0): driver supports Access Point (AP) mode
Aug  5 18:20:41 portatil kernel: [   36.264623] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 18:20:41 portatil kernel: [   36.265043] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): now managed
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): bringing up device.
Aug  5 18:20:41 portatil NetworkManager[959]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug  5 18:20:41 portatil kernel: [   36.269203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Aug  5 18:20:41 portatil NetworkManager[959]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug  5 18:20:41 portatil kernel: [   36.342442] init: alsa-restore main process (1108) terminated with status 19
Aug  5 18:20:41 portatil anacron[1143]: Anacron 2.3 started on 2012-08-05
Aug  5 18:20:41 portatil acpid: starting up with proc fs
Aug  5 18:20:41 portatil acpid: 35 rules loaded
Aug  5 18:20:41 portatil acpid: waiting for events: event logging is off
Aug  5 18:20:41 portatil cron[1109]: (CRON) INFO (pidfile fd = 3)
Aug  5 18:20:42 portatil cron[1151]: (CRON) STARTUP (fork ok)
Aug  5 18:20:42 portatil kernel: [   36.395608] init: gdm main process (1147) killed by TERM signal
Aug  5 18:20:42 portatil cron[1151]: (CRON) INFO (Running @reboot jobs)
Aug  5 18:20:42 portatil kernel: [   36.616617] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
Aug  5 18:20:42 portatil kernel: [   36.616832] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
Aug  5 18:20:42 portatil kernel: [   36.617461] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 17
Aug  5 18:20:42 portatil kernel: [   36.617481] snd_hda_intel 0000:02:00.1: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
Aug  5 18:20:42 portatil kernel: [   36.617484] hda_intel: Disabling MSI
Aug  5 18:20:42 portatil kernel: [   36.617556] snd_hda_intel 0000:02:00.1: setting latency timer to 64
Aug  5 18:20:42 portatil kernel: [   36.617768] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
Aug  5 18:20:42 portatil kernel: [   36.617772] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 22 (level, low) -> IRQ 22
Aug  5 18:20:42 portatil acpid: client connected from 1189[0:0]
Aug  5 18:20:42 portatil acpid: 1 client rule loaded
Aug  5 18:20:42 portatil anacron[1143]: Normal exit (0 jobs run)
Aug  5 18:20:42 portatil kernel: [   37.271076] vboxdrv: Found 2 processor cores.
Aug  5 18:20:42 portatil kernel: [   37.271377] vboxdrv: fAsync=0 offMin=0x24b offMax=0x1dc8
Aug  5 18:20:42 portatil kernel: [   37.271463] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug  5 18:20:42 portatil kernel: [   37.271465] vboxdrv: Successfully loaded version 4.1.18 (interface 0x00190000).
Aug  5 18:20:42 portatil kernel: [   37.343028] init: lightdm main process (1171) terminated with status 1
Aug  5 18:20:43 portatil kernel: [   37.448093] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Aug  5 18:20:43 portatil kernel: [   37.472067] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Aug  5 18:20:43 portatil kernel: [   37.484904] vboxpci: IOMMU not found (not registered)
Aug  5 18:20:43 portatil kernel: [   37.496086] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Aug  5 18:20:43 portatil kernel: [   37.520053] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Aug  5 18:20:43 portatil kernel: [   37.520206] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input12
Aug  5 18:20:43 portatil kernel: [   37.520398] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input13
Aug  5 18:20:43 portatil kernel: [   37.520541] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input14
Aug  5 18:20:43 portatil kernel: [   37.520681] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input15
Aug  5 18:20:43 portatil kernel: [   37.521488] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
Aug  5 18:20:43 portatil kernel: [   37.521506] nvidia 0000:02:00.0: setting latency timer to 64
Aug  5 18:20:43 portatil kernel: [   37.521513] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Aug  5 18:20:43 portatil kernel: [   37.521901] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
Aug  5 18:20:43 portatil acpid: client 1189[0:0] has disconnected
Aug  5 18:20:43 portatil acpid: client connected from 1344[0:0]
Aug  5 18:20:43 portatil acpid: 1 client rule loaded
Aug  5 18:20:43 portatil kernel: [   37.855584] r8169 0000:03:00.0: eth0: link up
Aug  5 18:20:43 portatil kernel: [   37.856227] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  5 18:20:43 portatil sm-mta[1350]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Aug  5 18:20:43 portatil NetworkManager[959]: <info> (eth0): carrier now ON (device state 20)
Aug  5 18:20:43 portatil NetworkManager[959]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Auto-activating connection 'Auto eth0'.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) starting connection 'Auto eth0'
Aug  5 18:20:43 portatil NetworkManager[959]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug  5 18:20:43 portatil NetworkManager[959]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug  5 18:20:44 portatil NetworkManager[959]: <info> DNS: starting dnsmasq...
Aug  5 18:20:44 portatil NetworkManager[959]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug  5 18:20:44 portatil dnsmasq[1379]: iniciado, versión 2.59 caché desactivada
Aug  5 18:20:44 portatil dnsmasq[1379]: opciones al compilar: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug  5 18:20:44 portatil dnsmasq[1379]: se usa el servidor 8.8.4.4#53
Aug  5 18:20:44 portatil dnsmasq[1379]: se usa el servidor 8.8.8.8#53
Aug  5 18:20:44 portatil NetworkManager[959]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug  5 18:20:44 portatil NetworkManager[959]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Aug  5 18:20:44 portatil NetworkManager[959]: <info> Activation (eth0) successful, device activated.
Aug  5 18:20:44 portatil NetworkManager[959]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug  5 18:20:44 portatil dbus[706]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug  5 18:20:44 portatil dbus[706]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  5 18:20:45 portatil anacron[1608]: Anacron 2.3 started on 2012-08-05
Aug  5 18:20:45 portatil anacron[1608]: Normal exit (0 jobs run)
Aug  5 18:20:46 portatil kernel: [   40.433588] init: plymouth-stop pre-start process (1703) terminated with status 1
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1710]: Upgrading MySQL tables if necessary.
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1713]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1713]: Looking for 'mysql' as: /usr/bin/mysql
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1713]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1713]: This installation of MySQL is already upgraded to 5.5.24, use --force if you still need to run mysql_upgrade
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1724]: Checking for insecure root accounts.
Aug  5 18:20:46 portatil /etc/mysql/debian-start[1729]: Triggering myisam-recover for all MyISAM tables
Aug  5 18:20:52 portatil ntpdate[1443]: step time server 91.189.94.4 offset -0.641091 sec
Aug  5 18:20:53 portatil kernel: [   48.584080] eth0: no IPv6 routers present
Aug  5 18:20:57 portatil kernel: [   52.800153] init: failsafe-x main process (1228) terminated with status 1
Aug  5 18:21:06 portatil kernel: [   61.772101] usb 3-1: USB disconnect, device number 2
Aug  5 18:21:08 portatil kernel: [   63.372072] usb 3-1: new low-speed USB device number 3 using ohci_hcd
Aug  5 18:21:08 portatil mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:04.0/usb3/3-1"
Aug  5 18:21:08 portatil mtp-probe: bus: 3, device: 3 was not an MTP device
Aug  5 18:21:08 portatil kernel: [   63.598379] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input16
Aug  5 18:21:08 portatil kernel: [   63.598575] generic-usb 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:04.0-1/input0
Aug  5 18:21:42 portatil dbus[706]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug  5 18:21:42 portatil dbus[706]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug  5 18:22:08 portatil kernel: [  123.598103] usb 3-1: USB disconnect, device number 3
Aug  5 18:22:10 portatil kernel: [  125.200065] usb 3-1: new low-speed USB device number 4 using ohci_hcd
Aug  5 18:22:10 portatil mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:04.0/usb3/3-1"
Aug  5 18:22:10 portatil mtp-probe: bus: 3, device: 4 was not an MTP device
Aug  5 18:22:10 portatil kernel: [  125.426517] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input17
Aug  5 18:22:10 portatil kernel: [  125.426800] generic-usb 0003:093A:2510.0003: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:04.0-1/input0

---

### Post by maminyana on 2012-08-05
And this is dmesg
#######################################
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-27-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 (Ubuntu 3.2.0-27.43-generic 3.2.21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=cef6db15-dbf1-4b34-9536-037319100792 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dffa8000 (usable)
[    0.000000]  BIOS-e820: 00000000dffa8000 - 00000000dffb0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dffb0000 - 00000000dffbff00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dffbff00 - 00000000dfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.5 present.
[    0.000000] DMI: ASUSTeK Computer Inc.  K50IE               /K50IE     , BIOS 215     06/22/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 512MB, type WB
[    0.000000] total RAM covered: 4096M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 4GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdffa8 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dffa8000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dffa8000 page 4k
[    0.000000] kernel direct mapping tables up to dffa8000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ dffa2000-dffa8000
[    0.000000] RAMDISK: 357aa000 - 36bcd000
[    0.000000] ACPI: RSDP 00000000000fa510 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000dffb0100 0007C (v01 _ASUS_ Notebook 20100622 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000dffb0290 000F4 (v03 062210 FACP1140 20100622 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000dffb06f0 0E698 (v01  A1559 A1559215 00000215 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dffbff00 00040
[    0.000000] ACPI: APIC 00000000dffb0390 00080 (v01 062210 APIC1140 20100622 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000dffb0450 0003C (v01 062210 OEMMCFG  20100622 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000dffb0490 00176 (v01 _ASUS_ Notebook 20100622 MSFT 00000097)
[    0.000000] ACPI: WDRT 00000000dffb0610 00047 (v01 062210 NV-WDRT  20100622 MSFT 00000097)
[    0.000000] ACPI: ECDT 00000000dffb0690 00054 (v01 062210 OEMECDT  20100622 MSFT 00000097)
[    0.000000] ACPI: DBGP 00000000dffb0410 00034 (v01 062210 DBGP1140 20100622 MSFT 00000097)
[    0.000000] ACPI: BOOT 00000000dffb0660 00028 (v01 062210 BOOT1140 20100622 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000dffbff40 00079 (v01 062210 OEMB1140 20100622 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000dffbf6f0 00038 (v01 062210 OEMHPET0 20100622 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000dffc0cf0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000dffa8
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1048374
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 897000 pages, LIFO batch:31
[    0.000000]   Normal zone: 2048 pages used for memmap
[    0.000000]   Normal zone: 129024 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dffa8000 - 00000000dffb0000
[    0.000000] PM: Registered nosave memory: 00000000dffb0000 - 00000000dffbf000
[    0.000000] PM: Registered nosave memory: 00000000dffbf000 - 00000000dffc0000
[    0.000000] PM: Registered nosave memory: 00000000dffc0000 - 00000000dfff0000
[    0.000000] PM: Registered nosave memory: 00000000dfff0000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011fc00000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029937
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=cef6db15-dbf1-4b34-9536-037319100792 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4025004k/4718592k available (6556k kernel code, 525096k absent, 168492k reserved, 6644k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2300.084 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4600.16 BogoMIPS (lpj=9200336)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004064] Yama: becoming mindful.
[    0.008228] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010861] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012156] Mount-cache hash table entries: 256
[    0.012351] Initializing cgroup subsys cpuacct
[    0.012358] Initializing cgroup subsys memory
[    0.012370] Initializing cgroup subsys devices
[    0.012373] Initializing cgroup subsys freezer
[    0.012375] Initializing cgroup subsys blkio
[    0.012384] Initializing cgroup subsys perf_event
[    0.012420] CPU: Physical Processor ID: 0
[    0.012421] CPU: Processor Core ID: 0
[    0.012424] mce: CPU supports 6 MCE banks
[    0.012435] CPU0: Thermal monitoring enabled (TM2)
[    0.012439] using mwait in idle threads.
[    0.015164] ACPI: Core revision 20110623
[    0.024016] ftrace: allocating 26993 entries in 106 pages
[    0.028539] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068898] CPU0: Intel Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Booting Node   0, Processors  #1
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.160045] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160094] Brought up 2 CPUs
[    0.160097] Total of 2 processors activated (9200.11 BogoMIPS).
[    0.161206] devtmpfs: initialized
[    0.161206] EVM: security.selinux
[    0.161206] EVM: security.SMACK64
[    0.161206] EVM: security.capability
[    0.161206] PM: Registering ACPI NVS region at dffa8000 (32768 bytes)
[    0.161206] PM: Registering ACPI NVS region at dffbff00 (196864 bytes)
[    0.161206] print_constraints: dummy: 
[    0.161206] RTC time: 18:20:05, date: 08/05/12
[    0.161206] NET: Registered protocol family 16
[    0.161206] Trying to unpack rootfs image as initramfs...
[    0.161206] ACPI: bus type pci registered
[    0.161206] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.161206] PCI: not using MMCONFIG
[    0.161206] PCI: Using configuration type 1 for base access
[    0.164707] bio: create slab <bio-0> at 0
[    0.164812] ACPI: Added _OSI(Module Device)
[    0.164814] ACPI: Added _OSI(Processor Device)
[    0.164816] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.164818] ACPI: Added _OSI(Processor Aggregator Device)
[    0.167062] ACPI: EC: EC description table is found, configuring boot EC
[    0.167069] ACPI: EC: Look up EC in DSDT
[    0.169444] ACPI: Executed 1 blocks of module-level executable AML code
[    0.172440] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.176292] ACPI: SSDT 00000000dffc0290 00206 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.176819] ACPI: Dynamic OEM Table Load:
[    0.176822] ACPI: SSDT           (null) 00206 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.176945] ACPI: SSDT 00000000dffc0530 007BF (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.177455] ACPI: Dynamic OEM Table Load:
[    0.177458] ACPI: SSDT           (null) 007BF (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.177648] ACPI: SSDT 00000000dffc01c0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.178167] ACPI: Dynamic OEM Table Load:
[    0.178170] ACPI: SSDT           (null) 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.178248] ACPI: SSDT 00000000dffc04a0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.178760] ACPI: Dynamic OEM Table Load:
[    0.178763] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.179067] ACPI: Interpreter enabled
[    0.179073] ACPI: (supports S0 S3 S4 S5)
[    0.179095] ACPI: Using IOAPIC for interrupt routing
[    0.179125] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.180166] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.194027] ACPI: EC: GPE = 0x27, I/O: command/status = 0x66, data = 0x62
[    0.194325] ACPI: No dock devices found.
[    0.194328] HEST: Table not found.
[    0.194332] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.194570] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.194782] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.194785] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.194788] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.194790] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.194793] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfbffffff]
[    0.194795] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.194817] pci 0000:00:00.0: [10de:0a86] type 0 class 0x000600
[    0.194926] pci 0000:00:00.1: [10de:0a88] type 0 class 0x000500
[    0.195082] pci 0000:00:03.0: [10de:0aae] type 0 class 0x000601
[    0.195091] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.195140] pci 0000:00:03.1: [10de:0aa4] type 0 class 0x000500
[    0.195226] pci 0000:00:03.2: [10de:0aa2] type 0 class 0x000c05
[    0.195240] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.195264] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.195271] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.195310] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.195316] pci 0000:00:03.2: PME# disabled
[    0.195336] pci 0000:00:03.3: [10de:0a89] type 0 class 0x000500
[    0.195486] pci 0000:00:03.5: [10de:0aa3] type 0 class 0x000b40
[    0.195506] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.195634] pci 0000:00:04.0: [10de:0aa5] type 0 class 0x000c03
[    0.195646] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.195697] pci 0000:00:04.0: supports D1 D2
[    0.195699] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195703] pci 0000:00:04.0: PME# disabled
[    0.195719] pci 0000:00:04.1: [10de:0aa6] type 0 class 0x000c03
[    0.195735] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.195796] pci 0000:00:04.1: supports D1 D2
[    0.195798] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195802] pci 0000:00:04.1: PME# disabled
[    0.195825] pci 0000:00:06.0: [10de:0aa7] type 0 class 0x000c03
[    0.195837] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.195889] pci 0000:00:06.0: supports D1 D2
[    0.195891] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195894] pci 0000:00:06.0: PME# disabled
[    0.195916] pci 0000:00:06.1: [10de:0aa9] type 0 class 0x000c03
[    0.195933] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
[    0.196022] pci 0000:00:06.1: supports D1 D2
[    0.196025] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196029] pci 0000:00:06.1: PME# disabled
[    0.196053] pci 0000:00:08.0: [10de:0ac0] type 0 class 0x000403
[    0.196066] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.196118] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.196122] pci 0000:00:08.0: PME# disabled
[    0.196135] pci 0000:00:09.0: [10de:0aab] type 1 class 0x000604
[    0.196186] pci 0000:00:0b.0: [10de:0ab9] type 0 class 0x000106
[    0.196198] pci 0000:00:0b.0: reg 10: [io  0xc080-0xc087]
[    0.196205] pci 0000:00:0b.0: reg 14: [io  0xc000-0xc003]
[    0.196212] pci 0000:00:0b.0: reg 18: [io  0xbc00-0xbc07]
[    0.196218] pci 0000:00:0b.0: reg 1c: [io  0xb880-0xb883]
[    0.196225] pci 0000:00:0b.0: reg 20: [io  0xb800-0xb80f]
[    0.196231] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.196318] pci 0000:00:0c.0: [10de:0ac4] type 1 class 0x000604
[    0.196548] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196556] pci 0000:00:0c.0: PME# disabled
[    0.196647] pci 0000:00:15.0: [10de:0ac6] type 1 class 0x000604
[    0.196875] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196883] pci 0000:00:15.0: PME# disabled
[    0.196963] pci 0000:00:16.0: [10de:0ac7] type 1 class 0x000604
[    0.197191] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197199] pci 0000:00:16.0: PME# disabled
[    0.197301] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.197308] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.197311] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.197313] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.197316] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.197318] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xfbffffff] (subtractive decode)
[    0.197321] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.197486] pci 0000:02:00.0: [10de:0a75] type 0 class 0x000300
[    0.197506] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.197525] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.197544] pci 0000:02:00.0: reg 1c: [mem 0xf6000000-0xf7ffffff 64bit pref]
[    0.197557] pci 0000:02:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.197570] pci 0000:02:00.0: reg 30: [mem 0xfaf80000-0xfaffffff pref]
[    0.197690] pci 0000:02:00.1: [10de:0be3] type 0 class 0x000403
[    0.197706] pci 0000:02:00.1: reg 10: [mem 0xfaf7c000-0xfaf7ffff]
[    0.204062] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.204078] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
[    0.204086] pci 0000:00:0c.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.204101] pci 0000:00:0c.0:   bridge window [mem 0xe0000000-0xf7ffffff 64bit pref]
[    0.204267] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.204282] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.204306] pci 0000:03:00.0: reg 18: [mem 0xf9fff000-0xf9ffffff 64bit pref]
[    0.204322] pci 0000:03:00.0: reg 20: [mem 0xf9ff8000-0xf9ffbfff 64bit pref]
[    0.204333] pci 0000:03:00.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
[    0.204395] pci 0000:03:00.0: supports D1 D2
[    0.204397] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204402] pci 0000:03:00.0: PME# disabled
[    0.212050] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.212066] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.212075] pci 0000:00:15.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.212090] pci 0000:00:15.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.212258] pci 0000:04:00.0: [168c:002b] type 0 class 0x000280
[    0.212279] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.212373] pci 0000:04:00.0: supports D1
[    0.212376] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.212381] pci 0000:04:00.0: PME# disabled
[    0.220049] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.220072] pci 0000:00:16.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.220139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.220285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.220347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.220394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.220433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.220599]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.220770]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
[    0.220772] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.227405] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.227499] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.227596] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.227684] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.227782] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *15
[    0.227873] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.227962] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.228068] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.228158] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.228247] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.228336] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.228424] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.228514] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.228602] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.228691] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.228779] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.228876] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.228965] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.229053] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.229142] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.229235] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *9
[    0.229323] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.229412] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.229501] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.229591] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.229680] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.229770] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.229859] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.229948] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.230037] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.230132] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.230220] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.230312] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.230402] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.230490] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
[    0.230580] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.230668] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.230760] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *14
[    0.230850] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.230940] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.231040] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.231130] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *9
[    0.231221] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *15
[    0.231312] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.231405] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.231495] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.231586] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.231677] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.231766] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *0, disabled.
[    0.231855] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *0, disabled.
[    0.232065] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.232070] vgaarb: loaded
[    0.232071] vgaarb: bridge control possible 0000:02:00.0
[    0.232183] i2c-core: driver [aat2870] using legacy suspend method
[    0.232185] i2c-core: driver [aat2870] using legacy resume method
[    0.232264] SCSI subsystem initialized
[    0.232351] libata version 3.00 loaded.
[    0.232404] usbcore: registered new interface driver usbfs
[    0.232418] usbcore: registered new interface driver hub
[    0.232451] usbcore: registered new device driver usb
[    0.232565] PCI: Using ACPI for IRQ routing
[    0.233453] PCI: pci_cache_line_size set to 64 bytes
[    0.233578] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.233581] reserve RAM buffer: 00000000dffa8000 - 00000000dfffffff 
[    0.233714] NetLabel: Initializing
[    0.233716] NetLabel:  domain hash size = 128
[    0.233718] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.233732] NetLabel:  unlabeled traffic allowed by default
[    0.233810] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.233818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.233823] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.240144] Switching to clocksource hpet
[    0.249035] AppArmor: AppArmor Filesystem Enabled
[    0.249090] pnp: PnP ACPI init
[    0.249112] ACPI: bus type pnp registered
[    0.249278] pnp 00:00: [bus 00-ff]
[    0.249281] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.249283] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.249286] pnp 00:00: [io  0x0d00-0xffff window]
[    0.249288] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.249290] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.249292] pnp 00:00: [mem 0xe0000000-0xfbffffff window]
[    0.249294] pnp 00:00: [mem 0xfe000000-0xfebfffff window]
[    0.249404] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.249435] pnp 00:01: [dma 4]
[    0.249437] pnp 00:01: [io  0x0000-0x000f]
[    0.249439] pnp 00:01: [io  0x0081-0x0083]
[    0.249441] pnp 00:01: [io  0x0087]
[    0.249443] pnp 00:01: [io  0x0089-0x008b]
[    0.249444] pnp 00:01: [io  0x008f]
[    0.249446] pnp 00:01: [io  0x00c0-0x00df]
[    0.249476] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.249507] pnp 00:02: [io  0x0060]
[    0.249509] pnp 00:02: [io  0x0064]
[    0.249522] pnp 00:02: [irq 1]
[    0.249547] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.249593] pnp 00:03: [irq 12]
[    0.249626] pnp 00:03: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.249636] pnp 00:04: [io  0x0061]
[    0.249662] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.249671] pnp 00:05: [io  0x00f0-0x00ff]
[    0.249676] pnp 00:05: [irq 13]
[    0.249699] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.249950] pnp 00:06: [mem 0x000d0000-0x000d3fff window]
[    0.249953] pnp 00:06: [mem 0x000d4000-0x000d7fff window]
[    0.249955] pnp 00:06: [mem 0x000de000-0x000dffff window]
[    0.249958] pnp 00:06: [io  0x0010-0x001f]
[    0.249959] pnp 00:06: [io  0x0022-0x003f]
[    0.249961] pnp 00:06: [io  0x0044-0x004d]
[    0.249963] pnp 00:06: [io  0x0050-0x005f]
[    0.249965] pnp 00:06: [io  0x0062-0x0063]
[    0.249967] pnp 00:06: [io  0x0065-0x006f]
[    0.249971] pnp 00:06: [io  0x0072-0x007f]
[    0.249973] pnp 00:06: [io  0x0080]
[    0.249975] pnp 00:06: [io  0x0084-0x0086]
[    0.249976] pnp 00:06: [io  0x0088]
[    0.249978] pnp 00:06: [io  0x008c-0x008e]
[    0.249980] pnp 00:06: [io  0x0090-0x009f]
[    0.249981] pnp 00:06: [io  0x00a2-0x00bf]
[    0.249983] pnp 00:06: [io  0x00e0-0x00ef]
[    0.249985] pnp 00:06: [io  0x04d0-0x04d1]
[    0.249987] pnp 00:06: [io  0x0800-0x080f]
[    0.249988] pnp 00:06: [io  0x4000-0x407f]
[    0.249990] pnp 00:06: [io  0x4080-0x40ff]
[    0.249992] pnp 00:06: [io  0x4400-0x447f]
[    0.249993] pnp 00:06: [io  0x4480-0x44ff]
[    0.249995] pnp 00:06: [io  0x4800-0x487f]
[    0.249997] pnp 00:06: [io  0x4880-0x48ff]
[    0.249999] pnp 00:06: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.250002] pnp 00:06: [mem 0xfefe2000-0xfefe3fff]
[    0.250003] pnp 00:06: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.250005] pnp 00:06: [mem 0xfee01000-0xfeefffff]
[    0.250007] pnp 00:06: [mem 0xfed01000-0xfed01fff]
[    0.250097] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.250100] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.250103] system 00:06: [io  0x4000-0x407f] has been reserved
[    0.250105] system 00:06: [io  0x4080-0x40ff] has been reserved
[    0.250107] system 00:06: [io  0x4400-0x447f] has been reserved
[    0.250110] system 00:06: [io  0x4480-0x44ff] has been reserved
[    0.250112] system 00:06: [io  0x4800-0x487f] has been reserved
[    0.250115] system 00:06: [io  0x4880-0x48ff] has been reserved
[    0.250118] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.250121] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.250123] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved
[    0.250127] system 00:06: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.250129] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.250132] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
[    0.250135] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250238] pnp 00:07: [mem 0xfed00000-0xfed00fff]
[    0.250241] pnp 00:07: [irq 2 disabled]
[    0.250249] pnp 00:07: [irq 8]
[    0.250286] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.250310] pnp 00:08: [io  0x0070-0x0071]
[    0.250338] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.250380] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.250382] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.250384] pnp 00:09: [io  0x0250-0x0253]
[    0.250386] pnp 00:09: [io  0x0256-0x025f]
[    0.250432] system 00:09: [io  0x0250-0x0253] has been reserved
[    0.250435] system 00:09: [io  0x0256-0x025f] has been reserved
[    0.250438] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.250441] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.250444] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250484] pnp 00:0a: [io  0x0260-0x026f]
[    0.250533] system 00:0a: [io  0x0260-0x026f] has been reserved
[    0.250537] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250574] pnp 00:0b: [io  0x5000-0x507f]
[    0.250576] pnp 00:0b: [io  0x5080-0x50ff]
[    0.250622] system 00:0b: [io  0x5000-0x507f] has been reserved
[    0.250625] system 00:0b: [io  0x5080-0x50ff] has been reserved
[    0.250628] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250676] pnp 00:0c: [mem 0xfc000000-0xfdffffff]
[    0.250721] system 00:0c: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.250724] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250938] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.250940] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.250943] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.250945] pnp 00:0d: [mem 0x00100000-0xdfffffff]
[    0.250947] pnp 00:0d: [mem 0xfc000000-0xffffffff]
[    0.251023] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.251026] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.251029] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.251032] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.251034] system 00:0d: [mem 0xfc000000-0xffffffff] could not be reserved
[    0.251038] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.251701] pnp: PnP ACPI: found 14 devices
[    0.251704] ACPI: ACPI bus type pnp unregistered
[    0.258220] PCI: max bus depth: 1 pci_try_num: 2
[    0.258302] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.258312] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.258318] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
[    0.258329] pci 0000:00:0c.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.258337] pci 0000:00:0c.0:   bridge window [mem 0xe0000000-0xf7ffffff 64bit pref]
[    0.258351] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.258357] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.258367] pci 0000:00:15.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.258375] pci 0000:00:15.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.258388] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.258399] pci 0000:00:16.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.258427] pci 0000:00:09.0: setting latency timer to 64
[    0.258636] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.258656] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.258665] pci 0000:00:0c.0: setting latency timer to 64
[    0.258808] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.258816] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.258825] pci 0000:00:15.0: setting latency timer to 64
[    0.258966] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.258974] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.258983] pci 0000:00:16.0: setting latency timer to 64
[    0.258989] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.258992] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.258994] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.258996] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.258999] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.259001] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.259004] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.259007] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.259010] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.259013] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.259016] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.259019] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.259023] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.259026] pci_bus 0000:02: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.259029] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xf7ffffff 64bit pref]
[    0.259033] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.259036] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.259039] pci_bus 0000:03: resource 2 [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.259042] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.259101] NET: Registered protocol family 2
[    0.259267] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.260707] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.266650] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.267378] TCP: Hash tables configured (established 524288 bind 65536)
[    0.267382] TCP reno registered
[    0.267398] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.267446] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.267655] NET: Registered protocol family 1
[    0.267933] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.267955] pci 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.356066] pci 0000:00:04.0: PCI INT A disabled
[    0.356285] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    0.356291] pci 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    0.356327] pci 0000:00:04.1: PCI INT B disabled
[    0.356468] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    0.356473] pci 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    0.428057] pci 0000:00:06.0: PCI INT A disabled
[    0.428288] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    0.428295] pci 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    0.428332] pci 0000:00:06.1: PCI INT B disabled
[    0.428488] pci 0000:02:00.0: Boot video device
[    0.428511] PCI: CLS 64 bytes, default 64
[    0.428515] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.428517] Placing 64MB software IO TLB between ffff8800dbfa2000 - ffff8800dffa2000
[    0.428520] software IO TLB at phys 0xdbfa2000 - 0xdffa2000
[    0.428533] Simple Boot Flag at 0xef set to 0x1
[    0.428950] audit: initializing netlink socket (disabled)
[    0.428964] type=2000 audit(1344190805.424:1): initialized
[    0.468359] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.505493] VFS: Disk quotas dquot_6.5.2
[    0.505560] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.506125] fuse init (API version 7.17)
[    0.506226] msgmni has been set to 7861
[    0.506610] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.506645] io scheduler noop registered
[    0.506647] io scheduler deadline registered
[    0.506690] io scheduler cfq registered (default)
[    0.507196] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.507221] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.507287] intel_idle: MWAIT substates: 0x2220
[    0.507289] intel_idle: does not run on family 6 model 23
[    0.507398] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.507460] ACPI: AC Adapter [AC0] (on-line)
[    0.507572] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.507579] ACPI: Power Button [PWRB]
[    0.507623] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.507626] ACPI: Sleep Button [SLPB]
[    0.507674] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.509620] ACPI: Lid Switch [LID]
[    0.509695] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.509701] ACPI: Power Button [PWRF]
[    0.512308] Monitor-Mwait will be used to enter C-1 state
[    0.512658] Monitor-Mwait will be used to enter C-2 state
[    0.513165] Monitor-Mwait will be used to enter C-3 state
[    0.513175] Marking TSC unstable due to TSC halts in idle
[    0.513189] ACPI: acpi_idle registered with cpuidle
[    0.521011] thermal LNXTHERM:00: registered as thermal_zone0
[    0.521015] ACPI: Thermal Zone [THRM] (46 C)
[    0.521064] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.521075] ACPI: Battery Slot [BAT0] (battery absent)
[    0.521165] ERST: Table is not found!
[    0.521167] GHES: HEST is not enabled!
[    0.521288] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.521524] ACPI: Battery Slot [BAT0] (battery absent)
[    0.617919] Freeing initrd memory: 20620k freed
[    0.700490] Linux agpgart interface v0.103
[    0.702136] brd: module loaded
[    0.703020] loop: module loaded
[    0.703185] ahci 0000:00:0b.0: version 3.0
[    0.703373] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    0.703379] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    0.703448] ahci 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.703518] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl SATA mode
[    0.703522] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    0.703526] ahci 0000:00:0b.0: setting latency timer to 64
[    0.704283] scsi0 : ahci
[    0.704389] scsi1 : ahci
[    0.704477] scsi2 : ahci
[    0.704561] scsi3 : ahci
[    0.704647] scsi4 : ahci
[    0.704731] scsi5 : ahci
[    0.704871] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 40
[    0.704875] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 40
[    0.704877] ata3: DUMMY
[    0.704878] ata4: DUMMY
[    0.704879] ata5: DUMMY
[    0.704881] ata6: DUMMY
[    0.705281] Fixed MDIO Bus: probed
[    0.705301] tun: Universal TUN/TAP device driver, 1.6
[    0.705303] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.705410] PPP generic driver version 2.4.2
[    0.705563] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.705596] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    0.705622] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.705625] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.705676] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.705706] ehci_hcd 0000:00:04.1: debug port 1
[    0.705714] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.705738] ehci_hcd 0000:00:04.1: irq 23, io mem 0xfae7ec00
[    0.716014] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.716178] hub 1-0:1.0: USB hub found
[    0.716183] hub 1-0:1.0: 11 ports detected
[    0.716271] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    0.716286] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.716289] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.716340] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.716359] ehci_hcd 0000:00:06.1: debug port 1
[    0.716367] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.716383] ehci_hcd 0000:00:06.1: irq 21, io mem 0xfae7e800
[    0.728018] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.728147] hub 2-0:1.0: USB hub found
[    0.728153] hub 2-0:1.0: 1 port detected
[    0.728222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.728241] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.728257] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.728260] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.728317] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.728343] ohci_hcd 0000:00:04.0: irq 20, io mem 0xfae7f000
[    0.786129] hub 3-0:1.0: USB hub found
[    0.786135] hub 3-0:1.0: 11 ports detected
[    0.786211] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    0.786225] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.786227] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.786283] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.786307] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
[    0.842133] hub 4-0:1.0: USB hub found
[    0.842139] hub 4-0:1.0: 1 port detected
[    0.842200] uhci_hcd: USB Universal Host Controller Interface driver
[    0.842265] usbcore: registered new interface driver libusual
[    0.842312] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.846275] i8042: Detected active multiplexing controller, rev 1.1
[    0.848320] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.848327] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.848362] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.848388] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.848414] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.848559] mousedev: PS/2 mouse device common for all mice
[    0.848807] rtc_cmos 00:08: RTC can wake from S4
[    0.849018] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.849069] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.849155] device-mapper: uevent: version 1.0.3
[    0.849236] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.849302] cpuidle: using governor ladder
[    0.849390] cpuidle: using governor menu
[    0.849392] EFI Variables Facility v0.08 2004-May-17
[    0.849639] TCP cubic registered
[    0.849745] NET: Registered protocol family 10
[    0.850238] NET: Registered protocol family 17
[    0.850244] Registering the dns_resolver key type
[    0.850436] PM: Hibernation image not present or could not be loaded.
[    0.850452] registered taskstats version 1
[    0.872878]   Magic number: 8:567:341
[    0.873064] rtc_cmos 00:08: setting system clock to 2012-08-05 18:20:06 UTC (1344190806)
[    0.873904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.873907] EDD information not available.
[    0.887847] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.024043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.024069] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.027489] ata2.00: ATAPI: HL-DT-STDVDRAM GT32N, AS01, max UDMA/100
[    1.030733] ata2.00: configured for UDMA/100
[    1.073714] ata1.00: ATA-8: WDC WD6400BEVT-80A0RT0, 01.01A01, max UDMA/133
[    1.073720] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.076190] ata1.00: configured for UDMA/133
[    1.076433] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BEVT-8 01.0 PQ: 0 ANSI: 5
[    1.076598] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.076622] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.076647] sd 0:0:0:0: [sda] Write Protect is off
[    1.076651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.076672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.078657] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT32N     AS01 PQ: 0 ANSI: 5
[    1.082784] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.082790] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.082973] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.083056] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.084083] usb 1-7: new high-speed USB device number 3 using ehci_hcd
[    1.172976]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    1.173767] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.175376] Freeing unused kernel memory: 920k freed
[    1.175735] Write protecting the kernel read-only data: 12288k
[    1.181232] Freeing unused kernel memory: 1616k freed
[    1.186089] Freeing unused kernel memory: 1200k freed
[    1.209203] udevd[104]: starting version 175
[    1.352226] acpi device:0c: registered as cooling_device2
[    1.352320] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/LNXVIDEO:00/input/input5
[    1.352600] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.360847] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.360872] r8169 0000:03:00.0: enabling device (0001 -> 0003)
[    1.361081] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[    1.361099] r8169 0000:03:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    1.361141] r8169 0000:03:00.0: setting latency timer to 64
[    1.361188] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[    1.361648] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc90000654000, 20:cf:30:4a:d2:6a, XID 083000c0 IRQ 41
[    1.361652] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.544066] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.772370] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input6
[    1.772558] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:04.0-1/input0
[    1.772580] usbcore: registered new interface driver usbhid
[    1.772582] usbhid: USB HID core driver
[    3.022975] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    3.022978] vesafb: scrolling: redraw
[    3.022980] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.022990] mtrr: type mismatch for f7000000,200000 old: write-back new: write-combining
[    3.022993] mtrr: type mismatch for f7000000,100000 old: write-back new: write-combining
[    3.022996] mtrr: type mismatch for f7000000,80000 old: write-back new: write-combining
[    3.022999] mtrr: type mismatch for f7000000,40000 old: write-back new: write-combining
[    3.023002] mtrr: type mismatch for f7000000,20000 old: write-back new: write-combining
[    3.023005] mtrr: type mismatch for f7000000,10000 old: write-back new: write-combining
[    3.023008] mtrr: type mismatch for f7000000,8000 old: write-back new: write-combining
[    3.023012] mtrr: type mismatch for f7000000,4000 old: write-back new: write-combining
[    3.023014] mtrr: type mismatch for f7000000,2000 old: write-back new: write-combining
[    3.023017] mtrr: type mismatch for f7000000,1000 old: write-back new: write-combining
[    3.023323] vesafb: framebuffer at 0xf7000000, mapped to 0xffffc90003100000, using 1216k, total 1216k
[    3.023459] Console: switching to colour frame buffer device 80x30
[    3.023473] fb0: VESA VGA frame buffer device
[    3.464689] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.464694] EXT4-fs (sda6): write access will be enabled during recovery
[   11.861758] EXT4-fs (sda6): recovery complete
[   11.862266] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   34.655551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.677773] udevd[413]: starting version 175
[   34.758454] Adding 4206588k swap on /dev/sda7.  Priority:-1 extents:1 across:4206588k 
[   34.765004] lp: driver loaded but no devices found
[   34.816146] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   34.816152] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [io 0x4e00-0x4e3f]
[   34.816155] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   34.849359] asus_laptop: Asus Laptop Support version 0.42
[   34.849515] asus_laptop: BSTS called, 0xf353 returned
[   34.849527] asus_laptop:   K50IE model detected
[   34.860096] asus_laptop: Backlight controlled by ACPI video driver
[   34.860312] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input7
[   34.865930] Registered led device: asus::mail
[   34.867577] Registered led device: asus::touchpad
[   34.946439] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   35.018008] nvidia: module license 'NVIDIA' taints kernel.
[   35.018014] Disabling lock debugging due to kernel taint
[   35.091372] wmi: Mapper loaded
[   35.218767] cfg80211: Calling CRDA to update world regulatory domain
[   35.270201] Linux video capture interface: v2.00
[   35.270963] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
[   35.279099] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:04.1/usb1/1-7/1-7:1.0/input/input8
[   35.279245] usbcore: registered new interface driver uvcvideo
[   35.279248] USB Video Class driver (1.1.1)
[   35.301694] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[   35.301700] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[   35.301876] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   35.301882] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   35.301885] hda_intel: Disabling MSI
[   35.301917] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[   35.410963] Bluetooth: Core ver 2.16
[   35.411407] NET: Registered protocol family 31
[   35.411412] Bluetooth: HCI device and connection manager initialized
[   35.411415] Bluetooth: HCI socket layer initialized
[   35.411418] Bluetooth: L2CAP socket layer initialized
[   35.411427] Bluetooth: SCO socket layer initialized
[   35.422194] ppdev: user-space parallel port driver
[   35.432861] type=1400 audit(1344183641.058:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=779 comm="apparmor_parser"
[   35.433333] type=1400 audit(1344183641.058:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=779 comm="apparmor_parser"
[   35.433577] type=1400 audit(1344183641.058:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=779 comm="apparmor_parser"
[   35.434173] Bluetooth: RFCOMM TTY layer initialized
[   35.434180] Bluetooth: RFCOMM socket layer initialized
[   35.434182] Bluetooth: RFCOMM ver 1.11
[   35.449429] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.449432] Bluetooth: BNEP filters: protocol multicast
[   35.459860] type=1400 audit(1344183641.082:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
[   35.460536] type=1400 audit(1344183641.086:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
[   35.571404] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040101)
[   35.603002] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 18
[   35.603023] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   35.603034] ath9k 0000:04:00.0: setting latency timer to 64
[   35.674752] ath: EEPROM regdomain: 0x60
[   35.674755] ath: EEPROM indicates we should expect a direct regpair map
[   35.674759] ath: Country alpha2 being used: 00
[   35.674761] ath: Regpair used: 0x60
[   35.674765] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   35.674767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674770] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   35.674772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674775] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   35.674777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674779] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   35.674782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674784] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   35.674787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674789] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   35.674792] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674794] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   35.674796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674799] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   35.674801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674803] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   35.674806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674808] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   35.674811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674813] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   35.674816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674818] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   35.674821] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674823] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   35.674826] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.674828] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   35.674831] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   35.722017] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   35.735959] psmouse serio4: elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   35.783705] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   35.784402] Registered led device: ath9k-phy0
[   35.784415] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900030e0000, irq=18
[   35.876649] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input9
[   35.946598] init: failsafe main process (870) killed by TERM signal
[   36.067868] type=1400 audit(1344183641.690:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1000 comm="apparmor_parser"
[   36.073212] type=1400 audit(1344183641.698:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1001 comm="apparmor_parser"
[   36.077664] type=1400 audit(1344183641.702:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1002 comm="apparmor_parser"
[   36.088596] type=1400 audit(1344183641.714:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1002 comm="apparmor_parser"
[   36.088839] type=1400 audit(1344183641.714:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1002 comm="apparmor_parser"
[   36.135032] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   36.135037] cfg80211: World regulatory domain updated:
[   36.135039] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.135042] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.135044] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.135047] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.135049] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.135052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.262650] r8169 0000:03:00.0: eth0: link down
[   36.262660] r8169 0000:03:00.0: eth0: link down
[   36.264623] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.265043] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.269203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.342442] init: alsa-restore main process (1108) terminated with status 19
[   36.395608] init: gdm main process (1147) killed by TERM signal
[   36.616617] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[   36.616832] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[   36.617461] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 17
[   36.617481] snd_hda_intel 0000:02:00.1: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
[   36.617484] hda_intel: Disabling MSI
[   36.617556] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[   36.617768] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
[   36.617772] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 22 (level, low) -> IRQ 22
[   37.271076] vboxdrv: Found 2 processor cores.
[   37.271377] vboxdrv: fAsync=0 offMin=0x24b offMax=0x1dc8
[   37.271463] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   37.271465] vboxdrv: Successfully loaded version 4.1.18 (interface 0x00190000).
[   37.343028] init: lightdm main process (1171) terminated with status 1
[   37.448093] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   37.472067] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   37.484904] vboxpci: IOMMU not found (not registered)
[   37.496086] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   37.520053] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   37.520206] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input12
[   37.520398] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input13
[   37.520541] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input14
[   37.520681] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0c.0/0000:02:00.1/sound/card1/input15
[   37.521488] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
[   37.521506] nvidia 0000:02:00.0: setting latency timer to 64
[   37.521513] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   37.521901] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   37.855584] r8169 0000:03:00.0: eth0: link up
[   37.856227] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.433588] init: plymouth-stop pre-start process (1703) terminated with status 1
[   48.584080] eth0: no IPv6 routers present
[   52.800153] init: failsafe-x main process (1228) terminated with status 1
[   61.772101] usb 3-1: USB disconnect, device number 2
[   63.372072] usb 3-1: new low-speed USB device number 3 using ohci_hcd
[   63.598379] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input16
[   63.598575] generic-usb 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:04.0-1/input0

---

