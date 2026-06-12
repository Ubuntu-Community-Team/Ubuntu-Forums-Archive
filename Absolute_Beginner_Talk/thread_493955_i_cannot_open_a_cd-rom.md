---
title: "i cannot open a cd-rom"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by xxchrisxx555 on 2007-07-06
i cannot open a cd-rom  containing a windows game

---

### Post by Cypher on 2007-07-06
When you put the CD into the drive, does it show up on your desktop?

---

### Post by xxchrisxx555 on 2007-07-06
i does not show up and will not mount
i have no problems with cds or dvds

---

### Post by Cypher on 2007-07-06
You mean Music CD's? A CD with a Windows game is still a CD and is no different to Ubuntu. Open up a terminal and after instering the CD, show us the output of
```

dmesg

```

---

### Post by xxchrisxx555 on 2007-07-06
[17182480.896000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182480.896000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182480.896000] ide: failed opcode was: unknown
[17182480.896000] end_request: I/O error, dev hdc, sector 68
[17182480.896000] Buffer I/O error on device hdc, logical block 17
[17182482.336000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182482.336000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182482.336000] ide: failed opcode was: unknown
[17182482.336000] end_request: I/O error, dev hdc, sector 68
[17182482.336000] Buffer I/O error on device hdc, logical block 17
[17182483.864000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182483.864000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182483.864000] ide: failed opcode was: unknown
[17182483.864000] end_request: I/O error, dev hdc, sector 8
[17182483.864000] Buffer I/O error on device hdc, logical block 2
[17182494.940000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182494.940000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182494.940000] ide: failed opcode was: unknown
[17182494.940000] end_request: I/O error, dev hdc, sector 68
[17182494.940000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=17, block=17
[17182918.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182918.692000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182918.692000] ide: failed opcode was: unknown
[17182918.692000] end_request: I/O error, dev hdc, sector 68
[17182918.696000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=17, block=17
chris@chris-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri May 18 23:39:08 UTC 2007 (Ubuntu 2.6.17-11.38-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffe2800 (usable)
[17179569.184000]  BIOS-e820: 000000001ffe2800 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131042
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126946 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde50
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d30304 ASL  0x00000061) @ 0x000fde64
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d30304 ASL  0x00000061) @ 0x000fde90
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0140b000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1994.416 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.640000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.640000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.656000] Memory: 509920k/524168k available (1911k kernel code, 13616k reserved, 1073k data, 308k init, 0k highmem)
[17179571.656000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.736000] Calibrating delay using timer specific routine.. 3993.42 BogoMIPS (lpj=7986859)
[17179571.736000] Security Framework v1.0.0 initialized
[17179571.736000] SELinux:  Disabled at boot.
[17179571.736000] Mount-cache hash table entries: 512
[17179571.736000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[17179571.736000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[17179571.736000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.736000] CPU: L2 cache: 512K
[17179571.736000] CPU: Hyper-Threading is disabled
[17179571.736000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00000400 00000000 00000000
[17179571.736000] Checking 'hlt' instruction... OK.
[17179571.752000] SMP alternatives: switching to UP code
[17179571.752000] Freeing SMP alternatives: 16k freed
[17179571.752000] checking if image is initramfs... it is
[17179572.372000] Freeing initrd memory: 5326k freed
[17179572.372000] ACPI: Core revision 20060707
[17179572.376000] ACPI: Looking for DSDT ... not found!
[17179572.412000] ACPI: setting ELCR to 0200 (from 0800)
[17179575.544000] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
[17179575.544000] SMP motherboard not detected.
[17179575.544000] Local APIC not detected. Using dummy APIC emulation.
[17179575.544000] Brought up 1 CPUs
[17179575.544000] migration_cost=0
[17179575.544000] NET: Registered protocol family 16
[17179575.544000] EISA bus registered
[17179575.544000] ACPI: bus type pci registered
[17179575.556000] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
[17179575.556000] PCI: Using configuration type 1
[17179575.556000] Setting up standard PCI resources
[17179575.588000] ACPI: Interpreter enabled
[17179575.588000] ACPI: Using PIC for interrupt routing
[17179575.588000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179575.588000] PCI: Probing PCI hardware (bus 00)
[17179575.588000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179575.664000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179575.664000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179575.664000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179575.664000] Boot video device is 0000:01:00.0
[17179575.664000] PCI: Transparent bridge - 0000:00:1e.0
[17179575.664000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179575.832000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179575.832000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[17179575.832000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[17179575.836000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[17179575.836000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179575.840000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179575.852000] ACPI: Power Resource [PADA] (on)
[17179575.852000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179575.852000] pnp: PnP ACPI init
[17179576.060000] pnp: PnP ACPI: found 15 devices
[17179576.060000] PnPBIOS: Disabled by ACPI PNP
[17179576.060000] PCI: Using ACPI for IRQ routing
[17179576.060000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179576.096000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179576.096000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179576.096000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179576.096000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179576.096000] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[17179576.096000] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[17179576.096000] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[17179576.096000] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[17179576.096000] pnp: 00:03: ioport range 0x8e0-0x8ff has been reserved
[17179576.096000] pnp: 00:08: ioport range 0x900-0x91f has been reserved
[17179576.096000] pnp: 00:08: ioport range 0x3f0-0x3f1 has been reserved
[17179576.096000] PCI: Bridge: 0000:00:01.0
[17179576.096000]   IO window: c000-cfff
[17179576.096000]   MEM window: fc000000-fdffffff
[17179576.096000]   PREFETCH window: e0000000-e7ffffff
[17179576.096000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[17179576.096000]   IO window: 0000e000-0000e0ff
[17179576.096000]   IO window: 0000e400-0000e4ff
[17179576.096000]   PREFETCH window: 30000000-31ffffff
[17179576.096000]   MEM window: f4000000-f5ffffff
[17179576.096000] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[17179576.096000]   IO window: 0000e800-0000e8ff
[17179576.096000]   IO window: 0000f000-0000f0ff
[17179576.096000]   PREFETCH window: 32000000-33ffffff
[17179576.096000]   MEM window: f6000000-f7ffffff
[17179576.096000] PCI: Bridge: 0000:00:1e.0
[17179576.096000]   IO window: e000-ffff
[17179576.096000]   MEM window: f4000000-fbffffff
[17179576.096000]   PREFETCH window: 30000000-34ffffff
[17179576.096000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179576.096000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[17179576.100000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.100000] PCI: setting IRQ 11 as level-triggered
[17179576.100000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.100000] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[17179576.100000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.100000] NET: Registered protocol family 2
[17179576.140000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179576.140000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179576.140000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179576.140000] TCP: Hash tables configured (established 16384 bind 8192)
[17179576.140000] TCP reno registered
[17179576.140000] audit: initializing netlink socket (disabled)
[17179576.140000] audit(1183730928.140:1): initialized
[17179576.140000] VFS: Disk quotas dquot_6.5.1
[17179576.140000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179576.140000] Initializing Cryptographic API
[17179576.140000] io scheduler noop registered
[17179576.140000] io scheduler anticipatory registered
[17179576.140000] io scheduler deadline registered
[17179576.140000] io scheduler cfq registered (default)
[17179576.140000] isapnp: Scanning for PnP cards...
[17179576.492000] isapnp: No Plug & Play device found
[17179576.528000] Real Time Clock Driver v1.12ac
[17179576.528000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179576.528000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179576.532000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179576.532000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179576.532000] PCI: setting IRQ 5 as level-triggered
[17179576.532000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179576.532000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179576.532000] mice: PS/2 mouse device common for all mice
[17179576.532000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179576.532000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179576.532000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179576.532000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179576.536000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179576.536000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179576.536000] EISA: Probing bus 0 at eisa.0
[17179576.536000] EISA: Detected 0 cards.
[17179576.540000] TCP bic registered
[17179576.540000] NET: Registered protocol family 1
[17179576.540000] NET: Registered protocol family 8
[17179576.540000] NET: Registered protocol family 20
[17179576.540000] Using IPI No-Shortcut mode
[17179576.540000] ACPI: (supports S0 S1 S3 S4 S5)
[17179576.540000] Freeing unused kernel memory: 308k freed
[17179576.544000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179577.680000] Capability LSM initialized
[17179578.020000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179578.020000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179578.080000] ACPI: Thermal Zone [THM] (60 C)
[17179578.744000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179578.744000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179578.748000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179578.748000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179578.748000] ICH3M: chipset revision 2
[17179578.748000] ICH3M: not 100% native mode: will probe irqs later
[17179578.748000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179578.748000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[17179578.748000] Probing IDE interface ide0...
[17179579.036000] hda: HITACHI_DK23EA-30, ATA DISK drive
[17179579.708000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.708000] Probing IDE interface ide1...
[17179580.448000] hdc: Samsung CD-RW/DVD-ROM SN-324B, ATAPI CD/DVD-ROM drive
[17179581.120000] ide1 at 0x170-0x177,0x376 on irq 15
[17179581.132000] hda: max request size: 128KiB
[17179581.140000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[17179581.140000] hda: cache flushes supported
[17179581.144000]  hda: hda1 hda2 < hda5 >
[17179581.224000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179581.224000] Uniform CD-ROM driver Revision: 3.20
[17179581.672000] usbcore: registered new driver usbfs
[17179581.672000] usbcore: registered new driver hub
[17179581.672000] USB Universal Host Controller Interface driver v3.0
[17179581.672000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179581.672000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179581.672000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179581.672000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179581.672000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17179581.672000] usb usb1: configuration #1 chosen from 1 choice
[17179581.672000] hub 1-0:1.0: USB hub found
[17179581.672000] hub 1-0:1.0: 2 ports detected
[17179581.776000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179581.776000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179581.776000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179581.776000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179581.776000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[17179581.776000] usb usb2: configuration #1 chosen from 1 choice
[17179581.776000] hub 2-0:1.0: USB hub found
[17179581.776000] hub 2-0:1.0: 2 ports detected
[17179581.880000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179581.880000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179581.880000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179581.880000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179581.880000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179581.880000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[17179581.880000] usb usb3: configuration #1 chosen from 1 choice
[17179581.880000] hub 3-0:1.0: USB hub found
[17179581.880000] hub 3-0:1.0: 2 ports detected
[17179582.072000] Attempting manual resume
[17179582.088000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179582.088000] EXT3-fs: write access will be enabled during recovery.
[17179582.120000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179582.288000] usb 2-2: configuration #1 chosen from 1 choice
[17179582.300000] usbcore: registered new driver hiddev
[17179582.320000] input: USB_PS2 Optical Mouse as /class/input/input1
[17179582.320000] input: USB HID v1.10 Mouse [USB_PS2 Optical Mouse] on usb-0000:00:1d.1-2
[17179582.320000] usbcore: registered new driver usbhid
[17179582.320000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.960000] kjournald starting.  Commit interval 5 seconds
[17179582.960000] EXT3-fs: recovery complete.
[17179582.976000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.320000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.336000] agpgart: Detected an Intel i845 Chipset.
[17179597.340000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179597.348000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.352000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.472000] hw_random: RNG not detected
[17179597.932000] input: PC Speaker as /class/input/input2
[17179598.168000] parport: PnPBIOS parport detected.
[17179598.168000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.192000] Floppy drive(s): fd0 is 1.44M
[17179598.212000] FDC 0 is a post-1991 82077
[17179598.216000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.216000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:012a]
[17179598.216000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.216000] Yenta: Routing CardBus interrupts to PCI
[17179598.216000] Yenta TI: socket 0000:02:01.0, mfunc 0x01261222, devctl 0x64
[17179598.448000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179598.448000] Socket status: 30000006
[17179598.448000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179598.448000] cs: IO port probe 0xe000-0xffff: clean.
[17179598.448000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179598.448000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x34ffffff
[17179598.448000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.448000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:012a]
[17179598.448000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.448000] Yenta: Routing CardBus interrupts to PCI
[17179598.448000] Yenta TI: socket 0000:02:01.1, mfunc 0x01261222, devctl 0x64
[17179598.560000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x9b4cb1, caps: 0x884793/0x0
[17179598.560000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179598.600000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179598.680000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179598.680000] Socket status: 30000020
[17179598.680000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179598.680000] cs: IO port probe 0xe000-0xffff: clean.
[17179598.680000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179598.680000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x34ffffff
[17179598.704000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179598.704000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179598.704000] 0000:02:00.0: 3Com PCI 3c905C Tornado at e089cc00.
[17179598.888000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179598.888000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179599.016000] ts: Compaq touchscreen protocol output
[17179599.404000] pccard: CardBus card inserted into slot 1
[17179599.456000] intel8x0_measure_ac97_clock: measured 55452 usecs
[17179599.456000] intel8x0: clocking to 48000
[17179599.520000] cs: IO port probe 0x100-0x3af: clean.
[17179599.520000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.524000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.524000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.524000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.560000] cs: IO port probe 0x100-0x3af: clean.
[17179599.560000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.560000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.560000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.564000] cs: IO port probe 0xa00-0xaff: clean.
[17179602.680000] input: PS/2 Generic Mouse as /class/input/input4
[17179603.124000] lp0: using parport0 (interrupt-driven).
[17179603.184000] ndiswrapper version 1.47 loaded (smp=yes)
[17179603.296000] ndiswrapper: driver lsbcmnds (The Linksys Group, Inc.,07/17/2003, 3.30.15.0) loaded
[17179603.296000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[17179603.296000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179603.296000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[17179603.300000] ndiswrapper: using IRQ 11
[17179603.664000] wlan0: ethernet device 00:0c:41:a9:ec:b1 using NDIS driver: lsbcmnds, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[17179603.664000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17179603.668000] usbcore: registered new driver ndiswrapper
[17179603.708000] Adding 1228932k swap on /dev/disk/by-uuid/0a3fef55-0495-4c13-8160-f8a28e829ff2.  Priority:-1 extents:1 across:1228932k
[17179603.792000] EXT3 FS on hda1, internal journal
[17179605.148000] ACPI: AC Adapter [AC] (on-line)
[17179605.624000] ACPI: Battery Slot [BAT0] (battery present)
[17179605.624000] ACPI: Battery Slot [BAT1] (battery absent)
[17179605.644000] ACPI: Lid Switch [LID]
[17179605.644000] ACPI: Power Button (CM) [PBTN]
[17179605.644000] ACPI: Sleep Button (CM) [SBTN]
[17179605.692000] ACPI: ACPI Dock Station Driver 
[17179605.800000] ibm_acpi: ec object not found
[17179605.836000] pcc_acpi: loading...
[17179605.964000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179609.500000] [drm] Initialized drm 1.0.1 20051102
[17179609.508000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179609.508000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179610.460000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179610.460000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179610.460000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179610.460000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179610.460000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179610.460000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179610.704000] [drm] Setting GART location based on new memory map
[17179610.704000] [drm] writeback test succeeded in 1 usecs
[17179610.928000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179610.928000] apm: overridden by ACPI.
[17179623.200000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179623.200000] eth0:  setting half-duplex.
[17179623.972000] Bluetooth: Core ver 2.8
[17179623.972000] NET: Registered protocol family 31
[17179623.972000] Bluetooth: HCI device and connection manager initialized
[17179623.972000] Bluetooth: HCI socket layer initialized
[17179623.992000] Bluetooth: L2CAP ver 2.8
[17179623.992000] Bluetooth: L2CAP socket layer initialized
[17179623.996000] Bluetooth: RFCOMM socket layer initialized
[17179623.996000] Bluetooth: RFCOMM TTY layer initialized
[17179623.996000] Bluetooth: RFCOMM ver 1.7
[17179631.820000] NET: Registered protocol family 10
[17179631.820000] lo: Disabled Privacy Extensions
[17179631.820000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179631.820000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179631.820000] IPv6 over IPv4 tunneling driver
[17179636.772000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179637.600000] ISO 9660 Extensions: RRIP_1991A
[17179644.368000] NET: Registered protocol family 17
[17179645.136000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17179661.244000] wlan0: no IPv6 routers present
[17181242.056000] usb 2-2: USB disconnect, address 2
[17181242.184000] hub 3-0:1.0: over-current change on port 2
[17181242.308000] hub 2-0:1.0: over-current change on port 2
[17181242.980000] hub 3-0:1.0: over-current change on port 2
[17181244.676000] hub 2-0:1.0: over-current change on port 2
[17181244.780000] hub 3-0:1.0: over-current change on port 2
[17181244.928000] hub 2-0:1.0: over-current change on port 2
[17181245.032000] hub 3-0:1.0: over-current change on port 2
[17181245.448000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17181245.596000] ACPI: docking
[17181247.356000] usb 2-2: configuration #1 chosen from 1 choice
[17181247.376000] input: USB_PS2 Optical Mouse as /class/input/input5
[17181247.376000] input: USB HID v1.10 Mouse [USB_PS2 Optical Mouse] on usb-0000:00:1d.1-2
[17181254.364000] usb 2-2: USB disconnect, address 3
[17181254.912000] hub 3-0:1.0: over-current change on port 2
[17181255.656000] hub 2-0:1.0: over-current change on port 2
[17181255.760000] hub 3-0:1.0: over-current change on port 2
[17181258.496000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17181258.496000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17181258.500000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17181258.512000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17181258.512000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17181258.512000] psmouse.c: issuing reconnect request
[17181500.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181500.692000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17181500.692000] ide: failed opcode was: unknown
[17181500.692000] end_request: I/O error, dev hdc, sector 64
[17181500.692000] Buffer I/O error on device hdc, logical block 16
[17181502.132000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181502.132000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17181502.132000] ide: failed opcode was: unknown
[17181502.132000] end_request: I/O error, dev hdc, sector 68
[17181502.132000] Buffer I/O error on device hdc, logical block 17
[17181504.088000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181504.088000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17181504.088000] ide: failed opcode was: unknown
[17181504.088000] end_request: I/O error, dev hdc, sector 64
[17181504.088000] Buffer I/O error on device hdc, logical block 16
[17181505.528000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181505.528000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17181505.528000] ide: failed opcode was: unknown
[17181505.528000] end_request: I/O error, dev hdc, sector 68
[17181505.528000] Buffer I/O error on device hdc, logical block 17
[17181948.236000] hub 2-0:1.0: over-current change on port 2
[17181948.340000] hub 3-0:1.0: over-current change on port 2
[17181948.728000] usb 2-2: new low speed USB device using uhci_hcd and address 4
[17181948.740000] ACPI: docking
[17181952.148000] usb 2-2: configuration #1 chosen from 1 choice
[17181952.188000] input: USB_PS2 Optical Mouse as /class/input/input6
[17181952.188000] input: USB HID v1.10 Mouse [USB_PS2 Optical Mouse] on usb-0000:00:1d.1-2
[17182165.808000] ACPI: docking
[17182167.836000] usb 2-2: USB disconnect, address 4
[17182172.448000] hub 2-0:1.0: over-current change on port 2
[17182172.552000] hub 3-0:1.0: over-current change on port 2
[17182172.700000] hub 2-0:1.0: over-current change on port 2
[17182173.372000] ACPI: docking
[17182173.776000] usb 2-2: new low speed USB device using uhci_hcd and address 5
[17182173.948000] usb 2-2: configuration #1 chosen from 1 choice
[17182173.968000] input: USB_PS2 Optical Mouse as /class/input/input7
[17182173.968000] input: USB HID v1.10 Mouse [USB_PS2 Optical Mouse] on usb-0000:00:1d.1-2
[17182480.896000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182480.896000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182480.896000] ide: failed opcode was: unknown
[17182480.896000] end_request: I/O error, dev hdc, sector 68
[17182480.896000] Buffer I/O error on device hdc, logical block 17
[17182482.336000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182482.336000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182482.336000] ide: failed opcode was: unknown
[17182482.336000] end_request: I/O error, dev hdc, sector 68
[17182482.336000] Buffer I/O error on device hdc, logical block 17
[17182483.864000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182483.864000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182483.864000] ide: failed opcode was: unknown
[17182483.864000] end_request: I/O error, dev hdc, sector 8
[17182483.864000] Buffer I/O error on device hdc, logical block 2
[17182494.940000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182494.940000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182494.940000] ide: failed opcode was: unknown
[17182494.940000] end_request: I/O error, dev hdc, sector 68
[17182494.940000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=17, block=17
[17182918.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17182918.692000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17182918.692000] ide: failed opcode was: unknown
[17182918.692000] end_request: I/O error, dev hdc, sector 68
[17182918.696000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=17, block=17
[17183486.912000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183486.912000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183486.912000] ide: failed opcode was: unknown
[17183486.916000] end_request: I/O error, dev hdc, sector 68
[17183486.916000] Buffer I/O error on device hdc, logical block 17
[17183488.352000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183488.352000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183488.352000] ide: failed opcode was: unknown
[17183488.352000] end_request: I/O error, dev hdc, sector 68
[17183488.352000] Buffer I/O error on device hdc, logical block 17
[17183490.480000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183490.480000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183490.480000] ide: failed opcode was: unknown
[17183490.480000] end_request: I/O error, dev hdc, sector 68
[17183490.480000] Buffer I/O error on device hdc, logical block 17
[17183577.232000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183577.232000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183577.232000] ide: failed opcode was: unknown
[17183577.232000] end_request: I/O error, dev hdc, sector 68
[17183577.232000] Buffer I/O error on device hdc, logical block 17
[17183578.672000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183578.672000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183578.672000] ide: failed opcode was: unknown
[17183578.672000] end_request: I/O error, dev hdc, sector 68
[17183578.672000] Buffer I/O error on device hdc, logical block 17
[17183580.288000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183580.288000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183580.288000] ide: failed opcode was: unknown
[17183580.288000] end_request: I/O error, dev hdc, sector 8
[17183580.288000] Buffer I/O error on device hdc, logical block 2

---

### Post by xxchrisxx555 on 2007-07-06
i think it is just a bad disk i put another in and it worked

---

### Post by Cypher on 2007-07-06
Yeah I was just going to suggest that as it's having a hard time reading the data on there..

---

### Post by 3rdalbum on 2007-07-06
> **xxchrisxx555 said:**
> 
[17183490.480000] Buffer I/O error on device hdc, logical block 17
[17183577.232000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183577.232000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183577.232000] ide: failed opcode was: unknown
[17183577.232000] end_request: I/O error, dev hdc, sector 68
[17183577.232000] Buffer I/O error on device hdc, logical block 17
[17183578.672000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183578.672000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183578.672000] ide: failed opcode was: unknown
[17183578.672000] end_request: I/O error, dev hdc, sector 68
[17183578.672000] Buffer I/O error on device hdc, logical block 17
[17183580.288000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183580.288000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183580.288000] ide: failed opcode was: unknown
[17183580.288000] end_request: I/O error, dev hdc, sector 8
[17183580.288000] Buffer I/O error on device hdc, logical block 2

> i think it is just a bad disk i put another in and it worked

Thanks for posting your dmesg log, from those last lines I've quoted above it looks like your diagnosis is correct. That is a bad disc.

---

