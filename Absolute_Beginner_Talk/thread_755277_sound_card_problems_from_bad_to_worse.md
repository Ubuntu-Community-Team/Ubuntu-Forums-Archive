---
title: "sound card problems from bad to worse"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by PoseidonOSU on 2008-04-14
In the beginning  in noticed a problem with some sound. The intro noise and basic games and movies played sound but when I tried to play Alien Arena it was staticky and horrible sounding. Then I tried playing boson and noticed that it was horribly unstable and if it did run for a few seconds I never heard any sound. 

 I figured I had/have a sound card issue. At this time the system said I have a sis sound card A'C97 7XXXXXXish from what I remember remember .

Based on something I read in a post I went here to try to fix it:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I got about half way through it. I got th stuff loaded and installed and then got as far as the reboot. After the reboot NO SOUND. A little Speaker with a no symbol appeared by my clock and it says: "No volume control GStreamer plugins and/or devices found."  i tried like the instructions say and looking at dmesg but I got a ton of stuff and  I could not find a single reference to snd anything.

I tried going into synaptic and reinstalling my ALSA stuff and then a reboot. That didn't help ether. Now I sit in silence! 

lspci says:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


dmesg says:
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5330
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
[    0.000000] ACPI: RSDP signature @ 0xC00F6BF0 checksum 0
[    0.000000] ACPI: RSDP 000F6BF0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 7FFF30C0, 3851 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF6940, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=6ce39dc7-3f02-487e-a35f-08352b21b2c6 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3014.796 MHz processor.
[   22.071634] Console: colour VGA+ 80x25
[   22.072165] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.072607] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.168005] Memory: 2067584k/2097088k available (2015k kernel code, 28188k reserved, 915k data, 364k init, 1179584k highmem)
[   22.168016] virtual kernel memory layout:
[   22.168017]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.168018]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.168019]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.168020]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.168021]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.168022]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   22.168023]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   22.168027] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.168079] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.247947] Calibrating delay using timer specific routine.. 6033.11 BogoMIPS (lpj=12066220)
[   22.247982] Security Framework v1.0.0 initialized
[   22.247989] SELinux:  Disabled at boot.
[   22.248003] Mount-cache hash table entries: 512
[   22.248169] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.248177] monitor/mwait feature present.
[   22.248179] using mwait in idle threads.
[   22.248187] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.248190] CPU: L2 cache: 1024K
[   22.248193] CPU: Physical Processor ID: 0
[   22.248195] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   22.248207] Compat vDSO mapped to ffffe000.
[   22.248225] Checking 'hlt' instruction... OK.
[   22.264067] SMP alternatives: switching to UP code
[   22.264659] Early unpacking initramfs... done
[   22.544023] ACPI: Core revision 20070126
[   22.544078] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.549570] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   22.549592] SMP alternatives: switching to SMP code
[   22.549737] Booting processor 1/1 eip 3000
[   22.559903] Initializing CPU#1
[   22.639168] Calibrating delay using timer specific routine.. 6029.47 BogoMIPS (lpj=12058956)
[   22.639179] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.639185] monitor/mwait feature present.
[   22.639193] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.639196] CPU: L2 cache: 1024K
[   22.639198] CPU: Physical Processor ID: 0
[   22.639201] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   22.639579] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   22.639623] Total of 2 processors activated (12062.58 BogoMIPS).
[   22.639720] ENABLING IO-APIC IRQs
[   22.639896] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.786999] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.806976] Brought up 2 CPUs
[   22.937077] migration_cost=147
[   22.937268] Booting paravirtualized kernel on bare hardware
[   22.937342] Time: 21:16:54  Date: 03/14/108
[   22.937370] NET: Registered protocol family 16
[   22.937471] EISA bus registered
[   22.937477] ACPI: bus type pci registered
[   22.959256] PCI: PCI BIOS revision 2.10 entry at 0xfb470, last bus=1
[   22.959258] PCI: Using configuration type 1
[   22.959260] Setting up standard PCI resources
[   22.961004] ACPI: EC: Look up EC in DSDT
[   22.964817] ACPI: Interpreter enabled
[   22.964821] ACPI: (supports S0 S1 S4 S5)
[   22.964841] ACPI: Using IOAPIC for interrupt routing
[   22.969956] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.969964] PCI: Probing PCI hardware (bus 00)
[   22.970876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.986470] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   22.986580] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   22.986683] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   22.986784] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   22.986883] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   22.986984] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   22.987089] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   22.987191] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   22.987309] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.987321] pnp: PnP ACPI init
[   22.987330] ACPI: bus type pnp registered
[   22.990191] pnp: PnP ACPI: found 13 devices
[   22.990194] ACPI: ACPI bus type pnp unregistered
[   22.990200] PnPBIOS: Disabled by ACPI PNP
[   22.990267] PCI: Using ACPI for IRQ routing
[   22.990271] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.997824] NET: Registered protocol family 8
[   22.997827] NET: Registered protocol family 20
[   22.997911] pnp: 00:0c: iomem range 0xcd000-0xcffff has been reserved
[   22.997915] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   22.997918] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   22.997921] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   22.998485] Time: tsc clocksource has been installed.
[   23.028241] PCI: Bridge: 0000:00:01.0
[   23.028246]   IO window: 9000-9fff
[   23.028252]   MEM window: e4000000-e5ffffff
[   23.028257]   PREFETCH window: d0000000-dfffffff
[   23.028278] NET: Registered protocol family 2
[   23.074475] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.074593] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   23.075782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.076329] TCP: Hash tables configured (established 131072 bind 65536)
[   23.076332] TCP reno registered
[   23.086615] checking if image is initramfs... it is
[   23.529437] Switched to high resolution mode on CPU 0
[   23.529534] Switched to high resolution mode on CPU 1
[   23.642813] Freeing initrd memory: 7067k freed
[   23.643468] audit: initializing netlink socket (disabled)
[   23.643486] audit(1208207814.212:1): initialized
[   23.643608] highmem bounce pool size: 64 pages
[   23.645986] VFS: Disk quotas dquot_6.5.1
[   23.646047] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.646153] io scheduler noop registered
[   23.646156] io scheduler anticipatory registered
[   23.646158] io scheduler deadline registered
[   23.646174] io scheduler cfq registered (default)
[   23.646243] Boot video device is 0000:01:00.0
[   23.646417] isapnp: Scanning for PnP cards...
[   23.997393] isapnp: No Plug & Play device found
[   24.024348] Real Time Clock Driver v1.12ac
[   24.024498] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.024597] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.024773] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.025395] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.025670] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.026489] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.026710] input: Macintosh mouse button emulation as /class/input/input0
[   24.026806] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.027083] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.027094] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.027856] mice: PS/2 mouse device common for all mice
[   24.027998] EISA: Probing bus 0 at eisa.0
[   24.028007] Cannot allocate resource for EISA slot 1
[   24.028037] EISA: Detected 0 cards.
[   24.028135] TCP cubic registered
[   24.028148] NET: Registered protocol family 1
[   24.028174] Using IPI No-Shortcut mode
[   24.028330]   Magic number: 4:985:297
[   24.028379]   hash matches device ttywe
[   24.028846] Freeing unused kernel memory: 364k freed
[   24.046027] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.243116] AppArmor: AppArmor initialized<5>audit(1208207815.712:2):  type=1505 info="AppArmor initialized" pid=1197
[   25.252046] fuse init (API version 7.8)
[   25.257295] Failure registering capabilities with primary security module.
[   25.877276] usbcore: registered new interface driver usbfs
[   25.877321] usbcore: registered new interface driver hub
[   25.877357] usbcore: registered new device driver usb
[   25.878481] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.878531] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   25.878547] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   25.878742] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   25.878765] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe7013000
[   25.958735] SCSI subsystem initialized
[   25.979910] usb usb1: configuration #1 chosen from 1 choice
[   25.979966] hub 1-0:1.0: USB hub found
[   25.979980] hub 1-0:1.0: 3 ports detected
[   26.009873] libata version 2.21 loaded.
[   26.010477] sis900.c: v1.08.10 Apr. 2 2006
[   26.017955] Floppy drive(s): fd0 is 1.44M
[   26.036137] FDC 0 is a post-1991 82077
[   26.080480] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   26.080503] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   26.080539] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   26.080561] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe7014000
[   26.138314] usb usb2: configuration #1 chosen from 1 choice
[   26.138362] hub 2-0:1.0: USB hub found
[   26.138376] hub 2-0:1.0: 3 ports detected
[   26.240116] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   26.240137] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   26.240171] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   26.240189] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe7010000
[   26.298001] usb usb3: configuration #1 chosen from 1 choice
[   26.298047] hub 3-0:1.0: USB hub found
[   26.298060] hub 3-0:1.0: 2 ports detected
[   26.383710] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   26.400416] pata_sis 0000:00:02.5: version 0.5.1
[   26.400460] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 19
[   26.401621] scsi0 : pata_sis
[   26.401728] scsi1 : pata_sis
[   26.401944] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   26.401950] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   26.579440] ata1.00: Host Protected Area detected:
[   26.579443]  current size: 40086047 sectors
[   26.579444]  native size: 40088160 sectors
[   26.579736] ata1.00: native size increased to 40088160 sectors
[   26.579739] ata1.00: ATA-4: IBM-DPTA-372050, P76GA30A, max UDMA/66
[   26.579742] ata1.00: 40088160 sectors, multi 16: LBA 
[   26.581252] ata1.01: ATA-7: Maxtor 6L120P0, BAH41G10, max UDMA/133
[   26.581255] ata1.01: 240121728 sectors, multi 16: LBA 
[   26.581261] ata1.00: limited to UDMA/33 due to 40-wire cable
[   26.581264] ata1.01: limited to UDMA/33 due to 40-wire cable
[   26.593619] usb 1-2: configuration #1 chosen from 1 choice
[   26.596563] hub 1-2:1.0: USB hub found
[   26.599497] hub 1-2:1.0: 4 ports detected
[   26.604256] ata1.00: configured for UDMA/33
[   26.620986] ata1.01: configured for UDMA/33
[   26.946806] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R902, max UDMA/33
[   26.947673] ata2.01: ATA-5: WDC WD800BB-00CAA1, 17.07W17, max UDMA/100
[   26.947676] ata2.01: 156301488 sectors, multi 16: LBA 
[   27.022433] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   27.118461] ata2.00: configured for UDMA/33
[   27.135289] ata2.01: configured for UDMA/100
[   27.135447] scsi 0:0:0:0: Direct-Access     ATA      IBM-DPTA-372050  P76G PQ: 0 ANSI: 5
[   27.135613] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L120P0   BAH4 PQ: 0 ANSI: 5
[   27.136538] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R902 PQ: 0 ANSI: 5
[   27.136691] scsi 1:0:1:0: Direct-Access     ATA      WDC WD800BB-00CA 17.0 PQ: 0 ANSI: 5
[   27.137291] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[   27.138383] 0000:00:04.0: ICS LAN PHY transceiver found at address 1.
[   27.148607] 0000:00:04.0: Using transceiver found at address 1 as default
[   27.150357] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 20, 00:0f:ea:f7:07:00.
[   27.150550] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
[   27.150567] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   27.150623] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   27.150667] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   27.150684] ehci_hcd 0000:00:03.3: irq 21, io mem 0xe7011000
[   27.169325] sd 0:0:0:0: [sda] 40088160 512-byte hardware sectors (20525 MB)
[   27.169346] sd 0:0:0:0: [sda] Write Protect is off
[   27.169350] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.169375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.169457] sd 0:0:0:0: [sda] 40088160 512-byte hardware sectors (20525 MB)
[   27.169472] sd 0:0:0:0: [sda] Write Protect is off
[   27.169475] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.169499] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.169506]  sda: sda1
[   27.174661] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.174764] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   27.174782] sd 0:0:1:0: [sdb] Write Protect is off
[   27.174786] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.174815] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.174883] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   27.174900] sd 0:0:1:0: [sdb] Write Protect is off
[   27.174905] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.174960] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.174965]  sdb: sdb1
[   27.190991] sd 0:0:1:0: [sdb] Attached SCSI disk
[   27.191074] sd 1:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   27.191090] sd 1:0:1:0: [sdc] Write Protect is off
[   27.191094] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   27.191121] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.191187] sd 1:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   27.191204] sd 1:0:1:0: [sdc] Write Protect is off
[   27.191208] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   27.191236] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.191240]  sdc:<6>ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.202229] usb usb4: configuration #1 chosen from 1 choice
[   27.202274] hub 4-0:1.0: USB hub found
[   27.202286] hub 4-0:1.0: 8 ports detected
[   27.214790]  sdc1 sdc2 < sdc5 >
[   27.243900] sd 1:0:1:0: [sdc] Attached SCSI disk
[   27.245098] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
[   27.245104] Uniform CD-ROM driver Revision: 3.20
[   27.245183] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   27.253918] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.254199] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   27.254434] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   27.254722] sd 1:0:1:0: Attached scsi generic sg3 type 0
[   27.306126] sata_sis 0000:00:05.0: version 0.8
[   27.306165] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   27.306175] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   27.306294] scsi2 : sata_sis
[   27.306376] scsi3 : sata_sis
[   27.306423] ata3: SATA max UDMA/133 cmd 0x0001ac00 ctl 0x0001b002 bmdma 0x0001bc00 irq 22
[   27.306431] ata4: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b802 bmdma 0x0001bc08 irq 22
[   27.551948] Attempting manual resume
[   27.551952] swsusp: Resume From Partition 8:37
[   27.551954] PM: Checking swsusp image.
[   27.552139] PM: Resume from disk failed.
[   27.596685] kjournald starting.  Commit interval 5 seconds
[   27.596701] EXT3-fs: mounted filesystem with ordered data mode.
[   27.609268] usb 3-1: device not accepting address 2, error -62
[   27.617272] ata3: SATA link down (SStatus 0 SControl 300)
[   27.666289] hub 1-2:1.0: hub_port_status failed (err = -62)
[   27.669283] hub 1-2:1.0: hub_port_status failed (err = -62)
[   27.672276] hub 1-2:1.0: hub_port_status failed (err = -62)
[   27.675267] hub 1-2:1.0: hub_port_status failed (err = -62)
[   27.800889] usb 1-2: USB disconnect, address 2
[   28.092316] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.272123] ata4.00: ATAPI: Optiarc DVD RW AD-7190S, 1.00, max UDMA/100
[   28.459758] ata4.00: configured for UDMA/100
[   28.461096] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7190S  1.00 PQ: 0 ANSI: 5
[   28.469726] sr1: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.469778] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   28.469822] sr 3:0:0:0: Attached scsi generic sg4 type 5
[   28.715069] usb 3-1: new full speed USB device using ohci_hcd and address 4
[   28.930574] usb 3-1: configuration #1 chosen from 1 choice
[   29.238003] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   29.447711] usb 1-2: configuration #1 chosen from 1 choice
[   29.450632] hub 1-2:1.0: USB hub found
[   29.453597] hub 1-2:1.0: 4 ports detected
[   29.786912] usb 1-2.2: new full speed USB device using ohci_hcd and address 4
[   29.885705] usb 1-2.2: not running at top speed; connect to a high speed hub
[   29.903805] usb 1-2.2: configuration #1 chosen from 1 choice
[   35.158551] Linux agpgart interface v0.102 (c) Dave Jones
[   35.274268] agpgart: Detected SiS chipset - id:1608
[   35.279131] agpgart: AGP aperture is 64M @ 0xe0000000
[   35.297116] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.300987] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.306955] ath_hal: module license 'Proprietary' taints kernel.
[   35.308007] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   35.975902] wlan: 0.8.4.2 (0.9.3.2)
[   36.165192] usbcore: registered new interface driver libusual
[   36.178915] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5611
[   36.178952] usbcore: registered new interface driver usblp
[   36.178957] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   36.228360] ath_pci: 0.9.4.5 (0.9.3.2)
[   36.228507] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   36.805630] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   36.805638] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   36.836108] Initializing USB Mass Storage driver...
[   36.836233] scsi4 : SCSI emulation for USB Mass Storage devices
[   36.836316] usb-storage: device found at 4
[   36.836319] usb-storage: waiting for device to settle before scanning
[   36.836336] usbcore: registered new interface driver usb-storage
[   36.836340] USB Mass Storage support registered.
[   36.846715] ath_rate_sample: 1.2 (0.9.3.2)
[   36.848056] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   36.848063] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   36.848075] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   36.848080] wifi0: mac 7.8 phy 4.5 radio 5.6
[   36.848087] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   36.848089] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   36.848092] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   36.848093] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   36.848096] wifi0: Use hw queue 8 for CAB traffic
[   36.848097] wifi0: Use hw queue 9 for beacons
[   36.873175] wifi0: Atheros 5212: mem=0xe7000000, irq=20
[   37.338608] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   37.341342] parport_pc 00:09: reported by Plug and Play ACPI
[   37.341420] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.343761] input: PC Speaker as /class/input/input3
[   37.604423] lp0: using parport0 (interrupt-driven).
[   37.658976] Adding 3229024k swap on /dev/sdc5.  Priority:-1 extents:1 across:3229024k
[   37.948629] EXT3 FS on sdc1, internal journal
[   38.934518] No dock devices found.
[   38.997047] input: Power Button (FF) as /class/input/input4
[   38.997075] ACPI: Power Button (FF) [PWRF]
[   38.997141] input: Power Button (CM) as /class/input/input5
[   38.997167] ACPI: Power Button (CM) [PWRB]
[   40.449362] ppdev: user-space parallel port driver
[   40.736743] audit(1208207831.958:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4751 profile="/usr/sbin/cupsd"
[   40.891547] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   40.891554] apm: disabled - APM is not SMP safe.
[   41.295035] Failure registering capabilities with primary security module.
[   41.788459] Bluetooth: Core ver 2.11
[   41.788692] NET: Registered protocol family 31
[   41.788697] Bluetooth: HCI device and connection manager initialized
[   41.788705] Bluetooth: HCI socket layer initialized
[   41.826093] usb-storage: device scan complete
[   41.833078] scsi 4:0:0:0: Direct-Access     HP       Photosmart C3180 1.00 PQ: 0 ANSI: 2
[   41.842918] Bluetooth: L2CAP ver 2.8
[   41.842925] Bluetooth: L2CAP socket layer initialized
[   41.844968] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[   41.845051] sd 4:0:0:0: Attached scsi generic sg5 type 0
[   41.931909] Bluetooth: RFCOMM socket layer initialized
[   41.932065] Bluetooth: RFCOMM TTY layer initialized
[   41.932070] Bluetooth: RFCOMM ver 1.8
[   42.779585] eth0: Media Link On 100mbps full-duplex 
[   44.261376] [drm] Initialized drm 1.1.0 20060810
[   44.329225] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   44.329968] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   46.429010] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   46.429198] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   46.429204] agpgart: SiS delay workaround: giving bridge time to recover.
[   46.443676] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   46.720496] [drm] Setting GART location based on new memory map
[   46.720508] [drm] Loading R300 Microcode
[   46.720554] [drm] writeback test succeeded in 1 usecs
[   46.821010] NET: Registered protocol family 17
[   49.279990] NET: Registered protocol family 10
[   49.280280] lo: Disabled Privacy Extensions
[   59.357797] ath0: no IPv6 routers present
[   59.796921] eth0: no IPv6 routers present


Thanks guys

---

### Post by estaticd on 2008-04-14
What model sound card do you have?

Have a look at this, might help:
[http://ubuntuforums.org/showthread.php?t=484876](http://ubuntuforums.org/showthread.php?t=484876)

---

### Post by PoseidonOSU on 2008-04-15
thanks
that seemed to work to get be back to where I was. I still have horrible audio on the alien thing and Boson won't work. Let me see if they are unrelated problems.

E

---

