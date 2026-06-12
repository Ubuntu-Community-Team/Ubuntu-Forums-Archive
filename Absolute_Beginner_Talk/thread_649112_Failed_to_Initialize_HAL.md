---
title: "Failed to Initialize HAL"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by dfault312 on 2007-12-24
Im a linux n00b, so I really have no idea what to look at and/or modify to fix this. I updated from 7.04 to 7.10 yesterday, and now every time I start a session, I get an error message "Failed to Initialize HAL" From searching the forums, it seems like this is a common program, but the solution seems a little bit elusive and usually complex. I tried reinstalling HAL, but in the proccess, this happens in the terminal:

> Setting up hal (0.5.9.1-6ubuntu5) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hal


So, maybe that points to something else that needs fixed? Can anyone help me?

---

### Post by p_quarles on 2007-12-24
What happens when you try to restart it? The installation process is try to start it, and may have encountered that error because it's already running (even though it "failed to initialize"). Anyway, give this a try:
```
sudo /etc/init.d/hal restart
```
If it doesn't work, post the output in your reply.

---

### Post by dfault312 on 2007-12-24
That seems to work

> me@ubuntu:~$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald
me@ubuntu:~$ 


Although, I'm not really sure if it has any lasting results on my system. Even if it does work, I still get the error the next time I log in.

---

### Post by p_quarles on 2007-12-24
Do you mean that you already logged back in and got the same error, or that you expect that you will? If the latter, that has not been my experience. 

In any case, if the problem persists, I would look at your kernel log files (the most recent ones will be /var/log/kern.log and /var/log/kern.log.0) for some more extensive explanations of the hald initialization problem. Even if you can't make sense of the log files, it's likely that I or someone else here can help you figure it out.

---

### Post by dfault312 on 2007-12-24
Yes, I've already logged back in and gotten the same error.

this is cat /var/log/kern.log ...i think it cut off the top, but i dont remember how to view all of that.

> Dec 24 19:45:20 ubuntu kernel: [   14.957874] PCI: Using ACPI for IRQ routing
Dec 24 19:45:20 ubuntu kernel: [   14.957878] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 24 19:45:20 ubuntu kernel: [   14.964890] NET: Registered protocol family 8
Dec 24 19:45:20 ubuntu kernel: [   14.964893] NET: Registered protocol family 20
Dec 24 19:45:20 ubuntu kernel: [   14.964972] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Dec 24 19:45:20 ubuntu kernel: [   14.964976] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
Dec 24 19:45:20 ubuntu kernel: [   14.964980] pnp: 00:00: iomem range 0x1000000-0x1ff76fff could not be reserved
Dec 24 19:45:20 ubuntu kernel: [   14.964983] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Dec 24 19:45:20 ubuntu kernel: [   14.964996] pnp: 00:0a: ioport range 0x800-0x85f has been reserved
Dec 24 19:45:20 ubuntu kernel: [   14.964999] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
Dec 24 19:45:20 ubuntu kernel: [   14.965002] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
Dec 24 19:45:20 ubuntu kernel: [   14.967345] Time: tsc clocksource has been installed.
Dec 24 19:45:20 ubuntu kernel: [   14.995381] PCI: Bridge: 0000:00:01.0
Dec 24 19:45:20 ubuntu kernel: [   14.995384]   IO window: disabled.
Dec 24 19:45:20 ubuntu kernel: [   14.995389]   MEM window: fc000000-fdffffff
Dec 24 19:45:20 ubuntu kernel: [   14.995393]   PREFETCH window: f0000000-f7ffffff
Dec 24 19:45:20 ubuntu kernel: [   14.995398] PCI: Bridge: 0000:00:1e.0
Dec 24 19:45:20 ubuntu kernel: [   14.995402]   IO window: e000-efff
Dec 24 19:45:20 ubuntu kernel: [   14.995408]   MEM window: fe100000-fe3fffff
Dec 24 19:45:20 ubuntu kernel: [   14.995412]   PREFETCH window: 30000000-300fffff
Dec 24 19:45:20 ubuntu kernel: [   14.995430] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Dec 24 19:45:20 ubuntu kernel: [   14.995443] NET: Registered protocol family 2
Dec 24 19:45:20 ubuntu kernel: [   15.035390] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 24 19:45:20 ubuntu kernel: [   15.035439] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Dec 24 19:45:20 ubuntu kernel: [   15.035571] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Dec 24 19:45:20 ubuntu kernel: [   15.035661] TCP: Hash tables configured (established 16384 bind 16384)
Dec 24 19:45:20 ubuntu kernel: [   15.035664] TCP reno registered
Dec 24 19:45:20 ubuntu kernel: [   15.047496] checking if image is initramfs... it is
Dec 24 19:45:20 ubuntu kernel: [   15.499302] Switched to high resolution mode on CPU 0
Dec 24 19:45:20 ubuntu kernel: [   15.782596] Freeing initrd memory: 7434k freed
Dec 24 19:45:20 ubuntu kernel: [   15.782731] Simple Boot Flag at 0x7a set to 0x1
Dec 24 19:45:20 ubuntu kernel: [   15.783013] audit: initializing netlink socket (disabled)
Dec 24 19:45:20 ubuntu kernel: [   15.783029] audit(1198525480.216:1): initialized
Dec 24 19:45:20 ubuntu kernel: [   15.785537] VFS: Disk quotas dquot_6.5.1
Dec 24 19:45:20 ubuntu kernel: [   15.785605] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 19:45:20 ubuntu kernel: [   15.785721] io scheduler noop registered
Dec 24 19:45:20 ubuntu kernel: [   15.785724] io scheduler anticipatory registered
Dec 24 19:45:20 ubuntu kernel: [   15.785726] io scheduler deadline registered
Dec 24 19:45:20 ubuntu kernel: [   15.785745] io scheduler cfq registered (default)
Dec 24 19:45:20 ubuntu kernel: [   15.785793] Boot video device is 0000:01:00.0
Dec 24 19:45:21 ubuntu kernel: [   15.786000] isapnp: Scanning for PnP cards...
Dec 24 19:45:21 ubuntu kernel: [   16.140084] isapnp: No Plug & Play device found
Dec 24 19:45:21 ubuntu kernel: [   16.173119] Real Time Clock Driver v1.12ac
Dec 24 19:45:21 ubuntu kernel: [   16.173217] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 24 19:45:21 ubuntu kernel: [   16.173314] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 24 19:45:21 ubuntu kernel: [   16.174348] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 24 19:45:21 ubuntu kernel: [   16.175283] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 24 19:45:21 ubuntu kernel: [   16.175538] input: Macintosh mouse button emulation as /class/input/input0
Dec 24 19:45:21 ubuntu kernel: [   16.175634] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
Dec 24 19:45:21 ubuntu kernel: [   16.175637] PNP: PS/2 controller doesn't have AUX irq; using default 12
Dec 24 19:45:21 ubuntu kernel: [   16.178962] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 19:45:21 ubuntu kernel: [   16.178972] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 24 19:45:21 ubuntu kernel: [   16.179226] mice: PS/2 mouse device common for all mice
Dec 24 19:45:21 ubuntu kernel: [   16.179364] EISA: Probing bus 0 at eisa.0
Dec 24 19:45:21 ubuntu kernel: [   16.179403] EISA: Detected 0 cards.
Dec 24 19:45:21 ubuntu kernel: [   16.179519] TCP cubic registered
Dec 24 19:45:21 ubuntu kernel: [   16.179535] NET: Registered protocol family 1
Dec 24 19:45:21 ubuntu kernel: [   16.179564] Using IPI No-Shortcut mode
Dec 24 19:45:21 ubuntu kernel: [   16.179745]   Magic number: 3:541:749
Dec 24 19:45:21 ubuntu kernel: [   16.179751]   hash matches device ttyS0
Dec 24 19:45:21 ubuntu kernel: [   16.180390] Freeing unused kernel memory: 364k freed
Dec 24 19:45:21 ubuntu kernel: [   16.215245] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 24 19:45:21 ubuntu kernel: [   17.429363] md: raid1 personality registered for level 1
Dec 24 19:45:21 ubuntu kernel: [   17.433747] md: raid0 personality registered for level 0
Dec 24 19:45:21 ubuntu kernel: [   17.440294] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
Dec 24 19:45:21 ubuntu kernel: [   17.460617] SCSI subsystem initialized
Dec 24 19:45:21 ubuntu kernel: [   17.467392] libata version 2.21 loaded.
Dec 24 19:45:21 ubuntu kernel: [   17.489164] usbcore: registered new interface driver usbfs
Dec 24 19:45:21 ubuntu kernel: [   17.489222] usbcore: registered new interface driver hub
Dec 24 19:45:21 ubuntu kernel: [   17.489269] usbcore: registered new device driver usb
Dec 24 19:45:21 ubuntu kernel: [   17.491267] ACPI: PCI Interrupt 0000:02:0a.2[C] -> GSI 17 (level, low) -> IRQ 16
Dec 24 19:45:21 ubuntu kernel: [   17.491281] ehci_hcd 0000:02:0a.2: EHCI Host Controller
Dec 24 19:45:21 ubuntu kernel: [   17.491346] ehci_hcd 0000:02:0a.2: new USB bus registered, assigned bus number 1
Dec 24 19:45:21 ubuntu kernel: [   17.515014] ehci_hcd 0000:02:0a.2: irq 16, io mem 0xfe2ff400
Dec 24 19:45:21 ubuntu kernel: [   17.515022] ehci_hcd 0000:02:0a.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Dec 24 19:45:21 ubuntu kernel: [   17.515188] usb usb1: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   17.515243] hub 1-0:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   17.515251] hub 1-0:1.0: 5 ports detected
Dec 24 19:45:21 ubuntu kernel: [   17.624093] USB Universal Host Controller Interface driver v3.0
Dec 24 19:45:21 ubuntu kernel: [   17.624201] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 17
Dec 24 19:45:21 ubuntu kernel: [   17.624214] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Dec 24 19:45:21 ubuntu kernel: [   17.624219] uhci_hcd 0000:00:1f.2: UHCI Host Controller
Dec 24 19:45:21 ubuntu kernel: [   17.624276] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 2
Dec 24 19:45:21 ubuntu kernel: [   17.624305] uhci_hcd 0000:00:1f.2: irq 17, io base 0x0000ff80
Dec 24 19:45:21 ubuntu kernel: [   17.624479] usb usb2: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   17.624539] hub 2-0:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   17.624548] hub 2-0:1.0: 2 ports detected
Dec 24 19:45:21 ubuntu kernel: [   17.727113] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 18
Dec 24 19:45:21 ubuntu kernel: [   17.727123] PCI: Setting latency timer of device 0000:00:1f.4 to 64
Dec 24 19:45:21 ubuntu kernel: [   17.727127] uhci_hcd 0000:00:1f.4: UHCI Host Controller
Dec 24 19:45:21 ubuntu kernel: [   17.727174] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 3
Dec 24 19:45:21 ubuntu kernel: [   17.727199] uhci_hcd 0000:00:1f.4: irq 18, io base 0x0000ff60
Dec 24 19:45:21 ubuntu kernel: [   17.727356] usb usb3: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   17.727413] hub 3-0:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   17.727424] hub 3-0:1.0: 2 ports detected
Dec 24 19:45:21 ubuntu kernel: [   17.835807] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 24 19:45:21 ubuntu kernel: [   17.835880] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 17
Dec 24 19:45:21 ubuntu kernel: [   17.835894] ohci_hcd 0000:02:0a.0: OHCI Host Controller
Dec 24 19:45:21 ubuntu kernel: [   17.835955] ohci_hcd 0000:02:0a.0: new USB bus registered, assigned bus number 4
Dec 24 19:45:21 ubuntu kernel: [   17.835970] ohci_hcd 0000:02:0a.0: irq 17, io mem 0xfe2fd000
Dec 24 19:45:21 ubuntu kernel: [   17.858971] usb 1-1: new high speed USB device using ehci_hcd and address 2
Dec 24 19:45:21 ubuntu kernel: [   18.397608] usb usb4: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   18.397663] hub 4-0:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   18.397672] hub 4-0:1.0: 3 ports detected
Dec 24 19:45:21 ubuntu kernel: [   18.474494] usb 1-1: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   18.714852] usb 1-2: new high speed USB device using ehci_hcd and address 3
Dec 24 19:45:21 ubuntu kernel: [   18.848702] usb 1-2: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   18.910966] ACPI: PCI Interrupt 0000:02:0a.1[B] -> GSI 16 (level, low) -> IRQ 19
Dec 24 19:45:21 ubuntu kernel: [   18.910978] ohci_hcd 0000:02:0a.1: OHCI Host Controller
Dec 24 19:45:21 ubuntu kernel: [   18.911026] ohci_hcd 0000:02:0a.1: new USB bus registered, assigned bus number 5
Dec 24 19:45:21 ubuntu kernel: [   18.911041] ohci_hcd 0000:02:0a.1: irq 19, io mem 0xfe2fc000
Dec 24 19:45:21 ubuntu kernel: [   19.473335] usb usb5: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   19.473394] hub 5-0:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   19.473405] hub 5-0:1.0: 2 ports detected
Dec 24 19:45:21 ubuntu kernel: [   19.582740] usb 1-3: new high speed USB device using ehci_hcd and address 4
Dec 24 19:45:21 ubuntu kernel: [   19.716062] usb 1-3: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   19.716245] hub 1-3:1.0: USB hub found
Dec 24 19:45:21 ubuntu kernel: [   19.716323] hub 1-3:1.0: 4 ports detected
Dec 24 19:45:21 ubuntu kernel: [   20.058679] usb 2-2: new low speed USB device using uhci_hcd and address 2
Dec 24 19:45:21 ubuntu kernel: [   20.234628] usb 2-2: configuration #1 chosen from 1 choice
Dec 24 19:45:21 ubuntu kernel: [   20.239018] usbcore: registered new interface driver libusual
Dec 24 19:45:21 ubuntu kernel: [   20.251335] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 24 19:45:21 ubuntu kernel: [   20.251342] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 24 19:45:21 ubuntu kernel: [   20.253656] Initializing USB Mass Storage driver...
Dec 24 19:45:21 ubuntu kernel: [   20.254084] scsi0 : SCSI emulation for USB Mass Storage devices
Dec 24 19:45:21 ubuntu kernel: [   20.254170] usb-storage: device found at 2
Dec 24 19:45:21 ubuntu kernel: [   20.254173] usb-storage: waiting for device to settle before scanning
Dec 24 19:45:21 ubuntu kernel: [   20.254218] scsi1 : SCSI emulation for USB Mass Storage devices
Dec 24 19:45:21 ubuntu kernel: [   20.254286] usb-storage: device found at 3
Dec 24 19:45:21 ubuntu kernel: [   20.254288] usb-storage: waiting for device to settle before scanning
Dec 24 19:45:21 ubuntu kernel: [   20.254312] usbcore: registered new interface driver usb-storage
Dec 24 19:45:21 ubuntu kernel: [   20.254315] USB Mass Storage support registered.
Dec 24 19:45:21 ubuntu kernel: [   20.270754] ata_piix 0000:00:1f.1: version 2.11
Dec 24 19:45:21 ubuntu kernel: [   20.270817] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Dec 24 19:45:21 ubuntu kernel: [   20.270908] scsi2 : ata_piix
Dec 24 19:45:21 ubuntu kernel: [   20.270991] scsi3 : ata_piix
Dec 24 19:45:21 ubuntu kernel: [   20.271041] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Dec 24 19:45:21 ubuntu kernel: [   20.271045] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Dec 24 19:45:21 ubuntu kernel: [   20.435726] ata1.00: Host Protected Area detected:
Dec 24 19:45:21 ubuntu kernel: [   20.435728] ^Icurrent size: 156250000 sectors
Dec 24 19:45:21 ubuntu kernel: [   20.435729] ^Inative size: 156301488 sectors
Dec 24 19:45:21 ubuntu kernel: [   20.437799] ata1.00: native size increased to 156301488 sectors
Dec 24 19:45:21 ubuntu kernel: [   20.437803] ata1.00: ATA-5: WDC WD800BB-75CAA0, 16.06V16, max UDMA/100
Dec 24 19:45:21 ubuntu kernel: [   20.437805] ata1.00: 156301488 sectors, multi 8: LBA 
Dec 24 19:45:21 ubuntu kernel: [   20.451728] ata1.00: configured for UDMA/100
Dec 24 19:45:21 ubuntu kernel: [   20.926866] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-616T, F308, max UDMA/33
Dec 24 19:45:21 ubuntu kernel: [   20.926872] ata2.01: ATAPI: SAMSUNG CD-R/RW SW-240B, BD11, max UDMA/33
Dec 24 19:45:21 ubuntu kernel: [   21.090846] ata2.00: configured for UDMA/33
Dec 24 19:45:21 ubuntu kernel: [   21.262804] ata2.01: configured for UDMA/33
Dec 24 19:45:21 ubuntu kernel: [   21.262924] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800BB-75CA 16.0 PQ: 0 ANSI: 5
Dec 24 19:45:21 ubuntu kernel: [   21.263158] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Dec 24 19:45:21 ubuntu kernel: [   21.263173] sd 2:0:0:0: [sda] Write Protect is off
Dec 24 19:45:21 ubuntu kernel: [   21.263176] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 24 19:45:21 ubuntu kernel: [   21.263197] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 19:45:21 ubuntu kernel: [   21.263259] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Dec 24 19:45:21 ubuntu kernel: [   21.263271] sd 2:0:0:0: [sda] Write Protect is off
Dec 24 19:45:21 ubuntu kernel: [   21.263274] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 24 19:45:21 ubuntu kernel: [   21.263294] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 19:45:21 ubuntu kernel: [   21.263299]  sda: sda1
Dec 24 19:45:21 ubuntu kernel: [   21.288670] sd 2:0:0:0: [sda] Attached SCSI disk
Dec 24 19:45:21 ubuntu kernel: [   21.289151] scsi 3:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F308 PQ: 0 ANSI: 5
Dec 24 19:45:21 ubuntu kernel: [   21.290767] scsi 3:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  BD11 PQ: 0 ANSI: 5
Dec 24 19:45:21 ubuntu kernel: [   21.431967] JFS: nTxBlock = 4026, nTxLock = 32210
Dec 24 19:45:21 ubuntu kernel: [   21.445852] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Dec 24 19:45:21 ubuntu kernel: [   21.446574] SGI XFS Quota Management subsystem
Dec 24 19:45:21 ubuntu kernel: [   21.478171] NTFS driver 2.1.28 [Flags: R/O MODULE].
Dec 24 19:45:21 ubuntu kernel: [   21.489068] fuse init (API version 7.8)
Dec 24 19:45:21 ubuntu kernel: [   21.495963] loop: module loaded
Dec 24 19:45:21 ubuntu kernel: [   21.501341] Registering unionfs 1.4
Dec 24 19:45:21 ubuntu kernel: [   21.501345] unionfs: debugging is not enabled
Dec 24 19:45:21 ubuntu kernel: [   21.506410] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
Dec 24 19:45:21 ubuntu kernel: [   21.538148] AppArmor: AppArmor initialized<5>audit(1198525486.216:2):  type=1505 info="AppArmor initialized" pid=1623
Dec 24 19:45:21 ubuntu kernel: [   21.547921][COLOR="Red"] Failure[/COLOR] registering capabilities with primary security module.
Dec 24 19:45:21 ubuntu kernel: [   22.373324] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Dec 24 19:45:21 ubuntu kernel: [   22.373367] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Dec 24 19:45:21 ubuntu kernel: [   22.373372] 8139cp 0000:02:07.0: Try the "8139too" driver instead.
Dec 24 19:45:21 ubuntu kernel: [   22.375318] 8139too Fast Ethernet driver 0.9.28
Dec 24 19:45:21 ubuntu kernel: [   22.375375] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 19
Dec 24 19:45:21 ubuntu kernel: [   22.375726] eth0: RealTek RTL8139 at 0xe0cfcc00, 00:c0:a8:86:c9:c8, IRQ 19
Dec 24 19:45:21 ubuntu kernel: [   22.375728] eth0:  Identified 8139 chip type 'RTL-8139C'
Dec 24 19:45:21 ubuntu kernel: [   22.382365] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
Dec 24 19:45:21 ubuntu kernel: [   22.382445] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 16
Dec 24 19:45:21 ubuntu kernel: [   22.383059] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
Dec 24 19:45:21 ubuntu kernel: [   22.389424] eth1: ADMtek Comet rev 17 at Port 0xe800, 00:1A:70:11:A7:0F, IRQ 16.
Dec 24 19:45:21 ubuntu kernel: [   22.464030] sd 2:0:0:0: Attached scsi generic sg0 type 0
Dec 24 19:45:21 ubuntu kernel: [   22.464059] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 24 19:45:21 ubuntu kernel: [   22.464083] scsi 3:0:1:0: Attached scsi generic sg2 type 5
Dec 24 19:45:21 ubuntu kernel: [   22.558607] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
Dec 24 19:45:21 ubuntu kernel: [   22.558614] Uniform CD-ROM driver Revision: 3.20
Dec 24 19:45:21 ubuntu kernel: [   22.558686] sr 3:0:0:0: Attached scsi CD-ROM sr0
Dec 24 19:45:21 ubuntu kernel: [   22.566806] usbcore: registered new interface driver hiddev
Dec 24 19:45:21 ubuntu kernel: [   22.680760] Floppy drive(s): fd0 is 1.44M
Dec 24 19:45:21 ubuntu kernel: [   22.682677] input: Logitech USB Optical Mouse as /class/input/input2
Dec 24 19:45:21 ubuntu kernel: [   22.682705] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1f.2-2
Dec 24 19:45:21 ubuntu kernel: [   22.682723] usbcore: registered new interface driver usbhid
Dec 24 19:45:21 ubuntu kernel: [   22.682727] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec 24 19:45:21 ubuntu kernel: [   22.718041] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Dec 24 19:45:21 ubuntu kernel: [   22.718119] sr 3:0:1:0: Attached scsi CD-ROM sr1
Dec 24 19:45:21 ubuntu kernel: [   22.733263] FDC 0 is a post-1991 82077
Dec 24 19:45:21 ubuntu kernel: [   23.778662] kjournald starting.  Commit interval 5 seconds
Dec 24 19:45:21 ubuntu kernel: [   23.778681] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 19:45:21 ubuntu kernel: [   23.859249] EXT3 FS on loop0, internal journal
Dec 24 19:45:21 ubuntu kernel: [   25.250901] usb-storage: device scan complete
Dec 24 19:45:21 ubuntu kernel: [   25.251263] usb-storage: device scan complete
Dec 24 19:45:21 ubuntu kernel: [   25.251529] scsi 1:0:0:0: Direct-Access     SEAGATE  ST3250823A       3.03 PQ: 0 ANSI: 2
Dec 24 19:45:21 ubuntu kernel: [   25.252148] scsi 0:0:0:0: Direct-Access     Canon    MP500Storage     0109 PQ: 0 ANSI: 2
Dec 24 19:45:21 ubuntu kernel: [   25.252749] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Dec 24 19:45:21 ubuntu kernel: [   25.253623] sd 1:0:0:0: [sdb] Write Protect is off
Dec 24 19:45:21 ubuntu kernel: [   25.253626] sd 1:0:0:0: [sdb] Mode Sense: 53 00 00 08
Dec 24 19:45:21 ubuntu kernel: [   25.253629] sd 1:0:0:0: [sdb] Assuming drive cache: write through
Dec 24 19:45:21 ubuntu kernel: [   25.254371] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Dec 24 19:45:21 ubuntu kernel: [   25.255247] sd 1:0:0:0: [sdb] Write Protect is off
Dec 24 19:45:21 ubuntu kernel: [   25.255250] sd 1:0:0:0: [sdb] Mode Sense: 53 00 00 08
Dec 24 19:45:21 ubuntu kernel: [   25.255252] sd 1:0:0:0: [sdb] Assuming drive cache: write through
Dec 24 19:45:21 ubuntu kernel: [   25.255258]  sdb: sdb1
Dec 24 19:45:21 ubuntu kernel: [   25.278477] sd 1:0:0:0: [sdb] Attached SCSI disk
Dec 24 19:45:21 ubuntu kernel: [   25.278534] sd 1:0:0:0: Attached scsi generic sg3 type 0
Dec 24 19:45:21 ubuntu kernel: [   25.281035] sd 0:0:0:0: [sdc] Attached SCSI removable disk
Dec 24 19:45:21 ubuntu kernel: [   25.281075] sd 0:0:0:0: Attached scsi generic sg4 type 0
Dec 24 19:45:21 ubuntu kernel: [   34.738554] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Dec 24 19:45:21 ubuntu kernel: [   36.203976] NET: Registered protocol family 10
Dec 24 19:45:21 ubuntu kernel: [   36.204100] lo: Disabled Privacy Extensions
Dec 24 19:45:21 ubuntu kernel: [   36.493671] NET: Registered protocol family 17
Dec 24 19:45:21 ubuntu kernel: [   36.592841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 19:45:21 ubuntu kernel: [   36.638569] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 24 19:45:21 ubuntu kernel: [   36.687198] Linux agpgart interface v0.102 (c) Dave Jones
Dec 24 19:45:21 ubuntu kernel: [   36.804881] iTCO_vendor_support: vendor-support=0
Dec 24 19:45:21 ubuntu kernel: [   36.823492] agpgart: Detected an Intel i850 Chipset.
Dec 24 19:45:21 ubuntu kernel: [   36.829367] agpgart: AGP aperture is 128M @ 0xe8000000
Dec 24 19:45:21 ubuntu kernel: [   36.836043] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Dec 24 19:45:21 ubuntu kernel: [   36.836122] iTCO_wdt: [COLOR="Red"]failed[/COLOR] to reset NO_REBOOT flag, reboot disabled by hardware
Dec 24 19:45:21 ubuntu kernel: [   36.836131] iTCO_wdt: No card detected
Dec 24 19:45:21 ubuntu kernel: [   36.896152] Intel 82802 RNG detected
Dec 24 19:45:21 ubuntu kernel: [   37.534397] 0000:02:08.0: tulip_stop_rxtx() [COLOR="Red"]failed[/COLOR] (CSR5 0xfc664010 CSR6 0xff972113)
Dec 24 19:45:21 ubuntu kernel: [   37.534410] eth1: Setting full-duplex based on MII#1 link partner capability of 45e1.
Dec 24 19:45:21 ubuntu kernel: [   37.728056] nvidia: module license 'NVIDIA' taints kernel.
Dec 24 19:45:21 ubuntu kernel: [   37.994909] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
Dec 24 19:45:21 ubuntu kernel: [   37.995232] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Dec 24 19:45:21 ubuntu kernel: [   38.159668] input: PC Speaker as /class/input/input3
Dec 24 19:45:21 ubuntu kernel: [   38.813434] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x170C
Dec 24 19:45:21 ubuntu kernel: [   38.813460] usbcore: registered new interface driver usblp
Dec 24 19:45:21 ubuntu kernel: [   38.813464] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Dec 24 19:45:21 ubuntu kernel: [   38.856584] parport_pc 00:09: reported by Plug and Play ACPI
Dec 24 19:45:21 ubuntu kernel: [   38.856639] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Dec 24 19:45:21 ubuntu kernel: [   39.213483] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 20
Dec 24 19:45:21 ubuntu kernel: [   41.901232] gameport: CS46xx Gameport is pci0000:02:09.0/gameport0, speed 1242kHz
Dec 24 19:45:21 ubuntu kernel: [   42.127229] lp0: using parport0 (interrupt-driven).
Dec 24 19:45:21 ubuntu kernel: [   42.517929] EXT3 FS on loop0, internal journal
Dec 24 19:45:21 ubuntu kernel: [   43.448251] kjournald starting.  Commit interval 5 seconds
Dec 24 19:45:21 ubuntu kernel: [   43.448567] EXT3 FS on loop1, internal journal
Dec 24 19:45:21 ubuntu kernel: [   43.448573] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 19:45:21 ubuntu kernel: [   46.383624] eth0: no IPv6 routers present
Dec 24 19:45:21 ubuntu kernel: [   46.971545] eth1: no IPv6 routers present
Dec 24 19:45:21 ubuntu kernel: [   50.532618] Adding 499012k swap on /media/host/wubi/disks/swap.virtual.disk.  Priority:-1 extents:2 across:16013108k
Dec 24 19:45:21 ubuntu kernel: [   53.982072] No dock devices found.
Dec 24 19:45:21 ubuntu kernel: [   54.190221] input: Power Button (FF) as /class/input/input4
Dec 24 19:45:21 ubuntu kernel: [   54.195207] ACPI: Power Button (FF) [PWRF]
Dec 24 19:45:21 ubuntu kernel: [   54.240255] input: Power Button (CM) as /class/input/input5
Dec 24 19:45:21 ubuntu kernel: [   54.245182] ACPI: Power Button (CM) [VBTN]
Dec 24 19:45:36 ubuntu kernel: [   71.716780] ppdev: user-space parallel port driver
Dec 24 19:45:39 ubuntu kernel: [   74.013320] audit(1198543538.950:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5598 profile="/usr/sbin/cupsd"
Dec 24 19:45:39 ubuntu kernel: [   74.463552] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 24 19:45:39 ubuntu kernel: [   74.463558] apm: overridden by ACPI.
Dec 24 19:45:40 ubuntu kernel: [   75.798069] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 24 19:45:40 ubuntu kernel: [   75.798217] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 24 19:45:40 ubuntu kernel: [   75.798351] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 24 19:45:42 ubuntu kernel: [   77.463119] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Dec 24 19:45:42 ubuntu kernel: [   77.966953] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec 24 19:45:43 ubuntu kernel: [   78.024040] NFSD: starting 90-second grace period
Dec 24 19:45:44 ubuntu kernel: [   79.078936] [COLOR="Red"]Failure[/COLOR] registering capabilities with primary security module.
Dec 24 19:45:51 ubuntu kernel: [   86.471163] device lo entered promiscuous mode
Dec 24 19:45:51 ubuntu kernel: [   86.471178] audit(1198543551.451:4): dev=lo prom=256 old_prom=0 auid=4294967295
Dec 24 19:45:51 ubuntu kernel: [   86.471518] device eth0 entered promiscuous mode
Dec 24 19:45:51 ubuntu kernel: [   86.471524] audit(1198543551.451:5): dev=eth0 prom=256 old_prom=0 auid=4294967295
Dec 24 19:45:51 ubuntu kernel: [   86.471781] device eth1 entered promiscuous mode
Dec 24 19:45:51 ubuntu kernel: [   86.471787] audit(1198543551.451:6): dev=eth1 prom=256 old_prom=0 auid=4294967295
Dec 24 19:48:49 ubuntu kernel: [  264.949399] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 24 19:48:50 ubuntu kernel: [  264.949555] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 24 19:48:50 ubuntu kernel: [  264.949689] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 24 19:53:26 ubuntu kernel: [  541.290848] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 24 19:53:26 ubuntu kernel: [  541.291005] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 24 19:53:26 ubuntu kernel: [  541.291140] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 24 20:01:08 ubuntu kernel: [ 1003.697724] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 24 20:01:08 ubuntu kernel: [ 1003.697884] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 24 20:01:08 ubuntu kernel: [ 1003.698018] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode


---

### Post by p_quarles on 2007-12-24
Hmm. I don't see anything related to hald in there. I had another thought, though: the problem seems to be that HAL doesn't want to want to fully initialize with the "start" command. Try this:
```
sudo /etc/init.d/hal stop
```
and then
```
sudo /etc/init.d/hal start
```
This should give you more information about why it's failing to start, which might provide a clue about what's going on.

---

### Post by dfault312 on 2007-12-24
and kern.log.0

> me@ubuntu:~$ cat /var/log/kern.log.0
Nov 13 11:59:36 ubuntu kernel: [ 4213.232588] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Nov 13 11:59:36 ubuntu kernel: [ 4213.434910] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov 13 11:59:36 ubuntu kernel: [ 4213.435643] NFSD: starting 90-second grace period
Nov 13 12:20:57 ubuntu kernel: [ 5494.079376] nfsd: last server has exited
Nov 13 12:20:57 ubuntu kernel: [ 5494.079381] nfsd: unexporting all filesystems
Nov 13 12:20:57 ubuntu kernel: [ 5494.079932] RPC: [COLOR="Red"]failed[/COLOR] to contact portmap (errno -5).
Dec 22 15:47:46 ubuntu kernel: Inspecting /boot/System.map-2.6.20-16-generic
Dec 22 15:47:46 ubuntu kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Dec 22 15:47:46 ubuntu kernel: Symbols match kernel version 2.6.20.
Dec 22 15:47:46 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 15:47:46 ubuntu kernel: [    0.000000] sanitize start
Dec 22 15:47:46 ubuntu kernel: [    0.000000] sanitize end
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fe77000 end: 000000001ff77000 type: 1
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 000000001ff77000 size: 0000000000002000 end: 000000001ff79000 type: 4
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 000000001ff79000 size: 0000000000087000 end: 0000000020000000 type: 2
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
Dec 22 15:47:46 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff77000 (usable)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ff77000 - 000000001ff79000 (ACPI NVS)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ff79000 - 0000000020000000 (reserved)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Dec 22 15:47:46 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] 511MB LOWMEM available.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] found SMP MP-table at 000fe710
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 130935) 0 entries of 256 used
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Zone PFN ranges:
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   Normal       4096 ->   130935
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   HighMem    130935 ->   130935
Dec 22 15:47:46 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 15:47:46 ubuntu kernel: [    0.000000]     0:        0 ->   130935
Dec 22 15:47:46 ubuntu kernel: [    0.000000] On node 0 totalpages: 130935
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   Normal zone: 990 pages used for memmap
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   Normal zone: 125849 pages, LIFO batch:31
Dec 22 15:47:46 ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Dec 22 15:47:46 ubuntu kernel: [    0.000000] DMI 2.3 present.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd560
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: RSDT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd574
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: FADT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd5a8
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffe5d85
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: MADT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd61c
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: BOOT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd678
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Processor #0 15:2 APIC version 20
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 22 15:47:46 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Dec 22 15:47:46 ubuntu kernel: [    0.000000] Detected 2386.645 MHz processor.
Dec 22 15:47:46 ubuntu kernel: [   13.789255] Built 1 zonelists.  Total pages: 129913
Dec 22 15:47:46 ubuntu kernel: [   13.789261] Kernel command line: find=/wubi/boot/linux ro quiet splash
Dec 22 15:47:46 ubuntu kernel: [   13.789454] mapped APIC to ffffd000 (fee00000)
Dec 22 15:47:46 ubuntu kernel: [   13.789457] mapped IOAPIC to ffffc000 (fec00000)
Dec 22 15:47:46 ubuntu kernel: [   13.789461] Enabling fast FPU save and restore... done.
Dec 22 15:47:46 ubuntu kernel: [   13.789465] Enabling unmasked SIMD FPU exception support... done.
Dec 22 15:47:46 ubuntu kernel: [   13.789478] Initializing CPU#0
Dec 22 15:47:46 ubuntu kernel: [   13.789566] PID hash table entries: 2048 (order: 11, 8192 bytes)
Dec 22 15:47:46 ubuntu kernel: [   13.791165] Console: colour VGA+ 80x25
Dec 22 15:47:46 ubuntu kernel: [   13.791525] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 15:47:46 ubuntu kernel: [   13.791870] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 15:47:46 ubuntu kernel: [   13.806056] Memory: 507576k/523740k available (1993k kernel code, 15596k reserved, 900k data, 328k init, 0k highmem)
Dec 22 15:47:46 ubuntu kernel: [   13.806067] virtual kernel memory layout:
Dec 22 15:47:47 ubuntu kernel: [   13.806068]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Dec 22 15:47:47 ubuntu kernel: [   13.806069]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 15:47:47 ubuntu kernel: [   13.806070]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Dec 22 15:47:47 ubuntu kernel: [   13.806072]     lowmem  : 0xc0000000 - 0xdff77000   ( 511 MB)
Dec 22 15:47:47 ubuntu kernel: [   13.806073]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Dec 22 15:47:47 ubuntu kernel: [   13.806074]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
Dec 22 15:47:47 ubuntu kernel: [   13.806075]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
Dec 22 15:47:47 ubuntu kernel: [   13.806079] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 22 15:47:47 ubuntu kernel: [   13.885562] Calibrating delay using timer specific routine.. 4777.34 BogoMIPS (lpj=9554692)
Dec 22 15:47:47 ubuntu kernel: [   13.885611] Security Framework v1.0.0 initialized
Dec 22 15:47:47 ubuntu kernel: [   13.885620] SELinux:  Disabled at boot.
Dec 22 15:47:47 ubuntu kernel: [   13.885640] Mount-cache hash table entries: 512
Dec 22 15:47:47 ubuntu kernel: [   13.885810] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
Dec 22 15:47:47 ubuntu kernel: [   13.885824] CPU: Trace cache: 12K uops, L1 D cache: 8K
Dec 22 15:47:47 ubuntu kernel: [   13.885827] CPU: L2 cache: 512K
Dec 22 15:47:47 ubuntu kernel: [   13.885830] CPU: Hyper-Threading is disabled
Dec 22 15:47:47 ubuntu kernel: [   13.885832] CPU: After all inits, caps: 3febfbff 00000000 00000000 00003080 00000000 00000000 00000000
Dec 22 15:47:47 ubuntu kernel: [   13.885845] Compat vDSO mapped to ffffe000.
Dec 22 15:47:47 ubuntu kernel: [   13.885849] Remapping vsyscall page to ffffe000
Dec 22 15:47:47 ubuntu kernel: [   13.885863] Checking 'hlt' instruction... OK.
Dec 22 15:47:47 ubuntu kernel: [   13.901708] SMP alternatives: switching to UP code
Dec 22 15:47:47 ubuntu kernel: [   13.901946] Freeing SMP alternatives: 11k freed
Dec 22 15:47:47 ubuntu kernel: [   13.902200] Early unpacking initramfs... done
Dec 22 15:47:47 ubuntu kernel: [   14.273552] ACPI: Core revision 20060707
Dec 22 15:47:47 ubuntu kernel: [   14.279697] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Dec 22 15:47:47 ubuntu kernel: [   14.302391] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
Dec 22 15:47:47 ubuntu kernel: [   14.302435] Total of 1 processors activated (4777.34 BogoMIPS).
Dec 22 15:47:47 ubuntu kernel: [   14.302573] ENABLING IO-APIC IRQs
Dec 22 15:47:47 ubuntu kernel: [   14.302759] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 22 15:47:47 ubuntu kernel: [   14.449549] Brought up 1 CPUs
Dec 22 15:47:47 ubuntu kernel: [   14.449838] Booting paravirtualized kernel on bare hardware
Dec 22 15:47:47 ubuntu kernel: [   14.449921] Time: 15:47:02  Date: 11/22/107
Dec 22 15:47:47 ubuntu kernel: [   14.449952] NET: Registered protocol family 16
Dec 22 15:47:47 ubuntu kernel: [   14.450056] EISA bus registered
Dec 22 15:47:47 ubuntu kernel: [   14.450062] ACPI: bus type pci registered
Dec 22 15:47:47 ubuntu kernel: [   14.476226] PCI: PCI BIOS revision 2.10 entry at 0xfbeae, last bus=2
Dec 22 15:47:47 ubuntu kernel: [   14.476229] PCI: Using configuration type 1
Dec 22 15:47:47 ubuntu kernel: [   14.476231] Setting up standard PCI resources
Dec 22 15:47:47 ubuntu kernel: [   14.498480] ACPI: Interpreter enabled
Dec 22 15:47:47 ubuntu kernel: [   14.498483] ACPI: Using IOAPIC for interrupt routing
Dec 22 15:47:47 ubuntu kernel: [   14.503084] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 22 15:47:47 ubuntu kernel: [   14.503094] PCI: Probing PCI hardware (bus 00)
Dec 22 15:47:47 ubuntu kernel: [   14.503116] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Dec 22 15:47:47 ubuntu kernel: [   14.503337] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Dec 22 15:47:47 ubuntu kernel: [   14.503342] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Dec 22 15:47:47 ubuntu kernel: [   14.503635] Boot video device is 0000:01:00.0
Dec 22 15:47:47 ubuntu kernel: [   14.504068] PCI: Transparent bridge - 0000:00:1e.0
Dec 22 15:47:47 ubuntu kernel: [   14.504097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 22 15:47:47 ubuntu kernel: [   14.599530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Dec 22 15:47:47 ubuntu kernel: [   14.616310] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 9 10 11 12 15)
Dec 22 15:47:47 ubuntu kernel: [   14.617098] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Dec 22 15:47:47 ubuntu kernel: [   14.617886] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Dec 22 15:47:47 ubuntu kernel: [   14.618658] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Dec 22 15:47:47 ubuntu kernel: [   14.619459] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Dec 22 15:47:47 ubuntu kernel: [   14.620255] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Dec 22 15:47:47 ubuntu kernel: [   14.621049] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Dec 22 15:47:47 ubuntu kernel: [   14.621837] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Dec 22 15:47:47 ubuntu kernel: [   14.622008] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 22 15:47:47 ubuntu kernel: [   14.622023] pnp: PnP ACPI init
Dec 22 15:47:47 ubuntu kernel: [   14.649190] pnp: PnP ACPI: found 11 devices
Dec 22 15:47:47 ubuntu kernel: [   14.649196] PnPBIOS: Disabled by ACPI PNP
Dec 22 15:47:47 ubuntu kernel: [   14.649257] PCI: Using ACPI for IRQ routing
Dec 22 15:47:47 ubuntu kernel: [   14.649260] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 22 15:47:47 ubuntu kernel: [   14.656284] NET: Registered protocol family 8
Dec 22 15:47:47 ubuntu kernel: [   14.656287] NET: Registered protocol family 20
Dec 22 15:47:47 ubuntu kernel: [   14.663206] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
Dec 22 15:47:47 ubuntu kernel: [   14.663210] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
Dec 22 15:47:47 ubuntu kernel: [   14.663213] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
Dec 22 15:47:47 ubuntu kernel: [   14.663552] PCI: Bridge: 0000:00:01.0
Dec 22 15:47:47 ubuntu kernel: [   14.663554]   IO window: disabled.
Dec 22 15:47:47 ubuntu kernel: [   14.663559]   MEM window: fc000000-fdffffff
Dec 22 15:47:47 ubuntu kernel: [   14.663563]   PREFETCH window: f0000000-f7ffffff
Dec 22 15:47:47 ubuntu kernel: [   14.663568] PCI: Bridge: 0000:00:1e.0
Dec 22 15:47:47 ubuntu kernel: [   14.663571]   IO window: e000-efff
Dec 22 15:47:47 ubuntu kernel: [   14.663577]   MEM window: fe100000-fe3fffff
Dec 22 15:47:47 ubuntu kernel: [   14.663582]   PREFETCH window: 30000000-300fffff
Dec 22 15:47:47 ubuntu kernel: [   14.663601] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Dec 22 15:47:47 ubuntu kernel: [   14.663636] NET: Registered protocol family 2
Dec 22 15:47:47 ubuntu kernel: [   14.701571] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 22 15:47:47 ubuntu kernel: [   14.701668] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Dec 22 15:47:47 ubuntu kernel: [   14.701759] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Dec 22 15:47:47 ubuntu kernel: [   14.701806] TCP: Hash tables configured (established 16384 bind 8192)
Dec 22 15:47:47 ubuntu kernel: [   14.701809] TCP reno registered
Dec 22 15:47:47 ubuntu kernel: [   14.713620] checking if image is initramfs... it is
Dec 22 15:47:47 ubuntu kernel: [   15.447418] Freeing initrd memory: 7397k freed
Dec 22 15:47:47 ubuntu kernel: [   15.447633] Simple Boot Flag at 0x7a set to 0x1
Dec 22 15:47:47 ubuntu kernel: [   15.447895] audit: initializing netlink socket (disabled)
Dec 22 15:47:47 ubuntu kernel: [   15.447910] audit(1198338422.740:1): initialized
Dec 22 15:47:47 ubuntu kernel: [   15.448078] VFS: Disk quotas dquot_6.5.1
Dec 22 15:47:47 ubuntu kernel: [   15.448105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 15:47:47 ubuntu kernel: [   15.448161] io scheduler noop registered
Dec 22 15:47:47 ubuntu kernel: [   15.448165] io scheduler anticipatory registered
Dec 22 15:47:47 ubuntu kernel: [   15.448168] io scheduler deadline registered
Dec 22 15:47:47 ubuntu kernel: [   15.448181] io scheduler cfq registered (default)
Dec 22 15:47:47 ubuntu kernel: [   15.448483] isapnp: Scanning for PnP cards...
Dec 22 15:47:47 ubuntu kernel: [   15.802555] isapnp: No Plug & Play device found
Dec 22 15:47:47 ubuntu kernel: [   15.832677] Real Time Clock Driver v1.12ac
Dec 22 15:47:47 ubuntu kernel: [   15.832731] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 22 15:47:47 ubuntu kernel: [   15.832855] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 22 15:47:47 ubuntu kernel: [   15.833798] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 22 15:47:47 ubuntu kernel: [   15.834103] mice: PS/2 mouse device common for all mice
Dec 22 15:47:47 ubuntu kernel: [   15.834786] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 22 15:47:47 ubuntu kernel: [   15.835066] input: Macintosh mouse button emulation as /class/input/input0
Dec 22 15:47:47 ubuntu kernel: [   15.835110] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 22 15:47:47 ubuntu kernel: [   15.835115] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 22 15:47:47 ubuntu kernel: [   15.835369] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
Dec 22 15:47:47 ubuntu kernel: [   15.835373] PNP: PS/2 controller doesn't have AUX irq; using default 12
Dec 22 15:47:47 ubuntu kernel: [   15.838816] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 15:47:47 ubuntu kernel: [   15.838825] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 22 15:47:47 ubuntu kernel: [   15.839014] EISA: Probing bus 0 at eisa.0
Dec 22 15:47:47 ubuntu kernel: [   15.839053] EISA: Detected 0 cards.
Dec 22 15:47:47 ubuntu kernel: [   15.869163] TCP cubic registered
Dec 22 15:47:47 ubuntu kernel: [   15.869172] NET: Registered protocol family 1
Dec 22 15:47:47 ubuntu kernel: [   15.869201] Using IPI No-Shortcut mode
Dec 22 15:47:47 ubuntu kernel: [   15.869276] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 15:47:47 ubuntu kernel: [   15.869329]   Magic number: 3:517:791
Dec 22 15:47:47 ubuntu kernel: [   15.869347] Time: tsc clocksource has been installed.
Dec 22 15:47:47 ubuntu kernel: [   15.869919] Freeing unused kernel memory: 328k freed
Dec 22 15:47:47 ubuntu kernel: [   15.882571] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 22 15:47:47 ubuntu kernel: [   17.139845] md: raid1 personality registered for level 1
Dec 22 15:47:47 ubuntu kernel: [   17.144361] md: raid0 personality registered for level 0
Dec 22 15:47:47 ubuntu kernel: [   17.150712] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
Dec 22 15:47:47 ubuntu kernel: [   17.170070] SCSI subsystem initialized
Dec 22 15:47:47 ubuntu kernel: [   17.177109] libata version 2.20 loaded.
Dec 22 15:47:47 ubuntu kernel: [   17.197444] usbcore: registered new interface driver usbfs
Dec 22 15:47:47 ubuntu kernel: [   17.197494] usbcore: registered new interface driver hub
Dec 22 15:47:47 ubuntu kernel: [   17.197538] usbcore: registered new device driver usb
Dec 22 15:47:47 ubuntu kernel: [   17.198846] ACPI: PCI Interrupt 0000:02:0a.2[C] -> GSI 17 (level, low) -> IRQ 16
Dec 22 15:47:47 ubuntu kernel: [   17.198860] ehci_hcd 0000:02:0a.2: EHCI Host Controller
Dec 22 15:47:47 ubuntu kernel: [   17.198922] ehci_hcd 0000:02:0a.2: new USB bus registered, assigned bus number 1
Dec 22 15:47:47 ubuntu kernel: [   17.225181] ehci_hcd 0000:02:0a.2: irq 16, io mem 0xfe2ff400
Dec 22 15:47:47 ubuntu kernel: [   17.225189] ehci_hcd 0000:02:0a.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Dec 22 15:47:47 ubuntu kernel: [   17.225353] usb usb1: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   17.225402] hub 1-0:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   17.225411] hub 1-0:1.0: 5 ports detected
Dec 22 15:47:47 ubuntu kernel: [   17.338037] USB Universal Host Controller Interface driver v3.0
Dec 22 15:47:47 ubuntu kernel: [   17.338123] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 17
Dec 22 15:47:47 ubuntu kernel: [   17.338137] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Dec 22 15:47:47 ubuntu kernel: [   17.338142] uhci_hcd 0000:00:1f.2: UHCI Host Controller
Dec 22 15:47:47 ubuntu kernel: [   17.338193] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 2
Dec 22 15:47:47 ubuntu kernel: [   17.338222] uhci_hcd 0000:00:1f.2: irq 17, io base 0x0000ff80
Dec 22 15:47:47 ubuntu kernel: [   17.338376] usb usb2: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   17.338430] hub 2-0:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   17.338439] hub 2-0:1.0: 2 ports detected
Dec 22 15:47:47 ubuntu kernel: [   17.445278] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 18
Dec 22 15:47:47 ubuntu kernel: [   17.445288] PCI: Setting latency timer of device 0000:00:1f.4 to 64
Dec 22 15:47:47 ubuntu kernel: [   17.445293] uhci_hcd 0000:00:1f.4: UHCI Host Controller
Dec 22 15:47:47 ubuntu kernel: [   17.445336] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 3
Dec 22 15:47:47 ubuntu kernel: [   17.445360] uhci_hcd 0000:00:1f.4: irq 18, io base 0x0000ff60
Dec 22 15:47:47 ubuntu kernel: [   17.445497] usb usb3: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   17.445543] hub 3-0:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   17.445552] hub 3-0:1.0: 2 ports detected
Dec 22 15:47:47 ubuntu kernel: [   17.557834] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 22 15:47:47 ubuntu kernel: [   17.557902] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 17
Dec 22 15:47:47 ubuntu kernel: [   17.557916] ohci_hcd 0000:02:0a.0: OHCI Host Controller
Dec 22 15:47:47 ubuntu kernel: [   17.557969] ohci_hcd 0000:02:0a.0: new USB bus registered, assigned bus number 4
Dec 22 15:47:47 ubuntu kernel: [   17.557987] ohci_hcd 0000:02:0a.0: irq 17, io mem 0xfe2fd000
Dec 22 15:47:47 ubuntu kernel: [   17.581173] usb 1-1: new high speed USB device using ehci_hcd and address 2
Dec 22 15:47:47 ubuntu kernel: [   18.123770] usb usb4: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   18.123820] hub 4-0:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   18.123831] hub 4-0:1.0: 3 ports detected
Dec 22 15:47:47 ubuntu kernel: [   18.208268] usb 1-1: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   18.457032] usb 1-2: new high speed USB device using ehci_hcd and address 3
Dec 22 15:47:47 ubuntu kernel: [   18.602835] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   18.641127] ACPI: PCI Interrupt 0000:02:0a.1[B] -> GSI 16 (level, low) -> IRQ 19
Dec 22 15:47:47 ubuntu kernel: [   18.641142] ohci_hcd 0000:02:0a.1: OHCI Host Controller
Dec 22 15:47:47 ubuntu kernel: [   18.641184] ohci_hcd 0000:02:0a.1: new USB bus registered, assigned bus number 5
Dec 22 15:47:47 ubuntu kernel: [   18.641199] ohci_hcd 0000:02:0a.1: irq 19, io mem 0xfe2fc000
Dec 22 15:47:47 ubuntu kernel: [   19.207571] usb usb5: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   19.207620] hub 5-0:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   19.207631] hub 5-0:1.0: 2 ports detected
Dec 22 15:47:47 ubuntu kernel: [   19.324920] usb 1-3: new high speed USB device using ehci_hcd and address 4
Dec 22 15:47:47 ubuntu kernel: [   19.470204] usb 1-3: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   19.470396] hub 1-3:1.0: USB hub found
Dec 22 15:47:47 ubuntu kernel: [   19.470477] hub 1-3:1.0: 4 ports detected
Dec 22 15:47:47 ubuntu kernel: [   19.820861] usb 2-1: new low speed USB device using uhci_hcd and address 2
Dec 22 15:47:47 ubuntu kernel: [   20.004507] usb 2-1: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   20.229741] usb 1-3.4: new high speed USB device using ehci_hcd and address 5
Dec 22 15:47:47 ubuntu kernel: [   20.335339] usb 1-3.4: configuration #1 chosen from 1 choice
Dec 22 15:47:47 ubuntu kernel: [   20.335744] usbcore: registered new interface driver libusual
Dec 22 15:47:47 ubuntu kernel: [   20.343725] Initializing USB Mass Storage driver...
Dec 22 15:47:47 ubuntu kernel: [   20.344074] scsi0 : SCSI emulation for USB Mass Storage devices
Dec 22 15:47:47 ubuntu kernel: [   20.344157] usb-storage: device found at 2
Dec 22 15:47:48 ubuntu kernel: [   20.344160] usb-storage: waiting for device to settle before scanning
Dec 22 15:47:48 ubuntu kernel: [   20.344206] scsi1 : SCSI emulation for USB Mass Storage devices
Dec 22 15:47:48 ubuntu kernel: [   20.344271] usb-storage: device found at 3
Dec 22 15:47:48 ubuntu kernel: [   20.344273] usb-storage: waiting for device to settle before scanning
Dec 22 15:47:48 ubuntu kernel: [   20.344323] scsi2 : SCSI emulation for USB Mass Storage devices
Dec 22 15:47:48 ubuntu kernel: [   20.344384] usb-storage: device found at 5
Dec 22 15:47:48 ubuntu kernel: [   20.344386] usb-storage: waiting for device to settle before scanning
Dec 22 15:47:48 ubuntu kernel: [   20.344396] usbcore: registered new interface driver usb-storage
Dec 22 15:47:48 ubuntu kernel: [   20.344399] USB Mass Storage support registered.
Dec 22 15:47:48 ubuntu kernel: [   20.359967] ata_piix 0000:00:1f.1: version 2.10ac1
Dec 22 15:47:48 ubuntu kernel: [   20.360002] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Dec 22 15:47:48 ubuntu kernel: [   20.360042] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Dec 22 15:47:48 ubuntu kernel: [   20.360086] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Dec 22 15:47:48 ubuntu kernel: [   20.360109] scsi3 : ata_piix
Dec 22 15:47:48 ubuntu kernel: [   20.529835] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156301488
Dec 22 15:47:48 ubuntu kernel: [   20.529841] ata1.00: Host Protected Area detected.
Dec 22 15:47:48 ubuntu kernel: [   20.529843]      current size : 156250000 sectors (80000 MB)
Dec 22 15:47:48 ubuntu kernel: [   20.529844]      native  size : 156301488 sectors (80026 MB)
Dec 22 15:47:48 ubuntu kernel: [   20.540969] ata1.00: Native size increased to 156301488 sectors
Dec 22 15:47:48 ubuntu kernel: [   20.540973] ata1.00: ATA-5: WDC WD800BB-75CAA0, 16.06V16, max UDMA/100
Dec 22 15:47:48 ubuntu kernel: [   20.540976] ata1.00: 156301488 sectors, multi 8: LBA 
Dec 22 15:47:48 ubuntu kernel: [   20.553846] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Dec 22 15:47:48 ubuntu kernel: [   20.553849] ata1.00: configured for UDMA/100
Dec 22 15:47:48 ubuntu kernel: [   20.553857] scsi4 : ata_piix
Dec 22 15:47:48 ubuntu kernel: [   21.045017] ata2.00: ATAPI, max UDMA/33
Dec 22 15:47:48 ubuntu kernel: [   21.045020] ata2.01: ATAPI, max UDMA/33
Dec 22 15:47:48 ubuntu kernel: [   21.204991] ata2.00: configured for UDMA/33
Dec 22 15:47:48 ubuntu kernel: [   21.376922] ata2.01: configured for UDMA/33
Dec 22 15:47:48 ubuntu kernel: [   21.377045] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800BB-75CA 16.0 PQ: 0 ANSI: 5
Dec 22 15:47:48 ubuntu kernel: [   21.377170] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Dec 22 15:47:48 ubuntu kernel: [   21.377184] sda: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   21.377187] sda: Mode Sense: 00 3a 00 00
Dec 22 15:47:48 ubuntu kernel: [   21.377207] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 15:47:48 ubuntu kernel: [   21.377262] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Dec 22 15:47:48 ubuntu kernel: [   21.377274] sda: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   21.377276] sda: Mode Sense: 00 3a 00 00
Dec 22 15:47:48 ubuntu kernel: [   21.377296] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 15:47:48 ubuntu kernel: [   21.377299]  sda: sda1
Dec 22 15:47:48 ubuntu kernel: [   21.395206] sd 3:0:0:0: Attached scsi disk sda
Dec 22 15:47:48 ubuntu kernel: [   21.403965] scsi 4:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F308 PQ: 0 ANSI: 5
Dec 22 15:47:48 ubuntu kernel: [   21.405676] scsi 4:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  BD11 PQ: 0 ANSI: 5
Dec 22 15:47:48 ubuntu kernel: [   21.549556] JFS: nTxBlock = 4027, nTxLock = 32218
Dec 22 15:47:48 ubuntu kernel: [   21.563121] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Dec 22 15:47:48 ubuntu kernel: [   21.563321] SGI XFS Quota Management subsystem
Dec 22 15:47:48 ubuntu kernel: [   21.593069] NTFS driver 2.1.28 [Flags: R/O MODULE].
Dec 22 15:47:48 ubuntu kernel: [   21.603224] fuse init (API version 7.8)
Dec 22 15:47:48 ubuntu kernel: [   21.609647] loop: loaded (max 8 devices)
Dec 22 15:47:48 ubuntu kernel: [   21.615869] Registering unionfs 20060916-2203
Dec 22 15:47:48 ubuntu kernel: [   21.615873] unionfs: debugging is not enabled
Dec 22 15:47:48 ubuntu kernel: [   21.621703] squashfs: version 3.2-UBUNTU (2007/08/29) Phillip Lougher
Dec 22 15:47:48 ubuntu kernel: [   21.651742] Capability LSM initialized
Dec 22 15:47:48 ubuntu kernel: [   22.456672] sd 3:0:0:0: Attached scsi generic sg0 type 0
Dec 22 15:47:48 ubuntu kernel: [   22.456697] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Dec 22 15:47:48 ubuntu kernel: [   22.456719] scsi 4:0:1:0: Attached scsi generic sg2 type 5
Dec 22 15:47:48 ubuntu kernel: [   22.518673] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Dec 22 15:47:48 ubuntu kernel: [   22.518714] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Dec 22 15:47:48 ubuntu kernel: [   22.518717] 8139cp 0000:02:07.0: Try the "8139too" driver instead.
Dec 22 15:47:48 ubuntu kernel: [   22.520651] 8139too Fast Ethernet driver 0.9.28
Dec 22 15:47:48 ubuntu kernel: [   22.520703] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 19
Dec 22 15:47:48 ubuntu kernel: [   22.521023] eth0: RealTek RTL8139 at 0xe0d2ac00, 00:c0:a8:86:c9:c8, IRQ 19
Dec 22 15:47:48 ubuntu kernel: [   22.521026] eth0:  Identified 8139 chip type 'RTL-8139C'
Dec 22 15:47:48 ubuntu kernel: [   22.531706] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 16
Dec 22 15:47:48 ubuntu kernel: [   22.531716] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
Dec 22 15:47:48 ubuntu kernel: [   22.531722] 0000:02:08.0: 3Com PCI 3c905C Tornado at e0d4a800.
Dec 22 15:47:48 ubuntu kernel: [   22.593132] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
Dec 22 15:47:48 ubuntu kernel: [   22.593138] Uniform CD-ROM driver Revision: 3.20
Dec 22 15:47:48 ubuntu kernel: [   22.593208] sr 4:0:0:0: Attached scsi CD-ROM sr0
Dec 22 15:47:48 ubuntu kernel: [   22.655648] Floppy drive(s): fd0 is 1.44M
Dec 22 15:47:48 ubuntu kernel: [   22.703114] usbcore: registered new interface driver hiddev
Dec 22 15:47:48 ubuntu kernel: [   22.728600] FDC 0 is a post-1991 82077
Dec 22 15:47:48 ubuntu kernel: [   22.742475] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Dec 22 15:47:48 ubuntu kernel: [   22.742556] sr 4:0:1:0: Attached scsi CD-ROM sr1
Dec 22 15:47:48 ubuntu kernel: [   22.843145] input: Logitech USB Optical Mouse as /class/input/input2
Dec 22 15:47:48 ubuntu kernel: [   22.843174] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1f.2-1
Dec 22 15:47:48 ubuntu kernel: [   22.843193] usbcore: registered new interface driver usbhid
Dec 22 15:47:48 ubuntu kernel: [   22.843197] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Dec 22 15:47:48 ubuntu kernel: [   23.793348] kjournald starting.  Commit interval 5 seconds
Dec 22 15:47:48 ubuntu kernel: [   23.793364] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 15:47:48 ubuntu kernel: [   23.890505] EXT3 FS on loop0, internal journal
Dec 22 15:47:48 ubuntu kernel: [   25.344247] usb-storage: device scan complete
Dec 22 15:47:48 ubuntu kernel: [   25.344980] usb-storage: device scan complete
Dec 22 15:47:48 ubuntu kernel: [   25.345353] usb-storage: device scan complete
Dec 22 15:47:48 ubuntu kernel: [   25.345434] scsi 1:0:0:0: Direct-Access     SEAGATE  ST3250823A       3.03 PQ: 0 ANSI: 2
Dec 22 15:47:48 ubuntu kernel: [   25.345489] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
Dec 22 15:47:48 ubuntu kernel: [   25.346236] scsi 0:0:0:0: Direct-Access     Canon    MP500Storage     0109 PQ: 0 ANSI: 2
Dec 22 15:47:48 ubuntu kernel: [   25.346839] SCSI device sdb: 2006673 512-byte hdwr sectors (1027 MB)
Dec 22 15:47:48 ubuntu kernel: [   25.347461] sdb: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   25.347464] sdb: Mode Sense: 03 00 00 00
Dec 22 15:47:48 ubuntu kernel: [   25.347466] sdb: assuming drive cache: write through
Dec 22 15:47:48 ubuntu kernel: [   25.349863] SCSI device sdb: 2006673 512-byte hdwr sectors (1027 MB)
Dec 22 15:47:48 ubuntu kernel: [   25.350461] sdb: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   25.350464] sdb: Mode Sense: 03 00 00 00
Dec 22 15:47:48 ubuntu kernel: [   25.350466] sdb: assuming drive cache: write through
Dec 22 15:47:48 ubuntu kernel: [   25.350470]  sdb: sdb1
Dec 22 15:47:48 ubuntu kernel: [   25.354927] sd 2:0:0:0: Attached scsi removable disk sdb
Dec 22 15:47:48 ubuntu kernel: [   25.354976] sd 2:0:0:0: Attached scsi generic sg3 type 0
Dec 22 15:47:48 ubuntu kernel: [   25.355836] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Dec 22 15:47:48 ubuntu kernel: [   25.356712] sdc: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   25.356715] sdc: Mode Sense: 53 00 00 08
Dec 22 15:47:48 ubuntu kernel: [   25.356718] sdc: assuming drive cache: write through
Dec 22 15:47:48 ubuntu kernel: [   25.357591] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Dec 22 15:47:48 ubuntu kernel: [   25.358461] sdc: Write Protect is off
Dec 22 15:47:48 ubuntu kernel: [   25.358464] sdc: Mode Sense: 53 00 00 08
Dec 22 15:47:48 ubuntu kernel: [   25.358466] sdc: assuming drive cache: write through
Dec 22 15:47:48 ubuntu kernel: [   25.358470]  sdc: sdc1
Dec 22 15:47:48 ubuntu kernel: [   25.376435] sd 1:0:0:0: Attached scsi disk sdc
Dec 22 15:47:48 ubuntu kernel: [   25.376484] sd 1:0:0:0: Attached scsi generic sg4 type 0
Dec 22 15:47:48 ubuntu kernel: [   25.379128] sd 0:0:0:0: Attached scsi removable disk sdd
Dec 22 15:47:48 ubuntu kernel: [   25.379163] sd 0:0:0:0: Attached scsi generic sg5 type 0
Dec 22 15:47:48 ubuntu kernel: [   37.287873] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Dec 22 15:47:48 ubuntu kernel: [   38.688022] NET: Registered protocol family 17
Dec 22 15:47:48 ubuntu kernel: [   39.365361] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 15:47:48 ubuntu kernel: [   39.390740] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 15:47:48 ubuntu kernel: [   39.781922] Linux agpgart interface v0.102 (c) Dave Jones
Dec 22 15:47:48 ubuntu kernel: [   39.788685] agpgart: Detected an Intel i850 Chipset.
Dec 22 15:47:48 ubuntu kernel: [   39.794764] agpgart: AGP aperture is 128M @ 0xe8000000
Dec 22 15:47:48 ubuntu kernel: [   40.226620] iTCO_vendor_support: vendor-support=0
Dec 22 15:47:48 ubuntu kernel: [   40.229015] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Dec 22 15:47:48 ubuntu kernel: [   40.229114] iTCO_wdt: [COLOR="Red"]failed[/COLOR] to reset NO_REBOOT flag, reboot disabled by hardware
Dec 22 15:47:48 ubuntu kernel: [   40.229122] iTCO_wdt: No card detected
Dec 22 15:47:48 ubuntu kernel: [   40.281379] Intel 82802 RNG detected
Dec 22 15:47:48 ubuntu kernel: [   40.478779] input: PC Speaker as /class/input/input3
Dec 22 15:47:48 ubuntu kernel: [   40.524034] nvidia: module license 'NVIDIA' taints kernel.
Dec 22 15:47:48 ubuntu kernel: [   40.786246] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
Dec 22 15:47:48 ubuntu kernel: [   40.786587] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Dec 22 15:47:48 ubuntu kernel: [   41.174455] parport: PnPBIOS parport detected.
Dec 22 15:47:48 ubuntu kernel: [   41.174509] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Dec 22 15:47:48 ubuntu kernel: [   41.235708] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x170C
Dec 22 15:47:48 ubuntu kernel: [   41.235725] usbcore: registered new interface driver usblp
Dec 22 15:47:48 ubuntu kernel: [   41.235729] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Dec 22 15:47:48 ubuntu kernel: [   41.645855] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 20
Dec 22 15:47:48 ubuntu kernel: [   44.728413] gameport: CS46xx Gameport is pci0000:02:09.0/gameport0, speed 1242kHz
Dec 22 15:47:48 ubuntu kernel: [   44.879401] lp0: using parport0 (interrupt-driven).
Dec 22 15:47:48 ubuntu kernel: [   45.074439] EXT3 FS on loop0, internal journal
Dec 22 15:47:48 ubuntu kernel: [   45.932088] NET: Registered protocol family 10
Dec 22 15:47:48 ubuntu kernel: [   45.932216] lo: Disabled Privacy Extensions
Dec 22 15:47:48 ubuntu kernel: [   46.783577] kjournald starting.  Commit interval 5 seconds
Dec 22 15:47:48 ubuntu kernel: [   46.783922] EXT3 FS on loop1, internal journal
Dec 22 15:47:48 ubuntu kernel: [   46.783928] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 15:47:48 ubuntu kernel: [   54.060615] Adding 499012k swap on /media/host/wubi/disks/swap.virtual.disk.  Priority:-1 extents:2 across:16013108k
Dec 22 15:47:48 ubuntu kernel: [   55.968464] eth0: no IPv6 routers present
Dec 22 15:47:48 ubuntu kernel: [   57.146725] No dock devices found.
Dec 22 15:47:48 ubuntu kernel: [   57.212586] Using specific hotkey driver
Dec 22 15:47:48 ubuntu kernel: [   57.485179] input: Power Button (FF) as /class/input/input4
Dec 22 15:47:48 ubuntu kernel: [   57.490016] ACPI: Power Button (FF) [PWRF]
Dec 22 15:47:48 ubuntu kernel: [   57.533013] input: Power Button (CM) as /class/input/input5
Dec 22 15:47:48 ubuntu kernel: [   57.537845] ACPI: Power Button (CM) [VBTN]
Dec 22 15:47:48 ubuntu kernel: [   57.559645] ibm_acpi: ec object not found
Dec 22 15:47:48 ubuntu kernel: [   57.619542] pcc_acpi: loading...
Dec 22 15:47:52 ubuntu kernel: [   64.867758] eth1:  setting half-duplex.
Dec 22 15:47:52 ubuntu kernel: [   64.868182] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 15:47:56 ubuntu kernel: [   68.760546] ppdev: user-space parallel port driver
Dec 22 15:48:01 ubuntu kernel: [   75.202054] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 22 15:48:02 ubuntu kernel: [   75.202060] apm: overridden by ACPI.
Dec 22 15:48:02 ubuntu kernel: [   76.042639] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 22 15:48:02 ubuntu kernel: [   76.042658] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 22 15:48:02 ubuntu kernel: [   76.042678] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 22 15:48:03 ubuntu kernel: [   77.310420] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Dec 22 15:48:04 ubuntu kernel: [   77.837943] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec 22 15:48:04 ubuntu kernel: [   77.904147] NFSD: starting 90-second grace period
Dec 22 15:48:08 ubuntu kernel: [   82.165277] eth0: no IPv6 routers present
Dec 22 15:48:18 ubuntu kernel: [   91.570299] Bluetooth: Core ver 2.11
Dec 22 15:48:18 ubuntu kernel: [   91.570707] NET: Registered protocol family 31
Dec 22 15:48:18 ubuntu kernel: [   91.570710] Bluetooth: HCI device and connection manager initialized
Dec 22 15:48:18 ubuntu kernel: [   91.570714] Bluetooth: HCI socket layer initialized
Dec 22 15:48:18 ubuntu kernel: [   91.686639] Bluetooth: L2CAP ver 2.8
Dec 22 15:48:18 ubuntu kernel: [   91.686644] Bluetooth: L2CAP socket layer initialized
Dec 22 15:48:18 ubuntu kernel: [   91.862883] Bluetooth: RFCOMM socket layer initialized
Dec 22 15:48:18 ubuntu kernel: [   91.862898] Bluetooth: RFCOMM TTY layer initialized
Dec 22 15:48:18 ubuntu kernel: [   91.862901] Bluetooth: RFCOMM ver 1.8
Dec 22 15:48:20 ubuntu kernel: [   94.200503] device lo entered promiscuous mode
Dec 22 15:48:20 ubuntu kernel: [   94.200516] audit(1198356500.788:2): dev=lo prom=256 old_prom=0 auid=4294967295
Dec 22 15:48:20 ubuntu kernel: [   94.212503] device eth0 entered promiscuous mode
Dec 22 15:48:20 ubuntu kernel: [   94.212516] audit(1198356500.800:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
Dec 22 15:57:58 ubuntu kernel: [  671.717480] usb 1-3.4: USB disconnect, address 5


---

### Post by dfault312 on 2007-12-24
yeah, i didnt see anything about hald in either of those, but i figured maybe there is something else related that i didnt know about. i highlighted everything that said "failed" in red. when i start hal in the terminal, it doesnt say "[ok]" from what i know of linux, it shouldnt have to, but since it says it for stopping, i would assume it should be there for starting as well?

> me@ubuntu:~$ sudo /etc/init.d/hal stop
[sudo] password for me:
 * Stopping Hardware abstraction layer hald                                       [ OK ]
me@ubuntu:~$ sudo /etc/init.d/hal start
 * Starting Hardware abstraction layer hald
me@ubuntu:~$ 


---

### Post by p_quarles on 2007-12-24
Hmm. No errors there.

Is there a possibility that the error message is a false alarm? I mean, if HAL wasn't working at all, you'd be experiencing problems with printing, plugging in USB drives -- basically any kind of hardware that you try to initialize after fully booting the system. Any problems like that?

If so, this is starting to look like something beyond my knowledge. The best advice I could offer at this point would be to add an item that initializes HAL to your session startup routine.

---

### Post by dfault312 on 2007-12-24
well, im able to print, but i am not able to find a USB disk, or my cd and dvd drives.... not that i use those very often anyway. my external hard drive shows up, but i cant access it because the owner is set as root... havent figured out how to change that yet, but im sure its pretty simple, i just havent gotten to it. thats another issue altogether. before i upgraded to 7.10 from 7.04 all of this stuff worked fine. before i upgraded there was a problem with GNOME locking up, but after i upgraded that went away and i started getting this HAL problem, and cant access my external hard drive. another thing that happened, and im not sure if this is related, is that when i click "quit" it takes forever for the logout/shutdown screen to appear. also, im not sure if it matters, but i have two ethernet cards and i am running LTSP. the internet and LAN cards both seem to be working fine (i have internet, and i can PXE boot my thin client), but there is an icon in my notification area that says "No Network Connection"

---

### Post by p_quarles on 2007-12-24
Okay, I just checked on Launchpad, and this seems to be a very persistent bug:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

This doesn't affect everyone, obviously, but it's happened to enough people to make this a "high" priority bug, two years after it was first reported. 

Anyway, I encourage you to add a comment to that bug report page. If you need any help setting up a startup script that will initialize HAL, don't hesitate to ask. Beyond that, I'm lost. ;)

---

### Post by groggyboy on 2007-12-30
i had this problem too.  your link to that bug report was helpful.  what fixed it for me was changing "CONCURRENCY" from "shell" back to "none" in "/etc/init.d/rc"

(posted here to maybe save someone some reading)

---

### Post by muggins on 2007-12-31
> **groggyboy said:**
> i had this problem too.  your link to that bug report was helpful.  what fixed it for me was changing "CONCURRENCY" from "shell" back to "none" in "/etc/init.d/rc"

(posted here to maybe save someone some reading)

Exactly how would I do this, I have the same message since upgrading as well.

---

### Post by p_quarles on 2007-12-31
> **muggins said:**
> Exactly how would I do this, I have the same message since upgrading as well.
Run this command:
```
gksudo gedit /etc/init.d/rc
```Find the line that begins with CONCURRENCY= (it's near the beginning of the file), and make sure it reads like so:
```
CONCURRENCY=none
```Save the file, and reboot.

---

### Post by mingster on 2008-01-06
yep, changing concurrency back to none worked for me

---

### Post by DreamerHxC on 2008-02-24
I have already tried all I have seen in this post: changing /etc/init.d/rc to none, uninstalling samba, rebooting a thousand times, etc., but I still can't access to my USB HD, and Ubuntu says I have no internet connection though I'm posting here, but I can't use pidgin because it says "waiting for connection".
What else can I do?

EDIT: OK, I solved the problem, the problem now is that I do not know how I did, but I think it could be because I installed via aptitude an application called preload, and it messed up all my system, couldn't be?

---

### Post by Guinness70 on 2008-03-05
> **p_quarles said:**
> What happens when you try to restart it? The installation process is try to start it, and may have encountered that error because it's already running (even though it "failed to initialize"). Anyway, give this a try:
```
sudo /etc/init.d/hal restart
```
If it doesn't work, post the output in your reply.
that code worked for me.

just reporting the events leading up to this error:
im on a amd64 and yday installed the (wrong) files for G15 keyb following the instructions on forum.
did a couple of restarts yday and worked fine
then surfed some more on here and discovered i installed the wrong version (not amd64)
couldnt redo coz im a noob and my linux helper already logged off.
hit hibernate, shut off power and went to bed.
today at reboot it gave "failed to hibernate"
and "internal error failed to initialize HAL"
couldnt get on internet with my puter so had to use the missus laptop

came on here and found this here thread.
for some reason a search for "failed to initialize hal" didnt give result (= the title of this thread afterall)
yet a search for "initialize hal" led me to this one

thanks!

---

