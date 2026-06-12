---
title: "No second CD after 7.10 install"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-11-01
Box has CDP and CDRW. After install, CDRW isn't listed in the fstab. There was no problem under 7.04.

Did a quick check with Knoppix, and it has no problem detecting both devices.

I was about to add the line from Knoppix's fstab, but I see 7.10 is now using an S form -- a drive partition will be 'sda5', rather than 'hda5'.

Checking my other slightly newer box, also a fresh install of 7.10, and it's still using H forms. Can't have things too simple, can we?

So... I guess the first question is how *should* one get a device detected by Gutsy?

---

### Post by Hospadar on 2007-11-01
S is the newer format, it denotes sata drives as being distinct from IDE drives (H format)  you could always try and take the line from knoppix and change from H to S.  
Also, if your drives are all correctly detected while using the livecd, you could always copy the lines out of the fstab from the 7.10 (or 7.4 if that works better) livecd.  Just make sure you only copy the lines you need, as copying the whole thing might make things get a little manky.

---

### Post by ofb on 2007-11-01
Alas, it's not that simple. The Ubuntu LiveCDs use a special format.


7.04 LiveCD fstab (7.04 detects 2nd CD, 7.10 does not)

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
```


7.10 LiveCD fstab 

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```


7.10 fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f79db761-d491-45fb-8151-41eb800dbf59 /               ext3   
defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=87cbc3c8-c632-4a19-a987-f3c6d0a2ec0b none            swap    sw      
       0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0
```


Knoppix fstab

```
/proc      /proc       proc   rw,nosuid,nodev,noexec 0 0
/sys       /sys        sysfs  rw,nosuid,nodev,noexec 0 0
/dev/shm   /dev/shm    tmpfs  rw,nosuid,nodev,noexec 0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /media/fd0  auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /media/cdrom  auto   user,noauto,exec,ro 0 0
/dev/hdd /media/hdd  auto   users,noauto,exec,ro 0 0
/dev/hdc /media/hdc  auto   users,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/hda1 /media/hda1 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/hda5 none swap defaults 0 0
# Added by KNOPPIX
/dev/hdb1 /media/hdb1 vfat
noauto,users,exec,umask=000,shortname=winnt,uid=knoppix,gid=knoppix 0 0
```


Second box 7.10 for comparison (only one CD device)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=9ba119d7-c767-4d47-8d54-a2e45fe08bb3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=2500e823-24dc-4a8c-8a55-2054e4d6c144 /home           ext3    defaults        0       2
# /dev/hda1
UUID=3530-1BFE  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd1
UUID=0917-16EE  /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=626a140e-b774-4695-978b-8f01d8ea984e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```


So, yeah. What to make of that? Make a wild guess with /dev/scd1? Whatever is up with the S form, it's not quite the same as the old hda,b,c,d.

And there is the uneasy little detail of why it's not just working on its own. Something isn't right.

---

### Post by ofb on 2007-11-01
Here's the dmesg. The missing CDRW is a Creative.

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
[    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131068
[    0.000000]   HighMem    131068 ->   131068
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131068
[    0.000000] On node 0 totalpages: 131068
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125981 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5A60 checksum 0
[    0.000000] ACPI: RSDP 000F5A60, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFFC000, 002C (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFFC080, 0074 (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFFC100, 2624 (r1   ASUS P3B_F        1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 130045
[    0.000000] Kernel command line: root=UUID=f79db761-d491-45fb-8151-41eb800dbf59 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 451.043 MHz processor.
[   39.944363] Console: colour VGA+ 80x25
[   39.945811] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   39.947365] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   40.025300] Memory: 507916k/524272k available (2015k kernel code, 15740k reserved, 916k data, 364k init, 0k highmem)
[   40.025346] virtual kernel memory layout:
[   40.025351]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   40.025358]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.025365]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   40.025371]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[   40.025377]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   40.025384]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   40.025390]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   40.025405] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.025554] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   40.105588] Calibrating delay using timer specific routine.. 903.11 BogoMIPS (lpj=1806222)
[   40.105696] Security Framework v1.0.0 initialized
[   40.105729] SELinux:  Disabled at boot.
[   40.105795] Mount-cache hash table entries: 512
[   40.106298] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.106345] CPU: L1 I cache: 16K, L1 D cache: 16K
[   40.106357] CPU: L2 cache: 512K
[   40.106369] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   40.106414] Compat vDSO mapped to ffffe000.
[   40.106468] Checking 'hlt' instruction... OK.
[   40.121952] SMP alternatives: switching to UP code
[   40.122592] Freeing SMP alternatives: 11k freed
[   40.123668] Early unpacking initramfs... done
[   41.628165] ACPI: Core revision 20070126
[   41.628452] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   41.632676] ACPI: setting ELCR to 0200 (from 0e20)
[   41.633194] CPU0: Intel Pentium III (Katmai) stepping 03
[   41.633218] SMP motherboard not detected.
[   41.633229] Local APIC not detected. Using dummy APIC emulation.
[   41.633436] Brought up 1 CPUs
[   41.633941] Booting paravirtualized kernel on bare hardware
[   41.634115] Time: 17:13:46  Date: 10/01/107
[   41.634221] NET: Registered protocol family 16
[   41.634636] EISA bus registered
[   41.634672] ACPI: bus type pci registered
[   41.637088] PCI: PCI BIOS revision 2.10 entry at 0xf08c0, last bus=1
[   41.637100] PCI: Using configuration type 1
[   41.637108] Setting up standard PCI resources
[   41.648987] ACPI: EC: Look up EC in DSDT
[   41.660659] ACPI: Interpreter enabled
[   41.660675] ACPI: (supports S0 S1 S4 S5)
[   41.660749] ACPI: Using PIC for interrupt routing
[   41.684392] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   41.684447] PCI: Probing PCI hardware (bus 00)
[   41.684977] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   41.684986] * this clock source is slow. Consider trying other clock sources
[   41.685055] PCI quirk: region e400-e43f claimed by PIIX4 ACPI
[   41.685069] PCI quirk: region e800-e80f claimed by PIIX4 SMB
[   41.685182] PCI: Firmware left 0000:00:0a.0 e100 interrupts enabled, disabling
[   41.685769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   41.691077] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   41.691504] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   41.691930] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   41.692355] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   41.692748] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.692796] pnp: PnP ACPI init
[   41.692865] ACPI: bus type pnp registered
[   41.708532] pnp: PnP ACPI: found 14 devices
[   41.708545] ACPI: ACPI bus type pnp unregistered
[   41.708563] PnPBIOS: Disabled by ACPI PNP
[   41.708804] PCI: Using ACPI for IRQ routing
[   41.708819] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.711857] NET: Registered protocol family 8
[   41.711868] NET: Registered protocol family 20
[   41.712153] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   41.712171] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   41.712186] pnp: 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   41.712202] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   41.712241] pnp: 00:03: ioport range 0xe400-0xe43f has been reserved
[   41.712255] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   41.713403] Time: tsc clocksource has been installed.
[   41.744086] PCI: Bridge: 0000:00:01.0
[   41.744098]   IO window: disabled.
[   41.744112]   MEM window: d5000000-d6efffff
[   41.744125]   PREFETCH window: d7f00000-e3ffffff
[   41.744190] NET: Registered protocol family 2
[   41.781615] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   41.781826] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   41.782713] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   41.783311] TCP: Hash tables configured (established 16384 bind 16384)
[   41.783324] TCP reno registered
[   41.793960] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   43.111332]  it is
[   44.674624] Freeing initrd memory: 7366k freed
[   44.675053] Simple Boot Flag at 0x3a set to 0x1
[   44.675976] audit: initializing netlink socket (disabled)
[   44.676028] audit(1193937228.192:1): initialized
[   44.688587] VFS: Disk quotas dquot_6.5.1
[   44.689009] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   44.689495] io scheduler noop registered
[   44.689508] io scheduler anticipatory registered
[   44.689518] io scheduler deadline registered
[   44.689635] io scheduler cfq registered (default)
[   44.689676] Limiting direct PCI/PCI transfers.
[   44.689742] Boot video device is 0000:01:00.0
[   44.690461] isapnp: Scanning for PnP cards...
[   45.044992] isapnp: No Plug & Play device found
[   45.211491] Real Time Clock Driver v1.12ac
[   45.211931] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.212131] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.212814] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.215359] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.216242] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.220222] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.220991] input: Macintosh mouse button emulation as /class/input/input0
[   45.221413] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   45.224414] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.224437] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.225451] mice: PS/2 mouse device common for all mice
[   45.226043] EISA: Probing bus 0 at eisa.0
[   45.226123] EISA: Detected 0 cards.
[   45.226571] TCP cubic registered
[   45.226647] NET: Registered protocol family 1
[   45.226758] Using IPI No-Shortcut mode
[   45.227341]   Magic number: 15:76:238
[   45.227428]   hash matches device ttyv8
[   45.227457]   hash matches device ttysb
[   45.229253] Freeing unused kernel memory: 364k freed
[   45.284865] input: AT Translated Set 2 keyboard as /class/input/input1
[   47.230068] AppArmor: AppArmor initialized<5>audit(1193937231.192:2):  type=1505 info="AppArmor initialized" pid=1166
[   47.275390] fuse init (API version 7.8)
[   47.307072] Failure registering capabilities with primary security module.
[   47.362778] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   47.362803] ACPI: Processor [CPU0] (supports 8 throttling states)
[   49.709423] SCSI subsystem initialized
[   49.764841] libata version 2.21 loaded.
[   49.794457] ata_piix 0000:00:04.1: version 2.11
[   49.795073] scsi0 : ata_piix
[   49.795278] scsi1 : ata_piix
[   49.795741] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001d800 irq 14
[   49.795760] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001d808 irq 15
[   49.908544] usbcore: registered new interface driver usbfs
[   49.908648] usbcore: registered new interface driver hub
[   49.908770] usbcore: registered new device driver usb
[   49.916164] USB Universal Host Controller Interface driver v3.0
[   49.966811] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[   49.976065] ata1.00: ATA-4: ST33221A, 3.11, max UDMA/33
[   49.976080] ata1.00: 6303024 sectors, multi 32: LBA 
[   49.976111] ata1.01: ATA-0: QUANTUM FIREBALL_TM2110A, A6B.2400, max MWDMA2
[   49.976125] ata1.01: 4124736 sectors, multi 16: LBA 
[   49.992044] ata1.00: configured for UDMA/33
[   50.008353] ata1.01: configured for MWDMA2
[   50.018369] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   50.018384] e100: Copyright(c) 1999-2006 Intel Corporation
[   50.328060] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   50.924015] Floppy drive(s): fd0 is 1.44M
[   50.951592] FDC 0 is a post-1991 82077
[   10.984000] Marking TSC unstable due to: possible TSC halt in C2.
[   10.988000] Time: acpi_pm clocksource has been installed.
[   11.132000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   11.132000] ata2.01: limiting speed to UDMA7:PIO5
[   11.956000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   12.772000] ata2.00: ATAPI: ASUS    CD-S520/A, 1.9K, max UDMA/33
[   12.928000] ata2.00: configured for UDMA/33
[   12.928000] scsi 0:0:0:0: Direct-Access     ATA      ST33221A         3.11 PQ: 0 ANSI: 5
[   12.932000] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A6B. PQ: 0 ANSI: 5
[   12.932000] scsi 1:0:0:0: CD-ROM            ASUS     CD-S520/A        1.9K PQ: 0 ANSI: 5
[   12.936000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   12.936000] PCI: setting IRQ 9 as level-triggered
[   12.936000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   12.936000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   12.936000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   12.936000] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000d400
[   12.940000] usb usb1: configuration #1 chosen from 1 choice
[   12.940000] hub 1-0:1.0: USB hub found
[   12.940000] hub 1-0:1.0: 2 ports detected
[   13.040000] sd 0:0:0:0: [sda] 6303024 512-byte hardware sectors (3227 MB)
[   13.044000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   13.044000] eth0: RealTek RTL-8029 found at 0xd000, IRQ 9, 00:50:BA:CB:0E:35.
[   13.044000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   13.044000] PCI: setting IRQ 5 as level-triggered
[   13.044000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   13.072000] e100: eth1: e100_probe: addr 0xd7000000, irq 5, MAC addr 00:A0:C9:16:C0:26
[   13.080000] sd 0:0:0:0: [sda] Write Protect is off
[   13.080000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.088000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.096000] sd 0:0:0:0: [sda] 6303024 512-byte hardware sectors (3227 MB)
[   13.100000] sd 0:0:0:0: [sda] Write Protect is off
[   13.100000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.108000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.108000]  sda: sda1 sda2 < sda5 >
[   13.152000] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.152000] sd 0:0:1:0: [sdb] 4124736 512-byte hardware sectors (2112 MB)
[   13.152000] sd 0:0:1:0: [sdb] Write Protect is off
[   13.152000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   13.152000] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.152000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   13.152000] Uniform CD-ROM driver Revision: 3.20
[   13.152000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.164000] sd 0:0:1:0: [sdb] 4124736 512-byte hardware sectors (2112 MB)
[   13.164000] sd 0:0:1:0: [sdb] Write Protect is off
[   13.164000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   13.164000] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.164000]  sdb:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.188000] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   13.188000] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   13.232000]  sdb1
[   13.232000] sd 0:0:1:0: [sdb] Attached SCSI disk
[   14.408000] Attempting manual resume
[   14.408000] swsusp: Resume From Partition 8:5
[   14.408000] PM: Checking swsusp image.
[   14.436000] PM: Resume from disk failed.
[   14.584000] kjournald starting.  Commit interval 5 seconds
[   14.584000] EXT3-fs: mounted filesystem with ordered data mode.
[   35.620000] NET: Registered protocol family 17
[   37.712000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.736000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.580000] Linux agpgart interface v0.102 (c) Dave Jones
[   40.236000] agpgart: Detected an Intel 440BX Chipset.
[   40.452000] agpgart: AGP aperture is 64M @ 0xe4000000
[   40.536000] piix4_smbus 0000:00:04.3: Found 0000:00:04.3 device
[   42.776000] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xb000, speed 1217kHz
[   43.508000] input: PC Speaker as /class/input/input2
[   43.924000] nvidia: module license 'NVIDIA' taints kernel.
[   44.264000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   44.264000] PCI: setting IRQ 11 as level-triggered
[   44.264000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   44.264000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   44.408000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   44.412000] parport_pc 00:09: reported by Plug and Play ACPI
[   44.412000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   46.892000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   46.892000] PCI: setting IRQ 10 as level-triggered
[   46.892000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   48.216000] lp0: using parport0 (interrupt-driven).
[   48.364000] Adding 192740k swap on /dev/sda5.  Priority:-1 extents:1 across:192740k
[   48.772000] EXT3 FS on sda1, internal journal
[   50.076000] NET: Registered protocol family 10
[   50.076000] lo: Disabled Privacy Extensions
[   53.176000] input: Power Button (FF) as /class/input/input4
[   53.176000] ACPI: Power Button (FF) [PWRF]
[   53.216000] input: Power Button (CM) as /class/input/input5
[   53.216000] ACPI: Power Button (CM) [PWRB]
[   53.604000] No dock devices found.
[   58.744000] ppdev: user-space parallel port driver
[   59.516000] audit(1193962484.611:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4751 profile="/usr/sbin/cupsd"
[   59.656000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.656000] apm: overridden by ACPI.
[   60.116000] Failure registering capabilities with primary security module.
[   60.348000] eth0: no IPv6 routers present
[   60.580000] Bluetooth: Core ver 2.11
[   60.580000] NET: Registered protocol family 31
[   60.580000] Bluetooth: HCI device and connection manager initialized
[   60.580000] Bluetooth: HCI socket layer initialized
[   60.640000] Bluetooth: L2CAP ver 2.8
[   60.640000] Bluetooth: L2CAP socket layer initialized
[   60.780000] Bluetooth: RFCOMM socket layer initialized
[   60.780000] Bluetooth: RFCOMM TTY layer initialized
[   60.780000] Bluetooth: RFCOMM ver 1.8
[   65.224000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   65.224000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   65.224000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode


```

---

### Post by rudeboyskunk on 2007-11-01
Don't cdroms immediately follow hard drives with lettering?  So, if you have only one hard drive, it would be sda (hda under the old system).  Your first cdrom would be sdb.  Your third would be sdc.

---

### Post by ofb on 2007-11-01
That's how the h system did it but you can see from my fstab that the recognized CDP is scd0 now, rather than hdc.

And take a look at this in the dmesg output.

```
[   50.328060] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   50.924015] Floppy drive(s): fd0 is 1.44M
[   50.951592] FDC 0 is a post-1991 82077
[   10.984000] Marking TSC unstable due to: possible TSC halt in C2.
[   10.988000] Time: acpi_pm clocksource has been installed.
[   11.132000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   11.132000] ata2.01: limiting speed to UDMA7:PIO5
[   11.956000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
```

ata2.01 is the position of the missing CDRW. This is not good.

I'm doing a little googling right now and not getting very far.

---

### Post by ofb on 2007-11-02
Okay, that took too long and left me none the wiser but here's a fix.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581)
specfically, this comment
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25)

What I don't like about it is I don't know precisely why I'm doing it, or what trouble it may cause in the future. But for the moment things are fixed. Here's the dmesg,

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
[    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131068
[    0.000000]   HighMem    131068 ->   131068
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131068
[    0.000000] On node 0 totalpages: 131068
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125981 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5A60 checksum 0
[    0.000000] ACPI: RSDP 000F5A60, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFFC000, 002C (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFFC080, 0074 (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFFC100, 2624 (r1   ASUS P3B_F        1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   P3B_F    30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 130045
[    0.000000] Kernel command line: root=UUID=f79db761-d491-45fb-8151-41eb800dbf59 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 451.040 MHz processor.
[   39.302348] Console: colour VGA+ 80x25
[   39.303800] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   39.305363] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   39.383318] Memory: 508300k/524272k available (2015k kernel code, 15460k reserved, 916k data, 364k init, 0k highmem)
[   39.383364] virtual kernel memory layout:
[   39.383370]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   39.383377]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   39.383383]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   39.383390]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[   39.383396]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   39.383403]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   39.383409]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   39.383424] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   39.383574] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   39.463607] Calibrating delay using timer specific routine.. 903.11 BogoMIPS (lpj=1806235)
[   39.463716] Security Framework v1.0.0 initialized
[   39.463748] SELinux:  Disabled at boot.
[   39.463814] Mount-cache hash table entries: 512
[   39.464317] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   39.464364] CPU: L1 I cache: 16K, L1 D cache: 16K
[   39.464376] CPU: L2 cache: 512K
[   39.464388] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   39.464433] Compat vDSO mapped to ffffe000.
[   39.464487] Checking 'hlt' instruction... OK.
[   39.479972] SMP alternatives: switching to UP code
[   39.480611] Freeing SMP alternatives: 11k freed
[   39.481685] Early unpacking initramfs... done
[   40.928608] ACPI: Core revision 20070126
[   40.928895] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.933120] ACPI: setting ELCR to 0200 (from 0e20)
[   40.933645] CPU0: Intel Pentium III (Katmai) stepping 03
[   40.933669] SMP motherboard not detected.
[   40.933680] Local APIC not detected. Using dummy APIC emulation.
[   40.933862] Brought up 1 CPUs
[   40.934371] Booting paravirtualized kernel on bare hardware
[   40.934546] Time: 23:29:21  Date: 10/01/107
[   40.934653] NET: Registered protocol family 16
[   40.935052] EISA bus registered
[   40.935088] ACPI: bus type pci registered
[   40.937536] PCI: PCI BIOS revision 2.10 entry at 0xf08c0, last bus=1
[   40.937549] PCI: Using configuration type 1
[   40.937558] Setting up standard PCI resources
[   40.949481] ACPI: EC: Look up EC in DSDT
[   40.961163] ACPI: Interpreter enabled
[   40.961180] ACPI: (supports S0 S1 S4 S5)
[   40.961254] ACPI: Using PIC for interrupt routing
[   40.984899] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.984954] PCI: Probing PCI hardware (bus 00)
[   40.985483] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   40.985492] * this clock source is slow. Consider trying other clock sources
[   40.985562] PCI quirk: region e400-e43f claimed by PIIX4 ACPI
[   40.985575] PCI quirk: region e800-e80f claimed by PIIX4 SMB
[   40.985688] PCI: Firmware left 0000:00:0a.0 e100 interrupts enabled, disabling
[   40.986246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.991604] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   40.992034] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   40.992463] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   40.992890] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   40.993280] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.993328] pnp: PnP ACPI init
[   40.993369] ACPI: bus type pnp registered
[   41.009115] pnp: PnP ACPI: found 14 devices
[   41.009128] ACPI: ACPI bus type pnp unregistered
[   41.009146] PnPBIOS: Disabled by ACPI PNP
[   41.009380] PCI: Using ACPI for IRQ routing
[   41.009396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.012438] NET: Registered protocol family 8
[   41.012449] NET: Registered protocol family 20
[   41.012729] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   41.012746] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   41.012761] pnp: 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   41.012777] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   41.012817] pnp: 00:03: ioport range 0xe400-0xe43f has been reserved
[   41.012832] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   41.015430] Time: tsc clocksource has been installed.
[   41.044618] PCI: Bridge: 0000:00:01.0
[   41.044627]   IO window: disabled.
[   41.044642]   MEM window: d5000000-d6efffff
[   41.044655]   PREFETCH window: d7f00000-e3ffffff
[   41.044718] NET: Registered protocol family 2
[   41.083642] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   41.083864] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   41.084729] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   41.085327] TCP: Hash tables configured (established 16384 bind 16384)
[   41.085339] TCP reno registered
[   41.095967] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   42.365323]  it is
[   43.868966] Freeing initrd memory: 7086k freed
[   43.869394] Simple Boot Flag at 0x3a set to 0x1
[   43.870330] audit: initializing netlink socket (disabled)
[   43.870382] audit(1193959763.136:1): initialized
[   43.883107] VFS: Disk quotas dquot_6.5.1
[   43.883473] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   43.883963] io scheduler noop registered
[   43.883976] io scheduler anticipatory registered
[   43.883985] io scheduler deadline registered
[   43.884103] io scheduler cfq registered (default)
[   43.884144] Limiting direct PCI/PCI transfers.
[   43.884211] Boot video device is 0000:01:00.0
[   43.884898] isapnp: Scanning for PnP cards...
[   44.239495] isapnp: No Plug & Play device found
[   44.404678] Real Time Clock Driver v1.12ac
[   44.405112] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   44.405316] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.405881] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.408515] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.409401] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.413425] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   44.414120] input: Macintosh mouse button emulation as /class/input/input0
[   44.414541] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   44.417550] serio: i8042 KBD port at 0x60,0x64 irq 1
[   44.417574] serio: i8042 AUX port at 0x60,0x64 irq 12
[   44.418515] mice: PS/2 mouse device common for all mice
[   44.419162] EISA: Probing bus 0 at eisa.0
[   44.419244] EISA: Detected 0 cards.
[   44.419640] TCP cubic registered
[   44.419714] NET: Registered protocol family 1
[   44.419826] Using IPI No-Shortcut mode
[   44.420410]   Magic number: 15:471:503
[   44.422261] Freeing unused kernel memory: 364k freed
[   44.490880] input: AT Translated Set 2 keyboard as /class/input/input1
[   46.479539] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   46.479560] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   46.481217] Probing IDE interface ide0...
[   46.894400] hda: ST33221A, ATA DISK drive
[   47.174345] hdb: QUANTUM FIREBALL_TM2110A, ATA DISK drive
[   47.230213] Probing IDE interface ide1...
[   48.094169] hdc: ASUS CD-S520/A, ATAPI CD/DVD-ROM drive
[   48.878023] hdd: CREATIVE CD-RW RW4224E, ATAPI CD/DVD-ROM drive
[   48.933948] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   48.934053] ide1 at 0x170-0x177,0x376 on irq 15
[   48.972750] hdc: ATAPI 52X CD-ROM drive, 128kB Cache
[   48.972776] Uniform CD-ROM driver Revision: 3.20
[   48.975079] hdd: ATAPI 24X CD-ROM CD-R/RW drive, 1860kB Cache
[   49.012317] hda: max request size: 128KiB
[   49.012336] hda: 6303024 sectors (3227 MB) w/128KiB Cache, CHS=6253/16/63
[   49.012354] hda: cache flushes not supported
[   49.012476]  hda: hda1 hda2 < hda5 >
[   49.053448] hdb: max request size: 128KiB
[   49.053464] hdb: 4124736 sectors (2111 MB) w/76KiB Cache, CHS=4092/16/63
[   49.053558]  hdb: hdb1
[   49.266427] AppArmor: AppArmor initialized<5>audit(1193959768.636:2):  type=1505 info="AppArmor initialized" pid=1228
[   49.311552] fuse init (API version 7.8)
[   49.343265] Failure registering capabilities with primary security module.
[   49.404526] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   49.404550] ACPI: Processor [CPU0] (supports 8 throttling states)
[   50.915088] Attempting manual resume
[   50.915104] swsusp: Resume From Partition 3:5
[   50.915113] PM: Checking swsusp image.
[   50.951346] PM: Resume from disk failed.
[   51.160539] kjournald starting.  Commit interval 5 seconds
[   51.160605] EXT3-fs: mounted filesystem with ordered data mode.
[   11.960000] Marking TSC unstable due to: possible TSC halt in C2.
[   11.964000] Time: acpi_pm clocksource has been installed.
[   43.584000] Linux agpgart interface v0.102 (c) Dave Jones
[   44.936000] SCSI subsystem initialized
[   44.968000] agpgart: Detected an Intel 440BX Chipset.
[   44.972000] agpgart: AGP aperture is 64M @ 0xe4000000
[   45.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.032000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.208000] usbcore: registered new interface driver usbfs
[   45.208000] usbcore: registered new interface driver hub
[   45.208000] usbcore: registered new device driver usb
[   45.252000] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[   45.252000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   45.252000] PCI: setting IRQ 9 as level-triggered
[   45.252000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   45.252000] eth0: RealTek RTL-8029 found at 0xd000, IRQ 9, 00:50:BA:CB:0E:35.
[   45.300000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   45.300000] e100: Copyright(c) 1999-2006 Intel Corporation
[   45.304000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   45.304000] PCI: setting IRQ 5 as level-triggered
[   45.304000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   45.328000] e100: eth1: e100_probe: addr 0xd7000000, irq 5, MAC addr 00:A0:C9:16:C0:26
[   45.356000] piix4_smbus 0000:00:04.3: Found 0000:00:04.3 device
[   45.408000] USB Universal Host Controller Interface driver v3.0
[   45.412000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   45.412000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   45.412000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   45.412000] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000d400
[   45.412000] usb usb1: configuration #1 chosen from 1 choice
[   45.412000] hub 1-0:1.0: USB hub found
[   45.412000] hub 1-0:1.0: 2 ports detected
[   45.520000] libata version 2.21 loaded.
[   45.552000] ata_piix 0000:00:04.1: version 2.11
[   45.552000] ata_piix 0000:00:04.1: 0x1F0 IDE port busy
[   45.552000] ata_piix 0000:00:04.1: 0x170 IDE port busy
[   45.552000] ata_piix 0000:00:04.1: no available legacy port
[   48.268000] nvidia: module license 'NVIDIA' taints kernel.
[   48.640000] input: PC Speaker as /class/input/input2
[   48.684000] Floppy drive(s): fd0 is 1.44M
[   48.704000] FDC 0 is a post-1991 82077
[   48.712000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   48.716000] PCI: setting IRQ 11 as level-triggered
[   48.716000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   48.716000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   49.096000] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xb000, speed 1193kHz
[   49.572000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   49.576000] parport_pc 00:09: reported by Plug and Play ACPI
[   49.576000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   51.948000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   51.948000] PCI: setting IRQ 10 as level-triggered
[   51.948000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   52.256000] NET: Registered protocol family 17
[   53.448000] lp0: using parport0 (interrupt-driven).
[   53.784000] Adding 192740k swap on /dev/hda5.  Priority:-1 extents:1 across:192740k
[   54.412000] EXT3 FS on hda1, internal journal
[   55.664000] NET: Registered protocol family 10
[   55.664000] lo: Disabled Privacy Extensions
[   59.472000] input: Power Button (FF) as /class/input/input4
[   59.472000] ACPI: Power Button (FF) [PWRF]
[   59.524000] input: Power Button (CM) as /class/input/input5
[   59.524000] ACPI: Power Button (CM) [PWRB]
[   60.072000] No dock devices found.
[   66.040000] ppdev: user-space parallel port driver
[   66.176000] eth0: no IPv6 routers present
[   66.888000] audit(1193985026.347:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4193 profile="/usr/sbin/cupsd"
[   67.028000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   67.028000] apm: overridden by ACPI.
[   67.580000] Failure registering capabilities with primary security module.
[   68.132000] Bluetooth: Core ver 2.11
[   68.132000] NET: Registered protocol family 31
[   68.132000] Bluetooth: HCI device and connection manager initialized
[   68.132000] Bluetooth: HCI socket layer initialized
[   68.216000] Bluetooth: L2CAP ver 2.8
[   68.216000] Bluetooth: L2CAP socket layer initialized
[   68.296000] Bluetooth: RFCOMM socket layer initialized
[   68.296000] Bluetooth: RFCOMM TTY layer initialized
[   68.296000] Bluetooth: RFCOMM ver 1.8
[   74.400000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   74.400000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   74.400000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   96.292000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   98.912000] ISO 9660 Extensions: RRIP_1991A
```


Right, now I'm going to expand on that a bit for confused new users who are tempted to play along.

You need to be root to edit /etc/initramfs-tools/modules. Also you should always make a backup so you can revert changes in the event of misfortune. So,

```
sudo cp /etc/initramfs-tools/modules /etc/initramfs-tools/modulesBAK
sudo gedit /etc/initramfs-tools/modules
```

Add these lines to /etc/initramfs-tools/modules

```
# https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581
# after editing: sudo update-initramfs -u
piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod
```

I added those two comment lines so this modification will make sense should I have to fix or re-use it in the future. Okay, save that file then run that command in terminal.

```
sudo update-initramfs -u
```

It'll take a minute.

After reboot, run 'dmesg' to see if that fixed your problem. (You /did/ save a copy of your previous dmesg output for comparison, right?)

Previously my IDE devices in dmesg looked like this

```
[   49.976065] ata1.00: ATA-4: ST33221A, 3.11, max UDMA/33
[   49.976080] ata1.00: 6303024 sectors, multi 32: LBA 
[   49.976111] ata1.01: ATA-0: QUANTUM FIREBALL_TM2110A, A6B.2400, max MWDMA2
[   49.976125] ata1.01: 4124736 sectors, multi 16: LBA 
[   49.992044] ata1.00: configured for UDMA/33
[   50.008353] ata1.01: configured for MWDMA2
[   50.018369] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   50.018384] e100: Copyright(c) 1999-2006 Intel Corporation
[   50.328060] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   50.924015] Floppy drive(s): fd0 is 1.44M
[   50.951592] FDC 0 is a post-1991 82077
[   10.984000] Marking TSC unstable due to: possible TSC halt in C2.
[   10.988000] Time: acpi_pm clocksource has been installed.
[   11.132000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   11.132000] ata2.01: limiting speed to UDMA7:PIO5
[   11.956000] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[   12.772000] ata2.00: ATAPI: ASUS    CD-S520/A, 1.9K, max UDMA/33
[   12.928000] ata2.00: configured for UDMA/33
[   12.928000] scsi 0:0:0:0: Direct-Access     ATA      ST33221A         3.11 PQ: 0 ANSI: 5
[   12.932000] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A6B. PQ: 0 ANSI: 5
[   12.932000] scsi 1:0:0:0: CD-ROM            ASUS     CD-S520/A    
```

Now they look like this, which is the "old" way before the unfortunate kernel upgrade.

```
[   46.481217] Probing IDE interface ide0...
[   46.894400] hda: ST33221A, ATA DISK drive
[   47.174345] hdb: QUANTUM FIREBALL_TM2110A, ATA DISK drive
[   47.230213] Probing IDE interface ide1...
[   48.094169] hdc: ASUS CD-S520/A, ATAPI CD/DVD-ROM drive
[   48.878023] hdd: CREATIVE CD-RW RW4224E, ATAPI CD/DVD-ROM drive
[   48.933948] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   48.934053] ide1 at 0x170-0x177,0x376 on irq 15
[   48.972750] hdc: ATAPI 52X CD-ROM drive, 128kB Cache
[   48.972776] Uniform CD-ROM driver Revision: 3.20
[   48.975079] hdd: ATAPI 24X CD-ROM CD-R/RW drive, 1860kB Cache
[   49.012317] hda: max request size: 128KiB
[   49.012336] hda: 6303024 sectors (3227 MB) w/128KiB Cache, CHS=6253/16/63
[   49.012354] hda: cache flushes not supported
[   49.012476]  hda: hda1 hda2 < hda5 >
[   49.053448] hdb: max request size: 128KiB
[   49.053464] hdb: 4124736 sectors (2111 MB) w/76KiB Cache, CHS=4092/16/63
[   49.053558]  hdb: hdb1
```

So my four IDE devices (two harddrives, a CDP, a CDRW) are now identified as hda, hdb, hdc, hdd. 

Okay, almost done. Everything should work now, but you'll notice in nautilus that you have two entries for most of your devices, and half of them don't work. That's because your fstab is still full of entries like /dev/sda1 and /dev/sda5 and /dev/sdd and /dev/scd0, all of which are pointing to devices that don't exist now, because it's all been changed to "h" series names.

You don't have exactly what I have, so first open terminal and enter

```
sudo fdisk -l
```

That will tell you your real harddrive partition names. Use that reference to change the relevent entries in your fstab.

```
sudo cp /etc/fstab /etc/fstabBAK
sudo gedit /etc/fstab
```

Mostly it's just a case of changing a few "s" to "h". In my case the CDP had to be changed from scd0 to hdc, which I knew from my dmesg fragment above.

Hopefully that made some sense. I'm kinda tired right now.

STANDARD DISCLAIMER: Advice from some random guy on the net is just advice from some random guy on the net. What you do with it is always & only your responsibility. Keep your brain turned on.

Bonus Advice: always make a backup of your /etc as well as your /home. As you muck with Ubuntu you will probably do a few system-level modifications to files like 'fstab' and 'hosts' and maybe you'll blacklist a module sometime. Then someday you will do a fresh install instead of an upgrade and lose all of it. Having /etc backed up makes it so much easier to remember exactly what you did. And it's only about 80mb in a .tar.gz.

---

### Post by ofb on 2007-11-04
NOT FIXED.

While I can read with that CDRW fine, now I've got the cannot burn problem that several people have with 7.10.

Are there any threads yet that actually get the bottom of the various IDE device issues we're having? There's missing devices, burners that can't burn, and 7.10 installs that swap hda and hdb randomly between two drives on each boot up. Oh, and the inconsistency of some 7.10 installs showning **h**da style device assignments while others get **s**da assignments. (Plain old IDE, not modern SATA drives.)

---

### Post by wolframarnold on 2007-11-15
Gutsy no longer includes the 'piix' driver, and the ide-generic driver doesn't seem to support DMA.  I'm running a notebook with ICH6 chipset.  I'm at a loss for a solution after two days of browsing.  Too long.  Seriously considering going back to Feisty.

---

### Post by calenti on 2007-11-17
I have the exact inverse issue of the inital post - my hd* have been remapped to sd*.

Before:

    CPU: eMachines 366 Celeron w/320 MB running Feisty Server 7.04
    
    Volumes:
            on IDE bus:
             hda - 40 GB Maxtor w/ everything but home
             hdd - 17 GB Maxtor w/ home only, subversion repository, documents
            
            plugged into USB port:
              sda - 250 GB USB drive on /mnt/usbdrive, no files yet

    did the Gutsy upgrade per Ubuntu.com:

         sudo aptitude install update-manager-core
         sudo do-release-upgrade

   everything seemed to work OK but when I restarted I
   
       - had no /home - the folder is there but nothing mapped
       - startup claims I have no /dev/hdd
       - /mnt/usbdrive has a weird set of files

              abi-2.6.20-15-server     initrd.img-2.6.20-15-server      System.map-2.6.20-15-server
              abi-2.6.22-14-server     initrd.img-2.6.22-14-server      System.map-2.6.22-14-server
              config-2.6.20-15-server  initrd.img-2.6.22-14-server.bak  vmlinuz-2.6.20-15-server
              config-2.6.22-14-server  lost+found                       vmlinuz-2.6.22-14-server
              grub                     memtest86+.bin


      ran dmesg and got (this is edited for just the drive part)

[   39.567281] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   43.192596] SCSI subsystem initialized
[   43.249414] libata version 2.21 loaded.
[   43.280563] ata_piix 0000:00:07.1: version 2.11
[   43.281150] scsi0 : ata_piix
[   43.281441] scsi1 : ata_piix
[   43.281613] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   43.281637] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   43.628998] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   43.629329] usbcore: registered new interface driver usbfs
[   43.629463] usbcore: registered new interface driver hub
[   43.629630] usbcore: registered new device driver usb
[   43.637787] USB Universal Host Controller Interface driver v3.0
[   43.639512] ata1.00: ATA-5: Maxtor 94098U8, FA500S60, max UDMA/66
[   43.639538] ata1.00: 80041248 sectors, multi 16: LBA
[   43.639579] ata1.01: ATAPI: LITE-ON LTR-12101B, LS39, max MWDMA2
[   43.679475] ata1.00: configured for UDMA/33
[   43.879272] ata1.01: configured for MWDMA2
[   44.079455] ata2.01: ATA-5: Maxtor 91741U4, FA570480, max UDMA/66
[   44.079480] ata2.01: 34004880 sectors, multi 16: LBA
[   44.119453] ata2.01: configured for UDMA/33
[   44.139047] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 94098U8   FA50 PQ: 0 ANSI: 5
[   44.140856] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-12101B       LS39 PQ: 0 ANSI: 5
[   44.158950] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 91741U4   FA57 PQ: 0 ANSI: 5
[   44.159861] PCI: setting IRQ 10 as level-triggered
[   44.159882] PCI: Found IRQ 10 for device 0000:00:13.0
[   44.185122] eth0: Lite-On PNIC-II rev 37 at Port 0xe400, 00:A0:CC:33:63:49, IRQ 10.
[   44.187029] PCI: setting IRQ 9 as level-triggered
[   44.187050] PCI: Found IRQ 9 for device 0000:00:07.2
[   44.187083] PCI: Sharing IRQ 9 with 0000:00:0b.0
[   44.187131] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   44.187708] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   44.187801] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000ef80
[   44.188505] usb usb1: configuration #1 chosen from 1 choice
[   44.188693] hub 1-0:1.0: USB hub found
[   44.188739] hub 1-0:1.0: 2 ports detected
[   44.315140] Floppy drive(s): fd0 is 1.44M
[   44.442370] FDC 0 is a post-1991 82077
[   44.587786] sd 0:0:0:0: [sda] 80041248 512-byte hardware sectors (40981 MB)
[   44.587927] sd 0:0:0:0: [sda] Write Protect is off
[   44.587944] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.588053] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.588374] sd 0:0:0:0: [sda] 80041248 512-byte hardware sectors (40981 MB)
[   44.588439] sd 0:0:0:0: [sda] Write Protect is off
[   44.588456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.588560] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.588591]  sda:<6>usb 1-1: new full speed USB device using uhci_hcd and address 2
[   44.684539]  sda1 sda2 < sda5 >
[   44.725491] sd 0:0:0:0: [sda] Attached SCSI disk
[   44.729889] sd 1:0:1:0: [sdb] 34004880 512-byte hardware sectors (17410 MB)
[   44.730307] sd 1:0:1:0: [sdb] Write Protect is off
[   44.730328] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.731543] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.733527] sd 1:0:1:0: [sdb] 34004880 512-byte hardware sectors (17410 MB)
[   44.734402] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   44.734426] Uniform CD-ROM driver Revision: 3.20
[   44.734712] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   44.734764] sd 1:0:1:0: [sdb] Write Protect is off
[   44.734780] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.738834] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.738870]  sdb: sdb1
[   44.749986] sd 1:0:1:0: [sdb] Attached SCSI disk
[   44.802501] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.802617] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   44.802723] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   44.807348] usb 1-1: configuration #1 chosen from 1 choice
[   45.044950] usbcore: registered new interface driver libusual
[   45.112698] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   45.112725] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   45.128399] Initializing USB Mass Storage driver...
[   45.128856] scsi2 : SCSI emulation for USB Mass Storage devices
[   45.129217] usbcore: registered new interface driver usb-storage
[   45.129239] USB Mass Storage support registered.
[   45.129276] usb-storage: device found at 2
[   45.129288] usb-storage: waiting for device to settle before scanning
[   46.241659] Attempting manual resume
[   46.241681] swsusp: Resume From Partition 254:1
[   46.241693] PM: Checking swsusp image.
[   46.242336] PM: Resume from disk failed.
[   46.390098] kjournald starting.  Commit interval 5 seconds
[   46.390168] EXT3-fs: mounted filesystem with ordered data mode.
[   50.129321] usb-storage: device scan complete
[   50.166360] scsi 2:0:0:0: Direct-Access     WD       2500JB External  0108 PQ: 0 ANSI: 0
[   50.206192] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   50.212186] sd 2:0:0:0: [sdc] Write Protect is off
[   50.212213] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   50.212227] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   50.218367] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   50.224172] sd 2:0:0:0: [sdc] Write Protect is off
[   50.224198] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   50.224213] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   50.224522]  sdc: sdc1
[   50.231575] sd 2:0:0:0: [sdc] Attached SCSI disk
[   50.231787] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   56.255904] eth0: Autonegotiation failed, using 10baseT, link beat status 10ce.
[   58.297037] NET: Registered protocol family 10
[   58.297545] lo: Disabled Privacy Extensions
[   63.117085] Linux agpgart interface v0.102 (c) Dave Jones
[   63.176953] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   63.176995] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   64.454057] agpgart: Detected an Intel 440LX Chipset.
[   64.455240] agpgart: AGP aperture is 4M @ 0xf8400000
[   64.595815] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.608540] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   64.626986] input: PC Speaker as /class/input/input2
[   64.657540] voodoo3_smbus 0000:00:12.0: Using Banshee/Voodoo3 I2C device at d48cc000
[   67.092569] parport_pc 00:0b: reported by Plug and Play BIOS
[   67.092632] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   68.475168] eth0: no IPv6 routers present
[   69.029326] PCI: Found IRQ 9 for device 0000:00:0b.0
[   69.029364] PCI: Sharing IRQ 9 with 0000:00:07.2
[   69.265637] gameport: CS46xx Gameport is pci0000:00:0b.0/gameport0, speed 1807kHz
[   70.963058] lp0: using parport0 (interrupt-driven).
[   72.054829] EXT3 FS on dm-0, internal journal
[   73.567172] kjournald starting.  Commit interval 5 seconds
[   73.567646] EXT3 FS on sda1, internal journal
[   73.567673] EXT3-fs: mounted filesystem with ordered data mode.
[   73.832670] Adding 958456k swap on /dev/mapper/em366is-swap_1.  Priority:-1 extents:1 across:958456k

          
fdisk -l shows

Disk /dev/sda: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2181

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        4982    39768907+   5  Extended
/dev/sda5              32        4982    39768876   8e  Linux LVM

Disk /dev/sdb: 17.4 GB, 17410498560 bytes
16 heads, 63 sectors/track, 33735 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x5e5c44f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33735    17002408+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76c5df55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux


My fstab is currently

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/em366is-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=e18c47b2-d2b4-4e0c-8b95-e60984c164a2 /boot           ext3    defaults        0       2
/dev/mapper/em366is-swap_1 none            swap    sw              0       0
/dev/hdb   /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /mnt/usbdrive ext3  defaults 0 3
/dev/hdd1 /home ext3 defaults 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


So I have the reverse from you (my hdX are now sdX and my sda USB drive has been clobbered to sdc). What are my options?

I think I have to choose from (in descending order of desireablity)

1) Edit fstab to match the new report from fdisk -l and move the loader files from /mnt/usbdrive to /
2) Try and load the PIIX driver as you list and restart 
2) Clobber the install with a fresh Feisty install from CD 


Any thoughts appreciated. BTW, I did this same upgrade on Ubuntu Feisty running on a SPARC Ultra 5 without incident so I thought this would be a cakewalk. Guess not.

---

### Post by ofb on 2007-11-17
> **wolframarnold said:**
> I'm at a loss for a solution after two days of browsing.  Too long.  Seriously considering going back to Feisty.

Yeah, after a lot of hours I've pulled back and am waiting for kernel patches to filter down before having another go.

I have the luxury of multiple machines so I can work around it, plus I needed some fixes that came with 7.10, but if I had a solo problematic unit I'd probably have reverted by now. The patch *will* happen, but whether tomorrow or a few weeks is anyone's guess.

---

### Post by ofb on 2007-11-17
> **calenti said:**
> So I have the reverse from you (my hdX are now sdX and my sda USB drive has been clobbered to sdc). What are my options?

My opinion: I really would /not/ mess with workarounds on this one. This looks like something bad up in kernel-land that causes a number of IDE issues. So the workarounds are just fighting symptoms, and will likely cause others. And god knows what'll happen to your fixes when we do get the patches.

If I were in your shoes I'd be doing a fresh 7.04 install. You'll spend much less time and sleep so much better.

---

### Post by calenti on 2007-11-17
The remap worked well enough for my /home and /mnt/usbdrive to reappear correctly but I agree with you - pry time to go back to Feisty. Perils of free software.

One issue with server stuff is that so many of the webpages, etc are about Ubuntu Desktop (and forget about SPARC).

Like I said, if the SPARC upgrade hadn't gone so well I would have been more suspicious but that's all SCSI. Should have known.

I'm just glad I parted out /home. That's a big time saver here, I can clobber / and reinstall without having to mess with trying to take a backup from a fubared system.

---

### Post by calenti on 2007-11-17
> **ofb said:**
> My opinion: I really would /not/ mess with workarounds on this one. This looks like something bad up in kernel-land that causes a number of IDE issues. So the workarounds are just fighting symptoms, and will likely cause others. And god knows what'll happen to your fixes when we do get the patches.

If I were in your shoes I'd be doing a fresh 7.04 install. You'll spend much less time and sleep so much better.

BTW, I appreciate the feedback - thanks. Forums like this are a big part of promoting Ubuntu (which is a fantastic product, though I'm a little miffed about this issue).

---

### Post by ofb on 2007-11-17
> **calenti said:**
> Perils of free software.

Oh I did laugh when I read that.

Looking back on 29 years of commerical software use, this really doesn't hold a candle to some of crap I've dealt with. It's unfortunate, it's frustrating, and I don't doubt for a minute the developers are just as disappointed and are working on it. And quite unlike the commercial world there will be no managerial delay blocking the fixes.

I feel pretty bad for the devs, actually. It's hard to find major problems right after a big release push. Really everyone needs a week off right then and just minor troubles to come back to.

---

### Post by calenti on 2007-11-17
Churlish comment on my part - sentiment was it's so easy to install one can forget that it's still an application with all of the risks, etc.

If Ubuntu was a commercial platform, these forum articles would be a series of unanswered posts on a corporate support site, backed by 100s of calls to a "help desk" consisting of outsourced non-native English speakers trying to search those same forums and reading FAQs with insights like "check your machine for viruses".

---

