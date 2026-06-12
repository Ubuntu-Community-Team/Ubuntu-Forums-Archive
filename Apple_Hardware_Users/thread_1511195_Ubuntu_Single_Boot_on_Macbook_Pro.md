---
title: "Ubuntu Single Boot on Macbook Pro"
date: 2010-06-16
forum: Apple Hardware Users
---

### Post by SRama on 2010-06-16
Hi, I've recently wiped by hard drive of mac osx and installed ubuntu. My problem is that i have no proprietary drivers and i cant get internet (wired and wireless) to work. I was wondering if this problem could be due to the fact that i dont have drivers for my ethernet.

I also had a slight problem when installed ubuntu. The install itself when through fine, but after completion, i received a prompt saying that I needed to restart. after clicking ok to restart, i received a string of error, and my cd ejected. when i retstarted after that, ubuntu loaded fine, but no wired or wireless internet for me. 

Can anyone shed light on this? I've reinstalled a few times and i have the same problem. Everyone i talk to says its strange that ethernet doesnt work. I'm not sure how to begin to tackle this issue.

Thanks

---

### Post by linuxopjemac on 2010-06-16
My guess is that your Mac Pro uses devices which are not standard. Can you do a dmesg and lspci and paste the output here?

```
dmesg
lspci
```

---

### Post by SRama on 2010-06-16
Heres the output:

[    0.309262] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 21
[    0.309264]   alloc irq_desc for 21 on node -1
[    0.309266]   alloc kstat_irqs on node -1
[    0.309269] pci 0000:00:16.0: PCI INT A -> Link[Z00J] -> GSI 21 (level, low) -> IRQ 21
[    0.309278] pci 0000:00:16.0: setting latency timer to 64
[    0.309284] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.309286] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.309289] pci_bus 0000:01: resource 1 mem: [0xe7300000-0xe73fffff]
[    0.309291] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.309293] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.309295] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.309297] pci_bus 0000:02: resource 1 mem: [0xe2000000-0xe50fffff]
[    0.309299] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.309301] pci_bus 0000:04: resource 1 mem: [0xe7200000-0xe72fffff]
[    0.309303] pci_bus 0000:05: resource 1 mem: [0xe7100000-0xe71fffff]
[    0.309349] NET: Registered protocol family 2
[    0.309459] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.309783] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.310769] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.311217] TCP: Hash tables configured (established 131072 bind 65536)
[    0.311219] TCP reno registered
[    0.311275] NET: Registered protocol family 1
[    0.323779] pci 0000:02:00.0: Boot video device
[    0.323937] cpufreq-nforce2: No nForce2 chipset.
[    0.323958] Scanning for low memory corruption every 60 seconds
[    0.324043] audit: initializing netlink socket (disabled)
[    0.324052] type=2000 audit(1276740855.323:1): initialized
[    0.331291] highmem bounce pool size: 64 pages
[    0.331295] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.332399] VFS: Disk quotas dquot_6.5.2
[    0.332443] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.332865] fuse init (API version 7.13)
[    0.332927] msgmni has been set to 1686
[    0.333085] alg: No test for stdrng (krng)
[    0.333125] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.333127] io scheduler noop registered
[    0.333129] io scheduler anticipatory registered
[    0.333130] io scheduler deadline registered
[    0.333158] io scheduler cfq registered (default)
[    0.333432]   alloc irq_desc for 24 on node -1
[    0.333434]   alloc kstat_irqs on node -1
[    0.333452] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.333472] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.333820]   alloc irq_desc for 25 on node -1
[    0.333821]   alloc kstat_irqs on node -1
[    0.333837] pcieport 0000:00:15.0: irq 25 for MSI/MSI-X
[    0.333856] pcieport 0000:00:15.0: setting latency timer to 64
[    0.334199]   alloc irq_desc for 26 on node -1
[    0.334201]   alloc kstat_irqs on node -1
[    0.334216] pcieport 0000:00:16.0: irq 26 for MSI/MSI-X
[    0.334235] pcieport 0000:00:16.0: setting latency timer to 64
[    0.334385] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.334403] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.334503] ACPI: AC Adapter [ADP1] (off-line)
[    0.334587] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.334633] ACPI: Lid Switch [LID0]
[    0.334669] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.334671] ACPI: Power Button [PWRB]
[    0.334701] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.334702] ACPI: Sleep Button [SLPB]
[    0.334752] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.334754] ACPI: Power Button [PWRF]
[    0.335416] ACPI: SSDT bfec5c18 002BC (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.335780] ACPI: SSDT bfec5918 002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.336116] Monitor-Mwait will be used to enter C-1 state
[    0.336135] Monitor-Mwait will be used to enter C-2 state
[    0.336153] Monitor-Mwait will be used to enter C-3 state
[    0.336159] Marking TSC unstable due to TSC halts in idle
[    0.336191] Switching to clocksource hpet
[    0.336231] processor LNXCPU:00: registered as cooling_device0
[    0.336514] ACPI: SSDT bfec5f18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.336804] ACPI: SSDT bfec4f18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.337251] processor LNXCPU:01: registered as cooling_device1
[    0.343216] isapnp: Scanning for PnP cards...
[    0.348816] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.349883] brd: module loaded
[    0.350292] loop: module loaded
[    0.350345] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.350868] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 20
[    0.350871]   alloc irq_desc for 20 on node -1
[    0.350873]   alloc kstat_irqs on node -1
[    0.350877] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    0.350905] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.350917] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.351174] Fixed MDIO Bus: probed
[    0.351201] PPP generic driver version 2.4.2
[    0.351227] tun: Universal TUN/TAP device driver, 1.6
[    0.351228] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.351283] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.351569] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    0.351572]   alloc irq_desc for 19 on node -1
[    0.351573]   alloc kstat_irqs on node -1
[    0.351576] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.351583] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.351585] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.351608] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.351627] ehci_hcd 0000:00:04.1: debug port 1
[    0.351640] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.351653] ehci_hcd 0000:00:04.1: irq 19, io mem 0xe7489200
[    0.361025] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.361087] usb usb1: configuration #1 chosen from 1 choice
[    0.361110] hub 1-0:1.0: USB hub found
[    0.361116] hub 1-0:1.0: 7 ports detected
[    0.361460] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 18
[    0.361463]   alloc irq_desc for 18 on node -1
[    0.361464]   alloc kstat_irqs on node -1
[    0.361467] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 18 (level, low) -> IRQ 18
[    0.361474] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.361476] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.361498] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.361517] ehci_hcd 0000:00:06.1: debug port 1
[    0.361524] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    0.361535] ehci_hcd 0000:00:06.1: irq 18, io mem 0xe7489100
[    0.373015] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.373068] usb usb2: configuration #1 chosen from 1 choice
[    0.373086] hub 2-0:1.0: USB hub found
[    0.373091] hub 2-0:1.0: 5 ports detected
[    0.373127] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.373413] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    0.373415]   alloc irq_desc for 17 on node -1
[    0.373416]   alloc kstat_irqs on node -1
[    0.373420] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    0.373426] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.373428] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.373451] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.373469] ohci_hcd 0000:00:04.0: irq 17, io mem 0xe7488000
[    0.433365] usb usb3: configuration #1 chosen from 1 choice
[    0.433384] hub 3-0:1.0: USB hub found
[    0.433392] hub 3-0:1.0: 7 ports detected
[    0.433705] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 16
[    0.433707]   alloc irq_desc for 16 on node -1
[    0.433708]   alloc kstat_irqs on node -1
[    0.433712] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 16 (level, low) -> IRQ 16
[    0.433718] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.433721] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.433744] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.433759] ohci_hcd 0000:00:06.0: irq 16, io mem 0xe7487000
[    0.441303] ACPI: Battery Slot [BAT0] (battery present)
[    0.523043] usb usb4: configuration #1 chosen from 1 choice
[    0.523063] hub 4-0:1.0: USB hub found
[    0.523071] hub 4-0:1.0: 5 ports detected
[    0.523106] uhci_hcd: USB Universal Host Controller Interface driver
[    0.523153] PNP: No PS/2 controller found. Probing ports directly.
[    0.524020] i8042.c: No controller found.
[    0.524067] mice: PS/2 mouse device common for all mice
[    0.524172] rtc_cmos 00:07: RTC can wake from S4
[    0.524197] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.524243] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.524310] device-mapper: uevent: version 1.0.3
[    0.524371] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.524412] device-mapper: multipath: version 1.1.0 loaded
[    0.524414] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.524491] EISA: Probing bus 0 at eisa.0
[    0.524497] Cannot allocate resource for EISA slot 2
[    0.524498] Cannot allocate resource for EISA slot 3
[    0.524511] EISA: Detected 0 cards.
[    0.524611] cpuidle: using governor ladder
[    0.524693] cpuidle: using governor menu
[    0.525013] TCP cubic registered
[    0.525122] NET: Registered protocol family 10
[    0.525453] lo: Disabled Privacy Extensions
[    0.525694] NET: Registered protocol family 17
[    0.526188] Using IPI No-Shortcut mode
[    0.526233] PM: Resume from disk failed.
[    0.526240] registered taskstats version 1
[    0.526836]   Magic number: 14:652:207
[    0.526848] acpi device:2f: hash matches
[    0.526923] rtc_cmos 00:07: setting system clock to 2010-06-17 02:14:16 UTC (1276740856)
[    0.526925] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.526927] EDD information not available.
[    0.698708] isapnp: No Plug & Play device found
[    0.698758] Freeing unused kernel memory: 656k freed
[    0.699090] Write protecting the kernel text: 4676k
[    0.699135] Write protecting the kernel read-only data: 1840k
[    0.711159] udev: starting version 151
[    0.749045] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.751357] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.751688] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    0.751693] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    0.751697] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.804482] b43-pci-bridge 0000:04:00.0: power state changed by ACPI to D0
[    0.804648] b43-pci-bridge 0000:04:00.0: PCI INT A -> Link[Z00F] -> GSI 22 (level, low) -> IRQ 22
[    0.804656] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[    0.812922] ohci1394 0000:05:00.0: PCI INT A -> Link[Z00J] -> GSI 21 (level, low) -> IRQ 21
[    0.812927] ohci1394 0000:05:00.0: setting latency timer to 64
[    0.814267] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 64:b9:e8:c8:91:d6
[    0.814270] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    0.814299] ahci 0000:00:0b.0: version 3.0
[    0.814305] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    0.814334]   alloc irq_desc for 27 on node -1
[    0.814335]   alloc kstat_irqs on node -1
[    0.814343] ahci 0000:00:0b.0: irq 27 for MSI/MSI-X
[    0.814390] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    0.814393] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pmp pio slum part boh 
[    0.814396] ahci 0000:00:0b.0: setting latency timer to 64
[    0.814563] scsi0 : ahci
[    0.814644] scsi1 : ahci
[    0.814687] scsi2 : ahci
[    0.814733] scsi3 : ahci
[    0.814780] scsi4 : ahci
[    0.814821] scsi5 : ahci
[    0.814942] ata1: SATA max UDMA/133 abar m8192@0xe7484000 port 0xe7484100 irq 27
[    0.814944] ata2: SATA max UDMA/133 abar m8192@0xe7484000 port 0xe7484180 irq 27
[    0.814946] ata3: DUMMY
[    0.814947] ata4: DUMMY
[    0.814948] ata5: DUMMY
[    0.814949] ata6: DUMMY
[    0.844261] ssb: ERROR: PLL init unknown for device 4322
[    0.844262] ssb: ERROR: PMU resource config unknown for device 4322
[    0.870105] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e7100000-e71007ff]  Max Packet=[4096]  IR/IT contexts=[8/8]
[    0.872393] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[    0.886337] usb 1-4: config 1 has an invalid descriptor of length 0, skipping remainder of the config
[    0.886342] usb 1-4: config 1 has 1 interface, different from the descriptor's value: 3
[    0.886347] usb 1-4: config 1 interface 0 altsetting 0 has 0 endpoint descriptors, different from the interface descriptor's value: 1
[    0.888077] usb 1-4: configuration #1 chosen from 1 choice
[    1.280104] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.296104] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.296118] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.297056] ata1.00: ATA-8: Hitachi HTS545050B9SA02, PB4AC60T, max UDMA/133
[    1.297060] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.298300] ata1.00: configured for UDMA/133
[    1.298631] ata2.00: ATAPI: MATSHITADVD-R   UJ-868, KB19, max UDMA/66, ATAPI AN
[    1.301332] ata2.00: configured for UDMA/66
[    1.312217] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 PB4A PQ: 0 ANSI: 5
[    1.312319] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.312378] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.312411] sd 0:0:0:0: [sda] Write Protect is off
[    1.312413] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.312430] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.312526]  sda:
[    1.317913] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-R   UJ-868   KB19 PQ: 0 ANSI: 5
[    1.321578] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.321582] Uniform CD-ROM driver Revision: 3.20
[    1.321689] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.321746] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.354594]  sda1 sda2 sda3
[    1.354841] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.417575] usb 2-5: configuration #1 chosen from 1 choice
[    1.422769] Initializing USB Mass Storage driver...
[    1.422855] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.422929] usbcore: registered new interface driver usb-storage
[    1.422931] USB Mass Storage support registered.
[    1.422992] usb-storage: device found at 3
[    1.422993] usb-storage: waiting for device to settle before scanning
[    1.724032] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.730126] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    1.934195] usb 4-1: configuration #1 chosen from 1 choice
[    1.937126] hub 4-1:1.0: USB hub found
[    1.940100] hub 4-1:1.0: 3 ports detected
[    2.156466] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[64b9e8fffec891d6]
[    2.257134] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    2.472436] usb 3-5: configuration #1 chosen from 1 choice
[    2.780100] usb 3-6: new full speed USB device using ohci_hcd and address 3
[    3.003422] usb 3-6: configuration #1 chosen from 1 choice
[    3.094104] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
[    3.217174] usb 4-1.1: configuration #1 chosen from 1 choice
[    3.298053] usb 4-1.2: new full speed USB device using ohci_hcd and address 4
[    3.409206] usb 4-1.2: configuration #1 chosen from 1 choice
[    3.490109] usb 4-1.3: new full speed USB device using ohci_hcd and address 5
[    3.605202] usb 4-1.3: configuration #1 chosen from 1 choice
[    6.420720] usb-storage: device scan complete
[    6.422861] scsi 6:0:0:0: Direct-Access     APPLE    SD Card Reader   1.00 PQ: 0 ANSI: 0
[    6.423204] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.424760] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.397758] udev: starting version 151
[    8.417893] Adding 8241144k swap on /dev/sda3.  Priority:-1 extents:1 across:8241144k 
[    8.543689] lp: driver loaded but no devices found
[    8.606402] i2c i2c-0: nForce2 SMBus adapter at 0x3140
[    8.606418] i2c i2c-1: nForce2 SMBus adapter at 0x3100
[    8.610669] Linux agpgart interface v0.103
[    8.626354] cfg80211: Calling CRDA to update world regulatory domain
[    8.648362] [drm] Initialized drm 1.1.0 20060810
[    8.650088] applesmc: Apple MacBook Pro 5 detected:
[    8.650090] applesmc:  - Model with accelerometer
[    8.650091] applesmc:  - Model with light sensors and backlight
[    8.650093] applesmc:  - Model with 20 temperature sensors
[    8.653166] input: bcm5974 as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input5
[    8.653238] usbcore: registered new interface driver bcm5974
[    8.662402] Linux video capture interface: v2.00
[    8.667610] Bluetooth: Core ver 2.15
[    8.669774] usbcore: registered new interface driver hiddev
[    8.670501] NET: Registered protocol family 31
[    8.670503] Bluetooth: HCI device and connection manager initialized
[    8.670505] Bluetooth: HCI socket layer initialized
[    8.671676] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    8.671747] usbcore: registered new interface driver btusb
[    8.674182] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input6
[    8.674233] generic-usb 0003:05AC:820A.0004: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-1.2/input0
[    8.679159] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input7
[    8.679223] generic-usb 0003:05AC:820B.0005: input,hidraw1: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-1.3/input0
[    8.679240] usbcore: registered new interface driver usbhid
[    8.679242] usbhid: v2.6:USB HID core driver
[    8.696751] cfg80211: World regulatory domain updated:
[    8.696753]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.696755]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.696757]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.696759]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.696761]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.696762]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.696991] type=1505 audit(1276740864.669:2):  operation="profile_load" pid=704 name="/sbin/dhclient3"
[    8.697480] type=1505 audit(1276740864.669:3):  operation="profile_load" pid=704 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.697742] type=1505 audit(1276740864.669:4):  operation="profile_load" pid=704 name="/usr/lib/connman/scripts/dhclient-script"
[    8.702302] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    8.705095] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8507)
[    8.705102] uvcvideo: No valid video chain found.
[    8.705146] usbcore: registered new interface driver uvcvideo
[    8.705342] USB Video Class driver (v0.1.0)
[    8.709747] applesmc: device successfully initialized (0xe0, 0x00).
[    8.709749] applesmc: device successfully initialized.
[    8.710416] applesmc: 2 fans found.
[    8.713316] input: applesmc as /devices/platform/applesmc.768/input/input8
[    8.713912] Registered led device: smc::kbd_backlight
[    8.713928] applesmc: driver successfully loaded.
[    8.725395] nouveau 0000:02:00.0: power state changed by ACPI to D0
[    8.725412] nouveau 0000:02:00.0: PCI INT A -> Link[Z003] -> GSI 23 (level, low) -> IRQ 23
[    8.725422] nouveau 0000:02:00.0: setting latency timer to 64
[    8.729352] apple 0003:05AC:8242.0001: hiddev96,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[    8.732097] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x096380c1)
[    8.732886] [drm] nouveau 0000:02:00.0: Detected MacBook Pro 9600GT chip. Disabling acceleration
[    8.732897] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
[    8.735633] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input9
[    8.735688] apple 0003:05AC:0236.0002: input,hidraw3: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[    8.746317] apple 0003:05AC:0236.0003: hidraw4: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
[    8.788937] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[    8.788941] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[    8.788944] hda_intel: Disable MSI for Nvidia chipset
[    8.788978] HDA Intel 0000:00:08.0: setting latency timer to 64
[    8.804193] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)
[    8.804394] b43: probe of ssb0:0 failed with error -95
[    8.804410] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    8.810932] [drm] nouveau 0000:02:00.0: ... appears to be valid
[    8.810935] [drm] nouveau 0000:02:00.0: BIT BIOS found
[    8.810938] [drm] nouveau 0000:02:00.0: Bios version 62.94.58.00
[    8.810941] [drm] nouveau 0000:02:00.0: TMDS table revision 2.0 not currently supported
[    8.810943] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 4.0
[    8.810946] [drm] nouveau 0000:02:00.0: DCB connector table: VHER 0x40 5 16 4
[    8.810948] [drm] nouveau 0000:02:00.0:   0: 0x00000340: type 0x40 idx 3 tag 0xff
[    8.810951] [drm] nouveau 0000:02:00.0:   1: 0x00001030: type 0x30 idx 0 tag 0x07
[    8.810953] [drm] nouveau 0000:02:00.0:   2: 0x0000a546: type 0x46 idx 5 tag 0x08
[    8.810955] [drm] nouveau 0000:02:00.0:   3: 0x00000400: type 0x00 idx 4 tag 0xff
[    8.810957] [drm] nouveau 0000:02:00.0:   4: 0x00050146: type 0x46 idx 1 tag 0x51
[    8.810959] [drm] nouveau 0000:02:00.0:   5: 0x00000210: type 0x10 idx 2 tag 0xff
[    8.810961] [drm] nouveau 0000:02:00.0:   6: 0x00000211: type 0x11 idx 2 tag 0xff
[    8.810963] [drm] nouveau 0000:02:00.0:   7: 0x00000213: type 0x13 idx 2 tag 0xff
[    8.810965] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 01000103 00010034
[    8.810967] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 02022286 0f200010
[    8.810969] [drm] nouveau 0000:02:00.0: Raw DCB entry 2: 02022212 00020010
[    8.810971] [drm] nouveau 0000:02:00.0: Raw DCB entry 3: 0000000e 00000000
[    8.810985] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xD47F
[    8.860156] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xD8CC
[    8.876103] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xE895
[    8.876119] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xE9DE
[    8.888241] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xEC4E
[    8.888244] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xECB3
[    8.912102] [drm] nouveau 0000:02:00.0: 0xECB3: Condition still not met after 20ms, skipping following opcodes
[    8.912117] [drm] nouveau 0000:02:00.0: 0xBFA6: parsing output script 0
[    8.912122] [drm] nouveau 0000:02:00.0: 0xC5C2: parsing output script 0
[    8.912125] [drm] nouveau 0000:02:00.0: 0xC3E4: parsing output script 0
[    9.029376] [TTM] Zone  kernel: Available graphics memory: 432110 kiB.
[    9.029379] [TTM] Zone highmem: Available graphics memory: 1406536 kiB.
[    9.029392] [drm] nouveau 0000:02:00.0: 512 MiB VRAM
[    9.041494] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)
[    9.043479] [drm] nouveau 0000:02:00.0: Detected a LVDS output
[    9.043490] [drm] nouveau 0000:02:00.0: Detected a DP output
[    9.043492] [drm] nouveau 0000:02:00.0: Detected a TMDS output
[    9.043495] [drm] nouveau 0000:02:00.0: Detected a LVDS connector
[    9.090569] type=1505 audit(1276740865.062:5):  operation="profile_load" pid=888 name="/usr/share/gdm/guest-session/Xsession"
[    9.091718] type=1505 audit(1276740865.062:6):  operation="profile_replace" pid=889 name="/sbin/dhclient3"
[    9.092269] type=1505 audit(1276740865.062:7):  operation="profile_replace" pid=889 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.092536] type=1505 audit(1276740865.062:8):  operation="profile_replace" pid=889 name="/usr/lib/connman/scripts/dhclient-script"
[    9.094797] type=1505 audit(1276740865.066:9):  operation="profile_load" pid=890 name="/usr/bin/evince"
[    9.101049] type=1505 audit(1276740865.074:10):  operation="profile_load" pid=890 name="/usr/bin/evince-previewer"
[    9.105956] type=1505 audit(1276740865.078:11):  operation="profile_load" pid=890 name="/usr/bin/evince-thumbnailer"
[    9.155292] [drm] nouveau 0000:02:00.0: Detected a DisplayPort connector
[    9.239622] applesmc: wait status failed: 5 != 0
[    9.341335]   alloc irq_desc for 28 on node -1
[    9.341338]   alloc kstat_irqs on node -1
[    9.341355] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
[    9.341642] eth0: no link during initialization.
[    9.342119] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.211400] [drm] nouveau 0000:02:00.0: allocated 1440x900 fb: 0x401a0000, bo f4b73c00
[   10.211445] fb0: nouveaufb frame buffer device
[   10.211447] registered panic notifier
[   10.211451] [drm] Initialized nouveau 0.0.15 20090420 for 0000:02:00.0 on minor 0
[   10.212792] vga16fb: initializing
[   10.212794] vga16fb: mapped to 0xc00a0000
[   10.212796] vga16fb: not registering due to another framebuffer present
[   10.227032] [drm] nouveau 0000:02:00.0: 0xBFAA: parsing output script 1
[   10.227053] [drm] nouveau 0000:02:00.0: 0xBE61: parsing clock script 0
[   10.230616] Console: switching to colour frame buffer device 180x56
[   10.486405] [drm] nouveau 0000:02:00.0: 0xBFA1: parsing clock script 1
s@Macbook:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
s@Macbook:~$

---

### Post by linuxopjemac on 2010-06-17
I though that you have a Mac Pro, sorry.

I will first try to focus on wired internet, which is the most important. Wireless does not work as you have the open source b43 driver which does not support this new Broadcom device 4322 (see [http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices):](http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices):)
[ 8.702302] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[ 8.804193] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)
[ 8.804394] b43: probe of ssb0:0 failed with error -95

You will need the closed source driver from Broadcom. We will do this after you have wired internet.

I see that the forcedeth driver is in use. This should be correct, as you have a Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1).

What kind of networkmanager do you use? Is it networkmanager?
```

sudo dpkg -l | grep networkmanager
```

Can you give me the output of :

```
sudo ifconfig
```

I guess that you are sure that wired ethernet works under MacOSX, right?

You might want to to it manually:

sudo nano /etc/network/interfaces

and add the following lines to the interfaces file (eth0 should be your ethernet, this can be checked with ifconfig)
```

auto eth0
iface eth0 inet dhcp
```

```
sudo ifdown eth0
sudo ifup eth0
```

and check if you have connection with:

```
sudo ifconfig
```

---

### Post by SRama on 2010-06-17
Here is the output of ifconfig
s@Macbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 64:b9:e8:c8:91:d6  
          inet6 addr: fe80::66b9:e8ff:fec8:91d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225910 (225.9 KB)  TX bytes:3260 (3.2 KB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

s@Macbook:~$ 


Sorry, but i'm really new to this and i'm not sure how to make the additions you mentioned for sudo nano /etc/network/interfaces

When i put that command into terminal it takes me to a screen where there are only two lines and some commands such as ^G, ^J at the bottom. After i type in those changes i'm not sure how to save them.

---

### Post by linuxopjemac on 2010-06-18
nano is an editor.

You can write those two lines of code and then you do CTRL-X and "y" to save.

---

