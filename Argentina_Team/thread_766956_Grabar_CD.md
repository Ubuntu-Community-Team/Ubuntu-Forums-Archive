---
title: "Grabar CD"
date: 2008-04-25
forum: Argentina Team
---

### Post by jorgito on 2008-04-25
Hola a todos!

En casi un año con Ubuntu nunca habia intentado grabar un CD o un DVD.
La idea es grabar todo el /home para tenerlo como backup al momento de hacer el upgrade a Hardy.

Inserto el DVD, me pregunta que es lo que quiero hacer, le copio el /home a la carpeta del creador de CD/DVD, le mando a grabar y ahi se cuelga. La ventanita del creador nunca mas responde y hay que matarla.

Como hago para saber que es lo que pasa? hay algun log por algun lado? se puede hacer desde la consola para ver algun mensaje al menos?

Desde ya muchas gracias y saludos para todos!

---

### Post by fmsismo on 2008-04-25
Que versión de ubuntu estas usando?

Podría ser útil que nos pases un poco de info de tu equipo.  Podrías copiarnos el output de un dmesg.

Yo para gravar uso k3b (que es de kde) pero desde mi punto de vista es lo mejor que hay. (sudo apt-get install k3b)

Igual si nos pasas más data vemos de ayudarte ;-)

Saludos

---

### Post by jorgito on 2008-04-25
Hola y gracias, 

El equipo es una portatil Olivetti 820 en la que anduvo todo el hardware de entrada, wi-fi, sonido, teclas de volumen, con la unica excepcion de la resolucion de pantalla en Feisty, pero de la que Gusty se encargo a la perfeccion.
Lo que tengo instalado ahora es Ubuntu 7.10.

Intente instalar el gnomebaker, para ver si se encargaba de arreglar las cosas que yo no se, pero me resulto imposible descargarlo.

Aca va la salida de dmesg con un DVD vacio puesto en la lectora.

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f69d000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7860
[    0.000000] Entering add_active_range(0, 0, 521872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521872
[    0.000000] On node 0 totalpages: 521872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290211 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77B0 checksum 0
[    0.000000] ACPI: RSDP 000F77B0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7F696CAF, 0048 (r1 STD    STANDARD  6040000  LTP        0)
[    0.000000] ACPI: FACP 7F69CE20, 0074 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 7F69838C, 4A94 (r1 UW____ FUW_____  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7F69DFC0, 0040
[    0.000000] ACPI: APIC 7F69CE94, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7F69CEFC, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7F69CF34, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 7F69CF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7F69CFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7F697D3D, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F6976AB, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F696CF7, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 517795
[    0.000000] Kernel command line: root=UUID=2bc84bcf-41a8-426b-8b8a-c8fccb2290ae ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.172 MHz processor.
[   16.758888] Console: colour VGA+ 80x25
[   16.759167] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.759564] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.883739] Memory: 2058164k/2087488k available (2015k kernel code, 28108k reserved, 915k data, 364k init, 1169984k highmem)
[   16.883751] virtual kernel memory layout:
[   16.883752]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   16.883754]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.883755]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.883756]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.883758]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   16.883759]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   16.883761]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   16.883764] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.883806] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.883964] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.883971] hpet0: 3 64-bit timers, 14318180 Hz
[   16.964871] Calibrating delay using timer specific routine.. 3203.80 BogoMIPS (lpj=6407611)
[   16.964897] Security Framework v1.0.0 initialized
[   16.964905] SELinux:  Disabled at boot.
[   16.964922] Mount-cache hash table entries: 512
[   16.965058] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   16.965067] monitor/mwait feature present.
[   16.965069] using mwait in idle threads.
[   16.965074] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.965077] CPU: L2 cache: 1024K
[   16.965080] CPU: Physical Processor ID: 0
[   16.965082] CPU: Processor Core ID: 0
[   16.965084] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   16.965094] Compat vDSO mapped to ffffe000.
[   16.965108] Checking 'hlt' instruction... OK.
[   16.980976] SMP alternatives: switching to UP code
[   16.981472] Early unpacking initramfs... done
[   17.342404] ACPI: Core revision 20070126
[   17.342469] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.367641] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   17.367661] SMP alternatives: switching to SMP code
[   17.367793] Booting processor 1/1 eip 3000
[   17.377889] Initializing CPU#1
[   17.456111] Calibrating delay using timer specific routine.. 3200.17 BogoMIPS (lpj=6400357)
[   17.456118] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   17.456124] monitor/mwait feature present.
[   17.456127] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.456130] CPU: L2 cache: 1024K
[   17.456132] CPU: Physical Processor ID: 0
[   17.456134] CPU: Processor Core ID: 1
[   17.456136] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   17.456551] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   17.456579] Total of 2 processors activated (6403.98 BogoMIPS).
[   17.456776] ENABLING IO-APIC IRQs
[   17.456988] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.603986] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.623975] Brought up 2 CPUs
[   17.666212] migration_cost=50
[   17.666365] Booting paravirtualized kernel on bare hardware
[   17.666455] Time: 12:19:31  Date: 03/25/108
[   17.666477] NET: Registered protocol family 16
[   17.666572] EISA bus registered
[   17.666577] ACPI: bus type pci registered
[   17.705939] PCI: PCI BIOS revision 2.10 entry at 0xfd843, last bus=6
[   17.705942] PCI: Using configuration type 1
[   17.705944] Setting up standard PCI resources
[   17.710114] ACPI: EC: Look up EC in DSDT
[   17.710759] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   17.712268] ACPI: System BIOS is requesting _OSI(Linux)
[   17.712271] ACPI: Please test with "acpi_osi=!Linux"
[   17.712272] Please send dmidecode to linux-acpi@vger.kernel.org
[   17.712865] ACPI: Interpreter enabled
[   17.712869] ACPI: (supports S0 S3 S4 S5)
[   17.712886] ACPI: Using IOAPIC for interrupt routing
[   17.719185] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   17.719248] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.719258] PCI: Probing PCI hardware (bus 00)
[   17.720045] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.720050] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   17.721189] PCI: Transparent bridge - 0000:00:1e.0
[   17.721268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.721612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   17.721749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   17.721885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   17.722037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   17.725314] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   17.725420] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   17.725523] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   17.725625] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   17.725726] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   17.725827] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   17.725929] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   17.726029] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   17.726162] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.726173] pnp: PnP ACPI init
[   17.726182] ACPI: bus type pnp registered
[   17.728106] pnp: PnP ACPI: found 11 devices
[   17.728108] ACPI: ACPI bus type pnp unregistered
[   17.728113] PnPBIOS: Disabled by ACPI PNP
[   17.728165] PCI: Using ACPI for IRQ routing
[   17.728168] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.728257] PCI: Cannot allocate resource region 0 of device 0000:05:00.0
[   17.749243] NET: Registered protocol family 8
[   17.749246] NET: Registered protocol family 20
[   17.749333] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.749338] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.749341] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.749345] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   17.749353] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   17.749363] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   17.749366] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   17.751666] Time: tsc clocksource has been installed.
[   17.751683] Switched to high resolution mode on CPU 0
[   17.751776] Switched to high resolution mode on CPU 1
[   17.779693] PCI: Bridge: 0000:00:1c.0
[   17.779697]   IO window: f000-ffff
[   17.779704]   MEM window: fac00000-febfffff
[   17.779708]   PREFETCH window: disabled.
[   17.779715] PCI: Bridge: 0000:00:1c.1
[   17.779716]   IO window: disabled.
[   17.779722]   MEM window: disabled.
[   17.779727]   PREFETCH window: disabled.
[   17.779745] PCI: Bridge: 0000:00:1c.2
[   17.779747]   IO window: disabled.
[   17.779754]   MEM window: f7000000-f70fffff
[   17.779758]   PREFETCH window: disabled.
[   17.779768] PCI: Bridge: 0000:00:1e.0
[   17.779771]   IO window: 2000-2fff
[   17.779778]   MEM window: f0200000-f02fffff
[   17.779782]   PREFETCH window: disabled.
[   17.779811] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   17.779819] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   17.779829] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.779854] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   17.779862] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.779886] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
[   17.779891] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.779899] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.779914] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.779927] NET: Registered protocol family 2
[   17.827544] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.827626] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   17.828781] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.829218] TCP: Hash tables configured (established 131072 bind 65536)
[   17.829221] TCP reno registered
[   17.843661] checking if image is initramfs... it is
[   18.563461] Freeing initrd memory: 7048k freed
[   18.563592] Simple Boot Flag at 0x36 set to 0x1
[   18.564145] audit: initializing netlink socket (disabled)
[   18.564162] audit(1209125971.228:1): initialized
[   18.564278] highmem bounce pool size: 64 pages
[   18.566365] VFS: Disk quotas dquot_6.5.1
[   18.566435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.566544] io scheduler noop registered
[   18.566547] io scheduler anticipatory registered
[   18.566549] io scheduler deadline registered
[   18.566566] io scheduler cfq registered (default)
[   18.566582] Boot video device is 0000:00:02.0
[   18.566763] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.566823] assign_interrupt_mode Found MSI capability
[   18.566826] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.566866] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.566969] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.567028] assign_interrupt_mode Found MSI capability
[   18.567031] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.567064] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.567172] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.567230] assign_interrupt_mode Found MSI capability
[   18.567233] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.567265] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.567435] isapnp: Scanning for PnP cards...
[   18.920992] isapnp: No Plug & Play device found
[   18.948747] Real Time Clock Driver v1.12ac
[   18.949004] hpet_resources: 0xfed00000 is busy
[   18.949037] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.950387] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.950636] input: Macintosh mouse button emulation as /class/input/input0
[   18.950720] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.953612] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.954781] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.954785] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.954788] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.954791] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.954794] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.954992] mice: PS/2 mouse device common for all mice
[   18.955213] EISA: Probing bus 0 at eisa.0
[   18.955222] Cannot allocate resource for EISA slot 1
[   18.955226] Cannot allocate resource for EISA slot 2
[   18.955255] EISA: Detected 0 cards.
[   18.955357] TCP cubic registered
[   18.955374] NET: Registered protocol family 1
[   18.955399] Using IPI No-Shortcut mode
[   18.955579]   Magic number: 4:409:330
[   18.955717]   hash matches device tty51
[   18.955936] Freeing unused kernel memory: 364k freed
[   19.033863] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.175667] AppArmor: AppArmor initialized<5>audit(1209125972.728:2):  type=1505 info="AppArmor initialized" pid=1264
[   20.184632] fuse init (API version 7.8)
[   20.190803] Failure registering capabilities with primary security module.
[   20.217804] ACPI: SSDT 7F697438, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   20.218024] ACPI: SSDT 7F6971ED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   20.218303] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.218309] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.218567] ACPI: SSDT 7F697622, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   20.218767] ACPI: SSDT 7F6973B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   20.219078] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.219083] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.220539] ACPI: Thermal Zone [THRM] (29 C)
[    3.208000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.212000] Time: hpet clocksource has been installed.
[    3.676000] usbcore: registered new interface driver usbfs
[    3.676000] usbcore: registered new interface driver hub
[    3.676000] usbcore: registered new device driver usb
[    3.676000] USB Universal Host Controller Interface driver v3.0
[    3.676000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.676000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.676000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.676000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.676000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.688000] usb usb1: configuration #1 chosen from 1 choice
[    3.688000] hub 1-0:1.0: USB hub found
[    3.688000] hub 1-0:1.0: 2 ports detected
[    3.732000] SCSI subsystem initialized
[    3.736000] libata version 2.21 loaded.
[    3.792000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.792000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.792000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.792000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.792000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.792000] usb usb2: configuration #1 chosen from 1 choice
[    3.792000] hub 2-0:1.0: USB hub found
[    3.792000] hub 2-0:1.0: 2 ports detected
[    3.856000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.896000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.896000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.896000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.896000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.896000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.896000] usb usb3: configuration #1 chosen from 1 choice
[    3.896000] hub 3-0:1.0: USB hub found
[    3.896000] hub 3-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -98042854 ns)
[    4.000000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.000000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.000000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.000000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.000000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.000000] usb usb4: configuration #1 chosen from 1 choice
[    4.000000] hub 4-0:1.0: USB hub found
[    4.000000] hub 4-0:1.0: 2 ports detected
[    4.104000] ata_piix 0000:00:1f.1: version 2.11
[    4.104000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[    4.104000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.104000] scsi0 : ata_piix
[    4.104000] scsi1 : ata_piix
[    4.104000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.104000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.424000] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.20, max UDMA/33
[    4.596000] ata1.00: configured for UDMA/33
[    4.596000] ata2: port disabled. ignoring.
[    4.596000] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5
[    4.596000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.596000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.752000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.752000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.752000] scsi2 : ata_piix
[    4.752000] scsi3 : ata_piix
[    4.752000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 20
[    4.752000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 20
[    4.916000] ata3.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
[    4.916000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.932000] ata3.00: configured for UDMA/100
[    5.096000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[    5.100000] PCI: Enabling device 0000:06:04.0 (0195 -> 0197)
[    5.100000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[    5.148000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f0200000-f02007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.152000] 8139cp 0000:06:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.152000] 8139cp 0000:06:05.0: Try the "8139too" driver instead.
[    5.152000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    5.152000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.152000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.152000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.152000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.152000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.152000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0004000
[    5.156000] 8139too Fast Ethernet driver 0.9.28
[    5.160000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.160000] usb usb5: configuration #1 chosen from 1 choice
[    5.160000] hub 5-0:1.0: USB hub found
[    5.160000] hub 5-0:1.0: 8 ports detected
[    5.264000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[    5.264000] eth0: RealTek RTL8139 at 0xf8824c00, 00:03:0d:5f:e9:02, IRQ 17
[    5.264000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.280000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.280000] Uniform CD-ROM driver Revision: 3.20
[    5.280000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.280000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.280000] sd 2:0:0:0: [sda] Write Protect is off
[    5.280000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.280000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.280000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.280000] sd 2:0:0:0: [sda] Write Protect is off
[    5.280000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.280000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.280000]  sda: sda1 sda2 <<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.288000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.340000]  sda5 >
[    5.340000] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.504000] Attempting manual resume
[    5.504000] swsusp: Resume From Partition 8:5
[    5.504000] PM: Checking swsusp image.
[    5.504000] PM: Resume from disk failed.
[    5.520000] kjournald starting.  Commit interval 5 seconds
[    5.520000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.424000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d004105bd0a]
[   13.732000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.736000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.932000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.932000] agpgart: Detected an Intel 945GM Chipset.
[   13.932000] agpgart: Detected 7932K stolen memory.
[   13.952000] agpgart: AGP aperture is 256M @ 0xc0000000
[   14.212000] intel_rng: FWH not detected
[   14.460000] ieee80211_crypt: registered algorithm 'NULL'
[   14.472000] sdhci: Secure Digital Host Controller Interface driver
[   14.472000] sdhci: Copyright(c) Pierre Ossman
[   14.472000] sdhci: SDHCI controller found at 0000:06:04.2 [1217:7120] (rev 1)
[   14.472000] ACPI: PCI Interrupt 0000:06:04.2[A] -> GSI 18 (level, low) -> IRQ 18
[   14.472000] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   14.472000] mmc0: SDHCI at 0xb0300800 irq 18 PIO
[   14.512000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.512000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.532000] iTCO_vendor_support: vendor-support=0
[   14.540000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.588000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.588000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.588000] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[   14.588000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   14.588000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   14.588000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   14.772000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   14.772000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.956000] input: PS/2 Logitech Wheel Mouse as /class/input/input2
[   14.960000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.960000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.152000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   15.444000] loop: module loaded
[   15.500000] lp: driver loaded but no devices found
[   15.612000] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   16.080000] EXT3 FS on sda1, internal journal
[   16.408000] hda_intel: azx_get_response timeout, switching to polling mode...
[   16.484000] ipw3945: Radio Frequency Kill Switch is On:
[   16.484000] Kill switch must be turned off for wireless networking to work.
[   17.432000] ACPI: AC Adapter [AC0] (on-line)
[   17.444000] input: Power Button (FF) as /class/input/input3
[   17.444000] ACPI: Power Button (FF) [PWRF]
[   17.444000] input: Lid Switch as /class/input/input4
[   17.444000] ACPI: Lid Switch [LID0]
[   17.444000] input: Power Button (CM) as /class/input/input5
[   17.444000] ACPI: Power Button (CM) [PWRB]
[   17.444000] input: Sleep Button (CM) as /class/input/input6
[   17.444000] ACPI: Sleep Button (CM) [SLPB]
[   17.556000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.556000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   17.568000] No dock devices found.
[   17.628000] ACPI: Battery Slot [BAT0] (battery present)
[   18.884000] Failure registering capabilities with primary security module.
[   19.144000] ppdev: user-space parallel port driver
[   19.264000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   19.400000] audit(1209125989.869:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5053 profile="/usr/sbin/cupsd"
[   19.448000] apm: BIOS not found.
[   19.928000] Bluetooth: Core ver 2.11
[   19.928000] NET: Registered protocol family 31
[   19.928000] Bluetooth: HCI device and connection manager initialized
[   19.928000] Bluetooth: HCI socket layer initialized
[   19.944000] Bluetooth: L2CAP ver 2.8
[   19.944000] Bluetooth: L2CAP socket layer initialized
[   20.004000] Bluetooth: RFCOMM socket layer initialized
[   20.004000] Bluetooth: RFCOMM TTY layer initialized
[   20.004000] Bluetooth: RFCOMM ver 1.8
[   23.160000] NET: Registered protocol family 10
[   23.160000] lo: Disabled Privacy Extensions
[   24.336000] NET: Registered protocol family 17
[   25.460000] [drm] Initialized drm 1.1.0 20060810
[   25.464000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   25.464000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.108000] eth0: no IPv6 routers present
[ 2663.976000] cdrom: This disc doesn't have any tracks I recognize!
[17153.364000] cdrom: This disc doesn't have any tracks I recognize!


```

Saludos y gracias de nuevo

---

### Post by fmsismo on 2008-04-25
Proba instalando el k3b.  Así aislas un tema de software de uno de hardware.

Las dvdrtools las tenés instaladas no? (sudo apt-get install dvdrtools)

Si no podes, probamos de hacerlo desde consola.


Saludos

---

