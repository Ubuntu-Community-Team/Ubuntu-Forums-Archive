---
title: "[SOLVED] Ethernet card not detected"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by sajiv_k on 2007-11-28
The ethernet card was working fine when I booted using the live cd. 

But after the installaing Gutsy, the ethernet card is not shown in the network properties.

The computer has an onboard card, its a VIA chipset.

The Interface file shows this:

> auto lo
iface lo inet loopback

Host file shows:

> # The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

I'm also pasting  the result of DMESG and LSPCI

This is an office computer and I had convinced some folks to switch to Gutsy from XP, hope I dont eat crow.:(

---

### Post by jcsteele on 2007-11-28
can you post the output of your "lspci" and "dmesg" please.

//jcs

---

### Post by sajiv_k on 2007-11-28
oops i missed pasting it

**LSPCI**

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

[B]

DMESG[/B]

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bfc0000 (usable)
[    0.000000]  BIOS-e820: 000000001bfc0000 - 000000001bfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bfce000 - 000000001bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 114624) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114624
[    0.000000]   HighMem    114624 ->   114624
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114624
[    0.000000] On node 0 totalpages: 114624
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109665 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
[    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1BFC0000, 0030 (r1 A M I  OEMRSDT   7000627 MSFT       97)
[    0.000000] ACPI: FACP 1BFC0200, 0084 (r2 A M I  OEMFACP   7000627 MSFT       97)
[    0.000000] ACPI: DSDT 1BFC0400, 3BB1 (r1  12345 12345123      123 INTL 20051117)
[    0.000000] ACPI: FACS 1BFCE000, 0040
[    0.000000] ACPI: APIC 1BFC0390, 006C (r1 A M I  OEMAPIC   7000627 MSFT       97)
[    0.000000] ACPI: OEMB 1BFCE040, 0060 (r1 A M I  AMI_OEM   7000627 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e2c00000)
[    0.000000] Built 1 zonelists.  Total pages: 113729
[    0.000000] Kernel command line: root=UUID=0686ad2d-84f6-4aa5-9b85-55a8ee2f1926 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 3000.503 MHz processor.
[   10.812045] Console: colour VGA+ 80x25
[   10.812406] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.812682] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.820782] Memory: 442764k/458496k available (2015k kernel code, 15248k reserved, 916k data, 364k init, 0k highmem)
[   10.820792] virtual kernel memory layout:
[   10.820793]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   10.820794]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.820795]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   10.820797]     lowmem  : 0xc0000000 - 0xdbfc0000   ( 447 MB)
[   10.820798]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   10.820799]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   10.820800]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   10.820803] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.820843] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   10.900803] Calibrating delay using timer specific routine.. 6008.54 BogoMIPS (lpj=12017098)
[   10.900827] Security Framework v1.0.0 initialized
[   10.900833] SELinux:  Disabled at boot.
[   10.900845] Mount-cache hash table entries: 512
[   10.900973] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   10.900982] monitor/mwait feature present.
[   10.900985] using mwait in idle threads.
[   10.900991] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   10.900994] CPU: L2 cache: 2048K
[   10.900997] CPU: Physical Processor ID: 0
[   10.900999] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e59d 00000000 00000001
[   10.901012] Compat vDSO mapped to ffffe000.
[   10.901027] Checking 'hlt' instruction... OK.
[   10.916883] SMP alternatives: switching to UP code
[   10.917309] Early unpacking initramfs... done
[   11.212392] ACPI: Core revision 20070126
[   11.212444] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.214848] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   11.214868] SMP alternatives: switching to SMP code
[   11.214995] Booting processor 1/1 eip 3000
[   11.225473] Initializing CPU#1
[   11.304443] Calibrating delay using timer specific routine.. 6000.68 BogoMIPS (lpj=12001376)
[   11.304454] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   11.304461] monitor/mwait feature present.
[   11.304469] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   11.304472] CPU: L2 cache: 2048K
[   11.304474] CPU: Physical Processor ID: 0
[   11.304477] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e59d 00000000 00000001
[   11.305041] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   11.305088] Total of 2 processors activated (12009.23 BogoMIPS).
[   11.305848] ENABLING IO-APIC IRQs
[   11.306173] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.452434] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   11.472433] Brought up 2 CPUs
[   11.527038] migration_cost=29
[   11.527219] Booting paravirtualized kernel on bare hardware
[   11.527322] Time: 20:33:50  Date: 10/28/107
[   11.527348] NET: Registered protocol family 16
[   11.527444] EISA bus registered
[   11.527450] ACPI: bus type pci registered
[   11.527559] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[   11.527561] PCI: Using configuration type 1
[   11.527563] Setting up standard PCI resources
[   11.535858] ACPI: EC: Look up EC in DSDT
[   11.541866] ACPI: Interpreter enabled
[   11.541870] ACPI: (supports S0 S1 S3 S4 S5)
[   11.541893] ACPI: Using IOAPIC for interrupt routing
[   11.553516] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.553525] PCI: Probing PCI hardware (bus 00)
[   11.554622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.554819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   11.564119] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   11.564238] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   11.564381] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   11.564495] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.564608] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.564720] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.564833] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.564946] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.565063] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.565074] pnp: PnP ACPI init
[   11.565084] ACPI: bus type pnp registered
[   11.572091] pnp: PnP ACPI: found 14 devices
[   11.572094] ACPI: ACPI bus type pnp unregistered
[   11.572098] PnPBIOS: Disabled by ACPI PNP
[   11.572155] PCI: Using ACPI for IRQ routing
[   11.572158] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.577684] NET: Registered protocol family 8
[   11.577686] NET: Registered protocol family 20
[   11.577759] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[   11.577762] pnp: 00:09: ioport range 0x290-0x29f has been reserved
[   11.577765] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[   11.577768] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[   11.577770] pnp: 00:09: ioport range 0xa40-0xa4f has been reserved
[   11.577784] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   11.577787] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   11.577794] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   11.577797] pnp: 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   11.577800] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   11.577803] pnp: 00:0d: iomem range 0x100000-0x1bffffff could not be reserved
[   11.580244] Time: tsc clocksource has been installed.
[   11.608155] PCI: Bridge: 0000:00:01.0
[   11.608157]   IO window: disabled.
[   11.608163]   MEM window: fca00000-feafffff
[   11.608168]   PREFETCH window: e7f00000-efefffff
[   11.608189] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.608201] NET: Registered protocol family 2
[   11.644312] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   11.644356] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   11.644469] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   11.644544] TCP: Hash tables configured (established 16384 bind 16384)
[   11.644547] TCP reno registered
[   11.656410] checking if image is initramfs... it is
[   12.107772] Switched to high resolution mode on CPU 0
[   12.107862] Switched to high resolution mode on CPU 1
[   12.243209] Freeing initrd memory: 7350k freed
[   12.243897] audit: initializing netlink socket (disabled)
[   12.243918] audit(1196282030.140:1): initialized
[   12.246439] VFS: Disk quotas dquot_6.5.1
[   12.246505] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.246614] io scheduler noop registered
[   12.246617] io scheduler anticipatory registered
[   12.246619] io scheduler deadline registered
[   12.246636] io scheduler cfq registered (default)
[   12.246659] PCI: VIA PCI bridge detected. Disabling DAC.
[   12.246734] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   12.246743] Boot video device is 0000:01:00.0
[   12.246924] isapnp: Scanning for PnP cards...
[   12.598286] isapnp: No Plug & Play device found
[   12.626296] Real Time Clock Driver v1.12ac
[   12.626422] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.626526] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.627302] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.628135] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.628370] input: Macintosh mouse button emulation as /class/input/input0
[   12.628463] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   12.628838] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.628848] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.629322] mice: PS/2 mouse device common for all mice
[   12.629461] EISA: Probing bus 0 at eisa.0
[   12.629508] EISA: Detected 0 cards.
[   12.629612] TCP cubic registered
[   12.629625] NET: Registered protocol family 1
[   12.629648] Using IPI No-Shortcut mode
[   12.629822]   Magic number: 15:287:600
[   12.629914]   hash matches device ptyd4
[   12.630421] Freeing unused kernel memory: 364k freed
[   12.647453] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.823455] AppArmor: AppArmor initialized<5>audit(1196282031.640:2):  type=1505 info="AppArmor initialized" pid=1214
[   13.831573] fuse init (API version 7.8)
[   13.836277] Failure registering capabilities with primary security module.
[   13.875086] ACPI: Processor [CPU1] (supports 16 throttling states)
[   13.875161] ACPI: Processor [CPU2] (supports 16 throttling states)
[   13.875176] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.875190] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.362912] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.362920] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.363764] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   14.363798] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   14.363816] VP_IDE: chipset revision 6
[   14.363819] VP_IDE: not 100% native mode: will probe irqs later
[   14.363835] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   14.363844]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   14.363858]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   14.363867] Probing IDE interface ide0...
[   14.376843] SCSI subsystem initialized
[   14.395750] libata version 2.21 loaded.
[   14.395878] usbcore: registered new interface driver usbfs
[   14.395916] usbcore: registered new interface driver hub
[   14.395952] usbcore: registered new device driver usb
[   14.397195] USB Universal Host Controller Interface driver v3.0
[   14.515109] Floppy drive(s): fd0 is 1.44M
[   14.537190] FDC 0 is a post-1991 82077
[   14.809528] hda: ST380215A, ATA DISK drive
[   15.481248] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.482509] Probing IDE interface ide1...
[   16.344197] hdc: SONY DVD RW DW-G120A, ATAPI CD/DVD-ROM drive
[   17.016092] ide1 at 0x170-0x177,0x376 on irq 15
[   17.028944] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   17.028962] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   17.029395] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   17.029432] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000dc00
[   17.029946] usb usb1: configuration #1 chosen from 1 choice
[   17.030168] hub 1-0:1.0: USB hub found
[   17.030176] hub 1-0:1.0: 2 ports detected
[   17.131532] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   17.131545] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   17.131577] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   17.131601] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d880
[   17.131752] usb usb2: configuration #1 chosen from 1 choice
[   17.131793] hub 2-0:1.0: USB hub found
[   17.131802] hub 2-0:1.0: 2 ports detected
[   17.235428] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   17.235442] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   17.235474] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   17.235498] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d800
[   17.235637] usb usb3: configuration #1 chosen from 1 choice
[   17.235685] hub 3-0:1.0: USB hub found
[   17.235694] hub 3-0:1.0: 2 ports detected
[   17.339345] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   17.339358] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   17.339395] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   17.339421] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d480
[   17.339556] usb usb4: configuration #1 chosen from 1 choice
[   17.339596] hub 4-0:1.0: USB hub found
[   17.339608] hub 4-0:1.0: 2 ports detected
[   17.447527] sata_via 0000:00:0f.0: version 2.2
[   17.447557] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   17.447629] sata_via 0000:00:0f.0: routed to hard irq line 11
[   17.447750] scsi0 : sata_via
[   17.447840] scsi1 : sata_via
[   17.448185] ata1: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 16
[   17.448191] ata2: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 16
[   17.468137] hda: max request size: 512KiB
[   17.510281] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   17.534666] hda: cache flushes supported
[   17.534714]  hda: hda1 hda2 < hda5 >
[   17.586190] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   17.586204] Uniform CD-ROM driver Revision: 3.20
[   17.650968] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   17.878768] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   17.888999] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   17.889014] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   17.889065] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   17.889118] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfebffc00
[   17.889127] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.889268] usb usb5: configuration #1 chosen from 1 choice
[   17.889312] hub 5-0:1.0: USB hub found
[   17.889323] hub 5-0:1.0: 8 ports detected
[   17.916093] Attempting manual resume
[   17.916098] swsusp: Resume From Partition 3:5
[   17.916100] PM: Checking swsusp image.
[   17.916248] PM: Resume from disk failed.
[   17.938387] kjournald starting.  Commit interval 5 seconds
[   17.938398] EXT3-fs: mounted filesystem with ordered data mode.
[   23.623061] Linux agpgart interface v0.102 (c) Dave Jones
[   23.657373] agpgart: Detected VIA VT3314 chipset
[   23.666676] agpgart: AGP aperture is 128M @ 0xf0000000
[   23.772954] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.867218] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.961259] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   24.961419] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   25.009345] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   25.011814] parport_pc 00:08: reported by Plug and Play ACPI
[   25.011906] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   25.013390] input: PC Speaker as /class/input/input3
[   26.389051] lp0: using parport0 (interrupt-driven).
[   26.434980] Adding 1317288k swap on /dev/hda5.  Priority:-1 extents:1 across:1317288k
[   26.690571] EXT3 FS on hda1, internal journal
[   27.589941] input: Power Button (FF) as /class/input/input4
[   27.589972] ACPI: Power Button (FF) [PWRF]
[   27.590098] input: Sleep Button (CM) as /class/input/input5
[   27.590140] ACPI: Sleep Button (CM) [SLPB]
[   27.590214] input: Power Button (CM) as /class/input/input6
[   27.590244] ACPI: Power Button (CM) [PWRB]
[   27.696737] No dock devices found.
[   29.222840] ppdev: user-space parallel port driver
[   29.333829] audit(1196282047.762:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4826 profile="/usr/sbin/cupsd"
[   29.416879] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.416887] apm: disabled - APM is not SMP safe.
[   29.579968] Failure registering capabilities with primary security module.
[   29.734798] Bluetooth: Core ver 2.11
[   29.734967] NET: Registered protocol family 31
[   29.734972] Bluetooth: HCI device and connection manager initialized
[   29.734976] Bluetooth: HCI socket layer initialized
[   29.744093] Bluetooth: L2CAP ver 2.8
[   29.744100] Bluetooth: L2CAP socket layer initialized
[   29.804345] Bluetooth: RFCOMM socket layer initialized
[   29.804492] Bluetooth: RFCOMM TTY layer initialized
[   29.804498] Bluetooth: RFCOMM ver 1.8
[  188.403339] NET: Registered protocol family 10
[  188.404294] lo: Disabled Privacy Extensions

---

### Post by sajiv_k on 2007-11-29
I tried a lot of things; even reinstalling and it still didnt work.

But when I came back today morning and booted up the computer, my Ethernet card got detected.


Magic :lolflag:

---

### Post by jcsteele on 2007-11-29
can you post the output of your "lspci" on the working system now?  just curious.  Glad everything is working now though.

//jcs

---

### Post by sajiv_k on 2007-12-03
Here you go buddy

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

