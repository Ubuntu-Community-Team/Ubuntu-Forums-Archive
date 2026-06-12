---
title: "PCI cannot allocate resource 7/8/9 on kubuntu 7.1 bootup"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-11-30
Hi 

Brand new install of Kubntu 7.1. 

Upon boot, this is the first thing on my screen right after Grub:

PCI: Cannot Allocate Resource Region 7 of device (numbers that I cant remember)
PCI: Cannot Allocate Resource Region 8 of device (numbers that I cant remember)
PCI: Cannot Allocate Resource Region 9 of device (numbers that I cant remember)

and then the system continues boot ok

What does it mean?

here is output of dmesg and lspci:

B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
laan97ac@laan97ac-laptop:~$  

laan97ac@laan97ac-laptop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef9000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7a70
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F79C0 checksum 0
[    0.000000] ACPI: RSDP 000F79C0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3FEF1A59, 0034 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEF8EC0, 0074 (r1 HP     3082      6040000 PTL         3)
[    0.000000] ACPI: DSDT 3FEF1A8D, 7433 (r1 HP     3082      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEF9FC0, 0040
[    0.000000] ACPI: MCFG 3FEF8F34, 003C (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: APIC 3FEF8F70, 0068 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FEF8FD8, 0028 (r1     HP 3082      6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=90244f93-bbd8-46f1-a58b-b46ad8ecc8ea ro quiet nosplash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2793.260 MHz processor.
[   15.283724] Console: colour VGA+ 80x25
[   15.284007] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.284335] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.308906] Memory: 1026872k/1047488k available (2015k kernel code, 19976k reserved, 916k data, 364k init, 129984k highmem)
[   15.308916] virtual kernel memory layout:
[   15.308918]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.308919]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.308920]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.308921]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.308922]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.308923]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   15.308925]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   15.308928] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.308968] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.388858] Calibrating delay using timer specific routine.. 5591.42 BogoMIPS (lpj=11182858)
[   15.388884] Security Framework v1.0.0 initialized
[   15.388889] SELinux:  Disabled at boot.
[   15.388902] Mount-cache hash table entries: 512
[   15.389033] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   15.389042] monitor/mwait feature present.
[   15.389045] using mwait in idle threads.
[   15.389052] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.389055] CPU: L2 cache: 1024K
[   15.389058] CPU: Physical Processor ID: 0
[   15.389060] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   15.389071] Compat vDSO mapped to ffffe000.
[   15.389087] Checking 'hlt' instruction... OK.
[   15.404928] SMP alternatives: switching to UP code
[   15.405375] Early unpacking initramfs... done
[   15.707764] ACPI: Core revision 20070126
[   15.707831] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.725824] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[   15.725844] SMP alternatives: switching to SMP code
[   15.725947] Booting processor 1/1 eip 3000
[   15.736049] Initializing CPU#1
[   15.816144] Calibrating delay using timer specific routine.. 5586.44 BogoMIPS (lpj=11172889)
[   15.816155] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   15.816162] monitor/mwait feature present.
[   15.816170] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.816173] CPU: L2 cache: 1024K
[   15.816176] CPU: Physical Processor ID: 0
[   15.816178] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   15.816568] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[   15.816610] Total of 2 processors activated (11177.87 BogoMIPS).
[   15.816759] ENABLING IO-APIC IRQs
[   15.816943] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.830458] APIC calibration not consistent with PM Timer: 968ms instead of 100ms
[   16.830463] APIC delta adjusted to PM-Timer: 1246873 (12070440)
[   16.830582] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.850565] Brought up 2 CPUs
[   16.938774] migration_cost=99
[   16.938955] Booting paravirtualized kernel on bare hardware
[   16.939023] Time: 20:06:39  Date: 10/30/107
[   16.939050] NET: Registered protocol family 16
[   16.939146] EISA bus registered
[   16.939152] ACPI: bus type pci registered
[   16.980724] PCI: PCI BIOS revision 2.10 entry at 0xfd95e, last bus=11
[   16.980727] PCI: Using configuration type 1
[   16.980729] Setting up standard PCI resources
[   16.990877] ACPI: EC: Look up EC in DSDT
[   16.991574] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   17.011698] ACPI: Interpreter enabled
[   17.011704] ACPI: (supports S0 S3 S4 S5)
[   17.011722] ACPI: Using IOAPIC for interrupt routing
[   17.017583] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   17.017640] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.017655] PCI: Probing PCI hardware (bus 00)
[   17.018276] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.018280] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   17.019022] PCI: Transparent bridge - 0000:00:1e.0
[   17.019135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.019438] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[   17.019568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   17.019697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   17.026356] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)
[   17.026451] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5
[   17.026543] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)
[   17.026633] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7
[   17.026727] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7
[   17.026821] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[   17.026916] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[   17.027011] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7
[   17.027130] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.027142] pnp: PnP ACPI init
[   17.027152] ACPI: bus type pnp registered
[   17.029129] pnp: PnP ACPI: found 9 devices
[   17.029132] ACPI: ACPI bus type pnp unregistered
[   17.029136] PnPBIOS: Disabled by ACPI PNP
[   17.029205] PCI: Using ACPI for IRQ routing
[   17.029210] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.029216] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   17.029255] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   17.029292] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   17.050598] NET: Registered protocol family 8
[   17.050601] NET: Registered protocol family 20
[   17.050670] pnp: 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[   17.050679] pnp: 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[   17.050682] pnp: 00:02: iomem range 0xfed13000-0xfed13fff has been reserved
[   17.050685] pnp: 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[   17.050689] pnp: 00:02: iomem range 0xfed20000-0xfed8ffff has been reserved
[   17.054102] Time: tsc clocksource has been installed.
[   17.081052] PCI: Bridge: 0000:00:01.0
[   17.081056]   IO window: 4000-4fff
[   17.081061]   MEM window: c8100000-c81fffff
[   17.081065]   PREFETCH window: d0000000-d7ffffff
[   17.081069] PCI: Bridge: 0000:00:1c.0
[   17.081070]   IO window: disabled.
[   17.081075]   MEM window: disabled.
[   17.081079]   PREFETCH window: disabled.
[   17.081091] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[   17.081094]   IO window: 00005400-000054ff
[   17.081099]   IO window: 00005800-000058ff
[   17.081104]   PREFETCH window: 50000000-53ffffff
[   17.081109]   MEM window: 54000000-57ffffff
[   17.081113] PCI: Bridge: 0000:00:1e.0
[   17.081117]   IO window: 5000-5fff
[   17.081122]   MEM window: c8200000-c82fffff
[   17.081126]   PREFETCH window: 50000000-53ffffff
[   17.081146] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.081153] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.081173] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   17.081180] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.081192] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.081207] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.081222] NET: Registered protocol family 2
[   17.126111] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.126187] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   17.127087] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.127351] TCP: Hash tables configured (established 131072 bind 65536)
[   17.127354] TCP reno registered
[   17.138230] checking if image is initramfs... it is
[   17.581198] Switched to high resolution mode on CPU 0
[   17.581290] Switched to high resolution mode on CPU 1
[   17.733824] Freeing initrd memory: 7069k freed
[   17.733918] Simple Boot Flag at 0x36 set to 0x1
[   17.734418] audit: initializing netlink socket (disabled)
[   17.734431] audit(1196453198.232:1): initialized
[   17.734536] highmem bounce pool size: 64 pages
[   17.737003] VFS: Disk quotas dquot_6.5.1
[   17.737073] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.737183] io scheduler noop registered
[   17.737186] io scheduler anticipatory registered
[   17.737188] io scheduler deadline registered
[   17.737205] io scheduler cfq registered (default)
[   17.737400] Boot video device is 0000:01:00.0
[   17.737493] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.737538] assign_interrupt_mode Found MSI capability
[   17.737541] Allocate Port Service[0000:00:01.0:pcie00]
[   17.737636] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.737681] assign_interrupt_mode Found MSI capability
[   17.737684] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.737725] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.737904] isapnp: Scanning for PnP cards...
[   18.089002] isapnp: No Plug & Play device found
[   18.117529] Real Time Clock Driver v1.12ac
[   18.117641] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.118274] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   18.118282] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   18.118961] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.119173] input: Macintosh mouse button emulation as /class/input/input0
[   18.119268] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.120948] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.120956] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.121154] mice: PS/2 mouse device common for all mice
[   18.121295] EISA: Probing bus 0 at eisa.0
[   18.121303] Cannot allocate resource for EISA slot 1
[   18.121309] Cannot allocate resource for EISA slot 3
[   18.121312] Cannot allocate resource for EISA slot 4
[   18.121314] Cannot allocate resource for EISA slot 5
[   18.121326] EISA: Detected 0 cards.
[   18.121410] TCP cubic registered
[   18.121423] NET: Registered protocol family 1
[   18.121445] Using IPI No-Shortcut mode
[   18.121607]   Magic number: 15:472:145
[   18.121957] Freeing unused kernel memory: 364k freed
[   18.150973] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.327155] AppArmor: AppArmor initialized<5>audit(1196453198.732:2):  type=1505 info="AppArmor initialized" pid=1181
[   18.336450] fuse init (API version 7.8)
[   18.341946] Failure registering capabilities with primary security module.
[   18.374957] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.374986] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.376939] ACPI: Thermal Zone [THRM] (59 C)
[   19.020149] SCSI subsystem initialized
[   19.028726] libata version 2.21 loaded.
[   19.035766] ata_piix 0000:00:1f.1: version 2.11
[   19.035790] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   19.035831] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.035910] scsi0 : ata_piix
[   19.035973] scsi1 : ata_piix
[   19.036020] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013c40 irq 14
[   19.036026] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013c48 irq 15
[   19.068883] usbcore: registered new interface driver usbfs
[   19.068926] usbcore: registered new interface driver hub
[   19.068964] usbcore: registered new device driver usb
[   19.070282] USB Universal Host Controller Interface driver v3.0
[   19.200885] 8139too Fast Ethernet driver 0.9.28
[   19.418357] ata1.00: ATA-6: ST9808211A, 3.02, max UDMA/100
[   19.418362] ata1.00: 156301488 sectors, multi 16: LBA48
[   19.418368] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CC15, max MWDMA2
[   19.434325] ata1.00: configured for UDMA/100
[   19.606037] ata1.01: configured for MWDMA2
[   19.606069] ata2: port disabled. ignoring.
[   19.606218] scsi 0:0:0:0: Direct-Access     ATA      ST9808211A       3.02 PQ: 0 ANSI: 5
[   19.610037] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CC15 PQ: 0 ANSI: 5
[   19.610473] ACPI: PCI Interrupt 0000:0b:00.2[C] -> GSI 22 (level, low) -> IRQ 18
[   19.610505] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   19.610519] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.610525] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.610689] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.610723] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   19.610914] usb usb1: configuration #1 chosen from 1 choice
[   19.610966] hub 1-0:1.0: USB hub found
[   19.610978] hub 1-0:1.0: 2 ports detected
[   19.664413] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.664438] sd 0:0:0:0: [sda] Write Protect is off
[   19.664443] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.664474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.664553] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.664570] sd 0:0:0:0: [sda] Write Protect is off
[   19.664575] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.664604] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.664612]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8208000-c82087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.692447]  sda1 sda2 sda3 sda4 < sda5<6>ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   19.713758] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.713764] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.713802] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.713836] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000038c0
[   19.714015] usb usb2: configuration #1 chosen from 1 choice
[   19.714064] hub 2-0:1.0: USB hub found
[   19.714074] hub 2-0:1.0: 2 ports detected
[   19.726987]  sda6 >
[   19.739631] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.744132] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.744164] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   19.760989] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   19.760996] Uniform CD-ROM driver Revision: 3.20
[   19.761071] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   19.817580] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   19.817598] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.817604] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.817644] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.817680] uhci_hcd 0000:00:1d.2: irq 19, io base 0x000038e0
[   19.817829] usb usb3: configuration #1 chosen from 1 choice
[   19.817874] hub 3-0:1.0: USB hub found
[   19.817885] hub 3-0:1.0: 2 ports detected
[   19.921420] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   19.921437] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.921443] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.921484] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   19.921521] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003c00
[   19.921649] usb usb4: configuration #1 chosen from 1 choice
[   19.921684] hub 4-0:1.0: USB hub found
[   19.921693] hub 4-0:1.0: 2 ports detected
[   20.025294] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   20.025310] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.025316] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.025360] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.025398] ehci_hcd 0000:00:1d.7: debug port 1
[   20.025407] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   20.025418] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xc8000000
[   20.057068] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   20.057078] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.057248] usb usb5: configuration #1 chosen from 1 choice
[   20.057293] hub 5-0:1.0: USB hub found
[   20.057305] hub 5-0:1.0: 8 ports detected
[   20.115217] Attempting manual resume
[   20.115222] swsusp: Resume From Partition 8:3
[   20.115224] PM: Checking swsusp image.
[   20.115433] PM: Resume from disk failed.
[   20.154340] kjournald starting.  Commit interval 5 seconds
[   20.154353] EXT3-fs: mounted filesystem with ordered data mode.
[   20.161887] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 20 (level, low) -> IRQ 22
[   20.162273] eth0: RealTek RTL8139 at 0xf885c400, 00:c0:9f:cc:4f:f3, IRQ 22
[   20.162277] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.167608] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.931694] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08002856000b29cb]
[   20.983470] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   21.247714] usb 5-5: configuration #1 chosen from 1 choice
[   21.486614] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   21.619556] usb 5-7: configuration #1 chosen from 1 choice
[   21.857986] usb 5-8: new high speed USB device using ehci_hcd and address 5
[   21.991896] usb 5-8: configuration #1 chosen from 2 choices
[   22.229359] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   22.402334] usb 2-1: configuration #1 chosen from 1 choice
[   22.405269] hub 2-1:1.0: USB hub found
[   22.408237] hub 2-1:1.0: 4 ports detected
[   22.717706] usb 2-1.1: new full speed USB device using uhci_hcd and address 4
[   22.875510] usb 2-1.1: configuration #1 chosen from 1 choice
[   23.081081] usb 2-1.2: new low speed USB device using uhci_hcd and address 5
[   23.225905] usb 2-1.2: configuration #1 chosen from 1 choice
[   28.393272] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.646098] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.770879] intel_rng: FWH not detected
[   28.937879] Linux agpgart interface v0.102 (c) Dave Jones
[   29.117689] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[   29.117710] Yenta: Enabling burst memory read transactions
[   29.117718] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.117722] Yenta: Routing CardBus interrupts to PCI
[   29.117756] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[   29.206644] input: PC Speaker as /class/input/input2
[   29.223984] iTCO_vendor_support: vendor-support=0
[   29.225486] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   29.225603] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x1060)
[   29.225664] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.350103] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   29.350109] Socket status: 30000006
[   29.350114] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   29.350119] cs: IO port probe 0x5000-0x5fff: clean.
[   29.350539] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   29.350544] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   29.362973] PCI: Enabling device 0000:0b:00.3 (0000 -> 0002)
[   29.362984] ACPI: PCI Interrupt 0000:0b:00.3[A] -> GSI 16 (level, low) -> IRQ 16
[   29.404051] sdhci: Secure Digital Host Controller Interface driver
[   29.404057] sdhci: Copyright(c) Pierre Ossman
[   29.404122] sdhci: SDHCI controller found at 0000:0b:00.4 [104c:8034] (rev 0)
[   29.404141] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[   29.404150] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 16
[   29.404241] mmc0: SDHCI at 0xc8209000 irq 16 DMA
[   29.408300] mmc1: SDHCI at 0xc8208c00 irq 16 DMA
[   29.408371] mmc2: SDHCI at 0xc8208800 irq 16 DMA
[   29.493822] ieee80211_crypt: registered algorithm 'NULL'
[   29.599244] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   29.599250] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   29.885488] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[   29.918847] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   29.959533] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8604
[   29.959563] usbcore: registered new interface driver usblp
[   29.959569] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   30.008103] usbcore: registered new interface driver hiddev
[   30.023423] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input4
[   30.023491] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1.2
[   30.023514] usbcore: registered new interface driver usbhid
[   30.023520] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.069551] usbcore: registered new interface driver libusual
[   30.101789] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.101796] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.105619] Initializing USB Mass Storage driver...
[   30.105710] scsi2 : SCSI emulation for USB Mass Storage devices
[   30.105801] usb-storage: device found at 3
[   30.105805] usb-storage: waiting for device to settle before scanning
[   30.105836] scsi3 : SCSI emulation for USB Mass Storage devices
[   30.109598] usb-storage: device found at 4
[   30.109603] usb-storage: waiting for device to settle before scanning
[   30.109653] scsi4 : SCSI emulation for USB Mass Storage devices
[   30.109805] usbcore: registered new interface driver usb-storage
[   30.109810] USB Mass Storage support registered.
[   30.109815] usb-storage: device found at 5
[   30.109818] usb-storage: waiting for device to settle before scanning
[   30.143869] bcm43xx driver
[   30.143966] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[   30.143977] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.306649] cs: IO port probe 0x100-0x3af: clean.
[   30.308094] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.308817] cs: IO port probe 0x820-0x8ff: clean.
[   30.309351] cs: IO port probe 0xc00-0xcf7: clean.
[   30.310017] cs: IO port probe 0xa00-0xaff: clean.
[   30.385952] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 18
[   30.385977] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   30.703064] intel8x0_measure_ac97_clock: measured 54103 usecs
[   30.703068] intel8x0: clocking to 48000
[   30.929206] lp: driver loaded but no devices found
[   30.987818] Adding 1967952k swap on /dev/sda3.  Priority:-1 extents:1 across:1967952k
[   31.449301] EXT3 FS on sda2, internal journal
[   32.697798] kjournald starting.  Commit interval 5 seconds
[   32.698003] EXT3 FS on sda5, internal journal
[   32.698008] EXT3-fs: mounted filesystem with ordered data mode.
[   32.745921] kjournald starting.  Commit interval 5 seconds
[   32.746108] EXT3 FS on sda6, internal journal
[   32.746113] EXT3-fs: mounted filesystem with ordered data mode.
[   34.480186] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.492395] No dock devices found.
[   34.526711] ACPI: AC Adapter [ACAD] (on-line)
[   34.538797] ACPI: Battery Slot [BAT1] (battery absent)
[   34.577721] input: Power Button (FF) as /class/input/input5
[   34.577756] ACPI: Power Button (FF) [PWRF]
[   34.577868] input: Lid Switch as /class/input/input6
[   34.577889] ACPI: Lid Switch [LID0]
[   34.577956] input: Power Button (CM) as /class/input/input7
[   34.577986] ACPI: Power Button (CM) [PWRB]
[   34.578049] input: Sleep Button (CM) as /class/input/input8
[   34.578080] ACPI: Sleep Button (CM) [SLPB]
[   35.095769] usb-storage: device scan complete
[   35.096264] scsi 2:0:0:0: Direct-Access     HTS54808 0M9AT00          MG4O PQ: 0 ANSI: 0
[   35.097497] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   35.098366] sd 2:0:0:0: [sdb] Write Protect is off
[   35.098370] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.098372] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   35.099486] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   35.099751] usb-storage: device scan complete
[   35.099879] usb-storage: device scan complete
[   35.100264] scsi 3:0:0:0: Direct-Access     WD       1600BEVExternal  1.02 PQ: 0 ANSI: 0
[   35.100369] sd 2:0:0:0: [sdb] Write Protect is off
[   35.100375] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.100379] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   35.100425]  sdb:<5>scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   35.415586]  sdb1
[   35.415690] sd 2:0:0:0: [sdb] Attached SCSI disk
[   35.415756] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   35.417547] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   35.418317] sd 3:0:0:0: [sdc] Write Protect is off
[   35.418324] sd 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   35.418330] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   35.419191] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   35.420062] sd 3:0:0:0: [sdc] Write Protect is off
[   35.420070] sd 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   35.420074] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   35.420125]  sdc:<6>ppdev: user-space parallel port driver
[   36.230102] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   36.528269] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   36.678734] audit(1196471218.723:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5043 profile="/usr/sbin/cupsd"
[   36.930280] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.930288] apm: disabled - APM is not SMP safe.
[   38.722255] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   39.119686]  sdc1
[   39.119793] sd 3:0:0:0: [sdc] Attached SCSI disk
[   39.119858] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   39.128869] sd 4:0:0:0: [sdd] 1999871 512-byte hardware sectors (1024 MB)
[   39.130291] sd 4:0:0:0: [sdd] Write Protect is off
[   39.130298] sd 4:0:0:0: [sdd] Mode Sense: 68 00 00 08
[   39.130301] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   39.132851] sd 4:0:0:0: [sdd] 1999871 512-byte hardware sectors (1024 MB)
[   39.136411] sd 4:0:0:0: [sdd] Write Protect is off
[   39.136419] sd 4:0:0:0: [sdd] Mode Sense: 68 00 00 08
[   39.136422] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   39.136431]  sdd: sdd1 sdd2
[   39.141462] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[   39.141539] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   39.381335] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   39.387674] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   39.387785] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   39.427106] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.517883] Failure registering capabilities with primary security module.
[   39.837824] Bluetooth: Core ver 2.11
[   39.837894] NET: Registered protocol family 31
[   39.837899] Bluetooth: HCI device and connection manager initialized
[   39.837905] Bluetooth: HCI socket layer initialized
[   39.870056] Bluetooth: L2CAP ver 2.8
[   39.870063] Bluetooth: L2CAP socket layer initialized
[   39.976445] Bluetooth: RFCOMM socket layer initialized
[   39.976463] Bluetooth: RFCOMM TTY layer initialized
[   39.976466] Bluetooth: RFCOMM ver 1.8
[   42.356344] [fglrx] total      GART = 130023424
[   42.356352] [fglrx] free       GART = 114032640
[   42.356356] [fglrx] max single GART = 114032640
[   42.356359] [fglrx] total      LFB  = 134086656
[   42.356362] [fglrx] free       LFB  = 115871744
[   42.356365] [fglrx] max single LFB  = 115871744
[   42.356368] [fglrx] total      Inv  = 0
[   42.356372] [fglrx] free       Inv  = 0
[   42.356375] [fglrx] max single Inv  = 0
[   42.356378] [fglrx] total      TIM  = 0
[   44.298908] NET: Registered protocol family 17
[   48.360485] NET: Registered protocol family 10
[   48.361803] lo: Disabled Privacy Extensions
[   59.172115] eth0: no IPv6 routers present
[   60.731571] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   82.734872] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  104.730719] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  126.740328] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  148.741616] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  170.739383] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  292.566313] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  414.388260] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by rax_m on 2007-12-01
It seems to be a common problem on some computer (especially laptops?) .. but as long as everything is working it shouldn't be an issue.

---

### Post by dca on 2007-12-04
It happens on my Acer laptop on two resource regions.  Something tells me it is because of either the WiFi card or USB hub...  Funny thing is it didn't happen in Ubuntu 7.04, only 7.10...
 
It hasn't affected anything as far as performance or caused any errors.

---

