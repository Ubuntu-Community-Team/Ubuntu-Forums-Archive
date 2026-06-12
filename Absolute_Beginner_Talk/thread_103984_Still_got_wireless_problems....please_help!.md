---
title: "Still got wireless problems....please help!"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2005-12-15
Hi there,

I'm new to Linux and Ubuntu. I've installed Breezy on my Acer 5021WLMi laptop but decided to go with the 32bit 386 version rather than the amd64bit version. I'm trying to configure a Netgear WG511T PCMCIA card that goes with my router rather than using the onboard broadcom wireless (which is difficult to configure with Ubuntu on acers). Looking through the forums I see that a lot of people said it worked straight out of the box but I seem to have had no such luck. The light is flashing (a great improvment on my broadcom hardware which won't even do that) but I can't find any options to enable it under the System>Administration>Networking settings.

In order to get it to detect do I need to install the windows driver with ndiswrapper or is there something else I should be using? Does anyone know of a good how to guide for this card and Breezy.

Thanks for your help.

---

### Post by Lambert on 2005-12-15
The 511t comes with an atheros chipset. You can double check this with *lspci -v*.  

So this should just work out of the box. But you say there's no options for it in networking? So the card doesn't show up at all in the list?

So do this.

unplug the card, plug it back in then run *dmesg*. Look through the output and post the lines that look involved with the card here. Should be the last set of lines.

Also with the card plugged in run these commands and post back here.

sudo lshw -C network
iwconfig

---

### Post by rikoshay on 2005-12-15
Thank you for your help. I can't get to my laptop now because I'm at work but I'll post the command line as soon as I get home.

Cheers!

---

### Post by rikoshay on 2005-12-16
OK, so here's what I got. Couldn't find any reference to the card or any wireless extensions.

rik@lappy:~$ dmesg
0001 00000000 00000001
[4294670.015000] CPU: AMD Turion(tm) 64 Mobile Technology ML-28 stepping 02
[4294670.015000] Enabling fast FPU save and restore... done.
[4294670.015000] Enabling unmasked SIMD FPU exception support... done.
[4294670.015000] Checking 'hlt' instruction... OK.
[4294670.019000] Checking for popad bug... OK.
[4294670.019000] checking if image is initramfs... it is
[4294670.503000] Freeing initrd memory: 5171k freed
[4294670.507000] ACPI: Looking for DSDT in initrd... not found!
[4294670.568000]  not found!
[4294670.583000] ENABLING IO-APIC IRQs
[4294670.583000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294670.707000] NET: Registered protocol family 16
[4294670.707000] EISA bus registered
[4294670.707000] ACPI: bus type pci registered
[4294670.719000] PCI: PCI BIOS revision 2.10 entry at 0xfd63c, last bus=6
[4294670.719000] PCI: Using configuration type 1
[4294670.719000] mtrr: v2.0 (20020519)
[4294670.721000] ACPI: Subsystem revision 20050729
[4294670.736000] ACPI: Interpreter enabled
[4294670.736000] ACPI: Using IOAPIC for interrupt routing
[4294670.738000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.738000] PCI: Probing PCI hardware (bus 00)
[4294670.738000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.746000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294670.746000] Boot video device is 0000:01:00.0
[4294670.748000] PCI: Transparent bridge - 0000:00:14.4
[4294670.754000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.756000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[4294670.756000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[4294670.756000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[4294670.758000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[4294670.758000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[4294670.758000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[4294670.760000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[4294670.760000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[4294670.760000] burst-mode-ec-10-Aug
[4294670.760000] ACPI: Embedded Controller [EC0] (gpe 3)
[4294670.838000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[4294670.838000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[4294670.838000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[4294670.840000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[4294670.840000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.840000] pnp: PnP ACPI init
[4294670.856000] pnp: PnP ACPI: found 10 devices
[4294670.856000] PnPBIOS: Disabled by ACPI PNP
[4294670.856000] PCI: Using ACPI for IRQ routing
[4294670.856000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.902000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[4294670.902000] pnp: 00:07: ioport range 0x1200-0x120f has been reserved
[4294670.902000] pnp: 00:07: ioport range 0x500-0x51f has been reserved
[4294670.902000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[4294670.904000] audit: initializing netlink socket (disabled)
[4294670.904000] audit: initialized
[4294670.904000] VFS: Disk quotas dquot_6.5.1
[4294670.904000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.904000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.904000] devfs: boot_options: 0x0
[4294670.904000] Initializing Cryptographic API
[4294670.904000] PCI: 0000:00:02.0 has unsupported PM cap regs version (3)
[4294670.904000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294670.904000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[4294670.904000] assign_interrupt_mode Found MSI capability
[4294670.904000] Allocate Port Service[pcie00]
[4294670.904000] PCI: 0000:00:06.0 has unsupported PM cap regs version (3)
[4294670.904000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294670.904000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[4294670.904000] assign_interrupt_mode Found MSI capability
[4294670.904000] Allocate Port Service[pcie00]
[4294670.904000] PCI: 0000:00:07.0 has unsupported PM cap regs version (3)
[4294670.904000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[4294670.904000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[4294670.904000] assign_interrupt_mode Found MSI capability
[4294670.904000] Allocate Port Service[pcie00]
[4294670.904000] isapnp: Scanning for PnP cards...
[4294671.612000] isapnp: No Plug & Play device found
[4294671.646000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.665000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.671000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.673000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.673000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.675000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.677000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.677000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.677000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.681000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[4294671.681000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[4294671.681000] io scheduler noop registered
[4294671.681000] io scheduler anticipatory registered
[4294671.681000] io scheduler deadline registered
[4294671.681000] io scheduler cfq registered
[4294671.681000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.687000] EISA: Probing bus 0 at eisa.0
[4294671.687000] Cannot allocate resource for EISA slot 1
[4294671.687000] Cannot allocate resource for EISA slot 8
[4294671.689000] EISA: Detected 0 cards.
[4294671.689000] NET: Registered protocol family 2
[4294671.707000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294671.707000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.707000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.707000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.707000] NET: Registered protocol family 8
[4294671.707000] NET: Registered protocol family 20
[4294671.707000] ACPI wakeup devices:
[4294671.707000] LID0 SLPB OHC1 OHC2 EHCI  P2P MODM
[4294671.707000] ACPI: (supports S0 S3 S4 S5)
[4294671.707000] Freeing unused kernel memory: 224k freed
[4294671.733000] vga16fb: initializing
[4294671.733000] vga16fb: mapped to 0xc00a0000
[4294672.009000] Console: switching to colour frame buffer device 80x30
[4294672.009000] fb0: VGA16 VGA frame buffer device
[4294673.375000] Capability LSM initialized
[4294673.393000] NET: Registered protocol family 1
[4294673.419000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.419000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.419000] ACPI: bus type ide registered
[4294673.435000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294673.435000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294673.435000] ATIIXP: chipset revision 0
[4294673.435000] ATIIXP: not 100% native mode: will probe irqs later
[4294673.435000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[4294673.435000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[4294673.435000] Probing IDE interface ide0...
[4294673.712000] hda: ST9808210A, ATA DISK drive
[4294674.334000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.334000] Probing IDE interface ide1...
[4294675.027000] hdc: MATSHITAUJ-845D, ATAPI CD/DVD-ROM drive
[4294675.339000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.339000] Probing IDE interface ide2...
[4294675.864000] Probing IDE interface ide3...
[4294676.386000] Probing IDE interface ide4...
[4294676.907000] Probing IDE interface ide5...
[4294677.434000] hda: max request size: 1024KiB
[4294677.436000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294677.436000] hda: cache flushes supported
[4294677.436000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 > p4
[4294677.539000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.539000] Uniform CD-ROM driver Revision: 3.20
[4294678.021000] Attempting manual resume
[4294678.023000] swsusp: Suspend partition has wrong signature?
[4294678.105000] usbcore: registered new driver usbfs
[4294678.105000] usbcore: registered new driver hub
[4294678.107000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294678.107000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294678.107000] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
[4294678.322000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294678.322000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[4294678.382000] hub 1-0:1.0: USB hub found
[4294678.382000] hub 1-0:1.0: 4 ports detected
[4294678.388000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[4294678.388000] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[4294678.603000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294678.603000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[4294678.663000] hub 2-0:1.0: USB hub found
[4294678.663000] hub 2-0:1.0: 4 ports detected
[4294678.699000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[4294678.699000] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[4294678.699000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294678.699000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[4294678.699000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.699000] hub 3-0:1.0: USB hub found
[4294678.699000] hub 3-0:1.0: 8 ports detected
[4294678.959000] r8169 Gigabit Ethernet driver 2.2LK loaded
[4294678.959000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294678.961000] eth0: Identified chip type is 'RTL8169s/8110s'.
[4294678.961000] eth0: RTL8169 at 0xe0898400, 00:0a:e4:e3:e2:66, IRQ 23
[4294681.777000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294681.877000] ACPI: Thermal Zone [TZS0] (56 C)
[4294681.975000] ACPI: Thermal Zone [TZS1] (31 C)
[4294682.073000] ACPI: Thermal Zone [TZSV] (39 C)
[4294682.543000] Attempting manual resume
[4294682.543000] swsusp: Suspend partition has wrong signature?
[4294682.581000] kjournald starting.  Commit interval 5 seconds
[4294682.581000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.983000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.773000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
[4294692.403000] EXT3 FS on hda2, internal journal
[4294706.821000] lp: driver loaded but no devices found
[4294706.889000] mice: PS/2 mouse device common for all mice
[4294706.967000] ieee1394: Initialized config rom entry `ip1394'
[4294706.999000] SCSI subsystem initialized
[4294707.007000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294708.215000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[4294708.221000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294708.291000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[4294708.799000] ts: Compaq touchscreen protocol output
[4294714.979000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294717.313000] cdrom: open failed.
[4294722.443000] Linux agpgart interface v0.101 (c) Dave Jones
[4294722.745000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294722.779000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294723.847000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294727.593000] Linux Kernel Card Services
[4294727.593000]   options:  [pci] [cardbus] [pm]
[4294727.617000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294727.617000] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[4294727.617000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294727.617000] Yenta: Routing CardBus interrupts to PCI
[4294727.617000] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[4294727.839000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[4294727.839000] Socket status: 30000820
[4294728.053000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294728.053000] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294728.163000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]
[4294729.427000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[1234567812345678][4294729.911000] Real Time Clock Driver v1.12
[4294730.003000] input: PC Speaker
[4294733.071000] r8169: eth0: link up
[4294733.091000] NET: Registered protocol family 17
[4294741.551000] NET: Registered protocol family 10
[4294741.551000] Disabled Privacy Extensions on device c02eb280(lo)
[4294741.551000] IPv6 over IPv4 tunneling driver
[4294743.825000] ACPI: AC Adapter [ADP1] (on-line)
[4294744.281000] ACPI: Battery Slot [BAT0] (battery present)
[4294744.319000] ACPI: Power Button (FF) [PWRF]
[4294744.319000] ACPI: Lid Switch [LID0]
[4294744.319000] ACPI: Sleep Button (CM) [SLPB]
[4294744.525000] ibm_acpi: ec object not found
[4294744.747000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294744.749000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294751.842000] eth0: no IPv6 routers present
[4294764.390000] apm: BIOS not found.
[4294769.480000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294769.488000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294769.490000] cs: IO port probe 0xa00-0xaff: clean.
[4294771.804000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294771.806000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
[4294771.806000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[4294771.806000] cpu_init done, current fid 0x8, vid 0x4
[4294772.074000] Bluetooth: Core ver 2.7
[4294772.074000] NET: Registered protocol family 31
[4294772.074000] Bluetooth: HCI device and connection manager initialized
[4294772.074000] Bluetooth: HCI socket layer initialized
[4294772.100000] Bluetooth: L2CAP ver 2.7
[4294772.100000] Bluetooth: L2CAP socket layer initialized
[4294772.148000] Bluetooth: RFCOMM ver 1.5
[4294772.148000] Bluetooth: RFCOMM socket layer initialized
[4294772.148000] Bluetooth: RFCOMM TTY layer initialized
[4294772.658000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294816.239000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[4295151.489000] APIC error on CPU0: 00(40)
[4295204.442000] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[4295204.448000] cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[4295204.454000] cs: warning: no high memory space available!
[4295433.809000] APIC error on CPU0: 40(40)
[4295613.012000] APIC error on CPU0: 40(40)
[4295618.709000] APIC error on CPU0: 40(40)
[4295666.048000] APIC error on CPU0: 40(40)
[4295953.989000] APIC error on CPU0: 40(40)
[4296455.261000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4296455.529000] NTFS volume version 3.1.
[4296521.089000] APIC error on CPU0: 40(40)
[4297278.478000] APIC error on CPU0: 40(40)
rik@lappy:~$ sudo lshw -C network
Password:
  *-network:0 UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:c0204000-c0205fff irq:10
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e3:e2:66
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.5 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0209400-c02094ff irq:23
rik@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

rik@lappy:~$

Any ideas? And when you said unplug the card and plug it back in I presumed you meant with the laptop powered down. Just checking.

Thanks!

---

### Post by thezerogroup on 2005-12-16
Try installing the madwifi drivers.

[http://madwifi.org/]("http://madwifi.org/")

Your can add madwifi to your /etc/apt/sources.list . . . so you can apt-get install them: 

```

deb ftp://debian.marlow.dk/ sid madwifi
 deb-src ftp://debian.marlow.dk/ sid madwifi

```

then run: 
```
sudo apt-get update
         sudo apt-get install madwifi* 
```

---

### Post by Mustard on 2005-12-16
thezerogroup, Is that asterisk on the end of madwifi supposed to be there?

---

### Post by thezerogroup on 2005-12-16
yep, as there are two packages needed for the install (madwifi-source and madwifi-tools). You can skip the * and do this instead: 

sudo apt-get install madwifi-source madwifi-tools.

---

### Post by rikoshay on 2005-12-18
Thanks guys. I installed MadWifi as instructed using the * command. I then followed the neewb guide on the MadWifi website and got this:

[PHP]rik@lappy:~$ sudo modprobe ath_pci
rik@lappy:~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
sudo: wlanconfig: command not found
rik@lappy:~$
[/PHP]

In the guide it describes compiling the program from source. Could this have anything to do with the error? Cheers.

---

