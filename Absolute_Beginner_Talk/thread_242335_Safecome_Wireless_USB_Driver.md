---
title: "Safecome Wireless USB Driver"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2006-08-23
Hi can anyone help me in getting drivers for my Safecom SWLUT-54125 USB wireless adapter?

I really want to use Ubuntu but I NEED to access the internet for it to be a viable OS for me to use.

Thanks, Tom

---

### Post by TFX360 on 2006-08-23
I really don't know about this usb adapter

Give us the output of:

```
sudo lsusb
```

```
sudo dmesg
```

```
sudo ifconfig
```

```
sudo iwconfig
```

```
sudo less /etc/network/interfaces
```


Kind regards,


TFX

---

### Post by AnotherMuggle on 2006-08-27
Hi,
I am still having trouble with this wifi card.  I am now using Kubuntu but I understand the working are very similar, if not the same!?!

sudo lsusb:

Bus 001 Device 006: ID 07b8:b21a D-Link Corp.
Bus 001 Device 001: ID 0000:0000

sudo dmesg:

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.
0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bef0000 - 000000001beff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001beff000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114416
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110320 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x0
00f7290
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @
 0x1bef8b73
[17179569.184000] ACPI: FADT (v001 ATI    Raptor   0x06040000 ATI  0x000f4240) @
 0x1befee2b
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @
 0x1befee9f
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @
 0x1befeec7
[17179569.184000] ACPI: DSDT (v001    ATI U1_M1535 0x06040000 MSFT 0x0100000d) @
 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e
3fc0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable
it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01380000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1855.392 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.476000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes
)
[17179570.476000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.496000] Memory: 443188k/457664k available (1976k kernel code, 13900k r
eserved, 606k data, 288k init, 0k highmem)
[17179570.496000] Checking if this processor honours the WP bit even in supervis
or mode... Ok.
[17179570.576000] Calibrating delay using timer specific routine.. 3712.66 BogoM
IPS (lpj=7425339)
[17179570.576000] Security Framework v1.0.0 initialized
[17179570.576000] SELinux:  Disabled at boot.
[17179570.576000] Mount-cache hash table entries: 512
[17179570.576000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000
00000000 00000000 00000000 00000000
[17179570.576000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 0
0000000 00000000 00000000 00000000
[17179570.576000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/li
ne)
[17179570.576000] CPU: L2 Cache: 512K (64 bytes/line)
[17179570.576000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 0000042
0 00000000 00000000 00000000
[17179570.576000] mtrr: v2.0 (20020519)
[17179570.576000] CPU: AMD mobile AMD Athlon(tm) XP2500+ stepping 00
[17179570.576000] Enabling fast FPU save and restore... done.
[17179570.576000] Enabling unmasked SIMD FPU exception support... done.
[17179570.576000] Checking 'hlt' instruction... OK.
[17179570.592000] checking if image is initramfs... it is
[17179571.172000] Freeing initrd memory: 6615k freed
[17179571.188000] ACPI: Looking for DSDT ... not found!
[17179571.192000] ACPI: setting ELCR to 0200 (from 0e28)
[17179571.192000] NET: Registered protocol family 16
[17179571.192000] EISA bus registered
[17179571.192000] ACPI: bus type pci registered
[17179571.200000] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[17179571.200000] PCI: Using configuration type 1
[17179571.200000] ACPI: Subsystem revision 20051216
[17179573.400000] ACPI: Interpreter enabled
[17179573.400000] ACPI: Using PIC for interrupt routing
[17179573.400000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.400000] PCI: Probing PCI hardware (bus 00)
[17179573.404000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179573.404000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179573.404000] Boot video device is 0000:01:05.0
[17179573.404000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.404000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.404000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[17179573.408000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[17179573.408000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[17179573.408000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *0, disabled.
[17179573.408000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[17179573.408000] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *0, disabled.
[17179573.408000] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[17179573.408000] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[17179573.408000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[17179573.412000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179573.412000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.412000] pnp: PnP ACPI init
[17179573.416000] pnp: PnP ACPI: found 13 devices
[17179573.416000] PnPBIOS: Disabled by ACPI PNP
[17179573.416000] PCI: Using ACPI for IRQ routing
[17179573.416000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179573.420000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[17179573.420000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[17179573.420000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[17179573.420000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[17179573.420000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[17179573.420000] PCI: Bridge: 0000:00:01.0
[17179573.420000]   IO window: 9000-9fff
[17179573.420000]   MEM window: d0100000-d01fffff
[17179573.420000]   PREFETCH window: e0000000-efffffff
[17179573.420000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179573.420000]   IO window: 00001000-000010ff
[17179573.420000]   IO window: 00001400-000014ff
[17179573.420000]   PREFETCH window: 20000000-21ffffff
[17179573.420000]   MEM window: 22000000-23ffffff
[17179573.420000] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[17179573.420000] **** SET: Misaligned resource pointer: dbe2f6e2 Type 07 Len 0
[17179573.420000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[17179573.420000] PCI: setting IRQ 11 as level-triggered
[17179573.420000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (
level, low) -> IRQ 11
[17179573.420000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179573.420000] Simple Boot Flag at 0x36 set to 0x1
[17179573.420000] audit: initializing netlink socket (disabled)
[17179573.420000] audit(1156696856.420:1): initialized
[17179573.420000] VFS: Disk quotas dquot_6.5.1
[17179573.420000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.420000] Initializing Cryptographic API
[17179573.420000] io scheduler noop registered
[17179573.420000] io scheduler anticipatory registered
[17179573.420000] io scheduler deadline registered
[17179573.420000] io scheduler cfq registered
[17179573.420000] ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
[17179573.420000] Activating ISA DMA hang workarounds.
[17179573.420000] isapnp: Scanning for PnP cards...
[17179573.688000] isapnp: No Plug & Play device found
[17179573.700000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64
irq 1,12
[17179573.708000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.708000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.708000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar
ing enabled
[17179573.708000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.712000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.712000] **** SET: Misaligned resource pointer: dbc2f322 Type 07 Len 0
[17179573.712000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[17179573.712000] PCI: setting IRQ 3 as level-triggered
[17179573.712000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 3 (l
evel, low) -> IRQ 3
[17179573.712000] 0000:00:08.0: ttyS9 at I/O 0x8828 (irq = 3) is a 8250
[17179573.712000] 0000:00:08.0: ttyS12 at I/O 0x8840 (irq = 3) is a 8250
[17179573.712000] 0000:00:08.0: ttyS14 at I/O 0x8850 (irq = 3) is a 8250
[17179573.712000] 0000:00:08.0: ttyS16 at I/O 0x8860 (irq = 3) is a 8250
[17179573.712000] 0000:00:08.0: ttyS18 at I/O 0x8870 (irq = 3) is a 8250
[17179573.716000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b
locksize
[17179573.716000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.716000] ide: Assuming 33MHz system bus speed for PIO modes; override w
ith idebus=xx
[17179573.716000] mice: PS/2 mouse device common for all mice
[17179573.716000] EISA: Probing bus 0 at eisa.0
[17179573.716000] Cannot allocate resource for EISA slot 1
[17179573.716000] Cannot allocate resource for EISA slot 8
[17179573.716000] EISA: Detected 0 cards.
[17179573.716000] NET: Registered protocol family 2
[17179573.752000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.756000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes
)
[17179573.756000] TCP established hash table entries: 16384 (order: 4, 65536 byt
es)
[17179573.756000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.756000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.756000] TCP reno registered
[17179573.756000] TCP bic registered
[17179573.756000] NET: Registered protocol family 1
[17179573.756000] NET: Registered protocol family 8
[17179573.756000] NET: Registered protocol family 20
[17179573.756000] Using IPI Shortcut mode
[17179573.756000] ACPI wakeup devices:
[17179573.756000] PCI0 MDEM  LAN  LID
[17179573.756000] ACPI: (supports S0 S3 S4 S5)
[17179573.756000] Freeing unused kernel memory: 288k freed
[17179573.804000] vga16fb: initializing
[17179573.804000] vga16fb: mapped to 0xc00a0000
[17179573.920000] Console: switching to colour frame buffer device 80x25
[17179573.920000] fb0: VGA16 VGA frame buffer device
[17179574.936000] Capability LSM initialized
[17179575.508000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.508000] ACPI: Thermal Zone [THRM] (43 C)
[17179575.900000] alim15x3: ATI Radeon IGP Northbridge is not yet fully tested.
[17179575.900000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[17179575.900000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[17179575.900000] ALI15X3: chipset revision 196
[17179575.900000] ALI15X3: not 100% native mode: will probe irqs later
[17179575.900000]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb
:pio
[17179575.900000]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd
:pio
[17179575.900000] Probing IDE interface ide0...
[17179576.192000] hda: FUJITSU MHT2030AT, ATA DISK drive
[17179576.864000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.944000] Probing IDE interface ide1...
[17179577.680000] hdc: SD-R2512, ATAPI CD/DVD-ROM drive
[17179578.372000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.388000] hda: max request size: 128KiB
[17179578.400000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16
/63, UDMA(100)
[17179578.400000] hda: cache flushes supported
[17179578.400000]  hda: hda1 hda2 hda3 < hda5 >
[17179578.472000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179578.472000] Uniform CD-ROM driver Revision: 3.20
[17179578.892000] usbcore: registered new driver usbfs
[17179578.892000] usbcore: registered new driver hub
[17179578.892000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI)
Driver (PCI)
[17179578.892000] **** SET: Misaligned resource pointer: dbcc84e2 Type 07 Len 0
[17179578.892000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[17179578.892000] PCI: setting IRQ 10 as level-triggered
[17179578.892000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 10 (
level, low) -> IRQ 10
[17179578.892000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179579.112000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus nu
mber 1
[17179579.112000] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[17179579.168000] hub 1-0:1.0: USB hub found
[17179579.168000] hub 1-0:1.0: 4 ports detected
[17179579.344000] Attempting manual resume
[17179579.356000] kjournald starting.  Commit interval 5 seconds
[17179579.356000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.576000] usb 1-1: new full speed USB device using ohci_hcd and address
2
[17179593.640000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.692000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.768000] input: PC Speaker as /class/input/input1
[17179593.772000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized -
 upgrade BIOS or use force_addr=0xaddr
[17179593.772000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not i
nserted.
[17179593.784000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.784000] agpgart: Detected Ati IGP320/M chipset
[17179593.792000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179593.900000] **** SET: Misaligned resource pointer: dba0f102 Type 07 Len 0
[17179593.900000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179593.900000] PCI: setting IRQ 5 as level-triggered
[17179593.900000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (l
evel, low) -> IRQ 5
[17179594.240000] FDC 0 is a post-1991 82077
[17179594.244000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179594.244000]   originally by Donald Becker <becker@scyld.com>
[17179594.244000]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[17179594.244000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179594.504000] Real Time Clock Driver v1.12
[17179594.524000] parport: PnPBIOS parport detected.
[17179594.524000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179594.944000] AC'97 1 does not respond - RESET
[17179594.944000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179594.944000] ali mixer 1 creating error.
[17179594.948000] **** SET: Misaligned resource pointer: d6aa87e2 Type 07 Len 0
[17179594.948000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179594.948000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKB] -> GSI 11 (
level, low) -> IRQ 11
[17179594.948000] natsemi eth0: NatSemi DP8381[56] at 0xd0003000 (0000:00:12.0),
 00:0f:20:21:fe:72, IRQ 11, port TP.
[17179594.952000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (
level, low) -> IRQ 11
[17179594.952000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0024]
[17179594.952000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179594.952000] Yenta: Routing CardBus interrupts to PCI
[17179594.952000] Yenta TI: socket 0000:00:0a.0, mfunc 0x01111112, devctl 0x64
[17179595.128000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x9
04713/0x10008
[17179595.164000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179595.176000] ts: Compaq touchscreen protocol output
[17179595.184000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
[17179595.184000] Socket status: 30000006
[17179595.632000] eth0: DSPCFG accepted after 0 usec.
[17179595.632000] eth0: link up.
[17179595.632000] eth0: Setting full-duplex based on negotiated link capability.
[17179595.752000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x2
2f 0x330-0x337 0x388-0x38f
[17179595.752000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179595.752000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.752000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.756000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.052000] lp0: using parport0 (interrupt-driven).
[17179596.112000] Adding 634528k swap on /dev/hda5.  Priority:-1 extents:1 acros
s:634528k
[17179596.232000] EXT3 FS on hda2, internal journal
[17179596.432000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.432000] md: bitmap version 4.39
[17179596.700000] NET: Registered protocol family 17
[17179596.996000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@
redhat.com
[17179598.316000] NET: Registered protocol family 10
[17179598.316000] lo: Disabled Privacy Extensions
[17179598.316000] IPv6 over IPv4 tunneling driver
[17179598.548000] cdrom: open failed.
[17179601.596000] ACPI: AC Adapter [ACAD] (on-line)
[17179601.604000] ACPI: Battery Slot [BAT1] (battery present)
[17179601.696000] ACPI: Power Button (FF) [PWRF]
[17179601.696000] ACPI: Power Button (CM) [PWRB]
[17179601.696000] ACPI: Lid Switch [LID]
[17179601.808000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179601.808000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[17179601.860000] pcc_acpi: loading...
[17179601.988000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179602.512000] powernow: PowerNOW! Technology present. Can scale: frequency a
nd voltage.
[17179602.532000] Detected 1855.325 MHz processor.
[17179602.540000] powernow: No PST tables match this cpuid (0x7a0)
[17179602.540000] powernow: This is indicative of a broken BIOS.
[17179602.540000] powernow: Trying ACPI perflib
[17179602.540000] powernow: Minimum speed 530 MHz. Maximum speed 1855 MHz.
[17179604.536000] ppdev: user-space parallel port driver
[17179605.056000] apm: BIOS not found.
[17179608.128000] Bluetooth: Core ver 2.8
[17179608.128000] NET: Registered protocol family 31
[17179608.128000] Bluetooth: HCI device and connection manager initialized
[17179608.128000] Bluetooth: HCI socket layer initialized
[17179608.144000] Bluetooth: L2CAP ver 2.8
[17179608.144000] Bluetooth: L2CAP socket layer initialized
[17179608.152000] Bluetooth: RFCOMM socket layer initialized
[17179608.152000] Bluetooth: RFCOMM TTY layer initialized
[17179608.152000] Bluetooth: RFCOMM ver 1.7
[17179609.196000] eth0: no IPv6 routers present
[17179611.328000] [drm] Initialized drm 1.0.1 20051102
[17179611.344000] **** SET: Misaligned resource pointer: d54de3a2 Type 07 Len 0
[17179611.344000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179611.344000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (
level, low) -> IRQ 10
[17179611.348000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179612.340000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179612.340000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179612.340000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179612.584000] [drm] Setting GART location based on old memory map
[17179612.584000] [drm] writeback test succeeded in 1 usecs
[17182533.468000] usb 1-1: USB disconnect, address 2
[17182536.796000] usb 1-2: new full speed USB device using ohci_hcd and address                                                               3
[17182925.456000] cdrom: open failed.
[17183553.148000] cdrom: open failed.
[17183580.416000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17183580.960000] ISO 9660 Extensions: RRIP_1991A
[17183937.612000] usb 1-2: USB disconnect, address 3
[17183967.968000] usb 1-2: new full speed USB device using ohci_hcd and address                                                               4
[17184067.896000] usb 1-2: USB disconnect, address 4
[17184076.296000] usb 1-2: new full speed USB device using ohci_hcd and address                                                               5
[17185817.784000] usb 1-2: USB disconnect, address 5
[17185897.532000] usb 1-2: new full speed USB device using ohci_hcd and address                                                               6

sudo ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:20:21:FE:72
          inet addr:82.46.23.156  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:20ff:fe21:fe72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44412960 (42.3 MiB)  TX bytes:2610612 (2.4 MiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

sudo iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

sudo less /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth0


Sorry, I am new to using Linux and I like it alot, I just need some real help.

Thanks in advance, Tom

---

### Post by TFX360 on 2006-08-27
[URL="http://www.ubuntuforums.org/showthread.php?t=190967&highlight=wpc54g"]http://www.ubuntuforums.org/showthread.php?t=190967&highlight=wpc54g
[/URL]

Could you use the above walkthrough as if it were your card of course replacing the drivers with yours. I can't find a good other walkthrough. Hope it helps,


TFX

---

