---
title: "Sound problem"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by kaski on 2008-03-27
Hi!

This is my last hope. I cant get my sound card working. I have tried everything! I have googled lots of tutorials and threads, non of them helped me. I now installed Ubuntu 7.10 again. I have now downloaded ALSA driver, lib and util and compiled them. 

I just got my new laptop, HP Pavilion TX2020eo. ALSAMixer says my chip Realtek ALC861-VD. I have dual boot with Windows Vista, audio is working there fine. I have "sound control buttons" (volume down, mute, volume up) above my keyboard. The 'mute' button is orange all the time, which means that mute is on. I can't get it off by pressing. I ran alsamixer and unmuted all, still nothing. I opened volume control, there is nothing muted. The mute button goes to orange, when ubuntu starts loading. 

aplay -l
[HTML]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/HTML]

dmesg
[HTML]00000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.388000] ACPI: Core revision 20070126
[    0.388000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.392000] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.392000] SMP alternatives: switching to SMP code
[    0.392000] Booting processor 1/1 eip 3000
[    0.400000] Initializing CPU#1
[    0.480000] Calibrating delay using timer specific routine.. 3989.28 BogoMIPS (lpj=7978573)
[    0.480000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.480000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.480000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.480000] CPU 1(2) -> Core 1
[    0.480000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.480000] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.480000] Total of 2 processors activated (7981.94 BogoMIPS).
[    0.480000] ENABLING IO-APIC IRQs
[    0.480000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.524000] Brought up 2 CPUs
[    0.548000] migration_cost=4000
[    0.548000] Booting paravirtualized kernel on bare hardware
[    0.548000] Time: 21:14:51  Date: 02/27/108
[    0.548000] NET: Registered protocol family 16
[    0.548000] EISA bus registered
[    0.548000] ACPI: bus type pci registered
[    0.564000] PCI: BIOS BUG #81[49435000] found
[    0.564000] PCI: Using configuration type 1
[    0.564000] Setting up standard PCI resources
[    0.564000] ACPI: EC: Look up EC in DSDT
[    0.592000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.592000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.592000] ACPI: Please test with "acpi_osi=!Linux"
[    0.592000] Please send dmidecode to linux-acpi@vger.kernel.org
[    0.600000] ACPI: Interpreter enabled
[    0.600000] ACPI: (supports S0 S3 S4 S5)
[    0.600000] ACPI: Using IOAPIC for interrupt routing
[    0.668000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.668000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.668000] PCI: Probing PCI hardware (bus 00)
[    0.672000] PCI: Transparent bridge - 0000:00:10.0
[    0.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.704000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *10 11 14 15)
[    0.704000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LK1E] (IRQs 19) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *10
[    0.708000] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 20 22 23) *10
[    0.708000] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 20 22 23) *11
[    0.708000] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 20 22 23) *11
[    0.708000] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 20 22 23) *7
[    0.708000] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 20 22 23) *11
[    0.708000] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 20 22 23) *0, disabled.
[    0.708000] ACPI: PCI Interrupt Link [LTID] (IRQs 21) *5
[    0.708000] ACPI: PCI Interrupt Link [LSI1] (IRQs 21) *0
[    0.708000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.708000] pnp: PnP ACPI init
[    0.708000] ACPI: bus type pnp registered
[    0.740000] pnp: PnP ACPI: found 13 devices
[    0.740000] ACPI: ACPI bus type pnp unregistered
[    0.740000] PnPBIOS: Disabled by ACPI PNP
[    0.740000] PCI: Using ACPI for IRQ routing
[    0.740000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.740000] NET: Registered protocol family 8
[    0.740000] NET: Registered protocol family 20
[    0.740000] pnp: 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.740000] pnp: 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.740000] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.740000] pnp: 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.740000] pnp: 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.740000] pnp: 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.740000] pnp: 00:04: ioport range 0x1000-0x107f has been reserved
[    0.740000] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.740000] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[    0.740000] pnp: 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.740000] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[    0.740000] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.740000] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[    0.744000] Time: hpet clocksource has been installed.
[    0.772000] PCI: Bridge: 0000:00:02.0
[    0.772000]   IO window: 4000-4fff
[    0.772000]   MEM window: c4000000-c7ffffff
[    0.772000]   PREFETCH window: c9000000-c91fffff
[    0.772000] PCI: Bridge: 0000:00:03.0
[    0.772000]   IO window: disabled.
[    0.772000]   MEM window: c8000000-c8ffffff
[    0.772000]   PREFETCH window: c9200000-c93fffff
[    0.772000] PCI: Bridge: 0000:00:10.0
[    0.772000]   IO window: disabled.
[    0.772000]   MEM window: disabled.
[    0.772000]   PREFETCH window: disabled.
[    0.772000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.772000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.772000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.772000] NET: Registered protocol family 2
[    0.820000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.820000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.820000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.820000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.820000] TCP reno registered
[    0.836000] checking if image is initramfs... it is
[    1.408000] Freeing initrd memory: 7124k freed
[    1.408000] Simple Boot Flag at 0x36 set to 0x1
[    1.408000] audit: initializing netlink socket (disabled)
[    1.408000] audit(1206652491.244:1): initialized
[    1.408000] highmem bounce pool size: 64 pages
[    1.408000] VFS: Disk quotas dquot_6.5.1
[    1.408000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.408000] io scheduler noop registered
[    1.408000] io scheduler anticipatory registered
[    1.408000] io scheduler deadline registered
[    1.408000] io scheduler cfq registered (default)
[    1.408000] Boot video device is 0000:00:05.0
[    1.412000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.412000] assign_interrupt_mode Found MSI capability
[    1.412000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.412000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.412000] assign_interrupt_mode Found MSI capability
[    1.412000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.412000] isapnp: Scanning for PnP cards...
[    1.764000] isapnp: No Plug & Play device found
[    1.788000] Real Time Clock Driver v1.12ac
[    1.788000] hpet_resources: 0xfed00000 is busy
[    1.788000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.788000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.788000] input: Macintosh mouse button emulation as /class/input/input0
[    1.788000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.804000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.804000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.804000] mice: PS/2 mouse device common for all mice
[    1.804000] EISA: Probing bus 0 at eisa.0
[    1.804000] Cannot allocate resource for EISA slot 1
[    1.804000] Cannot allocate resource for EISA slot 2
[    1.804000] Cannot allocate resource for EISA slot 3
[    1.804000] Cannot allocate resource for EISA slot 4
[    1.804000] EISA: Detected 0 cards.
[    1.804000] TCP cubic registered
[    1.804000] NET: Registered protocol family 1
[    1.804000] Using IPI No-Shortcut mode
[    1.804000]   Magic number: 0:407:248
[    1.804000]   hash matches device ttyw4
[    1.804000] Freeing unused kernel memory: 364k freed
[    1.824000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.020000] AppArmor: AppArmor initialized<5>audit(1206652492.744:2):  type=1505 info="AppArmor initialized" pid=1271
[    3.028000] fuse init (API version 7.8)
[    3.032000] Failure registering capabilities with primary security module.
[    3.060000] ACPI: Thermal Zone [THRM] (57 C)
[    3.648000] usbcore: registered new interface driver usbfs
[    3.648000] usbcore: registered new interface driver hub
[    3.648000] usbcore: registered new device driver usb
[    3.648000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.648000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[    3.648000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[    3.648000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    3.648000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.648000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.648000] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xc0004000
[    3.660000] SCSI subsystem initialized
[    3.664000] libata version 2.21 loaded.
[    3.700000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.700000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.704000] usb usb1: configuration #1 chosen from 1 choice
[    3.704000] hub 1-0:1.0: USB hub found
[    3.704000] hub 1-0:1.0: 8 ports detected
[    3.744000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.808000] sata_nv 0000:00:0e.0: version 3.4
[    3.808000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    3.808000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 21 (level, high) -> IRQ 17
[    3.808000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    3.808000] scsi0 : sata_nv
[    3.808000] scsi1 : sata_nv
[    3.808000] ata1: SATA max UDMA/133 cmd 0x000130b0 ctl 0x000130a6 bmdma 0x00013090 irq 17
[    3.808000] ata2: SATA max UDMA/133 cmd 0x000130a8 ctl 0x000130a2 bmdma 0x00013098 irq 17
[    4.112000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    4.276000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.284000] ata1.00: ATA-7: ST9160821AS, 3.BHE, max UDMA/100
[    4.284000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    4.300000] ata1.00: configured for UDMA/100
[    4.324000] usb 1-2: configuration #1 chosen from 1 choice
[    4.328000] hub 1-2:1.0: USB hub found
[    4.332000] hub 1-2:1.0: 4 ports detected
[    4.612000] ata2: SATA link down (SStatus 0 SControl 300)
[    4.616000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[    4.616000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    4.616000] NFORCE-MCP51: chipset revision 241
[    4.616000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    4.616000] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[    4.616000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    4.616000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[    4.616000] Probing IDE interface ide0...
[    4.752000] usb 1-7: new full speed USB device using ohci_hcd and address 3
[    4.984000] usb 1-7: configuration #1 chosen from 1 choice
[    5.296000] usb 1-8: new low speed USB device using ohci_hcd and address 4
[    5.372000] hda: Slimtype DVD A DS8A1H, ATAPI CD/DVD-ROM drive
[    5.504000] usb 1-8: configuration #1 chosen from 1 choice
[    5.728000] usb 1-2.1: new full speed USB device using ohci_hcd and address 5
[    5.852000] usb 1-2.1: configuration #1 chosen from 1 choice
[    6.060000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.080000] usb 1-2.2: new full speed USB device using ohci_hcd and address 6
[    6.088000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    6.088000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 18
[    6.088000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    6.088000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.088000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    6.088000] ehci_hcd 0000:00:0b.1: debug port 1
[    6.088000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    6.088000] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xc0005000
[    6.156000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.156000] usb usb2: configuration #1 chosen from 1 choice
[    6.156000] hub 2-0:1.0: USB hub found
[    6.156000] hub 2-0:1.0: 8 ports detected
[    6.260000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    6.260000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, high) -> IRQ 19
[    6.260000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    6.260000] forcedeth: using HIGHDMA
[    6.564000] usb 1-2.2: device not accepting address 6, error -62
[    6.564000] hub 1-2:1.0: cannot disable port 2 (err = -62)
[    6.568000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.568000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.572000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.576000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.580000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.580000] hub 1-2:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[    6.580000] hub 1-2:1.0: cannot disable port 2 (err = -62)
[    6.584000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.588000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.592000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.592000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.596000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.596000] hub 1-2:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[    6.600000] hub 1-2:1.0: cannot disable port 2 (err = -62)
[    6.604000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.604000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.608000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.612000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.616000] hub 1-2:1.0: cannot reset port 2 (err = -62)
[    6.616000] hub 1-2:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[    6.616000] hub 1-2:1.0: cannot disable port 2 (err = -62)
[    6.620000] hub 1-2:1.0: cannot disable port 2 (err = -62)
[    6.624000] hub 1-2:1.0: hub_port_status failed (err = -62)
[    6.628000] hub 1-2:1.0: hub_port_status failed (err = -62)
[    6.628000] hub 1-2:1.0: hub_port_status failed (err = -62)
[    6.628000] usb 1-2: USB disconnect, address 2
[    6.628000] usb 1-2.1: USB disconnect, address 5
[    6.772000] usb 1-7: USB disconnect, address 3
[    6.780000] eth0: forcedeth.c: subsystem: 0103c:30e5 bound to 0000:00:14.0
[    6.788000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.788000] sd 0:0:0:0: [sda] Write Protect is off
[    6.788000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.788000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.788000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.788000] sd 0:0:0:0: [sda] Write Protect is off
[    6.788000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.788000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.788000]  sda:<6>hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[    6.792000] Uniform CD-ROM driver Revision: 3.20
[    6.812000]  sda1 sda2 sda3
[    6.840000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.844000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.908000] usb 1-8: USB disconnect, address 4
[    7.224000] Attempting manual resume
[    7.224000] swsusp: Resume From Partition 8:3
[    7.224000] PM: Checking swsusp image.
[    7.224000] PM: Resume from disk failed.
[    7.256000] kjournald starting.  Commit interval 5 seconds
[    7.256000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.288000] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    7.424000] usb 2-2: configuration #1 chosen from 1 choice
[    7.424000] hub 2-2:1.0: USB hub found
[    7.424000] hub 2-2:1.0: 4 ports detected
[    7.964000] usbcore: registered new interface driver hiddev
[    8.288000] usb 1-7: new full speed USB device using ohci_hcd and address 10
[    8.508000] usb 1-7: configuration #1 chosen from 1 choice
[    8.820000] usb 1-8: new low speed USB device using ohci_hcd and address 11
[    9.028000] usb 1-8: configuration #1 chosen from 1 choice
[    9.248000] usb 2-2.1: new high speed USB device using ehci_hcd and address 5
[    9.352000] usb 2-2.1: configuration #1 chosen from 1 choice
[    9.564000] usb 2-2.2: new full speed USB device using ehci_hcd and address 6
[    9.660000] usb 2-2.2: configuration #1 chosen from 1 choice
[    9.868000] usb 2-2.3: new full speed USB device using ehci_hcd and address 7
[    9.968000] usb 2-2.3: configuration #1 chosen from 1 choice
[    9.976000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    9.976000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-8
[    9.976000] usbcore: registered new interface driver usbhid
[    9.976000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.816000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.820000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.304000] Bluetooth: Core ver 2.11
[   17.304000] NET: Registered protocol family 31
[   17.304000] Bluetooth: HCI device and connection manager initialized
[   17.304000] Bluetooth: HCI socket layer initialized
[   17.316000] input: PC Speaker as /class/input/input3
[   17.476000] Bluetooth: HCI USB driver ver 2.9
[   17.480000] usbcore: registered new interface driver hci_usb
[   17.488000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   17.488000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   17.532000] Linux video capture interface: v2.00
[   17.572000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.628000] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   17.632000] usbcore: registered new interface driver uvcvideo
[   17.632000] USB Video Class driver (v0.1.0)
[   17.648000] usbcore: registered new interface driver xpad
[   17.648000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   17.768000] nvidia: module license 'NVIDIA' taints kernel.
[   18.020000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   18.020000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 18 (level, high) -> IRQ 20
[   18.020000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.020000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   18.096000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   18.152000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   18.484000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   18.484000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 17 (level, high) -> IRQ 21
[   18.484000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   18.516000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:698: codec_mask = 0x3
[   18.836000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   18.916000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:2339: autoconfig: line_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   18.916000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:2343:    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   18.916000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:2347:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.916000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:2355:    inputs: mic=0x19, fmic=0x18, line=0x0, fline=0x0, cd=0x0, aux=0x0
[   19.616000] lp: driver loaded but no devices found
[   19.672000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   20.148000] EXT3 FS on sda2, internal journal
[   21.888000] input: Power Button (FF) as /class/input/input5
[   21.888000] ACPI: Power Button (FF) [PWRF]
[   21.888000] input: Power Button (CM) as /class/input/input6
[   21.888000] ACPI: Power Button (CM) [PWRB]
[   21.888000] input: Sleep Button (CM) as /class/input/input7
[   21.888000] ACPI: Sleep Button (CM) [SLPB]
[   21.888000] input: Lid Switch as /class/input/input8
[   21.888000] ACPI: Lid Switch [LID]
[   22.044000] ACPI: AC Adapter [ACAD] (on-line)
[   22.056000] No dock devices found.
[   22.068000] ACPI: \_SB_.PCI0.IDE0.PRI0.MAST: found ejectable bay
[   22.068000] ACPI: \_SB_.PCI0.IDE0.PRI0.MAST: Adding notify handler
[   22.068000] ACPI: Bay [\_SB_.PCI0.IDE0.PRI0.MAST] Added
[   22.480000] ACPI: Battery Slot [BAT0] (battery present)
[   22.496000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   22.496000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.724000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (version 2.00.00)
[   22.724000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[   22.724000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   22.724000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   22.724000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   23.812000] ppdev: user-space parallel port driver
[   24.084000] audit(1206645314.284:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5210 profile="/usr/sbin/cupsd"
[   24.136000] apm: BIOS not found.
[   24.580000] Failure registering capabilities with primary security module.
[   24.908000] Bluetooth: L2CAP ver 2.8
[   24.908000] Bluetooth: L2CAP socket layer initialized
[   25.000000] Clocksource tsc unstable (delta = -300018246 ns)
[   25.008000] Bluetooth: RFCOMM socket layer initialized
[   25.008000] Bluetooth: RFCOMM TTY layer initialized
[   25.008000] Bluetooth: RFCOMM ver 1.8
[   29.532000] NET: Registered protocol family 17
[   34.200000] NET: Registered protocol family 10
[   34.200000] lo: Disabled Privacy Extensions
[   37.384000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[   37.396000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[   37.404000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   37.412000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[   37.868000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   37.876000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[   37.884000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[   45.096000] eth0: no IPv6 routers present
[   76.672000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[   76.684000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[   76.692000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   76.700000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[   84.556000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   84.568000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[   84.576000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  127.580000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[  127.588000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[  127.596000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[  127.608000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[  127.620000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  127.632000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[  127.644000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  128.300000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[  128.308000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[  128.316000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[  128.324000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[  191.388000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  191.400000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[  191.408000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  559.896000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[  559.896000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[  579.144000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[  579.144000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[/HTML]


PS. I'm new on ubuntu. And sorry for my bad English.
EDIT:

More info

lsmod
[HTML]Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
sbs                    19592  0 
video                  18060  0 
battery                11012  0 
container               5504  0 
bay                     6912  0 
dock                   10656  1 bay
ac                      6148  0 
button                  8976  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         284952  2 
snd_pcm_oss            53632  0 
snd_mixer_oss          18304  2 snd_pcm_oss
snd_pcm                88836  2 snd_hda_intel,snd_pcm_oss
joydev                 11328  0 
snd_page_alloc         11528  2 snd_hda_intel,snd_pcm
snd_seq_oss            35712  0 
snd_seq_midi_event      8576  1 snd_seq_oss
nvidia               4716468  22 
snd_seq                58608  4 snd_seq_oss,snd_seq_midi_event
snd_timer              26116  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
xpad                    9988  0 
uvcvideo               48644  0 
agpgart                35016  1 nvidia
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
k8temp                  6656  0 
i2c_nforce2             7040  0 
hci_usb                18332  2 
snd                    64012  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_oss,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
serio_raw               8068  0 
psmouse                39952  0 
soundcore               8800  2 snd
i2c_core               26112  2 nvidia,i2c_nforce2
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sd_mod                 30336  4 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
forcedeth              51592  0 
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
ehci_hcd               36492  0 
sata_nv                20612  3 
libata                125168  2 ata_generic,sata_nv
scsi_mod              147084  3 sg,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  7 xpad,uvcvideo,hci_usb,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
[/HTML]

sudo lspci -v
[HTML]00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 00000000c9000000-00000000c91fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: c8000000-c8ffffff
        Prefetchable memory behind bridge: 00000000c9200000-00000000c93fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at c0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 30b0 [size=8]
        I/O ports at 30a4 [size=4]
        I/O ports at 30a8 [size=8]
        I/O ports at 30a0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30e5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30b8 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 1367
        Flags: bus master, fast devsel, latency 0, IRQ 255
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Memory at c9200000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0
[/HTML]

cat /proc/asound/version
[HTML]Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Mar 27 2008 for kernel 2.6.22-14-generic (SMP).[/HTML]

---

### Post by (((X))) on 2008-03-27
Too many modules are loaded, they may conflict.

---

### Post by amba on 2008-06-16
i just bought a tablet pc, HP TX2130EL, it's wonderfull!
Have installed Kubuntu, but got same audio problem as kaski.
Same audio chipset ofc...

No one knows about?

---

### Post by amba on 2008-06-16
WHOA!
Just fixed it!
Found this link in google cache, the real link is broken atm :D
[http://74.125.39.104/search?q=cache:U7b8TRRBjVUJ:pcworldonline.altervista.org/index.php/fedora/54-fedora/107-risolto-problema-audio-asus-x50n-n5n-scheda-realtek-alc861vd%3Ftmpl%3Dcomponent%26print%3D1%26page%3D+ALC861-VD&hl=it&ct=clnk&cd=5&gl=it](http://74.125.39.104/search?q=cache:U7b8TRRBjVUJ:pcworldonline.altervista.org/index.php/fedora/54-fedora/107-risolto-problema-audio-asus-x50n-n5n-scheda-realtek-alc861vd%3Ftmpl%3Dcomponent%26print%3D1%26page%3D+ALC861-VD&hl=it&ct=clnk&cd=5&gl=it)

It says to just add this line 
options snd-hda-intel model=lenovo

into
/etc/modprobe.d/alsa-base

Then restart :)

Google Cache I Love You! ;)

---

### Post by jamestwo on 2008-06-19
I have one Lenovo N200 laptop whit Kubuntu hardy heron and i have passed the same problem.First i download and installed the:
parport-module-generic

and after i have edit the file alsa-base.txt in /etc/modprobe.d/

whit the line:

options snd-hda-intel model=lenovo

now the sound is ok

Bye

---

