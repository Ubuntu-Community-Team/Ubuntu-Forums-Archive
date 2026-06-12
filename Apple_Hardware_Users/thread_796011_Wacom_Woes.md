---
title: "Wacom Woes"
date: 2008-05-16
forum: Apple Hardware Users
---

### Post by bunted on 2008-05-16
I am having a problem getting my Wacom Bamboo to work running Hardy on my Mac Pro (Intel).

I am fairly sure that my problem is the same as this:
[*Launchpad Bug*]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/212737")

There was also a discussion, especially pages three and four, in the development forum before it was closed:
[*Ubuntu Forums Hardy Development Archive*]("http://ubuntuforums.org/showthread.php?p=4617819")

It seems this just effects apple users.  I have made sure that I have the correct wacom packages and my xorg.conf reflects the device properly.  I had manually compiled the new wacom driver for Fiesty with no problems; the tablet worked fine.

I really need some help with this, and I thank you all in advance.  Any ideas?

](*,)

---

### Post by Paindistributor on 2008-05-17
Can you tell more about your problem?

I have a 20" Alu-iMac and the Wacom Bamboo model MTE-450. I've got 
anything working here under Hardy. Pasting your output from dmesg 
here might help. :)

---

### Post by bunted on 2008-05-17
Here is my dmesg.

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=e4f8f871-f9be-467b-b44a-c6819b03d70a ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007faa8000 (usable)
[    0.000000]  BIOS-e820: 000000007faa8000 - 000000007fb7b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fb7b000 - 000000007fc00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 522920) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1572864) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1572864
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 APPLE )
[    0.000000] ACPI: XSDT 7FBBA1C0, 00EC (r1 APPLE   Apple00       5D       1000013)
[    0.000000] ACPI: ECDT 7FBB9000, 0053 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: FACP 7FBB7000, 00F4 (r4 APPLE   Apple00       5D Loki       5F)
[    0.000000] ACPI: DSDT 7FBAE000, 47C6 (r1 APPLE   Apple00    10001 Loki       5F)
[    0.000000] ACPI: FACS 7FAC4000, 0040
[    0.000000] ACPI: HPET 7FBB6000, 0038 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: APIC 7FBB4000, 00BC (r2 APPLE   Apple00        0 Loki       5F)
[    0.000000] ACPI: MCFG 7FBB3000, 003C (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: SSDT 7FBAD000, 008E (r1  PmRef  Cpu0Cst     3001 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBAC000, 0030 (r1  PmRef  Cpu0Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBAB000, 0047 (r1  PmRef  Cpu1Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBAA000, 0030 (r1  PmRef  Cpu1Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA9000, 0047 (r1  PmRef  Cpu2Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA8000, 0030 (r1  PmRef  Cpu2Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA7000, 0047 (r1  PmRef  Cpu3Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA6000, 0030 (r1  PmRef  Cpu3Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA5000, 0047 (r1  PmRef  Cpu4Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA4000, 0030 (r1  PmRef  Cpu4Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA3000, 0047 (r1  PmRef  Cpu5Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA2000, 0030 (r1  PmRef  Cpu5Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA1000, 0047 (r1  PmRef  Cpu6Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FBA0000, 0030 (r1  PmRef  Cpu6Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB9F000, 0047 (r1  PmRef  Cpu7Cst     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB9E000, 0030 (r1  PmRef  Cpu7Ist     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB9D000, 0CEC (r1  PmRef    CpuPm     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB97000, 057B (r1 PCIRef Pci16118     1000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB9C000, 0892 (r1 SataRe  SataPri     1000 INTL 20050309)
[    0.000000] ACPI: SSDT 7FB9B000, 05F4 (r1 SataRe  SataSec     1000 INTL 20050309)
[    0.000000] ACPI: DMI detected: Apple
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000180000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 522920) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1572864) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000180000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1572864
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   522920
[    0.000000]     0:  1048576 ->  1572864
[    0.000000] On node 0 totalpages: 1047111
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1210 pages reserved
[    0.000000]   DMA zone: 2733 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 504544 pages, LIFO batch:31
[    0.000000]   Normal zone: 7168 pages used for memmap
[    0.000000]   Normal zone: 517120 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x07] enabled)
[    0.000000] Processor #7
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] Processor #6
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000007faa8000 - 000000007fb7b000
[    0.000000] swsusp: Registered nosave memory region: 000000007fb7b000 - 000000007fc00000
[    0.000000] swsusp: Registered nosave memory region: 000000007fc00000 - 00000000ffe00000
[    0.000000] swsusp: Registered nosave memory region: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7fc00000:80200000)
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1024397
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=e4f8f871-f9be-467b-b44a-c6819b03d70a ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   47.732217] time.c: Detected 2659.999 MHz processor.
[   47.732918] Console: colour VGA+ 80x25
[   47.732921] console [tty0] enabled
[   47.732938] Checking aperture...
[   47.732945] Calgary: detecting Calgary via BIOS EBDA area
[   47.732948] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   47.732950] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   47.763521] Placing software IO TLB between 0x1077000 - 0x5077000
[   47.793842] Memory: 4022916k/6291456k available (2466k kernel code, 165528k reserved, 1309k data, 316k init)
[   47.793870] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=1
[   47.869860] Calibrating delay using timer specific routine.. 5323.67 BogoMIPS (lpj=10647352)
[   47.869887] Security Framework initialized
[   47.869894] SELinux:  Disabled at boot.
[   47.869905] AppArmor: AppArmor initialized
[   47.869907] Failure registering capabilities with primary security module.
[   47.870203] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   47.872235] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   47.873192] Mount-cache hash table entries: 256
[   47.873315] CPU: L1 I cache: 32K, L1 D cache: 32K
[   47.873318] CPU: L2 cache: 4096K
[   47.873320] CPU 0/0 -> Node 0
[   47.873321] using mwait in idle threads.
[   47.873322] CPU: Physical Processor ID: 0
[   47.873323] CPU: Processor Core ID: 0
[   47.873328] CPU0: Thermal monitoring enabled (TM2)
[   47.873339] SMP alternatives: switching to UP code
[   47.874020] Early unpacking initramfs... done
[   48.154811] ACPI: Core revision 20070126
[   48.154846] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   48.197913] Using local APIC timer interrupts.
[   48.235416] APIC timer calibration result 20781233
[   48.235417] Detected 20.781 MHz APIC timer.
[   48.235489] SMP alternatives: switching to SMP code
[   48.236067] Booting processor 1/4 APIC 0x1
[   48.246394] Initializing CPU#1
[   48.323200] Calibrating delay using timer specific routine.. 5320.00 BogoMIPS (lpj=10640008)
[   48.323206] CPU: L1 I cache: 32K, L1 D cache: 32K
[   48.323207] CPU: L2 cache: 4096K
[   48.323209] CPU 1/1 -> Node 0
[   48.323210] CPU: Physical Processor ID: 0
[   48.323211] CPU: Processor Core ID: 1
[   48.323216] CPU1: Thermal monitoring enabled (TM2)
[   48.323621] Intel(R) Xeon(R) CPU            5150  @ 2.66GHz stepping 0b
[   48.323656] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   48.343688] SMP alternatives: switching to SMP code
[   48.344289] Booting processor 2/4 APIC 0x7
[   48.354586] Initializing CPU#2
[   48.434919] Calibrating delay using timer specific routine.. 5320.06 BogoMIPS (lpj=10640124)
[   48.434925] CPU: L1 I cache: 32K, L1 D cache: 32K
[   48.434926] CPU: L2 cache: 4096K
[   48.434928] CPU 2/7 -> Node 0
[   48.434929] CPU: Physical Processor ID: 3
[   48.434930] CPU: Processor Core ID: 1
[   48.434935] CPU2: Thermal monitoring enabled (TM2)
[   48.435341] Intel(R) Xeon(R) CPU            5150  @ 2.66GHz stepping 0b
[   48.435373] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   48.455377] SMP alternatives: switching to SMP code
[   48.455719] Booting processor 3/4 APIC 0x6
[   48.466017] Initializing CPU#3
[   48.542648] Calibrating delay using timer specific routine.. 5320.07 BogoMIPS (lpj=10640154)
[   48.542654] CPU: L1 I cache: 32K, L1 D cache: 32K
[   48.542655] CPU: L2 cache: 4096K
[   48.542657] CPU 3/6 -> Node 0
[   48.542658] CPU: Physical Processor ID: 3
[   48.542659] CPU: Processor Core ID: 0
[   48.542663] CPU3: Thermal monitoring enabled (TM2)
[   48.543069] Intel(R) Xeon(R) CPU            5150  @ 2.66GHz stepping 0b
[   48.543108] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   48.563072] Brought up 4 CPUs
[   48.563151] CPU0 attaching sched-domain:
[   48.563153]  domain 0: span 03
[   48.563154]   groups: 01 02
[   48.563155]   domain 1: span 0f
[   48.563156]    groups: 03 0c
[   48.563158]    domain 2: span 0f
[   48.563159]     groups: 0f
[   48.563160] CPU1 attaching sched-domain:
[   48.563161]  domain 0: span 03
[   48.563162]   groups: 02 01
[   48.563164]   domain 1: span 0f
[   48.563164]    groups: 03 0c
[   48.563166]    domain 2: span 0f
[   48.563167]     groups: 0f
[   48.563168] CPU2 attaching sched-domain:
[   48.563169]  domain 0: span 0c
[   48.563170]   groups: 04 08
[   48.563172]   domain 1: span 0f
[   48.563172]    groups: 0c 03
[   48.563174]    domain 2: span 0f
[   48.563175]     groups: 0f
[   48.563176] CPU3 attaching sched-domain:
[   48.563177]  domain 0: span 0c
[   48.563178]   groups: 08 04
[   48.563179]   domain 1: span 0f
[   48.563180]    groups: 0c 03
[   48.563182]    domain 2: span 0f
[   48.563183]     groups: 0f
[   48.563431] net_namespace: 120 bytes
[   48.563706] Time: 22:21:40  Date: 05/17/08
[   48.563728] NET: Registered protocol family 16
[   48.563868] ACPI: bus type pci registered
[   48.563924] PCI: Using configuration type 1
[   48.564999] ACPI: EC: EC description table is found, configuring boot EC
[   48.565932] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   48.663108] ACPI: Interpreter enabled
[   48.663110] ACPI: (supports S0 S1 S3 S4 S5)
[   48.663121] ACPI: Using IOAPIC for interrupt routing
[   48.665756] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[   48.665758] ACPI: EC: driver started in poll mode
[   48.666023] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   48.666113] PCI: 0000:00:03.0: class 600 doesn't match header type 01. Ignoring class.
[   48.666176] PCI: 0000:00:05.0: class 600 doesn't match header type 01. Ignoring class.
[   48.666218] PCI: 0000:00:06.0: class 600 doesn't match header type 01. Ignoring class.
[   48.666260] PCI: 0000:00:07.0: class 600 doesn't match header type 01. Ignoring class.
[   48.668102] PCI: Transparent bridge - 0000:00:1e.0
[   48.668142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   48.668464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   48.668544] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1.P1P2._PRT]
[   48.668695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1.P1P2.P2P5._PRT]
[   48.668783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1.P1P2.P2P3._PRT]
[   48.668870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   48.668960] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   48.669051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NRP4._PRT]
[   48.669132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SRP1._PRT]
[   48.669212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SRP3._PRT]
[   48.672648] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 9 10 *11)
[   48.672718] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 9 10 11) *3
[   48.672786] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 9 *10 11)
[   48.672854] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *9 10 11)
[   48.672921] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 7 9 10 11)
[   48.672989] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 9 10 *11)
[   48.673057] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 9 10 11) *0, disabled.
[   48.673127] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 7 9 *10 11)
[   48.673241] Linux Plug and Play Support v0.97 (c) Adam Belay
[   48.673262] pnp: PnP ACPI init
[   48.673267] ACPI: bus type pnp registered
[   48.674377] pnp: PnP ACPI: found 10 devices
[   48.674378] ACPI: ACPI bus type pnp unregistered
[   48.674546] PCI: Using ACPI for IRQ routing
[   48.674548] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   48.682936] NET: Registered protocol family 8
[   48.682937] NET: Registered protocol family 20
[   48.682968] PCI-GART: No AMD northbridge found.
[   48.682972] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   48.682975] hpet0: 3 64-bit timers, 14318180 Hz
[   48.684003] AppArmor: AppArmor Filesystem Enabled
[   48.686845] Time: tsc clocksource has been installed.
[   48.686852] Switched to high resolution mode on CPU 0
[   48.687102] Switched to high resolution mode on CPU 2
[   48.687104] Switched to high resolution mode on CPU 3
[   48.687328] Switched to high resolution mode on CPU 1
[   48.694815] system 00:01: iomem range 0xd0000000-0xdfffffff has been reserved
[   48.694818] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   48.694820] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   48.694822] system 00:01: iomem range 0xfec00000-0xfecfffff has been reserved
[   48.694825] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   48.694827] system 00:01: iomem range 0xfe700000-0xfe7003ff has been reserved
[   48.694829] system 00:01: iomem range 0xfe600000-0xfe6fffff has been reserved
[   48.694831] system 00:01: iomem range 0xfe000000-0xfe01ffff has been reserved
[   48.694840] system 00:08: ioport range 0x320-0x37f has been reserved
[   48.694842] system 00:08: ioport range 0x400-0x47f has been reserved
[   48.694844] system 00:08: ioport range 0x500-0x53f has been reserved
[   48.694846] system 00:08: ioport range 0x872-0x875 has been reserved
[   48.695160] PCI: Bridge: 0000:02:00.0
[   48.695161]   IO window: disabled.
[   48.695164]   MEM window: disabled.
[   48.695167]   PREFETCH window: disabled.
[   48.695170] PCI: Bridge: 0000:02:01.0
[   48.695170]   IO window: disabled.
[   48.695173]   MEM window: disabled.
[   48.695176]   PREFETCH window: disabled.
[   48.695179] PCI: Bridge: 0000:02:02.0
[   48.695180]   IO window: 2000-2fff
[   48.695184]   MEM window: f0000000-f08fffff
[   48.695186]   PREFETCH window: disabled.
[   48.695189] PCI: Bridge: 0000:01:00.0
[   48.695190]   IO window: 2000-2fff
[   48.695193]   MEM window: f0000000-f08fffff
[   48.695196]   PREFETCH window: disabled.
[   48.695199] PCI: Bridge: 0000:01:00.3
[   48.695199]   IO window: disabled.
[   48.695202]   MEM window: disabled.
[   48.695204]   PREFETCH window: disabled.
[   48.695207] PCI: Bridge: 0000:00:02.0
[   48.695208]   IO window: 2000-2fff
[   48.695211]   MEM window: f0000000-f09fffff
[   48.695213]   PREFETCH window: disabled.
[   48.695215] PCI: not setting up bridge 0000:00:03.0 for bus 7
[   48.695216] PCI: Bridge: 0000:00:04.0
[   48.695218]   IO window: 1000-1fff
[   48.695220]   MEM window: f0b00000-f0bfffff
[   48.695222]   PREFETCH window: e0000000-efffffff
[   48.695224] PCI: not setting up bridge 0000:00:05.0 for bus 9
[   48.695225] PCI: not setting up bridge 0000:00:06.0 for bus 10
[   48.695227] PCI: not setting up bridge 0000:00:07.0 for bus 11
[   48.695228] PCI: Bridge: 0000:00:1c.0
[   48.695229]   IO window: disabled.
[   48.695232]   MEM window: disabled.
[   48.695234]   PREFETCH window: disabled.
[   48.695237] PCI: Bridge: 0000:00:1c.1
[   48.695238]   IO window: disabled.
[   48.695241]   MEM window: disabled.
[   48.695243]   PREFETCH window: disabled.
[   48.695246] PCI: Bridge: 0000:00:1c.2
[   48.695247]   IO window: disabled.
[   48.695250]   MEM window: disabled.
[   48.695252]   PREFETCH window: disabled.
[   48.695255] PCI: Bridge: 0000:00:1c.3
[   48.695256]   IO window: disabled.
[   48.695259]   MEM window: disabled.
[   48.695262]   PREFETCH window: disabled.
[   48.695265] PCI: Bridge: 0000:00:1e.0
[   48.695266]   IO window: disabled.
[   48.695269]   MEM window: f0a00000-f0afffff
[   48.695271]   PREFETCH window: disabled.
[   48.695284] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.695288] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.695297] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.695300] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.695311] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.695314] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   48.695325] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   48.695328] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   48.695340] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   48.695343] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   48.695353] PCI: Setting latency timer of device 0000:01:00.3 to 64
[   48.695359] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   48.695365] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.695368] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   48.695374] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   48.695380] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   48.695387] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   48.695399] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   48.695402] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   48.695415] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   48.695418] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   48.695431] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   48.695434] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   48.695447] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   48.695451] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   48.695458] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   48.695470] NET: Registered protocol family 2
[   48.730831] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   48.731743] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   48.735166] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   48.735644] TCP: Hash tables configured (established 524288 bind 65536)
[   48.735646] TCP reno registered
[   48.746863] checking if image is initramfs... it is
[   49.292817] Freeing initrd memory: 8207k freed
[   49.297551] audit: initializing netlink socket (disabled)
[   49.297567] audit(1211062900.492:1): initialized
[   49.300013] VFS: Disk quotas dquot_6.5.1
[   49.300078] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   49.300205] io scheduler noop registered
[   49.300207] io scheduler anticipatory registered
[   49.300208] io scheduler deadline registered
[   49.300312] io scheduler cfq registered (default)
[   49.302203] Boot video device is 0000:08:00.0
[   49.302403] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.302429] assign_interrupt_mode Found MSI capability
[   49.302454] Allocate Port Service[0000:00:02.0:pcie00]
[   49.302530] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   49.302556] assign_interrupt_mode Found MSI capability
[   49.302576] Allocate Port Service[0000:00:04.0:pcie00]
[   49.302655] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   49.302686] assign_interrupt_mode Found MSI capability
[   49.302712] Allocate Port Service[0000:00:1c.0:pcie00]
[   49.302753] Allocate Port Service[0000:00:1c.0:pcie02]
[   49.302838] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   49.302873] assign_interrupt_mode Found MSI capability
[   49.302901] Allocate Port Service[0000:00:1c.1:pcie00]
[   49.302934] Allocate Port Service[0000:00:1c.1:pcie02]
[   49.303009] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   49.303044] assign_interrupt_mode Found MSI capability
[   49.303072] Allocate Port Service[0000:00:1c.2:pcie00]
[   49.303117] Allocate Port Service[0000:00:1c.2:pcie02]
[   49.303195] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   49.303229] assign_interrupt_mode Found MSI capability
[   49.303258] Allocate Port Service[0000:00:1c.3:pcie00]
[   49.303300] Allocate Port Service[0000:00:1c.3:pcie02]
[   49.303381] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   49.303411] Allocate Port Service[0000:01:00.0:pcie10]
[   49.303496] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   49.303524] assign_interrupt_mode Found MSI capability
[   49.303550] Allocate Port Service[0000:02:00.0:pcie20]
[   49.303627] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   49.303659] assign_interrupt_mode Found MSI capability
[   49.303686] Allocate Port Service[0000:02:01.0:pcie20]
[   49.303721] Allocate Port Service[0000:02:01.0:pcie22]
[   49.303803] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   49.303834] assign_interrupt_mode Found MSI capability
[   49.303861] Allocate Port Service[0000:02:02.0:pcie20]
[   49.330493] Real Time Clock Driver v1.12ac
[   49.330700] hpet_resources: 0xfed00000 is busy
[   49.330728] Linux agpgart interface v0.102
[   49.330730] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   49.331882] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   49.331953] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   49.332098] PNP: No PS/2 controller found. Probing ports directly.
[   49.332948] i8042.c: No controller found.
[   49.345962] mice: PS/2 mouse device common for all mice
[   49.346006] cpuidle: using governor ladder
[   49.346008] cpuidle: using governor menu
[   49.346158] NET: Registered protocol family 1
[   49.346212] registered taskstats version 1
[   49.346317]   Magic number: 8:428:401
[   49.346356] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   49.346358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   49.346359] EDD information not available.
[   49.346370] Freeing unused kernel memory: 316k freed
[   50.485116] fuse init (API version 7.9)
[   50.496230] Monitor-Mwait will be used to enter C-1 state
[   50.496988] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   50.496999] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   50.497007] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   50.497013] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   50.653086] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   50.653090] Copyright (c) 1999-2006 Intel Corporation.
[   50.653151] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   50.653161] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   50.678553] e1000: 0000:05:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x4) 00:17:f2:0f:33:ca
[   50.680428] usbcore: registered new interface driver usbfs
[   50.680449] usbcore: registered new interface driver hub
[   50.680905] SCSI subsystem initialized
[   50.684156] usbcore: registered new device driver usb
[   50.685713] USB Universal Host Controller Interface driver v3.0
[   50.685755] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 19 (level, low) -> IRQ 19
[   50.685763] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   50.685766] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   50.685985] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   50.686011] uhci_hcd 0000:00:1d.0: irq 19, io base 0x000030a0
[   50.686114] usb usb1: configuration #1 chosen from 1 choice
[   50.686129] hub 1-0:1.0: USB hub found
[   50.686134] hub 1-0:1.0: 2 ports detected
[   50.688996] libata version 3.00 loaded.
[   50.717596] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   50.717625] ACPI: PCI Interrupt 0000:05:00.1[B] -> GSI 19 (level, low) -> IRQ 19
[   50.717634] PCI: Setting latency timer of device 0000:05:00.1 to 64
[   50.740893] e1000: 0000:05:00.1: e1000_probe: (PCI Express:2.5Gb/s:Width x4) 00:17:f2:0f:33:cb
[   50.779326] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   50.789538] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 20
[   50.789547] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   50.789550] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   50.789572] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   50.789596] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00003080
[   50.789676] usb usb2: configuration #1 chosen from 1 choice
[   50.789690] hub 2-0:1.0: USB hub found
[   50.789695] hub 2-0:1.0: 2 ports detected
[   50.897251] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 21
[   50.897261] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   50.897264] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   50.897284] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   50.897308] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00003060
[   50.897389] usb usb3: configuration #1 chosen from 1 choice
[   50.897402] hub 3-0:1.0: USB hub found
[   50.897407] hub 3-0:1.0: 2 ports detected
[   51.004945] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 22
[   51.004952] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   51.004954] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   51.004978] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   51.005000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00003040
[   51.005083] usb usb4: configuration #1 chosen from 1 choice
[   51.005097] hub 4-0:1.0: USB hub found
[   51.005103] hub 4-0:1.0: 2 ports detected
[   51.104762] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   51.104797] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   51.104809] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   51.104838] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 21
[   51.104856] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   51.104862] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   51.105059] ACPI: PCI Interrupt 0000:10:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   51.105369] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 19 (level, low) -> IRQ 19
[   51.106337] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   51.106343] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   51.106392] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   51.110304] ehci_hcd 0000:00:1d.7: debug port 1
[   51.110308] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   51.110314] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0c04800
[   51.156077] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0a04000-f0a047ff]  Max Packet=[4096]  IR/IT contexts=[4/8]
[   51.169223] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   51.169309] usb usb5: configuration #1 chosen from 1 choice
[   51.169326] hub 5-0:1.0: USB hub found
[   51.169332] hub 5-0:1.0: 8 ports detected
[   51.272307] ata_piix 0000:00:1f.1: version 2.12
[   51.272328] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   51.272363] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   51.272475] scsi0 : ata_piix
[   51.272514] scsi1 : ata_piix
[   51.273027] ata1: PATA max UDMA/100 cmd 0x30e8 ctl 0x30fc bmdma 0x30c0 irq 20
[   51.273029] ata2: PATA max UDMA/100 cmd 0x30e0 ctl 0x30f8 bmdma 0x30c8 irq 20
[   51.523569] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   51.591766] ata1.00: ATAPI: OPTIARC DVD RW AD-7170A, 1.N8, max UDMA/66
[   51.655703] usb 5-5: configuration #1 chosen from 1 choice
[   51.655770] hub 5-5:1.0: USB hub found
[   51.655874] hub 5-5:1.0: 3 ports detected
[   51.763224] ata1.00: configured for UDMA/66
[   51.930212] scsi 0:0:0:0: CD-ROM            OPTIARC  DVD RW AD-7170A  1.N8 PQ: 0 ANSI: 5
[   51.930278] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   51.930296] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 21
[   51.930327] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   51.930361] scsi2 : ata_piix
[   51.930396] scsi3 : ata_piix
[   51.930927] ata3: SATA max UDMA/133 cmd 0x30d8 ctl 0x30f4 bmdma 0x3020 irq 21
[   51.930929] ata4: SATA max UDMA/133 cmd 0x30d0 ctl 0x30f0 bmdma 0x3028 irq 21
[   51.958488] usb 5-5.1: new full speed USB device using ehci_hcd and address 3
[   52.053443] usb 5-5.1: configuration #1 chosen from 1 choice
[   52.053660] hub 5-5.1:1.0: USB hub found
[   52.054125] hub 5-5.1:1.0: 3 ports detected
[   52.116904] ata3.00: ATA-7: WDC WD2500AAJS-41RYA0, 12.01B02, max UDMA/133
[   52.116908] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   52.131573] ata3.00: configured for UDMA/133
[   52.341523] ata4.00: ATA-7: ST3750640AS P, 3.BTH, max UDMA/133
[   52.341526] ata4.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   52.357496] usb 5-5.2: new full speed USB device using ehci_hcd and address 4
[   52.416288] ata4.00: configured for UDMA/133
[   52.416377] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-4 12.0 PQ: 0 ANSI: 5
[   52.416480] scsi 3:0:0:0: Direct-Access     ATA      ST3750640AS P    3.BT PQ: 0 ANSI: 5
[   52.421828] Driver 'sr' needs updating - please use bus_type methods
[   52.425483] Driver 'sd' needs updating - please use bus_type methods
[   52.425509] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
[   52.425513] Uniform CD-ROM driver Revision: 3.20
[   52.425550] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   52.425634] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   52.425646] sd 2:0:0:0: [sda] Write Protect is off
[   52.425647] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.425661] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.425716] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   52.425724] sd 2:0:0:0: [sda] Write Protect is off
[   52.425726] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.425741] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.425744]  sda:<7>ieee1394: Host added: ID:BUS[0-02:1023]  GUID[001d4ffffe7a3b48]
[   52.428948] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   52.428961] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   52.428974] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   52.462312]  sda1 sda2 sda3 sda4
[   52.462406] sd 2:0:0:0: [sda] Attached SCSI disk
[   52.462451] sd 3:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[   52.462458] sd 3:0:0:0: [sdb] Write Protect is off
[   52.462460] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   52.462471] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.462500] sd 3:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[   52.462506] sd 3:0:0:0: [sdb] Write Protect is off
[   52.462507] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   52.462525] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.462528]  sdb: sdb1 sdb2 sdb3
[   52.509144] sd 3:0:0:0: [sdb] Attached SCSI disk
[   52.763592] kjournald starting.  Commit interval 5 seconds
[   52.763611] EXT3-fs: mounted filesystem with ordered data mode.
[   57.302424] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   57.436811] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.456872] input: Power Button (FF) as /devices/virtual/input/input1
[   57.560286] ACPI: Power Button (FF) [PWRF]
[   57.560388] input: Power Button (CM) as /devices/virtual/input/input2
[   57.580534] ACPI: Power Button (CM) [PWRB]
[   57.625056] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   57.729117] EDAC MC: Ver: 2.1.0 Apr 10 2008
[   57.800165] iTCO_vendor_support: vendor-support=0
[   57.937557] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   57.937622] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   57.937643] iTCO_wdt: No card detected
[   57.945197] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   57.955674] [fglrx] Maximum main memory to use for locked dma buffers: 3774 MBytes.
[   57.955699] [fglrx] ASYNCIO init succeed!
[   57.957301] [fglrx] PAT is enabled successfully!
[   57.957403] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   58.001599] EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
[   58.001618] EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[   58.047980] ACPI: SBS HC: EC = 0xffff8101784b4c80, offset = 0x20, query_bit = 0x10
[   58.142088] intel_rng: FWH not detected
[   58.320046] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 23 (level, low) -> IRQ 23
[   58.320891] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   59.032105] lp: driver loaded but no devices found
[   59.629934] EXT3 FS on sda3, internal journal
[   62.425849] usb 5-5.2: configuration #1 chosen from 1 choice
[   62.495071] ip_tables: (C) 2000-2006 Netfilter Core Team
[   62.631366] usb 5-5.1.1: new low speed USB device using ehci_hcd and address 5
[   62.740675] usb 5-5.1.1: configuration #1 chosen from 1 choice
[   62.797130] No dock devices found.
[   62.939102] usb 5-5.1.2: new full speed USB device using ehci_hcd and address 6
[   63.034936] usb 5-5.1.2: configuration #1 chosen from 1 choice
[   63.241967] usb 5-5.1.3: new full speed USB device using ehci_hcd and address 7
[   63.340164] usb 5-5.1.3: configuration #1 chosen from 1 choice
[   63.341013] input: Wacom Bamboo as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5.1/5-5.1.2/5-5.1.2:1.0/input/input4
[   63.414055] usbcore: registered new interface driver wacom
[   63.414060] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
[   63.414246] usbcore: registered new interface driver hiddev
[   63.419179] hiddev96hidraw0: USB HID v1.11 Device [Apple Computer, Inc. Apple Cinema HD Display] on usb-0000:00:1d.7-5.2
[   63.422633] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5.1/5-5.1.1/5-5.1.1:1.0/input/input5
[   63.465271] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-5.1.1
[   63.468381] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5.1/5-5.1.3/5-5.1.3:1.0/input/input6
[   63.533097] input,hidraw2: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-5.1.3
[   63.537017] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5.1/5-5.1.3/5-5.1.3:1.1/input/input7
[   63.596657] input,hidraw3: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-5.1.3
[   63.596677] usbcore: registered new interface driver usbhid
[   63.596680] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   63.781903] ppdev: user-space parallel port driver
[   63.892705] audit(1211088115.928:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5489 profile="/usr/sbin/cupsd" namespace="default"
[   64.890377] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   64.890382] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   64.924404] Bluetooth: Core ver 2.11
[   64.924485] NET: Registered protocol family 31
[   64.924487] Bluetooth: HCI device and connection manager initialized
[   64.924493] Bluetooth: HCI socket layer initialized
[   64.936714] Bluetooth: L2CAP ver 2.9
[   64.936718] Bluetooth: L2CAP socket layer initialized
[   64.981524] Bluetooth: RFCOMM socket layer initialized
[   64.981787] Bluetooth: RFCOMM TTY layer initialized
[   64.981789] Bluetooth: RFCOMM ver 1.8
[   65.309265] input: Mouseemu virtual keyboard as /devices/virtual/input/input8
[   65.345021] input: Mouseemu virtual mouse as /devices/virtual/input/input9
[   66.818696] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   69.013290] NET: Registered protocol family 17
[   69.925066] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   69.925071] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   69.925073] [fglrx] Reserve Block - 2 offset =  0X1ffff000 length = 0X1000
[   69.925074] [fglrx] Reserve Block - 3 offset =  0Xffc0000 length = 0X40000
[   69.980653] [fglrx] interrupt source 20008000 successfully enabled
[   69.980658] [fglrx] enable ID = 0x00000008
[   69.980664] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   69.980703] [fglrx] interrupt source 10000000 successfully enabled
[   69.980704] [fglrx] enable ID = 0x00000009
[   69.980706] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   71.218271] NET: Registered protocol family 10
[   71.218509] lo: Disabled Privacy Extensions
[   71.219417] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   81.674294] eth0: no IPv6 routers present
```

Thanks for trying to help.

---

### Post by Paindistributor on 2008-05-18
Your dmesg looks fine - you've got not the problem described in the launchpad.

You have to check following:

1. Be sure you have the xorg-wacom driver installed. You can look in synaptic or simply use aptitude.

```
you@localhost:~$ aptitude search wacom
p   wacom-tools                     - utilities for Wacom tablet devices        
i   xserver-xorg-input-wacom        - X.Org X server -- Wacom input driver 
```

You see that "i" at the beginning of the line? Then you are fine. Overwise you have to install the driver.

2. Check your xorg configuration. I had to add some few lines by hand to get my wacoms work. 

But before doing any changes you should backup your xorg.conf file.

```
you@localhost:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

After that just open a terminal and type in

```
you@localhost:~$ sudo gedit /etc/X11/xorg.conf
```

That will open the configuration in the editor. You can copy the necessary lines from my config.

First you have to add the three "SendCoreEvents" Lines (stylus, cursor and eraser) to the section "ServerLayout".
Then add the three "InputDevice" Section-blocks right under your "ServerLayout" section.
Here are the lines:

```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

```

After this, just logout and your wacom should work. If not, just reboot one time and all should be fine :mrgreen:

---

### Post by bunted on 2008-05-18
I really appreciate the help, but I have already tried what you suggested.  Both the wacom driver and tools are installed.  I may only have a few posts in this forum, but I have been using linux for some time.  For argument's sake, I tried losing the pad device and set up xorg.conf like you suggested, even with the Force Device parameters (for a tablet PC?).  I have even tried using /dev/input/tablet-bamboo instead of wacom as well.

This is my xorg log searched for wacom without the pad device.

```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.9-8 $
(**) WACOM: suppress value is 2
(**) WACOM: suppress value is 2
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
eraser Wacom X driver can't grab event device, errno=1022
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=14760 bottom Y=9225

```

I really think this launchpad bug is what my problem is, as all of my logs and error reflect the same.  Thanks again.

Still ](*,)

---

### Post by Paindistributor on 2008-05-19
I've done some research on the linux-wacom website. What i've figured out
is, the "pad" device is important to get all the buttons on the wacom 
device work. On my Graphire4 i've got my scroll-wheel work and all the 
other buttons. That section was missing, but both Graphire and Bamboo 
worked flawless on the iMac and on my Notebook.

bunted, can you please try the follwing:

Add the "touch" and "pad" lines to your "ServerLayout" section. Then
add the other two blocks to your configuration. The device must
be "/dev/input/wacom" - it's automatically mapped to the proper device.

```


Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	InputDevice     "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
        InputDevice     "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets

EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# This section is for the TabletPC that supports touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "touch"
  Option        "USB"           "on"                  # USB ONLY
EndSection


```

Reboot and check the results.

I played around the wacdump tool - i dont get any informations from that.
In Feisty it worked. Probably the drivers got some problems with Hardy...

---

### Post by bunted on 2008-05-19
Tried the new xorg.conf suggestion to no avail.

Here's my xorg log

```
someone@foobar:~$ grep -i wacom /var/log/Xorg.0.log
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.9-8 $
(**) WACOM: suppress value is 2
(**) WACOM: suppress value is 2
(**) WACOM: suppress value is 2
(**) pad device is /dev/input/wacom
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
pad Wacom X driver can't grab event device, errno=1022
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled
(==) Wacom device "pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225
eraser Wacom X driver can't grab event device, errno=1022
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=14760 bottom Y=9225

```

I think I am settling on some sort of driver problem for my hardware, similar to the launchpad bug.  Thanks for the help though.

---

### Post by bunted on 2008-05-19
I also tried the how-to here:

[Wacom on 8.04]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom+hardy")

This still doesn't work and wacdump picks up nothing for me as well.

Man this is frustrating.  It seems that only a few people in the whole world have a problem with this, so I doubt I'll see it fixed soon.  I guess there's not a lot of people running linux on a Mac Pro . . . 

](*,)

---

### Post by Paindistributor on 2008-05-20
Hm... this looks really bad. It may be a bug in the wacom kernel-module or 
the usb-module. The concerning sourcecode line regards to the detection of 
the wacom usb-device. This fails and returns the errorcode.

The last thing i would try is to get the latest sourcecode of the wacom-
driver and compile it by hand. At least we do not know exactly where the 
problem is. Perhaps the kernel needs to be rebuild. So it can be difficult 
to get this work properly.

This is nothing i would recommend a user without experience in this stuff.

The current driver has to be debugged on a MacBook Pro. I'm afraid there's 
no other way for you than waiting for a patch. If you really need your 
wacom now i recommend to downgrade to feisty. :sad:

---

### Post by bunted on 2008-05-21
Yeah, that how-to is about compiling the wacom driver from source.  I guess I'll just have to wait to run feisty.  Thanks again for trying to help.

---

### Post by wasme on 2008-08-04
I ran across this posting while trying to solve my own problem with a wacom tablet (albit not on a Mac) ... after much frustration and hair pulling I found the source of my problem, and maybe it'll help you too:

My tablet worked fine on my laptop but not my desktop and so I did a process-by-process comparison of what was running on each, experimentally killing those on the desktop but not on the laptop until I found the offender: A program called 'mouseemu' that adds some features to multi-touch touchpads. I don't even know how it ended up installed on my desktop (as it doesn't have a touchpad of any sort). After uninstalling mouseemu (and restarting X) everything worked perfectly.

---

### Post by cyberdork33 on 2008-08-04
> **wasme said:**
> A program called 'mouseemu' that adds some features to multi-touch touchpads. I don't even know how it ended up installed on my desktop (as it doesn't have a touchpad of any sort). After uninstalling mouseemu (and restarting X) everything worked perfectly.
Good to know. It is installed by default in Ubuntu for some reason. I think that it is only useful for PowerPC Macs.

---

