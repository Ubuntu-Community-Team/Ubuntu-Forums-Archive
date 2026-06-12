---
title: "External USB Disk fails to Mount &quot;No Additional Sense Information&quot;"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by silentminja on 2008-03-08
I just installed the distro Xubuntu 7.10, replacing my bugged-up version of Mepis.
My external hard disk, a Western Digital 80GB USB, worked fine under Mepis.
However, when I installed Xubuntu, I noticed it did not auto detect the hard disk.

I used the following command just to see if it was even detected:
> sudo fdisk -l

Everything looked good from here:
> silentminja@silentminja-console:~$ sudo fdisk -l
[sudo] password for silentminja:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x159e159e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4773    38339091   83  Linux
/dev/sda2            4774        4865      738990    5  Extended
/dev/sda5            4774        4865      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a972f09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)


So I tried to manually mount the disk
> mount /dev/sdb1

It waits a few minutes, as if it's actually trying to mount it... then says theres nothing in /etc/fstab or /etc/mtab

Ok....  so let's see what's going on while this thing is plugged in, with the following:
> sudo tail -f /var/log/messages

I unplugged the disk, and then plugged it back in
The output was as follows:
> silentminja@silentminja-console:~$ sudo tail -f /var/log/messages
Mar  8 20:49:19 silentminja-console kernel: [ 8061.523388] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
Mar  8 20:49:19 silentminja-console kernel: [ 8061.523415] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
Mar  8 20:49:49 silentminja-console kernel: [ 8091.566762] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
Mar  8 20:49:52 silentminja-console kernel: [ 8094.045656] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
Mar  8 20:49:52 silentminja-console kernel: [ 8094.045687] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
Mar  8 20:50:22 silentminja-console kernel: [ 8124.086049] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
Mar  8 20:50:25 silentminja-console kernel: [ 8126.686839] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
Mar  8 20:50:25 silentminja-console kernel: [ 8126.686871] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
Mar  8 20:50:55 silentminja-console kernel: [ 8156.727156] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
Mar  8 21:16:32 silentminja-console -- MARK --
Mar  8 21:29:39 silentminja-console kernel: [10478.049194] usb 1-2.3: USB disconnect, address 8
Mar  8 21:29:47 silentminja-console kernel: [10486.787195] usb 1-2.3: new full speed USB device using uhci_hcd and address 9
Mar  8 21:29:47 silentminja-console kernel: [10486.902401] usb 1-2.3: configuration #1 chosen from 1 choice
Mar  8 21:29:47 silentminja-console kernel: [10486.907650] scsi6 : SCSI emulation for USB Mass Storage devices
Mar  8 21:29:52 silentminja-console kernel: [10491.944879] scsi 6:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
Mar  8 21:29:52 silentminja-console kernel: [10491.955772] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Mar  8 21:29:52 silentminja-console kernel: [10491.960773] sd 6:0:0:0: [sdb] Write Protect is off
Mar  8 21:29:52 silentminja-console kernel: [10491.965829] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Mar  8 21:29:52 silentminja-console kernel: [10491.970743] sd 6:0:0:0: [sdb] Write Protect is off
Mar  8 21:29:52 silentminja-console kernel: [10491.970794]  sdb: sdb1
Mar  8 21:29:52 silentminja-console kernel: [10491.987589] sd 6:0:0:0: [sdb] Attached SCSI disk
Mar  8 21:29:52 silentminja-console kernel: [10491.989540] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar  8 21:29:55 silentminja-console kernel: [10494.456603] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Mar  8 21:29:55 silentminja-console kernel: [10494.456633] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Mar  8 21:30:25 silentminja-console kernel: [10524.499114] usb 1-2.3: reset full speed USB device using uhci_hcd and address 9
Mar  8 21:30:27 silentminja-console kernel: [10526.715179] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Mar  8 21:30:27 silentminja-console kernel: [10526.715206] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information


No Additional Sense Information???  What does that mean.

I thought maybe it had something to do with ehci_hcd
> silentminja@silentminja-console:~$ sudo modprobe -r ehci_hcd
[sudo] password for silentminja:
silentminja@silentminja-console:~$ dmesg
[    0.000000] Linux version 2.6.22-14-rt (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 (Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000c8000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fcf0000 (usable)
[    0.000000]  BIOS-e820: 000000000fcf0000 - 000000000fcfc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fcfc000 - 000000000fd00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000fd00000 - 000000000fe80000 (usable)
[    0.000000]  BIOS-e820: 000000000fe80000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65152) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65152
[    0.000000]   HighMem     65152 ->    65152
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65152
[    0.000000] On node 0 totalpages: 65152
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0
[    0.000000]   Normal zone: 834 pages used for memmap
[    0.000000]   Normal zone: 60222 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6670 checksum 0
[    0.000000] ACPI: RSDP 000F6670, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FCF7217, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0FCFBF0A, 0074 (r1 INTEL  Whitney   6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 0FCF7247, 4CC3 (r1  INTEL  Whitney  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FCFCFC0, 0040
[    0.000000] ACPI: APIC 0FCFBF7E, 005A (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 0FCFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efb80000)
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists.  Total pages: 64262
[    0.000000] Kernel command line: root=UUID=affcc790-af6f-42e0-8419-b263fdc0b37f ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] WARNING: experimental RCU implementation.
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1096.390 MHz processor.
[   11.013500] Console: colour VGA+ 80x25
[   11.014177] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.015000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   11.045430] Memory: 245008k/260608k available (2056k kernel code, 14868k reserved, 969k data, 364k init, 0k highmem)
[   11.045453] virtual kernel memory layout:
[   11.045456]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   11.045458]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.045461]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   11.045464]     lowmem  : 0xc0000000 - 0xcfe80000   ( 254 MB)
[   11.045466]       .init : 0xc03fb000 - 0xc0456000   ( 364 kB)
[   11.045469]       .data : 0xc03023dc - 0xc03f4b44   ( 969 kB)
[   11.045472]       .text : 0xc0100000 - 0xc03023dc   (2056 kB)
[   11.045479] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.105701] Calibrating delay using timer specific routine.. 2193.61 BogoMIPS (lpj=1096809)
[   11.105802] Security Framework v1.0.0 initialized
[   11.105827] SELinux:  Disabled at boot.
[   11.105869] Mount-cache hash table entries: 512
[   11.106262] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   11.106295] CPU: L1 I cache: 16K, L1 D cache: 16K
[   11.106300] CPU: L2 cache: 128K
[   11.106309] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   11.106334] Compat vDSO mapped to ffffe000.
[   11.106376] Checking 'hlt' instruction... OK.
[   11.109956] SMP alternatives: switching to UP code
[   11.110331] Freeing SMP alternatives: 9k freed
[   11.111046] Early unpacking initramfs... done
[   11.852814] ACPI: Core revision 20070126
[   11.853089] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.874020] CPU0: Intel Celeron (Coppermine) stepping 0a
[   11.874084] Total of 1 processors activated (2193.61 BogoMIPS).
[   11.874242] ENABLING IO-APIC IRQs
[   11.874484] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.986785] Brought up 1 CPUs
[   11.987204] Booting paravirtualized kernel on bare hardware
[   11.987388] Time:  0:35:00  Date: 02/09/108
[   11.987482] NET: Registered protocol family 16
[   11.988018] EISA bus registered
[   11.988074] ACPI: bus type pci registered
[   11.989194] PCI: PCI BIOS revision 2.10 entry at 0xfd9a8, last bus=1
[   11.989201] PCI: Using configuration type 1
[   11.989206] Setting up standard PCI resources
[   11.994805] ACPI: EC: Look up EC in DSDT
[   12.001613] ACPI: Interpreter enabled
[   12.001679] ACPI: (supports S0 S1 S3 S4 S5)
[   12.001725] ACPI: Using IOAPIC for interrupt routing
[   12.015727] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.015752] PCI: Probing PCI hardware (bus 00)
[   12.016249] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   12.016262] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   12.016987] PCI: Transparent bridge - 0000:00:1e.0
[   12.017058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.017483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   12.021901] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   12.022091] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   12.022246] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   12.022399] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   12.022844] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.022883] pnp: PnP ACPI init
[   12.022914] ACPI: bus type pnp registered
[   12.058734] pnp: PnP ACPI: found 13 devices
[   12.058747] ACPI: ACPI bus type pnp unregistered
[   12.058756] PnPBIOS: Disabled by ACPI PNP
[   12.059037] PCI: Using ACPI for IRQ routing
[   12.059045] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.061645] NET: Registered protocol family 8
[   12.061652] NET: Registered protocol family 20
[   12.062071] pnp: 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[   12.062081] pnp: 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[   12.062088] pnp: 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[   12.062111] pnp: 00:02: iomem range 0x0-0x9ffff could not be reserved
[   12.062117] pnp: 00:02: iomem range 0xe0000-0xfffff could not be reserved
[   12.062123] pnp: 00:02: iomem range 0x100000-0xfffffff could not be reserved
[   12.094000] PCI: Bridge: 0000:00:1e.0
[   12.094011]   IO window: 2000-2fff
[   12.094021]   MEM window: f4100000-f41fffff
[   12.094027]   PREFETCH window: disabled.
[   12.094049] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.094122] NET: Registered protocol family 2
[   12.099684] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   12.099896] TCP established hash table entries: 8192 (order: 6, 360448 bytes)
[   12.102168] TCP bind hash table entries: 8192 (order: 6, 294912 bytes)
[   12.104206] TCP: Hash tables configured (established 8192 bind 8192)
[   12.104226] TCP reno registered
[   12.105941] checking if image is initramfs... it is
[   13.476968] Freeing initrd memory: 7073k freed
[   13.477553] Simple Boot Flag at 0x35 set to 0x1
[   13.478990] audit: initializing netlink socket (disabled)
[   13.479058] audit(1205022900.898:1): initialized
[   13.479719] VFS: Disk quotas dquot_6.5.1
[   13.479756] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.479925] io scheduler noop registered
[   13.479931] io scheduler anticipatory registered
[   13.479935] io scheduler deadline registered
[   13.479964] io scheduler cfq registered (default)
[   13.480004] Boot video device is 0000:00:01.0
[   13.481095] isapnp: Scanning for PnP cards...
[   13.837476] isapnp: No Plug & Play device found
[   14.055030] Real Time Clock Driver v1.12ac
[   14.055425] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.055654] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.059482] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.063486] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.064229] input: Macintosh mouse button emulation as /class/input/input0
[   14.064584] PNP: PS/2 Controller [PNP0f13:MSE0] at 0x0,0x0 irq 12
[   14.064592] PNP: PS/2 controller has invalid data port 0x0; using default 0x60
[   14.064598] PNP: PS/2 controller has invalid command port 0x0; using default 0x64
[   14.064604] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   14.067886] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.068199] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.068901] mice: PS/2 mouse device common for all mice
[   14.069531] EISA: Probing bus 0 at eisa.0
[   14.069551] Cannot allocate resource for EISA slot 1
[   14.069557] Cannot allocate resource for EISA slot 2
[   14.069587] EISA: Detected 0 cards.
[   14.069814] TCP cubic registered
[   14.069920] NET: Registered protocol family 1
[   14.069981] Using IPI No-Shortcut mode
[   14.070532]   Magic number: 0:681:556
[   14.070661]   hash matches device ptya2
[   14.073082] Freeing unused kernel memory: 364k freed
[   15.807525] AppArmor: AppArmor initialized<5>audit(1205022903.398:2):  type=1505 info="AppArmor initialized" pid=1068
[   15.864752] fuse init (API version 7.8)
[   15.905588] Failure registering capabilities with primary security module.
[   15.961950] ACPI: Invalid PBLK length [5]
[   19.193698] SCSI subsystem initialized
[   19.300686] Floppy drive(s): fd0 is 1.44M
[   19.306785] usbcore: registered new interface driver usbfs
[   19.309620] usbcore: registered new interface driver hub
[   19.315558] usbcore: registered new device driver usb
[   19.317846] FDC 0 is a post-1991 82077
[   19.381161] 8139too Fast Ethernet driver 0.9.28
[   19.382892] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 19 (level, low) -> IRQ 16
[   19.386314] eth0: RealTek RTL8139 at 0xd08c6000, 00:40:2b:1f:0e:78, IRQ 16
[   19.386327] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   19.388346] libata version 2.21 loaded.
[   19.394232] USB Universal Host Controller Interface driver v3.0
[   19.394450] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   19.394476] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.394485] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   19.394867] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   19.401813] uhci_hcd 0000:00:1f.2: irq 16, io base 0x00001080
[   19.404929] usb usb1: configuration #1 chosen from 1 choice
[   19.406204] hub 1-0:1.0: USB hub found
[   19.406254] hub 1-0:1.0: 2 ports detected
[   19.425774] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.534244] ata_piix 0000:00:1f.1: version 2.11
[   19.534426] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.542819] scsi0 : ata_piix
[   19.544103] scsi1 : ata_piix
[   19.544462] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000110a0 irq 14
[   19.544471] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x000110a8 irq 15
[   19.699279] ata1.00: ATA-6: ST340810A, 3.39, max UDMA/100
[   19.699291] ata1.00: 78165360 sectors, multi 16: LBA 
[   19.713861] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   19.721226] ata1.00: configured for UDMA/66
[   19.853674] usb 1-2: configuration #1 chosen from 1 choice
[   19.858600] hub 1-2:1.0: USB hub found
[   19.861456] hub 1-2:1.0: 4 ports detected
[   20.026817] ata2.00: ATAPI: SAMSUNG  CD-R/RW SW-216B, Q000, max MWDMA2
[   20.144028] usb 1-2.1: new low speed USB device using uhci_hcd and address 3
[   20.183644] ata2.00: configured for MWDMA2
[   20.184071] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        3.39 PQ: 0 ANSI: 5
[   20.187886] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-216B  Q000 PQ: 0 ANSI: 5
[   20.255524] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   20.255566] sd 0:0:0:0: [sda] Write Protect is off
[   20.255573] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.255617] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.255835] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   20.255864] sd 0:0:0:0: [sda] Write Protect is off
[   20.255870] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.255912] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.255922]  sda: sda1 sda2 <<6>usb 1-2.1: configuration #1 chosen from 1 choice
[   20.302595]  sda5 >
[   20.303485] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.309355] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   20.309373] Uniform CD-ROM driver Revision: 3.20
[   20.309541] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.394396] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.395578] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   20.459679] usb 1-2.2: new full speed USB device using uhci_hcd and address 4
[   20.565850] usb 1-2.2: configuration #1 chosen from 1 choice
[   20.744296] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[   20.885548] usb 1-2.3: configuration #1 chosen from 1 choice
[   20.892699] usbcore: registered new interface driver hiddev
[   20.892998] usbcore: registered new interface driver libusual
[   20.908541] input: G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01   as /class/input/input1
[   20.908606] input: USB HID v1.00 Keyboard [G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01  ] on usb-0000:00:1f.2-2.1
[   20.944062] input: G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01   as /class/input/input2
[   20.944188] input: USB HID v1.00 Mouse [G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01  ] on usb-0000:00:1f.2-2.1
[   20.944255] usbcore: registered new interface driver usbhid
[   20.944267] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.209808] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.209827] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.255800] Initializing USB Mass Storage driver...
[   21.261862] scsi2 : SCSI emulation for USB Mass Storage devices
[   21.265636] usbcore: registered new interface driver usb-storage
[   21.265652] USB Mass Storage support registered.
[   21.265985] usb-storage: device found at 4
[   21.265991] usb-storage: waiting for device to settle before scanning
[   21.313759] Attempting manual resume
[   21.313773] swsusp: Resume From Partition 8:5
[   21.313777] PM: Checking swsusp image.
[   21.314259] PM: Resume from disk failed.
[   21.408218] kjournald starting.  Commit interval 5 seconds
[   21.408271] EXT3-fs: mounted filesystem with ordered data mode.
[   26.262546] usb-storage: device scan complete
[   26.298427] scsi 2:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[   26.305317] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   26.310341] sd 2:0:0:0: [sdb] Write Protect is off
[   26.310361] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   26.310367] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   26.315296] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   26.320443] sd 2:0:0:0: [sdb] Write Protect is off
[   26.320455] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   26.320461] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   26.320496]  sdb: sdb1
[   26.326584] sd 2:0:0:0: [sdb] Attached SCSI disk
[   26.326722] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   32.387755] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[   32.387781] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[   36.089549] input: PC Speaker as /class/input/input3
[   36.627611] Linux agpgart interface v0.102 (c) Dave Jones
[   36.693111] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.726777] intel_rng: FWH not detected
[   36.890235] agpgart: Detected an Intel i810 Chipset.
[   36.908808] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   37.068504] agpgart: AGP aperture is 64M @ 0xf8000000
[   37.068725] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   37.069114] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.255806] iTCO_vendor_support: vendor-support=0
[   37.430930] parport_pc 00:09: reported by Plug and Play ACPI
[   37.431000] parport0: PC-style at 0x378 (0x778), irq 7<6>iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   37.446636] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x1060)
[   37.446737] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.481710] , dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.873187] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
[   38.873294] usbcore: registered new interface driver usblp
[   38.873304] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   39.865204] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   39.865264] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   40.528292] intel8x0_measure_ac97_clock: measured 50198 usecs
[   40.528307] intel8x0: clocking to 48000
[   62.429046] usb 1-2.2: reset full speed USB device using uhci_hcd and address 4
[   64.612317] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[   64.612341] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[   94.652672] usb 1-2.2: reset full speed USB device using uhci_hcd and address 4
[   96.225731] lp0: using parport0 (interrupt-driven).
[   96.378924] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   96.816250] EXT3 FS on sda1, internal journal
[   99.623878] No dock devices found.
[  100.123263] input: Power Button (FF) as /class/input/input5
[  100.126119] ACPI: Power Button (FF) [PWRF]
[  100.128106] input: Power Button (CM) as /class/input/input6
[  100.130273] ACPI: Power Button (CM) [PWRB]
[  103.693092] ppdev: user-space parallel port driver
[  104.220830] audit(1205022993.078:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4677 profile="/usr/sbin/cupsd"
[  104.392588] apm: BIOS not found.
[  105.095031] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  105.439732] Failure registering capabilities with primary security module.
[  107.639404] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  107.639429] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  110.625929] NET: Registered protocol family 17
[  113.269652] NET: Registered protocol family 10
[  113.269862] lo: Disabled Privacy Extensions
[  123.722122] eth0: no IPv6 routers present
[  137.681854] usb 1-2.2: reset full speed USB device using uhci_hcd and address 4
[  162.905245] end_request: I/O error, dev fd0, sector 0
[  162.932195] end_request: I/O error, dev fd0, sector 0
[ 1546.901404] usb 1-2.2: USB disconnect, address 4
[ 1560.241686] usb 1-2.2: new full speed USB device using uhci_hcd and address 6
[ 1560.358857] usb 1-2.2: configuration #1 chosen from 1 choice
[ 1560.364774] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1560.368431] usb-storage: device found at 6
[ 1560.368454] usb-storage: waiting for device to settle before scanning
[ 1565.364448] usb-storage: device scan complete
[ 1565.400350] scsi 3:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[ 1565.410236] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1565.415268] sd 3:0:0:0: [sdb] Write Protect is off
[ 1565.415291] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1565.415297] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1565.420232] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1565.425253] sd 3:0:0:0: [sdb] Write Protect is off
[ 1565.425274] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1565.425283] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1565.425396]  sdb: sdb1
[ 1565.433556] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 1565.433690] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1567.778262] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1567.778285] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1597.819621] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 1600.011886] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1600.011915] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1630.052235] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 3101.487411] [drm] Initialized drm 1.1.0 20060810
[ 3101.498625] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 18
[ 3101.504748] [drm] Initialized i810 1.4.0 20030605 on minor 0
[ 3101.522109] [drm] Using v1.4 init.
[ 3104.890754] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 3104.890763]  driver to use reclaim_buffers_idlelocked() instead.
[ 3104.890766]  I will go on reclaiming the buffers anyway.
[ 3107.888082] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 3107.888091]  driver to use reclaim_buffers_idlelocked() instead.
[ 3107.888094]  I will go on reclaiming the buffers anyway.
[ 3932.358102] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 3932.358132] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 3962.400449] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 3964.657638] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 3964.657668] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 3994.699012] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 4015.402073] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4015.402103] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4045.444422] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 4047.836440] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4047.836469] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4077.879788] usb 1-2.2: reset full speed USB device using uhci_hcd and address 6
[ 4143.583941] usb 1-2.3: USB disconnect, address 5
[ 4143.589364] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/usb/class/usblp.c: usblp0: removed
[ 4150.871347] usb 1-2.2: USB disconnect, address 6
[ 4164.850883] usb 1-2.3: new full speed USB device using uhci_hcd and address 7
[ 4164.965138] usb 1-2.3: configuration #1 chosen from 1 choice
[ 4164.970351] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4164.975475] usb-storage: device found at 7
[ 4164.975500] usb-storage: waiting for device to settle before scanning
[ 4169.972752] usb-storage: device scan complete
[ 4170.008629] scsi 4:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[ 4170.023761] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 4170.028636] sd 4:0:0:0: [sdb] Write Protect is off
[ 4170.028660] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4170.028666] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4170.033587] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 4170.038509] sd 4:0:0:0: [sdb] Write Protect is off
[ 4170.038535] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4170.038541] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4170.038572]  sdb: sdb1
[ 4170.046791] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 4170.046941] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 4172.847845] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4172.847875] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4202.889203] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4205.091443] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4205.091471] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4235.131795] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4237.654647] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4237.654676] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4267.695070] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4681.837207] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4681.837234] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4711.880679] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4758.546118] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4758.546150] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4788.589467] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4831.451784] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4831.451814] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4861.494134] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4863.889145] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 4863.889171] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 4893.932521] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 5574.965367] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 5574.965397] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 6112.426062] usb 1-2.3: reset full speed USB device using uhci_hcd and address 7
[ 6114.646294] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 6114.646323] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 8033.623327] usb 1-2.3: USB disconnect, address 7
[ 8053.866966] usb 1-2.3: new full speed USB device using uhci_hcd and address 8
[ 8053.982133] usb 1-2.3: configuration #1 chosen from 1 choice
[ 8053.988469] scsi5 : SCSI emulation for USB Mass Storage devices
[ 8053.993154] usb-storage: device found at 8
[ 8053.993179] usb-storage: waiting for device to settle before scanning
[ 8058.989736] usb-storage: device scan complete
[ 8059.025639] scsi 5:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[ 8059.035592] sd 5:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 8059.040557] sd 5:0:0:0: [sdb] Write Protect is off
[ 8059.040581] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 8059.040587] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 8059.053592] sd 5:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 8059.058609] sd 5:0:0:0: [sdb] Write Protect is off
[ 8059.058634] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 8059.058640] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 8059.058656]  sdb: sdb1
[ 8059.070980] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 8059.071143] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 8061.523388] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 8061.523415] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 8091.566762] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
[ 8094.045656] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 8094.045687] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 8124.086049] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
[ 8126.686839] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 8126.686871] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 8156.727156] usb 1-2.3: reset full speed USB device using uhci_hcd and address 8
[10478.049194] usb 1-2.3: USB disconnect, address 8
[10486.787195] usb 1-2.3: new full speed USB device using uhci_hcd and address 9
[10486.902401] usb 1-2.3: configuration #1 chosen from 1 choice
[10486.907650] scsi6 : SCSI emulation for USB Mass Storage devices
[10486.912425] usb-storage: device found at 9
[10486.912447] usb-storage: waiting for device to settle before scanning
[10491.909323] usb-storage: device scan complete
[10491.944879] scsi 6:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[10491.955772] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[10491.960773] sd 6:0:0:0: [sdb] Write Protect is off
[10491.960794] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[10491.960800] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10491.965829] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[10491.970743] sd 6:0:0:0: [sdb] Write Protect is off
[10491.970761] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[10491.970767] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10491.970794]  sdb: sdb1
[10491.987589] sd 6:0:0:0: [sdb] Attached SCSI disk
[10491.989540] sd 6:0:0:0: Attached scsi generic sg2 type 0
[10494.456603] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[10494.456633] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[10524.499114] usb 1-2.3: reset full speed USB device using uhci_hcd and address 9
[10526.715179] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[10526.715206] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[10556.754612] usb 1-2.3: reset full speed USB device using uhci_hcd and address 9


After hours and hours of searching forums, installing packages with sudo apt-get install blah blah... still no luck....

Any suggestions?

---

### Post by taurus on 2008-03-08
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by silentminja on 2008-03-08
I came up with the following:

> silentminja@silentminja-console:~$ sudo mkdir /media/sdb1
[sudo] password for silentminja:
silentminja@silentminja-console:~$ sudo mount -t vfat /dev/sdb1 -o umask=000
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
silentminja@silentminja-console:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.8G   32G   9% /
varrun                124M   88K  124M   1% /var/run
varlock               124M     0  124M   0% /var/lock
udev                  124M   76K  124M   1% /dev
devshm                124M     0  124M   0% /dev/shm


---

### Post by taurus on 2008-03-08
Look at my previous post over again, especially the second command to mount it.

You missed the mount point, /media/sdb1.

---

### Post by silentminja on 2008-03-08
Thanks man, works beautifully!
Stupid me for not thinking about even having a sdb1 mount point.
I thought stuff like that was suppost to be automatic upon installation.

But yea, thanks a million buddy!

---

