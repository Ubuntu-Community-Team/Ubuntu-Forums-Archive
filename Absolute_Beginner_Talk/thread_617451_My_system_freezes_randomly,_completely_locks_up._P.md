---
title: "My system freezes randomly, completely locks up. Please help? :("
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by OzyOly on 2007-11-19
Hey there I'm having a really bad problem with my gutsy install. It also happened with an attempt to use feisty not so long ago. 

Basically my system, randomly locks up. And I mean, locks up so I have to press the rest button on my computer.

This happens with ubuntu and other flavours (that I used to test if the freezing is just limited to ubuntu). It freezes on gusty and feisty and both the 64bit and 32bit versions.

My specs are as follows;

Conroe E6700 
2048MB Corsair XMS2PRO6400  
74GB WD Raptor 
250GB Hitachi 
500GB WD
Saphire Blizzard X1900XTX
Creative Audigy 4 7.1 Sound Card  
Terratec Dual DVB-T Tuner 
DFI infinity 975x/g mother board

I have a 50GB ext partition (that I use for root)  on the hitachi and a 2GB swap partition on the same drive. 

The result of lspci command is;

```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
03:00.0 Multimedia video controller: Micronas Semiconductor Holding AG Unknown device 0720
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```

I'm not sure if this is a driver problem or not. I've run memtest for hours and it results in zero errors but when my system freezes it had one module of memory stuck at full acitvity and the other at half if that is important?

I set up my swap and ext partitions in windows using partition magic and then reformated them using the gusty installer. 

The lock-ups can occur at start up, during login off or at any point when using no specific application in x. 

I like linux and I need it for my college course, so if I could get it stable I would be very happy.

Thanks in advance.

---

### Post by finer recliner on 2007-11-19
do you use compiz or beryl or compiz fusion?

the latest ubuntu comes with compiz enabled by default. try turning it off.

---

### Post by philinux on 2007-11-19
Before blaming the grapichs driver, have alook in system monitor, processes tab and loook whats eating cpu.

Also if it does lock up rather than reset try hold down Alt PrintScreen with your pinkies and type 

[FONT="Comic Sans MS"]REISUB[/FONT] this will soft boot the machine.

---

### Post by cmnorton on 2007-11-19
Look at the output of dmesg as well. You can attack the problem one of several ways. One would be use to take disk i/o out of this (as much as possible) and use a live distribution and do as much work without writing to your hard drive. Got a memory stick? Write to that, and see if you get the same freeze.

Look at /var/log/messages and /var/log/syslog for any other information as well.

---

### Post by OzyOly on 2007-11-19
> **cmnorton said:**
> Look at the output of dmesg as well. You can attack the problem one of several ways. One would be use to take disk i/o out of this (as much as possible) and use a live distribution and do as much work without writing to your hard drive. Got a memory stick? Write to that, and see if you get the same freeze.

Look at /var/log/messages and /var/log/syslog for any other information as well.

The dmesg output is;

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=594b9d30-a2d6-41e0-8ce8-4c7f79a801ad ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F79C0 checksum 0
[    0.000000] ACPI: RSDP 000F79C0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 7FEE3040, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 4530 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: MCFG 7FEE7800, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE7700, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7FEE7880, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    0.000000] ACPI: SSDT 7FEE7D10, 02F1 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1140 pages reserved
[    0.000000]   DMA zone: 2803 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515599
[    0.000000] Kernel command line: root=UUID=594b9d30-a2d6-41e0-8ce8-4c7f79a801ad ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   24.707158] time.c: Detected 2730.407 MHz processor.
[   24.707756] Console: colour VGA+ 80x25
[   24.707767] Checking aperture...
[   24.707774] Calgary: detecting Calgary via BIOS EBDA area
[   24.707776] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   24.724923] Memory: 2054984k/2096000k available (2274k kernel code, 40628k reserved, 1181k data, 296k init)
[   24.724953] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   24.801872] Calibrating delay using timer specific routine.. 5347.00 BogoMIPS (lpj=10694005)
[   24.801897] Security Framework v1.0.0 initialized
[   24.801899] SELinux:  Disabled at boot.
[   24.802039] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   24.802486] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.802730] Mount-cache hash table entries: 256
[   24.802804] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.802806] CPU: L2 cache: 4096K
[   24.802808] CPU 0/0 -> Node 0
[   24.802809] using mwait in idle threads.
[   24.802810] CPU: Physical Processor ID: 0
[   24.802811] CPU: Processor Core ID: 0
[   24.802816] CPU0: Thermal monitoring enabled (TM1)
[   24.802822] SMP alternatives: switching to UP code
[   24.802980] Early unpacking initramfs... done
[   25.150563] ACPI: Core revision 20070126
[   25.150591] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.199862] Using local APIC timer interrupts.
[   25.236487] result 17065036
[   25.236488] Detected 17.065 MHz APIC timer.
[   25.239938] SMP alternatives: switching to SMP code
[   25.239993] Booting processor 1/2 APIC 0x1
[   25.250088] Initializing CPU#1
[   25.325934] Calibrating delay using timer specific routine.. 5339.86 BogoMIPS (lpj=10679732)
[   25.325939] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.325940] CPU: L2 cache: 4096K
[   25.325942] CPU 1/1 -> Node 0
[   25.325943] CPU: Physical Processor ID: 0
[   25.325944] CPU: Processor Core ID: 1
[   25.325948] CPU1: Thermal monitoring enabled (TM2)
[   25.326306] Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz stepping 06
[   25.326387] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   25.349420] Brought up 2 CPUs
[   25.465946] migration_cost=10
[   25.466063] NET: Registered protocol family 16
[   25.466115] ACPI: bus type pci registered
[   25.466120] PCI: Using configuration type 1
[   25.466902] ACPI: EC: Look up EC in DSDT
[   25.470585] ACPI: Interpreter enabled
[   25.470588] ACPI: (supports S0 S3 S4 S5)
[   25.470603] ACPI: Using IOAPIC for interrupt routing
[   25.474836] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.474839] PCI: Probing PCI hardware (bus 00)
[   25.475256] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   25.475259] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   25.476056] PCI: Transparent bridge - 0000:00:1e.0
[   25.476113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.476215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   25.476268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   25.476323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   25.476377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[   25.476428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.485118] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   25.485188] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   25.485257] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   25.485326] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   25.485395] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   25.485464] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   25.485533] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   25.485602] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   25.485667] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.485673] pnp: PnP ACPI init
[   25.485678] ACPI: bus type pnp registered
[   25.487959] pnp: PnP ACPI: found 15 devices
[   25.487961] ACPI: ACPI bus type pnp unregistered
[   25.487992] PCI: Using ACPI for IRQ routing
[   25.487993] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.488067] NET: Registered protocol family 8
[   25.488068] NET: Registered protocol family 20
[   25.488079] PCI-GART: No AMD northbridge found.
[   25.488113] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[   25.488116] pnp: 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.488121] pnp: 00:0e: iomem range 0xd2800-0xd3fff has been reserved
[   25.488123] pnp: 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   25.488125] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   25.488127] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   25.488319] PCI: Bridge: 0000:00:01.0
[   25.488321]   IO window: e000-efff
[   25.488323]   MEM window: fd700000-fd7fffff
[   25.488326]   PREFETCH window: d0000000-dfffffff
[   25.488328] PCI: Bridge: 0000:00:1c.0
[   25.488330]   IO window: d000-dfff
[   25.488333]   MEM window: fd400000-fd4fffff
[   25.488336]   PREFETCH window: fde00000-fdefffff
[   25.488340] PCI: Bridge: 0000:00:1c.1
[   25.488341]   IO window: c000-cfff
[   25.488345]   MEM window: fdd00000-fddfffff
[   25.488348]   PREFETCH window: fdc00000-fdcfffff
[   25.488351] PCI: Bridge: 0000:00:1c.4
[   25.488353]   IO window: b000-bfff
[   25.488357]   MEM window: fdb00000-fdbfffff
[   25.488359]   PREFETCH window: fda00000-fdafffff
[   25.488363] PCI: Bridge: 0000:00:1c.5
[   25.488365]   IO window: 9000-9fff
[   25.488368]   MEM window: fd900000-fd9fffff
[   25.488371]   PREFETCH window: fd800000-fd8fffff
[   25.488374] PCI: Bridge: 0000:00:1e.0
[   25.488376]   IO window: a000-afff
[   25.488380]   MEM window: fd600000-fd6fffff
[   25.488382]   PREFETCH window: fd500000-fd5fffff
[   25.488392] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.488395] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.488407] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.488411] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.488424] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   25.488427] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   25.488439] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   25.488442] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   25.488454] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   25.488458] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   25.488465] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.488472] NET: Registered protocol family 2
[   25.490197] Time: tsc clocksource has been installed.
[   25.524332] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   25.524855] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   25.527107] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   25.527644] TCP: Hash tables configured (established 262144 bind 65536)
[   25.527646] TCP reno registered
[   25.536548] checking if image is initramfs... it is
[   26.015165] Freeing initrd memory: 7200k freed
[   26.017591] audit: initializing netlink socket (disabled)
[   26.017604] audit(1195490141.272:1): initialized
[   26.018948] VFS: Disk quotas dquot_6.5.1
[   26.018980] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   26.019037] io scheduler noop registered
[   26.019038] io scheduler anticipatory registered
[   26.019039] io scheduler deadline registered
[   26.019098] io scheduler cfq registered (default)
[   26.020706] Boot video device is 0000:01:00.0
[   26.020793] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.020815] assign_interrupt_mode Found MSI capability
[   26.020817] Allocate Port Service[0000:00:01.0:pcie00]
[   26.020870] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.020900] assign_interrupt_mode Found MSI capability
[   26.020902] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.020925] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.020978] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   26.021008] assign_interrupt_mode Found MSI capability
[   26.021009] Allocate Port Service[0000:00:1c.1:pcie00]
[   26.021027] Allocate Port Service[0000:00:1c.1:pcie02]
[   26.021082] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   26.021112] assign_interrupt_mode Found MSI capability
[   26.021114] Allocate Port Service[0000:00:1c.4:pcie00]
[   26.021132] Allocate Port Service[0000:00:1c.4:pcie02]
[   26.021187] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   26.021217] assign_interrupt_mode Found MSI capability
[   26.021218] Allocate Port Service[0000:00:1c.5:pcie00]
[   26.021239] Allocate Port Service[0000:00:1c.5:pcie02]
[   26.034580] Real Time Clock Driver v1.12ac
[   26.034642] Linux agpgart interface v0.102 (c) Dave Jones
[   26.034644] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.034724] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.034823] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.035144] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.035277] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.035692] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.035774] input: Macintosh mouse button emulation as /class/input/input0
[   26.035821] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.035822] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.036139] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.036144] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.036302] mice: PS/2 mouse device common for all mice
[   26.036417] TCP cubic registered
[   26.036479] NET: Registered protocol family 1
[   26.036636] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   26.036640] Freeing unused kernel memory: 296k freed
[   27.150888] AppArmor: AppArmor initialized<5>audit(1195490142.404:2):  type=1505 info="AppArmor initialized" pid=1245
[   27.154740] fuse init (API version 7.8)
[   27.157074] Failure registering capabilities with primary security module.
[   27.181687] ACPI: Fan [FAN] (on)
[   27.184271] ACPI: SSDT 7FEE7C80, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   27.184353] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.184359] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.184969] ACPI: Thermal Zone [THRM] (43 C)
[   27.471717] usbcore: registered new interface driver usbfs
[   27.471737] usbcore: registered new interface driver hub
[   27.471751] usbcore: registered new device driver usb
[   27.471882] SCSI subsystem initialized
[   27.474636] libata version 2.21 loaded.
[   27.475427] ata_piix 0000:00:1f.1: version 2.11
[   27.475442] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.486545] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.500212] scsi0 : ata_piix
[   27.500343] scsi1 : ata_piix
[   27.500491] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001fb00 irq 14
[   27.500494] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001fb08 irq 15
[   27.504299] USB Universal Host Controller Interface driver v3.0
[   27.506287] Floppy drive(s): fd0 is 1.44M
[   27.527234] FDC 0 is a post-1991 82077
[   27.815362] ata1.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[   27.985459] ata1.00: configured for UDMA/33
[   28.150967] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[   28.151282] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   28.151302] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   28.151320] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.151342] scsi2 : ata_piix
[   28.151449] scsi3 : ata_piix
[   28.151593] ata3: SATA max UDMA/133 cmd 0x000000000001fa00 ctl 0x000000000001f902 bmdma 0x000000000001f600 irq 19
[   28.151595] ata4: SATA max UDMA/133 cmd 0x000000000001f800 ctl 0x000000000001f702 bmdma 0x000000000001f608 irq 19
[   28.322402] ata3.00: ATA-6: WDC WD740GD-41FLC2, 31.08F31, max UDMA/133
[   28.322406] ata3.00: 145226112 sectors, multi 16: LBA48 
[   28.336136] ata3.01: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   28.336139] ata3.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.353196] ata3.00: configured for UDMA/133
[   28.372798] ata3.01: configured for UDMA/133
[   28.536122] ata4.00: ATA-7: HDT722525DLA380, V44OA96A, max UDMA/133
[   28.536125] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.550815] ata4.00: configured for UDMA/133
[   28.550879] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740GD-41FL 31.0 PQ: 0 ANSI: 5
[   28.551262] scsi 2:0:1:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   28.551494] scsi 3:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[   28.553083] ahci 0000:05:00.0: version 2.2
[   28.553099] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.534289] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[   29.534293] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   29.534300] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   29.534361] scsi4 : ahci
[   29.534413] ata5: SATA max UDMA/133 cmd 0xffffc20000ab0100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   29.843562] ata5: SATA link down (SStatus 0 SControl 300)
[   29.843689] r8169 Gigabit Ethernet driver 2.2LK loaded
[   29.843709] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.843726] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   29.844013] eth0: RTL8168b/8111b at 0xffffc20000aae000, 00:01:29:d6:d6:11, XID 38000000 IRQ 16
[   29.845085] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   29.845699] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.845704] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.845803] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   29.845827] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   29.845834] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[   29.849619] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.849697] usb usb1: configuration #1 chosen from 1 choice
[   29.849717] hub 1-0:1.0: USB hub found
[   29.849722] hub 1-0:1.0: 8 ports detected
[   29.852021] sd 2:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[   29.852029] sd 2:0:0:0: [sda] Write Protect is off
[   29.852030] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.852039] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.852071] sd 2:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[   29.852076] sd 2:0:0:0: [sda] Write Protect is off
[   29.852077] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.852086] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.852089]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   29.856394] Uniform CD-ROM driver Revision: 3.20
[   29.856432] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   29.858462]  sda1
[   29.858507] sd 2:0:0:0: [sda] Attached SCSI disk
[   29.858628] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.858639] sd 2:0:1:0: [sdb] Write Protect is off
[   29.858642] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.858657] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.858696] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.858705] sd 2:0:1:0: [sdb] Write Protect is off
[   29.858708] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.858724] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.858728]  sdb:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   29.860508] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.860518] sd 2:0:1:0: Attached scsi generic sg2 type 0
[   29.860529] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[   29.864236]  sdb1 < sdb5 >
[   29.871225] sd 2:0:1:0: [sdb] Attached SCSI disk
[   29.871267] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   29.871278] sd 3:0:0:0: [sdc] Write Protect is off
[   29.871281] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   29.871303] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.871327] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   29.871333] sd 3:0:0:0: [sdc] Write Protect is off
[   29.871334] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   29.871343] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.871345]  sdc: sdc1 sdc2 < sdc5 sdc6 >
[   29.923106] sd 3:0:0:0: [sdc] Attached SCSI disk
[   29.951048] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[   29.951057] PCI: Setting latency timer of device 0000:06:03.0 to 64
[   29.952681] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   29.952689] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.952691] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.952708] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   29.952779] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[   29.952842] usb usb2: configuration #1 chosen from 1 choice
[   29.952859] hub 2-0:1.0: USB hub found
[   29.952872] hub 2-0:1.0: 2 ports detected
[   30.003007] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd6ff000-fd6ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.055784] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   30.055796] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   30.055799] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   30.055822] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   30.055845] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[   30.055943] usb usb3: configuration #1 chosen from 1 choice
[   30.055959] hub 3-0:1.0: USB hub found
[   30.055963] hub 3-0:1.0: 2 ports detected
[   30.127320] Attempting manual resume
[   30.127322] swsusp: Resume From Partition 8:38
[   30.127323] PM: Checking swsusp image.
[   30.127464] PM: Resume from disk failed.
[   30.134385] EXT3-fs: INFO: recovery required on readonly filesystem.
[   30.134387] EXT3-fs: write access will be enabled during recovery.
[   30.157066] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   30.157076] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   30.157080] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   30.157103] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   30.157129] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[   30.157218] usb usb4: configuration #1 chosen from 1 choice
[   30.157233] hub 4-0:1.0: USB hub found
[   30.157236] hub 4-0:1.0: 2 ports detected
[   30.258416] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   30.258425] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   30.258428] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   30.258447] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   30.258471] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[   30.258566] usb usb5: configuration #1 chosen from 1 choice
[   30.258596] hub 5-0:1.0: USB hub found
[   30.258599] hub 5-0:1.0: 2 ports detected
[   30.607930] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   30.785909] usb 4-1: configuration #1 chosen from 1 choice
[   30.790531] kjournald starting.  Commit interval 5 seconds
[   30.790540] EXT3-fs: recovery complete.
[   30.794033] EXT3-fs: mounted filesystem with ordered data mode.
[   31.021793] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   31.202077] usb 5-1: configuration #1 chosen from 1 choice
[   31.205024] usbcore: registered new interface driver hiddev
[   31.210236] input: Microsoft Microsoft® Keyboard with Fingerprint Reader as /class/input/input1
[   31.210244] input: USB HID v1.11 Keyboard [Microsoft Microsoft® Keyboard with Fingerprint Reader] on usb-0000:00:1d.2-1
[   31.245471] input: Microsoft Microsoft Wireless Optical Mouse® 1.0A as /class/input/input2
[   31.245482] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.0A] on usb-0000:00:1d.3-1
[   31.245488] usbcore: registered new interface driver usbhid
[   31.245490] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.253441] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200005a83a]
[   37.802465] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.850308] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.922065] input: PC Speaker as /class/input/input3
[   37.945555] intel_rng: FWH not detected
[   37.953873] parport_pc 00:09: reported by Plug and Play ACPI
[   37.953926] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.095797] iTCO_vendor_support: vendor-support=0
[   38.096389] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   38.097412] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   38.097446] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.186353] usbcore: registered new interface driver xpad
[   38.186356] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   38.297298] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.297943] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.511098] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   38.640996] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   38.641046] PCI: Setting latency timer of device 0000:06:01.0 to 64
[   38.644325] Audigy2 value: Special config.
[   39.260403] loop: module loaded
[   39.280428] lp0: using parport0 (interrupt-driven).
[   39.366763] Adding 2096440k swap on /dev/sdc6.  Priority:-1 extents:1 across:2096440k
[   39.734340] EXT3 FS on sdc5, internal journal
[   40.775920] input: Power Button (FF) as /class/input/input4
[   40.776029] ACPI: Power Button (FF) [PWRF]
[   40.792166] input: Power Button (CM) as /class/input/input5
[   40.793762] ACPI: Power Button (CM) [PWRB]
[   40.799070] No dock devices found.
[   41.592702] ppdev: user-space parallel port driver
[   41.699128] audit(1195490157.501:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5172 profile="/usr/sbin/cupsd"
[   41.822101] Failure registering capabilities with primary security module.
[   41.838839] r8169: eth0: link up
[   41.838848] r8169: eth0: link up
[   41.933921] Bluetooth: Core ver 2.11
[   41.933962] NET: Registered protocol family 31
[   41.933963] Bluetooth: HCI device and connection manager initialized
[   41.933965] Bluetooth: HCI socket layer initialized
[   41.938186] Bluetooth: L2CAP ver 2.8
[   41.938188] Bluetooth: L2CAP socket layer initialized
[   41.959239] Bluetooth: RFCOMM socket layer initialized
[   41.959248] Bluetooth: RFCOMM TTY layer initialized
[   41.959250] Bluetooth: RFCOMM ver 1.8
[   44.077852] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   44.079736] [fglrx] Maximum main memory to use for locked dma buffers: 1887 MBytes.
[   44.079929] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   44.095646] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.074069] NET: Registered protocol family 17
[   47.301279] [fglrx] total      GART = 130023424
[   47.301284] [fglrx] free       GART = 114032640
[   47.301287] [fglrx] max single GART = 114032640
[   47.301290] [fglrx] total      LFB  = 268304384
[   47.301292] [fglrx] free       LFB  = 250474496
[   47.301294] [fglrx] max single LFB  = 250474496
[   47.301297] [fglrx] total      Inv  = 268435456
[   47.301300] [fglrx] free       Inv  = 268435456
[   47.301302] [fglrx] max single Inv  = 268435456
[   47.301304] [fglrx] total      TIM  = 0
[   48.428704] NET: Registered protocol family 10
[   48.428865] lo: Disabled Privacy Extensions
[   58.517472] eth0: no IPv6 routers present
```


In the messages log, in the time just before it freezes I get;

```
 Nov 19 16:54:11 powerpc kernel: [   48.383789] lo: Disabled Privacy Extensions 
```


The soft reboot doesn't seem to work, I still have to kill the power.


Here are the last few messages from the system log before it froze last;

```

Nov 19 16:54:11 powerpc kernel: [   48.383789] lo: Disabled Privacy Extensions
Nov 19 16:54:13 powerpc avahi-daemon[5393]: Registering new address record for fe80::201:29ff:fed6:d611 on eth0.*.
Nov 19 16:54:15 powerpc ntpdate[5730]: no server suitable for synchronization found
Nov 19 16:54:22 powerpc kernel: [   59.205666] eth0: no IPv6 routers present
Nov 19 16:54:22 powerpc hcid[5437]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Nov 19 16:54:22 powerpc hcid[5437]: Default authorization agent (:1.18, /org/bluez/auth) registered
Nov 19 16:54:25 powerpc NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 19 16:54:25 powerpc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..  
```

The system monitor is in the attachment.

---

### Post by OzyOly on 2007-11-19
> **finer recliner said:**
> do you use compiz or beryl or compiz fusion?

the latest ubuntu comes with compiz enabled by default. try turning it off.


It freezes with compiz enabled and disabled as well as with the default graphics drivers and the restricted ones.

---

### Post by panand178 on 2007-11-19
Just happened to bump into this thread. It looks like this is the same issue that I'm facing too. 

[http://ubuntuforums.org/showthread.php?t=616375]("http://ubuntuforums.org/showthread.php?t=616375")

I could use all the help that I can get on this. 

Thanks in advance,

---

### Post by POWERVICE on 2007-11-20
Hello, I am an absolute beginner with probably much less knowledge than yourself. However I was experiencing the same lockup problem but I seem to have completely curred it by using an ethernet modem. I worked out all my lockups occurred whenever the normal usb modem was connected. My new modem sent FOC by TISCALI is a speedtouch510 (I know there are much more advanced ones) but it takes about 1 minute to set up (simply plug in an attempt to visit any website (eg [www.tiscali.co.uk](www.tiscali.co.uk)). This opens up the THOMSON wizard which asks you for your name and password. That is all there is to it!! This appears to have worked for me and I really hope this helps someone. Sorry i was a touch premature - my lock ups returned and now occur even when not accessing internet

---

### Post by OzyOly on 2007-11-20
It's SOLVED for me now. I did something that I should have done in the first place - I reflashed my bios with the latest version and I cleared my cmos. All seems to be working now.

Well.....so far so good.

---

### Post by panand178 on 2007-11-21
I'm already using an ethernet modem so i dont think that could be what is causing the problem. I've noticed that it happens:

1. When i directly click on any link in akregator. 
2. When I start dragging an image or portion of text in Firefox and then leaving it. 

OzyOly: Could you please tell me how to reflash my bios adn cleaer my CMOS? Also does that mean that I'll have to reinstall Win XP and Ubuntu?

---

### Post by OzyOly on 2007-11-21
> **panand178 said:**
> I'm already using an ethernet modem so i dont think that could be what is causing the problem. I've noticed that it happens:

1. When i directly click on any link in akregator. 
2. When I start dragging an image or portion of text in Firefox and then leaving it. 

OzyOly: Could you please tell me how to reflash my bios adn cleaer my CMOS? Also does that mean that I'll have to reinstall Win XP and Ubuntu?

Hey there. Well it all depends on the make and model of your motherboard. You need to find out the make and model and revison and head over to your manufactures website and download the latest bios. Make sure you get the right one or you could stop your pc from booting all together.

As for flashing it, I used winflash, but your manufacture might have their own flashing tools. You don't have to flash from windows, you can also use a floppy disc and boot from that.

If you've never flashed a bios before, read up on it either on wiki or on your manufacturers website, because flashing it bad can be fatel to your motherboard.

For clearing the cmos, I just cleared it when I flashed it, that's just good practice, but if you want to clear it without reflashing your bios, you can just removed the power to you pc/motherboard and remove the battery on your motherboard for a few hours. This will reset your cmos so your bios will load to defaults.

I hope that is clear enough, if not just pm me.

---

### Post by Vadi on 2007-11-21
I randomly get the same problem with my wireless card - so I think we're all internet-related here.

By the way, this thread will be useful to you ([click]("http://ubuntuforums.org/showthread.php?t=617349")).

---

### Post by OzyOly on 2007-11-21
> **Vadi said:**
> I randomly get the same problem with my wireless card - so I think we're all internet-related here.

By the way, this thread will be useful to you ([click]("http://ubuntuforums.org/showthread.php?t=617349")).

I've had so much trouble with wireless card, not on ubunutu, but on windows, it turned out to be a really crappy driver, it used to freeze my system every time it lost connection. 

I don't know what you can do out the card on ubuntu though...

---

### Post by Vadi on 2007-11-21
Yeah I haven't been experiencing lately, but looking at the log, it does the renewal thing often, and it has a random chance of freezing when it does, apparently.

Sad thing is that the card I bought is based on a chipset praised by the FSF - I got it for it to only turn out that Ubuntu *completely* doesn't recognize it, and that I have to compile the native drivers manually (and the instructions were plain horrid). So, yes, it's ndiswrapper + windows version of the driver for me...

---

