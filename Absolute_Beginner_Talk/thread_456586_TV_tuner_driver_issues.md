---
title: "TV tuner driver issues"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by boe409 on 2007-05-27
Ok here's my problem. I downloaded ubuntu 7.04 and got it installed, but it dosn't load the driver for my TV tuner. 

I assume thats the problem due to the fact that I can't find the driver with device manager.

I went to the TV Time website ( thats the program that I would like to use and followed thier faq advice but it didn't help. So that brings me here, following is the output from typing the commands 
: dmesg 
: modprobe saa7134
: modprobe saa7134 card=1
; modprobe saa7134 card=1 tuner=1

Output follows:::::

user@user-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fef0000 end: 000000007fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000003000 end: 000000007fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fff3000 size: 000000000000d000 end: 0000000080000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f72b0
[    0.000000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3000
[    0.000000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3040
[    0.000000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Detected 2672.776 MHz processor.
[   16.036182] Built 1 zonelists.  Total pages: 520177
[   16.036187] Kernel command line: root=UUID=395afe8c-4ae8-4b03-b2a3-003aa24bde32 ro quiet splash
[   16.036345] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   16.036352] mapped APIC to ffffd000 (02012000)
[   16.036355] Enabling fast FPU save and restore... done.
[   16.036358] Enabling unmasked SIMD FPU exception support... done.
[   16.036370] Initializing CPU#0
[   16.036454] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.037788] Console: colour VGA+ 80x25
[   16.038373] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.038960] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.130384] Memory: 2067892k/2097088k available (1992k kernel code, 27920k reserved, 893k data, 328k init, 1179584k highmem)
[   16.130396] virtual kernel memory layout:
[   16.130397]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.130398]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.130399]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.130400]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.130401]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   16.130402]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   16.130403]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   16.130406] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.208410] Calibrating delay using timer specific routine.. 5349.67 BogoMIPS (lpj=10699348)
[   16.208460] Security Framework v1.0.0 initialized
[   16.208471] SELinux:  Disabled at boot.
[   16.208489] Mount-cache hash table entries: 512
[   16.208670] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[   16.208684] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.208687] CPU: L2 cache: 512K
[   16.208689] CPU: Hyper-Threading is disabled
[   16.208692] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00003080 00000400 00000000 00000000
[   16.208705] Compat vDSO mapped to ffffe000.
[   16.208711] Remapping vsyscall page to ffffe000
[   16.208724] Checking 'hlt' instruction... OK.
[   16.224532] SMP alternatives: switching to UP code
[   16.224790] Freeing SMP alternatives: 11k freed
[   16.224998] Early unpacking initramfs... done
[   16.522086] ACPI: Core revision 20060707
[   16.529863] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.531375] ACPI: setting ELCR to 0200 (from 0a28)
[   16.533467] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[   16.533474] SMP motherboard not detected.
[   16.533476] Local APIC not detected. Using dummy APIC emulation.
[   16.533522] Brought up 1 CPUs
[   16.533788] Booting paravirtualized kernel on bare hardware
[   16.552348] Time: 22:48:34  Date: 04/27/107
[   16.552379] NET: Registered protocol family 16
[   16.552478] EISA bus registered
[   16.552484] ACPI: bus type pci registered
[   16.592653] PCI: PCI BIOS revision 2.10 entry at 0xfb400, last bus=1
[   16.592655] PCI: Using configuration type 1
[   16.592657] Setting up standard PCI resources
[   16.609188] ACPI: Interpreter enabled
[   16.609192] ACPI: Using PIC for interrupt routing
[   16.609784] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.609790] PCI: Probing PCI hardware (bus 00)
[   16.609858] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.610234] Enabling SiS 96x SMBus.
[   16.611266] Boot video device is 0000:01:00.0
[   16.611348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.631960] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.632208] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   16.632464] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.632708] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.632951] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.633196] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.633442] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.633685] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.636107] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.636119] pnp: PnP ACPI init
[   16.639588] pnp: PnP ACPI: found 14 devices
[   16.639594] PnPBIOS: Disabled by ACPI PNP
[   16.639655] PCI: Using ACPI for IRQ routing
[   16.639659] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.669173] NET: Registered protocol family 8
[   16.669175] NET: Registered protocol family 20
[   16.669815] PCI: Bridge: 0000:00:01.0
[   16.669818]   IO window: disabled.
[   16.669827]   MEM window: ec000000-edffffff
[   16.669833]   PREFETCH window: e0000000-e7ffffff
[   16.669879] NET: Registered protocol family 2
[   16.708348] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.708524] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.709545] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.710198] TCP: Hash tables configured (established 131072 bind 65536)
[   16.710203] TCP reno registered
[   16.720432] checking if image is initramfs... it is
[   17.301923] Freeing initrd memory: 7017k freed
[   17.302320] audit: initializing netlink socket (disabled)
[   17.302335] audit(1180306114.452:1): initialized
[   17.302427] highmem bounce pool size: 64 pages
[   17.302490] VFS: Disk quotas dquot_6.5.1
[   17.302513] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.302565] io scheduler noop registered
[   17.302568] io scheduler anticipatory registered
[   17.302571] io scheduler deadline registered
[   17.302579] io scheduler cfq registered (default)
[   17.384287] isapnp: Scanning for PnP cards...
[   17.738104] isapnp: No Plug & Play device found
[   17.766843] Real Time Clock Driver v1.12ac
[   17.766895] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.767020] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.767903] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.768288] mice: PS/2 mouse device common for all mice
[   17.768873] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.769127] input: Macintosh mouse button emulation as /class/input/input0
[   17.769164] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.769168] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.769457] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.769669] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.769674] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.769795] EISA: Probing bus 0 at eisa.0
[   17.769805] Cannot allocate resource for EISA slot 1
[   17.769814] Cannot allocate resource for EISA slot 4
[   17.769830] EISA: Detected 0 cards.
[   17.800037] TCP cubic registered
[   17.800048] NET: Registered protocol family 1
[   17.800071] Using IPI No-Shortcut mode
[   17.800168] ACPI: (supports S0 S3 S4 S5)
[   17.800215]   Magic number: 7:146:857
[   17.800340]   hash matches device ptyv9
[   17.800354]   hash matches device ptysc
[   17.800667] Freeing unused kernel memory: 328k freed
[   17.803967] Time: tsc clocksource has been installed.
[   17.817145] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.047969] Capability LSM initialized
[   19.087156] ACPI: Fan [FAN] (on)
[   19.093209] ACPI: Thermal Zone [THRM] (30 C)
[   19.638332] ieee1394: Initialized config rom entry `ip1394'
[   19.663183] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[   19.663188] PCI: setting IRQ 3 as level-triggered
[   19.663191] ACPI: PCI Interrupt 0000:00:02.3[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   19.715046] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[3]  MMIO=[ee425000-ee4257ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[   19.726692] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   19.726911] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   19.726914] PCI: setting IRQ 11 as level-triggered
[   19.726918] ACPI: PCI Interrupt 0000:00:02.5[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.726930] SIS5513: chipset revision 0
[   19.726932] SIS5513: not 100% native mode: will probe irqs later
[   19.726948] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[   19.726969]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA
[   19.726986]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[   19.726996] Probing IDE interface ide0...
[   19.751260] usbcore: registered new interface driver usbfs
[   19.751284] usbcore: registered new interface driver hub
[   19.751308] usbcore: registered new device driver usb
[   19.752147] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.777414] sis900.c: v1.08.10 Apr. 2 2006
[   19.929545] FDC 0 is a post-1991 82077
[   20.019527] hda: ST3120023A, ATA DISK drive
[   20.299447] hdb: ST3500630A, ATA DISK drive
[   20.355990] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.361466] Probing IDE interface ide1...
[   20.995204] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[   21.095225] hdc: SONY CD-RW CRX210E1, ATAPI CD/DVD-ROM drive
[   21.879022] hdd: IDE DVD-ROM 16X, ATAPI CD/DVD-ROM drive
[   21.936691] ide1 at 0x170-0x177,0x376 on irq 15
[   21.947342] SCSI subsystem initialized
[   21.953487] libata version 2.20 loaded.
[   21.959450] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   21.959455] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   21.959472] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   21.959818] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   21.959837] ohci_hcd 0000:00:03.0: irq 11, io mem 0xee420000
[   21.969995] hda: max request size: 128KiB
[   21.979748] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   21.980586] hda: cache flushes supported
[   21.980627]  hda: hda1 hda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   22.016925] hub 1-0:1.0: USB hub found
[   22.016936] hub 1-0:1.0: 2 ports detected
[   22.016948]  hda5 >
[   22.017706] hdb: max request size: 512KiB
[   22.066432] hdb: 976773168 sectors (500107 MB) w/16384KiB Cache, CHS=60801/255/63, UDMA(100)
[   22.090797] hdb: cache flushes supported
[   22.090840]  hdb: unknown partition table
[   22.119140] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[   22.119145] PCI: setting IRQ 5 as level-triggered
[   22.119148] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[   22.119172] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   22.119200] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   22.119215] ohci_hcd 0000:00:03.1: irq 5, io mem 0xee421000
[   22.128631] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   22.128641] Uniform CD-ROM driver Revision: 3.20
[   22.168511] hdd: ATAPI 16X DVD-ROM drive, 512kB Cache, UDMA(33)
[   22.176872] usb usb2: configuration #1 chosen from 1 choice
[   22.176901] hub 2-0:1.0: USB hub found
[   22.176915] hub 2-0:1.0: 2 ports detected
[   22.279074] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   22.279079] ACPI: PCI Interrupt 0000:00:03.2[C] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   22.279102] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   22.279128] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   22.279143] ohci_hcd 0000:00:03.2: irq 11, io mem 0xee422000
[   22.336816] usb usb3: configuration #1 chosen from 1 choice
[   22.336846] hub 3-0:1.0: USB hub found
[   22.336857] hub 3-0:1.0: 2 ports detected
[   22.439132] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   22.439137] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   22.440214] 0000:00:04.0: Unknown PHY transceiver found at address 0.
[   22.440980] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   22.441746] 0000:00:04.0: Unknown PHY transceiver found at address 2.
[   22.442510] 0000:00:04.0: Unknown PHY transceiver found at address 3.
[   22.443288] 0000:00:04.0: Unknown PHY transceiver found at address 4.
[   22.444053] 0000:00:04.0: Unknown PHY transceiver found at address 5.
[   22.444818] 0000:00:04.0: Unknown PHY transceiver found at address 6.
[   22.445582] 0000:00:04.0: Unknown PHY transceiver found at address 7.
[   22.446347] 0000:00:04.0: Unknown PHY transceiver found at address 8.
[   22.447118] 0000:00:04.0: Unknown PHY transceiver found at address 9.
[   22.447883] 0000:00:04.0: Unknown PHY transceiver found at address 10.
[   22.448648] 0000:00:04.0: Unknown PHY transceiver found at address 11.
[   22.449413] 0000:00:04.0: Unknown PHY transceiver found at address 12.
[   22.450179] 0000:00:04.0: Unknown PHY transceiver found at address 13.
[   22.450950] 0000:00:04.0: Unknown PHY transceiver found at address 14.
[   22.451716] 0000:00:04.0: Unknown PHY transceiver found at address 15.
[   22.452481] 0000:00:04.0: Unknown PHY transceiver found at address 16.
[   22.453246] 0000:00:04.0: Unknown PHY transceiver found at address 17.
[   22.454011] 0000:00:04.0: Unknown PHY transceiver found at address 18.
[   22.454783] 0000:00:04.0: Unknown PHY transceiver found at address 19.
[   22.455553] 0000:00:04.0: Unknown PHY transceiver found at address 20.
[   22.456318] 0000:00:04.0: Unknown PHY transceiver found at address 21.
[   22.457083] 0000:00:04.0: Unknown PHY transceiver found at address 22.
[   22.457848] 0000:00:04.0: Unknown PHY transceiver found at address 23.
[   22.458614] 0000:00:04.0: Unknown PHY transceiver found at address 24.
[   22.459859] 0000:00:04.0: Unknown PHY transceiver found at address 25.
[   22.460626] 0000:00:04.0: Unknown PHY transceiver found at address 26.
[   22.461391] 0000:00:04.0: Unknown PHY transceiver found at address 27.
[   22.462221] 0000:00:04.0: Unknown PHY transceiver found at address 28.
[   22.462999] 0000:00:04.0: Unknown PHY transceiver found at address 29.
[   22.464146] 0000:00:04.0: Unknown PHY transceiver found at address 31.
[   22.487335] 0000:00:04.0: Using transceiver found at address 1 as default
[   22.488201] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 5, 00:10:dc:7f:9e:1a.
[   22.544478] Attempting manual resume
[   22.544483] swsusp: Resume From Partition 3:5
[   22.544485] PM: Checking swsusp image.
[   22.544809] PM: Resume from disk failed.
[   22.571563] kjournald starting.  Commit interval 5 seconds
[   22.571575] EXT3-fs: mounted filesystem with ordered data mode.
[   22.598636] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   22.814541] usb 2-1: configuration #1 chosen from 1 choice
[   32.468725] NET: Registered protocol family 17
[   33.120130] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.125321] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.152815] eth0: Media Link On 100mbps full-duplex
[   33.370449] Linux agpgart interface v0.102 (c) Dave Jones
[   33.388607] agpgart: Detected SiS 648 chipset
[   33.392413] agpgart: AGP aperture is 64M @ 0xe8000000
[   33.402858] input: PC Speaker as /class/input/input2
[   33.553664] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[   33.643168] parport: PnPBIOS parport detected.
[   33.643273] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   34.024316] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   34.096782] usbcore: registered new interface driver libusual
[   34.113245] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   34.113275] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   34.232214] Initializing USB Mass Storage driver...
[   34.232323] scsi0 : SCSI emulation for USB Mass Storage devices
[   34.237953] usbcore: registered new interface driver usb-storage
[   34.237959] USB Mass Storage support registered.
[   34.238099] usb-storage: device found at 2
[   34.238101] usb-storage: waiting for device to settle before scanning
[   34.389520] fuse init (API version 7.8)
[   34.413223] lp0: using parport0 (interrupt-driven).
[   34.469076] Adding 4803392k swap on /dev/disk/by-uuid/03f91e45-7718-4748-a7dd-6429cb8af37d.  Priority:-1 extents:1 across:4803392k
[   34.605015] EXT3 FS on hda1, internal journal
[   36.674140] NET: Registered protocol family 10
[   36.674232] lo: Disabled Privacy Extensions
[   39.235166] usb-storage: device scan complete
[   39.274149] scsi 0:0:0:0: Direct-Access     Medion   Flash XL      CF 2.6D PQ: 0 ANSI: 0 CCS
[   39.281135] scsi 0:0:0:1: Direct-Access     Medion   Flash XL      MS 2.6D PQ: 0 ANSI: 0 CCS
[   39.288128] scsi 0:0:0:2: Direct-Access     Medion   Flash XL  MMC/SD 2.6D PQ: 0 ANSI: 0 CCS
[   39.295128] scsi 0:0:0:3: Direct-Access     Medion   Flash XL      SM 2.6D PQ: 0 ANSI: 0 CCS
[   39.370132] sd 0:0:0:0: Attached scsi removable disk sda
[   39.392102] sd 0:0:0:1: Attached scsi removable disk sdb
[   39.414189] sd 0:0:0:2: Attached scsi removable disk sdc
[   39.436180] sd 0:0:0:3: Attached scsi removable disk sdd
[   39.463316] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.463438] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   39.463552] sd 0:0:0:2: Attached scsi generic sg2 type 0
[   39.463667] sd 0:0:0:3: Attached scsi generic sg3 type 0
[   40.252552] ibm_acpi: ec object not found
[   40.311175] No dock devices found.
[   40.429234] input: Power Button (FF) as /class/input/input4
[   40.434203] ACPI: Power Button (FF) [PWRF]
[   40.467528] input: Power Button (CM) as /class/input/input5
[   40.472382] ACPI: Power Button (CM) [PWRB]
[   40.505893] input: Sleep Button (CM) as /class/input/input6
[   40.510781] ACPI: Sleep Button (CM) [FUTS]
[   40.542052] Using specific hotkey driver
[   40.640405] pcc_acpi: loading...
[   46.197123] ppdev: user-space parallel port driver
[   46.958140] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   46.958146] apm: overridden by ACPI.
[   47.255101] Bluetooth: Core ver 2.11
[   47.255159] NET: Registered protocol family 31
[   47.255162] Bluetooth: HCI device and connection manager initialized
[   47.255165] Bluetooth: HCI socket layer initialized
[   47.337647] Bluetooth: L2CAP ver 2.8
[   47.337652] Bluetooth: L2CAP socket layer initialized
[   47.630684] Bluetooth: RFCOMM socket layer initialized
[   47.630697] Bluetooth: RFCOMM TTY layer initialized
[   47.630699] Bluetooth: RFCOMM ver 1.8
[   59.428297] eth0: no IPv6 routers present
[ 4443.821599] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4444.044296] ISOFS: changing to secondary root
[ 5010.783398] cmd: 0x3f failed at 0x330 (status = 0x80, data = 0x26)
[ 5049.330552] cmd: 0x3f failed at 0x330 (status = 0x80, data = 0x26)
[ 5055.875056] cmd: 0x3f failed at 0x330 (status = 0x80, data = 0x26)
[ 5136.303100] cmd: 0x3f failed at 0x330 (status = 0x80, data = 0x26)
[ 5140.716045] cmd: 0x3f failed at 0x330 (status = 0x80, data = 0x26)
user@user-desktop:~$ modprobe saa7134
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
user@user-desktop:~$ modprobe saa7134 card=1
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
user@user-desktop:~$ modprobe saa7134 card=1 tuner=1
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.20-15-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting ir_kbd_i2c (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/ir-kbd-i2c.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting video_buf (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/video-buf.ko): Operation not permitted
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
user@user-desktop:~$    

Any help would be greatly appriciated, Thanks

---

