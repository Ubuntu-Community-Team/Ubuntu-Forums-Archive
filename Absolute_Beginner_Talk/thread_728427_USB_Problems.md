---
title: "USB Problems"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-18
My USB Does not work at all, not for mice or printers or anything.  Does not even know its there.  I don't know what information to post so whatever you need tell me.  What i can tell you is i have an eMachines T4060 and the USB woks with windows.

---

### Post by thewho? on 2008-03-18
Run a dmesg and send the output to a file. ( dmesg > output.txt)  Then grep the output file for USB and see if the bus is even showing up in there.

---

### Post by The Titan on 2008-03-18
i dont know what to do with all that.  I found "USB" many times in there.  I dont know what im looking for so here is the output

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4840
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6670 checksum 0
[    0.000000] ACPI: RSDP 000F6670, 0014 (r0 FIC   )
[    0.000000] ACPI: RSDT 1FFF3000, 0030 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 3918 (r1 FIC    AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: DBGP 1FFF6A80, 0034 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: APIC 1FFF6A00, 0054 (r1 FIC    VC37     42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=f9657788-d44c-4720-a984-12845aa15a22 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1992.789 MHz processor.
[   16.311649] Console: colour VGA+ 80x25
[   16.312165] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.312643] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.328487] Memory: 508172k/524224k available (2015k kernel code, 15416k reserved, 915k data, 364k init, 0k highmem)
[   16.328500] virtual kernel memory layout:
[   16.328502]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   16.328503]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.328505]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   16.328508]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   16.328509]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   16.328511]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   16.328512]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   16.328516] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.328568] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.408460] Calibrating delay using timer specific routine.. 3989.35 BogoMIPS (lpj=7978715)
[   16.408492] Security Framework v1.0.0 initialized
[   16.408501] SELinux:  Disabled at boot.
[   16.408519] Mount-cache hash table entries: 512
[   16.408701] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   16.408718] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.408722] CPU: L2 cache: 512K
[   16.408725] CPU: Hyper-Threading is disabled
[   16.408728] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   16.408743] Compat vDSO mapped to ffffe000.
[   16.408760] Checking 'hlt' instruction... OK.
[   16.424629] SMP alternatives: switching to UP code
[   16.424911] Freeing SMP alternatives: 11k freed
[   16.425349] Early unpacking initramfs... done
[   16.852546] ACPI: Core revision 20070126
[   16.852617] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.908226] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[   16.908274] Total of 1 processors activated (3989.35 BogoMIPS).
[   16.908419] ENABLING IO-APIC IRQs
[   16.908612] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.055435] Brought up 1 CPUs
[   17.055598] Booting paravirtualized kernel on bare hardware
[   17.055681] Time: 11:11:18  Date: 02/17/108
[   17.055714] NET: Registered protocol family 16
[   17.055846] EISA bus registered
[   17.055863] ACPI: bus type pci registered
[   17.081195] PCI: PCI BIOS revision 2.10 entry at 0xfb180, last bus=2
[   17.081198] PCI: Using configuration type 1
[   17.081201] Setting up standard PCI resources
[   17.090384] ACPI: EC: Look up EC in DSDT
[   17.094796] ACPI: Interpreter enabled
[   17.094801] ACPI: (supports S0 S3 S4 S5)
[   17.094826] ACPI: Using IOAPIC for interrupt routing
[   17.101077] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.101097] PCI: Probing PCI hardware (bus 00)
[   17.101587] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   17.101589] * this clock source is slow. If you are sure your timer does not have
[   17.101591] * this bug, please use "acpi_pm_good" to disable the workaround
[   17.101645] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   17.101650] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   17.102123] PCI: Transparent bridge - 0000:00:1e.0
[   17.102161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.102398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   17.120967] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 9 11 12 14 15)
[   17.121115] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 11 12 14 15)
[   17.121263] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 11 12 14 15)
[   17.121408] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *11 12 14 15)
[   17.121552] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.121698] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.121843] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 11 12 14 15) *0, disabled.
[   17.121991] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 *11 12 14 15)
[   17.122125] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.122142] pnp: PnP ACPI init
[   17.122155] ACPI: bus type pnp registered
[   17.125749] pnp: PnP ACPI: found 14 devices
[   17.125753] ACPI: ACPI bus type pnp unregistered
[   17.125760] PnPBIOS: Disabled by ACPI PNP
[   17.125834] PCI: Using ACPI for IRQ routing
[   17.125839] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.141365] NET: Registered protocol family 8
[   17.141368] NET: Registered protocol family 20
[   17.141458] pnp: 00:00: ioport range 0x280-0x287 has been reserved
[   17.141468] pnp: 00:01: iomem range 0xd0000-0xd3fff has been reserved
[   17.141472] pnp: 00:01: iomem range 0xf0000-0xf7fff could not be reserved
[   17.141476] pnp: 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[   17.141480] pnp: 00:01: iomem range 0xfc000-0xfffff could not be reserved
[   17.141488] pnp: 00:03: ioport range 0x400-0x4bf could not be reserved
[   17.143238] Time: tsc clocksource has been installed.
[   17.171916] PCI: Bridge: 0000:00:01.0
[   17.171918]   IO window: disabled.
[   17.171925]   MEM window: e0000000-e1ffffff
[   17.171931]   PREFETCH window: d8000000-dfffffff
[   17.171939] PCI: Bridge: 0000:00:1e.0
[   17.171943]   IO window: c000-cfff
[   17.171949]   MEM window: e2000000-e3ffffff
[   17.171955]   PREFETCH window: 30000000-300fffff
[   17.171977] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.171994] NET: Registered protocol family 2
[   17.211188] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   17.211254] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   17.211434] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   17.211559] TCP: Hash tables configured (established 16384 bind 16384)
[   17.211563] TCP reno registered
[   17.223305] checking if image is initramfs... it is
[   17.674358] Switched to high resolution mode on CPU 0
[   18.069796] Freeing initrd memory: 7046k freed
[   18.070314] audit: initializing netlink socket (disabled)
[   18.070335] audit(1205752278.160:1): initialized
[   18.073312] VFS: Disk quotas dquot_6.5.1
[   18.073390] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.073525] io scheduler noop registered
[   18.073529] io scheduler anticipatory registered
[   18.073531] io scheduler deadline registered
[   18.073560] io scheduler cfq registered (default)
[   18.073664] Boot video device is 0000:01:00.0
[   18.073895] isapnp: Scanning for PnP cards...
[   18.427535] isapnp: No Plug & Play device found
[   18.464074] Real Time Clock Driver v1.12ac
[   18.464205] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.464316] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.465437] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.466559] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.466876] input: Macintosh mouse button emulation as /class/input/input0
[   18.466997] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.470924] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.470933] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.471212] mice: PS/2 mouse device common for all mice
[   18.471380] EISA: Probing bus 0 at eisa.0
[   18.471423] EISA: Detected 0 cards.
[   18.471564] TCP cubic registered
[   18.471581] NET: Registered protocol family 1
[   18.471612] Using IPI No-Shortcut mode
[   18.471810]   Magic number: 0:41:176
[   18.471900]   hash matches device ttyr2
[   18.472057]   hash matches device device:0c
[   18.472606] Freeing unused kernel memory: 364k freed
[   18.512973] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.760488] AppArmor: AppArmor initialized<5>audit(1205752280.160:2):  type=1505 info="AppArmor initialized" pid=1177
[   19.769883] fuse init (API version 7.8)
[   19.776782] Failure registering capabilities with primary security module.
[   19.800164] ACPI: Processor [CPU0] (supports 2 throttling states)
[   19.826785] ACPI: Thermal Zone [THRM] (40 C)
[   20.591843] usbcore: registered new interface driver usbfs
[   20.591886] usbcore: registered new interface driver hub
[   20.591919] usbcore: registered new device driver usb
[   20.593288] USB Universal Host Controller Interface driver v3.0
[   20.593409] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.593425] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.593430] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.593645] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.593679] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   20.593860] usb usb1: configuration #1 chosen from 1 choice
[   20.593899] hub 1-0:1.0: USB hub found
[   20.593911] hub 1-0:1.0: 2 ports detected
[   20.701974] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   20.701992] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.701997] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.702031] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.702066] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   20.702221] usb usb2: configuration #1 chosen from 1 choice
[   20.702267] hub 2-0:1.0: USB hub found
[   20.702281] hub 2-0:1.0: 2 ports detected
[   20.702712] SCSI subsystem initialized
[   20.710994] libata version 2.21 loaded.
[   20.741307] 8139too Fast Ethernet driver 0.9.28
[   20.805187] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.805204] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.805209] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.805244] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.805277] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   20.805427] usb usb3: configuration #1 chosen from 1 choice
[   20.805464] hub 3-0:1.0: USB hub found
[   20.805475] hub 3-0:1.0: 2 ports detected
[   20.909330] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   20.909349] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.909354] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.909404] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   20.909455] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   20.909470] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe4000000
[   20.913362] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.913487] usb usb4: configuration #1 chosen from 1 choice
[   20.913526] hub 4-0:1.0: USB hub found
[   20.913538] hub 4-0:1.0: 6 ports detected
[   20.963929] FDC 0 is a post-1991 82077
[   21.022223] ata_piix 0000:00:1f.1: version 2.11
[   21.022247] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.022319] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.022486] scsi0 : ata_piix
[   21.022551] scsi1 : ata_piix
[   21.022698] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   21.022703] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   21.340283] ata1.00: ATAPI: MAD DOG MD-16XDVD9, 2.FA, max UDMA/33
[   21.504010] ata1.00: configured for UDMA/33
[   21.667798] ata2.00: ATA-6: WDC WD400BB-00LNA0, 05.01C05, max UDMA/100
[   21.667803] ata2.00: 78165360 sectors, multi 16: LBA 
[   21.667810] ata2.00: limited to UDMA/33 due to 40-wire cable
[   21.675813] ata2.00: configured for UDMA/33
[   21.676761] scsi 0:0:0:0: CD-ROM            MAD DOG  MD-16XDVD9       2.FA PQ: 0 ANSI: 5
[   21.677356] scsi 1:0:0:0: Direct-Access     ATA      WDC WD400BB-00LN 05.0 PQ: 0 ANSI: 5
[   21.677907] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   21.678484] eth0: RealTek RTL8139 at 0xe0838000, 00:40:ca:34:2a:53, IRQ 17
[   21.678488] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.681859] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.706491] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.706520] sd 1:0:0:0: [sda] Write Protect is off
[   21.706524] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.706549] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.706741] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.706755] sd 1:0:0:0: [sda] Write Protect is off
[   21.706759] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.706783] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.706791]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   21.709020] Uniform CD-ROM driver Revision: 3.20
[   21.709316] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.713286]  sda1 sda2 < sda5 >
[   21.733858] sd 1:0:0:0: [sda] Attached SCSI disk
[   21.744074] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   21.744271] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   21.995566] Attempting manual resume
[   21.995572] swsusp: Resume From Partition 8:5
[   21.995575] PM: Checking swsusp image.
[   21.995889] PM: Resume from disk failed.
[   22.035229] kjournald starting.  Commit interval 5 seconds
[   22.035245] EXT3-fs: mounted filesystem with ordered data mode.
[   29.547984] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   30.198906] NET: Registered protocol family 10
[   30.199018] lo: Disabled Privacy Extensions
[   31.285395] Linux agpgart interface v0.102 (c) Dave Jones
[   31.300405] agpgart: Detected an Intel 830M Chipset.
[   31.307885] agpgart: AGP aperture is 128M @ 0xd0000000
[   31.440905] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.464391] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.111371] intel_rng: FWH not detected
[   32.551132] nvidia: module license 'NVIDIA' taints kernel.
[   32.837598] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.837990] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   32.863994] iTCO_vendor_support: vendor-support=0
[   32.865983] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   33.523403] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   33.550154] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   33.552955] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   33.553059] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.553262] parport_pc 00:0b: reported by Plug and Play ACPI
[   33.553317] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   33.555585] input: PC Speaker as /class/input/input3
[   34.077034] loop: module loaded
[   34.091965] lp0: using parport0 (interrupt-driven).
[   34.177519] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   34.555064] EXT3 FS on sda1, internal journal
[   37.196077] input: Power Button (FF) as /class/input/input4
[   37.202163] ACPI: Power Button (FF) [PWRF]
[   37.248008] input: Power Button (CM) as /class/input/input5
[   37.253999] ACPI: Power Button (CM) [PWRB]
[   37.303990] No dock devices found.
[   39.083671] ppdev: user-space parallel port driver
[   39.334238] audit(1205770300.155:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4608 profile="/usr/sbin/cupsd"
[   39.394848] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   39.394855] apm: overridden by ACPI.
[   39.656863] Failure registering capabilities with primary security module.
[   39.883324] Bluetooth: Core ver 2.11
[   39.883502] NET: Registered protocol family 31
[   39.883506] Bluetooth: HCI device and connection manager initialized
[   39.883512] Bluetooth: HCI socket layer initialized
[   39.908484] Bluetooth: L2CAP ver 2.8
[   39.908491] Bluetooth: L2CAP socket layer initialized
[   39.994159] Bluetooth: RFCOMM socket layer initialized
[   39.994301] Bluetooth: RFCOMM TTY layer initialized
[   39.994305] Bluetooth: RFCOMM ver 1.8
[   40.946312] eth0: no IPv6 routers present
[   41.651106] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   41.651131] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   41.651162] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[16377.549180] ppdev0: registered pardevice
[16377.549500] ppdev0: unregistered pardevice
[16379.286313] ppdev0: registered pardevice
[16379.333669] ppdev0: unregistered pardevice
[88832.312341] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[88832.312352] : Add. Sense: Medium not present
[88832.312360] end_request: I/O error, dev sr0, sector 0
[88832.312365] Buffer I/O error on device sr0, logical block 0
[88832.312371] Buffer I/O error on device sr0, logical block 1
[88832.312376] Buffer I/O error on device sr0, logical block 2
[88832.312380] Buffer I/O error on device sr0, logical block 3
[88832.312383] Buffer I/O error on device sr0, logical block 4
[88832.312387] Buffer I/O error on device sr0, logical block 5
[88832.312391] Buffer I/O error on device sr0, logical block 6
[88832.312394] Buffer I/O error on device sr0, logical block 7
[88832.313191] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[88832.313197] : Add. Sense: Medium not present
[88832.313202] end_request: I/O error, dev sr0, sector 0
[88832.313206] Buffer I/O error on device sr0, logical block 0
[88832.313732] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[88832.313738] : Add. Sense: Medium not present
[88832.313743] end_request: I/O error, dev sr0, sector 4
[88832.313746] Buffer I/O error on device sr0, logical block 1
[89532.035488] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89532.035499] : Add. Sense: Medium not present
[89532.035507] end_request: I/O error, dev sr0, sector 0
[89532.035512] Buffer I/O error on device sr0, logical block 0
[89532.035517] Buffer I/O error on device sr0, logical block 1
[89532.035522] Buffer I/O error on device sr0, logical block 2
[89532.035526] Buffer I/O error on device sr0, logical block 3
[89532.035529] Buffer I/O error on device sr0, logical block 4
[89532.035533] Buffer I/O error on device sr0, logical block 5
[89532.035537] Buffer I/O error on device sr0, logical block 6
[89532.035540] Buffer I/O error on device sr0, logical block 7
[89532.036048] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89532.036054] : Add. Sense: Medium not present
[89532.036059] end_request: I/O error, dev sr0, sector 0
[89532.036062] Buffer I/O error on device sr0, logical block 0
[89532.036713] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89532.036719] : Add. Sense: Medium not present
[89532.036724] end_request: I/O error, dev sr0, sector 4
[89532.036727] Buffer I/O error on device sr0, logical block 1
[89534.291911] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89534.291922] : Add. Sense: Medium not present
[89534.291931] end_request: I/O error, dev sr0, sector 0
[89534.292429] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89534.292435] : Add. Sense: Medium not present
[89534.292440] end_request: I/O error, dev sr0, sector 4
[89534.292948] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89534.292954] : Add. Sense: Medium not present
[89534.292959] end_request: I/O error, dev sr0, sector 0
[89534.293467] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[89534.293473] : Add. Sense: Medium not present
[89534.293478] end_request: I/O error, dev sr0, sector 4
```

---

