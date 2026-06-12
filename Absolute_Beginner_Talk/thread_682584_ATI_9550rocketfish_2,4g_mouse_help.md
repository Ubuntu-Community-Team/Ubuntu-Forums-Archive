---
title: "ATI 9550/rocketfish 2,4g mouse help"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-01-30
So here is what happened, a few day ago i posted a thread to help with my rocketfish mouse, but to no avail. I ended up find a few HowTo out there but i guess i didnt get it right. Once i got my mouse working as it should my video card (ATI radeon 9550) stoped working. I have been working on this for two days now without making any progress, i have picked threw every howto i can find but i still cant get it.


If you think you can help, i would greatly appreciate your help!

Here are a few of my outputs....```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

```


```
:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```








```
:~$ dmesg
[    0.000000] Linux version 2.6.22-14-386 (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Dec 18 07:34:24 UTC 2007 (Ubuntu 2.6.22-14.47-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f64c0
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
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8000 checksum 0
[    0.000000] ACPI: RSDP 000F8000, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 1FFF3040, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF30C0, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF3180, 422B (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7400, 005A (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=9fcb4f73-4061-48f7-9368-82e37e0703b8 ro quiet splash vga=786
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1808.460 MHz processor.
[   11.951343] Console: colour dummy device 80x25
[   11.951539] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.951910] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.960362] Memory: 508820k/524224k available (1929k kernel code, 14768k reserved, 877k data, 348k init, 0k highmem)
[   11.960372] virtual kernel memory layout:
[   11.960374]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   11.960375]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.960376]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   11.960377]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   11.960379]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   11.960380]       .data : 0xc02e25d5 - 0xc03bda04   ( 877 kB)
[   11.960381]       .text : 0xc0100000 - 0xc02e25d5   (1929 kB)
[   11.960384] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.960424] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.040408] Calibrating delay using timer specific routine.. 3618.57 BogoMIPS (lpj=7237152)
[   12.040428] Security Framework v1.0.0 initialized
[   12.040433] SELinux:  Disabled at boot.
[   12.040438] Mount-cache hash table entries: 512
[   12.040511] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   12.040518] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.040520] CPU: L2 Cache: 128K (64 bytes/line)
[   12.040522] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   12.040530] Compat vDSO mapped to ffffe000.
[   12.040538] CPU: AMD Sempron(tm) Processor 3000+ stepping 02
[   12.040542] Checking 'hlt' instruction... OK.
[   12.056885] Early unpacking initramfs... done
[   12.354110] ACPI: Core revision 20070126
[   12.354168] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.368683] ENABLING IO-APIC IRQs
[   12.368840] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.516298] Booting paravirtualized kernel on bare hardware
[   12.516355] Time: 11:09:56  Date: 00/30/108
[   12.516375] NET: Registered protocol family 16
[   12.516446] EISA bus registered
[   12.516457] ACPI: bus type pci registered
[   12.537312] PCI: PCI BIOS revision 2.10 entry at 0xf2550, last bus=1
[   12.537314] PCI: Using configuration type 1
[   12.537316] Setting up standard PCI resources
[   12.539160] ACPI: EC: Look up EC in DSDT
[   12.542112] ACPI: Interpreter enabled
[   12.542115] ACPI: (supports S0 S1 S3 S4 S5)
[   12.542129] ACPI: Using IOAPIC for interrupt routing
[   12.545913] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.545923] PCI: Probing PCI hardware (bus 00)
[   12.546422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.563898] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   12.564028] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   12.564143] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   12.564254] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   12.564360] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.564465] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.564570] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.564675] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.564765] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.564776] pnp: PnP ACPI init
[   12.564786] ACPI: bus type pnp registered
[   12.566606] pnp: PnP ACPI: found 10 devices
[   12.566609] ACPI: ACPI bus type pnp unregistered
[   12.566613] PnPBIOS: Disabled by ACPI PNP
[   12.566653] PCI: Using ACPI for IRQ routing
[   12.566656] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.572213] NET: Registered protocol family 8
[   12.572215] NET: Registered protocol family 20
[   12.572286] pnp: 00:00: iomem range 0xcd000-0xcffff has been reserved
[   12.572289] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   12.572292] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   12.572295] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   12.576218] Time: tsc clocksource has been installed.
[   12.602492] PCI: Bridge: 0000:00:01.0
[   12.602494]   IO window: 9000-9fff
[   12.602498]   MEM window: e4000000-e5ffffff
[   12.602502]   PREFETCH window: c0000000-dfffffff
[   12.602520] NET: Registered protocol family 2
[   12.640214] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   12.640250] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   12.640342] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   12.640398] TCP: Hash tables configured (established 16384 bind 16384)
[   12.640400] TCP reno registered
[   12.652296] checking if image is initramfs... it is
[   13.104027] Switched to high resolution mode on CPU 0
[   13.239728] Freeing initrd memory: 6702k freed
[   13.239996] audit: initializing netlink socket (disabled)
[   13.240007] audit(1201691396.160:1): initialized
[   13.241335] VFS: Disk quotas dquot_6.5.1
[   13.241347] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.241420] io scheduler noop registered
[   13.241422] io scheduler anticipatory registered
[   13.241424] io scheduler deadline registered
[   13.241440] io scheduler cfq registered (default)
[   13.241473] Boot video device is 0000:01:00.0
[   13.241579] isapnp: Scanning for PnP cards...
[   13.594851] isapnp: No Plug & Play device found
[   13.621162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.621247] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.622051] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.622621] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.622764] input: Macintosh mouse button emulation as /class/input/input0
[   13.622816] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   13.622818] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   13.875973] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.876096] mice: PS/2 mouse device common for all mice
[   13.876175] EISA: Probing bus 0 at eisa.0
[   13.876182] Cannot allocate resource for EISA slot 1
[   13.876191] Cannot allocate resource for EISA slot 4
[   13.876205] EISA: Detected 0 cards.
[   13.876283] TCP cubic registered
[   13.876293] NET: Registered protocol family 1
[   13.876315] Using IPI Shortcut mode
[   13.876457]   Magic number: 8:6:177
[   13.876494]   hash matches device ttyr3
[   13.876557]   hash matches device device:0d
[   13.876821] Freeing unused kernel memory: 348k freed
[   13.915628] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.092225] fuse init (API version 7.8)
[   15.096680] Capability LSM initialized
[   15.099739] ACPI: Fan [FAN] (on)
[   15.107673] ACPI: Thermal Zone [THRM] (40 C)
[   15.602536] SCSI subsystem initialized
[   15.606684] libata version 2.21 loaded.
[   15.607823] pata_sis 0000:00:02.5: version 0.5.1
[   15.607936] scsi0 : pata_sis
[   15.607970] scsi1 : pata_sis
[   15.608052] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   15.608056] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   15.641719] usbcore: registered new interface driver usbfs
[   15.641738] usbcore: registered new interface driver hub
[   15.641753] usbcore: registered new device driver usb
[   15.642357] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.693068] sis900.c: v1.08.10 Apr. 2 2006
[   15.771108] ata1.01: ATA-6: ST340015A, 3.15, max UDMA/100
[   15.771112] ata1.01: 78165360 sectors, multi 16: LBA 
[   15.787120] ata1.01: configured for UDMA/100
[   16.106789] ata2.00: ATAPI: TSSTcorpCD-R/RW TS-H292C, HP00, max UDMA/33
[   16.270726] ata2.00: configured for UDMA/33
[   16.270821] scsi 0:0:1:0: Direct-Access     ATA      ST340015A        3.15 PQ: 0 ANSI: 5
[   16.272273] scsi 1:0:0:0: CD-ROM            TSSTcorp CD-R/RW TS-H292C HP00 PQ: 0 ANSI: 5
[   16.275241] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   16.275256] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.275260] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   16.275468] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   16.275485] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe7004000
[   16.282557] sd 0:0:1:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.282569] sd 0:0:1:0: [sda] Write Protect is off
[   16.282572] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   16.282584] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.282634] sd 0:0:1:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.282641] sd 0:0:1:0: [sda] Write Protect is off
[   16.282643] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   16.282654] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.282657]  sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   16.332598] hub 1-0:1.0: USB hub found
[   16.332607] hub 1-0:1.0: 3 ports detected
[   16.336092]  sda5 >
[   16.336550] sd 0:0:1:0: [sda] Attached SCSI disk
[   16.340615] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   16.340760] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   16.364713] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   16.364718] Uniform CD-ROM driver Revision: 3.20
[   16.364948] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.434532] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   16.434545] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   16.434548] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   16.434573] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   16.434586] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe7000000
[   16.492488] usb usb2: configuration #1 chosen from 1 choice
[   16.492512] hub 2-0:1.0: USB hub found
[   16.492521] hub 2-0:1.0: 3 ports detected
[   16.578682] Attempting manual resume
[   16.578686] swsusp: Resume From Partition 8:5
[   16.578688] PM: Checking swsusp image.
[   16.578875] PM: Resume from disk failed.
[   16.594452] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   16.594466] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   16.594469] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   16.594489] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   16.594502] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe7001000
[   16.632047] kjournald starting.  Commit interval 5 seconds
[   16.632057] EXT3-fs: mounted filesystem with ordered data mode.
[   16.652435] usb usb3: configuration #1 chosen from 1 choice
[   16.652458] hub 3-0:1.0: USB hub found
[   16.652468] hub 3-0:1.0: 2 ports detected
[   16.738292] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   16.754467] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   16.754479] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   16.754502] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   16.754532] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   16.754541] ehci_hcd 0000:00:03.3: irq 19, io mem 0xe7002000
[   16.914219] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.914306] usb usb4: configuration #1 chosen from 1 choice
[   16.914327] hub 4-0:1.0: USB hub found
[   16.914335] hub 4-0:1.0: 8 ports detected
[   17.018348] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[   17.019241] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   17.028262] 0000:00:04.0: Using transceiver found at address 1 as default
[   17.028930] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 20, 00:13:d4:ca:c7:6c.
[   17.029020] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 21
[   17.081787] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e7005000-e70057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.086894] sata_sis 0000:00:05.0: version 0.8
[   17.086913] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   17.086918] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   17.086984] scsi2 : sata_sis
[   17.087024] scsi3 : sata_sis
[   17.087087] ata3: SATA max UDMA/133 cmd 0x0001ac00 ctl 0x0001b002 bmdma 0x0001bc00 irq 22
[   17.087091] ata4: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b802 bmdma 0x0001bc08 irq 22
[   17.322018] usb 1-3: device not accepting address 2, error -62
[   17.397990] ata3: SATA link down (SStatus 0 SControl 300)
[   17.717842] ata4: SATA link down (SStatus 0 SControl 300)
[   18.357625] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000628fd1]
[   18.361547] usb 1-3: new full speed USB device using ohci_hcd and address 4
[   18.577465] usb 1-3: configuration #1 chosen from 1 choice
[   18.881303] usb 3-2: new low speed USB device using ohci_hcd and address 2
[   19.098226] usb 3-2: configuration #1 chosen from 1 choice
[   31.757057] Linux agpgart interface v0.102 (c) Dave Jones
[   31.794723] agpgart: Detected AGP bridge 0
[   31.796676] agpgart: AGP aperture is 64M @ 0xe0000000
[   31.891867] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.893736] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.708104] Real Time Clock Driver v1.12ac
[   32.836305] input: PC Speaker as /class/input/input2
[   33.112598] parport_pc 00:08: reported by Plug and Play ACPI
[   33.112646] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   33.125417] usbcore: registered new interface driver libusual
[   33.213002] usbcore: registered new interface driver hiddev
[   33.220430] input: Primax Wireless 2.4G Laser Mouse as /class/input/input3
[   33.220478] input: USB HID v1.11 Mouse [Primax Wireless 2.4G Laser Mouse] on usb-0000:00:03.2-2
[   33.220490] usbcore: registered new interface driver usbhid
[   33.220494] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.225739] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.225745] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.242849] Initializing USB Mass Storage driver...
[   33.242919] scsi4 : SCSI emulation for USB Mass Storage devices
[   33.242964] usb-storage: device found at 4
[   33.242966] usb-storage: waiting for device to settle before scanning
[   33.242976] usbcore: registered new interface driver usb-storage
[   33.242979] USB Mass Storage support registered.
[   33.415218] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   33.738481] intel8x0_measure_ac97_clock: measured 53934 usecs
[   33.738485] intel8x0: clocking to 48000
[   34.174511] lp0: using parport0 (interrupt-driven).
[   34.229182] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   34.681622] EXT3 FS on sda1, internal journal
[   35.974842] input: Power Button (FF) as /class/input/input4
[   35.978577] ACPI: Power Button (FF) [PWRF]
[   36.011887] input: Power Button (CM) as /class/input/input5
[   36.015599] ACPI: Power Button (CM) [PWRB]
[   36.048341] input: Sleep Button (CM) as /class/input/input6
[   36.052062] ACPI: Sleep Button (CM) [FUTS]
[   36.101805] No dock devices found.
[   36.436317] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
[   36.443258] powernow-k8: no p states to transition
[   38.241734] usb-storage: device scan complete
[   38.249728] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   38.256444] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   38.263716] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   38.270717] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   38.286739] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   38.286774] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   38.297298] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   38.297334] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   38.307944] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   38.307979] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   38.319726] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   38.319766] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   39.003117] ppdev: user-space parallel port driver
[   40.244376] eth0: Media Link On 100mbps full-duplex 
[   41.998099] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   41.998103] apm: overridden by ACPI.
[   44.103250] nacctd uses obsolete (PF_INET,SOCK_PACKET)
[   44.160489] NET: Registered protocol family 17
[   46.800520] device eth0 entered promiscuous mode
[   46.800530] audit(1201691430.729:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   48.877609] NET: Registered protocol family 10
[   48.877749] lo: Disabled Privacy Extensions
[   48.972200] Capability LSM initialized
[   54.396169] [drm] Initialized drm 1.1.0 20060810
[   54.402880] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   54.405105] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   54.786085] Bluetooth: Core ver 2.11
[   54.786177] NET: Registered protocol family 31
[   54.786180] Bluetooth: HCI device and connection manager initialized
[   54.786183] Bluetooth: HCI socket layer initialized
[   54.824396] Bluetooth: L2CAP ver 2.8
[   54.824400] Bluetooth: L2CAP socket layer initialized
[   54.892459] Bluetooth: RFCOMM socket layer initialized
[   54.892536] Bluetooth: RFCOMM TTY layer initialized
[   54.892539] Bluetooth: RFCOMM ver 1.8
[   56.693632] agpgart: Found an AGP 3.1 compliant device at 0000:00:00.0.
[   56.693718] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.695683] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   57.071946] [drm] Setting GART location based on new memory map
[   57.071955] [drm] Loading R300 Microcode
[   57.071997] [drm] writeback test succeeded in 1 usecs
[   69.490269] eth0: no IPv6 routers present

```



```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```


If you need any more just give me the command, thanks for looking over it.

---

### Post by LostMagix on 2008-01-30
One more i forgot





```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1280x960@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by LostMagix on 2008-01-30
*bump*

---

