---
title: "wrong fs type, bad option, bad superblock on /dev/hdb1"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by MasterColdSoul on 2007-01-21
I am trying to mount my 2nd hard drives NTSF partition on boot so I can access my MP3s, Videos and documents on that drive. There is no form of windows on that drive.

Here is my fdisk info:
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         524       19326   151035097+   7  HPFS/NTFS
/dev/hda2               1         523     4200966    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10148    81513778+   f  W95 Ext'd (LBA)
/dev/hdb2   *       10149       14593    35704462+  83  Linux
/dev/hdb5               2       10014    80429422+   7  HPFS/NTFS
/dev/hdb6           10015       10148     1076323+  82  Linux swap / Solaris

Original fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=96a1f68a-29c9-4852-bd06-4911f66defc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=c1dadd8c-2246-4ccb-b671-83b4005ea3bd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0    

added:
/dev/hdb5  /media/hdb5  ntfs  defaults,umask=0222  0  0

and 

/dev/hdb1  /media/hdb1  ntfs  defaults,umask=0222  0  0
/dev/hdb5  /media/hdb5  ntfs  defaults,umask=0222  0  0

either way I get these errors (or just one if I do only hdb5 which has the data I want:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail gives:
17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000c0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000016f5a000 (usable)
[17179569.184000]  BIOS-e820: 0000000016f5a000 - 0000000016ff8000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000016ff8000 - 0000000017d94000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017d94000 - 0000000017d9c000 (reserved)
[17179569.184000]  BIOS-e820: 0000000017d9c000 - 0000000017e30000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017e30000 - 0000000017e34000 (reserved)
[17179569.184000]  BIOS-e820: 0000000017e34000 - 0000000017eac000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017eac000 - 0000000017eef000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000017eef000 - 0000000017f00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 367MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe860
[17179569.184000] On node 0 totalpages: 94042
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 89946 pages, LIFO batch:15
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v000 GATEWA                                ) @ 0x000fe020
[17179569.184000] ACPI: RSDT (v001 GATEWA 06DT047  0x00000009      0x01000013) @ 0x17efe038
[17179569.184000] ACPI: FADT (v001 GATEWA 06DT047  0x00000009 MSFT 0x01000013) @ 0x17efd000
[17179569.184000] ACPI: MADT (v001 GATEWA 06DT047  0x00000009 MSFT 0x01000013) @ 0x17ef8000
[17179569.184000] ACPI: MCFG (v001 GATEWA 06DT047  0x00000009 MSFT 0x01000013) @ 0x17ef7000
[17179569.184000] ACPI: DSDT (v001 GATEWA 06DT047  0x00000009 MSFT 0x01000013) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 17f00000:e8080000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 3334.467 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.436000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.436000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.444000] Memory: 363112k/376168k available (1910k kernel code, 12448k reserved, 1069k data, 308k init, 0k highmem)
[17179570.444000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.524000] Calibrating delay using timer specific routine.. 6679.29 BogoMIPS (lpj=13358592)
[17179570.524000] Security Framework v1.0.0 initialized
[17179570.524000] SELinux:  Disabled at boot.
[17179570.524000] Mount-cache hash table entries: 512
[17179570.524000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e41d 00000000 00000001
[17179570.524000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e41d 00000000 00000001
[17179570.524000] monitor/mwait feature present.
[17179570.524000] using mwait in idle threads.
[17179570.524000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.524000] CPU: L2 cache: 512K
[17179570.524000] CPU: Hyper-Threading is disabled
[17179570.524000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e41d 00000000 00000001
[17179570.524000] Checking 'hlt' instruction... OK.
[17179570.540000] SMP alternatives: switching to UP code
[17179570.540000] Freeing SMP alternatives: 16k freed
[17179570.540000] checking if image is initramfs... it is
[17179570.936000] Freeing initrd memory: 5322k freed
[17179570.936000] ACPI: Core revision 20060707
[17179570.940000] ACPI: Looking for DSDT ... not found!
[17179570.952000] CPU0: Intel(R) Celeron(R) D CPU 3.33GHz stepping 04
[17179570.952000] Total of 1 processors activated (6679.29 BogoMIPS).
[17179570.952000] ENABLING IO-APIC IRQs
[17179570.952000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.952000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179570.952000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179570.952000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179571.136000] Brought up 1 CPUs
[17179571.136000] migration_cost=0
[17179571.136000] NET: Registered protocol family 16
[17179571.136000] EISA bus registered
[17179571.136000] ACPI: bus type pci registered
[17179571.136000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179571.136000] PCI: Not using MMCONFIG.
[17179571.136000] PCI: Using configuration type 1
[17179571.136000] Setting up standard PCI resources
[17179571.160000] ACPI: Interpreter enabled
[17179571.160000] ACPI: Using IOAPIC for interrupt routing
[17179571.160000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.160000] PCI: Probing PCI hardware (bus 00)
[17179571.160000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.164000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179571.164000] Boot video device is 0000:01:05.0
[17179571.164000] PCI: Transparent bridge - 0000:00:14.4
[17179571.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179571.168000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.168000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.168000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.168000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.168000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.172000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.172000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.172000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.172000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.172000] pnp: PnP ACPI init
[17179571.172000] pnp: PnP ACPI: found 11 devices
[17179571.172000] PnPBIOS: Disabled by ACPI PNP
[17179571.172000] PCI: Using ACPI for IRQ routing
[17179571.172000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.172000] pnp: 00:07: ioport range 0x400-0x4cf could not be reserved
[17179571.172000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179571.172000] PCI: Bridge: 0000:00:01.0
[17179571.172000]   IO window: 2000-2fff
[17179571.172000]   MEM window: 41100000-411fffff
[17179571.172000]   PREFETCH window: 20000000-3fffffff
[17179571.172000] PCI: Bridge: 0000:00:14.4
[17179571.172000]   IO window: 1000-1fff
[17179571.172000]   MEM window: 40000000-410fffff
[17179571.172000]   PREFETCH window: disabled.
[17179571.172000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.172000] PCI: Setting latency timer of device 0000:00:14.4 to 64
[17179571.172000] NET: Registered protocol family 2
[17179571.212000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.212000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.212000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.212000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.212000] TCP reno registered
[17179571.212000] audit: initializing netlink socket (disabled)
[17179571.212000] audit(1169388968.212:1): initialized
[17179571.212000] VFS: Disk quotas dquot_6.5.1
[17179571.212000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.212000] Initializing Cryptographic API
[17179571.212000] io scheduler noop registered
[17179571.212000] io scheduler anticipatory registered
[17179571.212000] io scheduler deadline registered
[17179571.212000] io scheduler cfq registered (default)
[17179571.212000] isapnp: Scanning for PnP cards...
[17179571.564000] isapnp: No Plug & Play device found
[17179571.588000] Real Time Clock Driver v1.12ac
[17179571.588000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.588000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.588000] mice: PS/2 mouse device common for all mice
[17179571.592000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.592000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.592000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.592000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.592000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.592000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.592000] EISA: Probing bus 0 at eisa.0
[17179571.592000] Cannot allocate resource for EISA slot 1
[17179571.592000] Cannot allocate resource for EISA slot 2
[17179571.592000] Cannot allocate resource for EISA slot 3
[17179571.592000] EISA: Detected 0 cards.
[17179571.592000] TCP bic registered
[17179571.592000] NET: Registered protocol family 1
[17179571.592000] NET: Registered protocol family 8
[17179571.592000] NET: Registered protocol family 20
[17179571.592000] Using IPI No-Shortcut mode
[17179571.596000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.596000] Freeing unused kernel memory: 308k freed
[17179571.620000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.772000] Capability LSM initialized
[17179572.804000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.804000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.804000] ACPI: Getting cpuindex for acpiid 0x2
[17179572.804000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.804000] ACPI: Getting cpuindex for acpiid 0x3
[17179572.804000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.804000] ACPI: Getting cpuindex for acpiid 0x4
[17179573.208000] SCSI subsystem initialized
[17179573.212000] libata version 1.20 loaded.
[17179573.212000] sata_sil 0000:00:11.0: version 0.9
[17179573.212000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179573.212000] PCI: Setting latency timer of device 0000:00:11.0 to 64
[17179573.212000] ata1: SATA max UDMA/100 cmd 0xD7830680 ctl 0xD783068A bmdma 0xD7830600 irq 177
[17179573.212000] ata2: SATA max UDMA/100 cmd 0xD78306C0 ctl 0xD78306CA bmdma 0xD7830608 irq 177
[17179573.420000] ata1: SATA link down (SStatus 0)
[17179573.420000] scsi0 : sata_sil
[17179573.624000] ata2: SATA link down (SStatus 0)
[17179573.628000] scsi1 : sata_sil
[17179573.628000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 185
[17179573.628000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[17179573.628000] ata3: SATA max UDMA/100 cmd 0xD7832480 ctl 0xD783248A bmdma 0xD7832400 irq 185
[17179573.628000] ata4: SATA max UDMA/100 cmd 0xD78324C0 ctl 0xD78324CA bmdma 0xD7832408 irq 185
[17179573.832000] ata3: SATA link down (SStatus 0)
[17179573.836000] scsi2 : sata_sil
[17179574.040000] ata4: SATA link down (SStatus 0)
[17179574.044000] scsi3 : sata_sil
[17179574.124000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179574.124000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179574.124000] ATIIXP: chipset revision 128
[17179574.124000] ATIIXP: not 100% native mode: will probe irqs later
[17179574.124000]     ide0: BM-DMA at 0x3000-0x3007, BIOS settings: hda:DMA, hdb:DMA
[17179574.124000]     ide1: BM-DMA at 0x3008-0x300f, BIOS settings: hdc:DMA, hdd:pio
[17179574.124000] Probing IDE interface ide0...
[17179574.416000] hda: WDC WD1600BB-22RDA0, ATA DISK drive
[17179574.700000] hdb: WDC WD1200JB-00FUA0, ATA DISK drive
[17179574.760000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.776000] Probing IDE interface ide1...
[17179575.516000] hdc: TSSTcorpCD/DVDW TS-H552D, ATAPI CD/DVD-ROM drive
[17179576.192000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.232000] hda: max request size: 512KiB
[17179576.240000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[17179576.240000] hda: cache flushes supported
[17179576.240000]  hda: hda1 hda2
[17179576.252000] hdb: max request size: 512KiB
[17179576.372000] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.376000] hdb: cache flushes supported
[17179576.376000]  hdb: hdb1 < hdb5 hdb6 > hdb2
[17179576.444000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.444000] Uniform CD-ROM driver Revision: 3.20
[17179577.144000] usbcore: registered new driver usbfs
[17179577.144000] usbcore: registered new driver hub
[17179577.144000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.144000] PCI: Enabling device 0000:00:13.0 (0000 -> 0002)
[17179577.144000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179577.144000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179577.148000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179577.148000] ohci_hcd 0000:00:13.0: irq 201, io mem 0x41204000
[17179577.212000] usb usb1: configuration #1 chosen from 1 choice
[17179577.212000] hub 1-0:1.0: USB hub found
[17179577.212000] hub 1-0:1.0: 4 ports detected
[17179577.320000] PCI: Enabling device 0000:00:13.1 (0000 -> 0002)
[17179577.320000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179577.320000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179577.320000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179577.320000] ohci_hcd 0000:00:13.1: irq 201, io mem 0x41205000
[17179577.384000] usb usb2: configuration #1 chosen from 1 choice
[17179577.384000] hub 2-0:1.0: USB hub found
[17179577.384000] hub 2-0:1.0: 4 ports detected
[17179577.492000] PCI: Enabling device 0000:00:13.2 (0000 -> 0002)
[17179577.492000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 201
[17179577.492000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179577.492000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179577.492000] ehci_hcd 0000:00:13.2: irq 201, io mem 0x41206000
[17179577.492000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.492000] usb usb3: configuration #1 chosen from 1 choice
[17179577.492000] hub 3-0:1.0: USB hub found
[17179577.492000] hub 3-0:1.0: 8 ports detected
[17179577.668000] Attempting manual resume
[17179577.700000] kjournald starting.  Commit interval 5 seconds
[17179577.700000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.564000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17179578.772000] usb 2-1: configuration #1 chosen from 1 choice
[17179579.080000] usb 2-3: new full speed USB device using ohci_hcd and address 3
[17179579.284000] usb 2-3: configuration #1 chosen from 1 choice
[17179579.284000] ohci_hcd 0000:00:13.0: wakeup
[17179579.668000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17179579.836000] usb 1-1: device descriptor read/64, error -110
[17179580.108000] usb 1-1: device descriptor read/64, error -110
[17179580.388000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[17179580.556000] usb 1-1: device descriptor read/64, error -110
[17179580.828000] usb 1-1: device descriptor read/64, error -110
[17179581.108000] usb 1-1: new full speed USB device using ohci_hcd and address 4
[17179581.524000] usb 1-1: device not accepting address 4, error -110
[17179581.700000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[17179582.116000] usb 1-1: device not accepting address 5, error -110
[17179586.260000] input: PC Speaker as /class/input/input1
[17179586.308000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.312000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.800000] parport: PnPBIOS parport detected.
[17179586.800000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179586.928000] 8139too Fast Ethernet driver 0.9.27
[17179586.928000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179586.928000] PCI: Setting latency timer of device 0000:02:02.0 to 64
[17179586.928000] eth0: RealTek RTL8139 at 0xd78b2000, 00:16:76:5d:ce:31, IRQ 169
[17179586.928000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179586.932000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179586.988000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.000000] Linux video capture interface: v1.00
[17179587.020000] eth0: link down
[17179587.092000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[17179587.116000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179587.236000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179587.268000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0100
[17179587.268000] usbcore: registered new driver usblp
[17179587.268000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179587.288000] usbcore: registered new driver libusual
[17179587.448000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 193
[17179587.644000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179587.732000] Initializing USB Mass Storage driver...
[17179587.740000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179587.740000] usbcore: registered new driver usb-storage
[17179587.740000] USB Mass Storage support registered.
[17179587.740000] usb-storage: device found at 3
[17179587.740000] usb-storage: waiting for device to settle before scanning
[17179587.916000] PCI: Setting latency timer of device 0000:02:04.0 to 64
[17179588.096000] ts: Compaq touchscreen protocol output
[17179588.140000] NET: Registered protocol family 17
[17179588.240000] cx2388x v4l2 driver version 0.0.5 loaded
[17179588.348000] ttySHSF0 at I/O 0x1100 (irq = 209) is a Conexant HSF softmodem (PCI-14f1:2f20-14f1:2000)
[17179588.348000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179588.348000] CORE cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[17179588.348000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179588.560000] cx88[0]/0: found at 0000:02:03.0, rev: 5, irq: 193, latency: 0, mmio: 0x40000000
[17179588.560000] PCI: Setting latency timer of device 0000:02:03.0 to 64
[17179588.596000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179588.596000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179588.596000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179588.644000] tda9887 0-0043: chip found @ 0x86 (cx88[0])
[17179588.652000] cx88[0]/0: registered device video0 [v4l2]
[17179588.652000] cx88[0]/0: registered device vbi0
[17179588.760000] lp0: using parport0 (interrupt-driven).
[17179588.792000] [fglrx] Maximum main memory to use for locked dma buffers: 299 MBytes.
[17179588.792000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179588.844000] Adding 1076312k swap on /dev/disk/by-uuid/c1dadd8c-2246-4ccb-b671-83b4005ea3bd.  Priority:-1 extents:1 across:1076312k
[17179588.892000] EXT3 FS on hdb2, internal journal
[17179589.100000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179589.132000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179589.132000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179589.132000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17179589.140000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179589.140000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179589.140000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.
[17179592.744000] usb-storage: device scan complete
[17179592.748000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[17179592.748000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179592.756000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[17179592.756000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179592.760000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[17179592.760000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179592.768000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[17179592.768000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179592.824000] sd 4:0:0:0: Attached scsi removable disk sda
[17179592.852000] sd 4:0:0:1: Attached scsi removable disk sdb
[17179592.884000] sd 4:0:0:2: Attached scsi removable disk sdc
[17179592.912000] sd 4:0:0:3: Attached scsi removable disk sdd
[17179592.936000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17179592.936000] sd 4:0:0:1: Attached scsi generic sg1 type 0
[17179592.936000] sd 4:0:0:2: Attached scsi generic sg2 type 0
[17179592.936000] sd 4:0:0:3: Attached scsi generic sg3 type 0
[17179594.628000] ACPI: Power Button (FF) [PWRF]
[17179594.628000] ACPI: Power Button (CM) [PWRB]
[17179594.732000] ibm_acpi: ec object not found
[17179594.756000] pcc_acpi: loading...
[17179596.836000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179597.464000] [fglrx] total      GART = 134217728
[17179597.464000] [fglrx] free       GART = 118226944
[17179597.464000] [fglrx] max single GART = 118226944
[17179597.464000] [fglrx] total      LFB  = 128004096
[17179597.464000] [fglrx] free       LFB  = 120041472
[17179597.464000] [fglrx] max single LFB  = 120041472
[17179597.464000] [fglrx] total      Inv  = 0
[17179597.464000] [fglrx] free       Inv  = 0
[17179597.464000] [fglrx] max single Inv  = 0
[17179597.464000] [fglrx] total      TIM  = 0
[17179598.560000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179598.560000] apm: overridden by ACPI.
[17179601.044000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179602.500000] NET: Registered protocol family 10
[17179602.500000] lo: Disabled Privacy Extensions
[17179602.500000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179602.500000] IPv6 over IPv4 tunneling driver
[17179602.560000] Bluetooth: Core ver 2.8
[17179602.560000] NET: Registered protocol family 31
[17179602.560000] Bluetooth: HCI device and connection manager initialized
[17179602.560000] Bluetooth: HCI socket layer initialized
[17179602.580000] Bluetooth: L2CAP ver 2.8
[17179602.580000] Bluetooth: L2CAP socket layer initialized
[17179602.612000] Bluetooth: RFCOMM socket layer initialized
[17179602.612000] Bluetooth: RFCOMM TTY layer initialized
[17179602.612000] Bluetooth: RFCOMM ver 1.7
[17179743.284000] CSLIP: code copyright 1989 Regents of the University of California
[17179743.288000] PPP generic driver version 2.4.2
[17179746.588000] PPP BSD Compression module registered
[17179746.628000] PPP Deflate Compression module registered
[17179941.804000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179941.804000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179941.804000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17179941.812000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179941.812000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179941.812000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.
[17180275.316000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180275.316000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180275.316000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17180275.324000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180275.324000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180275.324000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.

Any help would be appreciated. Thanks.

---

### Post by taurus on 2007-01-21
Your /dev/hdb1 is an extended partition so you can't mount it.  Your ntfs is actually on /dev/hdb5.  So, what does your /etc/fstab look like anyway?

---

### Post by MasterColdSoul on 2007-01-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=96a1f68a-29c9-4852-bd06-4911f66defc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=c1dadd8c-2246-4ccb-b671-83b4005ea3bd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5  /media/hdb5  ntfs  defaults,umask=0222  0  0

I removed the /dev/hdb1, saved and typed sudo mount -a to re-mount and got this error:
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail:
[17179941.812000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.
[17180275.316000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180275.316000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180275.316000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17180275.324000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180275.324000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180275.324000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.
[17186917.668000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17186917.668000] NTFS-fs error (device hdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17186917.668000] NTFS-fs error (device hdb5): ntfs_fill_super(): Not an NTFS volume.

---

### Post by taurus on 2007-01-21
Try to replace the entry for ntfs in /etc/fstab with this and see what happens.

```
/dev/hdb5   /media/hdb5   ntfs   nls=utf8,umask=0222   0   0
```

p.s.  Is there anything on /dev/hdb5 at all?

---

### Post by MasterColdSoul on 2007-01-21
fstab of:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=96a1f68a-29c9-4852-bd06-4911f66defc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=c1dadd8c-2246-4ccb-b671-83b4005ea3bd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5   /media/hdb5   ntfs   nls=utf8,umask=0222   0   0


still results in this error:
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Is there anything on the partition... yes. There is about 12 gig of mp3's, and a good 30 gigs of videos and PDF's, DOC's. I really would like to be able to access it in Ubuntu.

---

### Post by taurus on 2007-01-21
And somehow the system thinks it is not ntfs!  Looks like you do dualboot on that machine, why don't you boot into Windows and run a disk scan or defrag of that partition, /dev/hdb5.  Then, boot back into Ubuntu and see if you can mount it as ntfs filesystem this time.

---

### Post by MasterColdSoul on 2007-01-21
Thanks will try it. I hope it didn't get messed up in installing Ubuntu as I haven't been into Windows since installing it (though I did Defrag it before installing). Will be back once I get it done to post the results.

---

### Post by MasterColdSoul on 2007-01-21
Well windows says that drive isn't formated (Ubuntu is on it) so I guess I might as well as turn it into a ubuntu HD. I lost alot though, I should have backed it up. Oh well.

---

### Post by taurus on 2007-01-21
So XP doesn't even recognize /dev/hdb5 as ntfs too, eh!

You now want to format /dev/hdb5 to ext3?  If you are, boot into Ubuntu and make sure it is not mounted (shouldn't but check it anyway just in case) by looking at the output of this command.

```
df -h
```
Then, format it with

```
sudo mke2fs -j /dev/hdb5
```
Now, edit /etc/fstab and replace the old entry for /dev/hdb5 with this new one.

```
/dev/hdb5   /media/hdb5   ext3   defaults   0   1
```
Mount it.

```
sudo mount -a
df -h
```

---

### Post by MasterColdSoul on 2007-01-22
Thanks for all your help Taurus!

---

### Post by wxnker on 2007-02-11
Deleted - wrong post

---

### Post by ububaba on 2007-02-11
> **wxnker said:**
> A newbie question I guess but I've often wondered what the difference is between:

/dev/hdd1 /media/lager-2 ext3 defaults 0 1

and

/dev/hdd1 /media/lager-2 ext3 defaults 0 0

You are right, it needs a thorough explaination.#-o

---

