---
title: "HD problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-05
I am completely new to Linux -- I am trying to install Ubuntu onto my new system.
I have tried to install 6.10 and I get to the point where it sets up the partitions and it seems not to recognize my harddrive, and I have no clue why.  

If anyone can tell me what I am doing wrong, or what I have previously done wrong.

---

### Post by taurus on 2007-03-05
Would be nice to know the spec of your machine especially your harddrive?  Is it a PATA, SATA, Raid, etc.?

---

### Post by jrandolph on 2007-03-05
Sorry -- I have a 250gb sata hd  with amd64 dual core processor

---

### Post by taurus on 2007-03-05
From the LiveCD, what's the output of this command from a terminal (before you click the install icon)?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jrandolph on 2007-03-05
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by taurus on 2007-03-05
```
sudo fdisk -l
```
That would be lower case letter l as in larry.

---

### Post by jrandolph on 2007-03-05
I copied and pasted what you wrote and I got nothing back

---

### Post by taurus on 2007-03-05
What's the output of this then?

```
dmesg
```

---

### Post by jrandolph on 2007-03-05
[    0.000000] Bootdata ok (command line is BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- acpi=off)
[    0.000000] Linux version 2.6.17-10-generic (root@crested) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 15:34:39 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007fee0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] On node 0 totalpages: 515387
[    0.000000]   DMA zone: 2591 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 15:11 APIC version 17
[    0.000000] Processor #1 15:11 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ a020000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- acpi=off
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 1.193182 MHz WALL PIT GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2010.312 MHz processor.
[   38.319293] Console: colour VGA+ 80x25
[   38.320113] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   38.321358] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   38.337441] Memory: 2052040k/2096000k available (2129k kernel code, 43572k reserved, 1424k data, 188k init)
[   38.416461] Calibrating delay using timer specific routine.. 4024.79 BogoMIPS (lpj=8049596)
[   38.416512] Security Framework v1.0.0 initialized
[   38.416518] SELinux:  Disabled at boot.
[   38.416538] Mount-cache hash table entries: 256
[   38.416661] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.416664] CPU: L2 Cache: 512K (64 bytes/line)
[   38.416667] CPU 0/0(2) -> Node 0 -> Core 0
[   38.416682] SMP alternatives: switching to UP code
[   38.416882] checking if image is initramfs... it is
[   38.937268] Freeing initrd memory: 6259k freed
[   38.940019] ExtINT not setup in hardware but reported by MP table
[   38.940118] Using IO-APIC 2
[   38.980297] Using local APIC timer interrupts.
[   39.030007] result 12564466
[   39.030008] Detected 12.564 MHz APIC timer.
[   39.032259] SMP alternatives: switching to SMP code
[   39.032362] Booting processor 1/2 APIC 0x1
[   39.042335] Initializing CPU#1
[   39.119692] Calibrating delay using timer specific routine.. 4020.89 BogoMIPS (lpj=8041795)
[   39.119699] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   39.119701] CPU: L2 Cache: 512K (64 bytes/line)
[   39.119704] CPU 1/1(2) -> Node 0 -> Core 1
[   39.119777] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   39.123698] CPU 1: Syncing TSC to CPU 0.
[   39.124077] CPU 1: synchronized TSC with CPU 0 (last diff -1 cycles, maxerr 519 cycles)
[   39.124083] Brought up 2 CPUs
[   39.124111] testing NMI watchdog ... OK.
[   39.862559] migration_cost=179
[   39.862828] NET: Registered protocol family 16
[   39.862855] PCI: Using configuration type 1
[   39.863048] ACPI: Interpreter disabled.
[   39.863051] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.863059] pnp: PnP ACPI: disabled
[   39.863094] PCI: Probing PCI hardware
[   39.863097] PCI: Probing PCI hardware (bus 00)
[   39.863286] PCI: Ignoring BAR0-3 of IDE controller 0000:00:06.0
[   39.863538] PCI: Transparent bridge - 0000:00:09.0
[   39.863730] Boot video device is 0000:05:00.0
[   39.864739] PCI->APIC IRQ transform: 0000:00:01.1[A] -> IRQ 11
[   39.864742] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 3
[   39.864744] PCI->APIC IRQ transform: 0000:00:02.1[B] -> IRQ 5
[   39.864747] PCI->APIC IRQ transform: 0000:00:04.0[A] -> IRQ 11
[   39.864750] PCI->APIC IRQ transform: 0000:00:07.0[A] -> IRQ 5
[   39.864752] PCI->APIC IRQ transform: 0000:00:08.0[A] -> IRQ 11
[   39.864755] PCI->APIC IRQ transform: 0000:00:0a.0[A] -> IRQ 3
[   39.864760] PCI->APIC IRQ transform: 0000:01:07.0[A] -> IRQ 5
[   39.864763] PCI->APIC IRQ transform: 0000:05:00.0[A] -> IRQ 3
[   39.864840] PCI-DMA: Disabling IOMMU.
[   39.865025] PCI: Bridge: 0000:00:09.0
[   39.865027]   IO window: disabled.
[   39.865031]   MEM window: fdf00000-fdffffff
[   39.865033]   PREFETCH window: disabled.
[   39.865036] PCI: Bridge: 0000:00:0b.0
[   39.865037]   IO window: disabled.
[   39.865039]   MEM window: disabled.
[   39.865041]   PREFETCH window: disabled.
[   39.865044] PCI: Bridge: 0000:00:0c.0
[   39.865045]   IO window: disabled.
[   39.865048]   MEM window: disabled.
[   39.865050]   PREFETCH window: disabled.
[   39.865052] PCI: Bridge: 0000:00:0d.0
[   39.865054]   IO window: disabled.
[   39.865056]   MEM window: disabled.
[   39.865058]   PREFETCH window: disabled.
[   39.865061] PCI: Bridge: 0000:00:0e.0
[   39.865063]   IO window: a000-afff
[   39.865066]   MEM window: fde00000-fdefffff
[   39.865069]   PREFETCH window: d0000000-dfffffff
[   39.865075] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   39.865082] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   39.865088] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   39.865093] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   39.865099] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   39.865135] NET: Registered protocol family 2
[   39.903452] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   39.903803] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   39.905646] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   39.906104] TCP: Hash tables configured (established 262144 bind 65536)
[   39.906107] TCP reno registered
[   39.906471] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   39.906783] audit: initializing netlink socket (disabled)
[   39.906792] audit(1173114003.592:1): initialized
[   39.906939] VFS: Disk quotas dquot_6.5.1
[   39.906957] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   39.907004] Initializing Cryptographic API
[   39.907009] io scheduler noop registered
[   39.907017] io scheduler anticipatory registered
[   39.907025] io scheduler deadline registered
[   39.907042] io scheduler cfq registered (default)
[   39.907544] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   39.907548] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   39.907565] assign_interrupt_mode Found MSI capability
[   39.907598] Allocate Port Service[0000:00:0b.0:pcie00]
[   39.907636] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   39.907639] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   39.907655] assign_interrupt_mode Found MSI capability
[   39.907673] Allocate Port Service[0000:00:0c.0:pcie00]
[   39.907705] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   39.907708] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   39.907723] assign_interrupt_mode Found MSI capability
[   39.907742] Allocate Port Service[0000:00:0d.0:pcie00]
[   39.907777] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   39.907780] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   39.907796] assign_interrupt_mode Found MSI capability
[   39.907813] Allocate Port Service[0000:00:0e.0:pcie00]
[   39.926805] Real Time Clock Driver v1.12ac
[   39.926862] Linux agpgart interface v0.101 (c) Dave Jones
[   39.926865] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.926965] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.927333] mice: PS/2 mouse device common for all mice
[   39.927788] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[   39.927892] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   39.927895] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   39.928056] PNP: No PS/2 controller found. Probing ports directly.
[   40.454068] serio: i8042 AUX port at 0x60,0x64 irq 12
[   40.454720] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.454804] TCP bic registered
[   40.454813] NET: Registered protocol family 1
[   40.454818] NET: Registered protocol family 8
[   40.454820] NET: Registered protocol family 20
[   40.455188] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   40.455209] Freeing unused kernel memory: 188k freed
[   40.481435] input: AT Translated Set 2 keyboard as /class/input/input0
[   40.527807] vga16fb: initializing
[   40.527812] vga16fb: mapped to 0xffff8100000a0000
[   40.638859] Console: switching to colour frame buffer device 80x25
[   40.638864] fb0: VGA16 VGA frame buffer device
[   41.664369] Capability LSM initialized
[   42.078216] SCSI subsystem initialized
[   42.081613] libata version 1.20 loaded.
[   42.082658] sata_nv 0000:00:07.0: version 0.8
[   42.082832] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   42.082909] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD400 irq 5
[   42.082925] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD408 irq 5
[   42.289597] ata1: SATA link down (SStatus 0)
[   42.289599] scsi0 : sata_nv
[   42.493440] ata2: SATA link down (SStatus 0)
[   42.493443] scsi1 : sata_nv
[   42.493618] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   42.493676] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xC000 irq 11
[   42.493695] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xC008 irq 11
[   42.701285] ata3: SATA link up 1.5 Gbps (SStatus 113)
[   42.865251] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
[   42.865255] ata3: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   43.020715] irq 5: nobody cared (try booting with the "irqpoll" option)
[   43.020719] 
[   43.020719] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[   43.020730]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff802b6190>{__do_IRQ+224}
[   43.020741]        <ffffffff802737e2>{do_IRQ+66} <ffffffff80271f00>{default_idle+0}
[   43.020749]        <ffffffff80265d08>{ret_from_intr+0} <EOI> <ffffffff80269d9f>{thread_return+0}
[   43.020759]        <ffffffff80271f29>{default_idle+41} <ffffffff8024ecfe>{cpu_idle+158}
[   43.020767]        <ffffffff8060885b>{start_kernel+523} <ffffffff80608293>{_sinittext+659}
[   43.020778] handlers:
[   43.020780] [<ffffffff880891e0>] (nv_interrupt+0x0/0xb0 [sata_nv])
[   43.020788] Disabling IRQ #5
[   72.842653] ata3: qc timeout (cmd 0xef)
[   72.842655] ata3: failed to set xfermode (err_mask=0x4)
[   72.842658] scsi2 : sata_nv
[   73.046497] ata4: SATA link down (SStatus 0)
[   73.046499] scsi3 : sata_nv
[   73.047358] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   73.047372] NFORCE-CK804: chipset revision 242
[   73.047374] NFORCE-CK804: not 100% native mode: will probe irqs later
[   73.047380] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   73.047387]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   73.047395]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   73.047401] Probing IDE interface ide0...
[   73.614071] Probing IDE interface ide1...
[   74.349591] hdc: _NEC CD-RW NR-7800A, ATAPI CD/DVD-ROM drive
[   75.021328] ide1 at 0x170-0x177,0x376 on irq 15
[   75.028921] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   75.028928] Uniform CD-ROM driver Revision: 3.20
[   75.176962] Probing IDE interface ide0...
[   75.204679] usbcore: registered new driver usbfs
[   75.204701] usbcore: registered new driver hub
[   75.205493] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   75.205686] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   75.205692] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   75.205831] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   75.227704] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   75.230268] ohci_hcd 0000:00:02.0: irq 3, io mem 0xfe02f000
[   75.287003] usb usb1: configuration #1 chosen from 1 choice
[   75.287105] hub 1-0:1.0: USB hub found
[   75.287115] hub 1-0:1.0: 10 ports detected
[   75.389036] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   75.389042] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   75.389093] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   75.389125] ehci_hcd 0000:00:02.1: debug port 1
[   75.389129] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   75.389137] ehci_hcd 0000:00:02.1: irq 5, io mem 0xfeb00000
[   75.389143] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   75.389201] usb usb2: configuration #1 chosen from 1 choice
[   75.389221] hub 2-0:1.0: USB hub found
[   75.389228] hub 2-0:1.0: 10 ports detected
[   75.492835] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   75.492845] forcedeth: using HIGHDMA
[   76.012579] eth0: forcedeth.c: subsystem: 01043:812a bound to 0000:00:0a.0
[   76.100215] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   77.099406] ehci_hcd 0000:00:02.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   77.883683] ISO 9660 Extensions: Microsoft Joliet Level 3
[   77.913121] ISO 9660 Extensions: RRIP_1991A
[   77.941200] Registering unionfs 1.1.4
[   77.944770] loop: loaded (max 8 devices)
[   78.071175] squashfs: version 3.0 (2006/03/15) Phillip Lougher
[   87.635247] usb 2-2: device not accepting address 3, error -110
[   87.747159] usb 2-2: new high speed USB device using ehci_hcd and address 4
[   99.286170] usb 2-2: device not accepting address 4, error -110
[   99.402083] usb 2-2: new high speed USB device using ehci_hcd and address 5
[  109.817949] usb 2-2: device not accepting address 5, error -110
[  109.929865] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  120.345826] usb 2-2: device not accepting address 6, error -110
[  120.649568] usb 1-1: new low speed USB device using ohci_hcd and address 2
[  120.870948] usb 1-1: configuration #1 chosen from 1 choice
[  120.884096] usbcore: registered new driver hiddev
[  120.899036] input: Logitech USB RECEIVER as /class/input/input1
[  120.899129] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-1
[  120.899141] usbcore: registered new driver usbhid
[  120.899145] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  138.984365] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  139.267006] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[  139.410212] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[  139.410233] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[  139.572220] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  140.349457] PCI: Setting latency timer of device 0000:00:04.0 to 64
[  140.577919] ts: Compaq touchscreen protocol output
[  140.670411] intel8x0_measure_ac97_clock: measured 54652 usecs
[  140.670415] intel8x0: clocking to 46984
[  143.539966] NET: Registered protocol family 17
[  148.555330] NET: Registered protocol family 10
[  148.555433] lo: Disabled Privacy Extensions
[  148.555777] IPv6 over IPv4 tunneling driver
[  157.214308] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[  157.214404] powernow-k8: MP systems not supported by PSB BIOS structure
[  157.214335] powernow-k8: MP systems not supported by PSB BIOS structure
[  158.952625] eth0: no IPv6 routers present
[  166.063386] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[  166.168296] lp0: using parport0 (polling).
[  167.059329] ppdev: user-space parallel port driver
[  167.121977] [drm] Initialized drm 1.0.1 20051102
[  167.423591] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  181.998081] Bluetooth: Core ver 2.8
[  181.998086] NET: Registered protocol family 31
[  181.998088] Bluetooth: HCI device and connection manager initialized
[  181.998102] Bluetooth: HCI socket layer initialized
[  182.119257] Bluetooth: L2CAP ver 2.8
[  182.119262] Bluetooth: L2CAP socket layer initialized
[  182.307885] Bluetooth: RFCOMM socket layer initialized
[  182.307903] Bluetooth: RFCOMM TTY layer initialized
[  182.307905] Bluetooth: RFCOMM ver 1.7
[  185.424855] [drm] Setting GART location based on new memory map
[  185.425096] [drm] Loading R300 Microcode
[  185.425121] [drm] writeback test succeeded in 1 usecs

---

### Post by taurus on 2007-03-05
Have you tried using the alternate CD?  And I assume you already have XP on it then.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by jrandolph on 2007-03-05
I thought this one I am using was the alternate cd but I could be wrong

I am wanting to get rid of the XP alltogether

---

### Post by taurus on 2007-03-05
When your machine boots from the CD, does it go into Gnome first and then you have to click the install icon on the desktop to install it?

If that's the case, then you have what we call a LiveCD (desktop CD).  The alternate CD doesn't boot into Gnome desktop first.  It allows you to install Ubuntu right away.

---

### Post by jrandolph on 2007-03-05
I will try to find that and download it and try it

---

### Post by jrandolph on 2007-03-05
Is the 64 bit (AMD64) alternate install cd  the one that I want?

---

### Post by taurus on 2007-03-05
Doesn't matter if you install x86 or x86_64.  However, I would recommend you use x86 even though you have an AMD64 because more stuff is available for x86.  But either one should be fine for your machine.

---

### Post by mountielad on 2007-03-06
Hi I think I have the same problem:
Dell Inspiron 1501 laptop, AMD Sempron 3500, 60GB, Windows XP.

I want to dual boot with XP from the Live CD. I get as far as step 5 of 7. It allows me to _manually edit only_. The next step reveals I have _'No devices detected' _when I forward to the next step I cannot allocate partitions.
I defragmented my harddrive before it.

Should I try it via the alternate CD or is there another way to allow it to detect my devices and allocate my partition space?
 (plain language please, I'm a beginner in all respects. Thank you!).

---

