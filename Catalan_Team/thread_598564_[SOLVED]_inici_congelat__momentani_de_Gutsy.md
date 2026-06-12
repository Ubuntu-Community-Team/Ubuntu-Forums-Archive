---
title: "[SOLVED] inici congelat  momentani de Gutsy"
date: 2007-10-31
forum: Catalan Team
---

### Post by ilku on 2007-10-31
Hola companys:

El meu sistema es queda 2 min congelats en iniciar el Gutsy.

Portàtil antic (PIII amb 256 mb de Ram no ampliable) amb Gutsy
Antecedents:
La primera vegada vaig actualitzar des de Feisty, en vista que no iniciava correctament (trigava molt en iniciar-se), vaig decidir instal-lar des de 0 (mantenint la meva partició /home i WinXP. la resta formatades).
Com és un ordinador antic ho vaig fer de de la versió alternate, tot relativament senzill (no més complicacions que amb altres versions).
Vaig fer actualitzar el sistema. (tot correcte)
Peró encara així trigava 2 min en iniciar. Observant el sistema, els logs, etc. Vaig trobar el que crec que és el problema. Buscant informació sobre el problema vaig trobar això en el nostre fòrum amb un Feisty [http://ubuntuforums.org/showthread.php?t=542603&page=2]("http://ubuntuforums.org/showthread.php?t=542603&page=2")
és el mateix però no la mateixa solució (ja la he provat, encara que no tinc aquesta unitat maleïda :)).
Si sou tan amables de donar-me un cop de mà o bé una orientació ho agraïra molt.
Ara faré una edició del post per posar el dmesg i el missatge de error del sistema (no estic en el ordinador malmès).

EDICIÓ afegir sortides per aclarir
sistema-->administració-->registre del sistema-->messages (nomes una part)

Oct 31 10:12:06 portatil kernel: [   18.296818] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 10:12:06 portatil kernel: [   47.770591]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 31 10:12:06 portatil kernel: [   47.770610] ata1: soft resetting port
Oct 31 10:12:06 portatil kernel: [   47.950762] ata1.00: configured for UDMA/100
Oct 31 10:12:06 portatil kernel: [   47.950795] ata1: EH complete
Oct 31 10:12:06 portatil kernel: [   77.933396]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 31 10:12:06 portatil kernel: [   77.933416] ata1: soft resetting port
Oct 31 10:12:06 portatil kernel: [   78.113559] ata1.00: configured for UDMA/100
Oct 31 10:12:06 portatil kernel: [   78.113601] ata1: EH complete
Oct 31 10:12:06 portatil kernel: [  108.096193]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 31 10:12:06 portatil kernel: [  108.096213] ata1: soft resetting port
Oct 31 10:12:06 portatil kernel: [  108.276362] ata1.00: configured for UDMA/100
Oct 31 10:12:06 portatil kernel: [  108.276402] ata1: EH complete
Oct 31 10:12:06 portatil kernel: [  138.258977] ata1.00: limiting speed to UDMA/66:PIO4
Oct 31 10:12:06 portatil kernel: [  138.259009]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 31 10:12:06 portatil kernel: [  138.259029] ata1: soft resetting port
Oct 31 10:12:06 portatil kernel: [  138.439075] ata1.00: configured for UDMA/66
Oct 31 10:12:06 portatil kernel: [  138.439113] ata1: EH complete
Oct 31 10:12:06 portatil kernel: [  138.466500]  sda1 sda2 sda3 <<5>sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)

$dmesg (poso tota la sortida per si de cas)
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000eff0000 (usable)
[    0.000000]  BIOS-e820: 000000000eff0000 - 000000000efffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000efffc00 - 000000000f000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 239MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 61424) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    61424
[    0.000000]   HighMem     61424 ->    61424
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    61424
[    0.000000] On node 0 totalpages: 61424
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 447 pages used for memmap
[    0.000000]   Normal zone: 56881 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6E90 checksum 0
[    0.000000] ACPI: RSDP 000F6E90, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0EFFC674, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0EFFFB64, 0074 (r1   MTC    7521    6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 0EFFC6A0, 34C4 (r1   MTC      7521  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 0EFFFFC0, 0040
[    0.000000] ACPI: BOOT 0EFFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0f000000:f0f80000)
[    0.000000] Built 1 zonelists.  Total pages: 60945
[    0.000000] Kernel command line: root=UUID=d4fa21fa-6195-43db-a7eb-c6616dd57f5e ro vga=791=quiet splash irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (011ec000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1136.009 MHz processor.
[  151.265941] Console: colour dummy device 80x25
[  151.266606] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  151.267145] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  151.285507] Memory: 232076k/245696k available (2015k kernel code, 13064k reserved, 916k data, 364k init, 0k highmem)
[  151.285543] virtual kernel memory layout:
[  151.285546]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  151.285548]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  151.285551]     vmalloc : 0xcf800000 - 0xff7fe000   ( 767 MB)
[  151.285554]     lowmem  : 0xc0000000 - 0xceff0000   ( 239 MB)
[  151.285556]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  151.285559]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[  151.285562]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[  151.285594] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  151.285680] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  151.365715] Calibrating delay using timer specific routine.. 2283.21 BogoMIPS (lpj=4566432)
[  151.365777] Security Framework v1.0.0 initialized
[  151.365799] SELinux:  Disabled at boot.
[  151.365832] Mount-cache hash table entries: 512
[  151.366092] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  151.366113] CPU: L1 I cache: 16K, L1 D cache: 16K
[  151.366124] CPU: L2 cache: 256K
[  151.366133] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  151.366153] Compat vDSO mapped to ffffe000.
[  151.366182] Checking 'hlt' instruction... OK.
[  151.381842] SMP alternatives: switching to UP code
[  151.382130] Freeing SMP alternatives: 11k freed
[  151.382643] Early unpacking initramfs... done
[  151.996674] ACPI: Core revision 20070126
[  151.996885] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  151.999320] ACPI: setting ELCR to 0800 (from 0a20)
[  151.999927] CPU0: Intel(R) Pentium(R) III CPU             1133MHz stepping 01
[  151.999947] SMP motherboard not detected.
[  151.999955] Local APIC not detected. Using dummy APIC emulation.
[  152.000063] Brought up 1 CPUs
[  152.000379] Booting paravirtualized kernel on bare hardware
[  152.000534] Time: 18:56:08  Date: 09/31/107
[  152.000614] NET: Registered protocol family 16
[  152.000911] EISA bus registered
[  152.000949] ACPI: bus type pci registered
[  152.024953] PCI: PCI BIOS revision 2.10 entry at 0xfd9ce, last bus=1
[  152.024966] PCI: Using configuration type 1
[  152.024974] Setting up standard PCI resources
[  152.030294] ACPI: EC: Look up EC in DSDT
[  152.033068] ACPI: EC: GPE=0x02, ports=0x66, 0x62
[  152.034663] ACPI: Interpreter enabled
[  152.034679] ACPI: (supports S0 S3 S4 S5)
[  152.034709] ACPI: Using PIC for interrupt routing
[  152.078614] ACPI: EC: GPE=0x02, ports=0x66, 0x62
[  152.078748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  152.078774] PCI: Probing PCI hardware (bus 00)
[  152.079593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  152.286906] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 11) *0, disabled.
[  152.287077] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 11)
[  152.287219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *11)
[  152.287361] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9)
[  152.287568] Linux Plug and Play Support v0.97 (c) Adam Belay
[  152.287612] pnp: PnP ACPI init
[  152.287645] ACPI: bus type pnp registered
[  152.347118] pnp: PnP ACPI: found 13 devices
[  152.347143] ACPI: ACPI bus type pnp unregistered
[  152.347156] PnPBIOS: Disabled by ACPI PNP
[  152.347297] PCI: Using ACPI for IRQ routing
[  152.347308] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  152.349048] NET: Registered protocol family 8
[  152.349057] NET: Registered protocol family 20
[  152.349216] Time: tsc clocksource has been installed.
[  152.349337] pnp: 00:05: iomem range 0x0-0x9ffff could not be reserved
[  152.349349] pnp: 00:05: iomem range 0xdc000-0xdffff has been reserved
[  152.349359] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[  152.349369] pnp: 00:05: iomem range 0xfffe0000-0xffffffff could not be reserved
[  152.349387] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[  152.349396] pnp: 00:06: ioport range 0x398-0x399 has been reserved
[  152.349406] pnp: 00:06: ioport range 0x9000-0x907f has been reserved
[  152.349414] pnp: 00:06: ioport range 0x481-0x483 has been reserved
[  152.349440] pnp: 00:06: ioport range 0x487-0x487 has been reserved
[  152.349449] pnp: 00:06: ioport range 0x489-0x48b has been reserved
[  152.380128] PCI: Bridge: 0000:00:02.0
[  152.380143]   IO window: a000-afff
[  152.380153]   MEM window: ec100000-ec1fffff
[  152.380162]   PREFETCH window: f0000000-f7ffffff
[  152.380173] PCI: Bus 2, cardbus bridge: 0000:00:08.0
[  152.380181]   IO window: 00002000-000020ff
[  152.380189]   IO window: 00002400-000024ff
[  152.380198]   PREFETCH window: 10000000-13ffffff
[  152.380207]   MEM window: 14000000-17ffffff
[  152.380216] PCI: Bus 6, cardbus bridge: 0000:00:08.1
[  152.380223]   IO window: 00002800-000028ff
[  152.380231]   IO window: 00002c00-00002cff
[  152.380240]   PREFETCH window: 18000000-1bffffff
[  152.380249]   MEM window: 1c000000-1fffffff
[  152.380268] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  152.380671] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[  152.380683] PCI: setting IRQ 9 as level-triggered
[  152.380688] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[  152.380715] ACPI: PCI Interrupt 0000:00:08.1[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[  152.380759] NET: Registered protocol family 2
[  152.417328] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  152.417444] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[  152.417735] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  152.417962] TCP: Hash tables configured (established 8192 bind 8192)
[  152.417974] TCP reno registered
[  152.429562] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[  152.907044]  it is
[  153.567886] Freeing initrd memory: 7063k freed
[  153.568230] Simple Boot Flag at 0x39 set to 0x1
[  153.569069] audit: initializing netlink socket (disabled)
[  153.569122] audit(1193856970.068:1): initialized
[  153.574269] VFS: Disk quotas dquot_6.5.1
[  153.574483] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  153.574785] io scheduler noop registered
[  153.574800] io scheduler anticipatory registered
[  153.574808] io scheduler deadline registered
[  153.574887] io scheduler cfq registered (default)
[  153.574952] Boot video device is 0000:01:00.0
[  153.575332] isapnp: Scanning for PnP cards...
[  153.931901] isapnp: No Plug & Play device found
[  154.018430] Real Time Clock Driver v1.12ac
[  154.018652] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  154.018830] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  154.019327] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[  154.021099] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  154.022073] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[  154.022094] PCI: setting IRQ 11 as level-triggered
[  154.022098] ACPI: PCI Interrupt 0000:00:01.6[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  154.022120] ACPI: PCI interrupt for device 0000:00:01.6 disabled
[  154.023369] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  154.023907] input: Macintosh mouse button emulation as /class/input/input0
[  154.024097] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  154.026100] serio: i8042 KBD port at 0x60,0x64 irq 1
[  154.026130] serio: i8042 AUX port at 0x60,0x64 irq 12
[  154.026567] mice: PS/2 mouse device common for all mice
[  154.026824] EISA: Probing bus 0 at eisa.0
[  154.026849] Cannot allocate resource for EISA slot 1
[  154.026858] Cannot allocate resource for EISA slot 2
[  154.026897] Cannot allocate resource for EISA slot 8
[  154.026904] EISA: Detected 0 cards.
[  154.027134] TCP cubic registered
[  154.027181] NET: Registered protocol family 1
[  154.027252] Using IPI No-Shortcut mode
[  154.027628]   Magic number: 11:156:950
[  154.027671]   hash matches device ttya5
[  154.027851]   hash matches device tty7
[  154.029326] Freeing unused kernel memory: 364k freed
[  154.052621] input: AT Translated Set 2 keyboard as /class/input/input1
[  155.537024] AppArmor: AppArmor initialized<5>audit(1193856972.068:2):  type=1505 info="AppArmor initialized" pid=1176
[  155.557684] fuse init (API version 7.8)
[  155.569732] Failure registering capabilities with primary security module.
[  155.603201] ACPI: Processor [CPU0] (supports 8 throttling states)
[  157.100498] SCSI subsystem initialized
[  157.118598] libata version 2.21 loaded.
[  157.123653] pata_sis 0000:00:00.1: version 0.5.1
[  157.124040] scsi0 : pata_sis
[  157.124142] scsi1 : pata_sis
[  157.124358] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011c80 irq 14
[  157.124365] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011c88 irq 15
[  157.212324] usbcore: registered new interface driver usbfs
[  157.212384] usbcore: registered new interface driver hub
[  157.212443] usbcore: registered new device driver usb
[  157.215358] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  157.287185] ata1.00: ATA-7: FUJITSU MHV2120AT, 000000A0, max UDMA/100
[  157.287199] ata1.00: 234441648 sectors, multi 16: LBA 
[  157.303218] ata1.00: configured for UDMA/100
[  157.344911] sis900.c: v1.08.10 Apr. 2 2006
[  157.622939] ata2.00: ATAPI: CD-W24E, 1.0A, max MWDMA2
[  157.662876] Floppy drive(s): fd0 is 1.44M
[  157.682069] FDC 0 is a National Semiconductor PC87306
[  157.794696] ata2.00: configured for PIO4
[  157.795005] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120A 0000 PQ: 0 ANSI: 5
[  157.795549] scsi 1:0:0:0: CD-ROM            TEAC     CD-W24E          1.0A PQ: 0 ANSI: 5
[  157.802336] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[  157.802350] PCI: setting IRQ 5 as level-triggered
[  157.802355] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[  157.802384] ohci_hcd 0000:00:01.2: OHCI Host Controller
[  157.802843] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[  157.802885] ohci_hcd 0000:00:01.2: irq 5, io mem 0xec000000
[  157.847505] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  157.849887] sd 0:0:0:0: [sda] Write Protect is off
[  157.849903] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  157.849979] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  157.850125] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  157.850146] sd 0:0:0:0: [sda] Write Protect is off
[  157.850152] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  157.850181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  157.850193]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[  157.860859] hub 1-0:1.0: USB hub found
[  157.860884] hub 1-0:1.0: 3 ports detected
[  157.962960] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  157.963892] 0000:00:09.0: SiS 900 Internal MII PHY transceiver found at address 1.
[  157.970829] 0000:00:09.0: Using transceiver found at address 1 as default
[  158.266355] usb 1-2: new low speed USB device using ohci_hcd and address 2
[  158.480307] usb 1-2: configuration #1 chosen from 1 choice
[  158.515231] usbcore: registered new interface driver hiddev
[  158.524190] input: Logitech Logitech USB Optical Mouse as /class/input/input2
[  158.524567] input: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:01.2-2
[  158.524605] usbcore: registered new interface driver usbhid
[  158.524614] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  159.626766] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 11, 00:40:d0:1e:81:b9.
[  187.831454] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  187.831477] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  187.831480]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  187.831501] ata1: soft resetting port
[  188.011688] ata1.00: configured for UDMA/100
[  188.011732] ata1: EH complete
[  217.996296] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  217.996318] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  217.996322]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  217.996342] ata1: soft resetting port
[  218.176499] ata1.00: configured for UDMA/100
[  218.176542] ata1: EH complete
[  248.161139] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  248.161160] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  248.161163]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  248.161183] ata1: soft resetting port
[  248.341342] ata1.00: configured for UDMA/100
[  248.341382] ata1: EH complete
[  278.325982] ata1.00: limiting speed to UDMA/66:PIO4
[  278.325998] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  278.326011] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  278.326015]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  278.326034] ata1: soft resetting port
[  278.506097] ata1.00: configured for UDMA/66
[  278.506140] ata1: EH complete
[  278.533695]  sda1 sda2 sda3 <<5>sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  278.558112] sd 0:0:0:0: [sda] Write Protect is off
[  278.558129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  278.558178]  sda5<5>sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  278.575995]  sda6<5>sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  278.595381]  sda7 >
[  278.597319] sd 0:0:0:0: [sda] Attached SCSI disk
[  278.597932] sd 0:0:0:0: [sda] Write Protect is off
[  278.597943] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  278.608444] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  278.611489] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  278.611819] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[  278.631083] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[  278.631099] Uniform CD-ROM driver Revision: 3.20
[  278.631730] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  279.133002] Attempting manual resume
[  279.133012] swsusp: Resume From Partition 8:6
[  279.133016] PM: Checking swsusp image.
[  279.133389] PM: Resume from disk failed.
[  279.208017] kjournald starting.  Commit interval 5 seconds
[  279.208053] EXT3-fs: mounted filesystem with ordered data mode.
[  290.943382] Linux agpgart interface v0.102 (c) Dave Jones
[  291.102493] agpgart: Detected SiS chipset - id:1584
[  291.107091] agpgart: AGP aperture is 64M @ 0xe8000000
[  291.308379] Yenta: CardBus bridge found at 0000:00:08.0 [1071:7522]
[  291.308406] Yenta: Enabling burst memory read transactions
[  291.308412] Yenta: Using CSCINT to route CSC interrupts to PCI
[  291.308416] Yenta: Routing CardBus interrupts to PCI
[  291.308423] Yenta TI: socket 0000:00:08.0, mfunc 0x01001000, devctl 0x66
[  291.323683] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  291.539754] Yenta: ISA IRQ mask 0x0498, PCI irq 9
[  291.539766] Socket status: 30000006
[  291.540175] Yenta: CardBus bridge found at 0000:00:08.1 [1071:7522]
[  291.540196] Yenta: Using CSCINT to route CSC interrupts to PCI
[  291.540200] Yenta: Routing CardBus interrupts to PCI
[  291.540207] Yenta TI: socket 0000:00:08.1, mfunc 0x01001000, devctl 0x66
[  291.771744] Yenta: ISA IRQ mask 0x0498, PCI irq 9
[  291.771756] Socket status: 30000006
[  291.772206] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  292.047915] input: PC Speaker as /class/input/input3
[  292.621737] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x8848a1, caps: 0x0/0x0
[  292.651075] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  292.890155] parport_pc 00:09: reported by Plug and Play ACPI
[  292.890231] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  292.923670] irda_init()
[  292.923712] NET: Registered protocol family 23
[  292.984003] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
[  292.984040] nsc-ircc, chip->init
[  292.984049] nsc-ircc, Found chip at base=0x398
[  292.984080] nsc-ircc, driver loaded (Dag Brattli)
[  292.984096] nsc_ircc_open(), can't get iobase of 0x2f8
[  292.984129] nsc-ircc, Found chip at base=0x398
[  292.984159] nsc-ircc, driver loaded (Dag Brattli)
[  292.984164] nsc_ircc_open(), can't get iobase of 0x2f8
[  292.989660] pnp: Device 00:0b disabled.
[  293.693130] cs: IO port probe 0x100-0x3af: clean.
[  293.695715] cs: IO port probe 0x3e0-0x4ff: clean.
[  293.696700] cs: IO port probe 0x820-0x8ff: clean.
[  293.697590] cs: IO port probe 0xc00-0xcf7: clean.
[  293.698747] cs: IO port probe 0xa00-0xaff: clean.
[  293.760863] cs: IO port probe 0x100-0x3af: clean.
[  293.763530] cs: IO port probe 0x3e0-0x4ff: clean.
[  293.764515] cs: IO port probe 0x820-0x8ff: clean.
[  293.765406] cs: IO port probe 0xc00-0xcf7: clean.
[  293.766586] cs: IO port probe 0xa00-0xaff: clean.
[  293.928739] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[  293.928754] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[  294.990657] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2593kHz
[  296.138370] loop: module loaded
[  296.176466] lp0: using parport0 (interrupt-driven).
[  296.322658] Adding 1975952k swap on /dev/sda6.  Priority:-1 extents:1 across:1975952k
[  296.714596] EXT3 FS on sda2, internal journal
[  300.078348] kjournald starting.  Commit interval 5 seconds
[  300.078732] EXT3 FS on sda5, internal journal
[  300.078744] EXT3-fs: mounted filesystem with ordered data mode.
[  302.663511] NET: Registered protocol family 17
[  303.476396] No dock devices found.
[  303.636667] ACPI: AC Adapter [ACAD] (on-line)
[  303.675282] ACPI: Battery Slot [BAT0] (battery present)
[  303.921156] input: Power Button (CM) as /class/input/input5
[  303.921783] ACPI: Power Button (CM) [PWRB]
[  303.957141] input: Sleep Button (CM) as /class/input/input6
[  303.957778] ACPI: Sleep Button (CM) [SLPB]
[  303.977118] input: Lid Switch as /class/input/input7
[  303.977802] ACPI: Lid Switch [LID]
[  306.303329] ppdev: user-space parallel port driver
[  306.527928] ttyS1: LSR safety check engaged!
[  306.738796] audit(1193853523.348:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=8194 profile="/usr/sbin/cupsd"
[  306.853007] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  306.853020] apm: overridden by ACPI.
[  308.507331] eth0: Media Link On 100mbps full-duplex 
[  308.554277] Failure registering capabilities with primary security module.
[  313.127811] [drm] Initialized drm 1.1.0 20060810
[  313.201882] [drm] Initialized sis 1.3.0 20070626 on minor 0
[  313.203495] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  313.203951] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  313.204348] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  318.036531] NET: Registered protocol family 10
[  318.037011] lo: Disabled Privacy Extensions
[  328.089334] eth0: no IPv6 routers present

$sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       FUJITSU MHV2120AT                       
        Serial Number:      NS17T7429GNM
        Firmware Revision:  000000A0
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 4a 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  234441648
        device size with M = 1024*1024:      114473 MBytes
        device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
        LBA, IORDY(cannot be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: 128 (0x80)
        Recommended acoustic management value: 254, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                Power-Up In Standby feature set
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    SMART error logging
           *    SMART self-test
           *    IDLE_IMMEDIATE with UNLOAD
           *    SMART Command Transport (SCT) feature set
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
        120min for SECURITY ERASE UNIT. 
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

---

### Post by Kosimo on 2007-10-31
Una pregunta:

Quan dius que es queda congelat. Veus alguna cosa a la pantalla? O es queda completament negra?

---

### Post by ilku on 2007-11-01
Perdona la teva pregunta em recorda que ho hauria d'haver posat ja d'entrada.
El Ubuntu iniciava i es quedava en el splash inicial. Llavors vaig fer Crtl+Alt+F1 per obrir una altre tty i veure que passava. I és on vaig veure els errors aquests. (és carrega de sistema i per tant no tinc consola encara). Al cap d'una estona, 2 min, iniciava.
Se'm va acudir posar uns quants paràmetres al grub (Vga=791 irqpoll, etc) tal com tenia avans amb el feisty per tal d'optimitzar una mica.

Aixo tampoc ho havia comentat:
El feisty m'anava correctament.
Per si algú m'ho diu, ja responc, No puc iniciar el CD-Autònom, ja que no tinc prou ram al sistema.

El sistema arrenca, em aquests errors, però arrenca.

---

### Post by ilku on 2007-11-14
Doncs mirant el panorama, es veu que es una errada que te tela. Resulta que algú molt "intel·ligent" se li va acudir modificar el modul pata-generic o una cosa semblant, i aquest no funciona del tot correctament. En comptes de deixar allò que funcionava, si mes no a mi i uns quants mes, van decidir incloure'l al gutsy.
Doncs be fins que no solucionen aquest problema, la solució passa per tornar a feisty on aquest maleït modul no hi és.

Nota: perdoneu el to però estic emprenyat.

---

### Post by CarlesOriol on 2007-11-15
pots dir el nom exacte del mòdul?

---

