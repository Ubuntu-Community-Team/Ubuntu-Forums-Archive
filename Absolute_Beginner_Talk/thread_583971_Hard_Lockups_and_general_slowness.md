---
title: "Hard Lockups and general slowness???"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by sad_iq on 2007-10-20
Ok...Just bought a new second-hand computer from a friend...and normally the first thing i did was installing linux into it! I installed Arch Linux....to test another distro...but after about 10 minutes the computer froze. I thought it was my fault(not too skilled yet)...so inserted my new Ubuntu 7.10 cd and tried to install it...froze in the middle of install. Tried many times with the same result.Tried my kubuntu 7.04 cd...same result. 
Also...running the live cd freezes my pc after about 5-10 minutes without any reason. The only thing I manage to install was Sabayon linux...but I really want to put ubuntu on my machine..so I tried to reinstalled it once more...success!!! The only thing is that it is very slow...everything runs smooth until the login screen...then all goes SLOW...I have to wait more than 2 minutes to even see the standard backgroung image, another 2 minutes for the Application bar,,,then to get to a console takes me another 2-3 minutes. I have all the latest updates and my graphics driver(using envy) installed so it should be hardware related. But what could it be??? I have a P4 2800 (no HT), 512 Ram, an Ati radeon 9800 Pro. Here is my dmesg and my lspci -v:
 ```
willy@willy:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f53b0
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
[    0.000000] ACPI: RSDP signature @ 0xC00F7560 checksum 0
[    0.000000] ACPI: RSDP 000F7560, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 1FFF30C0, 3104 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF6200, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=98ec1fa0-e9b1-4e98-87ba-a911fa2a50b7 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2813.620 MHz processor.
[   27.898357] Console: colour VGA+ 80x25
[   27.898635] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.898875] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.908324] Memory: 507916k/524224k available (2015k kernel code, 15720k reserved, 916k data, 364k init, 0k highmem)
[   27.908335] virtual kernel memory layout:
[   27.908336]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   27.908338]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.908339]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   27.908340]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   27.908341]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   27.908342]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   27.908343]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   27.908347] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.908388] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.988204] Calibrating delay using timer specific routine.. 5631.35 BogoMIPS (lpj=11262705)
[   27.988232] Security Framework v1.0.0 initialized
[   27.988237] SELinux:  Disabled at boot.
[   27.988250] Mount-cache hash table entries: 512
[   27.988388] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[   27.988398] monitor/mwait feature present.
[   27.988400] using mwait in idle threads.
[   27.988408] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   27.988411] CPU: L2 cache: 1024K
[   27.988414] CPU: Hyper-Threading is disabled
[   27.988416] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000
[   27.988428] Compat vDSO mapped to ffffe000.
[   27.988444] Checking 'hlt' instruction... OK.
[   28.004259] SMP alternatives: switching to UP code
[   28.004417] Freeing SMP alternatives: 11k freed
[   28.004702] Early unpacking initramfs... done
[   28.317298] ACPI: Core revision 20070126
[   28.317352] [COLOR="Red"]ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.[/COLOR]
[   28.320163] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   28.320205] Total of 1 processors activated (5631.35 BogoMIPS).
[   28.320307] ENABLING IO-APIC IRQs
[   28.320481] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.467025] Brought up 1 CPUs
[   28.467144] Booting paravirtualized kernel on bare hardware
[   28.467215] Time: 21:12:14  Date: 09/20/107
[   28.467237] NET: Registered protocol family 16
[   28.467330] EISA bus registered
[   28.467344] ACPI: bus type pci registered
[   28.478830] PCI: PCI BIOS revision 2.10 entry at 0xfb200, last bus=1
[   28.478833] PCI: Using configuration type 1
[   28.478835] Setting up standard PCI resources
[   28.486890] ACPI: EC: Look up EC in DSDT
[   28.489989] ACPI: Interpreter enabled
[   28.489993] ACPI: (supports S0 S3 S4 S5)
[   28.490017] ACPI: Using IOAPIC for interrupt routing
[   28.494034] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.494049] PCI: Probing PCI hardware (bus 00)
[   28.494245] Enabling SiS 96x SMBus.
[   28.494956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.509843] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.509967] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   28.510070] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.510175] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   28.510278] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[   28.510382] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   28.510486] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   28.510592] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.510690] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.510703] pnp: PnP ACPI init
[   28.510711] ACPI: bus type pnp registered
[   28.512531] pnp: PnP ACPI: found 9 devices
[   28.512534] ACPI: ACPI bus type pnp unregistered
[   28.512538] PnPBIOS: Disabled by ACPI PNP
[   28.512590] PCI: Using ACPI for IRQ routing
[   28.512594] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.520669] NET: Registered protocol family 8
[   28.520672] NET: Registered protocol family 20
[   28.522845] Time: tsc clocksource has been installed.
[   28.551000] PCI: Bridge: 0000:00:01.0
[   28.551005]   IO window: d000-dfff
[   28.551011]   MEM window: e0000000-e1ffffff
[   28.551016]   PREFETCH window: d0000000-dfffffff
[   28.551038] NET: Registered protocol family 2
[   28.590710] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   28.590755] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   28.590881] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   28.590962] TCP: Hash tables configured (established 16384 bind 16384)
[   28.590965] TCP reno registered
[   28.602775] checking if image is initramfs... it is
[   29.053495] Switched to high resolution mode on CPU 0
[   29.214394] Freeing initrd memory: 7351k freed
[   29.214887] [COLOR="Red"]audit: initializing netlink socket (disabled)[/COLOR]
[   29.214905] audit(1192914734.012:1): initialized
[   29.217132] VFS: Disk quotas dquot_6.5.1
[   29.217186] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.217288] io scheduler noop registered
[   29.217290] io scheduler anticipatory registered
[   29.217293] io scheduler deadline registered
[   29.217309] io scheduler cfq registered (default)
[   29.300796] Boot video device is 0000:01:00.0
[   29.300959] isapnp: Scanning for PnP cards...
[   29.653965] isapnp: No Plug & Play device found
[   29.681694] Real Time Clock Driver v1.12ac
[   29.681787] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.683008] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.683151] input: Macintosh mouse button emulation as /class/input/input0
[   29.683240] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.683510] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.683517] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.683697] mice: PS/2 mouse device common for all mice
[   29.683828] EISA: Probing bus 0 at eisa.0
[   29.683838] Cannot allocate resource for EISA slot 1
[   29.683865] EISA: Detected 0 cards.
[   29.683959] TCP cubic registered
[   29.683972] NET: Registered protocol family 1
[   29.683995] Using IPI No-Shortcut mode
[   29.684140]   Magic number: 11:922:247
[   29.684185]   hash matches device ttyw3
[   29.684632] Freeing unused kernel memory: 364k freed
[   29.727729] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.892653] AppArmor: AppArmor initialized<5>audit(1192914735.512:2):  type=1505 info="AppArmor initialized" pid=1166
[   30.899578] fuse init (API version 7.8)
[   30.904598][COLOR="Red"] Failure registering capabilities with primary security module.[/COLOR]
[   30.926195] [COLOR="Red"]ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126][/COLOR]
[   31.455265] SCSI subsystem initialized
[   31.461016] libata version 2.21 loaded.
[   31.462553] pata_sis 0000:00:02.5: version 0.5.1
[   31.462692] scsi0 : pata_sis
[   31.462740] scsi1 : pata_sis
[   31.462866] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   31.462870] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   31.488164] usbcore: registered new interface driver usbfs
[   31.488192] usbcore: registered new interface driver hub
[   31.488218] usbcore: registered new device driver usb
[   31.493001] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.560826] 8139too Fast Ethernet driver 0.9.28
[   31.678824] ata1.00: ATA-6: ST3160021A, 3.04, max UDMA/100
[   31.678829] ata1.00: 312581808 sectors, multi 16: LBA48 
[   31.694767] ata1.00: configured for UDMA/100
[   32.169483] ata2.00: ATAPI: JLMS XJ-HD166S, D9C2, max UDMA/33
[   32.169489] ata2.01: ATAPI: _NEC DVD_RW ND-1300A, 1.10, max UDMA/33
[   32.325067] ata2.00: configured for UDMA/33
[   32.496541] ata2.01: configured for UDMA/33
[   32.496680] scsi 0:0:0:0: Direct-Access     ATA      ST3160021A       3.04 PQ: 0 ANSI: 5
[   32.497267] scsi 1:0:0:0: CD-ROM            JLMS     XJ-HD166S        D9C2 PQ: 0 ANSI: 5
[   32.500522] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.10 PQ: 0 ANSI: 5
[   32.503360] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   32.503376] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   32.503680] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   32.503699] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe3001000
[   32.523657] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   32.523704] sd 0:0:0:0: [sda] Write Protect is off
[   32.523707] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.523742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.523813] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   32.523826] sd 0:0:0:0: [sda] Write Protect is off
[   32.523829] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.523849] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.523854]  sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   32.558284] hub 1-0:1.0: USB hub found
[   32.558297] hub 1-0:1.0: 2 ports detected
[   32.572081]  sda5 >
[   32.572638] sd 0:0:0:0: [sda] Attached SCSI disk
[   32.576907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.576929] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   32.576951] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   32.604631] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   32.604637] Uniform CD-ROM driver Revision: 3.20
[   32.604895] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   32.610830] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   32.611002] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   32.660010] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   32.660029] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   32.660057] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   32.660074] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe3002000
[   32.717824] usb usb2: configuration #1 chosen from 1 choice
[   32.717858] hub 2-0:1.0: USB hub found
[   32.717869] hub 2-0:1.0: 2 ports detected
[   32.814718] Attempting manual resume
[   32.814722] swsusp: Resume From Partition 8:5
[   32.814725] [COLOR="Red"]PM: Checking swsusp image.[/COLOR]
[   32.814943] [COLOR="Red"]PM: Resume from disk failed.[/COLOR]
[   32.819620] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   32.819638] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   32.819669] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   32.819686] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe3003000
[   32.831651] EXT3-fs: INFO: recovery required on readonly filesystem.
[   32.831655] EXT3-fs: write access will be enabled during recovery.
[   32.877394] usb usb3: configuration #1 chosen from 1 choice
[   32.877427] hub 3-0:1.0: USB hub found
[   32.877439] hub 3-0:1.0: 2 ports detected
[   32.979384] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   32.979400] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   32.979435] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   32.979470] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   32.979482] ehci_hcd 0000:00:03.3: irq 19, io mem 0xe3004000
[   32.979491] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.979574] usb usb4: configuration #1 chosen from 1 choice
[   32.979605] hub 4-0:1.0: USB hub found
[   32.979614] hub 4-0:1.0: 6 ports detected
[   33.049896] kjournald starting.  Commit interval 5 seconds
[   33.049913] EXT3-fs: recovery complete.
[   33.052143] EXT3-fs: mounted filesystem with ordered data mode.
[   33.082998] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 16 (level, low) -> IRQ 20
[   33.083297] eth0: RealTek RTL8139 at 0xe083a000, 00:0d:61:52:b0:00, IRQ 20
[   33.083300] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   33.085962] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   37.623863] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.317890] NET: Registered protocol family 10
[   38.317979] lo: Disabled Privacy Extensions
[   39.149387] Linux agpgart interface v0.102 (c) Dave Jones
[   39.175499] agpgart: Detected SiS chipset - id:1608
[   39.192546] agpgart: AGP aperture is 256M @ 0xc0000000
[   39.285125] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.299615] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.412105] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[   40.077858] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.081022] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   40.081027][COLOR="Red"] [fglrx] USWC is disabled in module parameters[/COLOR]
[   40.081029] [COLOR="Red"][fglrx] PAT is disabled![/COLOR]
[   40.081050] [fglrx] module loaded - fglrx 8.40.4 [Jul 31 2007] on minor 0
[   40.131124] input: PC Speaker as /class/input/input2
[   40.342276] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[   40.677650] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input3
[   41.165259] intel8x0_measure_ac97_clock: measured 55495 usecs
[   41.165264] intel8x0: clocking to 48000
[   41.413825] lp: driver loaded but no devices found
[   41.502934] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   41.811837] EXT3 FS on sda1, internal journal
[   42.584392] No dock devices found.
[   42.698986] input: Power Button (FF) as /class/input/input4
[   42.703492] ACPI: Power Button (FF) [PWRF]
[   42.743052] input: Power Button (CM) as /class/input/input5
[   42.747444] ACPI: Power Button (CM) [PWRB]
[   49.040325] eth0: no IPv6 routers present
[   53.993998] ppdev: user-space parallel port driver
[   64.125799] audit(1192914769.710:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4450 profile="/usr/sbin/cupsd"
[   84.152212] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   84.152219] [COLOR="Red"]apm: overridden by ACPI.[/COLOR]
[   84.348484] [COLOR="Red"]Failure registering capabilities with primary security module.[/COLOR]
[   84.507275] Bluetooth: Core ver 2.11
[   84.507400] NET: Registered protocol family 31
[   84.507404] Bluetooth: HCI device and connection manager initialized
[   84.507407] Bluetooth: HCI socket layer initialized
[   84.518688] Bluetooth: L2CAP ver 2.8
[   84.518693] Bluetooth: L2CAP socket layer initialized
[   84.583810] Bluetooth: RFCOMM socket layer initialized
[   84.583912] Bluetooth: RFCOMM TTY layer initialized
[   84.583916] Bluetooth: RFCOMM ver 1.8
[   86.390204] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   88.446531] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   88.446538] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   88.446543] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[   88.447235] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   88.447421] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   88.447426] agpgart: SiS delay workaround: giving bridge time to recover.
[   88.459624] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   88.459837] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   88.468128] [fglrx] total      GART = 268435456
[   88.468135] [fglrx] free       GART = 252440576
[   88.468138] [fglrx] max single GART = 252440576
[   88.468140] [fglrx] total      LFB  = 134217728
[   88.468142] [fglrx] free       LFB  = 116387840
[   88.468144] [fglrx] max single LFB  = 116387840
[   88.468146] [fglrx] total      Inv  = 134217728
[   88.468148] [fglrx] free       Inv  = 134217728
[   88.468150] [fglrx] max single Inv  = 134217728
[   88.468152] [fglrx] total      TIM  = 0
willy@willy:~$ 


```

```
willy@willy:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32
        Memory at c0000000 (32-bit, non-prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 1400 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e3001000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at e3002000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at e3003000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e3004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Unknown device 1631:e009
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at e800 [size=256]
        Memory at e3005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (prog-if 00 [VGA])
        Subsystem: Unknown device 1fd3:4e48
        Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 20
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at d000 [size=256]
        Memory at e1000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e0000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
        Subsystem: Unknown device 1fd3:4e49
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at e1010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

willy@willy:~$ 


```

---

### Post by barkej on 2007-10-20
This does sound like a hardware issue. It could be a number of things though. My first guess would be overheating followed closely by a bad power supply. Was Sabayon slow for you also?

---

### Post by barkej on 2007-10-20
Forgot to subscribe to thread.

---

### Post by sad_iq on 2007-10-21
Sabayon was almost the same, and I had fluxbox running there. The processor appears pretty cool, looking into the bios after about a few hours of running sabayon showed 45 degrees, same after ubuntu lockes after 10 minutes. The only thing that confuses me is that with sabayon it didn't crash, so why does it crash with Arch and Ubuntu??? The power supply could be a problem, it only has 280 wats. I will change it today and see if that still happens. But what about the error messages that appear with dmesg(colored in red??). also booting ubuntu with acpi=off lockes ubuntu before it even gets to the login screen :(
 Also memtest doesn't get any errors so the memory is OK.

---

### Post by pdlethbridge on 2007-10-21
It could be overheating. Check the case fans and make sure they are all working. I have mine set to blow into the case at the bottom in front, and pull out the air in back. Try cooling the case with a desk fan, and see if the problem goes away. I had problems with the inside of my case getting hot, but leaving the side panel off solved the problem.

---

### Post by sad_iq on 2007-10-21
Cooling appears to be working ok, all fans are spinning ok, the dust has been cleaned...so there has to be something else.

---

### Post by sad_iq on 2007-10-21
Anyone??

---

### Post by Sef on 2007-10-21
Check your memory.  Do a mem86 test.   Hit Esc and at the bottom is mem86 test.  Run it overnight and see what happens.  Hit C, I believe, when you are finished...it will tell you the results.

---

### Post by sad_iq on 2007-10-21
I have checked the memory...it is ok...and by the looks of the errors it appears to be a acpi problem, because windows worked ok..I will tryto install windows on it again and try to update the bios, but I doubt it wil fix things!! Also booting with acpi=off lockes it up hard!!!

---

### Post by sad_iq on 2007-10-21
anyone knows of any other boot option that can affect loading the system???

---

