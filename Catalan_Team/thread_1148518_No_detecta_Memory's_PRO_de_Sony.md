---
title: "No detecta Memory's PRO de Sony"
date: 2009-05-04
forum: Catalan Team
---

### Post by karto_on on 2009-05-04
hola a tothom!
m'acabo d'instal.lar l'ubuntu 9.04. tinc un Vaio VGN-FZ31E.
El meu problema es que tinc dos lectors de targetes integrats, un per a les SD i un altre per a les de sony les PRO i les antigues MS.
el tema es que les SD me les detecta sense problemes pero les PRO no... algu sap si necessito instal.lar algun driver i d'on el puc treure?
moltes gràcies!!

adjunto lspci:
kartoon@kartoon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by iSoc on 2009-05-09
Hola, company a mi també em passa el mateix tinc un **Thosiba satelite u-400 **i també em funcionen les SD sense problemes però les mmc no hi ha manera. Ja vinc d'intrepid sense poder fer anar les mmc. 

El meu lspci:
```
yoyo@yoyo-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) 
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16) 
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100 
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) 
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) 
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)    
 
```lsusb:
```
Bus 008 Device 005: ID 04f2:b064 Chicony Electronics Co., Ltd 
Bus 008 Device 002: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub    
```Aquest son els moduls que tinc el problema.

```
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) 
 0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)    
```Aixi que estic com tu no puc fer servir les meves targetes de la camara de vídeo ni de fotos que fan servir targetes mmc.

Un salut.

---

### Post by PatrickVogeli on 2009-05-09
Podrieu reiniciar el pc, esperar que estigui tot ben carregat, llavors insertar la tarjeta de sony, fer un dmesg i enganxar el contingut de l'ordre aqui?

---

### Post by iSoc on 2009-05-10
Hola bon dia aquí et deix-ho el meu dmesg a veure si veus alguna cosa. E reiniciat i posat la targeta tal com dius, després e fet el dmesg. Un salut.


```
[    0.000000] BIOS EBDA/lowmem at: 0009f400/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-12-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 (Ubuntu 2.6.28-12.43-generic)
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
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b76b1000 (usable)
[    0.000000]  BIOS-e820: 00000000b76b1000 - 00000000b76b7000 (reserved)
[    0.000000]  BIOS-e820: 00000000b76b7000 - 00000000b77ba000 (usable)
[    0.000000]  BIOS-e820: 00000000b77ba000 - 00000000b780f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b780f000 - 00000000b7908000 (usable)
[    0.000000]  BIOS-e820: 00000000b7908000 - 00000000b7b0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b0f000 - 00000000b7b18000 (usable)
[    0.000000]  BIOS-e820: 00000000b7b18000 - 00000000b7b1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b1f000 - 00000000b7b65000 (usable)
[    0.000000]  BIOS-e820: 00000000b7b65000 - 00000000b7b9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7b9f000 - 00000000b7be1000 (usable)
[    0.000000]  BIOS-e820: 00000000b7be1000 - 00000000b7bfd000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7bfd000 - 00000000b7c00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xb7c00 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b76b1000 (usable)
[    0.000000]  modified: 00000000b76b1000 - 00000000b76b7000 (reserved)
[    0.000000]  modified: 00000000b76b7000 - 00000000b77ba000 (usable)
[    0.000000]  modified: 00000000b77ba000 - 00000000b780f000 (reserved)
[    0.000000]  modified: 00000000b780f000 - 00000000b7908000 (usable)
[    0.000000]  modified: 00000000b7908000 - 00000000b7b0f000 (reserved)
[    0.000000]  modified: 00000000b7b0f000 - 00000000b7b18000 (usable)
[    0.000000]  modified: 00000000b7b18000 - 00000000b7b1f000 (reserved)
[    0.000000]  modified: 00000000b7b1f000 - 00000000b7b65000 (usable)
[    0.000000]  modified: 00000000b7b65000 - 00000000b7b9f000 (ACPI NVS)
[    0.000000]  modified: 00000000b7b9f000 - 00000000b7be1000 (usable)
[    0.000000]  modified: 00000000b7be1000 - 00000000b7bfd000 (ACPI data)
[    0.000000]  modified: 00000000b7bfd000 - 00000000b7c00000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef119
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fac119
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef118 to 0087b000 - 00fac118
[    0.000000] ACPI: RSDP 000F6F30, 0024 (r2 TOSQCI)
[    0.000000] ACPI: XSDT B7BF2A62, 007C (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: FACP B7BE5000, 00F4 (r3 T0SQCI TOSQCI00  6040000 ALAN        1)
[    0.000000] ACPI: DSDT B7BE6000, 9F1A (r2 TOSQCI CANTIGA   6040000 INTL 20061109)
[    0.000000] ACPI: FACS B7B9EFC0, 0040
[    0.000000] ACPI: APIC B7BFCD1E, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET B7BFCD86, 0038 (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG B7BFCDBE, 003C (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
[    0.000000] ACPI: APIC B7BFCDFA, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT B7BFCE62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC B7BFCE8A, 0176 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: SSDT B7BF2B06, 0196 (r1 SataRe SataAhci     1000 INTL 20061109)
[    0.000000] ACPI: SSDT B7BE4000, 0655 (r1  PmRef    CpuPm     3000 INTL 20061109)
[    0.000000] ACPI: SSDT B7BE3000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20061109)
[    0.000000] ACPI: SSDT B7BE2000, 020F (r1  PmRef    ApTst     3000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2056MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fac119]      NEW RAMDISK ==> [000087b000 - 0000fac119]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f6ff0] 000f6ff0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000b7c00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[10] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000b76b1
[    0.000000]     0: 0x000b76b7 -> 0x000b77ba
[    0.000000]     0: 0x000b780f -> 0x000b7908
[    0.000000]     0: 0x000b7b0f -> 0x000b7b18
[    0.000000]     0: 0x000b7b1f -> 0x000b7b65
[    0.000000]     0: 0x000b7b9f -> 0x000b7be1
[    0.000000]     0: 0x000b7bfd -> 0x000b7c00
[    0.000000] On node 0 totalpages: 751814
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4113 pages used for memmap
[    0.000000]   HighMem zone: 521522 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b7c00000:48400000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 745933
[    0.000000] Kernel command line: root=UUID=c43266e2-3c99-45cb-9fd1-91e1ca916af1 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2527.301 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15052800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2952160k/3010560k available (4110k kernel code, 54232k reserved, 2197k data, 532k init, 2102540k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.60 BogoMIPS (lpj=10109204)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018024] ACPI: Core revision 20080926
[    0.021239] ACPI: Checking initramfs for custom DSDT
[    0.260418] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.301149] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.304001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5053.96 BogoMIPS (lpj=10107938)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.388821] CPU1: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.388834] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.392030] Brought up 2 CPUs
[    0.392032] Total of 2 processors activated (10108.57 BogoMIPS).
[    0.392080] CPU0 attaching sched-domain:
[    0.392082]  domain 0: span 0-1 level MC
[    0.392084]   groups: 0 1
[    0.392089] CPU1 attaching sched-domain:
[    0.392090]  domain 0: span 0-1 level MC
[    0.392092]   groups: 1 0
[    0.392147] net_namespace: 776 bytes
[    0.392147] Booting paravirtualized kernel on bare hardware
[    0.392249] Time:  7:20:22  Date: 05/10/09
[    0.392249] regulator: core version 0.5
[    0.392249] NET: Registered protocol family 16
[    0.392249] EISA bus registered
[    0.392249] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.392249] ACPI: bus type pci registered
[    0.392249] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.392249] PCI: Not using MMCONFIG.
[    0.392517] PCI: PCI BIOS revision 3.00 entry at 0xfdc31, last bus=10
[    0.392518] PCI: Using configuration type 1 for base access
[    0.393152] ACPI: EC: Look up EC in DSDT
[    0.399741] ACPI: BIOS _OSI(Linux) query ignored
[    0.406479] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.904005] ACPI: EC: missing confirmations, switch off interrupt mode.
[    0.920105] ACPI: Interpreter enabled
[    0.920108] ACPI: (supports S0 S3 S4 S5)
[    0.920123] ACPI: Using IOAPIC for interrupt routing
[    0.920176] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.922497] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.922499] PCI: Using MMCONFIG for extended config space
[    0.929795] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.929797] ACPI: EC: driver started in poll mode
[    0.929926] ACPI: No dock devices found.
[    0.929996] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.930063] pci 0000:00:02.0: reg 10 64bit mmio: [0xf4000000-0xf43fffff]
[    0.930069] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.930072] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.930099] pci 0000:00:02.1: reg 10 64bit mmio: [0xf4400000-0xf44fffff]
[    0.930208] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.930283] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.930361] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.930438] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf4a04800-0xf4a04bff]
[    0.930483] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.930488] pci 0000:00:1a.7: PME# disabled
[    0.930541] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf4800000-0xf4803fff]
[    0.930579] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.930583] pci 0000:00:1b.0: PME# disabled
[    0.930644] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.930648] pci 0000:00:1c.0: PME# disabled
[    0.930717] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.930721] pci 0000:00:1c.4: PME# disabled
[    0.930786] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.930790] pci 0000:00:1c.5: PME# disabled
[    0.930866] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.930955] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.931039] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.931118] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4a04c00-0xf4a04fff]
[    0.931162] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.931167] pci 0000:00:1d.7: PME# disabled
[    0.931377] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.931384] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.931391] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.931398] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.931405] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.931413] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf4a04000-0xf4a047ff]
[    0.931431] pci 0000:00:1f.2: PME# supported from D3hot
[    0.931436] pci 0000:00:1f.2: PME# disabled
[    0.931472] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.931490] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.931567] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.931571] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.931579] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.931640] pci 0000:07:00.0: reg 10 64bit mmio: [0x000000-0x003fff]
[    0.931649] pci 0000:07:00.0: reg 18 io port: [0x00-0xff]
[    0.931680] pci 0000:07:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.931693] pci 0000:07:00.0: supports D1 D2
[    0.931695] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.931700] pci 0000:07:00.0: PME# disabled
[    0.931766] pci 0000:00:1c.4: bridge io port: [0x00-0xfff]
[    0.931770] pci 0000:00:1c.4: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.931777] pci 0000:00:1c.4: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.931862] pci 0000:08:00.0: reg 10 64bit mmio: [0x000000-0x001fff]
[    0.931932] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.931938] pci 0000:08:00.0: PME# disabled
[    0.932015] pci 0000:00:1c.5: bridge io port: [0x00-0xfff]
[    0.932019] pci 0000:00:1c.5: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.932026] pci 0000:00:1c.5: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.932068] pci 0000:0a:01.0: reg 10 32bit mmio: [0xff501000-0xff501fff]
[    0.932075] pci 0000:0a:01.0: reg 14 32bit mmio: [0xf4700000-0xf47007ff]
[    0.932113] pci 0000:0a:01.0: supports D1 D2
[    0.932115] pci 0000:0a:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.932119] pci 0000:0a:01.0: PME# disabled
[    0.932164] pci 0000:0a:01.2: reg 10 32bit mmio: [0xf4700800-0xf47008ff]
[    0.932213] pci 0000:0a:01.2: supports D1 D2
[    0.932215] pci 0000:0a:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.932220] pci 0000:0a:01.2: PME# disabled
[    0.932263] pci 0000:0a:01.3: reg 10 32bit mmio: [0xf4702000-0xf4702fff]
[    0.932313] pci 0000:0a:01.3: supports D1 D2
[    0.932314] pci 0000:0a:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.932319] pci 0000:0a:01.3: PME# disabled
[    0.932378] pci 0000:00:1e.0: transparent bridge
[    0.932385] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4700000-0xf47fffff]
[    0.932416] bus 00 -> node 0
[    0.932423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.932644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.932767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.932877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.944451] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.944560] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.944668] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[    0.944775] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.944882] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.944989] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.945096] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.945203] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.945543] ACPI: WMI: Mapper loaded
[    0.945566] SCSI subsystem initialized
[    0.945566] libata version 3.00 loaded.
[    0.945566] usbcore: registered new interface driver usbfs
[    0.945566] usbcore: registered new interface driver hub
[    0.945566] usbcore: registered new device driver usb
[    0.945566] PCI: Using ACPI for IRQ routing
[    0.945566] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.945566] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.945566] pci 0000:00:1c.0: BAR 9: can't allocate resource
[    0.945566] pci 0000:00:1c.4: BAR 7: can't allocate resource
[    0.945566] pci 0000:00:1c.4: BAR 8: can't allocate resource
[    0.945566] pci 0000:00:1c.4: BAR 9: can't allocate resource
[    0.945566] pci 0000:00:1c.5: BAR 7: can't allocate resource
[    0.945566] pci 0000:00:1c.5: BAR 8: can't allocate resource
[    0.945566] pci 0000:00:1c.5: BAR 9: can't allocate resource
[    0.948011] Bluetooth: Core ver 2.13
[    0.948014] NET: Registered protocol family 31
[    0.948014] Bluetooth: HCI device and connection manager initialized
[    0.948014] Bluetooth: HCI socket layer initialized
[    0.948015] NET: Registered protocol family 8
[    0.948016] NET: Registered protocol family 20
[    0.948024] NetLabel: Initializing
[    0.948026] NetLabel:  domain hash size = 128
[    0.948027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.948037] NetLabel:  unlabeled traffic allowed by default
[    0.948048] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.948052] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.952050] AppArmor: AppArmor Filesystem Enabled
[    0.956009] Switched to high resolution mode on CPU 0
[    0.956865] Switched to high resolution mode on CPU 1
[    0.956872] pnp: PnP ACPI init
[    0.956878] ACPI: bus type pnp registered
[    0.957752] pnp 00:04: io resource (0x2e-0x2f) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957755] pnp 00:04: io resource (0x4e-0x4f) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957757] pnp 00:04: io resource (0x61-0x61) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957759] pnp 00:04: io resource (0x63-0x63) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957761] pnp 00:04: io resource (0x65-0x65) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957763] pnp 00:04: io resource (0x67-0x67) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957765] pnp 00:04: io resource (0x68-0x68) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957767] pnp 00:04: io resource (0x6c-0x6c) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957769] pnp 00:04: io resource (0x70-0x70) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957771] pnp 00:04: io resource (0x80-0x80) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957773] pnp 00:04: io resource (0x92-0x92) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.957776] pnp 00:04: io resource (0xb2-0xb3) overlaps 0000:07:00.0 BAR 2 (0x0-0xff), disabling
[    0.958988] pnp: PnP ACPI: found 9 devices
[    0.958990] ACPI: ACPI bus type pnp unregistered
[    0.958992] PnPBIOS: Disabled by ACPI PNP
[    0.959000] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.959005] system 00:04: ioport range 0x3e0-0x3e1 has been reserved
[    0.959007] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.959008] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.959010] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.959012] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.959014] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.959016] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.959018] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.959020] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.959025] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.959027] system 00:08: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.959029] system 00:08: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.959031] system 00:08: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.959033] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
[    0.959036] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.993702] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.993704] pci 0000:00:1c.0:   IO window: disabled
[    0.993709] pci 0000:00:1c.0:   MEM window: disabled
[    0.993713] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.993731] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.993735] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.993740] pci 0000:00:1c.4:   MEM window: 0xb8000000-0xb80fffff
[    0.993745] pci 0000:00:1c.4:   PREFETCH window: 0x000000b8100000-0x000000b81fffff
[    0.993762] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.993764] pci 0000:00:1c.5:   IO window: disabled
[    0.993769] pci 0000:00:1c.5:   MEM window: 0xb8200000-0xb82fffff
[    0.993773] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.993779] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.993781] pci 0000:00:1e.0:   IO window: disabled
[    0.993786] pci 0000:00:1e.0:   MEM window: 0xf4700000-0xf47fffff
[    0.993790] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.993804] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.993810] pci 0000:00:1c.0: setting latency timer to 64
[    0.993817] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.993820] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.993825] pci 0000:00:1c.4: setting latency timer to 64
[    0.993832] pci 0000:00:1c.5: enabling device (0000 -> 0002)
[    0.993836] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.993842] pci 0000:00:1c.5: setting latency timer to 64
[    0.993848] pci 0000:00:1e.0: setting latency timer to 64
[    0.993851] bus: 00 index 0 io port: [0x00-0xffff]
[    0.993853] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.993855] bus: 02 index 0 mmio: [0x0-0xfff]
[    0.993856] bus: 02 index 1 mmio: [0x0-0xfffff]
[    0.993858] bus: 02 index 2 mmio: [0x0-0xfffff]
[    0.993859] bus: 02 index 3 mmio: [0x0-0x0]
[    0.993861] bus: 07 index 0 io port: [0x2000-0x2fff]
[    0.993862] bus: 07 index 1 mmio: [0xb8000000-0xb80fffff]
[    0.993864] bus: 07 index 2 mmio: [0xb8100000-0xb81fffff]
[    0.993865] bus: 07 index 3 mmio: [0x0-0x0]
[    0.993867] bus: 08 index 0 mmio: [0x0-0xfff]
[    0.993868] bus: 08 index 1 mmio: [0xb8200000-0xb82fffff]
[    0.993870] bus: 08 index 2 mmio: [0x0-0xfffff]
[    0.993871] bus: 08 index 3 mmio: [0x0-0x0]
[    0.993873] bus: 0a index 0 mmio: [0x0-0x0]
[    0.993874] bus: 0a index 1 mmio: [0xf4700000-0xf47fffff]
[    0.993876] bus: 0a index 2 mmio: [0x0-0x0]
[    0.993877] bus: 0a index 3 io port: [0x00-0xffff]
[    0.993879] bus: 0a index 4 mmio: [0x000000-0xffffffff]
[    0.993884] NET: Registered protocol family 2
[    1.005037] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.005211] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.005453] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.005578] TCP: Hash tables configured (established 131072 bind 65536)
[    1.005580] TCP reno registered
[    1.009041] NET: Registered protocol family 1
[    1.009122] checking if image is initramfs... it is
[    1.484609] Freeing initrd memory: 7364k freed
[    1.484641] Simple Boot Flag at 0x36 set to 0x1
[    1.484780] cpufreq: No nForce2 chipset.
[    1.484883] audit: initializing netlink socket (disabled)
[    1.484902] type=2000 audit(1241940022.484:1): initialized
[    1.490613] highmem bounce pool size: 64 pages
[    1.490616] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.491592] VFS: Disk quotas dquot_6.5.1
[    1.491637] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.492084] fuse init (API version 7.10)
[    1.492146] msgmni has been set to 1675
[    1.492277] alg: No test for stdrng (krng)
[    1.492286] io scheduler noop registered
[    1.492287] io scheduler anticipatory registered
[    1.492289] io scheduler deadline registered
[    1.492299] io scheduler cfq registered (default)
[    1.492308] pci 0000:00:02.0: Boot video device
[    1.494939] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.494985] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.495019] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.495033] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.495043] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.495052] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.495116] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.495160] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.495189] pcieport-driver 0000:00:1c.4: irq 2302 for MSI/MSI-X
[    1.495203] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.495212] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.495221] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.495285] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.495329] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.495358] pcieport-driver 0000:00:1c.5: irq 2301 for MSI/MSI-X
[    1.495373] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.495382] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.495391] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.495461] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.495535] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.497877] ACPI: AC Adapter [ACAD] (off-line)
[    1.497939] ACPI: Battery Slot [BAT1] (battery absent)
[    1.497991] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.497993] ACPI: Power Button (FF) [PWRF]
[    1.498033] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.498035] ACPI: Power Button (CM) [PWRB]
[    1.498066] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.498196] ACPI: Lid Switch [LID]
[    1.498770] ACPI: SSDT B7B1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[    1.499135] ACPI: SSDT B7B185A0, 0537 (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
[    1.500985] Monitor-Mwait will be used to enter C-1 state
[    1.500987] Monitor-Mwait will be used to enter C-2 state
[    1.500990] Monitor-Mwait will be used to enter C-3 state
[    1.501000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.501019] processor ACPI_CPU:00: registered as cooling_device0
[    1.501021] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.501375] ACPI: SSDT B7B19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20061109)
[    1.501747] ACPI: SSDT B7B19F20, 008D (r1  PmRef    ApCst     3000 INTL 20061109)
[    1.502670] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.502684] processor ACPI_CPU:01: registered as cooling_device1
[    1.502687] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.507783] thermal LNXTHERM:01: registered as thermal_zone0
[    1.509506] ACPI: Thermal Zone [THRM] (32 C)
[    1.509543] isapnp: Scanning for PnP cards...
[    1.863300] isapnp: No Plug & Play device found
[    1.869186] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.869940] brd: module loaded
[    1.870165] loop: module loaded
[    1.870212] Fixed MDIO Bus: probed
[    1.870216] PPP generic driver version 2.4.2
[    1.870257] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.870277] Driver 'sd' needs updating - please use bus_type methods
[    1.870284] Driver 'sr' needs updating - please use bus_type methods
[    1.870313] ahci 0000:00:1f.2: version 3.0
[    1.870326] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.870357] ahci 0000:00:1f.2: irq 2300 for MSI/MSI-X
[    1.870441] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.870444] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems 
[    1.870449] ahci 0000:00:1f.2: setting latency timer to 64
[    1.870713] scsi0 : ahci
[    1.870769] scsi1 : ahci
[    1.870808] scsi2 : ahci
[    1.870850] scsi3 : ahci
[    1.870891] scsi4 : ahci
[    1.870930] scsi5 : ahci
[    1.871013] ata1: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04100 irq 2300
[    1.871016] ata2: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04180 irq 2300
[    1.871018] ata3: DUMMY
[    1.871019] ata4: DUMMY
[    1.871021] ata5: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04300 irq 2300
[    1.871024] ata6: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04380 irq 2300
[    2.188019] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.188561] ACPI Warning (nspredef-0852): \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
[    2.188566] ata1.00: _GTF unexpected object type 0x1
[    2.263978] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV010M, max UDMA/100
[    2.263980] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.264841] ata1.00: _GTF unexpected object type 0x1
[    2.264960] ata1.00: configured for UDMA/100
[    2.988016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.989685] ata2.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.50, max UDMA/33
[    2.991721] ata2.00: configured for UDMA/33
[    3.312015] ata5: SATA link down (SStatus 0 SControl 300)
[    3.632015] ata6: SATA link down (SStatus 0 SControl 300)
[    3.632098] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    3.632163] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.632175] sd 0:0:0:0: [sda] Write Protect is off
[    3.632177] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.632195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.632239] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.632249] sd 0:0:0:0: [sda] Write Protect is off
[    3.632251] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.632269] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.632272]  sda: sda1 sda2 sda4 < sda5 sda6 >
[    3.741134] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.741163] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.742908] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.50 PQ: 0 ANSI: 5
[    3.746401] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.746403] Uniform CD-ROM driver Revision: 3.20
[    3.746463] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.746490] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.746992] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.747007] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.747016] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.747019] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.747059] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.750958] ehci_hcd 0000:00:1a.7: debug port 1
[    3.750964] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.750975] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4a04800
[    3.764007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.764054] usb usb1: configuration #1 chosen from 1 choice
[    3.764073] hub 1-0:1.0: USB hub found
[    3.764079] hub 1-0:1.0: 6 ports detected
[    3.764162] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.764171] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.764174] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.764206] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.768107] ehci_hcd 0000:00:1d.7: debug port 1
[    3.768112] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.768123] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4a04c00
[    3.784007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.784045] usb usb2: configuration #1 chosen from 1 choice
[    3.784065] hub 2-0:1.0: USB hub found
[    3.784070] hub 2-0:1.0: 6 ports detected
[    3.784144] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.784156] uhci_hcd: USB Universal Host Controller Interface driver
[    3.784170] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.784176] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.784178] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.784210] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.784241] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.784295] usb usb3: configuration #1 chosen from 1 choice
[    3.784313] hub 3-0:1.0: USB hub found
[    3.784318] hub 3-0:1.0: 2 ports detected
[    3.784383] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.784389] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.784391] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.784420] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.784452] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.784509] usb usb4: configuration #1 chosen from 1 choice
[    3.784527] hub 4-0:1.0: USB hub found
[    3.784532] hub 4-0:1.0: 2 ports detected
[    3.784594] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.784600] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.784602] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.784633] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.784656] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    3.784710] usb usb5: configuration #1 chosen from 1 choice
[    3.784728] hub 5-0:1.0: USB hub found
[    3.784732] hub 5-0:1.0: 2 ports detected
[    3.784793] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.784798] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.784801] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.784834] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.784857] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    3.784915] usb usb6: configuration #1 chosen from 1 choice
[    3.784933] hub 6-0:1.0: USB hub found
[    3.784938] hub 6-0:1.0: 2 ports detected
[    3.785002] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.785007] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.785010] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.785039] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.785062] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    3.785114] usb usb7: configuration #1 chosen from 1 choice
[    3.785133] hub 7-0:1.0: USB hub found
[    3.785138] hub 7-0:1.0: 2 ports detected
[    3.785198] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.785203] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.785206] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.785235] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.785264] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    3.785322] usb usb8: configuration #1 chosen from 1 choice
[    3.785339] hub 8-0:1.0: USB hub found
[    3.785344] hub 8-0:1.0: 2 ports detected
[    3.785442] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2A] at 0x60,0x64 irq 1,12
[    3.787332] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.788441] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.788445] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.788447] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.788449] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.788450] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.792025] mice: PS/2 mouse device common for all mice
[    3.808055] rtc_cmos 00:05: RTC can wake from S4
[    3.808077] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.808104] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.808143] device-mapper: uevent: version 1.0.3
[    3.808208] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.808259] device-mapper: multipath: version 1.0.5 loaded
[    3.808261] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.808313] EISA: Probing bus 0 at eisa.0
[    3.808319] Cannot allocate resource for EISA slot 1
[    3.808320] Cannot allocate resource for EISA slot 2
[    3.808342] EISA: Detected 0 cards.
[    3.808424] cpuidle: using governor ladder
[    3.808508] cpuidle: using governor menu
[    3.808875] TCP cubic registered
[    3.808946] NET: Registered protocol family 10
[    3.809260] lo: Disabled Privacy Extensions
[    3.809506] NET: Registered protocol family 17
[    3.809518] Bluetooth: L2CAP ver 2.11
[    3.809520] Bluetooth: L2CAP socket layer initialized
[    3.809522] Bluetooth: SCO (Voice Link) ver 0.6
[    3.809523] Bluetooth: SCO socket layer initialized
[    3.809546] Bluetooth: RFCOMM socket layer initialized
[    3.809548] Marking TSC unstable due to TSC halts in idle
[    3.809553] Bluetooth: RFCOMM TTY layer initialized
[    3.809554] Bluetooth: RFCOMM ver 1.10
[    3.810146] Using IPI No-Shortcut mode
[    3.810194] registered taskstats version 1
[    3.810274]   Magic number: 9:754:318
[    3.810281] tty tty43: hash matches
[    3.810322] rtc_cmos 00:05: setting system clock to 2009-05-10 07:20:26 UTC (1241940026)
[    3.810324] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.810326] EDD information not available.
[    3.810541] Freeing unused kernel memory: 532k freed
[    3.810633] Write protecting the kernel text: 4112k
[    3.810667] Write protecting the kernel read-only data: 1524k
[    3.837637] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.953585] sky2 driver version 1.22
[    3.953620] sky2 0000:07:00.0: enabling device (0000 -> 0003)
[    3.953628] sky2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.953646] sky2 0000:07:00.0: setting latency timer to 64
[    3.953684] sky2 0000:07:00.0: Yukon-2 Extreme chip revision 2
[    3.953927] sky2 0000:07:00.0: irq 2299 for MSI/MSI-X
[    3.954478] sky2 eth0: addr 00:23:8b:2b:35:f8
[    3.996327] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.046080] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[ff501000-ff5017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.324022] hub 2-0:1.0: unable to enumerate USB device on port 3
[    4.436016] usb 2-4: new high speed USB device using ehci_hcd and address 5
[    4.500010] Clocksource tsc unstable (delta = -140906501 ns)
[    4.552956] PM: Starting manual resume from disk
[    4.552958] PM: Resume from partition 8:2
[    4.552959] PM: Checking hibernation image.
[    4.553123] PM: Resume from disk failed.
[    4.568748] EXT4-fs: barriers enabled
[    4.582715] kjournald2 starting.  Commit interval 5 seconds
[    4.582753] EXT4-fs: delayed allocation enabled
[    4.582756] EXT4-fs: file extents enabled
[    4.583156] EXT4-fs: mballoc enabled
[    4.583158] EXT4-fs: mounted filesystem with ordered data mode.
[    4.612653] usb 2-4: configuration #1 chosen from 1 choice
[    4.852096] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    5.027976] usb 6-1: configuration #1 chosen from 1 choice
[    5.268247] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    5.316464] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400014475ec]
[    5.431974] usb 6-2: configuration #1 chosen from 1 choice
[    8.965615] udev: starting version 141
[    9.181317] acpi device:05: registered as cooling_device2
[    9.181561] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[    9.184334] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.622669] usbcore: registered new interface driver hiddev
[    9.635177] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input6
[    9.635436] generic-usb 0003:046D:C019.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    9.635450] usbcore: registered new interface driver usbhid
[    9.635467] usbhid: v2.6:USB HID core driver
[    9.677986] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    9.703641] iTCO_vendor_support: vendor-support=0
[    9.704742] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.704850] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[    9.704890] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.759398] Linux agpgart interface v0.103
[    9.772413] Linux video capture interface: v2.00
[    9.804481] sdhci: Secure Digital Host Controller Interface driver
[    9.804482] sdhci: Copyright(c) Pierre Ossman
[    9.805660] sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)
[    9.805676] sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.805695] mmc0: Unknown controller version (2). You may experience problems.
[    9.805752] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA
[    9.815315] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.906078] cfg80211: Calling CRDA to update world regulatory domain
[    9.907858] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    9.909447] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    9.912194] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    9.929111] uvcvideo: Found UVC 1.00 device CNA7137 (04f2:b064)
[    9.930631] input: CNA7137 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[    9.933150] usbcore: registered new interface driver uvcvideo
[    9.933178] USB Video Class driver (v0.1.0)
[   10.040855] cfg80211: World regulatory domain updated:
[   10.040858]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.040860]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.040862]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.040864]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.040865]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.040867]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.262455] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   10.262457] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   10.262510] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[   10.262517] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.262528] iwlagn 0000:08:00.0: setting latency timer to 64
[   10.262571] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   10.285225] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.285289] iwlagn 0000:08:00.0: irq 2298 for MSI/MSI-X
[   10.286147] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.491736] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   10.516922] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   10.552730] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.552786] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.770080] lp: driver loaded but no devices found
[   10.821296] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   10.836610] EXT4 FS on sda1, internal journal on sda1:8
[   11.118955] EXT4-fs: barriers enabled
[   11.129800] kjournald2 starting.  Commit interval 5 seconds
[   11.130003] EXT4 FS on sda6, internal journal on sda6:8
[   11.130006] EXT4-fs: delayed allocation enabled
[   11.130008] EXT4-fs: file extents enabled
[   11.131760] EXT4-fs: mballoc enabled
[   11.131762] EXT4-fs: mounted filesystem with ordered data mode.
[   11.283174] type=1505 audit(1241940033.970:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2107
[   11.314853] type=1505 audit(1241940034.002:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2111
[   11.314909] type=1505 audit(1241940034.002:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2111
[   11.314938] type=1505 audit(1241940034.002:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2111
[   11.314966] type=1505 audit(1241940034.002:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2111
[   11.402429] type=1505 audit(1241940034.090:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2116
[   11.402518] type=1505 audit(1241940034.090:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2116
[   11.420817] type=1505 audit(1241940034.106:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2120
[   14.443911] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   14.690811] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.690814] Bluetooth: BNEP filters: protocol multicast
[   14.727241] Registered led device: iwl-phy0:radio
[   14.727260] Registered led device: iwl-phy0:assoc
[   14.727281] Registered led device: iwl-phy0:RX
[   14.727298] Registered led device: iwl-phy0:TX
[   14.730897] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.745279] Bridge firewalling registered
[   15.678845] ppdev: user-space parallel port driver
[   16.372079] sky2 eth0: enabling interface
[   16.372224] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.369084] [drm] Initialized drm 1.1.0 20060810
[   17.381726] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.381730] pci 0000:00:02.0: setting latency timer to 64
[   17.381938] pci 0000:00:02.0: irq 2297 for MSI/MSI-X
[   17.381991] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   17.384014] [drm:i915_setparam] *ERROR* unknown parameter 4
[  583.291510] Registered led device: iwl-phy0:radio
[  583.291550] Registered led device: iwl-phy0:assoc
[  583.291586] Registered led device: iwl-phy0:RX
[  583.291622] Registered led device: iwl-phy0:TX
[  583.321678] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  583.536431] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  583.536461] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  583.538340] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  583.538783] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  583.539783] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  583.541476] wlan0: authenticated
[  583.541484] wlan0: associate with AP 00:03:c9:e6:b6:99
[  583.557152] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[  583.557160] wlan0: associated
[  583.562319] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  594.080559] wlan0: no IPv6 routers present
[  713.168718] usb 6-1: USB disconnect, address 2
[  725.052218] usb 3-1: new low speed USB device using uhci_hcd and address 2
[  725.226543] usb 3-1: configuration #1 chosen from 1 choice
[  725.253077] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input11
[  725.281149] generic-usb 0003:046D:C019.0002: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1/input0
[  805.453574] iwlagn: index 0 not used in uCode key table.
[  805.515976] Registered led device: iwl-phy0:radio
[  805.516815] Registered led device: iwl-phy0:assoc
[  805.516865] Registered led device: iwl-phy0:RX
[  805.516902] Registered led device: iwl-phy0:TX
[  805.539655] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  817.211629] iwlagn: index 0 not used in uCode key table.
[  817.332776] Registered led device: iwl-phy0:radio
[  817.332822] Registered led device: iwl-phy0:assoc
[  817.332858] Registered led device: iwl-phy0:RX
[  817.332893] Registered led device: iwl-phy0:TX
[  817.342596] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  817.366142] wlan0: deauthenticating by local choice (reason=3)
[  817.382434] iwlagn: index 0 not used in uCode key table.
[  817.540557] Registered led device: iwl-phy0:radio
[  817.541025] Registered led device: iwl-phy0:assoc
[  817.541072] Registered led device: iwl-phy0:RX
[  817.541111] Registered led device: iwl-phy0:TX
[  817.566047] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  818.683619] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  818.683653] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  818.687381] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  818.687799] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  818.688866] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  818.888545] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  819.088581] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  819.288604] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  828.689523] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  828.689618] iwlagn: index 0 not used in uCode key table.
[  828.888176] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  829.088626] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  829.288605] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  838.695391] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  838.701102] iwlagn: index 0 not used in uCode key table.
[  838.893580] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  839.092583] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  839.293581] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  848.701009] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  848.701454] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  848.708169] iwlagn: index 0 not used in uCode key table.
[  848.900612] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  849.100580] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  849.300604] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  854.255491] Registered led device: iwl-phy0:radio
[  854.255532] Registered led device: iwl-phy0:assoc
[  854.255568] Registered led device: iwl-phy0:RX
[  854.255602] Registered led device: iwl-phy0:TX
[  854.270890] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  854.316095] sky2 eth0: disabling interface
[  854.325703] sky2 eth0: enabling interface
[  854.326122] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  858.707023] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  858.707454] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  858.709858] iwlagn: index 0 not used in uCode key table.
[  858.904582] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  859.104584] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  859.304591] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  868.712243] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  868.717091] iwlagn: index 0 not used in uCode key table.
[  868.916063] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  869.112138] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  869.114337] wlan0 direct probe responded
[  869.114349] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  869.312602] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  869.317835] wlan0: authenticated
[  869.317848] wlan0: associate with AP 00:03:c9:e6:b6:99
[  869.516590] wlan0: associate with AP 00:03:c9:e6:b6:99
[  869.716085] wlan0: associate with AP 00:03:c9:e6:b6:99
[  869.729062] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[  869.729069] wlan0: associated
[  869.735077] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  872.724118] iwlagn: index 0 not used in uCode key table.
[  872.852811] Registered led device: iwl-phy0:radio
[  872.852853] Registered led device: iwl-phy0:assoc
[  872.852889] Registered led device: iwl-phy0:RX
[  872.852926] Registered led device: iwl-phy0:TX
[  872.952658] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  872.975658] wlan0: deauthenticating by local choice (reason=3)
[  872.995541] iwlagn: index 0 not used in uCode key table.
[  873.108473] Registered led device: iwl-phy0:radio
[  873.108537] Registered led device: iwl-phy0:assoc
[  873.108575] Registered led device: iwl-phy0:RX
[  873.108610] Registered led device: iwl-phy0:TX
[  873.137906] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  874.157083] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  874.168470] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  874.168891] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  874.368153] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  874.568164] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  874.768123] wlan0: authentication with AP 00:03:c9:e6:b6:99 timed out
[  884.153595] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  884.153633] iwlagn: index 0 not used in uCode key table.
[  884.154068] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  884.352189] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  884.552234] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  884.752041] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  894.159384] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  894.165295] iwlagn: index 0 not used in uCode key table.
[  894.356584] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  894.556579] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  894.757072] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  904.163578] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  904.169568] iwlagn: index 0 not used in uCode key table.
[  904.360640] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  904.560610] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  904.760335] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  914.168654] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[  914.172102] iwlagn: index 0 not used in uCode key table.
[  914.369077] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[  914.568124] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[  914.768640] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[  917.000201] Registered led device: iwl-phy0:radio
[  917.000241] Registered led device: iwl-phy0:assoc
[  917.000277] Registered led device: iwl-phy0:RX
[  917.000313] Registered led device: iwl-phy0:TX
[  917.026411] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  917.084038] iwlagn: index 0 not used in uCode key table.
[  917.210026] Registered led device: iwl-phy0:radio
[  917.210074] Registered led device: iwl-phy0:assoc
[  917.210111] Registered led device: iwl-phy0:RX
[  917.210152] Registered led device: iwl-phy0:TX
[  917.239213] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  918.269022] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  918.269078] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  918.271102] wlan0: authenticated
[  918.271109] wlan0: associate with AP 00:03:c9:e6:b6:99
[  918.271114] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  918.276951] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  918.277021] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  918.278915] wlan0: authenticated
[  918.278923] wlan0: associate with AP 00:03:c9:e6:b6:99
[  918.278928] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  918.283497] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  918.289550] wlan0: authenticated
[  918.289561] wlan0: associate with AP 00:03:c9:e6:b6:99
[  918.306146] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[  918.306154] wlan0: associated
[  918.311795] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  928.749056] wlan0: no IPv6 routers present
[  978.360727] wlan0 direct probe responded
[  978.360739] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[  978.367306] wlan0: authenticated
[  978.367314] wlan0: associate with AP 00:03:c9:e6:b6:99
[  978.385117] wlan0: RX ReassocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[  978.385125] wlan0: associated
[ 1098.517572] iwlagn: index 0 not used in uCode key table.
[ 1098.583434] Registered led device: iwl-phy0:radio
[ 1098.583479] Registered led device: iwl-phy0:assoc
[ 1098.583514] Registered led device: iwl-phy0:RX
[ 1098.583549] Registered led device: iwl-phy0:TX
[ 1098.616033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1110.596069] iwlagn: index 0 not used in uCode key table.
[ 1110.711812] Registered led device: iwl-phy0:radio
[ 1110.711853] Registered led device: iwl-phy0:assoc
[ 1110.711888] Registered led device: iwl-phy0:RX
[ 1110.711923] Registered led device: iwl-phy0:TX
[ 1110.729542] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1110.758046] wlan0: deauthenticating by local choice (reason=3)
[ 1110.776000] iwlagn: index 0 not used in uCode key table.
[ 1110.923496] Registered led device: iwl-phy0:radio
[ 1110.923538] Registered led device: iwl-phy0:assoc
[ 1110.923575] Registered led device: iwl-phy0:RX
[ 1110.923615] Registered led device: iwl-phy0:TX
[ 1110.941436] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1111.972634] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1111.972666] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1111.984193] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1112.182638] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1112.381556] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1112.580081] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[ 1121.979777] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1121.979872] iwlagn: index 0 not used in uCode key table.
[ 1122.176611] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1122.376603] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1122.378804] wlan0 direct probe responded
[ 1122.378817] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1122.381103] wlan0: authenticated
[ 1122.381115] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1122.387494] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[ 1122.387501] wlan0: associated
[ 1122.389267] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1132.484562] wlan0: no IPv6 routers present
[ 1247.321577] iwlagn: index 0 not used in uCode key table.
[ 1247.379927] Registered led device: iwl-phy0:radio
[ 1247.379967] Registered led device: iwl-phy0:assoc
[ 1247.380035] Registered led device: iwl-phy0:RX
[ 1247.380074] Registered led device: iwl-phy0:TX
[ 1247.398390] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1247.444080] sky2 eth0: disabling interface
[ 1247.453693] sky2 eth0: enabling interface
[ 1247.454110] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1258.280087] iwlagn: index 0 not used in uCode key table.
[ 1258.339448] Registered led device: iwl-phy0:radio
[ 1258.339487] Registered led device: iwl-phy0:assoc
[ 1258.339523] Registered led device: iwl-phy0:RX
[ 1258.339557] Registered led device: iwl-phy0:TX
[ 1258.359449] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1258.409083] sky2 eth0: disabling interface
[ 1258.418677] sky2 eth0: enabling interface
[ 1258.419096] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1373.433577] iwlagn: index 0 not used in uCode key table.
[ 1373.825175] Registered led device: iwl-phy0:radio
[ 1373.825217] Registered led device: iwl-phy0:assoc
[ 1373.825253] Registered led device: iwl-phy0:RX
[ 1373.825288] Registered led device: iwl-phy0:TX
[ 1373.860144] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1373.882696] wlan0: deauthenticating by local choice (reason=3)
[ 1373.899871] iwlagn: index 0 not used in uCode key table.
[ 1374.036720] Registered led device: iwl-phy0:radio
[ 1374.036767] Registered led device: iwl-phy0:assoc
[ 1374.036804] Registered led device: iwl-phy0:RX
[ 1374.036841] Registered led device: iwl-phy0:TX
[ 1374.049760] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1375.081282] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1375.081311] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1375.087033] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1375.087458] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1375.121181] wlan0: authenticated
[ 1375.121193] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1375.320604] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1375.342011] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[ 1375.342019] wlan0: associated
[ 1375.348405] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1386.169543] wlan0: no IPv6 routers present
[ 1401.797122] wlan0: deauthenticating by local choice (reason=3)
[ 1401.820047] iwlagn: index 0 not used in uCode key table.
[ 1410.591111] iwlagn: Radio Frequency Kill Switch is On:
[ 1410.591117] Kill switch must be turned off for wireless networking to work.
[ 1415.384042] atkbd.c: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[ 1415.384050] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 1415.394189] atkbd.c: Unknown key released (translated set 2, code 0xf0 on isa0060/serio0).
[ 1415.394197] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 1436.584564] Registered led device: iwl-phy0:radio
[ 1436.585055] Registered led device: iwl-phy0:assoc
[ 1436.585104] Registered led device: iwl-phy0:RX
[ 1436.585146] Registered led device: iwl-phy0:TX
[ 1436.613551] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1436.743967] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1436.743998] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1436.753601] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1436.753626] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1436.952113] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1436.952152] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1437.152177] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1437.152217] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1437.352578] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[ 1437.352591] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1439.792079] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1439.988608] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1440.188602] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1440.388610] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[ 1449.797374] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1449.800131] iwlagn: index 0 not used in uCode key table.
[ 1449.996584] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1450.196603] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1450.396577] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[ 1459.802895] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1459.803373] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1459.805173] iwlagn: index 0 not used in uCode key table.
[ 1459.807055] wlan0 direct probe responded
[ 1459.807063] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1460.005583] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1460.013551] wlan0: authenticated
[ 1460.013563] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1460.212580] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1460.412590] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1460.415766] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[ 1460.415775] wlan0: associated
[ 1460.421876] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1470.460556] wlan0: no IPv6 routers present
[ 1475.581183] wlan0: deauthenticating by local choice (reason=3)
[ 1475.604077] iwlagn: index 0 not used in uCode key table.
[ 1477.039372] Registered led device: iwl-phy0:radio
[ 1477.039413] Registered led device: iwl-phy0:assoc
[ 1477.039449] Registered led device: iwl-phy0:RX
[ 1477.039484] Registered led device: iwl-phy0:TX
[ 1477.058953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1484.848754] Registered led device: iwl-phy0:radio
[ 1484.848802] Registered led device: iwl-phy0:assoc
[ 1484.848839] Registered led device: iwl-phy0:RX
[ 1484.848873] Registered led device: iwl-phy0:TX
[ 1484.868826] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1484.975779] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1484.975792] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1485.069259] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1485.069682] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1485.268115] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1485.468579] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1485.668121] wlan0: direct probe to AP 00:03:c9:e6:b6:99 timed out
[ 1495.075678] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 1
[ 1495.080156] iwlagn: index 0 not used in uCode key table.
[ 1495.273139] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 2
[ 1495.473058] wlan0: direct probe to AP 00:03:c9:e6:b6:99 try 3
[ 1495.474998] wlan0 direct probe responded
[ 1495.475006] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1495.490596] wlan0: authenticated
[ 1495.490608] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1495.518980] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[ 1495.518988] wlan0: associated
[ 1495.523541] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1506.232544] wlan0: no IPv6 routers present
[ 1537.076309] iwlagn: index 0 not used in uCode key table.
[ 1537.139462] Registered led device: iwl-phy0:radio
[ 1537.139502] Registered led device: iwl-phy0:assoc
[ 1537.139539] Registered led device: iwl-phy0:RX
[ 1537.139574] Registered led device: iwl-phy0:TX
[ 1537.150663] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1537.212072] sky2 eth0: disabling interface
[ 1537.221820] sky2 eth0: enabling interface
[ 1537.222238] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1541.636124] iwlagn: index 0 not used in uCode key table.
[ 1541.743341] Registered led device: iwl-phy0:radio
[ 1541.743382] Registered led device: iwl-phy0:assoc
[ 1541.743417] Registered led device: iwl-phy0:RX
[ 1541.743451] Registered led device: iwl-phy0:TX
[ 1541.797311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1541.828444] wlan0: deauthenticating by local choice (reason=3)
[ 1541.847977] iwlagn: index 0 not used in uCode key table.
[ 1541.983802] Registered led device: iwl-phy0:radio
[ 1541.983843] Registered led device: iwl-phy0:assoc
[ 1541.983881] Registered led device: iwl-phy0:RX
[ 1541.983917] Registered led device: iwl-phy0:TX
[ 1541.998307] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1543.028684] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1543.028713] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1543.030716] wlan0: authenticated
[ 1543.030723] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1543.030729] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1543.034448] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1543.034918] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1543.035377] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1543.035827] wlan0: authenticate with AP 00:03:c9:e6:b6:99
[ 1543.038431] wlan0: authenticated
[ 1543.038440] wlan0: associate with AP 00:03:c9:e6:b6:99
[ 1543.042649] wlan0: RX AssocResp from 00:03:c9:e6:b6:99 (capab=0x411 status=0 aid=1)
[ 1543.042656] wlan0: associated
[ 1543.047082] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1553.524030] wlan0: no IPv6 routers present
```

---

### Post by PatrickVogeli on 2009-05-10
iSoc, sembla que no hi ha massa a fer. El dmesg no indica res del lector de tarjes de sony, no te'l reconeix i no carrega cap driver ni res; a més, si busques a google, no sembla que hagis de tenir massa sort amb aquest lector de tarjetes..

salut!

---

### Post by iSoc on 2009-05-10
Gracies per respondre PartrickVogeli, quina mala sort pensat que podia tindre les mmc amb el thosiba i ara resulta que tinc un model de lector de targetes que per ara no es compatible quina marranada. Peró bueno que i farem l'única solució es afegir-hi un extern que sigui compatible.

  Aixòes l'únic que trobo al dmesg que tingui algú que veure amb el lector de targetes.

[    9.805695] mmc0: Unknown controller version (2). You may experience problems.
[    9.805752] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA

Un salut.

---

