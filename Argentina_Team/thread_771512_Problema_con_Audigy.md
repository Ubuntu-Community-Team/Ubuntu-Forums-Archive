---
title: "Problema con Audigy"
date: 2008-04-27
forum: Argentina Team
---

### Post by fepe55 on 2008-04-27
Hola gente, empiezo como varios, diciendo que soy un *newbie* total con Ubuntu.

Y ahora paso al problema. Tengo una placa Audigy que no funciona.

En "Default Mixer Tracks" en "Sound Preferences" figura como "Audigy 1 [SB0090] (Alsa mixer)", así que veo que la reconoció, pero no emite sonido.
Lo más extraño es que una vez reinicié, y funcionó, pude ver un par de series y todo, hasta que reinicié de nuevo, y nada. Silencio. Reinicé una vez más y volvió. Y lo que noté fue que no funcionan los sonidos del sistema, pero sí puedo ver videos y escuchar MP3.

Luego volví a reiniciar y nada, lo mismo por las últimas cinco *reiniciadas*. Estoy sin sonido.

Cabe aclarar que no instalé nada "raro", sólo algunos codecs, el TVTime (que instalé y desinstalé un par de veces porque también estoy luchando con la placa de TV), Amarok y creo que nada más.


Estoy en Ubuntu, Hardy. Díganme qué cosas les debo pasar para que me puedan ayudar.


Muchas gracias.

---

### Post by Hei Ku on 2008-04-27
En la consola, pone:
alsamixer

Fijate ahi si no tenes algun canal de sonido en mute. Eso puede ser el problema.

---

### Post by fepe55 on 2008-04-27
Ya probé todos, y nop, nada. También probé lo de destildar Analog/Digital Output Jack. Y nada.

---

### Post by Hei Ku on 2008-04-27
que te dice el log de dmesg sobre el audio?

fijate el archivo en /var/log/dmesg

---

### Post by MeduZa on 2008-04-27
yo se que suena idiota pero me paso: proba si esta enchufado el parlante donde es, cuando me pase de windows a linux no me andaba eso y era que linux mapeaba distito las salidas.

yo tengo una audigy 2 pero creo que es mismo driver

por lo que veo, te la detecto lo mas bien
pega aca lo que te devuelva los siguientes comandos en consola:
cat /proc/asound/cards 
despues:
cat /proc/asound/pcm 
y por ultimo:
amixer scontents

---

### Post by fepe55 on 2008-04-27
> que te dice el log de dmesg sobre el audio?

fijate el archivo en /var/log/dmesg 

No encuentro ninguna referencia a la placa Audigy, acá va completo por las dudas:
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe30000 (usable)
[    0.000000]  BIOS-e820: 000000003fe30000 - 000000003fe3e05e (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe3e05e - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261936
[    0.000000] On node 0 totalpages: 261936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32306 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62F0 checksum 0
[    0.000000] ACPI: RSDP 000F62F0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF30000, 0034 (r1 INTEL  D865PERL 20040402 MSFT       97)
[    0.000000] ACPI: FACP 3FF30200, 0081 (r2 INTEL  D865PERL 20040402 MSFT       97)
[    0.000000] ACPI: DSDT 3FF30370, 4170 (r1 INTEL  D865PERL        6 MSFT  100000D)
[    0.000000] ACPI: FACS 3FF40000, 0040
[    0.000000] ACPI: APIC 3FF30300, 0068 (r1 INTEL  D865PERL 20040402 MSFT       97)
[    0.000000] ACPI: ASF! 3FF344E0, 0099 (r16 LEGEND I865PASF        1 MSFT  100000D)
[    0.000000] ACPI: WDDT 3FF34579, 0040 (r1 INTEL  OEMWDDT         1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259890
[    0.000000] Kernel command line: root=UUID=f5380525-81bc-4b13-a3b2-4b821b83ce5c ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3192.205 MHz processor.
[   13.749782] Console: colour VGA+ 80x25
[   13.749786] console [tty0] enabled
[   13.750177] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.750557] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.775007] Memory: 1026196k/1047744k available (2157k kernel code, 20836k reserved, 998k data, 364k init, 130180k highmem)
[   13.775016] virtual kernel memory layout:
[   13.775017]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.775018]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.775019]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.775020]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.775021]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   13.775022]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   13.775022]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   13.775025] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.775068] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.854894] Calibrating delay using timer specific routine.. 6389.02 BogoMIPS (lpj=12778053)
[   13.854922] Security Framework initialized
[   13.854928] SELinux:  Disabled at boot.
[   13.854943] AppArmor: AppArmor initialized
[   13.854947] Failure registering capabilities with primary security module.
[   13.854956] Mount-cache hash table entries: 512
[   13.855089] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   13.855098] monitor/mwait feature present.
[   13.855099] using mwait in idle threads.
[   13.855105] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   13.855108] CPU: L2 cache: 1024K
[   13.855110] CPU: Physical Processor ID: 0
[   13.855112] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   13.855123] Compat vDSO mapped to ffffe000.
[   13.855138] Checking 'hlt' instruction... OK.
[   13.871274] SMP alternatives: switching to UP code
[   13.873046] Early unpacking initramfs... done
[   14.162995] ACPI: Core revision 20070126
[   14.163044] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.165071] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[   14.165090] SMP alternatives: switching to SMP code
[   14.165847] Booting processor 1/1 eip 3000
[   14.175944] Initializing CPU#1
[   14.253915] Calibrating delay using timer specific routine.. 6384.48 BogoMIPS (lpj=12768967)
[   14.253925] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   14.253932] monitor/mwait feature present.
[   14.253938] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.253940] CPU: L2 cache: 1024K
[   14.253943] CPU: Physical Processor ID: 0
[   14.253945] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   14.254313] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[   14.254353] Total of 2 processors activated (12773.51 BogoMIPS).
[   14.254480] ENABLING IO-APIC IRQs
[   14.254648] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.401692] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   14.421659] Brought up 2 CPUs
[   14.421683] CPU0 attaching sched-domain:
[   14.421686]  domain 0: span 03
[   14.421688]   groups: 01 02
[   14.421692]   domain 1: span 03
[   14.421694]    groups: 03
[   14.421696] CPU1 attaching sched-domain:
[   14.421698]  domain 0: span 03
[   14.421700]   groups: 02 01
[   14.421703]   domain 1: span 03
[   14.421704]    groups: 03
[   14.421948] net_namespace: 64 bytes
[   14.421961] Booting paravirtualized kernel on bare hardware
[   14.422576] Time: 20:39:16  Date: 04/27/08
[   14.422599] NET: Registered protocol family 16
[   14.422839] EISA bus registered
[   14.422845] ACPI: bus type pci registered
[   14.424229] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   14.424232] PCI: Using configuration type 1
[   14.424233] Setting up standard PCI resources
[   14.435040] ACPI: EC: Look up EC in DSDT
[   14.438315] ACPI: Interpreter enabled
[   14.438319] ACPI: (supports S0 S1 S4 S5)
[   14.438334] ACPI: Using IOAPIC for interrupt routing
[   14.444235] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.444708] Force enabled HPET at base address 0xfed00000
[   14.444714] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   14.444718] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   14.445450] PCI: Transparent bridge - 0000:00:1e.0
[   14.445481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.445579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.445651] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   14.447920] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   14.448071] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   14.448219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   14.448365] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   14.448511] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   14.448657] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   14.448803] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   14.448950] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   14.449097] ACPI: Power Resource [URP1] (off)
[   14.449129] ACPI: Power Resource [FDDP] (off)
[   14.449161] ACPI: Power Resource [LPTP] (off)
[   14.449216] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.449257] pnp: PnP ACPI init
[   14.449266] ACPI: bus type pnp registered
[   14.452378] pnp: PnP ACPI: found 14 devices
[   14.452381] ACPI: ACPI bus type pnp unregistered
[   14.452385] PnPBIOS: Disabled by ACPI PNP
[   14.452663] PCI: Using ACPI for IRQ routing
[   14.452667] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.473401] NET: Registered protocol family 8
[   14.473403] NET: Registered protocol family 20
[   14.473512] hpet clockevent registered
[   14.473517] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.473522] hpet0: 3 64-bit timers, 14318180 Hz
[   14.474561] AppArmor: AppArmor Filesystem Enabled
[   14.477382] Time: tsc clocksource has been installed.
[   14.489404] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   14.489412] system 00:0c: ioport range 0x400-0x47f has been reserved
[   14.489414] system 00:0c: ioport range 0x680-0x6ff has been reserved
[   14.489417] system 00:0c: ioport range 0x500-0x53f has been reserved
[   14.489420] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.489423] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   14.489426] system 00:0c: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   14.489432] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   14.489434] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   14.489437] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   14.489440] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[   14.489442] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   14.519865] PCI: Bridge: 0000:00:01.0
[   14.519868]   IO window: a000-afff
[   14.519873]   MEM window: ff800000-ff8fffff
[   14.519876]   PREFETCH window: b6b00000-f6afffff
[   14.519881] PCI: Bridge: 0000:00:1e.0
[   14.519884]   IO window: b000-bfff
[   14.519889]   MEM window: ff900000-ff9fffff
[   14.519893]   PREFETCH window: disabled.
[   14.519909] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.519921] NET: Registered protocol family 2
[   14.557257] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.557544] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.558098] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.558391] TCP: Hash tables configured (established 131072 bind 65536)
[   14.558394] TCP reno registered
[   14.569335] checking if image is initramfs... it is
[   14.972305] Switched to high resolution mode on CPU 1
[   14.976156] Switched to high resolution mode on CPU 0
[   15.141123] Freeing initrd memory: 7698k freed
[   15.141995] audit: initializing netlink socket (disabled)
[   15.142012] audit(1209328756.248:1): initialized
[   15.142203] highmem bounce pool size: 64 pages
[   15.144410] VFS: Disk quotas dquot_6.5.1
[   15.144503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.144648] io scheduler noop registered
[   15.144651] io scheduler anticipatory registered
[   15.144653] io scheduler deadline registered
[   15.144664] io scheduler cfq registered (default)
[   15.144749] Boot video device is 0000:01:00.0
[   15.145086] isapnp: Scanning for PnP cards...
[   15.496104] isapnp: No Plug & Play device found
[   15.530390] Real Time Clock Driver v1.12ac
[   15.530502] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.530616] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.531421] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.532354] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.532429] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.532560] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.535471] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.535477] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.554794] mice: PS/2 mouse device common for all mice
[   15.554940] EISA: Probing bus 0 at eisa.0
[   15.554977] EISA: Detected 0 cards.
[   15.554980] cpuidle: using governor ladder
[   15.554982] cpuidle: using governor menu
[   15.555059] NET: Registered protocol family 1
[   15.555089] Using IPI No-Shortcut mode
[   15.555117] registered taskstats version 1
[   15.555217]   Magic number: 4:272:701
[   15.555316] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.555318] EDD information not available.
[   15.555537] Freeing unused kernel memory: 364k freed
[   15.578225] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.796400] fuse init (API version 7.9)
[   16.819201] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.819237] ACPI: Processor [CPU2] (supports 8 throttling states)
[   17.034750] usbcore: registered new interface driver usbfs
[   17.034796] usbcore: registered new interface driver hub
[   17.039386] usbcore: registered new device driver usb
[   17.041634] USB Universal Host Controller Interface driver v3.0
[   17.041709] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.041723] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.041728] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.042061] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.042102] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   17.042333] usb usb1: configuration #1 chosen from 1 choice
[   17.042374] hub 1-0:1.0: USB hub found
[   17.042386] hub 1-0:1.0: 2 ports detected
[   17.146867] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   17.146884] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.146890] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.146941] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.146977] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   17.147170] usb usb2: configuration #1 chosen from 1 choice
[   17.147217] hub 2-0:1.0: USB hub found
[   17.147227] hub 2-0:1.0: 2 ports detected
[   17.250584] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.250600] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.250605] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.250640] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.250669] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   17.250828] usb usb3: configuration #1 chosen from 1 choice
[   17.250864] hub 3-0:1.0: USB hub found
[   17.250874] hub 3-0:1.0: 2 ports detected
[   17.355544] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   17.355560] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   17.355566] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   17.355605] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   17.355631] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   17.355801] usb usb4: configuration #1 chosen from 1 choice
[   17.355839] hub 4-0:1.0: USB hub found
[   17.355848] hub 4-0:1.0: 2 ports detected
[   17.383135] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   17.389272] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.462120] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   17.462147] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.462153] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.462200] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   17.466104] ehci_hcd 0000:00:1d.7: debug port 1
[   17.466113] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   17.466127] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaffc00
[   17.499660] SCSI subsystem initialized
[   17.514979] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.515168] usb usb5: configuration #1 chosen from 1 choice
[   17.515208] hub 5-0:1.0: USB hub found
[   17.515217] hub 5-0:1.0: 8 ports detected
[   17.535933] libata version 3.00 loaded.
[   17.577901] Floppy drive(s): fd0 is 1.44M
[   17.597876] FDC 0 is a National Semiconductor PC87306
[   17.621693] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   17.621700] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   17.622071] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 23 (level, low) -> IRQ 19
[   17.672772] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ff9f6800-ff9f6fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.677323] 8139too Fast Ethernet driver 0.9.28
[   17.677410] ata_piix 0000:00:1f.1: version 2.12
[   17.677428] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   17.677436] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   17.677485] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   17.678017] scsi0 : ata_piix
[   17.678095] scsi1 : ata_piix
[   17.679891] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   17.679896] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   17.850629] ata1.00: ATA-6: HDS722580VLAT20, V32OA63A, max UDMA/100
[   17.850635] ata1.00: 160836480 sectors, multi 16: LBA48 
[   17.877523] ata1.00: configured for UDMA/100
[   17.920784] usb 1-1: device not accepting address 2, error -71
[   18.356964] ata2.00: ATAPI: ASUS    DVD-E616P2, 1.02, max UDMA/100
[   18.356989] ata2.01: ATAPI: ASUS    DRW-1604P, 1.10, max UDMA/66
[   18.357002] ata2.00: limited to UDMA/33 due to 40-wire cable
[   18.528464] ata2.00: configured for UDMA/33
[   18.691069] ata2.01: configured for UDMA/66
[   18.691206] scsi 0:0:0:0: Direct-Access     ATA      HDS722580VLAT20  V32O PQ: 0 ANSI: 5
[   18.701821] scsi 1:0:0:0: CD-ROM            ASUS     DVD-E616P2       1.02 PQ: 0 ANSI: 5
[   18.707899] scsi 1:0:1:0: CD-ROM            ASUS     DRW-1604P        1.10 PQ: 0 ANSI: 5
[   18.707979] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   18.708002] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   18.708046] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.708123] scsi2 : ata_piix
[   18.708187] scsi3 : ata_piix
[   18.709106] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   18.709109] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   18.714800] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   18.894316] usb 1-1: configuration #1 chosen from 1 choice
[   18.942371] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0020026d43]
[   19.034313] ata4.00: ATA-7: WDC WD2500JS-00MVB1, 10.02E01, max UDMA/133
[   19.034318] ata4.00: 488397168 sectors, multi 16: LBA48 
[   19.050276] ata4.00: configured for UDMA/133
[   19.050413] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500JS-00M 10.0 PQ: 0 ANSI: 5
[   19.054832] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
[   19.055662] eth0: RealTek RTL8139 at 0xb800, 00:c0:26:a1:08:47, IRQ 20
[   19.055666] eth0:  Identified 8139 chip type 'RTL-8139B'
[   19.074973] Driver 'sd' needs updating - please use bus_type methods
[   19.075084] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   19.075107] sd 0:0:0:0: [sda] Write Protect is off
[   19.075111] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.075141] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.075214] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   19.075233] sd 0:0:0:0: [sda] Write Protect is off
[   19.075237] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.075266] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.075271]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.089126]  sda1
[   19.089209] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.089356] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   19.089376] sd 3:0:0:0: [sdb] Write Protect is off
[   19.089379] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   19.089410] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.089481] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   19.089499] sd 3:0:0:0: [sdb] Write Protect is off
[   19.089503] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   19.089531] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.089538]  sdb:sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   19.090461] Uniform CD-ROM driver Revision: 3.20
[   19.090527] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.105390]  sdb1 < sdb5 sdb6sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   19.120700] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   19.130555]  sdb7 > sdb2
[   19.130705] sd 3:0:0:0: [sdb] Attached SCSI disk
[   19.133770] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   19.142857] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.142892] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.142920] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   19.142958] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   19.315203] usb 1-2: configuration #1 chosen from 1 choice
[   19.318207] usbcore: registered new interface driver hiddev
[   19.340078] input: WiseGroup.,Ltd MP-8888 USB Joypad as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   19.340220] input,hidraw0: USB HID v1.00 Joystick [WiseGroup.,Ltd MP-8888 USB Joypad] on usb-0000:00:1d.0-1
[   19.362014] input: WiseGroup.,Ltd MP-8888 USB Joypad as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input3
[   19.362046] input,hidraw1: USB HID v1.00 Joystick [WiseGroup.,Ltd MP-8888 USB Joypad] on usb-0000:00:1d.0-2
[   19.362068] usbcore: registered new interface driver usbhid
[   19.362075] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.539883] Attempting manual resume
[   19.539887] swsusp: Resume From Partition 8:22
[   19.539888] PM: Checking swsusp image.
[   19.540058] PM: Resume from disk failed.
[   19.569062] kjournald starting.  Commit interval 5 seconds
[   19.569081] EXT3-fs: mounted filesystem with ordered data mode.
[   24.655859] Linux agpgart interface v0.102
[   24.707877] agpgart: Detected an Intel 865 Chipset.
[   24.711481] agpgart: AGP aperture is 64M @ 0xf8000000
[   24.739882] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.772649] iTCO_vendor_support: vendor-support=0
[   24.819654] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   24.819767] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   24.819817] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.871975] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.970591] intel_rng: FWH not detected
[   25.113080] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   25.220258] input: Power Button (FF) as /devices/virtual/input/input5
[   25.239512] ACPI: Power Button (FF) [PWRF]
[   25.239688] input: Sleep Button (CM) as /devices/virtual/input/input6
[   25.259449] ACPI: Sleep Button (CM) [SLPB]
[   26.012513] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   26.233083] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   26.233136] [fglrx] ASYNCIO init succeed!
[   26.233772] [fglrx] PAT is enabled successfully!
[   26.233799] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   26.670678] gameport: EMU10K1 is pci0000:02:04.1/gameport0, io 0xbc00, speed 1147kHz
[   27.061637] Linux video capture interface: v2.00
[   27.798315] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   27.934562] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   27.941984] phy0: Selected rate control algorithm 'simple'
[   27.991820] parport_pc 00:09: reported by Plug and Play ACPI
[   27.991873] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   28.058883] saa7130/34: v4l2 driver version 0.2.14 loaded
[   28.139413] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   28.139441] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   28.563203] intel8x0_measure_ac97_clock: measured 56032 usecs
[   28.563210] intel8x0: clocking to 48000
[   28.564427] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   28.592793] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   28.592807] saa7133[0]: found at 0000:02:03.0, rev: 16, irq: 17, latency: 32, mmio: 0xff9f7000
[   28.592816] saa7133[0]: subsystem: 11bd:002b, board: ProVideo PV952 [card=51,insmod option]
[   28.592834] saa7133[0]: board init: gpio is 0
[   28.726909] saa7133[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   28.726928] saa7133[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   28.726945] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[   28.726959] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.726974] saa7133[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 02 ff ff ff ff ff ff ff ff
[   28.726985] saa7133[0]: i2c eeprom 50: 0c 22 17 0a 02 65 89 33 ff ff ff ff ff ff ff ff
[   28.726997] saa7133[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[   28.727008] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.806587] tuner 0-0043: chip found @ 0x86 (saa7133[0])
[   28.806616] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   28.806619] tuner 0-0043: type set to tda9887
[   28.822553] Chip ID is not zero. It is not a TEA5767
[   28.822562] tuner 0-0060: chip found @ 0xc0 (saa7133[0])
[   28.822608] tuner-simple 0-0060: type set to 37 (LG PAL (newer TAPC series))
[   28.822613] tuner 0-0060: type set to LG PAL (newer TAPC 
[   28.822618] tuner-simple 0-0060: type set to 37 (LG PAL (newer TAPC series))
[   28.822622] tuner 0-0060: type set to LG PAL (newer TAPC 
[   28.825386] saa7133[0]: registered device video0 [v4l2]
[   28.825417] saa7133[0]: registered device vbi0
[   28.825450] saa7133[0]: registered device radio0
[   28.870680] saa7134 ALSA driver for DMA sound loaded
[   28.870717] saa7133[0]/alsa: saa7133[0] at 0xff9f7000 irq 17 registered as card -2
[   29.548043] lp0: using parport0 (interrupt-driven).
[   29.611855] Adding 4192924k swap on /dev/sdb6.  Priority:-1 extents:1 across:4192924k
[   30.153527] EXT3 FS on sdb7, internal journal
[   30.870367] kjournald starting.  Commit interval 5 seconds
[   30.876560] EXT3 FS on sdb5, internal journal
[   30.876565] EXT3-fs: mounted filesystem with ordered data mode.
[   31.282779] ip_tables: (C) 2000-2006 Netfilter Core Team

```


> 
yo tengo una audigy 2 pero creo que es mismo driver

por lo que veo, te la detecto lo mas bien
pega aca lo que te devuelva los siguientes comandos en consola:
cat /proc/asound/cards
despues:
cat /proc/asound/pcm
y por ultimo:
amixer scontents



cat /proc/asound/cards
```

0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at irq 20
1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xb400, irq 18
2 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xff9f7000 irq 17

```

cat /proc/asound/pcm
```

00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1
01-03: emu10k1 : Multichannel Playback : playback 1
01-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
01-01: emu10k1 mic : Mic Capture : capture 1
01-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
02-00: SAA7134 PCM : SAA7134 PCM : capture 1

```

amixer scontents
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 12 [39%] [-28.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 15 [48%] [-12.00dB] [on] Capture [off]
  Front Right: Playback 15 [48%] [-12.00dB] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'A/D Converter'
  Item0: 'AC-Link'
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 6 [40%] [-27.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 10 [32%] [-19.50dB] [on] Capture [off]
  Front Right: Playback 10 [32%] [-19.50dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Downmix',0
  Capabilities: enum
  Items: 'Off' '6 -> 4' '6 -> 2'
  Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'High Pass Filter Enable',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
  Capabilities: enum
  Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
  Item0: '2.25 V'

```


Ojalá esto les diga algo :P.

Gracias a los dos

EDIT:
> yo se que suena idiota pero me paso: proba si esta enchufado el parlante donde es, cuando me pase de windows a linux no me andaba eso y era que linux mapeaba distito las salidas.


Qué boludo, ahora que me decís esto me olvidé de comentar algo importante. La que toma es la onboard (Intel ICH5). Si enchufo ahí los parlantes funca, pero no toma la Audigy :S.

---

### Post by MeduZa on 2008-04-28
aparentemente el problema es que la onboard esta andando por defecto,
tu configuracion usa las 2
Una de 2 o mapeas la salida de la onboard a la audigy (que es un lio pero se puede) o la desactivas de la bios y no *** mas !!

es eso la audigy esta andando al pelo pero el ubuntu usa la primera de la lista que es la onboard, te recomiendo que la desactives (es mucho mejor placa la audigy)
solo por esta razon:
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1  <-----------------  SOLO UNA SALIDA LOL
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1  
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1 
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1   
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1 
01-03: emu10k1 : Multichannel Playback : playback 1    
01-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1  <---- 8 salidas PARA 5.1 a la VEZ!!!!!
01-01: emu10k1 mic : Mic Capture : capture 1
01-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1  < ------  32 SALIDAS A LA VEZ POR HARDWARE!!!
02-00: SAA7134 PCM : SAA7134 PCM : capture 1

---

### Post by sajnox on 2008-04-28
Deshabilitala del bios (a mi me paso lo mismo) eso si, aun cuando la deshabilite Linux la reconocia igual, entonces hay que hacer lo siguiente

Listado de placas que la maquina reconoce

```
asoundconf list
```

Setear la placa que queres que el eqipo use

```
asoundconf set-default-card "nombre de la tarjeta que queres usar"
```

Listo, eso deberia dirigir el audio a esa placa.

---

### Post by fepe55 on 2008-04-28
Muchas gracias muchachos. Funcionó perfecto. Ya estoy con la Audigy :).

---

### Post by sajnox on 2008-04-28
Muy bueno que lo arreglaste, pero comenta con cual de todos los metodos lo pudiste hacer.

Esta guia le puede servir a quien tenga tu mismo problema

---

### Post by fepe55 on 2008-04-28
> **sajnox said:**
> Muy bueno que lo arreglaste, pero comenta con cual de todos los metodos lo pudiste hacer.

Esta guia le puede servir a quien tenga tu mismo problema

Deshabilité la placa onBoard desde la BIOS.

Gracias de nuevo.

---

### Post by MeduZa on 2008-04-28
> **sajnox said:**
> Deshabilitala del bios (a mi me paso lo mismo) eso si, aun cuando la deshabilite Linux la reconocia igual, entonces hay que hacer lo siguiente

Listado de placas que la maquina reconoce

```
asoundconf list
```

Setear la placa que queres que el eqipo use

```
asoundconf set-default-card "nombre de la tarjeta que queres usar"
```

Listo, eso deberia dirigir el audio a esa placa.

epa, no sabia eso, yo cuando la pongo "disable" en la bios es como que la quitara de la motherboard, o sea desaparece para siempre e incluso el IRQ queda libre.

que mobo era el que te hizo esa locura?

---

### Post by sajnox on 2008-04-28
El mother es un Asus A8-V, la verdad que me sorprendi cuando descubri que ese era el problema por el que no tenia sonido.

Y cada vez que hago un clean install tengo que setearlo de nuevo

---

### Post by guillermolisi on 2008-05-01
Increible como se dan las cosas a veces.

Actualice a HH y salio todo derechito, pero todo todo (lo hice usando Aptitude, btw, porque ya tuve problemas con Adept varias veces) y no escuchaba los sonidos.

Levantaba Amarok y se veia como que estaba todo OK, que habia sonido pero no se escuchaba.
Revise los controles de Kmix y estaba todo tal como los habia dejado antes de la actualizacion, que asi funcionaba barbaro.

Busque especificamente para la placa que tengo (VIA82xx), en Alsa.org, en los foros, Google, blogs y nada que me sirviera, hasta que "volvi a casa" (este foro) y me encontre con este thread, que no era especifico para mi problema pero que me permitio "ver la luz".

Abri de nuevo Kmix y empece a jugar con los controles, particularmente los que tenia en mute.
Ahora ya estoy de nuevo escuchando Radio Paradise, Dream Theater, Jethro, etc.

Una pavada, pero que de ser tan obvia resulta invisible :-)

Thanks a lot Hei Ku.

---

### Post by Hei Ku on 2008-05-01
Medallita, medallita!!! :lolflag:

Que tal el nuevo Kubuntu? Yo estoy esperando que termine de bajar el DVD para actualizar desde ahi.

---

### Post by guillermolisi on 2008-05-01
Mira, estuve probando desde el primer beta 8.04 + KDE 4.0 y todavia no me convencio.

El otro dia, al final de la Release Party en BsAs. estabamos charlando sobre el tema y casi todos los Kubunteros opinamos mas o menos igual: Todavia le falta un poco de horno al KDE 4.0.

Ahora, Kubuntu 8.04 con 3.5.9 ? Espectacular para mi.

Varios problemitas de estabilidad para algunas aplicaciones ya estan resueltos (Firestarter por ejemplo). Como es de esperar, nuevas soluciones traen tambien nuevos problemas: No funciona bien el Superkaramba theme Liquid Weather 14.7 (lo deshabilite por ahora).

Algo que note como un gran cambio respecto de la Kubuntu 7.10: consume menos RAM (ambas situaciones medidas de la misma forma).

PS: Ya me mande la medallita, antes de mandar el mensaje :-)

---

