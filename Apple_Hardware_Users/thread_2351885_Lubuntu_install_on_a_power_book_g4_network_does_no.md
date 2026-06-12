---
title: "Lubuntu install on a power book g4 network does not work"
date: 2017-02-07
forum: Apple Hardware Users
---

### Post by jake82 on 2017-02-07
so i just installed lubuntu 14.04 PPC on a power book g4 and everything works except for the internet (both wifi and ethernet) lspci -nn | grep 0200 tells me that the Ethernet controller is apple inc. but 0280 doesn't give me anything and yes i tried downloading both b43 and b43 legacy on another pc and then installing to the PPC but still no change

---

### Post by howefield on 2017-02-07
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by rican-linux on 2017-02-08
try running this commands

```

modprobe -r b43
modprobe b43

```

Wireless should be working after that.

---

### Post by jake82 on 2017-02-08
Sorry... Should have said I did that... I've researched everything about it and everyone always said to do that but it doesn't work. And I know the wireless worked on Mac OS

---

### Post by rican-linux on 2017-02-08
can you give us the output of *lspci -vvvv*? I have a PowerBook and an iBook and wireless is working on both.

---

### Post by jake82 on 2017-02-08
```
0000:00:0b.0 Host bridge: Apple Inc. UniNorth 1.5 AGP
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Capabilities: [80] AGP version 1.0
		Status: RQ=8 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel driver in use: agpgart-uninorth


0000:00:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV250/M9 GL [Mobility FireGL 9000/Radeon 9000] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RV250/M9 GL [Mobility FireGL 9000/Radeon 9000]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 255 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at b8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 0400 [size=256]
	Region 2: Memory at b0000000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at b0020000 [size=128K]
	Capabilities: [58] AGP version 2.0
		Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: radeonfb


0001:10:0b.0 Host bridge: Apple Inc. UniNorth 1.5 PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes


0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo Mac I/O (rev 03)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: macio


0001:10:18.0 USB controller: Apple Inc. KeyLargo USB (prog-if 10 [OHCI])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at a0002000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


0001:10:19.0 USB controller: Apple Inc. KeyLargo USB (prog-if 10 [OHCI])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at a0001000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 58
	Region 0: Memory at a0000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=10, secondary=11, subordinate=14, sec-latency=176
	Memory window 0: 84000000-87ffffff (prefetchable)
	Memory window 1: 88000000-8bffffff
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001100-000011ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Capabilities: [a0] Power Management version 1
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Kernel driver in use: yenta_cardbus


0002:24:0b.0 Host bridge: Apple Inc. UniNorth 1.5 Internal PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes


0002:24:0e.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (prog-if 10 [OHCI])
	Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 40
	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: firewire_ohci


0002:24:0f.0 Ethernet controller: Apple Inc. UniNorth GMAC (Sun GEM) (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 16 (16000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 41
	Region 0: Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
	Expansion ROM at f5100000 [disabled] [size=1M]
	Kernel driver in use: gem
```

---

### Post by rican-linux on 2017-02-08
Well the kernel does not see your wireless controller. What model is this PowerBook?

---

### Post by jake82 on 2017-02-08
Hey I'm coming home from working on another pc...  I'll check it in a min

[http://www.welovemacs.com/appog41g15tm16.html](http://www.welovemacs.com/appog41g15tm16.html) it was upgraded to 1gb of ram

---

### Post by rican-linux on 2017-02-08
Can you post your dmesg output? When you do mark it as code so it will be easier to read.

Thanks

---

### Post by wildmanne39 on 2017-02-08
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jake82 on 2017-02-08
oops sorry i'm not to familiar with Ubuntu forums... btw i also tried wicd and that didn't work either

```
[    0.000000] Using PowerMac machine description[    0.000000] Total memory = 512MB; using 1024kB for hash table (at cff00000)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-32-powerpc-smp (buildd@sagari) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #57-Ubuntu SMP Tue Jul 15 03:50:44 UTC 2014 (Ubuntu 3.13.0-32.57-powerpc-smp 3.13.11.4)
[    0.000000] Found initrd at 0xc1a00000:0xc2c41000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x11
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerBook Titanium IV
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] CPU maps initialized for 1 thread per core
[    0.000000]  (thread shift is 0)
[    0.000000] bootconsole [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x00000000b0000000..0x00000000bfffffff -> 0x00000000b0000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x00000000afffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=686, gen1=687
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x20000000, Total RAM: 0x20000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00000000-0x1fffffff]
[    0.000000]   Normal   empty
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00000000-0x1fffffff]
[    0.000000] On node 0 totalpages: 131072
[    0.000000] free_area_init_node: node 0, pgdat c0a43c00, node_mem_map c0c49000
[    0.000000]   DMA zone: 1024 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 131072 pages, LIFO batch:31
[    0.000000] PERCPU: Embedded 9 pages/cpu @c104d000 s15520 r8192 d13152 u36864
[    0.000000] pcpu-alloc: s15520 r8192 d13152 u36864 alloc=9*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=UUID=17b7b97a-c78c-4caf-9853-4edf112a8d03 ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Sorting __ex_table...
[    0.000000] allocated 1048576 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Memory: 420504K/524288K available (7260K kernel code, 496K rwdata, 2384K rodata, 500K init, 1870K bss, 103784K reserved, 0K highmem)
[    0.000000] Kernel virtual memory layout:
[    0.000000]   * 0xfff9f000..0xfffff000  : fixmap
[    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
[    0.000000]   * 0xfdf32000..0xff800000  : early ioremap
[    0.000000]   * 0xe1000000..0xfdf32000  : vmalloc & ioremap
[    0.000000] SLUB: HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=4 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:512 nr_irqs:512 16
[    0.000000] mpic: Resetting
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 1 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 33.330748 MHz
[    0.000000] time_init: processor frequency   = 667.000000 MHz
[    0.000000] clocksource: timebase mult[1e009880] shift[24] registered
[    0.000000] clockevent: decrementer mult[8885d29] shift[32] cpu[0]
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] bootconsole [udbg0] disabled
[    0.000443] pid_max: default: 32768 minimum: 301
[    0.000593] Security Framework initialized
[    0.000681] AppArmor: AppArmor initialized
[    0.000689] Yama: becoming mindful.
[    0.000888] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000899] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.001616] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.007055] Initializing cgroup subsys memory
[    0.007089] Initializing cgroup subsys devices
[    0.007098] Initializing cgroup subsys freezer
[    0.007108] Initializing cgroup subsys blkio
[    0.007117] Initializing cgroup subsys perf_event
[    0.007243] ftrace: allocating 24013 entries in 71 pages
[    0.045162] PowerMac SMP probe found 1 cpus
[    0.045184] MPC7450 family performance monitor hardware support registered
[    0.051039] Brought up 1 CPUs
[    0.051774] devtmpfs: initialized
[    0.052168] EVM: security.selinux
[    0.052178] EVM: security.SMACK64
[    0.052184] EVM: security.capability
[    0.053777] regulator-dummy: no parameters
[    0.054053] NET: Registered protocol family 16
[    0.055024] cpuidle: using governor ladder
[    0.055036] cpuidle: using governor menu
[    0.055284] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.055297]  channel 0 bus <multibus>
[    0.055314]  channel 1 bus <multibus>
[    0.055397] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.055407]  channel 0 bus <multibus>
[    0.055425] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[    0.055434]  channel 1 bus <multibus>
[    0.055441]  channel 2 bus <multibus>
[    0.074389] PCI: Probing PCI hardware
[    0.074718] PCI host bridge to bus 0000:00
[    0.074744] pci_bus 0000:00: root bus resource [io  0x802000-0x1001fff] (bus address [0x0000-0x7fffff])
[    0.074756] pci_bus 0000:00: root bus resource [mem 0xf1000000-0xf1ffffff]
[    0.074767] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xbfffffff]
[    0.074780] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.074794] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to ff
[    0.074858] pci 0000:00:0b.0: [106b:002d] type 00 class 0x060000
[    0.075100] pci 0000:00:10.0: [1002:4c66] type 00 class 0x030000
[    0.075135] pci 0000:00:10.0: reg 0x10: [mem 0xb8000000-0xbfffffff pref]
[    0.075153] pci 0000:00:10.0: reg 0x14: [io  0x802400-0x8024ff]
[    0.075171] pci 0000:00:10.0: reg 0x18: [mem 0xb0000000-0xb000ffff]
[    0.075210] pci 0000:00:10.0: reg 0x30: [mem 0xb0020000-0xb003ffff pref]
[    0.075265] pci 0000:00:10.0: supports D1 D2
[    0.075511] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 00
[    0.075632] PCI host bridge to bus 0001:10
[    0.075645] pci_bus 0001:10: root bus resource [io  0x0000-0x7fffff]
[    0.075656] pci_bus 0001:10: root bus resource [mem 0xf3000000-0xf3ffffff]
[    0.075667] pci_bus 0001:10: root bus resource [mem 0x80000000-0xafffffff]
[    0.075678] pci_bus 0001:10: root bus resource [bus 10-ff]
[    0.075691] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to ff
[    0.075742] pci 0001:10:0b.0: [106b:002e] type 00 class 0x060000
[    0.075956] pci 0001:10:17.0: [106b:0022] type 00 class 0xff0000
[    0.075983] pci 0001:10:17.0: reg 0x10: [mem 0x80000000-0x8007ffff]
[    0.076161] pci 0001:10:18.0: [106b:0019] type 00 class 0x0c0310
[    0.076184] pci 0001:10:18.0: reg 0x10: [mem 0xa0002000-0xa0002fff]
[    0.076388] pci 0001:10:19.0: [106b:0019] type 00 class 0x0c0310
[    0.076411] pci 0001:10:19.0: reg 0x10: [mem 0xa0001000-0xa0001fff]
[    0.076586] pci 0001:10:1a.0: [104c:ac50] type 02 class 0x060700
[    0.076616] pci 0001:10:1a.0: reg 0x10: [mem 0xa0000000-0xa0000fff]
[    0.076662] pci 0001:10:1a.0: supports D1 D2
[    0.076672] pci 0001:10:1a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.076955] pci 0001:10:1a.0: Primary bus is hard wired to 0
[    0.076968] pci 0001:10:1a.0: bridge configuration invalid ([bus 01-01]), reconfiguring
[    0.077227] pci_bus 0001:11: busn_res: [bus 11-ff] end is updated to 14
[    0.077246] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to 14
[    0.077366] PCI host bridge to bus 0002:24
[    0.077381] pci_bus 0002:24: root bus resource [io  0xff7fe000-0xffffdfff] (bus address [0x0000-0x7fffff])
[    0.077392] pci_bus 0002:24: root bus resource [mem 0xf5000000-0xf5ffffff]
[    0.077403] pci_bus 0002:24: root bus resource [bus 24-ff]
[    0.077416] pci_bus 0002:24: busn_res: [bus 24-ff] end is updated to ff
[    0.077465] pci 0002:24:0b.0: [106b:002f] type 00 class 0x060000
[    0.077656] pci 0002:24:0e.0: [11c1:5811] type 00 class 0x0c0010
[    0.077683] pci 0002:24:0e.0: reg 0x10: [mem 0xf5000000-0xf5000fff]
[    0.077753] pci 0002:24:0e.0: supports D1 D2
[    0.077764] pci 0002:24:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.077907] pci 0002:24:0f.0: [106b:0021] type 00 class 0x020000
[    0.077930] pci 0002:24:0f.0: reg 0x10: [mem 0xf5200000-0xf53fffff]
[    0.077981] pci 0002:24:0f.0: reg 0x30: [mem 0xf5100000-0xf51fffff pref]
[    0.078216] pci_bus 0002:24: busn_res: [bus 24-ff] end is updated to 24
[    0.078367] PCI 0000:00 Cannot reserve Legacy IO [io  0x802000-0x802fff]
[    0.078390] pci_bus 0000:00: resource 4 [io  0x802000-0x1001fff]
[    0.078401] pci_bus 0000:00: resource 5 [mem 0xf1000000-0xf1ffffff]
[    0.078412] pci_bus 0000:00: resource 6 [mem 0xb0000000-0xbfffffff]
[    0.078440] pci 0001:10:1a.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.078452] pci 0001:10:1a.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.078464] pci 0001:10:1a.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.078475] pci 0001:10:1a.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.078493] pci 0001:10:1a.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.078506] pci 0001:10:1a.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.078517] pci 0001:10:1a.0: BAR 13: assigned [io  0x1000-0x10ff]
[    0.078529] pci 0001:10:1a.0: BAR 14: assigned [io  0x1100-0x11ff]
[    0.078542] pci 0001:10:1a.0: CardBus bridge to [bus 11-14]
[    0.078553] pci 0001:10:1a.0:   bridge window [io  0x1000-0x10ff]
[    0.078565] pci 0001:10:1a.0:   bridge window [io  0x1100-0x11ff]
[    0.078578] pci 0001:10:1a.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.078591] pci 0001:10:1a.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.078604] pci_bus 0001:10: resource 4 [io  0x0000-0x7fffff]
[    0.078614] pci_bus 0001:10: resource 5 [mem 0xf3000000-0xf3ffffff]
[    0.078625] pci_bus 0001:10: resource 6 [mem 0x80000000-0xafffffff]
[    0.078636] pci_bus 0001:11: resource 0 [io  0x1000-0x10ff]
[    0.078647] pci_bus 0001:11: resource 1 [io  0x1100-0x11ff]
[    0.078658] pci_bus 0001:11: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.078668] pci_bus 0001:11: resource 3 [mem 0x88000000-0x8bffffff]
[    0.078682] pci_bus 0002:24: resource 4 [io  0xff7fe000-0xffffdfff]
[    0.078693] pci_bus 0002:24: resource 5 [mem 0xf5000000-0xf5ffffff]
[    0.085954] bio: create slab <bio-0> at 0
[    0.087313] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
[    0.087344] vgaarb: loaded
[    0.087350] vgaarb: bridge control possible 0000:00:10.0
[    0.088487] SCSI subsystem initialized
[    0.088751] libata version 3.00 loaded.
[    0.088970] usbcore: registered new interface driver usbfs
[    0.089033] usbcore: registered new interface driver hub
[    0.089219] usbcore: registered new device driver usb
[    0.090254] NetLabel: Initializing
[    0.090267] NetLabel:  domain hash size = 128
[    0.090272] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.090335] NetLabel:  unlabeled traffic allowed by default
[    0.090691] Switched to clocksource timebase
[    0.108207] AppArmor: AppArmor Filesystem Enabled
[    0.116317] NET: Registered protocol family 2
[    0.117052] TCP established hash table entries: 4096 (order: 2, 16384 bytes)
[    0.117102] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[    0.117175] TCP: Hash tables configured (established 4096 bind 4096)
[    0.117274] TCP: reno registered
[    0.117289] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.117326] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.117617] NET: Registered protocol family 1
[    0.117724] pci 0001:10:18.0: enabling device (0000 -> 0002)
[    0.170794] pci 0001:10:19.0: enabling device (0000 -> 0002)
[    0.226752] PCI: CLS mismatch (32 != 1020), using 32 bytes
[    0.227056] Trying to unpack rootfs image as initramfs...
[    1.464547] Freeing initrd memory: 18692K (c1a00000 - c2c41000)
[    1.465032] Thermal assist unit not available
[    1.465983] Initialise system trusted keyring
[    1.466194] audit: initializing netlink socket (disabled)
[    1.466244] type=2000 audit(1486970907.452:1): initialized
[    1.605436] zbud: loaded
[    1.605938] VFS: Disk quotas dquot_6.5.2
[    1.606146] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.608341] fuse init (API version 7.22)
[    1.608646] msgmni has been set to 988
[    1.608956] Key type big_key registered
[    1.610417] Key type asymmetric registered
[    1.610430] Asymmetric key parser 'x509' registered
[    1.610519] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.610798] io scheduler noop registered
[    1.610809] io scheduler deadline registered (default)
[    1.610981] io scheduler cfq registered
[    1.611381] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.611412] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.611735] radeonfb 0000:00:10.0: enabling device (0086 -> 0087)
[    1.810452] radeonfb 0000:00:10.0: Invalid ROM contents
[    1.810469] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
[    1.810483] radeonfb: Retrieved PLL infos from Open Firmware
[    1.810494] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=200.00 Mhz, System=200.00 MHz
[    1.810500] radeonfb: PLL min 12000 max 35000
[    1.907789] i2c i2c-2: unable to read EDID block.
[    2.059779] i2c i2c-2: unable to read EDID block.
[    2.211779] i2c i2c-2: unable to read EDID block.
[    2.363778] i2c i2c-3: unable to read EDID block.
[    2.515779] i2c i2c-3: unable to read EDID block.
[    2.667778] i2c i2c-3: unable to read EDID block.
[    2.723702] radeonfb: Monitor 1 type LCD found
[    2.723709] radeonfb: EDID probed
[    2.723716] radeonfb: Monitor 2 type no found
[    2.723733] radeonfb: Using Firmware dividers 0x0002008e from PPLL 0
[    2.882702] radeonfb: Dynamic Clock Power Management enabled
[    2.916536] Console: switching to colour frame buffer device 160x53
[    2.938310] radeonfb: Backlight initialized (radeonbl0)
[    2.938318] radeonfb (0000:00:10.0): ATI Radeon 4c66 "Lf"
[    2.938833] ipmi message handler version 39.2
[    2.940103] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.945540] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[    2.945637] ePAPR hypervisor byte channel driver
[    2.945907] Generic non-volatile memory driver v1.1
[    2.946058] Linux agpgart interface v0.103
[    2.952329] brd: module loaded
[    2.955536] loop: module loaded
[    2.956004] MacIO PCI driver attached to Keylargo chipset
[    2.957725] 0.00013020:ch-a: ttyPZ0 at MMIO 0x80013020 (irq = 22, base_baud = 230400) is a Z85c30 ESCC - Serial port
[    2.958235] 0.00013000:ch-b: ttyPZ1 at MMIO 0x80013000 (irq = 23, base_baud = 230400) is a Z85c30 ESCC - Serial port
[    2.959936] adb: starting probe task...
[    3.213037] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[    3.219770] ADB keyboard at 2, handler 1
[    3.219807] Detected ADB keyboard, type ANSI.
[    3.219996] input: ADB keyboard as /devices/virtual/input/input0
[    3.220188] input: ADB Powerbook buttons as /devices/virtual/input/input1
[    3.235200] ADB mouse at 3, handler set to 4 (trackpad)
[    3.295125] input: ADB mouse as /devices/virtual/input/input2
[    3.295139] adb: finished probe task...
[    3.978722] pata-macio 0.0001f000:ata-4: Activating pata-macio chipset KeyLargo ATA-4, Apple bus ID 2
[    3.979374] scsi0 : pata_macio
[    3.979609] ata1: PATA max UDMA/66 irq 19
[    4.500958] ata1.00: ATA-6: FUJITSU MHS2060AT, 8105, max UDMA/100
[    4.500975] ata1.00: 117210240 sectors, multi 16: LBA48 
[    4.576895] ata1.00: configured for UDMA/66
[    4.577357] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHS2060A 8105 PQ: 0 ANSI: 5
[    4.577986] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.578397] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.578642] sd 0:0:0:0: [sda] Write Protect is off
[    4.578657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.578857] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.986405]  sda: [mac] sda1 sda2 sda3 sda4 sda5
[    4.988199] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.998717] pata-macio 0.00020000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 0
[    4.999413] scsi1 : pata_macio
[    4.999614] ata2: PATA max MWDMA2 irq 20
[    5.001302] libphy: Fixed MDIO Bus: probed
[    5.001905] tun: Universal TUN/TAP device driver, 1.6
[    5.001913] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.002156] PPP generic driver version 2.4.2
[    5.002397] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.002529] ehci-pci: EHCI PCI platform driver
[    5.002597] ehci-platform: EHCI generic platform driver
[    5.002645] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.002933] ohci-pci: OHCI PCI platform driver
[    5.003045] ohci-pci 0001:10:18.0: OHCI PCI host controller
[    5.003073] ohci-pci 0001:10:18.0: new USB bus registered, assigned bus number 1
[    5.003183] ohci-pci 0001:10:18.0: irq 27, io mem 0xa0002000
[    5.078745] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    5.078759] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.078769] usb usb1: Product: OHCI PCI host controller
[    5.078779] usb usb1: Manufacturer: Linux 3.13.0-32-powerpc-smp ohci_hcd
[    5.078789] usb usb1: SerialNumber: 0001:10:18.0
[    5.079327] hub 1-0:1.0: USB hub found
[    5.079386] hub 1-0:1.0: 2 ports detected
[    5.079785] ohci-pci 0001:10:19.0: OHCI PCI host controller
[    5.079812] ohci-pci 0001:10:19.0: new USB bus registered, assigned bus number 2
[    5.079891] ohci-pci 0001:10:19.0: irq 28, io mem 0xa0001000
[    5.154731] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    5.154744] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.154754] usb usb2: Product: OHCI PCI host controller
[    5.154764] usb usb2: Manufacturer: Linux 3.13.0-32-powerpc-smp ohci_hcd
[    5.154774] usb usb2: SerialNumber: 0001:10:19.0
[    5.155260] hub 2-0:1.0: USB hub found
[    5.155306] hub 2-0:1.0: 2 ports detected
[    5.155697] ohci-platform: OHCI generic platform driver
[    5.155759] uhci_hcd: USB Universal Host Controller Interface driver
[    5.156581] mousedev: PS/2 mouse device common for all mice
[    5.157389] PowerMac i2c bus pmu 2 registered
[    5.157547] PowerMac i2c bus pmu 1 registered
[    5.157679] PowerMac i2c bus mac-io 0 registered
[    5.157829] i2c i2c-6: No i2c address for /pci@f2000000/mac-io@17/i2c@18000/i2c-modem
[    5.157966] PowerMac i2c bus uni-n 1 registered
[    5.158109] i2c i2c-7: i2c-powermac: modalias failure on /uni-n@f8000000/i2c@f8001000/cereal@1c0
[    5.158244] PowerMac i2c bus uni-n 0 registered
[    5.158588] device-mapper: uevent: version 1.0.3
[    5.159258] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    5.159328] Registering PowerMac CPU frequency driver
[    5.159336] Low: 667 Mhz, High: 1000 Mhz, Boot: 667 Mhz
[    5.159978] ledtrig-cpu: registered to indicate activity on CPUs
[    5.160476] TCP: cubic registered
[    5.160894] NET: Registered protocol family 10
[    5.161543] NET: Registered protocol family 17
[    5.161599] Key type dns_resolver registered
[    5.162101] Loading compiled-in X.509 certificates
[    5.168134] ata2.00: ATAPI: MATSHITADVD-R   UJ-815, D0CB, max UDMA/66
[    5.168691] Loaded X.509 cert 'Magrathea: Glacier signing key: 91a3227842f4967f8c0d3383862af8b97bd343c1'
[    5.168755] registered taskstats version 1
[    5.181796] Key type trusted registered
[    5.183242] ata2.00: configured for MWDMA2
[    5.187526] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-R   UJ-815   D0CB PQ: 0 ANSI: 5
[    5.190501] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.190517] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.191046] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.191418] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.197706] Key type encrypted registered
[    5.209569] AppArmor: AppArmor sha1 policy hashing enabled
[    5.209825] regulator-dummy: disabling
[    5.210186] input: PMU as /devices/virtual/input/input3
[    5.210422] /build/buildd/linux-3.13.0/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    5.211823] Freeing unused kernel memory: 500K (c096f000 - c09ec000)
[    5.291202] systemd-udevd[92]: starting version 204
[    5.454885] usb 1-1: new full-speed USB device number 2 using ohci-pci
[    5.597148] sungem.c:v1.0 David S. Miller <davem@redhat.com>
[    5.597867] gem 0002:24:0f.0 eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:d7:8d:ce
[    5.655180] usb 1-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[    5.667181] usb 1-1: New USB device found, idVendor=0781, idProduct=5581
[    5.667197] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.667204] usb 1-1: Product: Ultra
[    5.667210] usb 1-1: Manufacturer: SanDisk
[    5.667217] usb 1-1: SerialNumber: 4C531001611206101433
[    5.678887] firewire_ohci 0002:24:0e.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    6.016412] usb-storage 1-1:1.0: USB Mass Storage device detected
[    6.016663] scsi2 : usb-storage 1-1:1.0
[    6.017943] usbcore: registered new interface driver usb-storage
[    6.179050] firewire_core 0002:24:0e.0: created device fw0: GUID 000a95fffed78dce, S400
[    6.380710] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    6.380727] EXT4-fs (sda3): write access will be enabled during recovery
[    7.021321] scsi 2:0:0:0: Direct-Access     SanDisk  Ultra            1.00 PQ: 0 ANSI: 6
[    7.024303] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    7.032836] sd 2:0:0:0: [sdb] 60751872 512-byte logical blocks: (31.1 GB/28.9 GiB)
[    7.042200] sd 2:0:0:0: [sdb] Write Protect is off
[    7.042220] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    7.052163] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.139177] random: nonblocking pool is initialized
[    7.139350]  sdb: sdb1
[    7.188267] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.151909] EXT4-fs (sda3): orphan cleanup on readonly fs
[   10.152712] EXT4-fs (sda3): 8 orphan inodes deleted
[   10.152722] EXT4-fs (sda3): recovery complete
[   10.343456] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   28.690504] Adding 2439064k swap on /dev/sda4.  Priority:-1 extents:1 across:2439064k FS
[   28.895082] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.562307] systemd-udevd[277]: starting version 204
[   29.588463] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   30.079165] cfg80211: Calling CRDA to update world regulatory domain
[   30.217025] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   30.263866] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   30.263960] airport: Physical address 80030000
[   30.531249] agpgart-uninorth 0000:00:0b.0: Apple UniNorth 1.5 chipset
[   30.532539] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[   30.623117] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
[   31.472645] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[   31.472775] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
[   31.472785] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
[   31.823138] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[   31.823270] airport 0.00030000:radio: Station identity  001f:0002:0009:0030
[   31.823281] airport 0.00030000:radio: Firmware determined as Lucent/Agere 9.48
[   31.823288] airport 0.00030000:radio: Ad-hoc demo mode supported
[   31.823294] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
[   31.823301] airport 0.00030000:radio: WEP supported, 104-bit key
[   31.823307] airport 0.00030000:radio: WPA-PSK supported
[   31.991758] yenta_cardbus 0001:10:1a.0: CardBus bridge found [0000:0000]
[   31.991795] yenta_cardbus 0001:10:1a.0: Enabling burst memory read transactions
[   31.991804] yenta_cardbus 0001:10:1a.0: Using CSCINT to route CSC interrupts to PCI
[   31.991811] yenta_cardbus 0001:10:1a.0: Routing CardBus interrupts to PCI
[   31.991821] yenta_cardbus 0001:10:1a.0: TI: mfunc 0x00000002, devctl 0x60
[   32.068252] type=1400 audit(1486988938.053:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=349 comm="apparmor_parser"
[   32.068290] type=1400 audit(1486988938.053:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=349 comm="apparmor_parser"
[   32.068308] type=1400 audit(1486988938.053:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=349 comm="apparmor_parser"
[   32.069720] type=1400 audit(1486988938.053:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=349 comm="apparmor_parser"
[   32.069752] type=1400 audit(1486988938.053:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=349 comm="apparmor_parser"
[   32.104358] type=1400 audit(1486988938.089:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=349 comm="apparmor_parser"
[   32.107316] yenta_cardbus 0001:10:1a.0: ISA IRQ mask 0x0000, PCI irq 58
[   32.107331] yenta_cardbus 0001:10:1a.0: Socket status: 30000006
[   32.107353] yenta_cardbus 0001:10:1a.0: pcmcia: parent PCI bridge window: [io  0x0000-0x7fffff]
[   32.107362] yenta_cardbus 0001:10:1a.0: pcmcia: parent PCI bridge window: [mem 0xf3000000-0xf3ffffff]
[   32.107371] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf3000000-0xf3ffffff:
[   32.107411]  clean.
[   32.107418] yenta_cardbus 0001:10:1a.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0xafffffff]
[   32.107426] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0xafffffff:
[   32.107434]  excluding 0x80000000-0x807fffff 0x84000000-0x8bffffff 0xa0000000-0xa07fffff
[   32.227007] apm_emu: PMU APM Emulation initialized.
[   32.238667] type=1400 audit(1486988938.221:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=362 comm="apparmor_parser"
[   33.102349] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[   33.751188] i2c i2c-0: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751204] i2c i2c-0: Please use another way to instantiate your i2c_client
[   33.751212] i2c i2c-1: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751218] i2c i2c-1: Please use another way to instantiate your i2c_client
[   33.751226] i2c i2c-2: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751232] i2c i2c-2: Please use another way to instantiate your i2c_client
[   33.751239] i2c i2c-3: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751246] i2c i2c-3: Please use another way to instantiate your i2c_client
[   33.751253] i2c i2c-4: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751259] i2c i2c-4: Please use another way to instantiate your i2c_client
[   33.751267] i2c i2c-5: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751273] i2c i2c-5: Please use another way to instantiate your i2c_client
[   33.751280] i2c i2c-6: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751286] i2c i2c-6: Please use another way to instantiate your i2c_client
[   33.751301] i2c i2c-6: Failed to register i2c client keywest at 0x35 (-16)
[   33.751310] i2c i2c-7: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751316] i2c i2c-7: Please use another way to instantiate your i2c_client
[   33.751324] i2c i2c-8: PMac Keywest Audio: attach_adapter method is deprecated
[   33.751330] i2c i2c-8: Please use another way to instantiate your i2c_client
[   33.752848] ------------[ cut here ]------------
[   33.752868] WARNING: at /build/buildd/linux-3.13.0/sound/ppc/tumbler.c:986
[   33.752872] Modules linked in: snd_powermac snd_pcm snd_page_alloc rtc_generic snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd pcmcia soundcore apm_emu apm_emulation michael_mic yenta_socket pcmcia_rsrc uio_pdrv_genirq pcmcia_core uio uninorth_agp airport orinoco cfg80211 usb_storage firewire_ohci sungem firewire_core sungem_phy crc_itu_t
[   33.752957] CPU: 0 PID: 23 Comm: kworker/0:1 Not tainted 3.13.0-32-powerpc-smp #57-Ubuntu
[   33.752990] Workqueue: events device_change_handler [snd_powermac]
[   33.752997] task: df92dfa0 ti: df98a000 task.ti: df98a000
[   33.753003] NIP: e2d4ee30 LR: c005e1fc CTR: e2d4edf0
[   33.753008] REGS: df98bdc0 TRAP: 0700   Not tainted  (3.13.0-32-powerpc-smp)
[   33.753012] MSR: 00029032 <EE,ME,IR,DR,RI>  CR: 42002028  XER: 00000000
[   33.753031] 
[   33.753031] GPR00: c005e1fc df98be70 df92dfa0 e2d547a0 00000000 0000020e 00000000 00665000 
[   33.753031] GPR08: e2d547a4 00000001 00000001 00001032 42002022 00000000 c0065ec8 df97b180 
[   33.753031] GPR16: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 c1050340 
[   33.753031] GPR24: c0a40000 00000001 00000000 c1053400 c1050140 00000000 c4cb9800 00000000 
[   33.753103] NIP [e2d4ee30] device_change_handler+0x40/0x290 [snd_powermac]
[   33.753121] LR [c005e1fc] process_one_work+0x158/0x3cc
[   33.753125] Call Trace:
[   33.753137] [df98be70] [00000001] 0x1 (unreliable)
[   33.753147] [df98be90] [c005e1fc] process_one_work+0x158/0x3cc
[   33.753156] [df98bec0] [c005eb90] worker_thread+0x134/0x3fc
[   33.753167] [df98bef0] [c0065f9c] kthread+0xd4/0xe8
[   33.753177] [df98bf40] [c0017640] ret_from_kernel_thread+0x5c/0x64
[   33.753182] Instruction dump:
[   33.753189] 7c0802a6 7d800026 90010024 bf810010 9181000c 3d20e2d5 83c947b0 2f9e0000 
[   33.753207] 419e0244 83fe0178 7fe90034 5529d97e <0f090000> 2f890000 409e022c 813f003c 
[   33.753227] ---[ end trace 65e4ac2ec1be6e5c ]---
[   33.918234] lp: driver loaded but no devices found
[   34.018153] ppdev: user-space parallel port driver
[   35.574971] Bluetooth: Core ver 2.17
[   35.580400] NET: Registered protocol family 31
[   35.580417] Bluetooth: HCI device and connection manager initialized
[   35.580451] Bluetooth: HCI socket layer initialized
[   35.580460] Bluetooth: L2CAP socket layer initialized
[   35.580503] Bluetooth: SCO socket layer initialized
[   35.649778] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.649796] Bluetooth: BNEP filters: protocol multicast
[   35.649827] Bluetooth: BNEP socket layer initialized
[   35.790373] Bluetooth: RFCOMM TTY layer initialized
[   35.790421] Bluetooth: RFCOMM socket layer initialized
[   35.790456] Bluetooth: RFCOMM ver 1.11
[   36.060028] type=1400 audit(1486988942.045:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=539 comm="apparmor_parser"
[   36.060066] type=1400 audit(1486988942.045:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=539 comm="apparmor_parser"
[   36.061524] type=1400 audit(1486988942.045:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=539 comm="apparmor_parser"
[   36.391172] init: cups main process (542) killed by HUP signal
[   36.391252] init: cups main process ended, respawning
[   38.202071] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[   38.343411] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x80ffffff:
[   38.343436]  excluding 0x80000000-0x800fffff
[   38.412119] init: failsafe main process (583) killed by TERM signal
[   41.527439] type=1400 audit(1486988947.513:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=803 comm="apparmor_parser"
[   41.527478] type=1400 audit(1486988947.513:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=803 comm="apparmor_parser"
[   41.528364] type=1400 audit(1486988947.513:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=803 comm="apparmor_parser"
[   41.644457] type=1400 audit(1486988947.629:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=810 comm="apparmor_parser"
[   41.644498] type=1400 audit(1486988947.629:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=810 comm="apparmor_parser"
[   41.644518] type=1400 audit(1486988947.629:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=810 comm="apparmor_parser"
[   41.645960] type=1400 audit(1486988947.629:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=810 comm="apparmor_parser"
[   41.645991] type=1400 audit(1486988947.629:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=810 comm="apparmor_parser"
[   41.658179] type=1400 audit(1486988947.641:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=810 comm="apparmor_parser"
[   41.954192] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   41.961150] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.084973] type=1400 audit(1486988948.069:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=811 comm="apparmor_parser"
[   42.130683] eth1: New link status: Connected (0001)
[   42.215203] sungem_phy: PHY ID: 2060e1, addr: 0
[   42.215450] gem 0002:24:0f.0 eth0: Found BCM5421 PHY
[   42.215937] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.216000] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   42.218470] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.251264] input: Mouseemu virtual keyboard as /devices/virtual/input/input5
[   47.252306] input: Mouseemu virtual mouse as /devices/virtual/input/input6
[   48.404178] init: plymouth-upstart-bridge main process ended, respawning
[   66.656971] audit_printk_skb: 81 callbacks suppressed
[   66.656990] type=1400 audit(1486988972.641:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1296 comm="apparmor_parser"
[   66.657024] type=1400 audit(1486988972.641:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1296 comm="apparmor_parser"
[   66.658458] type=1400 audit(1486988972.641:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1296 comm="apparmor_parser"
[  107.373869] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  179.799610] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  186.108578] gksudo[1723]: unhandled signal 11 at 20000000 nip 0f4ef780 lr 0f4ef778 code 30001



```

one more thing... the networks show up on the list, but it just doesn't connect.

for [COLOR=#000000]wildmanne39
[/COLOR]```


########## wireless info START ##########


Report from: 13 Feb 2017 08:01 EST -0500


Booted last: 13 Feb 2017 07:53 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-32-powerpc-smp #57-Ubuntu SMP Tue Jul 15 03:50:44 UTC 2014 ppc ppc ppc GNU/Linux


, ro, quiet, splash, 


##### desktop ###########################


Lubuntu


##### lspci #############################


0002:24:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth GMAC (Sun GEM) [106b:0021] (rev 01)
    Kernel driver in use: gem


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5581 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


airport                 3654  0 
orinoco                73356  1 airport
cfg80211              424569  1 orinoco


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF2]>  
          inet6 addr: fe80::<IP6 'eth1' [IF2]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5449 (5.4 KB)
          Interrupt:57 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=19/70  Signal level=-83 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root       690     1  0 07:53 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airport
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth1' [IF2]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes


  Wireless Access Points 
    Bougie:          Infra, <MAC 'Bougie' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    wilds-public-meetinghall: Infra, <MAC 'wilds-public-meetinghall' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35
    wilds-public-campbell: Infra, <MAC 'wilds-public-campbell' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/wilds-public-campbell]] (600 root)
[connection] id=wilds-public-campbell | type=802-11-wireless
[802-11-wireless] ssid=wilds-public-campbell
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/wilds-public-meetinghall]] (600 root)
[connection] id=wilds-public-meetinghall | type=802-11-wireless
[802-11-wireless] ssid=wilds-public-meetinghall | mac-address=<MAC 'eth1' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)


eth1      Scan completed :
          Cell 01 - Address: <MAC 'Bougie' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Bougie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e2268ce1a
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'wilds-public-meetinghall' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"wilds-public-meetinghall"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000bd074ce6e35
                    Extra: Last beacon: 172ms ago
          Cell 03 - Address: <MAC 'wilds-public-campbell' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"wilds-public-campbell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006b0e0f62470
                    Extra: Last beacon: 232ms ago


##### module infos ######################


[airport]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/drivers/net/wireless/orinoco/airport.ko
license:        Dual MPL/GPL
description:    Driver for the Apple Airport wireless card.
author:         Benjamin Herrenschmidt <benh@kernel.crashing.org>
srcversion:     D1188A8250EBB457A04CEA6
depends:        orinoco
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512


[cfg80211]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     76D086E780971FB64CB6049
depends:        
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


airport
apm_emu
snd-powermac


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist.local.conf]
blacklist snd-aoa-codec-tas
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-i2sbus
blacklist snd-aoa-soundbus
blacklist snd-aoa


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x106b:0x0021 (gem)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x106b:0x0022 (airport)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[   38.724578] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   38.945320] eth1: New link status: Connected (0001)
[   38.991446] gem 0002:24:0f.0 eth0: Found BCM5421 PHY
[   38.991955] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.992019] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   38.994459] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


########## wireless info END ############



```[COLOR=#000000]
[/COLOR]

---

### Post by rican-linux on 2017-02-09
weird that the kernel identifies your wireless as eth1 instead of wlan0. Try running this command nmtui-connect. A ncurses interface should appear and list your available networks. See if you can join this way.

---

### Post by jake82 on 2017-02-09
i can try... i'm having some problems installing network-manager-tui but i'll get it

do you think linux-mint would be better on this laptop or even xubuntu? i've only run ubuntu and lubuntu so i'm not sure how light the other ones are

i've been looking into it though and i think Xubuntu might run better on it because the minimum requirements are lower

---

### Post by rican-linux on 2017-02-09
Xubuntu last PPC is 10.04 and MintPPC is no longer supported as well. Lubuntu and Ubuntu-MATE will no longer make PPC so 16.04 is the last LTS release.

---

### Post by wildmanne39 on 2017-02-09
First your link quality is 19 if it gets below 50 and that is low then it will not connect or your speed will be very slow.

I am not sure that your wifi device is supported well anymore in ubuntu, we almost never see that driver but a few months ago I believe I saw one that was working.

How far are you from your router? what is your network name?

Please do:
```
sudo dpkg-reconfigure resolv.conf
```
does that help? if not post another wireless file from the script.

---

### Post by jake82 on 2017-02-09
sudo dpkg-reconfigure resolv.conf says that resolv.conf is not installed. i just moved closer to my router and the signal is much better but its still not connecting

---

### Post by jake82 on 2017-02-09
my wifi ssid is "Bougie" 
```


########## wireless info START ##########


Report from: 15 Feb 2017 20:15 EST -0500


Booted last: 15 Feb 2017 19:50 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-powerpc-smp #57-Ubuntu SMP Tue Jul 15 03:50:44 UTC 2014 ppc ppc ppc GNU/Linux


, ro, quiet, splash, 


##### desktop ###########################


Lubuntu


##### lspci #############################


0002:24:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth GMAC (Sun GEM) [106b:0021] (rev 01)
	Kernel driver in use: gem


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


b43                   375240  0 
bcma                   44450  1 b43
mac80211              571192  1 b43
ssb                    57500  1 b43
airport                 3654  0 
orinoco                73356  1 airport
cfg80211              424569  3 b43,mac80211,orinoco


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager
	Wicd


Running:


root       776     1  0 19:50 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airport
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth1' [IF2]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes


  Wireless Access Points 
    wilds-public-campbell: Infra, <MAC 'wilds-public-campbell' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32
    wilds-public-meetinghall: Infra, <MAC 'wilds-public-meetinghall' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25
    Bougie:          Infra, <MAC 'Bougie' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/wilds-public-campbell]] (600 root)
[connection] id=wilds-public-campbell | type=802-11-wireless
[802-11-wireless] ssid=wilds-public-campbell
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/wilds-public-meetinghall]] (600 root)
[connection] id=wilds-public-meetinghall | type=802-11-wireless
[802-11-wireless] ssid=wilds-public-meetinghall | mac-address=<MAC 'eth1' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Bougie]] (600 root)
[connection] id=Bougie | type=802-11-wireless
[802-11-wireless] ssid=Bougie | mac-address=<MAC 'eth1' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)


eth1      Scan completed :
          Cell 01 - Address: <MAC 'wilds-public-campbell' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"wilds-public-campbell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006c1d69a3952
                    Extra: Last beacon: 244ms ago
          Cell 02 - Address: <MAC 'Bougie' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"Bougie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000005c17add4
                    Extra: Last beacon: 192ms ago
          Cell 03 - Address: <MAC 'wilds-public-meetinghall' [AC3]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"wilds-public-meetinghall"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000be16a6fa5e3
                    Extra: Last beacon: 160ms ago


##### module infos ######################


[b43]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     DBE2BA42E7E3AD9B00CCA2E
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[bcma]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     1D811BE4D53D78885E5638B
depends:        
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1D88DA8AA3488134CA34833
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ssb]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3188E13D66C5770F3BCBE8C
depends:        
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512


[airport]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/drivers/net/wireless/orinoco/airport.ko
license:        Dual MPL/GPL
description:    Driver for the Apple Airport wireless card.
author:         Benjamin Herrenschmidt <benh@kernel.crashing.org>
srcversion:     D1188A8250EBB457A04CEA6
depends:        orinoco
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512


[cfg80211]
filename:       /lib/modules/3.13.0-32-powerpc-smp/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     76D086E780971FB64CB6049
depends:        
intree:         Y
vermagic:       3.13.0-32-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        91:A3:22:78:42:F4:96:7F:8C:0D:33:83:86:2A:F8:B9:7B:D3:43:C1
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


airport
apm_emu
snd-powermac


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist.local.conf]
blacklist snd-aoa-codec-tas
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-i2sbus
blacklist snd-aoa-soundbus
blacklist snd-aoa


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x106b:0x0021 (gem)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x106b:0x0022 (airport)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[   38.378519] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   38.495046] gem 0002:24:0f.0 eth0: Found BCM5421 PHY
[   38.495637] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[  106.582434] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[  107.210979] gem 0002:24:0f.0 eth0: Found BCM5421 PHY
[  107.212029] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  108.238452] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[  111.109289] eth1: Lucent/Agere firmware doesn't support manual roaming
[  135.871477] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  152.865683] eth1: Lucent/Agere firmware doesn't support manual roaming (repeated 5 times)


########## wireless info END ############
```

---

### Post by rsavage on 2017-02-10
Sigh, nothing changes around here, does it?  You have an airport classic card, forget any b43 nonsense.  [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

---

### Post by este.el.paz on 2017-02-10
@rsavage:  Does seem like a time warp of some kind . . . .  : - )

@OP:

I would add that 14.04 was a "troubled" distro for PPC . . . but 16.04 was more "untroubled" . . . especially if you boot the DVD using alt/option and selecting "EFI boot" . . . then see how the internet side measures up . . . it should at least "find" your ethernet connection.  I'm not reading through all the posts to figure out how you are doing an "internet install" without having an ethernet connection, just suggesting that you try 16.04.  Or, roll back to 12.04, which was a good distro for PPC, although there was the need for adding the wifi packages . . . .  Ubuntu-MATE 16.04 for PPC is pretty good.

e.e.p.

---

