---
title: "Ubuntu not turning the comp off"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-08
Recently when using ubuntu when i ask the computer to turn off, it hasen't always been doing it, Sometimes it seems to be closing itself down, but just stands there with a blank screen at the end, the screen is black, but illuminated, i left it on all last night to see if it would turn itself off, but nothing happened.

---

### Post by ukripper on 2007-11-08
can you post output of following command here:

```
dmesg
```

also post output of following:```
sudo cat /boot/grub/menu.lst
```

---

### Post by Falc7 on 2007-11-08
This is from the first command, i think it missed out the top though, the terminal isen't big enough

[   17.774772] ACPI: EC: Look up EC in DSDT
[   17.775600] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   17.776768] ACPI: System BIOS is requesting _OSI(Linux)
[   17.776770] ACPI: Please test with "acpi_osi=!Linux"
[   17.776771] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   17.777168] ACPI: Interpreter enabled
[   17.777171] ACPI: (supports S0 S3 S4 S5)
[   17.777186] ACPI: Using IOAPIC for interrupt routing
[   17.782495] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   17.782544] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.782555] PCI: Probing PCI hardware (bus 00)
[   17.783232] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.783236] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   17.784617] PCI: Transparent bridge - 0000:00:1e.0
[   17.784700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.784938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   17.785048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   17.785149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   17.785248] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   17.785359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   17.790732] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[   17.790836] ACPI: PCI Interrupt Link [LNKB] (IRQs *3)
[   17.790938] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[   17.791039] ACPI: PCI Interrupt Link [LNKD] (IRQs *4)
[   17.791140] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[   17.791241] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[   17.791345] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[   17.791446] ACPI: PCI Interrupt Link [LNKH] (IRQs *7)
[   17.791550] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.791582] pnp: PnP ACPI init
[   17.791589] ACPI: bus type pnp registered
[   17.793448] pnp: PnP ACPI: found 11 devices
[   17.793450] ACPI: ACPI bus type pnp unregistered
[   17.793453] PnPBIOS: Disabled by ACPI PNP
[   17.793488] PCI: Using ACPI for IRQ routing
[   17.793490] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.820745] NET: Registered protocol family 8
[   17.820747] NET: Registered protocol family 20
[   17.820802] pnp: 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.820807] pnp: 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.820810] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.820812] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.820815] pnp: 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   17.820820] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   17.820826] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   17.820829] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   17.823546] Time: tsc clocksource has been installed.
[   17.823558] Switched to high resolution mode on CPU 0
[   17.823638] Switched to high resolution mode on CPU 1
[   17.851115] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[   17.851176] PCI: Bridge: 0000:00:01.0
[   17.851178]   IO window: 2000-2fff
[   17.851181]   MEM window: dc000000-ddffffff
[   17.851184]   PREFETCH window: c0000000-cfffffff
[   17.851188] PCI: Bridge: 0000:00:1c.0
[   17.851190]   IO window: 3000-3fff
[   17.851196]   MEM window: d8000000-d9ffffff
[   17.851201]   PREFETCH window: d2000000-d3ffffff
[   17.851206] PCI: Bridge: 0000:00:1c.1
[   17.851209]   IO window: 4000-4fff
[   17.851215]   MEM window: d6000000-d7ffffff
[   17.851219]   PREFETCH window: d0000000-d1ffffff
[   17.851225] PCI: Bridge: 0000:00:1c.2
[   17.851228]   IO window: 5000-5fff
[   17.851233]   MEM window: da000000-dbffffff
[   17.851238]   PREFETCH window: d4000000-d5ffffff
[   17.851244] PCI: Bridge: 0000:00:1e.0
[   17.851245]   IO window: disabled.
[   17.851250]   MEM window: de000000-de0fffff
[   17.851255]   PREFETCH window: disabled.
[   17.851269] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.851274] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.851296] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   17.851302] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.851324] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   17.851329] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.851352] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.851357] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.851368] PCI: Enabling device 0000:00:1e.0 (0004 -> 0006)
[   17.851374] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.851383] NET: Registered protocol family 2
[   17.891514] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.891562] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   17.892136] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.892327] TCP: Hash tables configured (established 131072 bind 65536)
[   17.892329] TCP reno registered
[   17.907605] checking if image is initramfs... it is
[   18.471139] Freeing initrd memory: 7346k freed
[   18.471251] Simple Boot Flag at 0x35 set to 0x1
[   18.471711] audit: initializing netlink socket (disabled)
[   18.471727] audit(1194555119.388:1): initialized
[   18.471821] highmem bounce pool size: 64 pages
[   18.473414] VFS: Disk quotas dquot_6.5.1
[   18.473456] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.473537] io scheduler noop registered
[   18.473539] io scheduler anticipatory registered
[   18.473541] io scheduler deadline registered
[   18.473552] io scheduler cfq registered (default)
[   18.473651] Boot video device is 0000:01:00.0
[   18.473728] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.473763] assign_interrupt_mode Found MSI capability
[   18.473766] Allocate Port Service[0000:00:01.0:pcie00]
[   18.473839] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.473895] assign_interrupt_mode Found MSI capability
[   18.473897] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.473922] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.474014] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.474071] assign_interrupt_mode Found MSI capability
[   18.474073] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.474102] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.474196] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.474252] assign_interrupt_mode Found MSI capability
[   18.474254] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.474281] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.474434] isapnp: Scanning for PnP cards...
[   18.828208] isapnp: No Plug & Play device found
[   18.845215] Real Time Clock Driver v1.12ac
[   18.845422] hpet_resources: 0xfed00000 is busy
[   18.845447] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.846343] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.846518] input: Macintosh mouse button emulation as /class/input/input0
[   18.846582] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.864811] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.864816] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.864926] mice: PS/2 mouse device common for all mice
[   18.865858] EISA: Probing bus 0 at eisa.0
[   18.865864] Cannot allocate resource for EISA slot 1
[   18.865867] Cannot allocate resource for EISA slot 2
[   18.865869] Cannot allocate resource for EISA slot 3
[   18.865871] Cannot allocate resource for EISA slot 4
[   18.865873] Cannot allocate resource for EISA slot 5
[   18.865887] EISA: Detected 0 cards.
[   18.865956] TCP cubic registered
[   18.865967] NET: Registered protocol family 1
[   18.865985] Using IPI No-Shortcut mode
[   18.866124]   Magic number: 15:93:902
[   18.866159]   hash matches device ptyvf
[   18.866364] Freeing unused kernel memory: 364k freed
[   18.878760] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.033720] AppArmor: AppArmor initialized<5>audit(1194555120.888:2):  type=1505 info="AppArmor initialized" pid=1244
[   20.038549] fuse init (API version 7.8)
[   20.042239] Failure registering capabilities with primary security module.
[   20.070309] ACPI: SSDT 7FE7C0DD, 0238 (r1 HP     30BD         3000 INTL 20050624)
[   20.070490] ACPI: SSDT 7FE7BB96, 04C2 (r1 HP     30BD         3001 INTL 20050624)
[   20.070903] Monitor-Mwait will be used to enter C-1 state
[   20.070906] Monitor-Mwait will be used to enter C-2 state
[   20.070908] Monitor-Mwait will be used to enter C-3 state
[   20.070912] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.070916] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.071122] ACPI: SSDT 7FE7C315, 00C8 (r1 HP     30BD         3000 INTL 20050624)
[   20.071301] ACPI: SSDT 7FE7C058, 0085 (r1 HP     30BD         3000 INTL 20050624)
[   20.071733] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.071738] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.136000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.136000] ACPI: Thermal Zone [THR1] (52 C)
[    3.140000] Time: hpet clocksource has been installed.
[    3.504000] usbcore: registered new interface driver usbfs
[    3.504000] usbcore: registered new interface driver hub
[    3.504000] usbcore: registered new device driver usb
[    3.504000] USB Universal Host Controller Interface driver v3.0
[    3.504000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.504000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.504000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.508000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.508000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[    3.508000] usb usb1: configuration #1 chosen from 1 choice
[    3.508000] hub 1-0:1.0: USB hub found
[    3.508000] hub 1-0:1.0: 2 ports detected
[    3.528000] SCSI subsystem initialized
[    3.532000] libata version 2.21 loaded.
[    3.568000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.568000] Copyright (c) 1999-2006 Intel Corporation.
[    3.612000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.612000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.612000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.612000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.612000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[    3.612000] usb usb2: configuration #1 chosen from 1 choice
[    3.612000] hub 2-0:1.0: USB hub found
[    3.612000] hub 2-0:1.0: 2 ports detected
[    3.716000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.716000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.716000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.716000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.716000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    3.716000] usb usb3: configuration #1 chosen from 1 choice
[    3.716000] hub 3-0:1.0: USB hub found
[    3.716000] hub 3-0:1.0: 2 ports detected
[    3.820000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.820000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.820000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.820000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.820000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    3.820000] usb usb4: configuration #1 chosen from 1 choice
[    3.820000] hub 4-0:1.0: USB hub found
[    3.820000] hub 4-0:1.0: 2 ports detected
[    3.924000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.924000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.924000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.924000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.924000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.924000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.924000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xde304000
[    3.928000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.928000] usb usb5: configuration #1 chosen from 1 choice
[    3.928000] hub 5-0:1.0: USB hub found
[    3.928000] hub 5-0:1.0: 8 ports detected
[    4.000000] Clocksource tsc unstable (delta = -297970337 ns)
[    4.032000] ahci 0000:00:1f.2: version 2.2
[    4.032000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.348000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[    4.492000] usb 5-1: configuration #1 chosen from 1 choice
[    4.736000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    4.876000] usb 5-4: configuration #1 chosen from 1 choice
[    4.876000] usbcore: registered new interface driver libusual
[    4.880000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.880000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.884000] Initializing USB Mass Storage driver...
[    5.004000] scsi0 : SCSI emulation for USB Mass Storage devices
[    5.004000] usb-storage: device found at 2
[    5.004000] usb-storage: waiting for device to settle before scanning
[    5.004000] usbcore: registered new interface driver usb-storage
[    5.004000] USB Mass Storage support registered.
[    5.036000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.036000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.036000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.036000] scsi1 : ahci
[    5.036000] scsi2 : ahci
[    5.036000] scsi3 : ahci
[    5.036000] scsi4 : ahci
[    5.036000] ata1: SATA max UDMA/133 cmd 0xf886e500 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.036000] ata2: SATA max UDMA/133 cmd 0xf886e580 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.036000] ata3: SATA max UDMA/133 cmd 0xf886e600 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.036000] ata4: SATA max UDMA/133 cmd 0xf886e680 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.520000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.520000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[    5.520000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    5.520000] ata1.00: configured for UDMA/100
[    5.832000] ata2: SATA link down (SStatus 0 SControl 0)
[    6.148000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.460000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.460000] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    6.460000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    6.460000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    6.464000] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.464000] sd 1:0:0:0: [sda] Write Protect is off
[    6.464000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.464000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.464000] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.464000] sd 1:0:0:0: [sda] Write Protect is off
[    6.464000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.464000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.464000]  sda:<6>e1000: 0000:05:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1b:24:27:61:07
[    6.580000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    6.580000] ACPI: PCI Interrupt 0000:07:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.580000] PCI: Setting latency timer of device 0000:07:05.0 to 64
[    6.632000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.636000] ata_piix 0000:00:1f.1: version 2.11
[    6.636000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    6.636000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.636000] scsi5 : ata_piix
[    6.636000] scsi6 : ata_piix
[    6.636000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[    6.636000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[    6.868000]  sda1 sda2 sda3 sda4 < sda5 >
[    6.892000] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.896000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    6.972000] ata5.00: ATAPI: Slimtype DVD A  DS8AZH, NH61, max MWDMA2
[    7.160000] ata5.00: configured for MWDMA2
[    7.160000] ata6: port disabled. ignoring.
[    7.160000] scsi 5:0:0:0: CD-ROM            Slimtype DVD A  DS8AZH    NH61 PQ: 0 ANSI: 5
[    7.160000] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[    7.168000] sr0: scsi3-mmc drive: 10x/10x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.168000] Uniform CD-ROM driver Revision: 3.20
[    7.168000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    7.264000] Attempting manual resume
[    7.264000] swsusp: Resume From Partition 8:5
[    7.264000] PM: Checking swsusp image.
[    7.264000] PM: Resume from disk failed.
[    7.304000] kjournald starting.  Commit interval 5 seconds
[    7.304000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.908000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b000d471500]
[   10.004000] usb-storage: device scan complete
[   10.004000] scsi 0:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
[   10.012000] sd 0:0:0:0: [sdb] Spinning up disk...ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.456000] Netfilter messages via NETLINK v0.30.
[   13.472000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   14.524000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.580000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.616000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.644000] sdhci: Secure Digital Host Controller Interface driver
[   14.644000] sdhci: Copyright(c) Pierre Ossman
[   14.644000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   14.644000] PCI: Enabling device 0000:07:05.1 (0000 -> 0002)
[   14.644000] ACPI: PCI Interrupt 0000:07:05.1[B] -> GSI 17 (level, low) -> IRQ 17
[   14.644000] PCI: Setting latency timer of device 0000:07:05.1 to 64
[   14.644000] mmc0: SDHCI at 0xde000800 irq 17 DMA
[   14.664000] intel_rng: FWH not detected
[   14.916000] nvidia: module license 'NVIDIA' taints kernel.
[   15.168000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.168000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.168000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   15.168000] ieee80211_crypt: registered algorithm 'NULL'
[   15.168000] iTCO_vendor_support: vendor-support=0
[   15.184000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.212000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.212000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.308000] Linux video capture interface: v2.00
[   15.356000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   15.356000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   15.356000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.356000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   15.356000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   15.468000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   15.468000] usbcore: registered new interface driver uvcvideo
[   15.468000] USB Video Class driver (v0.1.0)
[   15.612000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   15.612000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.796000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   15.864000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   15.868000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.868000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.248000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   18.408000] lp: driver loaded but no devices found
[   18.480000] Adding 3943916k swap on /dev/sda5.  Priority:-1 extents:1 across:3943916k
[   18.824000] EXT3 FS on sda3, internal journal
[   19.788000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.792000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.840000] ACPI: AC Adapter [ACAD] (on-line)
[   19.896000] No dock devices found.
[   19.916000] ACPI: Battery Slot [BAT0] (battery absent)
[   19.984000] input: Power Button (FF) as /class/input/input3
[   19.984000] ACPI: Power Button (FF) [PWRF]
[   19.984000] input: Power Button (CM) as /class/input/input4
[   19.984000] ACPI: Power Button (CM) [PWRB]
[   19.984000] input: Sleep Button (CM) as /class/input/input5
[   19.984000] ACPI: Sleep Button (CM) [SLPB]
[   19.984000] input: Lid Switch as /class/input/input6
[   19.984000] ACPI: Lid Switch [LID]
[   20.152000] .ready
[   20.152000] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   20.152000] sd 0:0:0:0: [sdb] Write Protect is off
[   20.152000] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   20.152000] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   20.156000] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   20.156000] sd 0:0:0:0: [sdb] Write Protect is off
[   20.156000] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   20.156000] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   20.156000]  sdb: sdb1
[   20.180000] sd 0:0:0:0: [sdb] Attached SCSI disk
[   20.180000] sd 0:0:0:0: Attached scsi generic sg2 type 0
[   21.092000] ppdev: user-space parallel port driver
[   21.256000] audit(1194555138.855:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5289 profile="/usr/sbin/cupsd"
[   21.320000] apm: BIOS not found.
[   21.828000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.828000] vboxdrv: Successfully done.
[   22.164000] Failure registering capabilities with primary security module.
[   22.360000] Bluetooth: Core ver 2.11
[   22.360000] NET: Registered protocol family 31
[   22.360000] Bluetooth: HCI device and connection manager initialized
[   22.360000] Bluetooth: HCI socket layer initialized
[   22.376000] Bluetooth: L2CAP ver 2.8
[   22.376000] Bluetooth: L2CAP socket layer initialized
[   22.464000] Bluetooth: RFCOMM socket layer initialized
[   22.464000] Bluetooth: RFCOMM TTY layer initialized
[   22.464000] Bluetooth: RFCOMM ver 1.8
[   44.352000] UDF-fs: No VRS found
[   44.384000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.428000] ISOFS: changing to secondary root
[   57.588000] NET: Registered protocol family 17
[   60.792000] ieee80211_crypt: registered algorithm 'TKIP'
[   69.124000] NET: Registered protocol family 10
[   69.124000] lo: Disabled Privacy Extensions
[   69.124000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.684000] eth1: no IPv6 routers present
[  133.828000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=203.144.160.11 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=52 ID=10217 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=203.144.160.11 LEN=93 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=6881 DPT=16881 LEN=73 ] 
[  133.860000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=190.22.64.201 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=238 ID=50527 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=190.22.64.201 LEN=93 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=6881 DPT=17529 LEN=73 ] 
[  133.920000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=90.22.73.138 DST=192.168.0.4 LEN=56 TOS=0x00 PREC=0x00 TTL=115 ID=9845 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=90.22.73.138 LEN=93 TOS=0x00 PREC=0x00 TTL=51 ID=0 DF PROTO=UDP SPT=6881 DPT=6456 LEN=73 ] 
[  133.920000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=201.216.64.2 DST=192.168.0.4 LEN=56 TOS=0x00 PREC=0x00 TTL=237 ID=25476 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.0.4 DST=201.216.70.74 LEN=93 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=6881 DPT=61916 LEN=73 ] 
[  133.968000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=86.135.132.204 DST=192.168.0.4 LEN=1458 TOS=0x00 PREC=0x00 TTL=111 ID=1122 DF PROTO=TCP SPT=20273 DPT=49963 WINDOW=64466 RES=0x00 ACK URGP=0 
[  134.028000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.80.67.130 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=244 ID=33510 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=212.80.67.130 LEN=93 TOS=0x00 PREC=0x00 TTL=51 ID=0 DF PROTO=UDP SPT=6881 DPT=13844 LEN=73 ] 
[  134.264000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=83.237.197.30 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x20 TTL=115 ID=11636 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=83.237.197.30 LEN=93 TOS=0x00 PREC=0x20 TTL=49 ID=0 DF PROTO=UDP SPT=6881 DPT=29353 LEN=73 ] 
[  134.812000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.72.211.34 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=53 ID=7632 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=212.72.211.34 LEN=93 TOS=0x14 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=6881 DPT=9090 LEN=73 ] 
[  134.812000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.199.24.225 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0xC0 TTL=54 ID=2680 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=212.199.24.225 LEN=93 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=UDP SPT=6881 DPT=2048 LEN=73 ] 
[  134.828000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=89.152.209.144 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=49 ID=20463 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=89.152.209.144 LEN=93 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=6881 DPT=60000 LEN=73 ] 
[  135.088000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=86.129.180.24 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=111 ID=2899 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=86.129.180.24 LEN=93 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=6881 DPT=2165 LEN=73 ] 
[  135.252000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=78.50.13.11 DST=192.168.0.4 LEN=56 TOS=0x00 PREC=0x00 TTL=53 ID=10519 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.0.4 DST=78.50.13.11 LEN=93 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=UDP SPT=6881 DPT=65533 LEN=73 ] 
[  135.600000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=62.233.181.26 DST=192.168.0.4 LEN=121 TOS=0x00 PREC=0x00 TTL=51 ID=3976 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.0.4 DST=81.219.74.242 LEN=93 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=6881 DPT=21500 LEN=73 ] 
[  172.556000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=85.98.20.41 DST=192.168.0.4 LEN=95 TOS=0x00 PREC=0x00 TTL=112 ID=1333 PROTO=UDP SPT=15874 DPT=6881 LEN=75 
[  189.052000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=80.220.72.195 DST=192.168.0.4 LEN=95 TOS=0x00 PREC=0x00 TTL=112 ID=35164 PROTO=UDP SPT=19355 DPT=6881 LEN=75 
miqian@miqian-laptop:~$

---

### Post by Falc7 on 2007-11-08
I noticed something strange today, i left my computer on ubuntu on, for maybe 2 hours with Deluge downloading, but when i came back, the screen was completely blank, but still illuminated, with the computer and the fan constantly running, Nothing i did could bring the screen back. i had to hold down the off button to turn it off. Once i turned it back on it was fine


2nd command

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=89092ec3-7038-4fea-9500-eccd668bf647 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=89092ec3-7038-4fea-9500-eccd668bf647 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=89092ec3-7038-4fea-9500-eccd668bf647 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Falc7 on 2007-11-09
Any ideas? It happened again

---

### Post by Falc7 on 2007-11-10
I've done some more testing, it seems to only happen in ubuntu, i've dual boot vista and although that has some other problems the comp not turning itself off itsen't one of them. 
Could it be something to do with the computer itself?

---

### Post by anewguy on 2007-11-11
How old is your computer?  I ask because I am using an old Dell XPS that has a old PIII at 500mhz, and an old BIOS.  When Ubuntu boots, I get a message saying I have to force acpi.  I've never made that change to boot line, so my PC will not actually turn the power off - it spins down the drive, etc., just I have to physically power it off.

Your 2nd piece of the puzzle sounds like you are having trouble waking your computer up when it suspends.  I have seen several posts on that on this board so you may want to search for those.

Sorry I'm giving precise instructions of any sort - I'm hoping someone else with more knowledge will maybe recognize something in what I've mentioned and help you along.:)

---

### Post by Falc7 on 2007-11-11
Its quite new, maybe a month, but it is manufacter refurbished.

If i force the computer into turning off, once the screen goes black at the end, would that be bad for the computer?

---

### Post by strutzz on 2007-11-11
i have the same problem with a via kt 333 moterboard for some time( 1 month) and the moment it turns black i shut it off and it's ok

---

### Post by Falc7 on 2007-11-11
I see, i guess i will have to do the same, i just hope doing that won't cause any lasting damage

---

### Post by scratched on 2007-11-11
I've been having the same problem. I went and tried investigating a little further on it myself.

I tried shutting the computer down from the terminal on Ctrl + Alt + F1 and I saw that it shuts everything down, then it says "switching to single user mode" or something like that, and it gives me a terminal prompt again. At this point if I try shutting down, it goes through the same routine of saying it is shutting everything down, sending the term signal and sending the kill signal, and then it switches to single user mode again.

I haven't actually figured out why this happens, but I'd like to be able to turn off my computer like a normal person. Windows does not have this problem, and older versions of Ubuntu don't have this problem. I've only had this problem in Gutsy (both live and installed) and it seems to be inconsistent (sometimes I can shut down).

---

### Post by ukripper on 2007-11-13
I think this will solve your problems -
In terminal type -
```
sudo gedit /etc/modules
```

Enter your  password

Scroll down to bottom of file and then copy paste this ```
apm power_off=1
```
 
Save and reboot and then try to shutdown

---

### Post by philinux on 2007-11-13
I had an old motherboard and had same thing. I added acpi=force to the end of the kernel boot up line. This sorted it out for me. Then I found a bios update which really sorted it and now I dont need the acpi=force. Which incidentally got removed when there was a kernel update.

---

### Post by ukripper on 2007-11-13
> **philinux said:**
> I had an old motherboard and had same thing. I added acpi=force to the end of the kernel boot up line. This sorted it out for me. Then I found a bios update which really sorted it and now I dont need the acpi=force. Which incidentally got removed when there was a kernel update.

i guess that is another method to sort the same problem by adding acpi=force in menu.list

---

### Post by Falc7 on 2007-11-13
thanks very much, i think this will have fixed it

this is what that file looks like now

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
apm power_off=1

---

### Post by ukripper on 2007-11-13
> **Falc7 said:**
> thanks very much, i think this will have fixed it

this is what that file looks like now

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
apm power_off=1

Great. so is it working now?

---

### Post by Falc7 on 2007-11-13
too soon to tell, before i had that problem maybe once a day, and since i've done as you've said no problems so far, which is why i am happy. so i will let you know to soon.

---

### Post by urmston on 2007-11-13
I have the same problem, but on a Dell laptop.  The best solution I've found is to disable networking by right-clicking on the network icon on the top panel.  Wait about ten to fifteen seconds and the computer will shut down fine.

---

