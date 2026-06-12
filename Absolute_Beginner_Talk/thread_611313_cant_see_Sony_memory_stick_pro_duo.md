---
title: "cant see Sony memory stick pro duo"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by bereta on 2007-11-12
Hello all

I have Ubuntu 7.10 and it can not see my 8 GB memory stick pro duo or any memory stick. Iv seen some posts by other people with the same problem and my question is :

Is this a driver problem or some kind of licensing problem since the makers of the memory stick is Sony.

I am running an Asus A8Js laptop that has a built in memory stick/SD card reader and that is what i am trying to read the cards with. By the way ubuntu can see SD cards no problem.

Thanks

---

### Post by infurnus on 2007-11-12
Is it not auto mounting or can you not find it to mount it?

---

### Post by bereta on 2007-11-12
Correct it is not auto mounting, and i did try to manualy mount it and i could not.

I am new to linux can some one tell me you exacty do i mount a drive it is seposto show up in the dev/sda derectory ?

---

### Post by infurnus on 2007-11-14
plug in the memory stick and open terminal and type
```

dmesg

```
post your output

---

### Post by scotthammy on 2008-01-14
000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515853
[    0.000000] Kernel command line: root=/dev/mapper/ubuntu-root ro quiet splash vga=792
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.132523] time.c: Detected 1800.081 MHz processor.
[   14.132569] Console: colour dummy device 80x25
[   14.132587] Checking aperture...
[   14.132591] CPU 0: aperture @ f88000000 size 32 MB
[   14.132593] Aperture too small (32 MB)
[   14.139483] No AGP bridge found
[   14.171787] Memory: 2055280k/2096960k available (2274k kernel code, 41292k reserved, 1181k data, 296k init)
[   14.171847] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.250350] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204094)
[   14.250392] Security Framework v1.0.0 initialized
[   14.250402] SELinux:  Disabled at boot.
[   14.250580] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   14.253059] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.254262] Mount-cache hash table entries: 256
[   14.254453] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.254456] CPU: L2 Cache: 512K (64 bytes/line)
[   14.254459] CPU 0/0 -> Node 0
[   14.254482] SMP alternatives: switching to UP code
[   14.254752] Freeing SMP alternatives: 24k freed
[   14.255224] Early unpacking initramfs... done
[   14.612435] ACPI: Core revision 20070126
[   14.612512] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.656895] Using local APIC timer interrupts.
[   14.712367] result 12500569
[   14.712369] Detected 12.500 MHz APIC timer.
[   14.713708] Brought up 1 CPUs
[   14.713917] NET: Registered protocol family 16
[   14.714007] ACPI: bus type pci registered
[   14.714014] PCI: Using configuration type 1
[   14.718846] ACPI: EC: Look up EC in DSDT
[   14.719754] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.752559] ACPI: Interpreter enabled
[   14.752562] ACPI: (supports S0 S1 S3 S4 S5)
[   14.752585] ACPI: Using IOAPIC for interrupt routing
[   14.760924] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.761052] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.761061] PCI: Probing PCI hardware (bus 00)
[   14.761892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.762070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.777832] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[   14.777993] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   14.778145] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   14.778299] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[   14.778450] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   14.778601] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 10 11 12 14 15)
[   14.778755] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[   14.778906] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   14.779051] ACPI: Power Resource [GFAN] (off)
[   14.779057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.779070] pnp: PnP ACPI init
[   14.779079] ACPI: bus type pnp registered
[   14.782218] pnp: PnP ACPI: found 14 devices
[   14.782221] ACPI: ACPI bus type pnp unregistered
[   14.782286] PCI: Using ACPI for IRQ routing
[   14.782289] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.782378] NET: Registered protocol family 8
[   14.782380] NET: Registered protocol family 20
[   14.782497] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[   14.782503] pnp: 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.782507] pnp: 00:0a: iomem range 0xffe80000-0xffefffff could not be reserved
[   14.782511] pnp: 00:0a: iomem range 0xffb80000-0xffbfffff could not be reserved
[   14.782514] pnp: 00:0a: iomem range 0xfed00000-0xfed003ff has been reserved
[   14.782519] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.782523] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.782528] pnp: 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   14.782532] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   14.782535] pnp: 00:0d: iomem range 0xc0000-0xcffff has been reserved
[   14.782538] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   14.782541] pnp: 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[   14.782822] PCI: Bridge: 0000:00:01.0
[   14.782823]   IO window: disabled.
[   14.782828]   MEM window: fa200000-fe2fffff
[   14.782832]   PREFETCH window: bde00000-ddefffff
[   14.782836] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   14.782839]   IO window: 00001000-000010ff
[   14.782842]   IO window: 00001400-000014ff
[   14.782846]   PREFETCH window: 88000000-8bffffff
[   14.782850]   MEM window: 8c000000-8fffffff
[   14.782869] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.782883] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.782928] NET: Registered protocol family 2
[   14.785562] Time: tsc clocksource has been installed.
[   14.821590] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.822489] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   14.829848] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.831033] TCP: Hash tables configured (established 262144 bind 65536)
[   14.831038] TCP reno registered
[   14.841635] checking if image is initramfs... it is
[   15.528902] Freeing initrd memory: 7961k freed
[   15.537892] audit: initializing netlink socket (disabled)
[   15.537907] audit(1200284834.332:1): initialized
[   15.539790] VFS: Disk quotas dquot_6.5.1
[   15.539848] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.539959] io scheduler noop registered
[   15.539962] io scheduler anticipatory registered
[   15.539964] io scheduler deadline registered
[   15.540058] io scheduler cfq registered (default)
[   15.540834] Boot video device is 0000:01:00.0
[   15.540982] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.541014] assign_interrupt_mode Found MSI capability
[   15.541017] Allocate Port Service[0000:00:01.0:pcie00]
[   15.564736] Real Time Clock Driver v1.12ac
[   15.564833] Linux agpgart interface v0.102 (c) Dave Jones
[   15.564835] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.565058] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   15.565461] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 18
[   15.565468] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   15.565992] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.566223] input: Macintosh mouse button emulation as /class/input/input0
[   15.566293] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.569530] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.570713] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.570718] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.570721] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.570724] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.570726] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.571013] mice: PS/2 mouse device common for all mice
[   15.571158] TCP cubic registered
[   15.571222] NET: Registered protocol family 1
[   15.571444] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.571453] Freeing unused kernel memory: 296k freed
[   15.636506] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.761126] AppArmor: AppArmor initialized<5>audit(1200284835.556:2):  type=1505 info="AppArmor initialized" pid=1217
[   16.767105] fuse init (API version 7.8)
[   16.771622] Failure registering capabilities with primary security module.
[   16.778241] ACPI: Transitioning device [FN00] to D3
[   16.778246] ACPI: Transitioning device [FN00] to D3
[   16.778250] ACPI: Fan [FN00] (off)
[   16.782696] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.782703] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.796934] ACPI: Thermal Zone [THRM] (33 C)
[   16.808634] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   17.395864] SCSI subsystem initialized
[   17.401308] libata version 2.21 loaded.
[   17.404815] pata_sis 0000:00:02.5: version 0.5.1
[   17.404994] scsi0 : pata_sis
[   17.405043] scsi1 : pata_sis
[   17.405145] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   17.405150] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   17.456622] usbcore: registered new interface driver usbfs
[   17.456650] usbcore: registered new interface driver hub
[   17.462269] usbcore: registered new device driver usb
[   17.463159] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.565864] ata1.00: ATA-6: ST960812A, 3.04, max UDMA/100
[   17.565869] ata1.00: 117210240 sectors, multi 16: LBA48 
[   17.581850] ata1.00: configured for UDMA/100
[   17.749203] Marking TSC unstable due to possible TSC halt in C2
[   17.753205] Time: acpi_pm clocksource has been installed.
[   17.901369] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.00, max UDMA/33
[   18.073108] ata2.00: configured for UDMA/33
[   18.073230] scsi 0:0:0:0: Direct-Access     ATA      ST960812A        3.04 PQ: 0 ANSI: 5
[   18.075177] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[   18.075364] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   18.075500] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   18.075703] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   18.075724] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfebff000
[   18.092900] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   18.092948] sd 0:0:0:0: [sda] Write Protect is off
[   18.092951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.092976] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.093044] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   18.093052] sd 0:0:0:0: [sda] Write Protect is off
[   18.093054] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.093066] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.093071]  sda: sda1 sda2 < sda5 >
[   18.114379] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.119296] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.119461] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.130848] usb usb1: configuration #1 chosen from 1 choice
[   18.130876] hub 1-0:1.0: USB hub found
[   18.130888] hub 1-0:1.0: 3 ports detected
[   18.147783] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.147790] Uniform CD-ROM driver Revision: 3.20
[   18.148063] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   18.232630] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   18.232782] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   18.232843] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   18.232866] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfebfe000
[   18.290551] usb usb2: configuration #1 chosen from 1 choice
[   18.290593] hub 2-0:1.0: USB hub found
[   18.290605] hub 2-0:1.0: 3 ports detected
[   18.392418] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[   18.392572] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   18.392646] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   18.392666] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfebfd000
[   18.450331] usb usb3: configuration #1 chosen from 1 choice
[   18.450363] hub 3-0:1.0: USB hub found
[   18.450372] hub 3-0:1.0: 2 ports detected
[   18.459170] Attempting manual resume
[   18.459175] swsusp: Resume From Partition 254:1
[   18.459177] PM: Checking swsusp image.
[   18.459403] PM: Resume from disk failed.
[   18.463780] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
[   18.463788] swsusp: Basic memory bitmaps created
[   18.492630] swsusp: Basic memory bitmaps freed
[   18.542935] kjournald starting.  Commit interval 5 seconds
[   18.542947] EXT3-fs: mounted filesystem with ordered data mode.
[   18.548046] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   18.553365] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   18.553532] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   18.553607] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   18.553643] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   18.553655] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfebfc000
[   18.723794] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.723914] usb usb4: configuration #1 chosen from 1 choice
[   18.723942] hub 4-0:1.0: USB hub found
[   18.723951] hub 4-0:1.0: 8 ports detected
[   18.827858] ACPI: PCI Interrupt 0000:00:0a.1[B] -> GSI 18 (level, low) -> IRQ 18
[   18.881015] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[febf9800-febf9fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   18.888179] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.888202] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   18.888322] eth0: RTL8169sb/8110sb at 0xffffc20000ab6c00, 00:15:f2:d8:19:84, XID 10000000 IRQ 19
[   19.131181] usb 1-2: device not accepting address 2, error -62
[   19.682381] usb 4-4: new high speed USB device using ehci_hcd and address 2
[   19.822125] usb 4-4: configuration #1 chosen from 1 choice
[   20.157780] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800034f16a9]
[   20.365353] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   20.661594] usb 3-2: configuration #1 chosen from 1 choice
[   27.564686] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.608375] Netfilter messages via NETLINK v0.30.
[   27.632358] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   30.563798] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.650515] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.153934] ieee80211_crypt: registered algorithm 'NULL'
[   31.250918] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   31.250923] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   31.429628] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1107]
[   31.557652] Yenta: ISA IRQ mask 0x04b8, PCI irq 17
[   31.557658] Socket status: 30000006
[   31.629234] sdhci: Secure Digital Host Controller Interface driver
[   31.629239] sdhci: Copyright(c) Pierre Ossman
[   31.629282] sdhci: SDHCI controller found at 0000:00:0a.2 [1180:0822] (rev 17)
[   31.629297] ACPI: PCI Interrupt 0000:00:0a.2[C] -> GSI 19 (level, low) -> IRQ 19
[   31.629537] mmc0: SDHCI at 0xfebf9400 irq 19 DMA
[   31.895697] bcm43xx driver
[   31.895816] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 18
[   31.984470] Bluetooth: Core ver 2.11
[   31.984527] NET: Registered protocol family 31
[   31.984530] Bluetooth: HCI device and connection manager initialized
[   31.984533] Bluetooth: HCI socket layer initialized
[   32.110794] input: PC Speaker as /class/input/input2
[   32.154229] nvidia: module license 'NVIDIA' taints kernel.
[   32.411261] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.411273] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   32.411495] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   32.426607] Bluetooth: HCI USB driver ver 2.9
[   32.429930] usbcore: registered new interface driver hci_usb
[   32.558655] irda_init()
[   32.558688] NET: Registered protocol family 23
[   32.563311] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   32.600403] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   32.722700] parport_pc 00:08: reported by Plug and Play ACPI
[   32.722730] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   33.028325] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[   33.853514] intel8x0_measure_ac97_clock: measured 55482 usecs
[   33.853518] intel8x0: clocking to 48000
[   34.160003] loop: module loaded
[   34.217587] lp0: using parport0 (interrupt-driven).
[   34.393708] Adding 2428920k swap on /dev/mapper/ubuntu-swap_1.  Priority:-1 extents:1 across:2428920k
[  227.382085] EXT3 FS on dm-0, internal journal
[  227.681754] kjournald starting.  Commit interval 5 seconds
[  227.688280] EXT3 FS on sda1, internal journal
[  227.688285] EXT3-fs: mounted filesystem with ordered data mode.
[  229.183473] pnp: Device 00:07 disabled.
[  229.184042] ACPI Error (dsopcode-0548): Field [IRQF] at 152 exceeds Buffer [NULL] size 136 (bits) [20070126]
[  229.184050] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.SBRG.UAR2._SRS] (Node ffff81007c8c5b60), AE_AML_BUFFER_LIMIT
[  229.184100] pnp: Failed to activate device 00:07.
[  229.184606] ACPI Error (dsopcode-0548): Field [IRQF] at 152 exceeds Buffer [NULL] size 136 (bits) [20070126]
[  229.184612] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.SBRG.UAR2._SRS] (Node ffff81007c8c5b60), AE_AML_BUFFER_LIMIT
[  229.184659] pnp: Failed to activate device 00:07.
[  229.690283] ACPI: Battery Slot [BAT0] (battery present)
[  229.706846] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  229.718056] No dock devices found.
[  229.751909] Asus Laptop ACPI Extras version 0.30
[  229.752124]   unsupported model A6Km, trying default values
[  229.752127]   send /proc/acpi/dsdt to the developers
[  229.795230] input: Power Button (FF) as /class/input/input4
[  229.800108] ACPI: Power Button (FF) [PWRF]
[  229.829137] input: Power Button (CM) as /class/input/input5
[  229.833910] ACPI: Power Button (CM) [PWRB]
[  229.862400] input: Lid Switch as /class/input/input6
[  229.867241] ACPI: Lid Switch [LID]
[  229.895863] input: Sleep Button (CM) as /class/input/input7
[  229.900635] ACPI: Sleep Button (CM) [SLPB]
[  229.967048] ACPI: AC Adapter [AC0] (on-line)
[  230.189025] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-32 processors (version 2.00.00)
[  230.189067] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
[  230.189070] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
[  230.189073] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[  231.224439] ppdev: user-space parallel port driver
[  231.874995] audit(1200285051.161:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4963 profile="/usr/sbin/cupsd"
[  231.893153] r8169: eth1: link down
[  233.192752] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  233.192757] vboxdrv: Successfully done.
[  233.382051] Failure registering capabilities with primary security module.
[  233.581482] Bluetooth: L2CAP ver 2.8
[  233.581486] Bluetooth: L2CAP socket layer initialized
[  233.623740] Bluetooth: RFCOMM socket layer initialized
[  233.623817] Bluetooth: RFCOMM TTY layer initialized
[  233.623820] Bluetooth: RFCOMM ver 1.8
[  604.765651] NET: Registered protocol family 17
[  604.986362] SoftMAC: Open Authentication completed with 00:18:4d:5e:41:b0
[  605.013590] ieee80211_crypt: registered algorithm 'TKIP'
[  605.891524] APIC error on CPU0: 00(40)
[  607.929180] APIC error on CPU0: 40(40)
[  609.727980] NET: Registered protocol family 10
[  609.728481] lo: Disabled Privacy Extensions
[  609.728638] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  615.188554] eth0: no IPv6 routers present
[  725.581885] APIC error on CPU0: 40(40)
[  743.579402] APIC error on CPU0: 40(40)
[  744.298437] APIC error on CPU0: 40(40)
[  746.055204] APIC error on CPU0: 40(40)
[  747.073271] APIC error on CPU0: 40(40)
[  748.560445] APIC error on CPU0: 40(40)
[  753.924464] APIC error on CPU0: 40(40)
[  754.109447] APIC error on CPU0: 40(40)
[  754.198132] APIC error on CPU0: 40(40)
[  754.367576] APIC error on CPU0: 40(40)
[  759.229249] APIC error on CPU0: 40(40)
[  770.127495] APIC error on CPU0: 40(40)
[  781.668255] APIC error on CPU0: 40(40)
[  785.961219] APIC error on CPU0: 40(40)
[  787.040832] APIC error on CPU0: 40(40)
[  791.819297] APIC error on CPU0: 40(40)
[  804.928934] APIC error on CPU0: 40(40)
[  805.228691] APIC error on CPU0: 40(40)
[  805.979947] APIC error on CPU0: 40(40)
[  807.681238] APIC error on CPU0: 40(40)
[  807.821047] APIC error on CPU0: 40(40)
[  808.020543] APIC error on CPU0: 40(40)
[  808.829202] APIC error on CPU0: 40(40)
[  808.895956] APIC error on CPU0: 40(40)
[  809.193829] APIC error on CPU0: 40(40)
[  815.324722] APIC error on CPU0: 40(40)
[  815.325854] APIC error on CPU0: 40(40)
[  818.266878] APIC error on CPU0: 40(40)
[  822.531335] APIC error on CPU0: 40(40)
[  822.664727] APIC error on CPU0: 40(40)
[  829.350152] APIC error on CPU0: 40(40)
[  829.614234] APIC error on CPU0: 40(40)
[  829.856312] APIC error on CPU0: 40(40)
[  831.674445] APIC error on CPU0: 40(40)
[  840.168976] APIC error on CPU0: 40(40)
[  840.303892] APIC error on CPU0: 40(40)
[  848.631753] APIC error on CPU0: 40(40)
[  851.341446] APIC error on CPU0: 40(40)
[  851.362327] APIC error on CPU0: 40(40)
[  851.363785] APIC error on CPU0: 40(40)
[  851.484102] APIC error on CPU0: 40(40)
[  851.814462] APIC error on CPU0: 40(40)
[  851.897828] APIC error on CPU0: 40(40)
[  851.991008] APIC error on CPU0: 40(40)
[  851.992505] APIC error on CPU0: 40(40)
[  868.003864] APIC error on CPU0: 40(40)
[  873.273948] APIC error on CPU0: 40(40)
[  878.705366] APIC error on CPU0: 40(40)
[  884.509155] APIC error on CPU0: 40(40)
[  889.521912] APIC error on CPU0: 40(40)
[  889.660427] APIC error on CPU0: 40(40)
[  891.448490] APIC error on CPU0: 40(40)
[  895.174629] APIC error on CPU0: 40(40)
[  915.479221] APIC error on CPU0: 40(40)
[  915.481410] APIC error on CPU0: 40(40)
[  917.905712] APIC error on CPU0: 40(40)
[  931.878171] APIC error on CPU0: 40(40)
[  940.445700] APIC error on CPU0: 40(40)
[  940.488247] APIC error on CPU0: 40(40)
[  941.242629] APIC error on CPU0: 40(40)
[  941.346894] APIC error on CPU0: 40(40)
[  941.867204] APIC error on CPU0: 40(40)
[  941.868054] APIC error on CPU0: 40(40)
[  941.894282] APIC error on CPU0: 40(40)
[  941.918886] APIC error on CPU0: 40(40)
[  941.934238] APIC error on CPU0: 40(40)
[  942.013721] APIC error on CPU0: 40(40)
[  942.313954] APIC error on CPU0: 40(40)
[  943.863382] APIC error on CPU0: 40(40)
[  945.323412] APIC error on CPU0: 40(40)
[  970.646095] APIC error on CPU0: 40(40)
[  973.386591] APIC error on CPU0: 40(40)
[  978.266428] APIC error on CPU0: 40(40)
[  989.213844] APIC error on CPU0: 40(40)
[ 1001.235619] APIC error on CPU0: 40(40)
[ 1015.863023] APIC error on CPU0: 40(40)
[ 1023.167785] APIC error on CPU0: 40(40)
[ 1038.452928] APIC error on CPU0: 40(40)
[ 1038.555419] APIC error on CPU0: 40(40)
[ 1038.939969] APIC error on CPU0: 40(40)
[ 1038.957746] APIC error on CPU0: 40(40)
[ 1038.980204] APIC error on CPU0: 40(40)
[ 1039.116550] APIC error on CPU0: 40(40)
[ 1039.199703] APIC error on CPU0: 40(40)
[ 1039.209059] APIC error on CPU0: 40(40)
[ 1040.195636] APIC error on CPU0: 40(40)
[ 1040.448325] APIC error on CPU0: 40(40)
[ 1040.700455] APIC error on CPU0: 40(40)
[ 1041.217993] APIC error on CPU0: 40(40)
[ 1041.986037] npviewer.bin[7233]: segfault at 000000006c705f64 rip 000000006c705f64 rsp 00000000ffd91a8c error 14
[ 1041.992346] APIC error on CPU0: 40(40)
[ 1041.992568] APIC error on CPU0: 40(40)
[ 1041.993410] APIC error on CPU0: 40(40)
[ 1048.262274] APIC error on CPU0: 40(40)
[ 1054.627053] APIC error on CPU0: 40(40)
[ 1054.864351] APIC error on CPU0: 40(40)
[ 1054.918684] APIC error on CPU0: 40(40)
[ 1055.348608] APIC error on CPU0: 40(40)
[ 1055.943251] APIC error on CPU0: 40(40)
[ 1058.761505] APIC error on CPU0: 40(40)
[ 1060.655613] APIC error on CPU0: 40(40)
[ 1066.193335] APIC error on CPU0: 40(40)
[ 1070.549921] APIC error on CPU0: 40(40)
[ 1086.412314] APIC error on CPU0: 40(40)
[ 1096.815352] APIC error on CPU0: 40(40)
[ 1097.051807] APIC error on CPU0: 40(40)
[ 1098.397017] npviewer.bin[7528]: segfault at 0000000076726553 rip 0000000076726553 rsp 00000000fffe34dc error 14
[ 1111.580985] APIC error on CPU0: 40(40)
[ 1124.376988] APIC error on CPU0: 40(40)
[ 1125.573473] APIC error on CPU0: 40(40)
[ 1126.855994] APIC error on CPU0: 40(40)
[ 1162.059340] APIC error on CPU0: 40(40)
[ 1172.442302] APIC error on CPU0: 40(40)
[ 1172.652963] APIC error on CPU0: 40(40)
[ 1173.495918] APIC error on CPU0: 40(40)
[ 1174.585226] APIC error on CPU0: 40(40)
[ 1178.539822] APIC error on CPU0: 40(40)
[ 1178.540111] APIC error on CPU0: 40(40)
scotthammy@ubuntu:~$ 
:confused::confused:

---

### Post by dutchcow on 2008-01-14
My laptop also has a card reader, memory stick duo also doesnt work on my ubuntu install. This is a long standing kernel related issue with ricoh chipset based card readers. Other chipsets/card readers might work fine with memory stick. When inserting the memory stick duo in my card reader nothing shows up in "dmesg" the reader light also stays off as if its not even trying to read it. We can only hope that one day ricoh chips will be fully supported in the kernel. I've found 2 other threads dealign with this, one has a link to instructions on howto install a beta module/driver, which might make your system unstable and one can only hope it works on your card reader since the posted reported it didn't work for him. The threads are here:
[http://ubuntuforums.org/showthread.php?t=653152](http://ubuntuforums.org/showthread.php?t=653152)
[http://ubuntuforums.org/showthread.php?t=336982](http://ubuntuforums.org/showthread.php?t=336982)

---

### Post by red-lichtie on 2008-02-02
I had the same problem on gutsy,  so I downloaded/compiled/installed the code directly from the svn trunk as described on that other thread.

I had to slightly modify the Makefile so that it built all the modules I wanted and changed the installation location to match where the old ones were located.

After rebooting, this is what I get when I stick the card in the reader:

from dmesg:
[ 5967.976000] tifm_core: MemoryStick card detected in socket 0:0
[ 5969.592000]  mspblk1: p1

$ ll /dev/mspblk*
brw-rw---- 1 root disk 254, 8 2008-02-02 19:53 /dev/mspblk1
brw-rw---- 1 root disk 254, 9 2008-02-02 19:53 /dev/mspblk1p1

So its there :)

Monitoring UDEV while plugging in gives this:
$ sudo udevmonitor -e
------------------------


UEVENT[1201978584.877189] add      /devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0 (tifm)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0
SUBSYSTEM=tifm
SEQNUM=3138
PHYSDEVBUS=tifm
TIFM_CARD_TYPE=MS

UEVENT[1201978584.877274] add      /class/memstick_host/memstick0 (memstick_host)
ACTION=add
DEVPATH=/class/memstick_host/memstick0
SUBSYSTEM=memstick_host
SEQNUM=3139
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0
PHYSDEVBUS=tifm
PHYSDEVDRIVER=tifm_ms

UDEV  [1201978584.887536] add      /devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0 (tifm)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0
SUBSYSTEM=tifm
SEQNUM=3138
PHYSDEVBUS=tifm
TIFM_CARD_TYPE=MS
UDEVD_EVENT=1

UDEV  [1201978584.912389] add      /class/memstick_host/memstick0 (memstick_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/memstick_host/memstick0
SUBSYSTEM=memstick_host
SEQNUM=3139
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0
PHYSDEVBUS=tifm
PHYSDEVDRIVER=tifm_ms
UDEVD_EVENT=1

UEVENT[1201978585.059321] add      /devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0 (memstick)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
SUBSYSTEM=memstick
SEQNUM=3140
PHYSDEVBUS=memstick
MEMSTICK_TYPE=01
MEMSTICK_CATEGORY=00
MEMSTICK_CLASS=00

UDEV  [1201978585.105612] add      /devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0 (memstick)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
SUBSYSTEM=memstick
SEQNUM=3140
PHYSDEVBUS=memstick
MEMSTICK_TYPE=01
MEMSTICK_CATEGORY=00
MEMSTICK_CLASS=00
UDEVD_EVENT=1

UEVENT[1201978586.795059] add      /block/mspblk1 (block)
ACTION=add
DEVPATH=/block/mspblk1
SUBSYSTEM=block
SEQNUM=3141
MINOR=8
MAJOR=254
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
PHYSDEVBUS=memstick
PHYSDEVDRIVER=mspro_block

UEVENT[1201978586.795151] add      /block/mspblk1/mspblk1p1 (block)
ACTION=add
DEVPATH=/block/mspblk1/mspblk1p1
SUBSYSTEM=block
SEQNUM=3142
MINOR=9
MAJOR=254
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
PHYSDEVBUS=memstick
PHYSDEVDRIVER=mspro_block

UDEV  [1201978596.745964] add      /block/mspblk1 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/mspblk1
SUBSYSTEM=block
SEQNUM=3141
MINOR=8
MAJOR=254
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
PHYSDEVBUS=memstick
PHYSDEVDRIVER=mspro_block
UDEVD_EVENT=1
DEVTYPE=disk
ID_PATH=pci-memstick0-
DEVNAME=/dev/mspblk1
DEVLINKS=/dev/disk/by-path/pci-memstick0-

UDEV  [1201978609.024231] add      /block/mspblk1/mspblk1p1 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/mspblk1/mspblk1p1
SUBSYSTEM=block
SEQNUM=3142
MINOR=9
MAJOR=254
PHYSDEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:12:04.2/tifm_ms0:0/memstick0
PHYSDEVBUS=memstick
PHYSDEVDRIVER=mspro_block
UDEVD_EVENT=1
DEVTYPE=partition
ID_PATH=pci-memstick0-
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=512MB
ID_FS_LABEL_ENC=512MB
ID_FS_LABEL_SAFE=512MB
DEVNAME=/dev/mspblk1p1
DEVLINKS=/dev/disk/by-path/pci-memstick0--part1 /dev/disk/by-label/512MB



------------------------

I can manually mount /dev/mspblk1p1 and it works, but how do I set things up so that it will be automatically mounted and appear on the desktop ?

I've never made a udev rule before, and I think thats what I have to do, but how ?

---

### Post by scotthammy on 2008-02-02
If you have this working, This Really needs to be put into the next version of ubuntu. :KS

---

