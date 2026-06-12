---
title: "Harddrive hooped"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-02-07
Okay, had a bad crash and afterwards cannot boot. Sometimes BIOS does not find my primary drives, sometimes it does. When it does, Ubuntu hangs soon after beginning. When it doesn't, Ubuntu doesn't get a chance to start. Instead I get a continuous "01 01 01 01..." scrolling down the screen

Did much messing around looking for hardware issues like bad caps, bad PSU, etc. Did have a PSU fail during that, but it doesn't appear to be related.

Couldn't get it to boot Ubuntu LiveCD. Have got it to boot Knoppix.

Drives:
hda1 - windows
hdb1 - /home
hdb3 - ubuntu
hdb5 - swap
hdc - CDRW
hdd1 - files

```
knoppix@Knoppix:~$ sudo mount /dev/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

knoppix@Knoppix:~$ dmesg | tail
end_request: I/O error, dev hdb, sector 8
Buffer I/O error on device hdb, logical block 1
end_request: I/O error, dev hdb, sector 16
Buffer I/O error on device hdb, logical block 2
end_request: I/O error, dev hdb, sector 24
Buffer I/O error on device hdb, logical block 3
end_request: I/O error, dev hdb, sector 0
Buffer I/O error on device hdb, logical block 0
end_request: I/O error, dev hdb, sector 65
EXT3-fs: unable to read superblock
```

Odd details:

When the BIOS does not detect the Primary drives, Knoppix boots and shows only hdb partitions are missing - hda1 is accessible.

When the BIOS does detect the Primary drives, Knoppix take a very long time to boot, then shows all partitions are available for mounting. However trying to mount any of the hdb partitions fails.

Naturally, I haven't done a backup for a couple of months, so would really like to access the bad drive for salvage. Or repair the filesystem if that's possible. I'm really not quite sure what's going on here.

---

### Post by talsemgeest on 2008-02-07
Try resetting the CMOS. I.e. remove the battery, change a jumper etc... whatever it is for your motherboard. Or try just resetting the settings...?

Hope this helps :)

---

### Post by ofb on 2008-02-07
Correct me if I'm wrong, but AFAIK you should only reset CMOS if cannot get into BIOS settings  - it's a rather extreme step. Really not something to be suggested in a beginners forum without appropriate cautions and detail. With some motherboards, like this one unfortunately, it's a real minefield of problems. Best avoided.

I can get into BIOS settings okay, and everything looks good in there. The computer works except for that drive with the superblock errors; I can run under the Knoppix LiveCD, and I can boot the Windows drive.


EDIT: I've just found the Explore2fs utility for reading ext3 under Windows, and I'm able to access the bum drive with it, so at least the salvage operation is underway.

This only deepens the mystery of what's wrong with the drive though.

---

### Post by ofb on 2008-02-07
This morning I let Ubuntu boot to see if having a cold drive would help. Kept an eye on it over my shoulder while fixing wakefulness.

It did the usual hang with just a terminal cursor in the upper left. A while later it showed a TTY logon with some complaints about UID. Meant to write that down once I had coffee ready. By the time I had coffee it had actually booted the full desktop.

Poked around a bit. Incredibly slow for anything that required drive access. No interesting noises.

Rebooted (took a while) into Win to continue the salvage operation.

For the moment I'm presuming an unusual drive failure. I'm used to drive failures being noisy, and/or complete.

Anyone have other ideas?

---

### Post by talsemgeest on 2008-02-07
Just a check: Have you checked the drive for errors?

---

### Post by Herman on 2008-02-08
[Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").
If your hard disk in question supports S.M.A.R.T. smartmontools might be able to provide some answers for you.
Regards, Herman :)

---

### Post by ofb on 2008-02-08
I'm not having a good time with this.

After getting the files off hdb with Windows, I disconnected the drive and installed Ubuntu to hda, which had been Windows.

Sometime during one of the update reboots I ended up with a maintenance terminal and a message to manually fsck the system -- options like '-a' to accept defaults not allowed. Had results like the following,

```
ubuntu@ubuntu:~$ sudo fsck /dev/hda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/hda3 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 950311 (Attempt to read block from filesystem resulted
in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 950312 (Attempt to read block from filesystem resulted
in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 950313 (Attempt to read block from filesystem resulted
in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 950314 (Attempt to read block from filesystem resulted
in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes
```

And so on. (hda3 is /home, for what it's worth.)

After an hour of hitting Yes, I decided to start over.

I fdisked and formatted the drive with DOS, then proceeded with Ubuntu install. And here I am again... During the update reboot Ubuntu hung after logon, making the same buzz-buzz noise it makes for each of the above errors, about 70 times. Gnome loaded slowly during this, with errors. One, Gnome Setting Daemon timed out (so my personal settings weren't loaded), and another about 'Volume Control has quit unexpectedly'.

Here's dmesg,

```
o@redfish:~$ sudo dmesg
[sudo] password for o:
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000027fec000 (usable)
[    0.000000]  BIOS-e820: 0000000027fec000 - 0000000027fef000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000027fef000 - 0000000027fff000 (reserved)
[    0.000000]  BIOS-e820: 0000000027fff000 - 0000000028000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 639MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 163820) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   163820
[    0.000000]   HighMem    163820 ->   163820
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   163820
[    0.000000] On node 0 totalpages: 163820
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1247 pages used for memmap
[    0.000000]   Normal zone: 158477 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6A70 checksum 0
[    0.000000] ACPI: RSDP 000F6A70, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 27FEC000, 002C (r1 ASUS   A7V-133  30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 27FEC080, 0074 (r1 ASUS   A7V-133  30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 27FEC100, 2CE1 (r1   ASUS A7V-133      1000 MSFT  100000B)
[    0.000000] ACPI: FACS 27FFF000, 0040
[    0.000000] ACPI: BOOT 27FEC040, 0028 (r1 ASUS   A7V-133  30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 28000000:d7ff0000)
[    0.000000] Built 1 zonelists.  Total pages: 162541
[    0.000000] Kernel command line: root=UUID=e9d407bd-812b-4b0f-b792-edbebd5b7e17 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0150e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 958.607 MHz processor.
[   25.481584] Console: colour VGA+ 80x25
[   25.483073] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.485458] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.528601] Memory: 637836k/655280k available (2015k kernel code, 16856k reserved, 916k data, 364k init, 0k highmem)
[   25.528625] virtual kernel memory layout:
[   25.528627]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.528630]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.528633]     vmalloc : 0xe8800000 - 0xff7fe000   ( 367 MB)
[   25.528636]     lowmem  : 0xc0000000 - 0xe7fec000   ( 639 MB)
[   25.528639]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.528642]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
[   25.528645]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
[   25.528652] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.528746] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.608764] Calibrating delay using timer specific routine.. 1919.41 BogoMIPS (lpj=3838828)
[   25.608826] Security Framework v1.0.0 initialized
[   25.608840] SELinux:  Disabled at boot.
[   25.608879] Mount-cache hash table entries: 512
[   25.609158] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   25.609179] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.609185] CPU: L2 Cache: 64K (64 bytes/line)
[   25.609191] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   25.609214] Compat vDSO mapped to ffffe000.
[   25.609242] Checking 'hlt' instruction... OK.
[   25.624837] SMP alternatives: switching to UP code
[   25.625415] Freeing SMP alternatives: 11k freed
[   25.626221] Early unpacking initramfs... done
[   26.297458] ACPI: Core revision 20070126
[   26.297654] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.299719] ACPI: setting ELCR to 0200 (from 0e00)
[   26.299927] CPU0: AMD Duron(tm) Processor stepping 01
[   26.299938] SMP motherboard not detected.
[   26.299944] Local APIC not detected. Using dummy APIC emulation.
[   26.300034] Brought up 1 CPUs
[   26.300319] Booting paravirtualized kernel on bare hardware
[   26.300448] Time:  8:49:50  Date: 01/08/108
[   26.300520] NET: Registered protocol family 16
[   26.300819] EISA bus registered
[   26.300846] ACPI: bus type pci registered
[   26.303576] PCI: PCI BIOS revision 2.10 entry at 0xf1180, last bus=1
[   26.303581] PCI: Using configuration type 1
[   26.303585] Setting up standard PCI resources
[   26.321823] ACPI: EC: Look up EC in DSDT
[   26.325788] ACPI: Interpreter enabled
[   26.325798] ACPI: (supports S0 S1 S4 S5)
[   26.325831] ACPI: Using PIC for interrupt routing
[   26.341604] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.341628] PCI: Probing PCI hardware (bus 00)
[   26.341798] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 89 & 1f -> 09
[   26.342070] PCI quirk: region e200-e27f claimed by vt82c686 HW-mon
[   26.342076] PCI quirk: region e800-e80f claimed by vt82c686 SMB
[   26.342520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.418664] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   26.418832] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   26.418985] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   26.419136] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   26.419383] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.419412] pnp: PnP ACPI init
[   26.419441] ACPI: bus type pnp registered
[   26.425390] pnp: PnP ACPI: found 14 devices
[   26.425399] ACPI: ACPI bus type pnp unregistered
[   26.425409] PnPBIOS: Disabled by ACPI PNP
[   26.425539] PCI: Using ACPI for IRQ routing
[   26.425546] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.435408] NET: Registered protocol family 8
[   26.435414] NET: Registered protocol family 20
[   26.435636] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   26.435644] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   26.435651] pnp: 00:00: iomem range 0x100000-0x27ffffff could not be reserved
[   26.435659] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   26.435685] pnp: 00:03: ioport range 0xe400-0xe47f has been reserved
[   26.435691] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   26.436594] Time: tsc clocksource has been installed.
[   26.466421] PCI: Bridge: 0000:00:01.0
[   26.466425]   IO window: disabled.
[   26.466433]   MEM window: d6000000-d75fffff
[   26.466440]   PREFETCH window: d7700000-e5ffffff
[   26.466465] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.466503] NET: Registered protocol family 2
[   26.504693] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.505171] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.511078] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.513653] TCP: Hash tables configured (established 131072 bind 65536)
[   26.513662] TCP reno registered
[   26.524891] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   27.103819]  it is
[   27.801944] Freeing initrd memory: 7056k freed
[   27.802186] Simple Boot Flag at 0x3a set to 0x1
[   27.802797] audit: initializing netlink socket (disabled)
[   27.802829] audit(1202460590.912:1): initialized
[   27.807029] VFS: Disk quotas dquot_6.5.1
[   27.807172] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.807393] io scheduler noop registered
[   27.807398] io scheduler anticipatory registered
[   27.807403] io scheduler deadline registered
[   27.807438] io scheduler cfq registered (default)
[   27.807470] Applying VIA southbridge workaround.
[   27.807477] PCI: VIA PCI bridge detected. Disabling DAC.
[   27.807484] PCI: Disabling Via external APIC routing
[   27.807529] Boot video device is 0000:01:00.0
[   27.807904] isapnp: Scanning for PnP cards...
[   28.162476] isapnp: No Plug & Play device found
[   28.271529] Real Time Clock Driver v1.12ac
[   28.271710] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.271883] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.272708] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.274743] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.275636] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.277639] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.278100] input: Macintosh mouse button emulation as /class/input/input0
[   28.278279] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   28.278691] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.278702] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.279096] mice: PS/2 mouse device common for all mice
[   28.279371] EISA: Probing bus 0 at eisa.0
[   28.279428] Cannot allocate resource for EISA slot 8
[   28.279433] EISA: Detected 0 cards.
[   28.279654] TCP cubic registered
[   28.279673] NET: Registered protocol family 1
[   28.279713] Using IPI No-Shortcut mode
[   28.280195]   Magic number: 12:209:826
[   28.280423]   hash matches device ptyt6
[   28.281547] Freeing unused kernel memory: 364k freed
[   28.348231] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.849881] AppArmor: AppArmor initialized<5>audit(1202460592.912:2):  type=1505 info="AppArmor initialized" pid=1174
[   29.866139] fuse init (API version 7.8)
[   29.878953] Failure registering capabilities with primary security module.
[   29.908531] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   29.908544] ACPI: Processor [CPU0] (supports 16 throttling states)
[   31.498751] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.498765] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.500433] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   31.500478] VP_IDE: chipset revision 6
[   31.500483] VP_IDE: not 100% native mode: will probe irqs later
[   31.500503] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:04.1
[   31.500518]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[   31.500540]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
[   31.500556] Probing IDE interface ide0...
[   31.539732] usbcore: registered new interface driver usbfs
[   31.539791] usbcore: registered new interface driver hub
[   31.539857] usbcore: registered new device driver usb
[   31.541943] USB Universal Host Controller Interface driver v3.0
[   31.691674] SCSI subsystem initialized
[   31.939396] hda: QUANTUM FIREBALLP KA13.6, ATA DISK drive
[   31.976447] Floppy drive(s): fd0 is 1.44M
[   32.046671] FDC 0 is a post-1991 82077
[    6.684000] Marking TSC unstable due to: possible TSC halt in C2.
[    6.696000] Time: acpi_pm clocksource has been installed.
[    7.088000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.096000] Probing IDE interface ide1...
[   17.652000] hdc: no response (status = 0x80), resetting drive
[   26.500000] hdc: LITE-ON LTR-40125S, ATAPI CD/DVD-ROM drive
[   26.780000] hdd: WDC WD800JB-00DUA3, ATA DISK drive
[   26.840000] ide1 at 0x170-0x177,0x376 on irq 15
[   26.868000] libata version 2.21 loaded.
[   26.876000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   26.876000] PCI: setting IRQ 9 as level-triggered
[   26.876000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   26.876000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   26.880000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   26.880000] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000d400
[   26.880000] usb usb1: configuration #1 chosen from 1 choice
[   26.880000] hub 1-0:1.0: USB hub found
[   26.880000] hub 1-0:1.0: 2 ports detected
[   26.896000] hda: max request size: 128KiB
[   26.932000] hda: 27067824 sectors (13858 MB) w/371KiB Cache, CHS=26853/16/63<4>hda: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   26.932000] 
[   26.932000] hda: cache flushes not supported
[   26.932000]  hda: hda1 hda2 hda3
[   26.952000] hdd: max request size: 512KiB
[   26.956000] hdd: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(33)
[   26.956000] hdd: cache flushes supported
[   26.956000]  hdd: hdd1
[   26.984000] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   26.984000] uhci_hcd 0000:00:04.3: UHCI Host Controller
[   26.984000] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[   26.984000] uhci_hcd 0000:00:04.3: irq 9, io base 0x0000d000
[   26.984000] usb usb2: configuration #1 chosen from 1 choice
[   26.988000] hub 2-0:1.0: USB hub found
[   26.988000] hub 2-0:1.0: 2 ports detected
[   27.092000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   27.140000] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.140000] Uniform CD-ROM driver Revision: 3.20
[   27.224000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   27.396000] usb 1-1: configuration #1 chosen from 1 choice
[   27.584000] Attempting manual resume
[   27.584000] swsusp: Resume From Partition 3:2
[   27.584000] PM: Checking swsusp image.
[   27.588000] PM: Resume from disk failed.
[   27.628000] EXT3-fs: INFO: recovery required on readonly filesystem.
[   27.628000] EXT3-fs: write access will be enabled during recovery.
[   27.768000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   27.948000] usb 2-1: configuration #1 chosen from 1 choice
[   28.080000] usbcore: registered new interface driver hiddev
[   28.096000] input: Microsoft Microsoft SideWinder Plug & Play Game Pad as /class/input/input2
[   28.096000] input: USB HID v1.00 Gamepad [Microsoft Microsoft SideWinder Plug & Play Game Pad] on usb-0000:00:04.3-1
[   28.096000] usbcore: registered new interface driver usbhid
[   28.096000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.784000] kjournald starting.  Commit interval 5 seconds
[   31.784000] EXT3-fs: hda1: orphan cleanup on readonly fs
[   31.784000] ext3_orphan_cleanup: deleting unreferenced inode 19587
[   31.948000] ext3_orphan_cleanup: deleting unreferenced inode 16180
[   31.960000] EXT3-fs: hda1: 2 orphan inodes deleted
[   31.960000] EXT3-fs: recovery complete.
[   31.972000] EXT3-fs: mounted filesystem with ordered data mode.
[   42.108000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   42.108000]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   42.108000]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   42.108000] 
[   42.108000] PDC20265: IDE controller at PCI slot 0000:00:11.0
[   42.108000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   42.108000] PCI: setting IRQ 10 as level-triggered
[   42.108000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   42.108000] PDC20265: chipset revision 2
[   42.108000] PDC20265: ROM enabled at 0x30040000
[   42.108000] PDC20265: 100% native mode on irq 10
[   42.108000] PDC20265: (U)DMA Burst Bit DISABLED Primary PCI Mode Secondary PCI Mode.
[   42.108000] PDC20265: FORCING BURST BIT 0x00->0x01 ACTIVE
[   42.108000]     ide2: BM-DMA at 0x8000-0x8007, BIOS settings: hde:pio, hdf:DMA
[   42.108000]     ide3: BM-DMA at 0x8008-0x800f, BIOS settings: hdg:DMA, hdh:pio
[   42.108000] Probing IDE interface ide2...
[   42.676000] Probing IDE interface ide3...
[   43.244000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   43.244000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   43.244000] 3c59x: Donald Becker and others.
[   43.244000] 0000:00:0a.0: 3Com PCI 3c900 Cyclone 10Mbps TPO at e883c000.
[   43.264000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   43.264000] 0000:00:0b.0: 3Com PCI 3c900 Cyclone 10Mbps TPO at e883e000.
[   44.668000] Linux agpgart interface v0.102 (c) Dave Jones
[   44.708000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   44.712000] agpgart: AGP aperture is 32M @ 0xe6000000
[   44.900000] parport_pc: VIA 686A/8231 detected
[   44.900000] parport_pc: probing current configuration
[   44.900000] parport_pc: Current parallel port base: 0x378
[   44.900000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   44.996000] parport_pc: VIA parallel port: io=0x378, irq=7
[   45.804000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.820000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.872000] i2c-adapter i2c-9191: sensors disabled - enable with force_addr=0xe200
[   47.072000] input: PC Speaker as /class/input/input3
[   47.136000] input: Wacom Graphire as /class/input/input4
[   47.156000] usbcore: registered new interface driver wacom
[   47.156000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   47.620000] nvidia: module license 'NVIDIA' taints kernel.
[   47.884000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   47.884000] PCI: setting IRQ 11 as level-triggered
[   47.884000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   47.884000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   48.024000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input5
[   48.040000] usbcore: registered new interface driver xpad
[   48.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   48.600000] ACPI: PCI Interrupt 0000:00:04.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   48.600000] PCI: Setting latency timer of device 0000:00:04.5 to 64
[   50.376000] lp0: using parport0 (interrupt-driven).
[   50.476000] Adding 682752k swap on /dev/hda2.  Priority:-1 extents:1 across:682752k
[   50.868000] EXT3 FS on hda1, internal journal
[  152.816000] kjournald starting.  Commit interval 5 seconds
[  152.816000] EXT3 FS on hda3, internal journal
[  152.816000] EXT3-fs: mounted filesystem with ordered data mode.
[  155.504000] No dock devices found.
[  155.616000] input: Power Button (FF) as /class/input/input6
[  155.616000] ACPI: Power Button (FF) [PWRF]
[  155.648000] input: Power Button (CM) as /class/input/input7
[  155.648000] ACPI: Power Button (CM) [PWRB]
[  156.904000] powernow: No powernow capabilities detected
[  159.888000] ppdev: user-space parallel port driver
[  160.852000] eth0:  setting half-duplex.
[  160.976000] eth1:  setting half-duplex.
[  161.428000] audit(1202460751.078:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5212 profile="/usr/sbin/cupsd"
[  161.724000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  161.728000] apm: overridden by ACPI.
[  162.544000] Failure registering capabilities with primary security module.
[  163.080000] Bluetooth: Core ver 2.11
[  163.080000] NET: Registered protocol family 31
[  163.080000] Bluetooth: HCI device and connection manager initialized
[  163.080000] Bluetooth: HCI socket layer initialized
[  163.116000] Bluetooth: L2CAP ver 2.8
[  163.116000] Bluetooth: L2CAP socket layer initialized
[  163.160000] Bluetooth: RFCOMM socket layer initialized
[  163.160000] Bluetooth: RFCOMM TTY layer initialized
[  163.160000] Bluetooth: RFCOMM ver 1.8
[  166.452000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  166.452000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  166.452000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  167.616000] NET: Registered protocol family 17
[  169.548000] NET: Registered protocol family 10
[  169.548000] lo: Disabled Privacy Extensions
[  169.548000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  180.256000] eth0: no IPv6 routers present
[  191.564000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  191.564000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669528
[  191.564000] ide: failed opcode was: unknown
[  191.564000] end_request: I/O error, dev hda, sector 25669528
[  198.348000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  198.348000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669536
[  198.348000] ide: failed opcode was: unknown
[  198.348000] end_request: I/O error, dev hda, sector 25669536
[  205.144000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  205.144000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669544
[  205.144000] ide: failed opcode was: unknown
[  205.144000] end_request: I/O error, dev hda, sector 25669544
[  212.068000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  212.068000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669552
[  212.068000] ide: failed opcode was: unknown
[  212.068000] end_request: I/O error, dev hda, sector 25669552
[  218.888000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  218.888000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669560
[  218.888000] ide: failed opcode was: unknown
[  218.888000] end_request: I/O error, dev hda, sector 25669560
[  225.684000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  225.684000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669568
[  225.684000] ide: failed opcode was: unknown
[  225.684000] end_request: I/O error, dev hda, sector 25669568
[  232.508000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  232.508000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669576
[  232.508000] ide: failed opcode was: unknown
[  232.508000] end_request: I/O error, dev hda, sector 25669576
[  239.680000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  239.680000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669582, sector=25669576
[  239.680000] ide: failed opcode was: unknown
[  239.680000] end_request: I/O error, dev hda, sector 25669576
[  248.624000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  248.624000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25669262, sector=25669256
[  248.624000] ide: failed opcode was: unknown
[  248.624000] end_request: I/O error, dev hda, sector 25669256
[  248.624000] EXT3-fs error (device hda3): ext3_find_entry: reading directory #959349 offset 0
[  279.096000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  279.096000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636128
[  279.096000] ide: failed opcode was: unknown
[  279.096000] end_request: I/O error, dev hda, sector 25636128
[  285.956000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  285.956000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636136
[  285.956000] ide: failed opcode was: unknown
[  285.956000] end_request: I/O error, dev hda, sector 25636136
[  293.012000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  293.012000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636144
[  293.012000] ide: failed opcode was: unknown
[  293.012000] end_request: I/O error, dev hda, sector 25636144
[  299.968000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  299.968000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636152
[  299.968000] ide: failed opcode was: unknown
[  299.968000] end_request: I/O error, dev hda, sector 25636152
[  306.908000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  306.908000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636160
[  306.908000] ide: failed opcode was: unknown
[  306.908000] end_request: I/O error, dev hda, sector 25636160
[  333.292000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  333.292000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636264
[  333.292000] ide: failed opcode was: unknown
[  333.292000] end_request: I/O error, dev hda, sector 25636264
[  346.144000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  346.144000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636267, sector=25636264
[  346.144000] ide: failed opcode was: unknown
[  346.144000] end_request: I/O error, dev hda, sector 25636264
[  367.152000] hda: dma_timer_expiry: dma status == 0x25
[  367.204000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  367.204000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624374, sector=25624216
[  367.204000] ide: failed opcode was: unknown
[  367.204000] end_request: I/O error, dev hda, sector 25624216
[  367.440000] Clocksource tsc unstable (delta = 9373483770 ns)
[  381.284000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  381.284000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624376, sector=25624224
[  381.284000] ide: failed opcode was: unknown
[  381.284000] end_request: I/O error, dev hda, sector 25624224
[  388.244000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  388.244000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624376, sector=25624232
[  388.244000] ide: failed opcode was: unknown
[  388.244000] end_request: I/O error, dev hda, sector 25624232
[  395.320000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  395.320000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624376, sector=25624240
[  395.320000] ide: failed opcode was: unknown
[  395.320000] end_request: I/O error, dev hda, sector 25624240
[  415.320000] hda: dma_timer_expiry: dma status == 0x24
[  457.984000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  457.984000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636264
[  457.984000] ide: failed opcode was: unknown
[  457.984000] end_request: I/O error, dev hda, sector 25636264
[  483.900000] hda: dma_timer_expiry: dma status == 0x25
[  485.640000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  485.640000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624514, sector=25624472
[  485.640000] ide: failed opcode was: unknown
[  485.640000] end_request: I/O error, dev hda, sector 25624472
[  505.640000] hda: dma_timer_expiry: dma status == 0x25
[  505.760000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  505.760000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624522, sector=25624480
[  505.760000] ide: failed opcode was: unknown
[  505.760000] end_request: I/O error, dev hda, sector 25624480
[  525.760000] hda: dma_timer_expiry: dma status == 0x25
[  527.264000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  527.264000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624535, sector=25624488
[  527.264000] ide: failed opcode was: unknown
[  527.264000] end_request: I/O error, dev hda, sector 25624488
[  534.060000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  534.060000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624535, sector=25624496
[  534.060000] ide: failed opcode was: unknown
[  534.060000] end_request: I/O error, dev hda, sector 25624496
[  541.120000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  541.120000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624535, sector=25624504
[  541.120000] ide: failed opcode was: unknown
[  541.120000] end_request: I/O error, dev hda, sector 25624504
[  561.120000] hda: dma_timer_expiry: dma status == 0x25
[  564.348000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  564.348000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624512
[  564.348000] ide: failed opcode was: unknown
[  564.348000] end_request: I/O error, dev hda, sector 25624512
[  571.272000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  571.272000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624520
[  571.272000] ide: failed opcode was: unknown
[  571.272000] end_request: I/O error, dev hda, sector 25624520
[  578.328000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  578.328000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624528
[  578.328000] ide: failed opcode was: unknown
[  578.328000] end_request: I/O error, dev hda, sector 25624528
[  585.256000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  585.256000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624536
[  585.256000] ide: failed opcode was: unknown
[  585.256000] end_request: I/O error, dev hda, sector 25624536
[  592.140000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  592.140000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624544
[  592.140000] ide: failed opcode was: unknown
[  592.140000] end_request: I/O error, dev hda, sector 25624544
[  599.184000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  599.184000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624552
[  599.184000] ide: failed opcode was: unknown
[  599.184000] end_request: I/O error, dev hda, sector 25624552
[  606.104000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  606.104000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624560
[  606.104000] ide: failed opcode was: unknown
[  606.104000] end_request: I/O error, dev hda, sector 25624560
[  612.972000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  612.972000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624568
[  612.972000] ide: failed opcode was: unknown
[  612.972000] end_request: I/O error, dev hda, sector 25624568
[  632.972000] hda: dma_timer_expiry: dma status == 0x25
[  633.032000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  633.032000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624685, sector=25624576
[  633.032000] ide: failed opcode was: unknown
[  633.032000] end_request: I/O error, dev hda, sector 25624576
[  638.304000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  638.304000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624685, sector=25624584
[  638.304000] ide: failed opcode was: unknown
[  638.304000] end_request: I/O error, dev hda, sector 25624584
[  645.356000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  645.356000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624685, sector=25624592
[  645.356000] ide: failed opcode was: unknown
[  645.356000] end_request: I/O error, dev hda, sector 25624592
[  652.148000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  652.148000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624685, sector=25624600
[  652.148000] ide: failed opcode was: unknown
[  652.148000] end_request: I/O error, dev hda, sector 25624600
[  666.724000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  666.724000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624568
[  666.724000] ide: failed opcode was: unknown
[  666.724000] end_request: I/O error, dev hda, sector 25624568
[  676.544000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  676.544000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25624570, sector=25624568
[  676.544000] ide: failed opcode was: unknown
[  676.544000] end_request: I/O error, dev hda, sector 25624568
[  689.804000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  689.804000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25627738, sector=25627736
[  689.804000] ide: failed opcode was: unknown
[  689.804000] end_request: I/O error, dev hda, sector 25627736
[  697.336000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  697.336000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25627744, sector=25627744
[  697.336000] ide: failed opcode was: unknown
[  697.336000] end_request: I/O error, dev hda, sector 25627744
[  707.128000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  707.128000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25627738, sector=25627736
[  707.128000] ide: failed opcode was: unknown
[  707.128000] end_request: I/O error, dev hda, sector 25627736
[  714.192000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  714.192000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25627738, sector=25627736
[  714.192000] ide: failed opcode was: unknown
[  714.192000] end_request: I/O error, dev hda, sector 25627736
[  742.508000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  742.508000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636264
[  742.508000] ide: failed opcode was: unknown
[  742.508000] end_request: I/O error, dev hda, sector 25636264
[  824.056000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  824.056000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25636270, sector=25636264
[  824.056000] ide: failed opcode was: unknown
[  824.056000] end_request: I/O error, dev hda, sector 25636264
```


/var/log/fsck/

```
Log of fsck -C -R -A -a 
Fri Feb  8 00:50:40 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Wrong checksum for long file name "pao_1.JPG".
  (Short name 000\0000000.\000PG may have changed without updating the long name)
  Not auto-correcting this.
/images/vehicles/automobiles/pao/pao_1.JPG
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000PG
Performing changes.
/dev/hdd1: 241059 files, 2196988/2441533 clusters
/dev/hda3: clean, 319/1056640 files, 73741/2112547 blocks
fsck died with exit status 1

Fri Feb  8 00:52:22 2008
----------------
```

---

### Post by ofb on 2008-02-08
Had to turn SMART on. Overall-health self-assessment test result: PASSED.


```

knoppix@Knoppix:~$ sudo smartctl -A /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 9
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0029   100   253   020    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   057   056   020    Pre-fail  Always       -       5410
  4 Start_Stop_Count        0x0032   094   094   008    Old_age   Always       -       3945
  5 Reallocated_Sector_Ct   0x0033   052   052   020    Pre-fail  Always       -       242
  7 Seek_Error_Rate         0x000b   100   100   023    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0012   091   091   001    Old_age   Always       -       6522
 11 Calibration_Retry_Count 0x0013   100   253   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   008    Old_age   Always       -       3633
 13 Read_Soft_Error_Rate    0x000b   100   253   023    Pre-fail  Always       -       0
199 UDMA_CRC_Error_Count    0x001a   200   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0

```


```

knoppix@Knoppix:~$ sudo smartctl -l error /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 2001 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2001 occurred at disk power-on lifetime: 6522 hours (271 days + 18 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 d1 00 00 4f c2 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 da 00 00 4f c2 e0 00      00:02:15.687  SMART RETURN STATUS
  ec 00 00 5f 00 00 e0 00      00:02:15.669  IDENTIFY DEVICE
  c8 00 40 20 00 00 e0 00      00:01:42.966  READ DMA
  c8 00 20 00 00 00 e0 00      00:01:42.952  READ DMA
  c8 00 08 90 0c 9b e0 00  49d+17:01:01.098  READ DMA

Error 2000 occurred at disk power-on lifetime: 6521 hours (271 days + 17 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d9 07 a8 be 87 e1  Error: UNC 7 sectors at LBA = 0x0187bea8 = 25673384

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a8 be 87 e1 00      00:05:59.861  READ DMA
  ca 00 00 c8 31 88 e1 00      00:05:59.851  WRITE DMA
  ca 00 00 c8 30 88 e1 00      00:05:59.840  WRITE DMA
  ca 00 00 c8 2f 88 e1 00      00:05:59.750  WRITE DMA
  ca 00 00 c8 2e 88 e1 00      00:05:59.747  WRITE DMA

Error 1999 occurred at disk power-on lifetime: 6521 hours (271 days + 17 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d9 17 a8 be 87 e1  Error: UNC 23 sectors at LBA = 0x0187bea8 = 25673384

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 18 a8 be 87 e1 00      00:05:52.705  READ DMA
  c8 00 20 a0 be 87 e1 00      00:05:43.872  READ DMA
  c8 00 28 98 be 87 e1 00      00:05:35.398  READ DMA
  c8 00 38 58 be 87 e1 00      00:05:35.379  READ DMA
  c8 00 08 50 be 87 e1 00      00:05:35.377  READ DMA

Error 1998 occurred at disk power-on lifetime: 6521 hours (271 days + 17 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d9 17 a8 be 87 e1  Error: UNC 23 sectors at LBA = 0x0187bea8 = 25673384

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 a0 be 87 e1 00      00:05:43.872  READ DMA
  c8 00 28 98 be 87 e1 00      00:05:35.398  READ DMA
  c8 00 38 58 be 87 e1 00      00:05:35.379  READ DMA
  c8 00 08 50 be 87 e1 00      00:05:35.377  READ DMA
  c8 00 08 57 be 41 e0 00      00:05:35.377  READ DMA

Error 1997 occurred at disk power-on lifetime: 6521 hours (271 days + 17 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d9 19 a6 be 87 e1  Error: UNC 25 sectors at LBA = 0x0187bea6 = 25673382

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 28 98 be 87 e1 00      00:05:35.398  READ DMA
  c8 00 38 58 be 87 e1 00      00:05:35.379  READ DMA
  c8 00 08 50 be 87 e1 00      00:05:35.377  READ DMA
  c8 00 08 57 be 41 e0 00      00:05:35.377  READ DMA
  c8 00 08 5f bf 41 e0 00      00:05:35.369  READ DMA

```

```

knoppix@Knoppix:~$ sudo smartctl -t short /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Feb  8 06:04:00 2008

Use smartctl -X to abort test.


knoppix@Knoppix:~$ sudo smartctl -l selftest /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 26881
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Vendor offline      Aborted by host               90%     26625         -


```

Note I waited 10 minutes before checking result. Previously I waited 2 minutes and got this

```

knoppix@Knoppix:~$ sudo smartctl -l selftest /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 26881
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Vendor offline      Aborted by host               90%         0         -

```

I must say this doesn't explain much to me.

---

### Post by Herman on 2008-02-08
It shows your total powered on hours as 6522 and you have had 2000 errors.
At least five errors occurred in the last hour of operation. It only shows the last five, so more than five errors may have occurred in the last hour.

You already have 242 reallocated sectors. 

I'd keep an eye on it.
Recheck it at regular intervals and look for a trend.

You left out the output from[COLOR=Black][FONT=Bitstream Vera Sans Mono] sudo smartctl -i[/FONT][/COLOR]

---

### Post by ofb on 2008-02-08
> **Herman said:**
> You left out the output from[COLOR=Black][FONT=Bitstream Vera Sans Mono] sudo smartctl -i[/FONT][/COLOR]

It didn't seem to add anything relevant. Did I miss something?

```
knoppix@Knoppix:~$ sudo smartctl -i /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     QUANTUM FIREBALLP KA13.6
Serial Number:    362908531369
Firmware Version: A42.0400
User Capacity:    13,858,725,888 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   4
ATA Standard is:  ATA/ATAPI-4 T13 1153D revision 15
Local Time is:    Fri Feb  8 16:58:08 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

I'm afraid keeping an eye on it isn't an option, since I can't seem to repair it - I can't run fsck -a, and have already spent over an hour in manual mode without getting to an end of answering Yes. I certainly can't run Ubuntu as it is now.

Also it seems very strange that the drive is showing bad sectors now (that's what this is, yes?) - shouldn't that show up earlier in the process? Note I've done a full format install twice with the same result, and the drive had been just fine under Win.

And, of course. *two* drives go south? Both on the primary IDE?

I wondering if something has gone bad on the motherboard, or perhaps the cable? This isn't presenting a clear picture to me so I'm having trouble figuring out where to look, and what to do, next.

---

### Post by jhenager on 2008-02-08
First of all, clearing the CMOS is not the same as flashing your BIOS, which can be tricky, and if something goes wrong, can leave your system in an inoperable state. Clearing the CMOS just erases the NVRAM. Flashing the BIOS rewrites your BIOS chip, which is an EEPROM (Electrically Erasable Read Only Memory) chip. So, don't be afraid to clear your CMOS when you think it will help, but in this case, I doubt it.
As far as Windows working fine with these hard disks, and Ubuntu hanging, be aware that Windows is fairly sloppy when it comes to some devices, ignoring errors and proceeding until the wheels fall off. NIX operating systems perform a much more stringent check on the hardware before continuing. As hard drive capacities have increased, I am seeing more and more HD failures. Two on the same system in a short time span would raise a flag with me. If you have one of those IDE to USB adapters (about $15-20), it would be worthwhile to check them on a known good system. Good luck.

---

### Post by ofb on 2008-02-08
Yup, CMOS reset is not BIOS flashing. But just to add a caution for people reading along, do not reset your CMOS without at least researching your particular motherboard. Some, like this one, have a few issues that did not make it into the manuals for certain board versions -- it's fairly well documented in the relevant forums now, but there's certainly more tales of woe than successes.

I don't know how common that is with the modern boards. I never ran into it with AT form factor. Reseting the CMOS on those was straightforward.

> **jhenager said:**
> it would be worthwhile to check them on a known good system. 

I can put them and the remaining power supply in what was my back-up computer. It's a little involved to do a piece by piece troubleshoot like that, so right now I'm pausing to see if I can narrow it down some first. Anyone see a useful clue in that dmesg output? I'm not well versed in that.

---

### Post by talsemgeest on 2008-02-08
I reckon doing that would be the best way to narrow it down

---

### Post by Herman on 2008-02-09
> It didn't seem to add anything relevant. Did I miss something?To my way of thinking it is most important to know what the make and model of the hardware is in the first place before the rest of the figures about it will make any sense.
I tried to look up QUANTUM FIREBALLP KA13.6 but the manufacturer doesn't list then anymore, [Page Not Found]("http://www.quantum.com/products/hdd/fireball_pluska/fireball_pluska_overview.htm").
Sometimes I am lucky and I can even find the attributes for the specific hard drive model from the manufacturer, like how many start/stop cycles or how many hours or operation the disk might be good for.  Then the smartmontolls outputs start to make more sense, although they're still only indicators.

I did find two good reviews and even some wallpaper,

[Quantum Fireball Plus KA Review]("http://www.firingsquad.com/hardware/fireballpluska/page2.asp")

[Quantum Fireball Plus KA 13.6GB UDMA/66 Hard Drive Review]("http://www.sharkyextreme.com/hardware/reviews/storage/quantum_fireball/")

[Quantum Fireball Hard Disk Wallpaper]("http://www.deskpicture.com/DPs/Technology/FireballHardDisk_3.html")

I found one not so good opinion, [Quantum Fireball Nightmare]("http://www.geek.com/forums/topic.php?id=33168&page")

I enjoy running older hardware too, I have an old PC Chips Book PC that I have managed to keep running, [herman543 - Book PC Gets Big Power Supply]("http://herman543.googlepages.com/bookpcgetsbigpowersupply2"). It's fun to have older hardware that still works, but I have newer machines for my important uses. 

Even though your old hard drive hasn't actually failed yet, it is probably about eight or nine years old. I have read that an average life expectancy for a hard drive is around four or five years, but it depends on how it's used of course. Materials do age though, even if they're not used at all.

It might be time to consider buying a new hard drive, they aren't very expensive these days, and you can still use your QUANTUM FIREBALLP KA13.6 for an easier job such as data storage and keep it going for a while longer.
Even if the problem does turn out to be something else, another hard drive is always useful.
That's my 2 cents worth anyway. :)

Regards, Herman  :)

---

### Post by ofb on 2008-02-09
Ah, I see. You wanted model to help form an opinion.

Yup, it's an old drive. I've been on the upgrade curve for a long time, so there tends to be a mixture in my machines. Until this unhappiness, that box had a modern drive for files, a slightly older drive for Ubuntu, and the old 13 for Win gaming. Second machine has a different mixture of retired drives, and I've quite lost count of how many older & smaller drives are in the closet. The lower strata includes an Osborne.

My point right now is back-to-back drive trouble on the same IDE cable makes me suspicious that this may not be a drive issue. However I'm not well versed in Linux and I'm hoping others can see something in the outputs that I'm missing.

---

### Post by talsemgeest on 2008-02-09
Perhaps it was a power surge? Sorry, I'm just clutching at straws here...

---

### Post by ofb on 2008-02-09
Yeah, me too.

Power surge is always possible but hard to confirm unless spectacular. But I've known people in old houses with instable computers that became stable after getting an UPS.

I just ran the SMART on the original Ubuntu drive, with the 13 disconnected. Everything looks like roses except fdisk -lu included "Partition table entries are not in disk order."

Which is interesting, but I haven't messed with partitions since it was installed a year ago, and I wasn't doing any unusual operations that might be tripped by that.

I'll look into this further tomorrow. It's three in the morning here.

---

### Post by ofb on 2008-02-09
Well, this is unsatisfying -- I've got my original Ubuntu back, but I've no idea what the real trouble was.

Since SMART was showing the original U drive was fine, and the 13 was troubled, I decided to try booting the original U again.

First thought was to simply remove the 13, but that would require an adventure with fstab and grub/menu.lst. 

Instead I reformatted the 13 as an empty fat32, restored my missing Grub to its MBR, and removed the 13 from fstab so it won't be mounted otherwise.

The idea of fat32 is to avoid the long seeking of an ext3's self-check. The idea of removing it from fstab is /maybe/ trouble with the 13 caused all the original problems?

I really don't see how a mounted but unused fat32 drive can muck up my Ubuntu session and BIOS like that.


EDIT: Uh-oh, the time is 8 hours fast. Date is correct. How did that change?

---

### Post by talsemgeest on 2008-02-10
Well that really takes the fun out of fixing it doesnt it?

---

### Post by ofb on 2008-02-10
Yeah, being unsolved doesn't give me the warm fuzzies, and it makes for a poor thread.

The machine has now run for several hours including a few boots, and there's been no trouble other than that incorrect time. That turned out to be timezone -- something had reset me to the first option, 'Africa/Abidjan'.

To be clear, Ubuntu is running on the same drive that gave this report back in the first post:

```

knoppix@Knoppix:~$ sudo mount /dev/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

knoppix@Knoppix:~$ dmesg | tail
end_request: I/O error, dev hdb, sector 8
Buffer I/O error on device hdb, logical block 1
end_request: I/O error, dev hdb, sector 16
Buffer I/O error on device hdb, logical block 2
end_request: I/O error, dev hdb, sector 24
Buffer I/O error on device hdb, logical block 3
end_request: I/O error, dev hdb, sector 0
Buffer I/O error on device hdb, logical block 0
end_request: I/O error, dev hdb, sector 65
EXT3-fs: unable to read superblock

```

I don't see how that just can go away, or be related to trouble with the 13, which was hda at that time.

---

### Post by talsemgeest on 2008-02-11
Well its definitely beyond me...

---

