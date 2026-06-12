---
title: "Problems with my Ethernet card.Need Help!!!"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Urko on 2006-07-14
I have problems vith my ethernet card witch is Cnet pro200 10/100with tulip chip.I heard that this chip must be properly instaled but becouse i am beginer i don't know how to do this.Can anybody help me configure it???????????


If I type dmseg in terminal it write me this:

ubuntu@ubuntu:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000] BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[4294667.296000] BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[4294667.296000] BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[4294667.296000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000] BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[4294667.296000] BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fb970
[4294667.296000] On node 0 totalpages: 131056
[4294667.296000] DMA zone: 4096 pages, LIFO batch:0
[4294667.296000] DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000] Normal zone: 126960 pages, LIFO batch:31
[4294667.296000] HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI ) @ 0x00 0fa750
[4294667.296000] ACPI: RSDT (v001 AMIINT INTEL845 0x00000010 MSFT 0x00000097) @ 0x1fff0000
[4294667.296000] ACPI: FADT (v001 AMIINT INTEL845 0x00000011 MSFT 0x00000097) @ 0x1fff0030
[4294667.296000] ACPI: MADT (v001 AMIINT INTEL845 0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[4294667.296000] ACPI: DSDT (v001 INTEL BROKDALE 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:1 APIC version 20
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode: Flat. Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:de c00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper ini trd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1703.840 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.706000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes )
[4294670.708000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.728000] Memory: 508596k/524224k available (1976k kernel code, 15024k re served, 606k data, 288k init, 0k highmem)
[4294670.728000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294670.788000] Calibrating delay using timer specific routine.. 3410.30 BogoMI PS (lpj=1705153)
[4294670.788000] Security Framework v1.0.0 initialized
[4294670.788000] SELinux: Disabled at boot.
[4294670.788000] Mount-cache hash table entries: 512
[4294670.788000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 0 0000000 00000000 00000000 00000000
[4294670.788000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00 000000 00000000 00000000 00000000
[4294670.788000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.788000] CPU: L2 cache: 128K
[4294670.788000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[4294670.788000] mtrr: v2.0 (20020519)
[4294670.788000] CPU: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[4294670.788000] Enabling fast FPU save and restore... done.
[4294670.788000] Enabling unmasked SIMD FPU exception support... done.
[4294670.788000] Checking 'hlt' instruction... OK.
[4294670.792000] checking if image is initramfs... it is
[4294671.688000] Freeing initrd memory: 6838k freed
[4294671.705000] ACPI: Looking for DSDT ... not found!
[4294671.708000] ENABLING IO-APIC IRQs
[4294671.709000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294671.820000] NET: Registered protocol family 16
[4294671.820000] EISA bus registered
[4294671.820000] ACPI: bus type pci registered
[4294671.821000] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=3
[4294671.821000] PCI: Using configuration type 1
[4294671.822000] ACPI: Subsystem revision 20051216
[4294671.828000] ACPI: Interpreter enabled
[4294671.828000] ACPI: Using IOAPIC for interrupt routing
[4294671.829000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.829000] PCI: Probing PCI hardware (bus 00)
[4294671.833000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294671.833000] PCI quirk: region 0400-043f claimed by ICH4 GPIO
[4294671.833000] Boot video device is 0000:01:00.0
[4294671.834000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.834000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.851000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[4294671.857000] ACPI: Power Resource [URP1] (off)
[4294671.857000] ACPI: Power Resource [URP2] (off)
[4294671.857000] ACPI: Power Resource [FDDP] (off)
[4294671.858000] ACPI: Power Resource [LPTP] (off)
[4294671.860000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15 )
[4294671.860000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15 )
[4294671.861000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.861000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15 )
[4294671.862000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.862000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15 )
[4294671.863000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.863000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15 )
[4294671.864000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.864000] pnp: PnP ACPI init
[4294671.871000] pnp: PnP ACPI: found 12 devices
[4294671.871000] PnPBIOS: Disabled by ACPI PNP
[4294671.871000] PCI: Using ACPI for IRQ routing
[4294671.871000] PCI: If a device doesn't work, try "pci=routeirq". If it helps , post a report
[4294671.876000] PCI: Bridge: 0000:00:01.0
[4294671.876000] IO window: disabled.
[4294671.876000] MEM window: ddc00000-dfdfffff
[4294671.876000] PREFETCH window: cd700000-dd9fffff
[4294671.876000] PCI: Bridge: 0000:00:1e.0
[4294671.876000] IO window: d000-dfff
[4294671.876000] MEM window: dfe00000-dfefffff
[4294671.876000] PREFETCH window: dda00000-ddafffff
[4294671.876000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.877000] audit: initializing netlink socket (disabled)
[4294671.877000] audit(1152722706.876:1): initialized
[4294671.877000] VFS: Disk quotas dquot_6.5.1
[4294671.877000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.878000] Initializing Cryptographic API
[4294671.878000] io scheduler noop registered
[4294671.878000] io scheduler anticipatory registered
[4294671.878000] io scheduler deadline registered
[4294671.878000] io scheduler cfq registered
[4294671.878000] isapnp: Scanning for PnP cards...
[4294672.235000] isapnp: No Plug & Play device found
[4294672.291000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 i rq 1,12
[4294672.293000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.293000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.293000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294672.293000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.294000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.302000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.302000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.304000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[4294672.304000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.304000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294672.304000] mice: PS/2 mouse device common for all mice
[4294672.305000] EISA: Probing bus 0 at eisa.0
[4294672.305000] EISA: Detected 0 cards.
[4294672.305000] NET: Registered protocol family 2
[4294672.315000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.315000] TCP established hash table entries: 32768 (order: 5, 131072 byt es)
[4294672.315000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.315000] TCP: Hash tables configured (established 32768 bind 3276
[4294672.315000] TCP reno registered
[4294672.316000] TCP bic registered
[4294672.316000] NET: Registered protocol family 1
[4294672.316000] NET: Registered protocol family 8
[4294672.316000] NET: Registered protocol family 20
[4294672.316000] Using IPI Shortcut mode
[4294672.316000] ACPI wakeup devices:
[4294672.316000] ICHB PS2M PS2K UAR1 UAR2 USB1 USB2 MC9 SLT1 SLT2 SLT3 SLT4 SLT 5 SLPB
[4294672.316000] ACPI: (supports S0 S1 S4 S5)
[4294672.316000] Freeing unused kernel memory: 288k freed
[4294672.326000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.411000] vga16fb: initializing
[4294672.411000] vga16fb: mapped to 0xc00a0000
[4294672.571000] Console: switching to colour frame buffer device 80x25
[4294672.571000] fb0: VGA16 VGA frame buffer device
[4294673.731000] Capability LSM initialized
[4294673.806000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294674.976000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294674.976000] ICH2: chipset revision 5
[4294674.976000] ICH2: not 100% native mode: will probe irqs later
[4294674.976000] ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hdaMA, hdb: DMA
[4294674.976000] ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdcMA, hdd: pio
[4294674.976000] Probing IDE interface ide0...
[4294675.240000] hda: WDC WD800JB-00CRA1, ATA DISK drive
[4294675.495000] hdb: IBM-DTTA-351010, ATA DISK drive
[4294675.547000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.567000] Probing IDE interface ide1...
[4294676.239000] hdc: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[4294676.851000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.867000] hda: max request size: 128KiB
[4294676.890000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16 /63, UDMA(100)
[4294676.891000] hda: cache flushes not supported
[4294676.891000] hda: hda1 hda2 < hda5 >
[4294676.912000] hdb: max request size: 128KiB
[4294676.917000] hdb: 19807200 sectors (10141 MB) w/466KiB Cache, CHS=19650/16/6 3, UDMA(33)
[4294676.917000] hdb: cache flushes not supported
[4294676.917000] hdb: hdb1 < hdb5 >
[4294676.932000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA( 33)
[4294676.932000] Uniform CD-ROM driver Revision: 3.20
[4294677.470000] usbcore: registered new driver usbfs
[4294677.471000] usbcore: registered new driver hub
[4294677.474000] USB Universal Host Controller Interface driver v2.3
[4294677.475000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> I RQ 169
[4294677.475000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294677.475000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[4294677.476000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus num ber 1
[4294677.476000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x0000e800
[4294677.476000] hub 1-0:1.0: USB hub found
[4294677.476000] hub 1-0:1.0: 2 ports detected
[4294677.513000] ieee1394: Initialized config rom entry `ip1394'
[4294677.577000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> I RQ 177
[4294677.577000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294677.577000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[4294677.577000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus num ber 2
[4294677.577000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000ec00
[4294677.578000] hub 2-0:1.0: USB hub found
[4294677.578000] hub 2-0:1.0: 2 ports detected
[4294677.682000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294677.682000] ACPI: PCI Interrupt 0000:03:03.2[b] -> GSI 17 (level, low) -> I RQ 185
[4294677.734000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185] MMIO=[dfefe 800-dfefefff] Max Packet=[2048]
[4294678.995000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00023c003102c325]
[4294679.374000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294679.374000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294679.374000] ide: failed opcode was: unknown
[4294679.374000] end_request: I/O error, dev hdc, sector 1429184
[4294679.374000] Buffer I/O error on device hdc, logical block 357296
[4294680.001000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294680.001000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294680.001000] ide: failed opcode was: unknown
[4294680.001000] end_request: I/O error, dev hdc, sector 1429184
[4294680.001000] Buffer I/O error on device hdc, logical block 357296
[4294680.803000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294680.803000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294680.803000] ide: failed opcode was: unknown
[4294680.803000] end_request: I/O error, dev hdc, sector 1429184
[4294680.803000] Buffer I/O error on device hdc, logical block 357296
[4294681.331000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294681.331000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294681.331000] ide: failed opcode was: unknown
[4294681.331000] end_request: I/O error, dev hdc, sector 1429184
[4294681.331000] Buffer I/O error on device hdc, logical block 357296
[4294681.859000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294681.859000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294681.859000] ide: failed opcode was: unknown
[4294681.859000] end_request: I/O error, dev hdc, sector 1429184
[4294681.859000] Buffer I/O error on device hdc, logical block 357296
[4294682.387000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294682.387000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294682.387000] ide: failed opcode was: unknown
[4294682.387000] end_request: I/O error, dev hdc, sector 1429184
[4294682.387000] Buffer I/O error on device hdc, logical block 357296
[4294683.623000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294683.816000] ISO 9660 Extensions: RRIP_1991A
[4294683.941000] loop: loaded (max 8 devices)
[4294683.964000] Registering unionfs 1.1.2
[4294684.174000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[4294756.497000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[4294756.497000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> I RQ 185
[4294756.521000] eth0: Davicom DM9102 at pci0000:03:00.0, 00:08:a1:84:95:d2, irq 185.
[4294756.525000] Linux Tulip driver version 1.1.13 (December 15, 2004)
[4294787.416000] Linux agpgart interface v0.101 (c) Dave Jones
[4294787.523000] agpgart: Detected an Intel i845 Chipset.
[4294787.527000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294787.672000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294788.390000] NET: Registered protocol family 17
[4294788.513000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294788.963000] Floppy drive(s): fd0 is 1.44M
[4294788.971000] parport: PnPBIOS parport detected.
[4294788.971000] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,EPP,ECP,DMA]
[4294788.978000] FDC 0 is a post-1991 82077
[4294789.056000] input: PC Speaker as /class/input/input1
[4294789.339000] Real Time Clock Driver v1.12
[4294789.692000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[4294790.305000] hw_random: RNG not detected
[4294790.341000] ts: Compaq touchscreen protocol output
[4294790.888000] gameport: EMU10K1 is pci0000:03:03.1/gameport0, io 0xdc00, spee d 978kHz
[4294791.717000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 21 (level, low) -> I RQ 193
[4294794.367000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294794.368000] md: bitmap version 4.39
[4294795.021000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294810.670000] ACPI: Power Button (FF) [PWRF]
[4294810.670000] ACPI: Power Button (CM) [PWRB]
[4294810.670000] ACPI: Sleep Button (CM) [SLPB]
[4294810.848000] ibm_acpi: ec object not found
[4294810.890000] pcc_acpi: loading...
[4294828.106000] lp0: using parport0 (interrupt-driven).
[4294828.157000] ppdev: user-space parallel port driver
[4294829.292000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294829.292000] apm: overridden by ACPI.
[4294837.505000] NET: Registered protocol family 10
[4294837.506000] lo: Disabled Privacy Extensions
[4294837.506000] IPv6 over IPv4 tunneling driver
[4294846.406000] Bluetooth: Core ver 2.8
[4294846.406000] NET: Registered protocol family 31
[4294846.406000] Bluetooth: HCI device and connection manager initialized
[4294846.406000] Bluetooth: HCI socket layer initialized
[4294846.571000] Bluetooth: L2CAP ver 2.8
[4294846.571000] Bluetooth: L2CAP socket layer initialized
[4294847.006000] Bluetooth: RFCOMM socket layer initialized
[4294847.006000] Bluetooth: RFCOMM TTY layer initialized
[4294847.006000] Bluetooth: RFCOMM ver 1.7
[4294847.906000] eth0: no IPv6 routers present

What to do now???????

---

### Post by cyberlite on 2006-07-14
Hey there
First of all goto the network progam and see ig you see you card?? Go to system them network tools.

Click net work devices see if it's there. If so try to ping 127.0.0.1
Then get back to me.

---

### Post by monkieie on 2006-07-14
please go to the terminal and enter:
**ifconfig**

and paste the results here. 

Pinging the localhost (Click net work devices see if it's there. If so try to ping 127.0.0.1) is a good starting point, so that you can see if the card handles packets at all. Are you behind a firewall / using a proxy? Using DHCP? Has your card worked on other systems? Do you have a link?

Please give an accurate problem description.

---

### Post by Urko on 2006-07-14
if I type ifconfig write me this:

eth0

Link encap: Ethernet HWaddr: 00:0C:29:40:A1:7D
inet 6adrr: fe80::20C:29ff.fe40:a17d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:15 errors:0 dropped:0 overruns:0 frame:0
TX packets:10 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:1752 (1.7 KiB) TX Bytes:4914 (4.7KiB)
Interrupt:185 Base addres:0x1080

lo

Link encap:Local Loopback
inet addr:127.0.0.1  Net mask:255.0.0.0.
inet6 addr:1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:0
RX bytes:1556 (1.5 KiB) TX Bytes:1556 (1.5KiB)

My ethernet card system detect in network devices.But I am running Ubuntu in Wmware station!!!!

Please what I must do next and sorry for so long answer.I have some tehnical problems with my pc during the writhing this post.

---

### Post by Urko on 2006-07-15
am..can enybody please help me:( ?

---

### Post by [S|G] on 2006-07-15
As you could see, your network card is being detected by the system. Try this:
```

ifconfig eth0 down
ifconfig eth0 up

```

EDIT: I corrected the code.

---

### Post by immesys on 2006-07-15
I had exactly the same problem on the same brand of card.

It appears as if the problem might be that it is not as compatible with tulip as it claims to be.

I'm new at this so ignore me if you know better but I solved
the problem by looking at:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by MindFul on 2006-07-22
I had the same problem and I found a posting from h3h_timo, with a very simple solution that works for me.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

thank you very much timo.

---

