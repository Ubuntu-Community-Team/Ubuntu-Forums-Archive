---
title: "[SOLVED] Problemas con PPP"
date: 2008-02-04
forum: Argentina Team
---

### Post by atari130xe on 2008-02-04
Cuando creía tener el sistema "a punto" hace ayer empecé a tener problemas con mi conexion dial up (ppp). Me conecto, disca y de manera caprichosa, se corta la comunicación sin motivo alguno, eso puede pasar inmediatamente luego de conectarme, o a los 3 min o a la 1 hora, pero fastidiosamente se me cortan todas las comunicaciones como nunca antes me había pasado, en la infinidad de re instalaciones que hice en mi PC. Fui al /var/log y vi que dice [COLOR="Blue"]**error 16 modem hung up**[/COLOR], no creo que sea un problema de hardware porque tengo en la misma pc una particion con Elive Gem, y no me pasa lo mismo que con Ubuntu, sinceramente estoy desconcertado. Busqué en google el error 16 y hay varios motivos pero ninguno tiene que ver con mi pc, o sea problemas de nros a discar, de passwords, de usuarios, configuracion de wvdial, pppconfig, etc. todo esta como cuando me funcionó, es más ese tipo de configuraciones las hago con los "ojos cerrados", si alguien tiene una idea?:confused:
PD: hoy re instalé el sistema operativo desde cero y continua el mismo problema., podría ser la linea de tel? si es así no comprendo como no se me corta con Elive.
Editado: estoy pensando si no es un problema el que le haya instalado una placa de red ethernet, puede ser un problema con la placa? podria ser un problema con el demonio pppd? la instalé porque cuando vuelva a bsas pienso poner banda ancha.
/Var/log muestra algo así:
> Status is: disconnected
tStatus is: connecting
pppd[0]: --> WvDial: Internet dialer version 1.54.0
pppd[0]: --> Initializing modem.
pppd[0]: --> Sending: ATX3
pppd[0]: OK
pppd[0]: --> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: OK
pppd[0]: --> Sending: ATM1
pppd[0]: ATM1
pppd[0]: OK
pppd[0]: --> Modem initialized.
pppd[0]: --> Sending: ATDT (el nro)
pppd[0]: --> Waiting for carrier.
pppd[0]: ATDT....
pppd[0]: CONNECT 49333/V42BIS
pppd[0]: --> Carrier detected. Waiting for prompt.
pppd[0]: --> Don't know what to do! Starting pppd and hoping for the best.
pppd[0]: Serial connection established.
pppd[0]: Renamed interface ppp0 to modem0
pppd[0]: Using interface modem0
Status is: connecting
pppd[0]: Connect: modem0 <--> /dev/ttyS2
pppd[0]: Hangup (SIGHUP)
pppd[0]: Modem hangup
pppd[0]: Connection terminated.
Status is: disconnected
pppd[0] died: A modem hung up the phone (exit code 16)


---

### Post by euzkoarima on 2008-02-04
La verdad, raro. Lo único parecido que vi fue un caso en que teíian llamada en espera, entonces si estabas con el modem y alguien te llamaba, te colgaba la conexión del modem. Ahora que te pase con ubuntu y no con elive es raro.
Proba de fijarte en elive que configuración de inicilización del modem esta usando, y comparala con el AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 que estas usando en ubuntu, a ver si hay algun comando AT distinto que pueda dar una pista.

Saludos

---

### Post by atari130xe on 2008-02-04
Cuando llegue a casa lo chequeo, es raro de verdad, instalé ubuntu 7.10 en mi pc unas 11 veces con esta y nunca me habia pasado, me hace acordar a cuando recien habia empezado donde no tenia la menor idea de como configurar el modem :(, lo que sí tengo en mi linea de tel es el contestador de Telecom, (mi linea tiene el tono con "intermitencias") pero para eso al inicio del discado pongo ATX3.

No quiero imaginarme configurando ADSL jajaja si yá con dial up me dio ciertos dolores de cabeza :)

---

### Post by atari130xe on 2008-02-06
Bueno me temo que el problema es la actualizacion, porque durante la instalacion previamente en modo live configuro PPPconfig y va todo de 10 actualiza apt y baja los paquetes de idiomas mientras se instala (me lleva aprox 1:40 mins con dial up), cuando instalaba Ubuntu sin estar conectado a la net todo funcionaba bien, supongo que el problema puede ser ese. o no? alguien que pueda deducir otra cosa...

---

### Post by euzkoarima on 2008-02-06
Yo insisto en que trates de copiarte la configuración del modem de una variante que funcione, si con el liveCD te funciona, fijate como está ahí. Ojala funcione.

Saludos

---

### Post by atari130xe on 2008-02-07
Bueno hoy hice una prueba, me conecte a Internet y estuve 1 hora y media sin que se corte hasta que abri Xmms para escuchar musica y... se cortó! :mad:, o sea que algo pasa ahí, que será? no lo sé, en el /var/log/ no encuentro nada especial, si es necesario posteo el resultado.

---

### Post by atari130xe on 2008-02-08
Bueno hoy seguí experimentando el corte de las comunicaciones con mi modem, y estoy tratando de orientarme para que lado ir, por ej, hoy estaba todo bien 2hs conectado y al conectar mi pendrive USB, puff, se corto la comunicacion y no solo eso, sino que como me conecté via consola "pon arnet", al desconectarse se volvio a reconectar pero esta vez como un "loop" interminable, o sea connect disconnect connect disconnect hasta que cerré la consola, puede que sea un problema de IRQ´s con los puertos USB no lo sé pero estoy investigando. Estoy pensando en cambiar el IRQ al modem (ISA PnP), nunca me habia pasado antes, pero como le agregué nuevo Hard (una placa PCI de sonido y una placa de puertos USB, puede que el problema sea ese no lo sé.
Posteo un simple DMESG:
```
jose@jose-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bff3000 - 000000001c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114672
[    0.000000]   HighMem    114672 ->   114672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114672
[    0.000000] On node 0 totalpages: 114672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109713 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F79A0 checksum 0
[    0.000000] ACPI: RSDP 000F79A0, 0014 (r0 SOYO  )
[    0.000000] ACPI: RSDT 1BFF3000, 0028 (r1 SOYO   AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1BFF3040, 0074 (r1 SOYO   AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1BFF30C0, 22C3 (r1 SOYO   AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1BFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 113777
[    0.000000] Kernel command line: root=UUID=d5759f95-b3cc-454f-9249-b0893f5da167 ro quiet splash locale=es_ES
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0138c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 600.047 MHz processor.
[   26.791464] Console: colour VGA+ 80x25
[   26.792512] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.793516] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.834228] Memory: 443148k/458688k available (2015k kernel code, 14904k reserved, 916k data, 364k init, 0k highmem)
[   26.834265] virtual kernel memory layout:
[   26.834269]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.834273]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.834278]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   26.834282]     lowmem  : 0xc0000000 - 0xdbff0000   ( 447 MB)
[   26.834287]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.834291]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   26.834296]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   26.834308] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.834443] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.914465] Calibrating delay using timer specific routine.. 1201.84 BogoMIPS (lpj=2403685)
[   26.914559] Security Framework v1.0.0 initialized
[   26.914579] SELinux:  Disabled at boot.
[   26.914636] Mount-cache hash table entries: 512
[   26.915040] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   26.915072] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.915081] CPU: L2 Cache: 512K (64 bytes/line)
[   26.915090] CPU: After all inits, caps: 0183f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   26.915123] Compat vDSO mapped to ffffe000.
[   26.915160] Checking 'hlt' instruction... OK.
[   26.930546] SMP alternatives: switching to UP code
[   26.931259] Freeing SMP alternatives: 11k freed
[   26.932228] Early unpacking initramfs... done
[   27.990294] ACPI: Core revision 20070126
[   27.990547] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.993221] ACPI: setting ELCR to 0800 (from 0e00)
[   27.994769] CPU0: AMD Athlon(tm) Processor stepping 01
[   27.994787] SMP motherboard not detected.
[   27.994796] Local APIC not detected. Using dummy APIC emulation.
[   27.994941] Brought up 1 CPUs
[   27.995365] Booting paravirtualized kernel on bare hardware
[   27.995538] Time: 12:37:50  Date: 01/09/108
[   27.995630] NET: Registered protocol family 16
[   27.995980] EISA bus registered
[   27.996015] ACPI: bus type pci registered
[   28.029330] PCI: PCI BIOS revision 2.10 entry at 0xfb110, last bus=1
[   28.029340] PCI: Using configuration type 1
[   28.029346] Setting up standard PCI resources
[   28.045810] ACPI: EC: Look up EC in DSDT
[   28.050954] ACPI: Interpreter enabled
[   28.050966] ACPI: (supports S0 S1 S4 S5)
[   28.051017] ACPI: Using PIC for interrupt routing
[   28.062185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.062221] PCI: Probing PCI hardware (bus 00)
[   28.062779] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
[   28.062790] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   28.062800] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   28.063362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.099998] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   28.100384] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   28.100761] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   28.101134] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[   28.101412] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.101466] pnp: PnP ACPI init
[   28.101495] ACPI: bus type pnp registered
[   28.109016] pnp: PnP ACPI: found 13 devices
[   28.109026] ACPI: ACPI bus type pnp unregistered
[   28.109039] PnPBIOS: Disabled by ACPI PNP
[   28.109212] PCI: Using ACPI for IRQ routing
[   28.109223] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.139317] NET: Registered protocol family 8
[   28.139326] NET: Registered protocol family 20
[   28.139563] pnp: 00:00: iomem range 0xcec00-0xcffff has been reserved
[   28.139576] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   28.139586] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   28.139596] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   28.142101] Time: tsc clocksource has been installed.
[   28.170741] PCI: Bridge: 0000:00:01.0
[   28.170747]   IO window: disabled.
[   28.170759]   MEM window: e4000000-e6ffffff
[   28.170769]   PREFETCH window: d0000000-dfffffff
[   28.170799] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.170840] NET: Registered protocol family 2
[   28.210239] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   28.210409] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   28.211283] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   28.212002] TCP: Hash tables configured (established 16384 bind 16384)
[   28.212014] TCP reno registered
[   28.222533] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   29.142712]  it is
[   30.246440] Freeing initrd memory: 7040k freed
[   30.247833] audit: initializing netlink socket (disabled)
[   30.247878] audit(1202560672.312:1): initialized
[   30.254925] VFS: Disk quotas dquot_6.5.1
[   30.255135] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.255470] io scheduler noop registered
[   30.255479] io scheduler anticipatory registered
[   30.255486] io scheduler deadline registered
[   30.255542] io scheduler cfq registered (default)
[   30.255579] PCI: VIA PCI bridge detected. Disabling DAC.
[   30.255597] PCI: Disabling Via external APIC routing
[   30.255702] Boot video device is 0000:01:00.0
[   30.256267] isapnp: Scanning for PnP cards...
[   30.358331] isapnp: Card 'U.S. Robotics 56K Voice INT'
[   30.358342] isapnp: 1 Plug & Play card detected total
[   30.466225] Real Time Clock Driver v1.12ac
[   30.466532] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.466764] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.467284] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.469064] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.469991] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.472728] pnp: Device 01:01.00 activated.
[   30.473111] 01:01.00: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
[   30.475745] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.476531] input: Macintosh mouse button emulation as /class/input/input0
[   30.476824] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   30.477506] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.477525] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.478131] mice: PS/2 mouse device common for all mice
[   30.478524] EISA: Probing bus 0 at eisa.0
[   30.478572] Cannot allocate resource for EISA slot 4
[   30.478579] Cannot allocate resource for EISA slot 5
[   30.478587] Cannot allocate resource for EISA slot 6
[   30.478607] EISA: Detected 0 cards.
[   30.478909] TCP cubic registered
[   30.478945] NET: Registered protocol family 1
[   30.479008] Using IPI No-Shortcut mode
[   30.479524]   Magic number: 12:502:632
[   30.479714]   hash matches device ptycb
[   30.481145] Freeing unused kernel memory: 364k freed
[   30.549376] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.215988] AppArmor: AppArmor initialized<5>audit(1202560674.312:2):  type=1505 info="AppArmor initialized" pid=1167
[   32.238730] fuse init (API version 7.8)
[   32.256001] Failure registering capabilities with primary security module.
[   32.301169] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   32.301188] ACPI: Processor [CPU0] (supports 2 throttling states)
[   34.186798] SCSI subsystem initialized
[   34.204750] libata version 2.21 loaded.
[   34.225511] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.225528] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.227466] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   34.227514] VP_IDE: chipset revision 16
[   34.227521] VP_IDE: not 100% native mode: will probe irqs later
[   34.227547] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[   34.227565]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   34.227592]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[   34.227612] Probing IDE interface ide0...
[   34.341842] usbcore: registered new interface driver usbfs
[   34.341918] usbcore: registered new interface driver hub
[   34.342002] usbcore: registered new device driver usb
[   34.345001] USB Universal Host Controller Interface driver v3.0
[   34.456920] 8139too Fast Ethernet driver 0.9.28
[   34.739779] hda: SAMSUNG SP0822N, ATA DISK drive
[   35.105422] Floppy drive(s): fd0 is 1.44M
[   35.129363] FDC 0 is a post-1991 82077
[    8.360000] Marking TSC unstable due to: possible TSC halt in C2.
[    8.384000] Time: acpi_pm clocksource has been installed.
[    8.584000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.584000] Probing IDE interface ide1...
[    9.448000] hdc: Optiarc DVD RW AD-7190A, ATAPI CD/DVD-ROM drive
[   10.120000] ide1 at 0x170-0x177,0x376 on irq 15
[   10.120000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   10.120000] PCI: setting IRQ 10 as level-triggered
[   10.120000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.120000] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 9 to 10
[   10.120000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   10.124000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   10.124000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[   10.124000] usb usb1: configuration #1 chosen from 1 choice
[   10.124000] hub 1-0:1.0: USB hub found
[   10.124000] hub 1-0:1.0: 2 ports detected
[   10.148000] hda: max request size: 512KiB
[   10.184000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[   10.188000] hda: cache flushes supported
[   10.188000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[   10.264000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.264000] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 9 to 10
[   10.264000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   10.264000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   10.264000] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   10.264000] usb usb2: configuration #1 chosen from 1 choice
[   10.264000] hub 2-0:1.0: USB hub found
[   10.264000] hub 2-0:1.0: 2 ports detected
[   10.304000] hdc: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   10.304000] Uniform CD-ROM driver Revision: 3.20
[   10.388000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.388000] PCI: setting IRQ 11 as level-triggered
[   10.388000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.388000] uhci_hcd 0000:00:0a.0: UHCI Host Controller
[   10.388000] uhci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 3
[   10.388000] uhci_hcd 0000:00:0a.0: irq 11, io base 0x0000e000
[   10.392000] usb usb3: configuration #1 chosen from 1 choice
[   10.392000] hub 3-0:1.0: USB hub found
[   10.392000] hub 3-0:1.0: 2 ports detected
[   10.496000] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.496000] uhci_hcd 0000:00:0a.1: UHCI Host Controller
[   10.496000] uhci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 4
[   10.496000] uhci_hcd 0000:00:0a.1: irq 10, io base 0x0000e400
[   10.500000] usb usb4: configuration #1 chosen from 1 choice
[   10.500000] hub 4-0:1.0: USB hub found
[   10.500000] hub 4-0:1.0: 2 ports detected
[   10.604000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   10.604000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   10.608000] eth0: RealTek RTL8139 at 0xdc83a000, 00:50:fc:2b:80:ac, IRQ 11
[   10.608000] eth0:  Identified 8139 chip type 'RTL-8139C'
[   10.612000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   10.616000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   10.616000] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   10.616000] ehci_hcd 0000:00:0a.2: EHCI Host Controller
[   10.616000] ehci_hcd 0000:00:0a.2: new USB bus registered, assigned bus number 5
[   10.616000] ehci_hcd 0000:00:0a.2: irq 10, io mem 0xe8001000
[   10.616000] ehci_hcd 0000:00:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.616000] usb usb5: configuration #1 chosen from 1 choice
[   10.616000] hub 5-0:1.0: USB hub found
[   10.616000] hub 5-0:1.0: 4 ports detected
[   10.988000] Attempting manual resume
[   10.988000] swsusp: Resume From Partition 3:3
[   10.988000] PM: Checking swsusp image.
[   10.988000] PM: Resume from disk failed.
[   11.056000] kjournald starting.  Commit interval 5 seconds
[   11.056000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.852000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   12.040000] usb 4-1: configuration #1 chosen from 1 choice
[   24.848000] parport_pc: VIA 686A/8231 detected
[   24.848000] parport_pc: probing current configuration
[   24.848000] parport_pc: Current parallel port base: 0x378
[   24.848000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   24.948000] parport_pc: VIA parallel port: io=0x378, irq=7
[   25.580000] Linux agpgart interface v0.102 (c) Dave Jones
[   25.596000] agpgart: Detected VIA KX133 chipset
[   25.604000] agpgart: AGP aperture is 64M @ 0xe0000000
[   25.784000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.836000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.452000] nvidia: module license 'NVIDIA' taints kernel.
[   28.720000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   28.720000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   29.368000] input: PC Speaker as /class/input/input2
[   29.868000] Linux video capture interface: v2.00
[   30.048000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   30.380000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   31.484000] usbcore: registered new interface driver gspca
[   31.484000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   31.700000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   32.648000] lp0: using parport0 (interrupt-driven).
[   32.780000] Adding 1116508k swap on /dev/hda3.  Priority:-1 extents:1 across:1116508k
[   33.220000] EXT3 FS on hda2, internal journal
[   45.280000] kjournald starting.  Commit interval 5 seconds
[   45.280000] EXT3 FS on hda5, internal journal
[   45.280000] EXT3-fs: mounted filesystem with ordered data mode.
[   45.404000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[   45.404000] ReiserFS: hda1: using ordered data mode
[   45.408000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   45.412000] ReiserFS: hda1: checking transaction log (hda1)
[   45.444000] ReiserFS: hda1: Using r5 hash to sort names
[   47.704000] input: Power Button (FF) as /class/input/input4
[   47.704000] ACPI: Power Button (FF) [PWRF]
[   47.748000] input: Power Button (CM) as /class/input/input5
[   47.748000] ACPI: Power Button (CM) [PWRB]
[   48.092000] No dock devices found.
[   48.836000] powernow: No powernow capabilities detected
[   51.652000] ppdev: user-space parallel port driver
[   52.044000] eth0: link down
[   52.540000] audit(1202560722.046:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4579 profile="/usr/sbin/cupsd"
[   52.656000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   52.656000] apm: overridden by ACPI.
[   53.164000] Failure registering capabilities with primary security module.
[   53.556000] Bluetooth: Core ver 2.11
[   53.556000] NET: Registered protocol family 31
[   53.556000] Bluetooth: HCI device and connection manager initialized
[   53.556000] Bluetooth: HCI socket layer initialized
[   53.660000] Bluetooth: L2CAP ver 2.8
[   53.660000] Bluetooth: L2CAP socket layer initialized
[   53.768000] Bluetooth: RFCOMM socket layer initialized
[   53.768000] Bluetooth: RFCOMM TTY layer initialized
[   53.768000] Bluetooth: RFCOMM ver 1.8
[   56.600000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   56.600000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   56.600000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   76.012000] NET: Registered protocol family 10
[   76.012000] lo: Disabled Privacy Extensions
[   76.012000] ADDRCONF(NETDEV_UP): eth0: link is not ready
jose@jose-desktop:~$ 

```
A ver si alguien encuentra algo "raro"

---

### Post by atari130xe on 2008-02-09
Ahora un: dmesg | less
A ver si alguien me puede ayudar con estos datos:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ub
untu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bff3000 - 000000001c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114672
[    0.000000]   HighMem    114672 ->   114672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114672
[    0.000000] On node 0 totalpages: 114672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109713 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F79A0 checksum 0
[    0.000000] ACPI: RSDP 000F79A0, 0014 (r0 SOYO  )
[    0.000000] ACPI: RSDT 1BFF3000, 0028 (r1 SOYO   AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1BFF3040, 0074 (r1 SOYO   AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1BFF30C0, 22C3 (r1 SOYO   AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1BFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 113777
[    0.000000] Kernel command line: root=UUID=d5759f95-b3cc-454f-9249-b0893f5da167 ro quiet splash locale=es_ES
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0138c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 600.047 MHz processor.
[   26.791464] Console: colour VGA+ 80x25
[   26.792512] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.793516] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.834228] Memory: 443148k/458688k available (2015k kernel code, 14904k reserved, 916k data, 364k init, 0k highmem)
[   26.834265] virtual kernel memory layout:
[   26.834269]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.834273]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.834278]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   26.834282]     lowmem  : 0xc0000000 - 0xdbff0000   ( 447 MB)
[   26.834287]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.834291]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   26.834296]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   26.834308] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.834443] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.914465] Calibrating delay using timer specific routine.. 1201.84 BogoMIPS (lpj=2403685)
[   26.914559] Security Framework v1.0.0 initialized
[   26.914579] SELinux:  Disabled at boot.
[   26.914636] Mount-cache hash table entries: 512
[   26.915040] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   26.915072] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.915081] CPU: L2 Cache: 512K (64 bytes/line)
[   26.915090] CPU: After all inits, caps: 0183f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   26.915123] Compat vDSO mapped to ffffe000.
[   26.915160] Checking 'hlt' instruction... OK.
[   26.930546] SMP alternatives: switching to UP code
[   26.931259] Freeing SMP alternatives: 11k freed
[   26.932228] Early unpacking initramfs... done
[   27.990294] ACPI: Core revision 20070126
[   27.990547] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.993221] ACPI: setting ELCR to 0800 (from 0e00)
[   27.994769] CPU0: AMD Athlon(tm) Processor stepping 01
[   27.994787] SMP motherboard not detected.
[   27.994796] Local APIC not detected. Using dummy APIC emulation.
[   27.994941] Brought up 1 CPUs
[   27.995365] Booting paravirtualized kernel on bare hardware
[   27.995538] Time: 12:37:50  Date: 01/09/108
[   27.995630] NET: Registered protocol family 16
[   27.995980] EISA bus registered
[   27.996015] ACPI: bus type pci registered
[   28.029330] PCI: PCI BIOS revision 2.10 entry at 0xfb110, last bus=1
[   28.029340] PCI: Using configuration type 1
[   28.029346] Setting up standard PCI resources
[   28.045810] ACPI: EC: Look up EC in DSDT
[   28.050954] ACPI: Interpreter enabled
[   28.050966] ACPI: (supports S0 S1 S4 S5)
[   28.051017] ACPI: Using PIC for interrupt routing
[   28.062185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.062221] PCI: Probing PCI hardware (bus 00)
[   28.062779] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
[   28.062790] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   28.062800] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   28.063362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.099998] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   28.100384] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   28.100761] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   28.101134] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[   28.101412] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.101466] pnp: PnP ACPI init
[   28.101495] ACPI: bus type pnp registered
[   28.109016] pnp: PnP ACPI: found 13 devices
[   28.109026] ACPI: ACPI bus type pnp unregistered
[   28.109039] PnPBIOS: Disabled by ACPI PNP
[   28.109212] PCI: Using ACPI for IRQ routing
[   28.109223] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.139317] NET: Registered protocol family 8
[   28.139326] NET: Registered protocol family 20
[   28.139563] pnp: 00:00: iomem range 0xcec00-0xcffff has been reserved
[   28.139576] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   28.139586] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   28.139596] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   28.142101] Time: tsc clocksource has been installed.
[   28.170741] PCI: Bridge: 0000:00:01.0
[   28.170747]   IO window: disabled.
[   28.170759]   MEM window: e4000000-e6ffffff
[   28.170769]   PREFETCH window: d0000000-dfffffff
[   28.170799] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.170840] NET: Registered protocol family 2
[   28.210239] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   28.210409] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   28.211283] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   28.212002] TCP: Hash tables configured (established 16384 bind 16384)
[   28.212014] TCP reno registered
[   28.222533] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   29.142712]  it is
[   30.246440] Freeing initrd memory: 7040k freed
[   30.247833] audit: initializing netlink socket (disabled)
[   30.247878] audit(1202560672.312:1): initialized
[   30.254925] VFS: Disk quotas dquot_6.5.1
[   30.255135] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.255470] io scheduler noop registered
[   30.255479] io scheduler anticipatory registered
[   30.255486] io scheduler deadline registered
[   30.255542] io scheduler cfq registered (default)
[   30.255579] PCI: VIA PCI bridge detected. Disabling DAC.
[   30.255597] PCI: Disabling Via external APIC routing
[   30.255702] Boot video device is 0000:01:00.0
[   30.256267] isapnp: Scanning for PnP cards...
[   30.358331] isapnp: Card 'U.S. Robotics 56K Voice INT'
[   30.358342] isapnp: 1 Plug & Play card detected total
[   30.466225] Real Time Clock Driver v1.12ac
[   30.466532] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.466764] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.467284] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.469064] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.469991] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.472728] pnp: Device 01:01.00 activated.
[   30.473111] 01:01.00: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
[   30.475745] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.476531] input: Macintosh mouse button emulation as /class/input/input0
[   30.476824] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   30.477506] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.477525] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.478131] mice: PS/2 mouse device common for all mice
[   30.478524] EISA: Probing bus 0 at eisa.0
[   30.478572] Cannot allocate resource for EISA slot 4
[   30.478579] Cannot allocate resource for EISA slot 5
[   30.478587] Cannot allocate resource for EISA slot 6
[   30.478607] EISA: Detected 0 cards.
[   30.478909] TCP cubic registered
[   30.478945] NET: Registered protocol family 1
[   30.479008] Using IPI No-Shortcut mode
[   30.479524]   Magic number: 12:502:632
[   30.479714]   hash matches device ptycb
[   30.481145] Freeing unused kernel memory: 364k freed
[   30.549376] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.215988] AppArmor: AppArmor initialized<5>audit(1202560674.312:2):  type=1505 info="AppArmor initialized" pid=1167
[   32.238730] fuse init (API version 7.8)
[   32.256001] Failure registering capabilities with primary security module.
[   32.301169] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   32.301188] ACPI: Processor [CPU0] (supports 2 throttling states)
[   34.186798] SCSI subsystem initialized
[   34.204750] libata version 2.21 loaded.
[   34.225511] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.225528] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.227466] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   34.227514] VP_IDE: chipset revision 16
[   34.227521] VP_IDE: not 100% native mode: will probe irqs later
[   34.227547] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[   34.227565]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   34.227592]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[   34.227612] Probing IDE interface ide0...
[   34.341842] usbcore: registered new interface driver usbfs
[   34.341918] usbcore: registered new interface driver hub
[   34.342002] usbcore: registered new device driver usb
[   34.345001] USB Universal Host Controller Interface driver v3.0
[   34.456920] 8139too Fast Ethernet driver 0.9.28
[   34.739779] hda: SAMSUNG SP0822N, ATA DISK drive
[   35.105422] Floppy drive(s): fd0 is 1.44M
[   35.129363] FDC 0 is a post-1991 82077
[    8.360000] Marking TSC unstable due to: possible TSC halt in C2.
[    8.384000] Time: acpi_pm clocksource has been installed.
[    8.584000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.584000] Probing IDE interface ide1...
[    9.448000] hdc: Optiarc DVD RW AD-7190A, ATAPI CD/DVD-ROM drive
[   10.120000] ide1 at 0x170-0x177,0x376 on irq 15
[   10.120000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   10.120000] PCI: setting IRQ 10 as level-triggered
[   10.120000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.120000] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 9 to 10
[   10.120000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   10.124000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   10.124000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[   10.124000] usb usb1: configuration #1 chosen from 1 choice
[   10.124000] hub 1-0:1.0: USB hub found
[   10.124000] hub 1-0:1.0: 2 ports detected
[   10.148000] hda: max request size: 512KiB
[   10.184000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[   10.188000] hda: cache flushes supported
[   10.188000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[   10.264000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.264000] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 9 to 10
[   10.264000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   10.264000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   10.264000] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   10.264000] usb usb2: configuration #1 chosen from 1 choice
[   10.264000] hub 2-0:1.0: USB hub found
[   10.264000] hub 2-0:1.0: 2 ports detected
[   10.304000] hdc: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   10.304000] Uniform CD-ROM driver Revision: 3.20
[   10.388000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.388000] PCI: setting IRQ 11 as level-triggered
[   10.388000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.388000] uhci_hcd 0000:00:0a.0: UHCI Host Controller
[   10.388000] uhci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 3
[   10.388000] uhci_hcd 0000:00:0a.0: irq 11, io base 0x0000e000
[   10.392000] usb usb3: configuration #1 chosen from 1 choice
[   10.392000] hub 3-0:1.0: USB hub found
[   10.392000] hub 3-0:1.0: 2 ports detected
[   10.496000] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.496000] uhci_hcd 0000:00:0a.1: UHCI Host Controller
[   10.496000] uhci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 4
[   10.496000] uhci_hcd 0000:00:0a.1: irq 10, io base 0x0000e400
[   10.500000] usb usb4: configuration #1 chosen from 1 choice
[   10.500000] hub 4-0:1.0: USB hub found
[   10.500000] hub 4-0:1.0: 2 ports detected
[   10.604000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   10.604000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   10.608000] eth0: RealTek RTL8139 at 0xdc83a000, 00:50:fc:2b:80:ac, IRQ 11
[   10.608000] eth0:  Identified 8139 chip type 'RTL-8139C'
[   10.612000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   10.616000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   10.616000] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   10.616000] ehci_hcd 0000:00:0a.2: EHCI Host Controller
[   10.616000] ehci_hcd 0000:00:0a.2: new USB bus registered, assigned bus number 5
[   10.616000] ehci_hcd 0000:00:0a.2: irq 10, io mem 0xe8001000
[   10.616000] ehci_hcd 0000:00:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.616000] usb usb5: configuration #1 chosen from 1 choice
[   10.616000] hub 5-0:1.0: USB hub found
[   10.616000] hub 5-0:1.0: 4 ports detected
[   10.988000] Attempting manual resume
[   10.988000] swsusp: Resume From Partition 3:3
[   10.988000] PM: Checking swsusp image.
[   10.988000] PM: Resume from disk failed.
[   11.056000] kjournald starting.  Commit interval 5 seconds
[   11.056000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.852000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   12.040000] usb 4-1: configuration #1 chosen from 1 choice
[   24.848000] parport_pc: VIA 686A/8231 detected
[   24.848000] parport_pc: probing current configuration
[   24.848000] parport_pc: Current parallel port base: 0x378
[   24.848000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   24.948000] parport_pc: VIA parallel port: io=0x378, irq=7
[   25.580000] Linux agpgart interface v0.102 (c) Dave Jones
[   25.596000] agpgart: Detected VIA KX133 chipset
[   25.604000] agpgart: AGP aperture is 64M @ 0xe0000000
[   25.784000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.836000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.452000] nvidia: module license 'NVIDIA' taints kernel.
[   28.720000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   28.720000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   29.368000] input: PC Speaker as /class/input/input2
[   29.868000] Linux video capture interface: v2.00
[   30.048000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   30.380000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   31.484000] usbcore: registered new interface driver gspca
[   31.484000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   31.700000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   32.648000] lp0: using parport0 (interrupt-driven).
[   32.780000] Adding 1116508k swap on /dev/hda3.  Priority:-1 extents:1 across:1116508k
[   33.220000] EXT3 FS on hda2, internal journal
[   45.280000] kjournald starting.  Commit interval 5 seconds
[   45.280000] EXT3 FS on hda5, internal journal
[   45.280000] EXT3-fs: mounted filesystem with ordered data mode.
[   45.404000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[   45.404000] ReiserFS: hda1: using ordered data mode
[   45.408000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   45.412000] ReiserFS: hda1: checking transaction log (hda1)
[   45.444000] ReiserFS: hda1: Using r5 hash to sort names
[   47.704000] input: Power Button (FF) as /class/input/input4
[   47.704000] ACPI: Power Button (FF) [PWRF]
[   47.748000] input: Power Button (CM) as /class/input/input5
[   47.748000] ACPI: Power Button (CM) [PWRB]
[   48.092000] No dock devices found.
[   48.836000] powernow: No powernow capabilities detected
[   51.652000] ppdev: user-space parallel port driver
[   52.044000] eth0: link down
[   52.540000] audit(1202560722.046:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4579 profile="/usr/sbin/cupsd"
[   52.656000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   52.656000] apm: overridden by ACPI.
[   53.164000] Failure registering capabilities with primary security module.
[   53.556000] Bluetooth: Core ver 2.11
[   53.556000] NET: Registered protocol family 31
[   53.556000] Bluetooth: HCI device and connection manager initialized
[   53.556000] Bluetooth: HCI socket layer initialized
[   53.660000] Bluetooth: L2CAP ver 2.8
[   53.660000] Bluetooth: L2CAP socket layer initialized
[   53.768000] Bluetooth: RFCOMM socket layer initialized
[   53.768000] Bluetooth: RFCOMM TTY layer initialized
[   53.768000] Bluetooth: RFCOMM ver 1.8
[   56.600000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   56.600000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   56.600000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   76.012000] NET: Registered protocol family 10
[   76.012000] lo: Disabled Privacy Extensions
[   76.012000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  207.716000] PPP generic driver version 2.4.2
[  254.788000] PPP BSD Compression module registered
[  254.964000] PPP Deflate Compression module registered

```

Me parece que tengo problemas con ACPI y las interrupciones IRQ alguien podria decirme con solucionar esto?

---

### Post by faktorqm on 2008-02-09
de irq no vi nada. de acpi tampoco, en las ultimas lineas lo que dice es que apm fue "reemplazado" por acpi, deberias sacar apm creo yo, pero nada mas. salu2!

---

### Post by atari130xe on 2008-02-09
> **faktorqm said:**
> de irq no vi nada. de acpi tampoco, en las ultimas lineas lo que dice es que apm fue "reemplazado" por acpi, deberias sacar apm creo yo, pero nada mas. salu2! Voy a intentar desactivando ACPI de la BIOS, por alguna  razón algo esta en "corto" porque no puedo hacer 2 cosas simultaneamente (ejemplo: estar conectado a internet y escuchar musica, automaticamente se me corta la conexion), o sea veo que onda y despues te digo. Antes de actualizar la BIOS me daba errores con el ACPI luego no los tuve más pero empecé a tenes estos problemas, en fin a buscarle la vuelta!

---

### Post by atari130xe on 2008-02-11
Bueno, en lugar de ACPI dejé APM y aparentemente la cosa mejoró, no se corta ahora, como mi PC es viejita es muy probable que ACPI entre en conflicto con mi modem ISA PnP. gracias!

---

