---
title: "Problema amb lector/gravadors de cd/dvd"
date: 2011-04-19
forum: Catalan Team
---

### Post by Original Flo on 2011-04-19
Bon dia a tothom, aquest es el meu primer misatge en aquest fòrum. Disculpeu la meva ortografia, però esque no estic acostumat a escriure en català Us explico el meu problema.

Abans de res dir que porto uns 6 mesos amb el problema, he buscat per google, he llegit un munt, he preguntat a d'altres fòrums i de moment l'únic que he trobat es gent al el mateix problema i sense solució.

El problema va començar amb la actualització a 10.10, desde aquell moment les gravadores em van deixar de funcionar al meu ordinador (laptop), però també quan vaig anar a casa dels meus pares i els i vaig instal·lar ubuntu 10.10 (instal·lació neta) tampoc els hi gravava.

Vaig fer lo que em van recomanar [en un altre fòrum]("http://www.ubuntu-es.org/node/144644"), i la cosa va empitjorar, primer em va deixar de llegir els cd's grabables o grabats y nomes em lleigía els original i ara ya no em llegeix ni els originals.

M'agradaria fer una instal·lació de 0 al meu laptop (he provat moltes coses i crec que es lo últim que em queda per provar), però quan poso un livecd, no mel reconeix ni al iniciar l'ordinador.

El meu ordinador es un laptop HP dv7 1250es i la gravadora de cd/dvd que tinc ara es una HP DVDRAM GT20L. Està nova, la vaig posar nova i no la he utilitzat pràcticament ja que no funcionava (vaig gravar un parell de cd's quan tenia ubuntu 10.04 i encara em funcionava), igual que li passava a la que tenia abans, que la vaig canviar pensant que seria problema de la gravadora, però al posar una nova, el problema persisteix.

Espero que algú em pugui ajudar encara que nomes sigui per que llegeixi o per poder, d'alguna manera, fer una nova instal·lació de 0.

Gracies anticipades.

---

### Post by wgarcia on 2011-04-19
Quan dius:

> **Original Flo said:**
> però quan poso un livecd, no mel reconeix ni al iniciar l'ordinador.

vols dir que no et llegeix el livecd? Pots provar de preparar un live usb, i provar si des del live usb et funciona la gravadora. Per arrencar el live usb un cop creat has de dir-li a l'ordinador que arrenqui des d'aquest dispositiu, es pot fer des del menú que pots obrir abans d'iniciar l'ordinador (amb F2 o la tecla que correspongui al teu ordinador). 

Per preparar un live usb pots mirar 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

la pàgina de descàrrega de l'Ubuntu on expliquen com crear-se un.

Una altra cosa que pot servir és intentar fer anar la unitat de CD i mirar les últimes línies que et surten si entres en una terminal:

dmesg

Aquestes últimes línies poden contindre errors que hagi produït la unitat de CD i poden donar pistes sobre per què no funciona.

---

### Post by Original Flo on 2011-04-19
> **wgarcia said:**
> Quan dius:



vols dir que no et llegeix el livecd? Pots provar de preparar un live usb, i provar si des del live usb et funciona la gravadora. Per arrencar el live usb un cop creat has de dir-li a l'ordinador que arrenqui des d'aquest dispositiu, es pot fer des del menú que pots obrir abans d'iniciar l'ordinador (amb F2 o la tecla que correspongui al teu ordinador). 

Per preparar un live usb pots mirar 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

la pàgina de descàrrega de l'Ubuntu on expliquen com crear-se un.

Una altra cosa que pot servir és intentar fer anar la unitat de CD i mirar les últimes línies que et surten si entres en una terminal:

dmesg

Aquestes últimes línies poden contindre errors que hagi produït la unitat de CD i poden donar pistes sobre per què no funciona.

Per fer lo del USB, ha de ser un pen drive per força, o es por utilitzar qualsevol unitat d'emmagatzemament que vagi per USB, com un mp3?

I sobre lo altre, entenc que per fer "dmesg", ho haig de fer una vegada "dintre" de l'unitat de cddvd, com entro en aquesta unitat amb el terminal.

Gracies.

---

### Post by wgarcia on 2011-04-19
En quant a la primera pregunta, no ho sé, suposo que a un mp3 l'ordinador el veu com una unitat de disc usb, però no sé si gravar l'arrencada al mp3 no pot danyar altres elements que faci servir per al funcionament com reproductor de fitxers mp3. 

Quant a la segona pregunta, no, des d'Aplicacions -> Terminal, s'ha d'obrir una terminal. Posar algun disc a la unitat de CD, i després anar a la terminal i esciure

dmesg

i intro. Mostrarà per pantalla molta informació, però s'ha de mirar a les últimes línies a veure si mostra algun error que pugui estar relacionat amb la unitat de CD.

---

### Post by Original Flo on 2011-04-19
He posat un disc al terminal.

He fet el demesg, aixo es lo que m'ha tornat.


> [    0.497780] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.497783] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.497786] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.497788] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.497791] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.497794] pci_bus 0000:00: resource 19 [mem 0xe1000000-0xffffffff]
[    0.497798] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.497801] pci_bus 0000:01: resource 1 [mem 0xd2300000-0xd23fffff]
[    0.497804] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.497807] pci_bus 0000:02: resource 0 [io  0x3000-0x6fff]
[    0.497810] pci_bus 0000:02: resource 1 [mem 0xd1300000-0xd22fffff]
[    0.497813] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.497816] pci_bus 0000:08: resource 1 [mem 0xd1200000-0xd12fffff]
[    0.497819] pci_bus 0000:09: resource 1 [mem 0xd1100000-0xd11fffff]
[    0.497822] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
[    0.497825] pci_bus 0000:0a: resource 1 [mem 0xd2500000-0xd25fffff]
[    0.497828] pci_bus 0000:0a: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.497831] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.497834] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    0.497837] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    0.497840] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    0.497843] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.497845] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.497848] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.497851] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.497854] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.497857] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.497860] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    0.497863] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.497866] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.497869] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.497872] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    0.497875] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.497878] pci_bus 0000:80: resource 19 [mem 0xe1000000-0xffffffff]
[    0.497920] NET: Registered protocol family 2
[    0.498000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.498317] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.499029] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.499363] TCP: Hash tables configured (established 131072 bind 65536)
[    0.499366] TCP reno registered
[    0.499371] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.499384] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.499499] NET: Registered protocol family 1
[    0.499685] pci 0000:01:00.0: Boot video device
[    0.499711] PCI: CLS 64 bytes, default 64
[    0.499775] Simple Boot Flag at 0x44 set to 0x1
[    0.499984] cpufreq-nforce2: No nForce2 chipset.
[    0.500091] Scanning for low memory corruption every 60 seconds
[    0.500259] audit: initializing netlink socket (disabled)
[    0.500270] type=2000 audit(1303214576.496:1): initialized
[    0.511966] highmem bounce pool size: 64 pages
[    0.511972] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.513460] VFS: Disk quotas dquot_6.5.2
[    0.513525] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.514345] fuse init (API version 7.14)
[    0.514452] msgmni has been set to 1603
[    0.584557] Freeing initrd memory: 14940k freed
[    0.598247] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.598252] io scheduler noop registered
[    0.598255] io scheduler deadline registered
[    0.598282] io scheduler cfq registered (default)
[    0.598445] pcieport 0000:00:02.0: setting latency timer to 64
[    0.598485]   alloc irq_desc for 40 on node -1
[    0.598488]   alloc kstat_irqs on node -1
[    0.598502] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.598587] pcieport 0000:00:04.0: setting latency timer to 64
[    0.598618]   alloc irq_desc for 41 on node -1
[    0.598620]   alloc kstat_irqs on node -1
[    0.598626] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.598712] pcieport 0000:00:05.0: setting latency timer to 64
[    0.598743]   alloc irq_desc for 42 on node -1
[    0.598745]   alloc kstat_irqs on node -1
[    0.598751] pcieport 0000:00:05.0: irq 42 for MSI/MSI-X
[    0.598824] pcieport 0000:00:06.0: setting latency timer to 64
[    0.598854]   alloc irq_desc for 43 on node -1
[    0.598856]   alloc kstat_irqs on node -1
[    0.598862] pcieport 0000:00:06.0: irq 43 for MSI/MSI-X
[    0.598934] pcieport 0000:00:07.0: setting latency timer to 64
[    0.598964]   alloc irq_desc for 44 on node -1
[    0.598966]   alloc kstat_irqs on node -1
[    0.598972] pcieport 0000:00:07.0: irq 44 for MSI/MSI-X
[    0.599074] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.599222] \_SB_.PCI0:_OSC request failed
[    0.599224] _OSC request data:1 0 1f 
[    0.599345] \_SB_.PCI0:_OSC request failed
[    0.599347] _OSC request data:1 0 1f 
[    0.599371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.603797] ACPI: AC Adapter [ACAD] (on-line)
[    0.603889] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.603897] ACPI: Power Button [PWRB]
[    0.603984] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.604134] ACPI: Lid Switch [LID]
[    0.604187] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.604192] ACPI: Power Button [PWRF]
[    0.604670] ACPI: acpi_idle registered with cpuidle
[    0.706943] thermal LNXTHERM:01: registered as thermal_zone0
[    0.706953] ACPI: Thermal Zone [TZ01] (63 C)
[    0.707036] ERST: Table is not found!
[    0.707105] isapnp: Scanning for PnP cards...
[    0.707268] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.708852] brd: module loaded
[    0.709434] loop: module loaded
[    0.709783] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.709868] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.710250] Fixed MDIO Bus: probed
[    0.710290] PPP generic driver version 2.4.2
[    0.710332] tun: Universal TUN/TAP device driver, 1.6
[    0.710334] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.710432] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.710485] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.710510] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.710514] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.710550] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.710620] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.710637] ehci_hcd 0000:00:12.2: debug port 1
[    0.710669] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2408500
[    0.720558] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.720701] hub 1-0:1.0: USB hub found
[    0.720707] hub 1-0:1.0: 6 ports detected
[    0.720879] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.720893] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.720897] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.720931] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.720955] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.720970] ehci_hcd 0000:00:13.2: debug port 1
[    0.720993] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2408400
[    0.732557] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.732661] hub 2-0:1.0: USB hub found
[    0.732665] hub 2-0:1.0: 6 ports detected
[    0.732747] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732794] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.732806] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.732810] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.732847] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.732914] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2407000
[    0.792653] hub 3-0:1.0: USB hub found
[    0.792693] hub 3-0:1.0: 3 ports detected
[    0.792769] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.792782] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    0.792785] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.792825] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.792883] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2406000
[    0.852645] hub 4-0:1.0: USB hub found
[    0.852685] hub 4-0:1.0: 3 ports detected
[    0.852754] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.852766] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    0.852770] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.852804] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.852830] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2405000
[    0.912649] hub 5-0:1.0: USB hub found
[    0.912690] hub 5-0:1.0: 3 ports detected
[    0.912758] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.912770] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    0.912774] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.912813] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.912869] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2404000
[    0.972644] hub 6-0:1.0: USB hub found
[    0.972684] hub 6-0:1.0: 3 ports detected
[    0.972767] uhci_hcd: USB Universal Host Controller Interface driver
[    0.972875] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.008691] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.008709] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.008779] mice: PS/2 mouse device common for all mice
[    1.008951] rtc_cmos 00:04: RTC can wake from S4
[    1.008995] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.009058] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.009205] device-mapper: uevent: version 1.0.3
[    1.009379] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.009494] device-mapper: multipath: version 1.1.1 loaded
[    1.009497] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.009680] EISA: Probing bus 0 at eisa.0
[    1.009683] EISA: Cannot allocate resource for mainboard
[    1.009686] Cannot allocate resource for EISA slot 1
[    1.009689] Cannot allocate resource for EISA slot 2
[    1.009692] Cannot allocate resource for EISA slot 3
[    1.009694] Cannot allocate resource for EISA slot 4
[    1.009697] Cannot allocate resource for EISA slot 5
[    1.009699] Cannot allocate resource for EISA slot 6
[    1.009702] Cannot allocate resource for EISA slot 7
[    1.009705] Cannot allocate resource for EISA slot 8
[    1.009707] EISA: Detected 0 cards.
[    1.009819] cpuidle: using governor ladder
[    1.009822] cpuidle: using governor menu
[    1.010147] TCP cubic registered
[    1.010331] NET: Registered protocol family 10
[    1.010754] lo: Disabled Privacy Extensions
[    1.011008] NET: Registered protocol family 17
[    1.011045] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual-Core QL-64 (2 cpu cores) (version 2.20.00)
[    1.011097] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.011099] powernow-k8:    1 : pstate 1 (1050 MHz)
[    1.044651] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.066201] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.088772] isapnp: No Plug & Play device found
[    1.088932] Using IPI No-Shortcut mode
[    1.089061] PM: Resume from disk failed.
[    1.089077] registered taskstats version 1
[    1.089617]   Magic number: 7:647:26
[    1.089778] rtc_cmos 00:04: setting system clock to 2011-04-19 12:02:58 UTC (1303214578)
[    1.089781] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.089784] EDD information not available.
[    1.089934] Freeing unused kernel memory: 708k freed
[    1.090543] Write protecting the kernel text: 5096k
[    1.090656] Write protecting the kernel read-only data: 2016k
[    1.118124] udev[77]: starting version 163
[    1.190720] ACPI: Battery Slot [BAT0] (battery present)
[    1.204239] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.210882] acpi device:08: registered as cooling_device2
[    1.212289] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:06/LNXVIDEO:01/input/input4
[    1.212383] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    1.364583] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.422783] sdhci: Secure Digital Host Controller Interface driver
[    1.422787] sdhci: Copyright(c) Pierre Ossman
[    1.424269] sdhci-pci 0000:08:00.1: SDHCI controller found [197b:2382] (rev 0)
[    1.424326] sdhci-pci 0000:08:00.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.424379] sdhci-pci 0000:08:00.1: setting latency timer to 64
[    1.424429] Registered led device: mmc0::
[    1.424478] mmc0: SDHCI controller on PCI [0000:08:00.1] using DMA
[    1.424603] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.441931] scsi0 : pata_atiixp
[    1.444415] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.444445] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.444584] r8169 0000:0a:00.0: setting latency timer to 64
[    1.444680]   alloc irq_desc for 45 on node -1
[    1.444682]   alloc kstat_irqs on node -1
[    1.444698] r8169 0000:0a:00.0: irq 45 for MSI/MSI-X
[    1.445234] r8169 0000:0a:00.0: eth0: RTL8168c/8111c at 0xf8532000, 00:1e:ec:fc:99:ee, XID 1c2000c0 IRQ 45
[    1.449289] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.449298] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
[    1.449334] sdhci-pci 0000:08:00.2: PCI INT A disabled
[    1.453002] scsi1 : pata_atiixp
[    1.454129] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
[    1.454133] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
[    1.614769] firewire_ohci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.614779] firewire_ohci 0000:08:00.0: setting latency timer to 64
[    1.614955] ahci 0000:00:11.0: version 3.0
[    1.615014]   alloc irq_desc for 22 on node -1
[    1.615016]   alloc kstat_irqs on node -1
[    1.615026] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.615790] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.615796] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.616972] scsi2 : ahci
[    1.617118] scsi3 : ahci
[    1.617253] scsi4 : ahci
[    1.617379] scsi5 : ahci
[    1.617497] scsi6 : ahci
[    1.617597] scsi7 : ahci
[    1.617670] ata3: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408100 irq 22
[    1.617675] ata4: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408180 irq 22
[    1.617680] ata5: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408200 irq 22
[    1.617684] ata6: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408280 irq 22
[    1.617689] ata7: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408300 irq 22
[    1.617693] ata8: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408380 irq 22
[    1.708076] firewire_ohci: Added fw-ohci device 0000:08:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.780070] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.936105] ata5: SATA link down (SStatus 0 SControl 300)
[    1.936109] ata8: SATA link down (SStatus 0 SControl 300)
[    1.936154] ata4: SATA link down (SStatus 0 SControl 300)
[    1.936186] ata7: SATA link down (SStatus 0 SControl 300)
[    2.108077] ata3: softreset failed (device not ready)
[    2.108083] ata3: applying SB600 PMP SRST workaround and retrying
[    2.108106] ata6: softreset failed (device not ready)
[    2.108109] ata6: applying SB600 PMP SRST workaround and retrying
[    2.200176] firewire_core: created device fw0: GUID 8c3f0200110340d7, S400
[    2.280084] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.280117] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.280977] ata3.00: ATA-8: TOSHIBA MK3252GSX, LV011C, max UDMA/100
[    2.280982] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.281986] ata3.00: configured for UDMA/100
[    2.284214] ata6.00: ATAPI: hp       DVDRAM GT20L, DC05, max UDMA/100
[    2.289144] ata6.00: configured for UDMA/100
[    2.296338] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    2.296566] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.296676] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.296810] sd 2:0:0:0: [sda] Write Protect is off
[    2.296814] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.296864] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.297064]  sda:
[    2.307583] scsi 5:0:0:0: CD-ROM            hp       DVDRAM GT20L     DC05 PQ: 0 ANSI: 5
[    2.318852] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.318856] Uniform CD-ROM driver Revision: 3.20
[    2.319001] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.319076] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    2.352242]  sda1 sda2 < sda5 sda6 >
[    2.379575] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.388235] usbcore: registered new interface driver hiddev
[    2.394141] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input5
[    2.394274] generic-usb 0003:046D:C050.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-2/input0
[    2.394302] usbcore: registered new interface driver usbhid
[    2.394304] usbhid: USB HID core driver
[    2.848173] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.192924] Adding 9068656k swap on /dev/sda5.  Priority:-1 extents:1 across:9068656k 
[    6.878636] udev[431]: starting version 163
[    9.905478] cfg80211: Calling CRDA to update world regulatory domain
[    9.914120] Linux video capture interface: v2.00
[    9.923950] lirc_dev: IR Remote Control driver registered, major 249 
[   10.128143] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   10.316306] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.327334] input: HP WMI hotkeys as /devices/virtual/input/input6
[   10.492696] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.492707] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[   10.557196] uvcvideo: Found UVC 1.00 device HP Webcam (064e:c107)
[   10.566338] input: HP Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input7
[   10.566427] usbcore: registered new interface driver uvcvideo
[   10.566430] USB Video Class driver (v0.1.0)
[   10.665732] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
[   10.666558] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
[   10.666663] enecir: KB3926C detected, driver support is not complete!
[   10.666666] enecir: chip is 0x3926 - 0x00, 0xc0
[   10.666674] enecir: hardware features:
[   10.666676] enecir: learning and tx off, gpio40_learn off, fan_in off
[   10.666679] enecir: driver has been succesfully loaded
[   10.706764] lis3lv02d: hardware type DV7 found.
[   10.707611] lis3lv02d: 8 bits sensor found
[   10.753084] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   10.754195] Registered led device: hp::hddprotect
[   10.754301] lis3lv02d driver loaded.
[   10.806077] type=1400 audit(1303214588.214:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=611 comm="apparmor_parser"
[   10.806101] type=1400 audit(1303214588.214:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=610 comm="apparmor_parser"
[   10.806379] type=1400 audit(1303214588.214:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=611 comm="apparmor_parser"
[   10.806408] type=1400 audit(1303214588.214:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=610 comm="apparmor_parser"
[   10.806553] type=1400 audit(1303214588.214:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=611 comm="apparmor_parser"
[   10.806586] type=1400 audit(1303214588.214:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=610 comm="apparmor_parser"
[   11.083549] lp: driver loaded but no devices found
[   11.192269] cfg80211: World regulatory domain updated:
[   11.192274]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.192278]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.192281]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.192284]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.192288]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.192291]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.498088] ath5k 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.498102] ath5k 0000:09:00.0: setting latency timer to 64
[   11.498167] ath5k 0000:09:00.0: registered as 'phy0'
[   11.998995] ath: EEPROM regdomain: 0x67
[   11.998997] ath: EEPROM indicates we should expect a direct regpair map
[   11.999003] ath: Country alpha2 being used: 00
[   11.999006] ath: Regpair used: 0x67
[   12.016248] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.016340] HDA Intel 0000:00:14.2: setting latency timer to 64
[   12.253597] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   12.253700] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   12.254208] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.254287]   alloc irq_desc for 46 on node -1
[   12.254290]   alloc kstat_irqs on node -1
[   12.254306] HDA Intel 0000:01:00.1: irq 46 for MSI/MSI-X
[   12.254336] HDA Intel 0000:01:00.1: setting latency timer to 64
[   12.387372] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000/0x20000
[   12.508054] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   12.561394] phy0: Selected rate control algorithm 'minstrel'
[   12.562108] Registered led device: ath5k-phy0::rx
[   12.562134] Registered led device: ath5k-phy0::tx
[   12.562138] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.823808] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7611
[   12.823898] usbcore: registered new interface driver usblp
[   14.943676] type=1400 audit(1303214592.346:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1040 comm="apparmor_parser"
[   14.943983] type=1400 audit(1303214592.346:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1040 comm="apparmor_parser"
[   14.944224] type=1400 audit(1303214592.350:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1040 comm="apparmor_parser"
[   15.106663] type=1400 audit(1303214592.510:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1039 comm="apparmor_parser"
[   15.955147] audit_printk_skb: 12 callbacks suppressed
[   15.955152] type=1400 audit(1303214593.362:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1041 comm="apparmor_parser"
[   15.959293] type=1400 audit(1303214593.366:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1041 comm="apparmor_parser"
[   15.961946] type=1400 audit(1303214593.370:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1041 comm="apparmor_parser"
[   16.481947] type=1400 audit(1303214593.890:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1120 comm="apparmor_parser"
[   16.529245] type=1400 audit(1303214593.938:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1122 comm="apparmor_parser"
[   16.801085] type=1400 audit(1303214594.206:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1146 comm="apparmor_parser"
[   16.801495] type=1400 audit(1303214594.206:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1146 comm="apparmor_parser"
[   17.255323] ppdev: user-space parallel port driver
[   19.111773] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.128047] r8169 0000:0a:00.0: eth0: link up
[   19.128056] r8169 0000:0a:00.0: eth0: link up
[   22.247812] Linux agpgart interface v0.103
[   22.312207] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   22.375484] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   22.375491] Disabling lock debugging due to kernel taint
[   22.545362] [fglrx] Maximum main memory to use for locked dma buffers: 3856 MBytes.
[   22.545779] [fglrx]   vendor: 1002 device: 9591 count: 1
[   22.546402] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   22.546445] pci 0000:01:00.0: power state changed by ACPI to D0
[   22.546455] pci 0000:01:00.0: power state changed by ACPI to D0
[   22.546467] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.546474] pci 0000:01:00.0: setting latency timer to 64
[   22.546742] [fglrx] Kernel PAT support is enabled
[   22.546774] [fglrx] module loaded - fglrx 8.83.6 [Mar  8 2011] with 1 minors
[   22.605314] [fglrx] ATIF platform detected with notification ID: 0x81
[   23.040810]   alloc irq_desc for 47 on node -1
[   23.040815]   alloc kstat_irqs on node -1
[   23.040830] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[   23.041643] [fglrx] Firegl kernel thread PID: 1636
[   23.041803] [fglrx] Firegl kernel thread PID: 1637
[   23.041880] [fglrx] Firegl kernel thread PID: 1638
[   23.042184] [fglrx] IRQ 47 Enabled
[   24.619121] [fglrx] Gart USWC size:1256 M.
[   24.619126] [fglrx] Gart cacheable size:498 M.
[   24.619134] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   24.619139] [fglrx] Reserved FB block: Unshared offset:fc11000, size:3ef000 
[   24.619143] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   27.721923] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[   30.072021] eth0: no IPv6 routers present
[   40.330109] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   40.619094] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   40.849644] vboxdrv: Found 2 processor cores.
[   40.850625] vboxdrv: fAsync=1 offMin=0xd9302c9 offMax=0xd9302c9
[   40.851324] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   40.851328] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[   66.347284] wlan0: authenticate with 00:1a:2b:16:66:7b (try 1)
[   66.355644] wlan0: authenticated
[   66.355674] wlan0: associate with 00:1a:2b:16:66:7b (try 1)
[   66.357939] wlan0: RX AssocResp from 00:1a:2b:16:66:7b (capab=0x411 status=0 aid=1)
[   66.357945] wlan0: associated
[   66.358626] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.164356] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   77.328566] wlan0: no IPv6 routers present
[ 4862.973305] r8169 0000:0a:00.0: eth0: link down
[ 4864.620348] r8169 0000:0a:00.0: eth0: link up
[ 5416.369945] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 5503.073886] hrtimer: interrupt took 1410047 ns


Que es lo que està malament?

Es que tampoc llegeix els discos, poso un cd y es com si no poses res. Se sent el cd intentant llegir, però mai apareix el disc, es con si no estigues, no el reconeix.

---

### Post by kimet on 2011-04-19
Podries posar la sortida de: ```
cat /etc/fstab
``` ?

---

### Post by Original Flo on 2011-04-19
He provat amb el livecd i no em reconeix un cd original d'àudio que he posat.

aquesta es la sortida que hem demaneu

> david@david-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bcec6836-9d34-4eb0-a864-c654a36ca055 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b2be910a-da7f-46f3-92b6-deb7fdb01ac5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
david@david-laptop:~$ 


---

### Post by wgarcia on 2011-04-19
Una observació Original Flo, un altre cop quan hagis d'enganxar tanta informació millor adjuntar-lo en un fitxer de text.

Quant al teu "/etc/fstab" a veure què diu el Kimet, però em sembla que la línia que refereix al cdrom que surt en aquest fitxer no és necessària.

---

### Post by Original Flo on 2011-04-19
> **wgarcia said:**
> Una observació Original Flo, un altre cop quan hagis d'enganxar tanta informació millor adjuntar-lo en un fitxer de text.

Quant al teu "/etc/fstab" a veure què diu el Kimet, però em sembla que la línia que refereix al cdrom que surt en aquest fitxer no és necessària.

Gracies, la pròxima vegada arxiu de text;)

Si fos necessària mes informació per saber quin es el problema, me la demaneu i la penjo de seguida que pugui.

---

### Post by kimet on 2011-04-19
Jo crec que si es necessària la línia a fstab, a no ser que hagi canviat la forma de muntar els dispositius, que també és possible perquè hi han hagut canvis entre hal i udev.

Per si de cas no fos necessària pots provar editant aquesta línia posant un # al davant perquè no sigui tinguda en compte, i provar amb diferents programes!.

Si no, pots mirar si aquest /dev/scd0 correspon al dispositiu de cd o no. ho podries fer amb:
```
eject /dev/scd0
``` Si s'obre la safata es correcte, si no buscar on es i modificar la línia.

Pot ser també que el programa que fas servir no el busqui a lloc adequat,/media/cdrom0 en el teu cas, prova també amb diferents programes.

No se'm acut res més. Salut

---

### Post by Original Flo on 2011-04-19
> **kimet said:**
> Jo crec que si es necessària la línia a fstab, a no ser que hagi canviat la forma de muntar els dispositius, que també és possible perquè hi han hagut canvis entre hal i udev.

Per si de cas no fos necessària pots provar editant aquesta línia posant un # al davant perquè no sigui tinguda en compte, i provar amb diferents programes!.

Si no, pots mirar si aquest /dev/scd0 correspon al dispositiu de cd o no. ho podries fer amb:
```
eject /dev/scd0
``` Si s'obre la safata es correcte, si no buscar on es i modificar la línia.

Pot ser també que el programa que fas servir no el busqui a lloc adequat,/media/cdrom0 en el teu cas, prova també amb diferents programes.

No se'm acut res més. Salut

Si, s'obre la safata.

He editat "/etc/fstab" a quedat aixi.

> david@david-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bcec6836-9d34-4eb0-a864-c654a36ca055 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b2be910a-da7f-46f3-92b6-deb7fdb01ac5 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
david@david-laptop:~$ Després he ficat un cd i com sempre sembla que intenta llegir, però no em reconeix cap cd, aixi que no he pogut provar cap programa de gravació.

Si li clico a l'unitat de cd quan he ficat el cd em diu que no s'ha pogut muntar l'unitat.

Que faríeu vosaltres ara?

P.D.: Ahhh, un altre cosa, he aconseguit convertir la meva antiga PSP (Play Station Portable) amb un disc d'inici d'ubuntu:D, l'he provat i funciona, aixi que quan surti natty el podré instal·lar de 0 i m'instal-lare la versió de 64 Bits. Ara tinc instal-lada la versió 10.10 de 32 Bits, però tinc un amd de 64Bits amb 4 Gigas de Ram i em vull canviar a 64 bits.

---

### Post by kimet on 2011-04-19
Verificar que el directori /media/cdrom0 existeix i intentar muntar el cd manualment. > sudo mount /dev/scd0 /media/cdrom0 . ( amb un cd a dins) i estar al tanto de si a /media apareix el cd muntat.

---

### Post by Original Flo on 2011-04-19
Aixo es lo que em diu just després de ficar un cd i quan encara està fent soroll la gravadora de que intenta llegir.

[HTML]david@david-laptop:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for david: 
mount: /dev/sr0 ya está montado o /media/cdrom0 está ocupado
david@david-laptop:~$ [/HTML]

Quan ja no fa soroll de intentar llegir, torno a posar lo mateix i em torna aixo.

[HTML]david@david-laptop:~$ sudo mount /dev/scd0 /media/cdrom0
umount: /dev/sr0: dispositivo desconocido
david@david-laptop:~$ 
[/HTML]

Gracies per intentar ajudar-me.

Que faríeu ara?

---

### Post by Original Flo on 2011-04-19
Per cert, com he comentat, el problema va començar amb que la gravadora simplement no gravava, pero si llegia.

En un altre fòrum em van recomanar que instal·les uns codecs.

Després d'instal·lar aquells codecs va ser quan va deixar de llegir.

Us comento aixo per si creieu que pot aver-hi relació.

---

### Post by wgarcia on 2011-04-20
Suposo que en tots aquests passos que has fet (la línia amb # al fstab, mount, etc.) has anat reiniciant l'ordinador, oi? Sinó els canvis no entren en efecte.

Per cert, jo no tinc cap línia relacionada amb el CD al fstab.

Quant als còdecs no crec que tinguin gaire a veure amb el teu problema, són necessaris per reconèixer DVD i poder-los gravar però en aquest cas et diria alguna cosa com format desconegut o així.

Per acabar de fer sistemàtic aquestes proves mira el següent:

1) deixa el /etc/fstab amb el "#" davant la línia esmentada

2) reinicia l'ordinador

3) posa un CD de música o algun altre CD que sàpigues que està ben gravat a la unitat

4) en una terminal entra "mount" i mira si es veu alguna línia relacionada amb el CD

---

### Post by Original Flo on 2011-04-20
Pues us comento.

L'# no l'he tret mai de la linea del cd des que hem vau dir que li poses, i si he reiniciat el cd.

Aixo es lo que em torna després de ficar un cd i posar mount al terminal.

[HTML]david@david-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
david@david-laptop:~$ [/HTML]

---

### Post by wgarcia on 2011-04-20
Hem refereixo a reiniciar l'ordinador, no el CD. Has reiniciat l'ordinador amb el "#" a la línia del /etc/fstab ?

---

### Post by Original Flo on 2011-04-20
> **wgarcia said:**
> Hem refereixo a reiniciar l'ordinador, no el CD. Has reiniciat l'ordinador amb el "#" a la línia del /etc/fstab ?

Si:D, varies vegades.

---

### Post by wgarcia on 2011-04-20
D'acord. El CD que poses a la unitat és un CD d'àudio? Pots provar amb un CD da dades, és a dir un CD on hagis gravat dades o fitxers MP3 o qualsevol altra cosa?

Si ho proves mira amb la comanda "mount" a veure si es munta el CD.

---

### Post by Original Flo on 2011-04-20
He ficat un cd de dades i aixo es lo que em torna.

[HTML]david@david-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
david@david-laptop:~$ 
[/HTML]

---

### Post by wgarcia on 2011-04-20
Està clar que el sistema no està muntant el CD, i pel que es pot veure al "dmesg" d'alguna manera no veu aquest dispositiu. 

Deies al principi que amb la versió Ubuntu 10.04 sí que funcionava. Quan comença l'ordinador et surt la pantalla Grub per escollir el nucli pel qual començar o va directament a la pantalla d'entrada a l'Ubuntu sense mostrar-te diversos nuclis? 

En el cas que et mostri diversos nuclis prova d'iniciar amb algun altre nucli que no sigui el primer a veure si amb algun d'aquests altres nuclis el CD funciona.

---

### Post by kimet on 2011-04-20
La manera antiga de muntar les unitats de cd era amb mount i posant les entrades a fstab per que les muntés automaticament com qualsevol altre disc, ara em sembla que s'en encarrega udev.

Veig aquí: [http://ubuntuforums.org/showthread.php?t=1618085&page=3](http://ubuntuforums.org/showthread.php?t=1618085&page=3)
 Que la comanda udisks que et podría servir:
```
udisks --mount /dev/sr0
```
I, investigant sobre udisks veig que te forces opcions entre d'altres:
posar al terminal:
```
udisks --monitor-details
```
prémer enter i posar un cd a la unitat, t'hauria de donar informació sobre aquesta.
Mira el manual per a d'altres opcions.
De totes maneres hauries de descartar un problema de hardware provant amb un altre SO des de un llapis usb com t'ha dit en wgarcia.

Salut.

---

### Post by Original Flo on 2011-04-20
El meu sistema entra directament a ubuntu (es l'unic SO que tinc a l'ordinador) sense passar pel menú del grub.



> **kimet said:**
> La manera antiga de muntar les unitats de cd era amb mount i posant les entrades a fstab per que les muntés automaticament com qualsevol altre disc, ara em sembla que s'en encarrega udev.

Veig aquí: [http://ubuntuforums.org/showthread.php?t=1618085&page=3](http://ubuntuforums.org/showthread.php?t=1618085&page=3)
 Que la comanda udisks que et podría servir:
```
udisks --mount /dev/sr0
```I, investigant sobre udisks veig que te forces opcions entre d'altres:
posar al terminal:
```
udisks --monitor-details
```prémer enter i posar un cd a la unitat, t'hauria de donar informació sobre aquesta.
Mira el manual per a d'altres opcions.
De totes maneres hauries de descartar un problema de hardware provant amb un altre SO des de un llapis usb com t'ha dit en wgarcia.

Salut.

Quan poso
```
udisks --mount /dev/sr0
```El terminal em torna aixo.
```
david@david-laptop:~$ udisks --mount /dev/sr0
Mount failed: Error mounting: mount: /dev/sr0: unknown device

david@david-laptop:~$
```
Quan poso
```
udisks --monitor-details
```Em tona aixo.

```
david@david-laptop:~$ udisks --monitor-details
Uso:
  udisks [OPCIÓN...] udisks commandline tool

Opciones de ayuda:
  -h, --help                   Mostrar opciones de ayuda

Opciones de la aplicación:
  --enumerate                  Enumerate objects paths for devices
  --enumerate-device-files     Enumerate device files for devices
  --dump                       Dump all information about all devices
  --monitor                    Monitor activity from the disk daemon
  --monitor-detail             Monitor with detail
  --show-info                  Show information about a device file
  --inhibit-polling            Inhibit polling
  --inhibit-all-polling        Inhibit all polling
  --poll-for-media             Poll for media
  --set-spindown               Set spindown timeout for drive
  --set-spindown-all           Set spindown timeout for all drives
  --spindown-timeout           Spindown timeout in seconds
  --inhibit                    Inhibit the daemon
  --mount                      Mount the given device
  --mount-fstype               Specify file system type
  --mount-options              Mount options separated by comma
  --unmount                    Unmount the given device
  --unmount-options            Unmount options separated by comma
  --detach                     Detach the given device
  --detach-options             Detach options separated by comma
  --ata-smart-refresh          Refresh ATA SMART data
  --ata-smart-wakeup           Wake up the disk if it is not awake
  --ata-smart-simulate         Inject libatasmart BLOB for testing

See the udisks man page for details.
david@david-laptop:~$ 

```

---

### Post by wgarcia on 2011-04-21
Per obrir el menú de "grub" i poder provar algun nucli més antic s'ha de prémer la tecla "ESC" dins de 3 segons després que el grub comença, és a dir immediatament després que el sistema hagi passat pels missatges inicials relacionats amb la bios.

---

### Post by Original Flo on 2011-05-01
Buenassss.

Feia dies que entre la setmana santa y una cosa o altre no he pogut comentar res d'aquest tema.

El lector/gravador continua igual.

D'es de l'última vegada que vaig passar per aquí, us comento els canvis que he fet.

Vaig passar el arxius de documents, fotos, música i demés de home a un disc dur portàtil i vaig esborrar tot el disc dur.

Vaig eliminar totes les particions, les vaig formatar i vaig deixar el disc dur sense res, ni particions ni res de res.

Vaig posar un usb d'ubuntu 11.04 64 bits (la versió final que va sortir fa un parell de dies).

Vaig fer la instal·lació amb la opció de "fer mes coses" (la que et deixa escollir les particions).

Vaig crear tres particions:

-una partició per "/" de 15000 MB
-una d'intercanvi "swap" del doble de capacitat que la meva ram (4GB) que es lo que recomanen (8192MB).
-una partició amb la resta del disc dur per "/home".

-Després de tenir-ho tot instal·lat i funcionant vaig tornar a passar a home tot lo que havia guardat al disc dur extern.

Com us he comentat, en lo referent al cd/dvd, continua tot exactament com abans. Encara havent fet instal·lació nova formatant tot, continua igual que abans.

Que creieu que pot ser?

Salut.

---

### Post by wgarcia on 2011-05-02
Amb un USB amb Ubuntu 10.04 (Lucid) et funciona la unitat de CD? Si no funciona amb algun sistema operatiu s'ha de començar a sospitar que es tracta d'un problema de funcionament del maquinari.

---

### Post by Original Flo on 2011-05-02
No funciona amb res, ni iniciant un live usb ni de cap manera.

Com puc saber si lo que falla es la lectora/gravadora o si lo que falla es el port sata de la placa base.

Pregunto per que no sigui el cas que compri un lector/gravador nou i despres lo que estigui malament sigui alguna cosa del port sata.

Salut.

---

### Post by wgarcia on 2011-05-03
Potser ho podries comprovar si puguessis provar alguna unitat d'algun altre ordinador que tinguis constància que funciona.

---

### Post by Original Flo on 2011-05-03
Pues no en tinc cap.

Bueno deixarem que passi el temps a veure si algun dia tinc per casualitat oportunitat de provar amb un altre unitat.

---

