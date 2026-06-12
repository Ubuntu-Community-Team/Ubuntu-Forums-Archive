---
title: "New install, no sound! ALC850 on GA-k8n51gmf mobo"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-25
Hi,

I'm getting no sound at all, in fact my PC, with a fresh install of 5.10 64 bit version, is not recognizing my sound at all. There is no sound while booting, and there is a red "X" next to volume control. My Gigabyte GA-K8N51GMF mobo with onboard ALC850 Sound, and 6100 graphics seems to running great, but this sound issue.

Also when I goto system/preferences/sound, there is nothing listed or choices under default sound card. It seems like I just need to install a driver. Can anyone help?

Any ideas how to enable? Thanks

linux@ubuntu:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 02f1 (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 02fa (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 02fe (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 02f8 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 02f9 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation: Unknown device 02ff (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation: Unknown device 027f (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation: Unknown device 027e (rev a2)
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0242 (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 0270 (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0261 (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation: Unknown device 0264 (rev a2)
0000:00:0a.2 RAM memory: nVidia Corporation: Unknown device 0272 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation: Unknown device 026d (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation: Unknown device 026e (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation: Unknown device 0265 (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation: Unknown device 0266 (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation: Unknown device 026f (rev a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026b (rev a2)
0000:00:14.0 Bridge: nVidia Corporation: Unknown device 0269 (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


C timer.
[   17.008076] testing NMI watchdog ... OK.
[   17.018174] NET: Registered protocol family 16
[   17.018200] ACPI: bus type pci registered
[   17.018274] PCI: Using configuration type 1
[   17.018277] mtrr: v2.0 (20020519)
[   17.018608] ACPI: Subsystem revision 20050729
[   17.033267] ACPI: Interpreter enabled
[   17.033271] ACPI: Using IOAPIC for interrupt routing
[   17.033910] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.033913] PCI: Probing PCI hardware (bus 00)
[   17.034061] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[   17.040425] Boot video device is 0000:00:05.0
[   17.041023] PCI: Transparent bridge - 0000:00:10.0
[   17.195519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.196265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   17.198233] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.198743] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.199242] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.199750] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[   17.200245] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.200749] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.201243] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
[   17.201745] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.202244] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   17.202749] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.203245] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   17.203748] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 *11 14 15)
[   17.204243] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.204745] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.205241] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.205748] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   17.206245] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   17.206750] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.207248] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   17.207753] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.208366] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   17.208975] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   17.209590] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   17.210191] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   17.210799] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   17.211400] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   17.212006] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   17.212612] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   17.213212] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   17.213824] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   17.214426] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   17.215035] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   17.215645] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   17.216247] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   17.216860] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   17.217464] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   17.218079] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   17.218688] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   17.219289] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   17.219897] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   17.220506] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   17.224665] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.224680] pnp: PnP ACPI init
[   17.233800]     ACPI-0423: *** Error: Handler for [SystemMemory] returned AE_AML_ALIGNMENT
[   17.233808]     ACPI-0508: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff810016e7ddc0), AE_AML_ALIGNMENT
[   17.233898]     ACPI-0171: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff810016e7ddc0), AE_AML_ALIGNMENT
[   17.233908] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c01
[   17.233933] pnp: PnP ACPI: found 11 devices
[   17.234022] usbcore: registered new driver usbfs
[   17.234044] usbcore: registered new driver hub
[   17.234080] PCI: Using ACPI for IRQ routing
[   17.234087] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.234180] PCI-DMA: Disabling IOMMU.
[   17.234481]     ACPI-0423: *** Error: Handler for [SystemMemory] returned AE_AML_ALIGNMENT
[   17.234488]     ACPI-0508: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff810016e7ddc0), AE_AML_ALIGNMENT
[   17.234582]     ACPI-0171: *** Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff810016e7ddc0), AE_AML_ALIGNMENT
[   17.235004] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[   17.235009] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[   17.235013] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[   17.235017] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[   17.235020] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[   17.235024] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[   17.235028] pnp: 00:00: ioport range 0x2000-0x207f has been reserved
[   17.235031] pnp: 00:00: ioport range 0x2080-0x20ff has been reserved
[   17.235327] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   17.235545] audit: initializing netlink socket (disabled)
[   17.235554] audit: initialized
[   17.235662] VFS: Disk quotas dquot_6.5.1
[   17.235679] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   17.235707] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   17.235712] devfs: boot_options: 0x0
[   17.235738] Initializing Cryptographic API
[   17.253114] Linux agpgart interface v0.101 (c) Dave Jones
[   17.253191] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[   17.253196] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[   17.255015] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.255078] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.255082] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   17.255216] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.255368] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.257147] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.257298] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.257384] io scheduler noop registered
[   17.257399] io scheduler anticipatory registered
[   17.257405] io scheduler deadline registered
[   17.257414] io scheduler cfq registered
[   17.257753] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.257826] NET: Registered protocol family 2
[   17.267517] IP: routing cache hash table of 4096 buckets, 32Kbytes
[   17.267685] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   17.267789] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   17.267895] TCP: Hash tables configured (established 16384 bind 16384)
[   17.267961] NET: Registered protocol family 8
[   17.267964] NET: Registered protocol family 20
[   17.268103] ACPI wakeup devices:
[   17.268106] HUB0 XVRA XVRB XVRC USB0 USB2 AZAD MMAC MMCI UAR1
[   17.268112] ACPI: (supports S0 S1 S4 S5)
[   17.268308] Freeing unused kernel memory: 136k freed
[   17.286116] vga16fb: initializing
[   17.286121] vga16fb: mapped to 0xffff8100000a0000
[   17.478512] Console: switching to colour frame buffer device 80x30
[   17.478518] fb0: VGA16 VGA frame buffer device
[   17.547494] input: AT Translated Set 2 keyboard on isa0060/serio0
[   18.604157] Capability LSM initialized
[   18.614592] NET: Registered protocol family 1
[   18.631270] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.631282] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.631286] ACPI: bus type ide registered
[   18.635222] SCSI subsystem initialized
[   18.636465] libata version 1.11 loaded.
[   18.638634] sata_nv version 0.6
[   18.639306] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   18.639312] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   18.639332] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.639382] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xDC00 irq 23
[   18.639404] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xDC08 irq 23
[   18.994125] ata1: dev 0 cfg 49:2f00 82:706b 83:7e01 84:4023 85:7068 86:3c01 87:4023 88:407f
[   18.994130] ata1: dev 0 ATA, max UDMA/133, 156312576 sectors: lba48
[   18.994219] ata1: dev 0 configured for UDMA/133
[   18.994222] scsi0 : sata_nv
[   19.194906] ata2: no device found (phy stat 00000000)
[   19.194909] scsi1 : sata_nv
[   19.194991]   Vendor: ATA       Model: WDC WD800JD-08LS  Rev: 09.0
[   19.194998]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   19.208279] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   19.208302] NFORCE-MCP51: chipset revision 161
[   19.208304] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   19.208312] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   19.208323]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.208335]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   19.208343] Probing IDE interface ide0...
[   19.879813] hda: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[   20.491812] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.491870] Probing IDE interface ide1...
[   21.010419] Probing IDE interface ide1...
[   21.528231] Probing IDE interface ide2...
[   22.040083] Probing IDE interface ide3...
[   22.551935] Probing IDE interface ide4...
[   23.063787] Probing IDE interface ide5...
[   23.582133] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   23.582141] Uniform CD-ROM driver Revision: 3.20
[   23.588523] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[   23.588535] SCSI device sda: drive cache: write back
[   23.588605] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[   23.588613] SCSI device sda: drive cache: write back
[   23.588616]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
[   23.616091] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[   23.965246] Attempting manual resume
[   23.965424] swsusp: Suspend partition has wrong signature?
[   24.034116] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   24.034882] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   24.034889] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   24.034910] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.034914] ohci_hcd 0000:00:0b.0: nVidia Corporation MCP51 USB Controller
[   24.035075] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   24.035088] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xf5104000
[   24.087573] hub 1-0:1.0: USB hub found
[   24.087584] hub 1-0:1.0: 8 ports detected
[   24.097170] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[   24.097179] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 21
[   24.097197] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   24.097202] ehci_hcd 0000:00:0b.1: nVidia Corporation MCP51 USB Controller
[   24.097211] ehci_hcd 0000:00:0b.1: debug port 1
[   24.097258] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   24.097271] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xf5100000
[   24.097303] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   24.097307] ehci_hcd 0000:00:0b.1: park 0
[   24.097314] ehci_hcd 0000:00:0b.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   24.097402] hub 2-0:1.0: USB hub found
[   24.097411] hub 2-0:1.0: 8 ports detected
[   24.144240] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   24.144993] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   24.145000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[   24.145008] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   24.552357] usb 1-5: new low speed USB device using ohci_hcd and address 2
[   24.656538] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:14.0
[   26.693475] usbcore: registered new driver hiddev
[   26.705175] input: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer\uffff] on usb-0000:00:0b.0-5
[   26.705184] usbcore: registered new driver usbhid
[   26.705188] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   27.202570] ACPI: CPU0 (power states: C1[C1])
[   27.388697] Attempting manual resume
[   27.388881] swsusp: Suspend partition has wrong signature?
[   27.399600] kjournald starting.  Commit interval 5 seconds
[   27.399613] EXT3-fs: mounted filesystem with ordered data mode.
[   28.353753] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   31.489045] Adding 1108444k swap on /dev/sda5.  Priority:-1 extents:1
[   31.773389] EXT3 FS on sda1, internal journal
[   36.557164] parport: PnPBIOS parport detected.
[   36.557228] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   36.644128] lp0: using parport0 (interrupt-driven).
[   36.671962] mice: PS/2 mouse device common for all mice
[   36.723884] Real Time Clock Driver v1.12
[   36.760187] ieee1394: Initialized config rom entry `ip1394'
[   36.778662] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   39.966066] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   40.621245] cdrom: open failed.
[   43.355913] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   43.356666] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   43.356674] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   43.356682] PCI: Via IRQ fixup for 0000:01:0e.0, from 10 to 3
[   43.414016] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
[   44.679051] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000148500e4e635]
[   44.969702] input: PC Speaker
[   45.022036] Floppy drive(s): fd0 is 1.44M
[   45.095564] FDC 0 is a post-1991 82077
[   45.374367] ts: Compaq touchscreen protocol output
[   46.817145] NET: Registered protocol family 17
[   51.055275] NET: Registered protocol family 10
[   51.055400] Disabled Privacy Extensions on device ffffffff8035a7c0(lo)
[   51.055795] IPv6 over IPv4 tunneling driver
[   52.345138] ACPI: Power Button (FF) [PWRF]
[   52.345151] ACPI: Power Button (CM) [PWRB]
[   52.450135] ibm_acpi: ec object not found
[   59.807594] powernow-k8: Power state transitions not supported
[   59.942061] Bluetooth: Core ver 2.7
[   59.942071] NET: Registered protocol family 31
[   59.942074] Bluetooth: HCI device and connection manager initialized
[   59.942086] Bluetooth: HCI socket layer initialized
[   59.962626] Bluetooth: L2CAP ver 2.7
[   59.962632] Bluetooth: L2CAP socket layer initialized
[   59.986495] Bluetooth: RFCOMM ver 1.5
[   59.986505] Bluetooth: RFCOMM socket layer initialized
[   59.986519] Bluetooth: RFCOMM TTY layer initialized
[   61.146698] eth0: no IPv6 routers present
linux@ubuntu:~$

Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:15:30 UTC 2006

---

### Post by gordong11 on 2006-03-25
there has got to be a fix...anyone?

---

### Post by WelterPelter on 2006-03-27
I just got the same board, although I'm still running my 32-bit install on it. Can't get any sound either. Anybody have an answer?

---

### Post by shambling on 2006-03-28
see:
[http://www.nvnews.net/vbulletin/showthread.php?t=57791](http://www.nvnews.net/vbulletin/showthread.php?t=57791)

&

[http://www.ubuntuforums.org/showthread.php?t=150387&highlight=nforce](http://www.ubuntuforums.org/showthread.php?t=150387&highlight=nforce)

Have not had time to read through the nvidia fourms fully, or setup alsa yet.

Installed 0310 nforce driver, works to a point. Only media players that use OSS work, anything that trys to use alsa fails to work, alsa mixer cant find card.

Hope this helps in some way.

---

