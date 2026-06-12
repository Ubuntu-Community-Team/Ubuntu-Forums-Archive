---
title: "NO Sound Capture Aspire 5601 Ubuntu 7.04"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by gymmeh on 2007-09-20
I have the sound output working fine with ubuntu 7.04 but my sound input is not working
I downloaded Skype and Ventrillo, and I have used both of their advice forums to get the mic to work, I ended up making things worse and just re formating ubuntu.

What Info do you need from me, that can help?

my codec info from 
[PHP]$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: Generic 11c1 Si3054
[/PHP]

I have seen people post the dmesg

[PHP][    0.153117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.153397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.153628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.153903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.154568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.155188] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.155455] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.155719] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.156008] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.156271] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.156530] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.156793] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.157056] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.179505] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.179519] pnp: PnP ACPI init
[    0.182448] pnp: PnP ACPI: found 9 devices
[    0.182452] PnPBIOS: Disabled by ACPI PNP
[    0.182495] PCI: Using ACPI for IRQ routing
[    0.182498] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.182502] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    0.182505] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    0.182507] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[    0.182510] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    0.182512] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    0.182515] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    0.182517] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    0.182520] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    0.182522] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[    0.182525] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[    0.182527] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[    0.182530] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3
[    0.218390] NET: Registered protocol family 8
[    0.218393] NET: Registered protocol family 20
[    0.218993] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.219011] PCI: Bridge: 0000:00:1c.0
[    0.219013]   IO window: disabled.
[    0.219019]   MEM window: 34000000-340fffff
[    0.219024]   PREFETCH window: disabled.
[    0.219030] PCI: Bridge: 0000:00:1c.1
[    0.219032]   IO window: disabled.
[    0.219038]   MEM window: disabled.
[    0.219042]   PREFETCH window: disabled.
[    0.219048] PCI: Bridge: 0000:00:1c.2
[    0.219050]   IO window: disabled.
[    0.219056]   MEM window: disabled.
[    0.219060]   PREFETCH window: disabled.
[    0.219066] PCI: Bridge: 0000:00:1c.3
[    0.219067]   IO window: disabled.
[    0.219073]   MEM window: disabled.
[    0.219078]   PREFETCH window: disabled.
[    0.219087] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[    0.219089]   IO window: 00002400-000024ff
[    0.219095]   IO window: 00002800-000028ff
[    0.219100]   PREFETCH window: 30000000-33ffffff
[    0.219106]   MEM window: 38000000-3bffffff
[    0.219112] PCI: Bridge: 0000:00:1e.0
[    0.219115]   IO window: 2000-2fff
[    0.219121]   MEM window: b0300000-b03fffff
[    0.219126]   PREFETCH window: 30000000-33ffffff
[    0.219154] PCI: Enabling device 0000:00:1c.0 (0000 -> 0002)
[    0.219162] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.219170] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.219195] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.219203] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.219227] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.219235] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.219260] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    0.219268] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.219282] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.219301] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[    0.219334] NET: Registered protocol family 2
[    0.271627] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.271708] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.271808] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.271860] TCP: Hash tables configured (established 16384 bind 8192)
[    0.271863] TCP reno registered
[    0.287669] checking if image is initramfs... it is
[    0.974775] Freeing initrd memory: 6782k freed
[    0.974982] Simple Boot Flag at 0x3e set to 0x1
[    0.975488] audit: initializing netlink socket (disabled)
[    0.975508] audit(1190323570.764:1): initialized
[    0.975694] VFS: Disk quotas dquot_6.5.1
[    0.975716] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.975770] io scheduler noop registered
[    0.975773] io scheduler anticipatory registered
[    0.975776] io scheduler deadline registered
[    0.975789] io scheduler cfq registered (default)
[    0.976060] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.976120] assign_interrupt_mode Found MSI capability
[    0.976123] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.976161] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.976291] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.976350] assign_interrupt_mode Found MSI capability
[    0.976353] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.976388] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.976512] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.976570] assign_interrupt_mode Found MSI capability
[    0.976573] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.976607] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.976733] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.976792] assign_interrupt_mode Found MSI capability
[    0.976795] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.976830] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.977022] isapnp: Scanning for PnP cards...
[    1.330537] isapnp: No Plug & Play device found
[    1.355128] Real Time Clock Driver v1.12ac
[    1.355188] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.355850] mice: PS/2 mouse device common for all mice
[    1.356437] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.356684] input: Macintosh mouse button emulation as /class/input/input0
[    1.356722] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.356726] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.356974] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.361391] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.362346] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.362350] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.362352] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.362355] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.362358] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.362483] EISA: Probing bus 0 at eisa.0
[    1.362492] Cannot allocate resource for EISA slot 1
[    1.362496] Cannot allocate resource for EISA slot 2
[    1.362524] EISA: Detected 0 cards.
[    1.392585] TCP cubic registered
[    1.392595] NET: Registered protocol family 1
[    1.392620] Starting balanced_irq
[    1.392626] Using IPI No-Shortcut mode
[    1.392732] ACPI: (supports S0 S3 S4 S5)
[    1.392785]   Magic number: 7:125:450
[    1.393109] Freeing unused kernel memory: 328k freed
[    1.393873] Time: tsc clocksource has been installed.
[    1.394553] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.607099] Capability LSM initialized
[    2.641247] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.641480] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.641728] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.641734] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.642260] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.642475] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.642783] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.642788] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.646499] ACPI: Thermal Zone [THRM] (32 C)
[    3.260000] Time: hpet clocksource has been installed.
[    3.604000] usbcore: registered new interface driver usbfs
[    3.604000] usbcore: registered new interface driver hub
[    3.604000] usbcore: registered new device driver usb
[    3.608000] USB Universal Host Controller Interface driver v3.0
[    3.608000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    3.608000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.608000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.608000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.608000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001820
[    3.608000] usb usb1: configuration #1 chosen from 1 choice
[    3.608000] hub 1-0:1.0: USB hub found
[    3.608000] hub 1-0:1.0: 2 ports detected
[    3.620000] SCSI subsystem initialized
[    3.624000] libata version 2.20 loaded.
[    3.628000] 8139too Fast Ethernet driver 0.9.28
[    3.712000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.712000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.712000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.712000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.712000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.712000] usb usb2: configuration #1 chosen from 1 choice
[    3.712000] hub 2-0:1.0: USB hub found
[    3.712000] hub 2-0:1.0: 2 ports detected
[    3.816000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.816000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.816000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.816000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.816000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.816000] usb usb3: configuration #1 chosen from 1 choice
[    3.816000] hub 3-0:1.0: USB hub found
[    3.816000] hub 3-0:1.0: 2 ports detected
[    3.920000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    3.920000] eth0: RealTek RTL8139 at 0xe0066000, 00:16:36:63:fa:98, IRQ 16
[    3.920000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.920000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.920000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.920000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.920000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.920000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    3.920000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    3.920000] scsi0 : ata_piix
[    4.264000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    4.264000] ata1.00: ATA-6: HTS541010G9AT00, MBZOA60A, max UDMA/100
[    4.264000] ata1.00: 195371568 sectors, multi 16: LBA48 
[    4.264000] ata1.01: ATAPI, max UDMA/33
[    4.264000] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.272000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    4.272000] ata1.00: configured for UDMA/33
[    4.452000] ata1.01: configured for UDMA/33
[    4.452000] scsi1 : ata_piix
[    4.616000] ATA: abnormal status 0x7F on port 0x00010177
[    4.616000] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9AT00  MBZO PQ: 0 ANSI: 5
[    4.624000] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D ac00 PQ: 0 ANSI: 5
[    4.624000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    4.624000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.624000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.624000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.624000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.624000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.624000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xb0004000
[    4.628000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.628000] usb usb4: configuration #1 chosen from 1 choice
[    4.628000] hub 4-0:1.0: USB hub found
[    4.628000] hub 4-0:1.0: 8 ports detected
[    4.732000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.732000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.732000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.732000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.732000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.732000] usb usb5: configuration #1 chosen from 1 choice
[    4.732000] hub 5-0:1.0: USB hub found
[    4.732000] hub 5-0:1.0: 2 ports detected
[    4.872000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.872000] sda: Write Protect is off
[    4.872000] sda: Mode Sense: 00 3a 00 00
[    4.872000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.872000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.876000] sda: Write Protect is off
[    4.876000] sda: Mode Sense: 00 3a 00 00
[    4.876000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.876000]  sda: sda1 sda2 < sda5 >
[    4.912000] sd 0:0:0:0: Attached scsi disk sda
[    4.916000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.916000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    5.004000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.004000] Uniform CD-ROM driver Revision: 3.20
[    5.004000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.156000] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    5.332000] usb 5-2: configuration #1 chosen from 1 choice
[    5.344000] usbcore: registered new interface driver hiddev
[    5.356000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    5.356000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-2
[    5.356000] usbcore: registered new interface driver usbhid
[    5.356000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.428000] Attempting manual resume
[    5.428000] swsusp: Resume From Partition 8:5
[    5.428000] PM: Checking swsusp image.
[    5.428000] PM: Resume from disk failed.
[    5.472000] kjournald starting.  Commit interval 5 seconds
[    5.476000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.204000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   17.184000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.184000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.188000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.192000] agpgart: Detected an Intel 945GM Chipset.
[   17.192000] agpgart: Detected 7932K stolen memory.
[   17.208000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.500000] iTCO_vendor_support: vendor-support=0
[   17.532000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.644000] ieee80211_crypt: registered algorithm 'NULL'
[   17.656000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.656000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.684000] NET: Registered protocol family 17
[   17.700000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0102]
[   17.700000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.700000] Yenta: Routing CardBus interrupts to PCI
[   17.700000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.760000] sdhci: Secure Digital Host Controller Interface driver
[   17.760000] sdhci: Copyright(c) Pierre Ossman
[   17.832000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.832000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.932000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[   17.932000] Socket status: 30000006
[   17.932000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   17.932000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.932000] cs: IO port probe 0x2000-0x2fff: clean.
[   17.932000] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xb03fffff
[   17.932000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.940000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 20
[   17.940000] sdhci: SDHCI controller found at 0000:0a:09.3 [104c:803c] (rev 0)
[   17.940000] ACPI: PCI Interrupt 0000:0a:09.3[A] -> GSI 20 (level, low) -> IRQ 20
[   17.940000] mmc0: SDHCI at 0xb0300400 irq 20 DMA
[   17.940000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   17.940000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.940000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.952000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   18.044000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.044000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.096000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   18.144000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.148000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.148000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.176000] intel_rng: FWH not detected
[   18.328000] cs: IO port probe 0x100-0x3af: clean.
[   18.328000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.328000] cs: IO port probe 0x820-0x8ff: clean.
[   18.328000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.332000] cs: IO port probe 0xa00-0xaff: clean.
[   18.692000] fuse init (API version 7.8)
[   18.748000] lp: driver loaded but no devices found
[   18.772000] Adding 1477940k swap on /dev/disk/by-uuid/c1aff684-eb64-48e5-8ffc-9dc3fe892986.  Priority:-1 extents:1 across:1477940k
[   18.952000] EXT3 FS on sda1, internal journal
[   19.840000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   20.488000] NET: Registered protocol family 10
[   20.488000] lo: Disabled Privacy Extensions
[   31.408000] eth0: no IPv6 routers present
[   56.444000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   69.708000] No dock devices found.
[   69.800000] Using specific hotkey driver
[   69.852000] ACPI: Battery Slot [BAT1] (battery present)
[   69.888000] ibm_acpi: ec object not found
[   69.928000] input: Power Button (FF) as /class/input/input4
[   69.928000] ACPI: Power Button (FF) [PWRF]
[   69.928000] input: Lid Switch as /class/input/input5
[   69.928000] ACPI: Lid Switch [LID]
[   69.928000] input: Power Button (CM) as /class/input/input6
[   69.928000] ACPI: Power Button (CM) [PWRB]
[   69.928000] input: Sleep Button (CM) as /class/input/input7
[   69.928000] ACPI: Sleep Button (CM) [SLPB]
[   70.040000] ACPI: AC Adapter [ACAD] (off-line)
[   70.056000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   70.084000] wmi_add device=ddf00800
[   70.084000] calling WQBA
[   70.096000] pcc_acpi: loading...
[   75.844000] [drm] Initialized drm 1.1.0 20060810
[   75.848000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   75.848000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   76.556000] ppdev: user-space parallel port driver
[   77.568000] apm: BIOS not found.
[   78.076000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   78.312000] Netfilter messages via NETLINK v0.30.
[   78.320000] nf_conntrack version 0.5.0 (4020 buckets, 32160 max)
[   79.592000] Bluetooth: Core ver 2.11
[   79.592000] NET: Registered protocol family 31
[   79.592000] Bluetooth: HCI device and connection manager initialized
[   79.592000] Bluetooth: HCI socket layer initialized
[   79.652000] Bluetooth: L2CAP ver 2.8
[   79.652000] Bluetooth: L2CAP socket layer initialized
[   79.760000] Bluetooth: RFCOMM socket layer initialized
[   79.760000] Bluetooth: RFCOMM TTY layer initialized
[   79.760000] Bluetooth: RFCOMM ver 1.8
[   88.208000] eth0: no IPv6 routers present
[  106.376000] Inbound IN=eth0 OUT= MAC=00:16:36:63:fa:98:00:01:5c:22:55:82:08:00 SRC=79.74.175.193 [/PHP]

And also post lspci but they both look the same so I will go with the first one...
I have already added 

[PHP]snd-hda-intel model=ACER
[/PHP]

to the following thinkings 
[PHP]sudo nano /etc/modules
nano /etc/modprobe.d/snd-hda-intel.modprobe
nano /etc/modprobe.d/alsa-base
[/PHP]

Thank you!

---

### Post by linuxwizard on 2007-09-21
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by gymmeh on 2008-02-10
sweet got it working thanks

---

