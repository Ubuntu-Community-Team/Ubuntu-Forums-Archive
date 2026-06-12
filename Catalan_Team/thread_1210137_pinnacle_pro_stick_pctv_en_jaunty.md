---
title: "pinnacle pro stick pctv en jaunty"
date: 2009-07-11
forum: Catalan Team
---

### Post by venusfenix on 2009-07-11
buenas,

tinc un acer de sobretaula un intel core 2 quad q6600 amb jaunty jackalope.
vull installar un stick pinnacle pro pctv (2xtdt) pero no se com fer-ho.

tincs el drivers de windows, i no trobo els de linux.

com puc procedir??

merci.

---

### Post by PatrickVogeli on 2009-07-11
Si es USB, enganxa el resultat de fer lsusb, si es pci, lspci.

Salut

---

### Post by venusfenix on 2009-07-11
lsusb
Bus 001 Device 002: ID 2304:022c Pinnacle Systems, Inc. [hex] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 003 Device 002: ID 056a:0060 Wacom Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Aqui tens el resultat

---

### Post by PatrickVogeli on 2009-07-11
[http://www.mail-archive.com/linux-dvb@linuxtv.org/msg22884/dvb-usb-dib0700-01.fw](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg22884/dvb-usb-dib0700-01.fw)

Baixat aquest arxiu i el copies a /lib/firmware, reinicia el pc, connecta l'usb i a vuere si funciona, jo feia servir el kaffeine per la tdt i anava molt be.

Si no va, enganxan's el resultat de fer dmesg.

salut

---

### Post by venusfenix on 2009-07-13
buenas,

gracies per l'ajuda,
nomes dir que no ha funcionat, vaig instalar el kafeine i es va passar tota la nit escanejant els canals i res.

si puc, aquesta nit, enganxo el resultat de dmesg

merci!!

---

### Post by PatrickVogeli on 2009-07-13
una pregunta, no estaras fent servir l'anteneta aquella petita que ve amb l'aparell, no?

Algun cop has captat alguna cosa amb aquesta anteneta? jo provaria a endollar-ho a un punt de tv de casa.

Salut

---

### Post by venusfenix on 2009-07-13
si, son 2 antenetes, pero amb windows vista y el centro multimedia, puc mira tots el canals sense probleme, amb ubuntu, ha de ser el mateix.
no?

gracies,

---

### Post by venusfenix on 2009-07-13
continua sense funcionar.

Tambe, per si et dona alguna pista, quan entro, en diu que si vull veure el differents modes de video. es normal?

et deixo el resultat de dmesg:


dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fff0000 (usable)
[    0.000000]  BIOS-e820: 000000006fff0000 - 000000006fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fff3000 - 0000000070000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x6fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fff0000 (usable)
[    0.000000]  modified: 000000006fff0000 - 000000006fff3000 (ACPI NVS)
[    0.000000]  modified: 000000006fff3000 - 0000000070000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef38c
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb238c
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef38b to 00881000 - 00fb238b
[    0.000000] ACPI: RSDP 000F8180, 0014 (r0 ACRSYS)
[    0.000000] ACPI: RSDT 6FFF3040, 0040 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 6FFF30C0, 0074 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 6FFF3180, 48AE (r1 ACRSYS AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FFF0000, 0040
[    0.000000] ACPI: HPET 6FFF7B80, 0038 (r1 ACRSYS ACRPRDCT 42302E31 AWRD       98)
[    0.000000] ACPI: SLIC 6FFF7C00, 0176 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: MCFG 6FFF7DC0, 003C (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 6FFF7A80, 0084 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 6FFF7E40, 0175 (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    0.000000] ACPI: SSDT 6FFF84C0, 02F9 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 907MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb238c]      NEW RAMDISK ==> [0000881000 - 0000fb238c]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f4030] 000f4030
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0006fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006fff0
[    0.000000] On node 0 totalpages: 458623
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1816 pages used for memmap
[    0.000000]   HighMem zone: 230618 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 70000000:70000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 455039
[    0.000000] Kernel command line: root=UUID=f30a5604-539f-47b6-9443-b3236ed246a6 ro splash vga=795 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2399.715 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9174400 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1794244k/1834944k available (4126k kernel code, 39372k reserved, 2208k data, 532k init, 929736k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.43 BogoMIPS (lpj=9598860)
[    0.004094] Security Framework initialized
[    0.004136] SELinux:  Disabled at boot.
[    0.004181] AppArmor: AppArmor initialized
[    0.004222] Mount-cache hash table entries: 512
[    0.004384] Initializing cgroup subsys ns
[    0.004422] Initializing cgroup subsys cpuacct
[    0.004458] Initializing cgroup subsys memory
[    0.004495] Initializing cgroup subsys freezer
[    0.004543] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004607] CPU: L2 cache: 4096K
[    0.004643] CPU: Physical Processor ID: 0
[    0.004678] CPU: Processor Core ID: 0
[    0.004715] using mwait in idle threads.
[    0.004760] Checking 'hlt' instruction... OK.
[    0.022135] ACPI: Core revision 20080926
[    0.023937] ACPI: Checking initramfs for custom DSDT
[    0.272409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.314944] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.316001] Booting processor 1 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4800.21 BogoMIPS (lpj=9600426)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.400607] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.401613] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.404094] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4800.21 BogoMIPS (lpj=9600432)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.496632] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.496937] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.500091] Booting processor 3 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4800.19 BogoMIPS (lpj=9600389)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.592556] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.592878] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.596033] Brought up 4 CPUs
[    0.596070] Total of 4 processors activated (19200.05 BogoMIPS).
[    0.596149] CPU0 attaching sched-domain:
[    0.596152]  domain 0: span 0,3 level MC
[    0.596154]   groups: 0 3
[    0.596158]   domain 1: span 0-3 level CPU
[    0.596160]    groups: 0,3 1-2
[    0.596164] CPU1 attaching sched-domain:
[    0.596166]  domain 0: span 1-2 level MC
[    0.596167]   groups: 1 2
[    0.596170]   domain 1: span 0-3 level CPU
[    0.596172]    groups: 1-2 0,3
[    0.596176] CPU2 attaching sched-domain:
[    0.596178]  domain 0: span 1-2 level MC
[    0.596179]   groups: 2 1
[    0.596182]   domain 1: span 0-3 level CPU
[    0.596184]    groups: 1-2 0,3
[    0.596188] CPU3 attaching sched-domain:
[    0.596189]  domain 0: span 0,3 level MC
[    0.596191]   groups: 3 0
[    0.596194]   domain 1: span 0-3 level CPU
[    0.596195]    groups: 0,3 1-2
[    0.596318] net_namespace: 776 bytes
[    0.596318] Booting paravirtualized kernel on bare hardware
[    0.596374] Time: 20:19:53  Date: 07/13/09
[    0.596374] regulator: core version 0.5
[    0.596374] NET: Registered protocol family 16
[    0.596374] EISA bus registered
[    0.596374] ACPI: bus type pci registered
[    0.596389] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.596426] PCI: MCFG area at e0000000 reserved in E820
[    0.596462] PCI: Using MMCONFIG for extended config space
[    0.596498] PCI: Using configuration type 1 for base access
[    0.597245] ACPI: EC: Look up EC in DSDT
[    0.605762] ACPI: Interpreter enabled
[    0.605804] ACPI: (supports S0 S3 S4 S5)
[    0.605970] ACPI: Using IOAPIC for interrupt routing
[    0.610317] ACPI: No dock devices found.
[    0.610359] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.610496] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.610534] pci 0000:00:06.0: PME# disabled
[    0.610623] pci 0000:00:12.0: reg 10 io port: [0xff00-0xff07]
[    0.610630] pci 0000:00:12.0: reg 14 io port: [0xfe00-0xfe03]
[    0.610638] pci 0000:00:12.0: reg 18 io port: [0xfd00-0xfd07]
[    0.610645] pci 0000:00:12.0: reg 1c io port: [0xfc00-0xfc03]
[    0.610652] pci 0000:00:12.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.610659] pci 0000:00:12.0: reg 24 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.610680] pci 0000:00:12.0: set SATA to AHCI mode
[    0.610745] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdffe000-0xfdffefff]
[    0.610804] pci 0000:00:13.1: reg 10 32bit mmio: [0xfdffd000-0xfdffdfff]
[    0.610864] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdffc000-0xfdffcfff]
[    0.610923] pci 0000:00:13.3: reg 10 32bit mmio: [0xfdffb000-0xfdffbfff]
[    0.610982] pci 0000:00:13.4: reg 10 32bit mmio: [0xfdffa000-0xfdffafff]
[    0.611063] pci 0000:00:13.5: reg 10 32bit mmio: [0xfdff9000-0xfdff90ff]
[    0.611107] pci 0000:00:13.5: supports D1 D2
[    0.611109] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.611148] pci 0000:00:13.5: PME# disabled
[    0.611217] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.611275] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.611282] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.611289] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.611296] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.611303] pci 0000:00:14.1: reg 20 io port: [0xf900-0xf90f]
[    0.611360] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    0.611399] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.611438] pci 0000:00:14.2: PME# disabled
[    0.611610] pci 0000:01:05.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.611616] pci 0000:01:05.0: reg 18 64bit mmio: [0xfdde0000-0xfddeffff]
[    0.611620] pci 0000:01:05.0: reg 20 io port: [0xde00-0xdeff]
[    0.611630] pci 0000:01:05.0: supports D1 D2
[    0.611655] pci 0000:01:05.2: reg 10 64bit mmio: [0xfddfc000-0xfddfffff]
[    0.611695] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.611698] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.611702] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.611754] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdcfc000-0xfdcfffff]
[    0.611761] pci 0000:02:00.0: reg 18 io port: [0xee00-0xeeff]
[    0.611784] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.611794] pci 0000:02:00.0: supports D1 D2
[    0.611795] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.611835] pci 0000:02:00.0: PME# disabled
[    0.611925] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
[    0.611928] pci 0000:00:06.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.611932] pci 0000:00:06.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.611984] pci 0000:03:02.0: reg 10 32bit mmio: [0xfdbff000-0xfdbff7ff]
[    0.611993] pci 0000:03:02.0: reg 14 32bit mmio: [0xfdbf8000-0xfdbfbfff]
[    0.612053] pci 0000:03:02.0: supports D1 D2
[    0.612054] pci 0000:03:02.0: PME# supported from D0 D1 D2 D3hot
[    0.612094] pci 0000:03:02.0: PME# disabled
[    0.612189] pci 0000:00:14.4: transparent bridge
[    0.612227] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]
[    0.612232] pci 0000:00:14.4: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.612237] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
[    0.612250] bus 00 -> node 0
[    0.612256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.612540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.612676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.612764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.627612] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628080] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628538] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628996] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.629452] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.629909] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.630366] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.630834] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.631421] ACPI: WMI: Mapper loaded
[    0.631490] SCSI subsystem initialized
[    0.631490] libata version 3.00 loaded.
[    0.631490] usbcore: registered new interface driver usbfs
[    0.631490] usbcore: registered new interface driver hub
[    0.631490] usbcore: registered new device driver usb
[    0.632059] PCI: Using ACPI for IRQ routing
[    0.636014] Bluetooth: Core ver 2.13
[    0.636068] NET: Registered protocol family 31
[    0.636068] Bluetooth: HCI device and connection manager initialized
[    0.636104] Bluetooth: HCI socket layer initialized
[    0.636140] NET: Registered protocol family 8
[    0.636175] NET: Registered protocol family 20
[    0.636218] NetLabel: Initializing
[    0.636252] NetLabel:  domain hash size = 128
[    0.636287] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.636331] NetLabel:  unlabeled traffic allowed by default
[    0.636395] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.636577] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.648065] AppArmor: AppArmor Filesystem Enabled
[    0.652011] Switched to high resolution mode on CPU 0
[    0.652987] Switched to high resolution mode on CPU 3
[    0.653975] Switched to high resolution mode on CPU 2
[    0.654675] Switched to high resolution mode on CPU 1
[    0.655827] pnp: PnP ACPI init
[    0.655872] ACPI: bus type pnp registered
[    0.658593] pnp: PnP ACPI: found 14 devices
[    0.658630] ACPI: ACPI bus type pnp unregistered
[    0.658666] PnPBIOS: Disabled by ACPI PNP
[    0.658707] system 00:01: ioport range 0x4100-0x411f has been reserved
[    0.658744] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.658780] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.658817] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.658854] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.658890] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.658926] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.658963] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.658999] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.659036] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[    0.659073] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[    0.659109] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.659146] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.659182] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.659219] system 00:01: ioport range 0xb10-0xb1f has been reserved
[    0.659260] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.659297] system 00:07: ioport range 0x800-0x805 has been reserved
[    0.659333] system 00:07: ioport range 0x880-0x88f has been reserved
[    0.659374] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.659414] system 00:0d: iomem range 0xf0000-0xfffff could not be reserved
[    0.659451] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.659488] system 00:0d: iomem range 0x6fff0000-0x6fffffff could not be reserved
[    0.659529] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.659566] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.659603] system 00:0d: iomem range 0x100000-0x6ffeffff could not be reserved
[    0.659643] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.659680] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.659718] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.694414] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.694451] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.694489] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.694526] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.694570] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.694606] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.694643] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.694680] pci 0000:00:06.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.694723] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.694760] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.694800] pci 0000:00:14.4:   MEM window: 0xfdb00000-0xfdbfffff
[    0.694838] pci 0000:00:14.4:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.694891] pci 0000:00:06.0: setting latency timer to 64
[    0.694899] bus: 00 index 0 io port: [0x00-0xffff]
[    0.694935] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.694970] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.695006] bus: 01 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.695042] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.695077] bus: 01 index 3 mmio: [0x0-0x0]
[    0.695113] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.695148] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.695184] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.695220] bus: 02 index 3 mmio: [0x0-0x0]
[    0.695255] bus: 03 index 0 io port: [0xc000-0xcfff]
[    0.695291] bus: 03 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.695326] bus: 03 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.695362] bus: 03 index 3 io port: [0x00-0xffff]
[    0.695397] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.695438] NET: Registered protocol family 2
[    0.708084] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.708323] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.708678] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.708879] TCP: Hash tables configured (established 131072 bind 65536)
[    0.708916] TCP reno registered
[    0.712113] NET: Registered protocol family 1
[    0.712249] checking if image is initramfs... it is
[    1.211606] Freeing initrd memory: 7364k freed
[    1.212049] cpufreq: No nForce2 chipset.
[    1.212222] audit: initializing netlink socket (disabled)
[    1.212285] type=2000 audit(1247516393.212:1): initialized
[    1.218324] highmem bounce pool size: 64 pages
[    1.218362] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.219614] VFS: Disk quotas dquot_6.5.1
[    1.219719] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.220313] fuse init (API version 7.10)
[    1.220416] msgmni has been set to 1704
[    1.220665] alg: No test for stdrng (krng)
[    1.220715] io scheduler noop registered
[    1.220756] io scheduler anticipatory registered
[    1.220794] io scheduler deadline registered
[    1.220851] io scheduler cfq registered (default)
[    2.048020] pci 0000:00:13.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    2.132058] pci 0000:01:05.0: Boot video device
[    2.134498] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.134526] pcieport-driver 0000:00:06.0: found MSI capability
[    2.134585] pcieport-driver 0000:00:06.0: irq 2303 for MSI/MSI-X
[    2.134594] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.134606] pci_express 0000:00:06.0:pcie03: allocate port service
[    2.134656] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.134698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.134857] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.135600] ACPI: Power Button (FF) [PWRF]
[    2.135668] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.135709] ACPI: Power Button (CM) [PWRB]
[    2.135784] fan PNP0C0B:00: registered as cooling_device0
[    2.135823] ACPI: Fan [FAN] (on)
[    2.136084] processor ACPI_CPU:00: registered as cooling_device1
[    2.136122] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.136403] ACPI: SSDT 6FFF8250, 00CE (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    2.136735] processor ACPI_CPU:01: registered as cooling_device2
[    2.136784] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.137122] ACPI: SSDT 6FFF8320, 00CE (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[    2.137426] processor ACPI_CPU:02: registered as cooling_device3
[    2.137464] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.137761] ACPI: SSDT 6FFF83F0, 00CE (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[    2.138079] processor ACPI_CPU:03: registered as cooling_device4
[    2.138119] ACPI: Processor [CPU3] (supports 8 throttling states)
[    2.140211] thermal LNXTHERM:01: registered as thermal_zone0
[    2.140486] ACPI: Thermal Zone [THRM] (40 C)
[    2.140568] isapnp: Scanning for PnP cards...
[    2.494394] isapnp: No Plug & Play device found
[    2.501736] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.501878] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.502277] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.502956] brd: module loaded
[    2.503241] loop: module loaded
[    2.503329] Fixed MDIO Bus: probed
[    2.503367] PPP generic driver version 2.4.2
[    2.503447] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.503509] Driver 'sd' needs updating - please use bus_type methods
[    2.503551] Driver 'sr' needs updating - please use bus_type methods
[    2.503614] ahci 0000:00:12.0: version 3.0
[    2.503630] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.503694] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    2.503827] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.503871] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    2.504308] scsi0 : ahci
[    2.504444] scsi1 : ahci
[    2.504554] scsi2 : ahci
[    2.504678] scsi3 : ahci
[    2.504796] ata1: SATA max UDMA/133 irq_stat 0x00400000 irq 22, PHY RDY changed
[    2.504837] ata2: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff180 irq 22
[    2.504878] ata3: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff200 irq 22
[    2.504920] ata4: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff280 irq 22
[    3.392033] ata1: softreset failed (device not ready)
[    3.392076] ata1: failed due to HW bug, retry pmp=0
[    3.556036] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.556634] ata1.00: ATA-7: ST3250310AS, 3.AAD, max UDMA/133
[    3.556678] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.556730] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.557478] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.557522] ata1.00: configured for UDMA/133
[    3.892036] ata2: SATA link down (SStatus 0 SControl 300)
[    4.392033] ata3: softreset failed (device not ready)
[    4.392073] ata3: failed due to HW bug, retry pmp=0
[    4.556053] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.558809] ata3.00: ATAPI: HL-DT-ST DVDRAM_GSA-H60N, CA01, max UDMA/100
[    4.558878] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.562753] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.562793] ata3.00: configured for UDMA/100
[    5.008038] ata4: SATA link down (SStatus 0 SControl 300)
[    5.024150] scsi 0:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    5.024264] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    5.024316] sd 0:0:0:0: [sda] Write Protect is off
[    5.024352] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.024372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.024460] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    5.024510] sd 0:0:0:0: [sda] Write Protect is off
[    5.024546] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.024565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.024608]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    5.069221] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.069289] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.072147] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM_GSA-H60N  CA01 PQ: 0 ANSI: 5
[    5.399095] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.399142] Uniform CD-ROM driver Revision: 3.20
[    5.399253] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    5.399283] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    5.399521] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.399682] scsi4 : pata_atiixp
[    5.399797] scsi5 : pata_atiixp
[    5.400783] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    5.400820] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    5.720456] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.720509] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.720556] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    5.720638] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    5.720702] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    5.720760] ehci_hcd 0000:00:13.5: debug port 1
[    5.720810] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfdff9000
[    5.732025] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    5.732145] usb usb1: configuration #1 chosen from 1 choice
[    5.732201] hub 1-0:1.0: USB hub found
[    5.732242] hub 1-0:1.0: 10 ports detected
[    5.732381] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.732426] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.732470] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.732535] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    5.732592] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfdffe000
[    5.792051] usb usb2: configuration #1 chosen from 1 choice
[    5.792108] hub 2-0:1.0: USB hub found
[    5.792150] hub 2-0:1.0: 2 ports detected
[    5.792252] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.792296] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.792362] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.792418] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfdffd000
[    5.852048] usb usb3: configuration #1 chosen from 1 choice
[    5.852102] hub 3-0:1.0: USB hub found
[    5.852144] hub 3-0:1.0: 2 ports detected
[    5.852245] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.852290] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    5.852356] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    5.852414] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfdffc000
[    5.912051] usb usb4: configuration #1 chosen from 1 choice
[    5.912105] hub 4-0:1.0: USB hub found
[    5.912147] hub 4-0:1.0: 2 ports detected
[    5.912249] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.912293] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    5.912359] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    5.912409] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfdffb000
[    5.972049] usb usb5: configuration #1 chosen from 1 choice
[    5.972106] hub 5-0:1.0: USB hub found
[    5.972151] hub 5-0:1.0: 2 ports detected
[    5.972251] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.972296] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    5.972367] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    5.972420] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfdffa000
[    6.032051] usb usb6: configuration #1 chosen from 1 choice
[    6.032105] hub 6-0:1.0: USB hub found
[    6.032149] hub 6-0:1.0: 2 ports detected
[    6.032253] uhci_hcd: USB Universal Host Controller Interface driver
[    6.032343] usbcore: registered new interface driver libusual
[    6.032403] usbcore: registered new interface driver usbserial
[    6.032446] USB Serial support registered for generic
[    6.044060] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.176917] usb 1-1: configuration #1 chosen from 1 choice
[    6.664026] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    6.833245] usb 3-1: configuration #1 chosen from 1 choice
[    7.096075] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    7.265312] usb 3-2: configuration #1 chosen from 1 choice
[    7.528036] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    7.697357] usb 6-2: configuration #1 chosen from 1 choice
[    7.699493] usbcore: registered new interface driver usbserial_generic
[    7.699534] usbserial: USB Serial Driver core
[    7.699609] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    7.699646] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    7.699751] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.704066] mice: PS/2 mouse device common for all mice
[    7.708161] rtc_cmos 00:04: RTC can wake from S4
[    7.708229] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    7.708289] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    7.708371] device-mapper: uevent: version 1.0.3
[    7.708516] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    7.709442] device-mapper: multipath: version 1.0.5 loaded
[    7.709487] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.709624] EISA: Probing bus 0 at eisa.0
[    7.709675] Cannot allocate resource for EISA slot 4
[    7.709725] EISA: Detected 0 cards.
[    7.709889] cpuidle: using governor ladder
[    7.709933] cpuidle: using governor menu
[    7.710373] TCP cubic registered
[    7.710486] NET: Registered protocol family 10
[    7.710884] lo: Disabled Privacy Extensions
[    7.711176] NET: Registered protocol family 17
[    7.711224] Bluetooth: L2CAP ver 2.11
[    7.711259] Bluetooth: L2CAP socket layer initialized
[    7.711296] Bluetooth: SCO (Voice Link) ver 0.6
[    7.711331] Bluetooth: SCO socket layer initialized
[    7.711423] Bluetooth: RFCOMM socket layer initialized
[    7.711471] Bluetooth: RFCOMM TTY layer initialized
[    7.711507] Bluetooth: RFCOMM ver 1.10
[    7.712286] Using IPI No-Shortcut mode
[    7.712375] registered taskstats version 1
[    7.712510]   Magic number: 1:376:346
[    7.712558] tty tty63: hash matches
[    7.712649] rtc_cmos 00:04: setting system clock to 2009-07-13 20:20:00 UTC (1247516400)
[    7.712696] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.712736] EDD information not available.
[    7.713098] Freeing unused kernel memory: 532k freed
[    7.713254] Write protecting the kernel text: 4128k
[    7.713337] Write protecting the kernel read-only data: 1532k
[    7.737155] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    7.851783] Floppy drive(s): fd0 is 1.44M
[    7.863780] sky2 driver version 1.22
[    7.863827] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.863838] sky2 0000:02:00.0: setting latency timer to 64
[    7.863893] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
[    7.878343] usbcore: registered new interface driver hiddev
[    7.882598] input: Justcom Technology USB KVM Switch as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input4
[    7.895868] sky2 0000:02:00.0: Marvell Yukon 88E8056 Gigabit Ethernet Controller
[    7.895871]  Part Number: Yukon 88E8056
[    7.895872]  Engineering Level: Rev. 1.2
[    7.895873]  Manufacturer: Marvell
[    7.895983] sky2 0000:02:00.0: irq 2302 for MSI/MSI-X
[    7.896705] sky2 eth0: addr 00:1d:92:3e:74:f1
[    7.900167] FDC 0 is a post-1991 82077
[    7.906634] ohci1394 0000:03:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.956400] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.969974] generic-usb 0003:06F2:0011.0001: input,hidraw0: USB HID v1.10 Keyboard [Justcom Technology USB KVM Switch] on usb-0000:00:13.1-2/input0
[    7.974206] input: Justcom Technology USB KVM Switch as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input5
[    7.993624] generic-usb 0003:06F2:0011.0002: input,hidraw1: USB HID v1.10 Mouse [Justcom Technology USB KVM Switch] on usb-0000:00:13.1-2/input1
[    7.993655] usbcore: registered new interface driver usbhid
[    7.993664] usbhid: v2.6:USB HID core driver
[    8.249311] PM: Starting manual resume from disk
[    8.249315] PM: Resume from partition 8:6
[    8.249316] PM: Checking hibernation image.
[    8.249458] PM: Resume from disk failed.
[    8.275442] kjournald starting.  Commit interval 5 seconds
[    8.275449] EXT3-fs: mounted filesystem with ordered data mode.
[    9.240404] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00013c305b]
[   11.907410] udev: starting version 141
[   12.063635] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.063692] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.102074] Linux agpgart interface v0.103
[   12.214478] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.245080] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.254102] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.268211] input: Wacom Volito as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input7
[   12.303072] usbcore: registered new interface driver wacom
[   12.303103] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[   12.345672] ppdev: user-space parallel port driver
[   12.437723] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.437737] acer-wmi: No or unsupported WMI interface, unable to load
[   12.657863] dib0700: loaded with support for 8 different device-types
[   12.657991] dvb-usb: found a 'Pinnacle PCTV 2000e' in warm state.
[   12.658047] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.658268] DVB: registering new adapter (Pinnacle PCTV 2000e)
[   12.783146] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   12.996705] MT2266: successfully identified
[   13.073271] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.097934] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.126868] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.127118] DVB: registering new adapter (Pinnacle PCTV 2000e)
[   13.131340] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.195516] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   13.197262] MT2266: successfully identified
[   13.326948] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/input/input8
[   13.332103] dvb-usb: schedule remote query interval to 50 msecs.
[   13.332108] dvb-usb: Pinnacle PCTV 2000e successfully initialized and connected.
[   13.332211] usbcore: registered new interface driver dvb_usb_dib0700
[   13.459609] lp0: using parport0 (interrupt-driven).
[   13.520459] Adding 2498068k swap on /dev/sda6.  Priority:-1 extents:1 across:2498068k
[   14.050657] EXT3 FS on sda5, internal journal
[   15.087717] type=1505 audit(1247509207.871:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2209
[   15.124423] type=1505 audit(1247509207.911:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2213
[   15.124499] type=1505 audit(1247509207.911:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2213
[   15.124530] type=1505 audit(1247509207.911:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2213
[   15.124558] type=1505 audit(1247509207.911:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2213
[   15.225758] type=1505 audit(1247509208.011:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2218
[   15.225904] type=1505 audit(1247509208.011:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2218
[   15.247749] type=1505 audit(1247509208.031:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2222
[   18.384134] dib0700: RC Query Failed
[   18.384140] dvb-usb: error while querying for an remote control event.
[   22.884139] 
[   22.884143] floppy driver state
[   22.884144] -------------------
[   22.884147] now=4294898017 last interrupt=4294894271 diff=3746 last called handler=f7ccd4f0
[   22.884150] timeout_message=lock fdc
[   22.884152] last output bytes:
[   22.884154]  8 80 4294894258
[   22.884156]  8 80 4294894258
[   22.884158]  8 80 4294894259
[   22.884160]  8 80 4294894270
[   22.884161]  8 80 4294894270
[   22.884163]  8 80 4294894270
[   22.884165]  8 80 4294894270
[   22.884167]  e 80 4294894270
[   22.884168] 13 80 4294894270
[   22.884170]  0 90 4294894270
[   22.884172] 1a 90 4294894270
[   22.884174]  0 90 4294894270
[   22.884176] 12 90 4294894270
[   22.884177]  0 90 4294894270
[   22.884179] 14 90 4294894270
[   22.884181] 18 80 4294894270
[   22.884182]  8 80 4294894271
[   22.884184]  8 80 4294894271
[   22.884186]  8 80 4294894271
[   22.884188]  8 80 4294894271
[   22.884190] last result at 4294894271
[   22.884191] last redo_fd_request at 4294894271
[   22.884193] 
[   22.884202] status=80
[   22.884204] fdc_busy=1
[   22.884205] floppy_work.func=f7cd1be0
[   22.884207] cont=f7cd6bb4
[   22.884209] current_req=00000000
[   22.884211] command_status=-1
[   22.884212] 
[   22.884216] floppy0: floppy timeout called
[   23.436087] dib0700: RC Query Failed
[   23.436092] dvb-usb: error while querying for an remote control event.
[   23.508668] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.508671] Bluetooth: BNEP filters: protocol multicast
[   23.515517] Bridge firewalling registered
[   28.488162] dib0700: RC Query Failed
[   28.488197] dvb-usb: error while querying for an remote control event.
[   33.540117] dib0700: RC Query Failed
[   33.540160] dvb-usb: error while querying for an remote control event.
[   33.697341] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   33.958207] [drm] Initialized drm 1.1.0 20060810
[   34.067934] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   34.334000] [drm] Setting GART location based on new memory map
[   34.334743] [drm] Loading RS600 Microcode
[   34.334760] [drm] Num pipes: 1
[   34.334765] [drm] writeback test succeeded in 1 usecs
[   38.217096] sky2 eth0: enabling interface
[   38.217262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.592068] dib0700: RC Query Failed
[   38.592074] dvb-usb: error while querying for an remote control event.
[   40.288143] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   43.644145] dib0700: RC Query Failed
[   43.644154] dvb-usb: error while querying for an remote control event.
[   43.644329] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.696152] dib0700: RC Query Failed
[   48.696158] dvb-usb: error while querying for an remote control event.
[   53.748074] dib0700: RC Query Failed
[   53.748079] dvb-usb: error while querying for an remote control event.
[   54.332017] eth0: no IPv6 routers present
[   58.800129] dib0700: RC Query Failed
[   58.800135] dvb-usb: error while querying for an remote control event.
[   63.852051] dib0700: RC Query Failed
[   63.852058] dvb-usb: error while querying for an remote control event.
[   68.904103] dib0700: RC Query Failed
[   68.904109] dvb-usb: error while querying for an remote control event.
[   73.956153] dib0700: RC Query Failed
[   73.956159] dvb-usb: error while querying for an remote control event.
[   79.008079] dib0700: RC Query Failed
[   79.008085] dvb-usb: error while querying for an remote control event.
[   84.060130] dib0700: RC Query Failed
[   84.060134] dvb-usb: error while querying for an remote control event.
[   89.112055] dib0700: RC Query Failed
[   89.112061] dvb-usb: error while querying for an remote control event.
[   94.168103] dib0700: RC Query Failed
[   94.168110] dvb-usb: error while querying for an remote control event.
[   99.224162] dib0700: RC Query Failed
[   99.224168] dvb-usb: error while querying for an remote control event.
[  104.272081] dib0700: RC Query Failed
[  104.272087] dvb-usb: error while querying for an remote control event.
[  109.324131] dib0700: RC Query Failed
[  109.324137] dvb-usb: error while querying for an remote control event.
[  114.376056] dib0700: RC Query Failed
[  114.376062] dvb-usb: error while querying for an remote control event.
[  119.428106] dib0700: RC Query Failed
[  119.428111] dvb-usb: error while querying for an remote control event.
[  124.480909] dib0700: RC Query Failed
[  124.480917] dvb-usb: error while querying for an remote control event.
[  129.532083] dib0700: RC Query Failed
[  129.532089] dvb-usb: error while querying for an remote control event.
[  134.585137] dib0700: RC Query Failed
[  134.585144] dvb-usb: error while querying for an remote control event.
[  139.636058] dib0700: RC Query Failed
[  139.636065] dvb-usb: error while querying for an remote control event.
[  144.692109] dib0700: RC Query Failed
[  144.692115] dvb-usb: error while querying for an remote control event.
[  149.740160] dib0700: RC Query Failed
[  149.740166] dvb-usb: error while querying for an remote control event.
[  154.792150] dib0700: RC Query Failed
[  154.792156] dvb-usb: error while querying for an remote control event.
[  159.844101] dib0700: RC Query Failed
[  159.844107] dvb-usb: error while querying for an remote control event.
[  164.900053] dib0700: RC Query Failed
[  164.900058] dvb-usb: error while querying for an remote control event.
[  169.948130] dib0700: RC Query Failed
[  169.948136] dvb-usb: error while querying for an remote control event.
[  175.000082] dib0700: RC Query Failed
[  175.000088] dvb-usb: error while querying for an remote control event.
[  180.052159] dib0700: RC Query Failed
[  180.052166] dvb-usb: error while querying for an remote control event.
[  185.104111] dib0700: RC Query Failed
[  185.104117] dvb-usb: error while querying for an remote control event.
[  190.156066] dib0700: RC Query Failed
[  190.156073] dvb-usb: error while querying for an remote control event.
[  195.208142] dib0700: RC Query Failed
[  195.208151] dvb-usb: error while querying for an remote control event.
[  200.260092] dib0700: RC Query Failed
[  200.260097] dvb-usb: error while querying for an remote control event.
[  205.312170] dib0700: RC Query Failed
[  205.312176] dvb-usb: error while querying for an remote control event.
[  210.364123] dib0700: RC Query Failed
[  210.364128] dvb-usb: error while querying for an remote control event.
[  215.416074] dib0700: RC Query Failed
[  215.416081] dvb-usb: error while querying for an remote control event.
[  220.468150] dib0700: RC Query Failed
[  220.468156] dvb-usb: error while querying for an remote control event.
[  225.520103] dib0700: RC Query Failed
[  225.520111] dvb-usb: error while querying for an remote control event.
[  230.572056] dib0700: RC Query Failed
[  230.572062] dvb-usb: error while querying for an remote control event.
[  235.624132] dib0700: RC Query Failed
[  235.624138] dvb-usb: error while querying for an remote control event.
[  240.676085] dib0700: RC Query Failed
[  240.676091] dvb-usb: error while querying for an remote control event.
[  245.728163] dib0700: RC Query Failed
[  245.728168] dvb-usb: error while querying for an remote control event.
[  250.784117] dib0700: RC Query Failed
[  250.784122] dvb-usb: error while querying for an remote control event.
[  255.836068] dib0700: RC Query Failed
[  255.836074] dvb-usb: error while querying for an remote control event.
[  260.888144] dib0700: RC Query Failed
[  260.888151] dvb-usb: error while querying for an remote control event.
[  265.940096] dib0700: RC Query Failed
[  265.940102] dvb-usb: error while querying for an remote control event.
[  270.996175] dib0700: RC Query Failed
[  270.996181] dvb-usb: error while querying for an remote control event.
[  276.052129] dib0700: RC Query Failed
[  276.052135] dvb-usb: error while querying for an remote control event.
[  281.104079] dib0700: RC Query Failed
[  281.104085] dvb-usb: error while querying for an remote control event.
[  286.156156] dib0700: RC Query Failed
[  286.156163] dvb-usb: error while querying for an remote control event.
[  291.208106] dib0700: RC Query Failed
[  291.208112] dvb-usb: error while querying for an remote control event.
[  296.260060] dib0700: RC Query Failed
[  296.260065] dvb-usb: error while querying for an remote control event.
[  301.312137] dib0700: RC Query Failed
[  301.312144] dvb-usb: error while querying for an remote control event.
[  306.365715] dib0700: RC Query Failed
[  306.365720] dvb-usb: error while querying for an remote control event.
[  311.416042] dib0700: RC Query Failed
[  311.416048] dvb-usb: error while querying for an remote control event.
[  316.468118] dib0700: RC Query Failed
[  316.468124] dvb-usb: error while querying for an remote control event.
[  321.520071] dib0700: RC Query Failed
[  321.520077] dvb-usb: error while querying for an remote control event.
[  326.572148] dib0700: RC Query Failed
[  326.572154] dvb-usb: error while querying for an remote control event.
[  331.624601] dib0700: RC Query Failed
[  331.624607] dvb-usb: error while querying for an remote control event.
[  336.680054] dib0700: RC Query Failed
[  336.680061] dvb-usb: error while querying for an remote control event.
[  341.732130] dib0700: RC Query Failed
[  341.732136] dvb-usb: error while querying for an remote control event.
[  346.784082] dib0700: RC Query Failed
[  346.784089] dvb-usb: error while querying for an remote control event.
[  351.836159] dib0700: RC Query Failed
[  351.836165] dvb-usb: error while querying for an remote control event.
[  356.888110] dib0700: RC Query Failed
[  356.888116] dvb-usb: error while querying for an remote control event.
[  361.940064] dib0700: RC Query Failed
[  361.940070] dvb-usb: error while querying for an remote control event.
[  366.992142] dib0700: RC Query Failed
[  366.992148] dvb-usb: error while querying for an remote control event.
[  372.044093] dib0700: RC Query Failed
[  372.044099] dvb-usb: error while querying for an remote control event.
[  377.096044] dib0700: RC Query Failed
[  377.096050] dvb-usb: error while querying for an remote control event.
[  382.148121] dib0700: RC Query Failed
[  382.148127] dvb-usb: error while querying for an remote control event.
[  387.204078] dib0700: RC Query Failed
[  387.204084] dvb-usb: error while querying for an remote control event.
[  392.256151] dib0700: RC Query Failed
[  392.256156] dvb-usb: error while querying for an remote control event.
[  397.308104] dib0700: RC Query Failed
[  397.308110] dvb-usb: error while querying for an remote control event.
[  402.360055] dib0700: RC Query Failed
[  402.360061] dvb-usb: error while querying for an remote control event.
[  407.412134] dib0700: RC Query Failed
[  407.412140] dvb-usb: error while querying for an remote control event.
[  412.464087] dib0700: RC Query Failed
[  412.464093] dvb-usb: error while querying for an remote control event.
[  417.516174] dib0700: RC Query Failed
[  417.516180] dvb-usb: error while querying for an remote control event.
[  422.568114] dib0700: RC Query Failed
[  422.568120] dvb-usb: error while querying for an remote control event.
[  427.620068] dib0700: RC Query Failed
[  427.620074] dvb-usb: error while querying for an remote control event.
[  432.672143] dib0700: RC Query Failed
[  432.672148] dvb-usb: error while querying for an remote control event.
[  437.724095] dib0700: RC Query Failed
[  437.724102] dvb-usb: error while querying for an remote control event.
[  442.776044] dib0700: RC Query Failed
[  442.776049] dvb-usb: error while querying for an remote control event.
[  447.828125] dib0700: RC Query Failed
[  447.828132] dvb-usb: error while querying for an remote control event.
[  452.880082] dib0700: RC Query Failed
[  452.880088] dvb-usb: error while querying for an remote control event.
[  457.932154] dib0700: RC Query Failed
[  457.932160] dvb-usb: error while querying for an remote control event.
[  462.984104] dib0700: RC Query Failed
[  462.984110] dvb-usb: error while querying for an remote control event.
[  468.036059] dib0700: RC Query Failed
[  468.036065] dvb-usb: error while querying for an remote control event.
[  473.088133] dib0700: RC Query Failed
[  473.088139] dvb-usb: error while querying for an remote control event.
[  478.140086] dib0700: RC Query Failed
[  478.140093] dvb-usb: error while querying for an remote control event.
[  483.192164] dib0700: RC Query Failed
[  483.192170] dvb-usb: error while querying for an remote control event.
[  488.248236] dib0700: RC Query Failed
[  488.248241] dvb-usb: error while querying for an remote control event.
[  493.299446] dib0700: RC Query Failed
[  493.299452] dvb-usb: error while querying for an remote control event.
[  498.356148] MT2266 I2C read failed
[  498.356153] dib0700: RC Query Failed
[  498.356157] dvb-usb: error while querying for an remote control event.
[  503.408105] dib0700: RC Query Failed
[  503.408113] dvb-usb: error while querying for an remote control event.
[  508.460052] dib0700: RC Query Failed
[  508.460059] dvb-usb: error while querying for an remote control event.
[  513.512131] dib0700: RC Query Failed
[  513.512137] dvb-usb: error while querying for an remote control event.
[  518.564082] dib0700: RC Query Failed
[  518.564088] dvb-usb: error while querying for an remote control event.
[  523.616160] dib0700: RC Query Failed
[  523.616166] dvb-usb: error while querying for an remote control event.
[  528.668111] dib0700: RC Query Failed
[  528.668117] dvb-usb: error while querying for an remote control event.
[  533.720073] dib0700: RC Query Failed
[  533.720079] dvb-usb: error while querying for an remote control event.
[  538.772150] dib0700: RC Query Failed
[  538.772157] dvb-usb: error while querying for an remote control event.
[  543.824093] dib0700: RC Query Failed
[  543.824100] dvb-usb: error while querying for an remote control event.
[  543.839653] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  543.839659] usb 1-1: USB disconnect, address 2
[  543.847396] MT2266 I2C write failed
[  543.847400] MT2266 I2C write failed
[  548.828046] dvb-usb: error while stopping stream.
[  548.828841] dvb-usb: Pinnacle PCTV 2000e successfully deinitialized and disconnected.
[  549.068028] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  549.201103] usb 1-1: configuration #1 chosen from 1 choice
[  549.201382] dvb-usb: found a 'Pinnacle PCTV 2000e' in warm state.
[  549.201415] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  549.201630] DVB: registering new adapter (Pinnacle PCTV 2000e)
[  549.343176] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[  549.344922] MT2266: successfully identified
[  549.473461] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  549.473688] DVB: registering new adapter (Pinnacle PCTV 2000e)
[  549.555238] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[  549.556985] MT2266: successfully identified
[  549.686860] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/input/input9
[  549.687959] dvb-usb: schedule remote query interval to 50 msecs.
[  549.687964] dvb-usb: Pinnacle PCTV 2000e successfully initialized and connected.
[  554.736103] dib0700: RC Query Failed
[  554.736109] dvb-usb: error while querying for an remote control event.
[  559.788055] dib0700: RC Query Failed
[  559.788062] dvb-usb: error while querying for an remote control event.
[  564.840132] dib0700: RC Query Failed
[  564.840139] dvb-usb: error while querying for an remote control event.
[  569.896088] dib0700: RC Query Failed
[  569.896095] dvb-usb: error while querying for an remote control event.

---

### Post by venusfenix on 2009-07-13
continua sense funcionar.

Tambe, per si et dona alguna pista, quan entro, en diu que si vull veure el differents modes de video. es normal?

et deixo el resultat de dmesg:


dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fff0000 (usable)
[    0.000000]  BIOS-e820: 000000006fff0000 - 000000006fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fff3000 - 0000000070000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x6fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fff0000 (usable)
[    0.000000]  modified: 000000006fff0000 - 000000006fff3000 (ACPI NVS)
[    0.000000]  modified: 000000006fff3000 - 0000000070000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef38c
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb238c
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef38b to 00881000 - 00fb238b
[    0.000000] ACPI: RSDP 000F8180, 0014 (r0 ACRSYS)
[    0.000000] ACPI: RSDT 6FFF3040, 0040 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 6FFF30C0, 0074 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 6FFF3180, 48AE (r1 ACRSYS AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FFF0000, 0040
[    0.000000] ACPI: HPET 6FFF7B80, 0038 (r1 ACRSYS ACRPRDCT 42302E31 AWRD       98)
[    0.000000] ACPI: SLIC 6FFF7C00, 0176 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: MCFG 6FFF7DC0, 003C (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 6FFF7A80, 0084 (r1 ACRSYS ACRPRDCT 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 6FFF7E40, 0175 (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    0.000000] ACPI: SSDT 6FFF84C0, 02F9 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 907MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb238c]      NEW RAMDISK ==> [0000881000 - 0000fb238c]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f4030] 000f4030
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0006fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006fff0
[    0.000000] On node 0 totalpages: 458623
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1816 pages used for memmap
[    0.000000]   HighMem zone: 230618 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 70000000:70000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 455039
[    0.000000] Kernel command line: root=UUID=f30a5604-539f-47b6-9443-b3236ed246a6 ro splash vga=795 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2399.715 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9174400 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1794244k/1834944k available (4126k kernel code, 39372k reserved, 2208k data, 532k init, 929736k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.43 BogoMIPS (lpj=9598860)
[    0.004094] Security Framework initialized
[    0.004136] SELinux:  Disabled at boot.
[    0.004181] AppArmor: AppArmor initialized
[    0.004222] Mount-cache hash table entries: 512
[    0.004384] Initializing cgroup subsys ns
[    0.004422] Initializing cgroup subsys cpuacct
[    0.004458] Initializing cgroup subsys memory
[    0.004495] Initializing cgroup subsys freezer
[    0.004543] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004607] CPU: L2 cache: 4096K
[    0.004643] CPU: Physical Processor ID: 0
[    0.004678] CPU: Processor Core ID: 0
[    0.004715] using mwait in idle threads.
[    0.004760] Checking 'hlt' instruction... OK.
[    0.022135] ACPI: Core revision 20080926
[    0.023937] ACPI: Checking initramfs for custom DSDT
[    0.272409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.314944] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.316001] Booting processor 1 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4800.21 BogoMIPS (lpj=9600426)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.400607] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.401613] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.404094] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4800.21 BogoMIPS (lpj=9600432)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.496632] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.496937] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.500091] Booting processor 3 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4800.19 BogoMIPS (lpj=9600389)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.592556] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.592878] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.596033] Brought up 4 CPUs
[    0.596070] Total of 4 processors activated (19200.05 BogoMIPS).
[    0.596149] CPU0 attaching sched-domain:
[    0.596152]  domain 0: span 0,3 level MC
[    0.596154]   groups: 0 3
[    0.596158]   domain 1: span 0-3 level CPU
[    0.596160]    groups: 0,3 1-2
[    0.596164] CPU1 attaching sched-domain:
[    0.596166]  domain 0: span 1-2 level MC
[    0.596167]   groups: 1 2
[    0.596170]   domain 1: span 0-3 level CPU
[    0.596172]    groups: 1-2 0,3
[    0.596176] CPU2 attaching sched-domain:
[    0.596178]  domain 0: span 1-2 level MC
[    0.596179]   groups: 2 1
[    0.596182]   domain 1: span 0-3 level CPU
[    0.596184]    groups: 1-2 0,3
[    0.596188] CPU3 attaching sched-domain:
[    0.596189]  domain 0: span 0,3 level MC
[    0.596191]   groups: 3 0
[    0.596194]   domain 1: span 0-3 level CPU
[    0.596195]    groups: 0,3 1-2
[    0.596318] net_namespace: 776 bytes
[    0.596318] Booting paravirtualized kernel on bare hardware
[    0.596374] Time: 20:19:53  Date: 07/13/09
[    0.596374] regulator: core version 0.5
[    0.596374] NET: Registered protocol family 16
[    0.596374] EISA bus registered
[    0.596374] ACPI: bus type pci registered
[    0.596389] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.596426] PCI: MCFG area at e0000000 reserved in E820
[    0.596462] PCI: Using MMCONFIG for extended config space
[    0.596498] PCI: Using configuration type 1 for base access
[    0.597245] ACPI: EC: Look up EC in DSDT
[    0.605762] ACPI: Interpreter enabled
[    0.605804] ACPI: (supports S0 S3 S4 S5)
[    0.605970] ACPI: Using IOAPIC for interrupt routing
[    0.610317] ACPI: No dock devices found.
[    0.610359] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.610496] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.610534] pci 0000:00:06.0: PME# disabled
[    0.610623] pci 0000:00:12.0: reg 10 io port: [0xff00-0xff07]
[    0.610630] pci 0000:00:12.0: reg 14 io port: [0xfe00-0xfe03]
[    0.610638] pci 0000:00:12.0: reg 18 io port: [0xfd00-0xfd07]
[    0.610645] pci 0000:00:12.0: reg 1c io port: [0xfc00-0xfc03]
[    0.610652] pci 0000:00:12.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.610659] pci 0000:00:12.0: reg 24 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.610680] pci 0000:00:12.0: set SATA to AHCI mode
[    0.610745] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdffe000-0xfdffefff]
[    0.610804] pci 0000:00:13.1: reg 10 32bit mmio: [0xfdffd000-0xfdffdfff]
[    0.610864] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdffc000-0xfdffcfff]
[    0.610923] pci 0000:00:13.3: reg 10 32bit mmio: [0xfdffb000-0xfdffbfff]
[    0.610982] pci 0000:00:13.4: reg 10 32bit mmio: [0xfdffa000-0xfdffafff]
[    0.611063] pci 0000:00:13.5: reg 10 32bit mmio: [0xfdff9000-0xfdff90ff]
[    0.611107] pci 0000:00:13.5: supports D1 D2
[    0.611109] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.611148] pci 0000:00:13.5: PME# disabled
[    0.611217] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.611275] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.611282] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.611289] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.611296] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.611303] pci 0000:00:14.1: reg 20 io port: [0xf900-0xf90f]
[    0.611360] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    0.611399] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.611438] pci 0000:00:14.2: PME# disabled
[    0.611610] pci 0000:01:05.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.611616] pci 0000:01:05.0: reg 18 64bit mmio: [0xfdde0000-0xfddeffff]
[    0.611620] pci 0000:01:05.0: reg 20 io port: [0xde00-0xdeff]
[    0.611630] pci 0000:01:05.0: supports D1 D2
[    0.611655] pci 0000:01:05.2: reg 10 64bit mmio: [0xfddfc000-0xfddfffff]
[    0.611695] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.611698] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.611702] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.611754] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdcfc000-0xfdcfffff]
[    0.611761] pci 0000:02:00.0: reg 18 io port: [0xee00-0xeeff]
[    0.611784] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.611794] pci 0000:02:00.0: supports D1 D2
[    0.611795] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.611835] pci 0000:02:00.0: PME# disabled
[    0.611925] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
[    0.611928] pci 0000:00:06.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.611932] pci 0000:00:06.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.611984] pci 0000:03:02.0: reg 10 32bit mmio: [0xfdbff000-0xfdbff7ff]
[    0.611993] pci 0000:03:02.0: reg 14 32bit mmio: [0xfdbf8000-0xfdbfbfff]
[    0.612053] pci 0000:03:02.0: supports D1 D2
[    0.612054] pci 0000:03:02.0: PME# supported from D0 D1 D2 D3hot
[    0.612094] pci 0000:03:02.0: PME# disabled
[    0.612189] pci 0000:00:14.4: transparent bridge
[    0.612227] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]
[    0.612232] pci 0000:00:14.4: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.612237] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
[    0.612250] bus 00 -> node 0
[    0.612256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.612540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.612676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.612764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.627612] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628080] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628538] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.628996] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.629452] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.629909] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.630366] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.630834] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.631421] ACPI: WMI: Mapper loaded
[    0.631490] SCSI subsystem initialized
[    0.631490] libata version 3.00 loaded.
[    0.631490] usbcore: registered new interface driver usbfs
[    0.631490] usbcore: registered new interface driver hub
[    0.631490] usbcore: registered new device driver usb
[    0.632059] PCI: Using ACPI for IRQ routing
[    0.636014] Bluetooth: Core ver 2.13
[    0.636068] NET: Registered protocol family 31
[    0.636068] Bluetooth: HCI device and connection manager initialized
[    0.636104] Bluetooth: HCI socket layer initialized
[    0.636140] NET: Registered protocol family 8
[    0.636175] NET: Registered protocol family 20
[    0.636218] NetLabel: Initializing
[    0.636252] NetLabel:  domain hash size = 128
[    0.636287] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.636331] NetLabel:  unlabeled traffic allowed by default
[    0.636395] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.636577] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.648065] AppArmor: AppArmor Filesystem Enabled
[    0.652011] Switched to high resolution mode on CPU 0
[    0.652987] Switched to high resolution mode on CPU 3
[    0.653975] Switched to high resolution mode on CPU 2
[    0.654675] Switched to high resolution mode on CPU 1
[    0.655827] pnp: PnP ACPI init
[    0.655872] ACPI: bus type pnp registered
[    0.658593] pnp: PnP ACPI: found 14 devices
[    0.658630] ACPI: ACPI bus type pnp unregistered
[    0.658666] PnPBIOS: Disabled by ACPI PNP
[    0.658707] system 00:01: ioport range 0x4100-0x411f has been reserved
[    0.658744] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.658780] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.658817] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.658854] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.658890] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.658926] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.658963] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.658999] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.659036] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[    0.659073] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[    0.659109] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.659146] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.659182] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.659219] system 00:01: ioport range 0xb10-0xb1f has been reserved
[    0.659260] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.659297] system 00:07: ioport range 0x800-0x805 has been reserved
[    0.659333] system 00:07: ioport range 0x880-0x88f has been reserved
[    0.659374] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.659414] system 00:0d: iomem range 0xf0000-0xfffff could not be reserved
[    0.659451] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.659488] system 00:0d: iomem range 0x6fff0000-0x6fffffff could not be reserved
[    0.659529] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.659566] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.659603] system 00:0d: iomem range 0x100000-0x6ffeffff could not be reserved
[    0.659643] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.659680] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.659718] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.694414] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.694451] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.694489] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.694526] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.694570] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.694606] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.694643] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.694680] pci 0000:00:06.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.694723] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.694760] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.694800] pci 0000:00:14.4:   MEM window: 0xfdb00000-0xfdbfffff
[    0.694838] pci 0000:00:14.4:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.694891] pci 0000:00:06.0: setting latency timer to 64
[    0.694899] bus: 00 index 0 io port: [0x00-0xffff]
[    0.694935] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.694970] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.695006] bus: 01 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.695042] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.695077] bus: 01 index 3 mmio: [0x0-0x0]
[    0.695113] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.695148] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.695184] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.695220] bus: 02 index 3 mmio: [0x0-0x0]
[    0.695255] bus: 03 index 0 io port: [0xc000-0xcfff]
[    0.695291] bus: 03 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.695326] bus: 03 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.695362] bus: 03 index 3 io port: [0x00-0xffff]
[    0.695397] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.695438] NET: Registered protocol family 2
[    0.708084] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.708323] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.708678] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.708879] TCP: Hash tables configured (established 131072 bind 65536)
[    0.708916] TCP reno registered
[    0.712113] NET: Registered protocol family 1
[    0.712249] checking if image is initramfs... it is
[    1.211606] Freeing initrd memory: 7364k freed
[    1.212049] cpufreq: No nForce2 chipset.
[    1.212222] audit: initializing netlink socket (disabled)
[    1.212285] type=2000 audit(1247516393.212:1): initialized
[    1.218324] highmem bounce pool size: 64 pages
[    1.218362] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.219614] VFS: Disk quotas dquot_6.5.1
[    1.219719] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.220313] fuse init (API version 7.10)
[    1.220416] msgmni has been set to 1704
[    1.220665] alg: No test for stdrng (krng)
[    1.220715] io scheduler noop registered
[    1.220756] io scheduler anticipatory registered
[    1.220794] io scheduler deadline registered
[    1.220851] io scheduler cfq registered (default)
[    2.048020] pci 0000:00:13.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    2.132058] pci 0000:01:05.0: Boot video device
[    2.134498] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.134526] pcieport-driver 0000:00:06.0: found MSI capability
[    2.134585] pcieport-driver 0000:00:06.0: irq 2303 for MSI/MSI-X
[    2.134594] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.134606] pci_express 0000:00:06.0:pcie03: allocate port service
[    2.134656] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.134698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.134857] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.135600] ACPI: Power Button (FF) [PWRF]
[    2.135668] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.135709] ACPI: Power Button (CM) [PWRB]
[    2.135784] fan PNP0C0B:00: registered as cooling_device0
[    2.135823] ACPI: Fan [FAN] (on)
[    2.136084] processor ACPI_CPU:00: registered as cooling_device1
[    2.136122] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.136403] ACPI: SSDT 6FFF8250, 00CE (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    2.136735] processor ACPI_CPU:01: registered as cooling_device2
[    2.136784] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.137122] ACPI: SSDT 6FFF8320, 00CE (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[    2.137426] processor ACPI_CPU:02: registered as cooling_device3
[    2.137464] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.137761] ACPI: SSDT 6FFF83F0, 00CE (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[    2.138079] processor ACPI_CPU:03: registered as cooling_device4
[    2.138119] ACPI: Processor [CPU3] (supports 8 throttling states)
[    2.140211] thermal LNXTHERM:01: registered as thermal_zone0
[    2.140486] ACPI: Thermal Zone [THRM] (40 C)
[    2.140568] isapnp: Scanning for PnP cards...
[    2.494394] isapnp: No Plug & Play device found
[    2.501736] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.501878] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.502277] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.502956] brd: module loaded
[    2.503241] loop: module loaded
[    2.503329] Fixed MDIO Bus: probed
[    2.503367] PPP generic driver version 2.4.2
[    2.503447] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.503509] Driver 'sd' needs updating - please use bus_type methods
[    2.503551] Driver 'sr' needs updating - please use bus_type methods
[    2.503614] ahci 0000:00:12.0: version 3.0
[    2.503630] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.503694] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    2.503827] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.503871] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    2.504308] scsi0 : ahci
[    2.504444] scsi1 : ahci
[    2.504554] scsi2 : ahci
[    2.504678] scsi3 : ahci
[    2.504796] ata1: SATA max UDMA/133 irq_stat 0x00400000 irq 22, PHY RDY changed
[    2.504837] ata2: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff180 irq 22
[    2.504878] ata3: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff200 irq 22
[    2.504920] ata4: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff280 irq 22
[    3.392033] ata1: softreset failed (device not ready)
[    3.392076] ata1: failed due to HW bug, retry pmp=0
[    3.556036] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.556634] ata1.00: ATA-7: ST3250310AS, 3.AAD, max UDMA/133
[    3.556678] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.556730] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.557478] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.557522] ata1.00: configured for UDMA/133
[    3.892036] ata2: SATA link down (SStatus 0 SControl 300)
[    4.392033] ata3: softreset failed (device not ready)
[    4.392073] ata3: failed due to HW bug, retry pmp=0
[    4.556053] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.558809] ata3.00: ATAPI: HL-DT-ST DVDRAM_GSA-H60N, CA01, max UDMA/100
[    4.558878] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.562753] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.562793] ata3.00: configured for UDMA/100
[    5.008038] ata4: SATA link down (SStatus 0 SControl 300)
[    5.024150] scsi 0:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    5.024264] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    5.024316] sd 0:0:0:0: [sda] Write Protect is off
[    5.024352] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.024372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.024460] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    5.024510] sd 0:0:0:0: [sda] Write Protect is off
[    5.024546] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.024565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.024608]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    5.069221] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.069289] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.072147] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM_GSA-H60N  CA01 PQ: 0 ANSI: 5
[    5.399095] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.399142] Uniform CD-ROM driver Revision: 3.20
[    5.399253] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    5.399283] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    5.399521] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.399682] scsi4 : pata_atiixp
[    5.399797] scsi5 : pata_atiixp
[    5.400783] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    5.400820] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    5.720456] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.720509] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.720556] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    5.720638] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    5.720702] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    5.720760] ehci_hcd 0000:00:13.5: debug port 1
[    5.720810] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfdff9000
[    5.732025] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    5.732145] usb usb1: configuration #1 chosen from 1 choice
[    5.732201] hub 1-0:1.0: USB hub found
[    5.732242] hub 1-0:1.0: 10 ports detected
[    5.732381] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.732426] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.732470] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.732535] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    5.732592] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfdffe000
[    5.792051] usb usb2: configuration #1 chosen from 1 choice
[    5.792108] hub 2-0:1.0: USB hub found
[    5.792150] hub 2-0:1.0: 2 ports detected
[    5.792252] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.792296] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.792362] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.792418] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfdffd000
[    5.852048] usb usb3: configuration #1 chosen from 1 choice
[    5.852102] hub 3-0:1.0: USB hub found
[    5.852144] hub 3-0:1.0: 2 ports detected
[    5.852245] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.852290] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    5.852356] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    5.852414] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfdffc000
[    5.912051] usb usb4: configuration #1 chosen from 1 choice
[    5.912105] hub 4-0:1.0: USB hub found
[    5.912147] hub 4-0:1.0: 2 ports detected
[    5.912249] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.912293] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    5.912359] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    5.912409] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfdffb000
[    5.972049] usb usb5: configuration #1 chosen from 1 choice
[    5.972106] hub 5-0:1.0: USB hub found
[    5.972151] hub 5-0:1.0: 2 ports detected
[    5.972251] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.972296] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    5.972367] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    5.972420] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfdffa000
[    6.032051] usb usb6: configuration #1 chosen from 1 choice
[    6.032105] hub 6-0:1.0: USB hub found
[    6.032149] hub 6-0:1.0: 2 ports detected
[    6.032253] uhci_hcd: USB Universal Host Controller Interface driver
[    6.032343] usbcore: registered new interface driver libusual
[    6.032403] usbcore: registered new interface driver usbserial
[    6.032446] USB Serial support registered for generic
[    6.044060] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.176917] usb 1-1: configuration #1 chosen from 1 choice
[    6.664026] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    6.833245] usb 3-1: configuration #1 chosen from 1 choice
[    7.096075] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    7.265312] usb 3-2: configuration #1 chosen from 1 choice
[    7.528036] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    7.697357] usb 6-2: configuration #1 chosen from 1 choice
[    7.699493] usbcore: registered new interface driver usbserial_generic
[    7.699534] usbserial: USB Serial Driver core
[    7.699609] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    7.699646] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    7.699751] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.704066] mice: PS/2 mouse device common for all mice
[    7.708161] rtc_cmos 00:04: RTC can wake from S4
[    7.708229] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    7.708289] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    7.708371] device-mapper: uevent: version 1.0.3
[    7.708516] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    7.709442] device-mapper: multipath: version 1.0.5 loaded
[    7.709487] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.709624] EISA: Probing bus 0 at eisa.0
[    7.709675] Cannot allocate resource for EISA slot 4
[    7.709725] EISA: Detected 0 cards.
[    7.709889] cpuidle: using governor ladder
[    7.709933] cpuidle: using governor menu
[    7.710373] TCP cubic registered
[    7.710486] NET: Registered protocol family 10
[    7.710884] lo: Disabled Privacy Extensions
[    7.711176] NET: Registered protocol family 17
[    7.711224] Bluetooth: L2CAP ver 2.11
[    7.711259] Bluetooth: L2CAP socket layer initialized
[    7.711296] Bluetooth: SCO (Voice Link) ver 0.6
[    7.711331] Bluetooth: SCO socket layer initialized
[    7.711423] Bluetooth: RFCOMM socket layer initialized
[    7.711471] Bluetooth: RFCOMM TTY layer initialized
[    7.711507] Bluetooth: RFCOMM ver 1.10
[    7.712286] Using IPI No-Shortcut mode
[    7.712375] registered taskstats version 1
[    7.712510]   Magic number: 1:376:346
[    7.712558] tty tty63: hash matches
[    7.712649] rtc_cmos 00:04: setting system clock to 2009-07-13 20:20:00 UTC (1247516400)
[    7.712696] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.712736] EDD information not available.
[    7.713098] Freeing unused kernel memory: 532k freed
[    7.713254] Write protecting the kernel text: 4128k
[    7.713337] Write protecting the kernel read-only data: 1532k
[    7.737155] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    7.851783] Floppy drive(s): fd0 is 1.44M
[    7.863780] sky2 driver version 1.22
[    7.863827] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.863838] sky2 0000:02:00.0: setting latency timer to 64
[    7.863893] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
[    7.878343] usbcore: registered new interface driver hiddev
[    7.882598] input: Justcom Technology USB KVM Switch as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input4
[    7.895868] sky2 0000:02:00.0: Marvell Yukon 88E8056 Gigabit Ethernet Controller
[    7.895871]  Part Number: Yukon 88E8056
[    7.895872]  Engineering Level: Rev. 1.2
[    7.895873]  Manufacturer: Marvell
[    7.895983] sky2 0000:02:00.0: irq 2302 for MSI/MSI-X
[    7.896705] sky2 eth0: addr 00:1d:92:3e:74:f1
[    7.900167] FDC 0 is a post-1991 82077
[    7.906634] ohci1394 0000:03:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.956400] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.969974] generic-usb 0003:06F2:0011.0001: input,hidraw0: USB HID v1.10 Keyboard [Justcom Technology USB KVM Switch] on usb-0000:00:13.1-2/input0
[    7.974206] input: Justcom Technology USB KVM Switch as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input5
[    7.993624] generic-usb 0003:06F2:0011.0002: input,hidraw1: USB HID v1.10 Mouse [Justcom Technology USB KVM Switch] on usb-0000:00:13.1-2/input1
[    7.993655] usbcore: registered new interface driver usbhid
[    7.993664] usbhid: v2.6:USB HID core driver
[    8.249311] PM: Starting manual resume from disk
[    8.249315] PM: Resume from partition 8:6
[    8.249316] PM: Checking hibernation image.
[    8.249458] PM: Resume from disk failed.
[    8.275442] kjournald starting.  Commit interval 5 seconds
[    8.275449] EXT3-fs: mounted filesystem with ordered data mode.
[    9.240404] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00013c305b]
[   11.907410] udev: starting version 141
[   12.063635] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.063692] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.102074] Linux agpgart interface v0.103
[   12.214478] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.245080] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.254102] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.268211] input: Wacom Volito as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input7
[   12.303072] usbcore: registered new interface driver wacom
[   12.303103] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[   12.345672] ppdev: user-space parallel port driver
[   12.437723] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.437737] acer-wmi: No or unsupported WMI interface, unable to load
[   12.657863] dib0700: loaded with support for 8 different device-types
[   12.657991] dvb-usb: found a 'Pinnacle PCTV 2000e' in warm state.
[   12.658047] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.658268] DVB: registering new adapter (Pinnacle PCTV 2000e)
[   12.783146] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   12.996705] MT2266: successfully identified
[   13.073271] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.097934] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.126868] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.127118] DVB: registering new adapter (Pinnacle PCTV 2000e)
[   13.131340] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.195516] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   13.197262] MT2266: successfully identified
[   13.326948] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/input/input8
[   13.332103] dvb-usb: schedule remote query interval to 50 msecs.
[   13.332108] dvb-usb: Pinnacle PCTV 2000e successfully initialized and connected.
[   13.332211] usbcore: registered new interface driver dvb_usb_dib0700
[   13.459609] lp0: using parport0 (interrupt-driven).
[   13.520459] Adding 2498068k swap on /dev/sda6.  Priority:-1 extents:1 across:2498068k
[   14.050657] EXT3 FS on sda5, internal journal
[   15.087717] type=1505 audit(1247509207.871:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2209
[   15.124423] type=1505 audit(1247509207.911:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2213
[   15.124499] type=1505 audit(1247509207.911:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2213
[   15.124530] type=1505 audit(1247509207.911:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2213
[   15.124558] type=1505 audit(1247509207.911:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2213
[   15.225758] type=1505 audit(1247509208.011:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2218
[   15.225904] type=1505 audit(1247509208.011:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2218
[   15.247749] type=1505 audit(1247509208.031:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2222
[   18.384134] dib0700: RC Query Failed
[   18.384140] dvb-usb: error while querying for an remote control event.
[   22.884139] 
[   22.884143] floppy driver state
[   22.884144] -------------------
[   22.884147] now=4294898017 last interrupt=4294894271 diff=3746 last called handler=f7ccd4f0
[   22.884150] timeout_message=lock fdc
[   22.884152] last output bytes:
[   22.884154]  8 80 4294894258
[   22.884156]  8 80 4294894258
[   22.884158]  8 80 4294894259
[   22.884160]  8 80 4294894270
[   22.884161]  8 80 4294894270
[   22.884163]  8 80 4294894270
[   22.884165]  8 80 4294894270
[   22.884167]  e 80 4294894270
[   22.884168] 13 80 4294894270
[   22.884170]  0 90 4294894270
[   22.884172] 1a 90 4294894270
[   22.884174]  0 90 4294894270
[   22.884176] 12 90 4294894270
[   22.884177]  0 90 4294894270
[   22.884179] 14 90 4294894270
[   22.884181] 18 80 4294894270
[   22.884182]  8 80 4294894271
[   22.884184]  8 80 4294894271
[   22.884186]  8 80 4294894271
[   22.884188]  8 80 4294894271
[   22.884190] last result at 4294894271
[   22.884191] last redo_fd_request at 4294894271
[   22.884193] 
[   22.884202] status=80
[   22.884204] fdc_busy=1
[   22.884205] floppy_work.func=f7cd1be0
[   22.884207] cont=f7cd6bb4
[   22.884209] current_req=00000000
[   22.884211] command_status=-1
[   22.884212] 
[   22.884216] floppy0: floppy timeout called
[   23.436087] dib0700: RC Query Failed
[   23.436092] dvb-usb: error while querying for an remote control event.
[   23.508668] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.508671] Bluetooth: BNEP filters: protocol multicast
[   23.515517] Bridge firewalling registered
[   28.488162] dib0700: RC Query Failed
[   28.488197] dvb-usb: error while querying for an remote control event.
[   33.540117] dib0700: RC Query Failed
[   33.540160] dvb-usb: error while querying for an remote control event.
[   33.697341] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   33.958207] [drm] Initialized drm 1.1.0 20060810
[   34.067934] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   34.334000] [drm] Setting GART location based on new memory map
[   34.334743] [drm] Loading RS600 Microcode
[   34.334760] [drm] Num pipes: 1
[   34.334765] [drm] writeback test succeeded in 1 usecs
[   38.217096] sky2 eth0: enabling interface
[   38.217262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.592068] dib0700: RC Query Failed
[   38.592074] dvb-usb: error while querying for an remote control event.
[   40.288143] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   43.644145] dib0700: RC Query Failed
[   43.644154] dvb-usb: error while querying for an remote control event.
[   43.644329] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.696152] dib0700: RC Query Failed
[   48.696158] dvb-usb: error while querying for an remote control event.
[   53.748074] dib0700: RC Query Failed
[   53.748079] dvb-usb: error while querying for an remote control event.
[   54.332017] eth0: no IPv6 routers present
[   58.800129] dib0700: RC Query Failed
[   58.800135] dvb-usb: error while querying for an remote control event.
[   63.852051] dib0700: RC Query Failed
[   63.852058] dvb-usb: error while querying for an remote control event.
[   68.904103] dib0700: RC Query Failed
[   68.904109] dvb-usb: error while querying for an remote control event.
[   73.956153] dib0700: RC Query Failed
[   73.956159] dvb-usb: error while querying for an remote control event.
[   79.008079] dib0700: RC Query Failed
[   79.008085] dvb-usb: error while querying for an remote control event.
[   84.060130] dib0700: RC Query Failed
[   84.060134] dvb-usb: error while querying for an remote control event.
[   89.112055] dib0700: RC Query Failed
[   89.112061] dvb-usb: error while querying for an remote control event.
[   94.168103] dib0700: RC Query Failed
[   94.168110] dvb-usb: error while querying for an remote control event.
[   99.224162] dib0700: RC Query Failed
[   99.224168] dvb-usb: error while querying for an remote control event.
[  104.272081] dib0700: RC Query Failed
[  104.272087] dvb-usb: error while querying for an remote control event.
[  109.324131] dib0700: RC Query Failed
[  109.324137] dvb-usb: error while querying for an remote control event.
[  114.376056] dib0700: RC Query Failed
[  114.376062] dvb-usb: error while querying for an remote control event.
[  119.428106] dib0700: RC Query Failed
[  119.428111] dvb-usb: error while querying for an remote control event.
[  124.480909] dib0700: RC Query Failed
[  124.480917] dvb-usb: error while querying for an remote control event.
[  129.532083] dib0700: RC Query Failed
[  129.532089] dvb-usb: error while querying for an remote control event.
[  134.585137] dib0700: RC Query Failed
[  134.585144] dvb-usb: error while querying for an remote control event.
[  139.636058] dib0700: RC Query Failed
[  139.636065] dvb-usb: error while querying for an remote control event.
[  144.692109] dib0700: RC Query Failed
[  144.692115] dvb-usb: error while querying for an remote control event.
[  149.740160] dib0700: RC Query Failed
[  149.740166] dvb-usb: error while querying for an remote control event.
[  154.792150] dib0700: RC Query Failed
[  154.792156] dvb-usb: error while querying for an remote control event.
[  159.844101] dib0700: RC Query Failed
[  159.844107] dvb-usb: error while querying for an remote control event.
[  164.900053] dib0700: RC Query Failed
[  164.900058] dvb-usb: error while querying for an remote control event.
[  169.948130] dib0700: RC Query Failed
[  169.948136] dvb-usb: error while querying for an remote control event.
[  175.000082] dib0700: RC Query Failed
[  175.000088] dvb-usb: error while querying for an remote control event.
[  180.052159] dib0700: RC Query Failed
[  180.052166] dvb-usb: error while querying for an remote control event.
[  185.104111] dib0700: RC Query Failed
[  185.104117] dvb-usb: error while querying for an remote control event.
[  190.156066] dib0700: RC Query Failed
[  190.156073] dvb-usb: error while querying for an remote control event.
[  195.208142] dib0700: RC Query Failed
[  195.208151] dvb-usb: error while querying for an remote control event.
[  200.260092] dib0700: RC Query Failed
[  200.260097] dvb-usb: error while querying for an remote control event.
[  205.312170] dib0700: RC Query Failed
[  205.312176] dvb-usb: error while querying for an remote control event.
[  210.364123] dib0700: RC Query Failed
[  210.364128] dvb-usb: error while querying for an remote control event.
[  215.416074] dib0700: RC Query Failed
[  215.416081] dvb-usb: error while querying for an remote control event.
[  220.468150] dib0700: RC Query Failed
[  220.468156] dvb-usb: error while querying for an remote control event.
[  225.520103] dib0700: RC Query Failed
[  225.520111] dvb-usb: error while querying for an remote control event.
[  230.572056] dib0700: RC Query Failed
[  230.572062] dvb-usb: error while querying for an remote control event.
[  235.624132] dib0700: RC Query Failed
[  235.624138] dvb-usb: error while querying for an remote control event.
[  240.676085] dib0700: RC Query Failed
[  240.676091] dvb-usb: error while querying for an remote control event.
[  245.728163] dib0700: RC Query Failed
[  245.728168] dvb-usb: error while querying for an remote control event.
[  250.784117] dib0700: RC Query Failed
[  250.784122] dvb-usb: error while querying for an remote control event.
[  255.836068] dib0700: RC Query Failed
[  255.836074] dvb-usb: error while querying for an remote control event.
[  260.888144] dib0700: RC Query Failed
[  260.888151] dvb-usb: error while querying for an remote control event.
[  265.940096] dib0700: RC Query Failed
[  265.940102] dvb-usb: error while querying for an remote control event.
[  270.996175] dib0700: RC Query Failed
[  270.996181] dvb-usb: error while querying for an remote control event.
[  276.052129] dib0700: RC Query Failed
[  276.052135] dvb-usb: error while querying for an remote control event.
[  281.104079] dib0700: RC Query Failed
[  281.104085] dvb-usb: error while querying for an remote control event.
[  286.156156] dib0700: RC Query Failed
[  286.156163] dvb-usb: error while querying for an remote control event.
[  291.208106] dib0700: RC Query Failed
[  291.208112] dvb-usb: error while querying for an remote control event.
[  296.260060] dib0700: RC Query Failed
[  296.260065] dvb-usb: error while querying for an remote control event.
[  301.312137] dib0700: RC Query Failed
[  301.312144] dvb-usb: error while querying for an remote control event.
[  306.365715] dib0700: RC Query Failed
[  306.365720] dvb-usb: error while querying for an remote control event.
[  311.416042] dib0700: RC Query Failed
[  311.416048] dvb-usb: error while querying for an remote control event.
[  316.468118] dib0700: RC Query Failed
[  316.468124] dvb-usb: error while querying for an remote control event.
[  321.520071] dib0700: RC Query Failed
[  321.520077] dvb-usb: error while querying for an remote control event.
[  326.572148] dib0700: RC Query Failed
[  326.572154] dvb-usb: error while querying for an remote control event.
[  331.624601] dib0700: RC Query Failed
[  331.624607] dvb-usb: error while querying for an remote control event.
[  336.680054] dib0700: RC Query Failed
[  336.680061] dvb-usb: error while querying for an remote control event.
[  341.732130] dib0700: RC Query Failed
[  341.732136] dvb-usb: error while querying for an remote control event.
[  346.784082] dib0700: RC Query Failed
[  346.784089] dvb-usb: error while querying for an remote control event.
[  351.836159] dib0700: RC Query Failed
[  351.836165] dvb-usb: error while querying for an remote control event.
[  356.888110] dib0700: RC Query Failed
[  356.888116] dvb-usb: error while querying for an remote control event.
[  361.940064] dib0700: RC Query Failed
[  361.940070] dvb-usb: error while querying for an remote control event.
[  366.992142] dib0700: RC Query Failed
[  366.992148] dvb-usb: error while querying for an remote control event.
[  372.044093] dib0700: RC Query Failed
[  372.044099] dvb-usb: error while querying for an remote control event.
[  377.096044] dib0700: RC Query Failed
[  377.096050] dvb-usb: error while querying for an remote control event.
[  382.148121] dib0700: RC Query Failed
[  382.148127] dvb-usb: error while querying for an remote control event.
[  387.204078] dib0700: RC Query Failed
[  387.204084] dvb-usb: error while querying for an remote control event.
[  392.256151] dib0700: RC Query Failed
[  392.256156] dvb-usb: error while querying for an remote control event.
[  397.308104] dib0700: RC Query Failed
[  397.308110] dvb-usb: error while querying for an remote control event.
[  402.360055] dib0700: RC Query Failed
[  402.360061] dvb-usb: error while querying for an remote control event.
[  407.412134] dib0700: RC Query Failed
[  407.412140] dvb-usb: error while querying for an remote control event.
[  412.464087] dib0700: RC Query Failed
[  412.464093] dvb-usb: error while querying for an remote control event.
[  417.516174] dib0700: RC Query Failed
[  417.516180] dvb-usb: error while querying for an remote control event.
[  422.568114] dib0700: RC Query Failed
[  422.568120] dvb-usb: error while querying for an remote control event.
[  427.620068] dib0700: RC Query Failed
[  427.620074] dvb-usb: error while querying for an remote control event.
[  432.672143] dib0700: RC Query Failed
[  432.672148] dvb-usb: error while querying for an remote control event.
[  437.724095] dib0700: RC Query Failed
[  437.724102] dvb-usb: error while querying for an remote control event.
[  442.776044] dib0700: RC Query Failed
[  442.776049] dvb-usb: error while querying for an remote control event.
[  447.828125] dib0700: RC Query Failed
[  447.828132] dvb-usb: error while querying for an remote control event.
[  452.880082] dib0700: RC Query Failed
[  452.880088] dvb-usb: error while querying for an remote control event.
[  457.932154] dib0700: RC Query Failed
[  457.932160] dvb-usb: error while querying for an remote control event.
[  462.984104] dib0700: RC Query Failed
[  462.984110] dvb-usb: error while querying for an remote control event.
[  468.036059] dib0700: RC Query Failed
[  468.036065] dvb-usb: error while querying for an remote control event.
[  473.088133] dib0700: RC Query Failed
[  473.088139] dvb-usb: error while querying for an remote control event.
[  478.140086] dib0700: RC Query Failed
[  478.140093] dvb-usb: error while querying for an remote control event.
[  483.192164] dib0700: RC Query Failed
[  483.192170] dvb-usb: error while querying for an remote control event.
[  488.248236] dib0700: RC Query Failed
[  488.248241] dvb-usb: error while querying for an remote control event.
[  493.299446] dib0700: RC Query Failed
[  493.299452] dvb-usb: error while querying for an remote control event.
[  498.356148] MT2266 I2C read failed
[  498.356153] dib0700: RC Query Failed
[  498.356157] dvb-usb: error while querying for an remote control event.
[  503.408105] dib0700: RC Query Failed
[  503.408113] dvb-usb: error while querying for an remote control event.
[  508.460052] dib0700: RC Query Failed
[  508.460059] dvb-usb: error while querying for an remote control event.
[  513.512131] dib0700: RC Query Failed
[  513.512137] dvb-usb: error while querying for an remote control event.
[  518.564082] dib0700: RC Query Failed
[  518.564088] dvb-usb: error while querying for an remote control event.
[  523.616160] dib0700: RC Query Failed
[  523.616166] dvb-usb: error while querying for an remote control event.
[  528.668111] dib0700: RC Query Failed
[  528.668117] dvb-usb: error while querying for an remote control event.
[  533.720073] dib0700: RC Query Failed
[  533.720079] dvb-usb: error while querying for an remote control event.
[  538.772150] dib0700: RC Query Failed
[  538.772157] dvb-usb: error while querying for an remote control event.
[  543.824093] dib0700: RC Query Failed
[  543.824100] dvb-usb: error while querying for an remote control event.
[  543.839653] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  543.839659] usb 1-1: USB disconnect, address 2
[  543.847396] MT2266 I2C write failed
[  543.847400] MT2266 I2C write failed
[  548.828046] dvb-usb: error while stopping stream.
[  548.828841] dvb-usb: Pinnacle PCTV 2000e successfully deinitialized and disconnected.
[  549.068028] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  549.201103] usb 1-1: configuration #1 chosen from 1 choice
[  549.201382] dvb-usb: found a 'Pinnacle PCTV 2000e' in warm state.
[  549.201415] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  549.201630] DVB: registering new adapter (Pinnacle PCTV 2000e)
[  549.343176] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[  549.344922] MT2266: successfully identified
[  549.473461] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  549.473688] DVB: registering new adapter (Pinnacle PCTV 2000e)
[  549.555238] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[  549.556985] MT2266: successfully identified
[  549.686860] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/input/input9
[  549.687959] dvb-usb: schedule remote query interval to 50 msecs.
[  549.687964] dvb-usb: Pinnacle PCTV 2000e successfully initialized and connected.
[  554.736103] dib0700: RC Query Failed
[  554.736109] dvb-usb: error while querying for an remote control event.
[  559.788055] dib0700: RC Query Failed
[  559.788062] dvb-usb: error while querying for an remote control event.
[  564.840132] dib0700: RC Query Failed
[  564.840139] dvb-usb: error while querying for an remote control event.
[  569.896088] dib0700: RC Query Failed
[  569.896095] dvb-usb: error while querying for an remote control event.

---

### Post by papapep on 2009-07-13
Si us plau, venusfenix (i qualsevol altre que tingui tentacions de fer-ho), quan tinguis tant de contingut per a posar a un post, cal adjuntar un arxiu de text i no posar-ho al fòrum directament, si no, com ja veus, es fa tot plegat bastant intractable. :)

---

### Post by PatrickVogeli on 2009-07-13
Diria que tot sembla correcte, t'el detecta i si et deixa escanejar doncs diria que esta tot OK.

Però... segons he llegit, en els drivers per a linux no esta suportada la funció diversity, que es la que fa servir les 2 antenes per aconseguir un senyal millor, i linux ho veu com un aparell amb 2 sintonitzadors. Per tant, es possible que degut a això no et trovi els canals.

Per tant, si no ho has fet, et recomanaria provar a connectar l'aparell a un endoll de tv normal. Si ja ho has fet, doncs ho sento. Fins aqui he arribat, no se que més dir-te.

Salut!

---

### Post by venusfenix on 2009-07-14
buenas, i moltes merces,

començo a trobar canals, el stick que tinc te dues antenes pero perque te 2 TDT's.
pero alguna senyal agafo i començo a veure canals. 
ara es qüestió de temps que es vegim totes, necesito un fitxer de canals .cfg pero no sé on buscar-ne, i quan millori el temps, o potser quan empitjori.

moltes merces!!!

---

