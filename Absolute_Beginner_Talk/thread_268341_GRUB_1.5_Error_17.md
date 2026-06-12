---
title: "GRUB 1.5 Error 17"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by AstenMarquis on 2006-09-30
Windows Experience: 20 years
Linux Experience: 1 week

System: AMD 64 X2 4200+, Winfast MOBO, 1Gb RAM, NVidia 6100
        WD 320Gb SATA - WinXP bootable 1 partition
        WD 320Gb SATA - WinXP bootable 1 partition (yes I have 2 of them)
        Maxtor 250Gb PATA on Maxtor PCI card IDE slot - NTFS 2 partitions
        Maxtor 80Gb PATA on Maxtor PCI card IDE slot - Ubuntu

I downloaded the Ubuntu ISO and burned it to a CD. I used it awhile before deciding to install to the blank 80Gb drive, letting it have the whole drive for the partitions it created. After the reboot, got the GRUB 1.5 Error 17 message. Can no longer boot to either of the Windows disks or the Ubuntu install. Only able to boot with the live CD and luckily can get to the internet.

Found some info about this error, but I don't yet fully understand some of the instructions. I can get to the Terminal window but am stuck logged in as ubuntu@ubuntu. This is what I got from fdisk -l:
ubuntu@ubuntu:/etc$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
161 heads, 15 sectors/track, 258858 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      620181   312571192+   7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9732    78172258+   7  HPFS/NTFS
/dev/sdc2            9733       30515   166939447+   f  W95 Ext'd (LBA)
/dev/sdc5            9733       30515   166939416    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9382    75360883+  83  Linux
/dev/sdd2            9383        9732     2811375    5  Extended
/dev/sdd5            9383        9732     2811343+  82  Linux swap / Solaris
ubuntu@ubuntu:/etc$ ~
ubuntu@ubuntu:/etc$

The first drive should not be showing up as FAT16. It shows as unallocated when looking at the drive in GParted.](*,) It should be NTFS Win XP. I hope the Ubuntu install did not corrupt it!!

I was able to mount the /dev/sdd1 drive, but I don't know what to do next.


Please help with explicit instructions as I am a new newbie.
Thanks.

---

### Post by BoneKracker on 2006-09-30
I'm not sure I can help, but I can help you gather some additional information needed to figure it out.

Congratulations on figuring out how to mount the drive.  In that sdd1 partion, you should see a /boot directory.  There's a file in there it would be useful to post here.
navigate into the /boot/grub directory on that drive
you should see a file named menu.lst  This is the bootloader's configuration file.  It's called GRUB.  You can read about it by typing "man grub" in the terminal or googling "GRUB documentation menu.lst".
```
cat menu.lst
```
Copy and paste the output into a reply here.

Also:
```
dmesg |more
```
Examine the output to see if the LiveCD seems to be properly identifying the relevant hardware components (i.e., drives, southbridge, drive controllers, etc.)  If you see anything suspicious, post it here in another reply.  Don't be afraid to post the whole thing.

---

### Post by AstenMarquis on 2006-09-30
Here's the menu.lst:
ubuntu@ubuntu:/mnt/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd3,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd3,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd3,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:/mnt/boot/grub$

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Anothe rpost will have the output of dmesg |more.

How do I fix the GRUB now? Is there any interplay between the BIOS HD boot priority and what is set up in GRUB? Do I have to set up my Linux drive to be the first in the boot order in the BIOS?

Now that I've mounted the Linux drive, why can't I see it in the Ubuntu GUI under Places - Computer?

Thanks for your help,
Steve

---

### Post by AstenMarquis on 2006-09-30
Here's the dmesg | more output:


ubuntu@ubuntu:/mnt/boot/grub$ dmesg |more
[    0.000000] Bootdata ok (command line is BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --)
[    0.000000] Linux version 2.6.15-26-amd64-generic (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f7c00
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003bef3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003bef30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003bef9680
[    0.000000] ACPI: SRAT (v001 AMD    HAMMER   0x00000001 AMD  0x00000001) @ 0x000000003bef98c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003bef99c0
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003bef95c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 0-40000000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bef0000
[    0.000000] On node 0 totalpages: 241106
[    0.000000]   DMA zone: 3014 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 238092 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 5060000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 3 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2210.223 MHz processor.
[   37.933891] Console: colour VGA+ 80x25
[   37.934716] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   37.935916] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   37.947180] Memory: 955000k/981952k available (2150k kernel code, 26560k reserved, 757k data, 180k init)
[   38.024963] Calibrating delay using timer specific routine.. 4427.56 BogoMIPS (lpj=8855128)
[   38.025025] Security Framework v1.0.0 initialized
[   38.025033] SELinux:  Disabled at boot.
[   38.025057] Mount-cache hash table entries: 256
[   38.025212] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.025216] CPU: L2 Cache: 512K (64 bytes/line)
[   38.025219] CPU 0(2) -> Node 0 -> Core 0
[   38.025227] mtrr: v2.0 (20020519)
[   38.025238] SMP alternatives: switching to UP code
[   38.025585] checking if image is initramfs... it is
[   38.643040] Freeing initrd memory: 7606k freed
[   38.652751] ACPI: Looking for DSDT ... not found!
[   38.702377] Using local APIC timer interrupts.
[   38.747598] Detected 12.558 MHz APIC timer.
[   38.747789] SMP alternatives: switching to SMP code
[   38.748010] Booting processor 1/2 APIC 0x1
[   38.758852] Initializing CPU#1
[   38.837030] Calibrating delay using timer specific routine.. 4420.68 BogoMIPS (lpj=8841365)
[   38.837037] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.837039] CPU: L2 Cache: 512K (64 bytes/line)
[   38.837041] CPU 1(2) -> Node 0 -> Core 1
[   38.837119] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   38.837127] CPU 1: Syncing TSC to CPU 0.
[   38.836653] CPU 1: synchronized TSC with CPU 0 (last diff -84 cycles, maxerr 580 cycles)
[   38.836666] Brought up 2 CPUs
[   38.836727] Disabling vsyscall due to use of PM timer
[   38.836729] time.c: Using PM based timekeeping.
[   38.836732] testing NMI watchdog ... OK.
[   38.877237] NET: Registered protocol family 16
[   38.877280] ACPI: bus type pci registered
[   38.877346] PCI: Using configuration type 1
[   38.880936] PCI: Using MMCONFIG at e0000000
[   38.881788] ACPI: Subsystem revision 20051216
[   38.892294] ACPI: Interpreter enabled
[   38.892299] ACPI: Using IOAPIC for interrupt routing
[   38.893810] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.893815] PCI: Probing PCI hardware (bus 00)
[   38.910367] Boot video device is 0000:00:05.0
[   38.911476] PCI: Transparent bridge - 0000:00:10.0
[   38.911992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   39.236895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   39.242915] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   39.243887] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.244865] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[   39.245806] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[   39.246763] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.247738] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.248731] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   39.249703] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.250681] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   39.251702] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.252695] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   39.253651] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 *10 11 14 15)
[   39.254610] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.255590] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[   39.256582] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.257559] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   39.258547] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   39.259550] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.260535] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   39.261513] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   39.262700] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   39.263888] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   39.265082] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   39.266242] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   39.267429] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   39.268613] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   39.269764] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   39.270901] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   39.272067] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   39.273247] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   39.274391] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   39.275535] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   39.276682] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   39.277827] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   39.278971] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   39.280139] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   39.281295] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   39.282423] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   39.283571] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   39.284718] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   39.285853] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   39.295546] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.295564] pnp: PnP ACPI init
[   39.314040] pnp: PnP ACPI: found 14 devices
[   39.314066] PCI: Using ACPI for IRQ routing
[   39.314071] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   39.314297] PCI-DMA: Disabling IOMMU.
[   39.315908] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[   39.315912] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[   39.315915] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[   39.315918] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[   39.315921] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[   39.315924] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[   39.315927] pnp: 00:00: ioport range 0x2000-0x207f has been reserved
[   39.315930] pnp: 00:00: ioport range 0x2080-0x20ff has been reserved
[   39.316558] PCI: Bridge: 0000:00:02.0
[   39.316563]   IO window: 9000-9fff
[   39.316566]   MEM window: fd600000-fd6fffff
[   39.316569]   PREFETCH window: fde00000-fdefffff
[   39.316571] PCI: Bridge: 0000:00:03.0
[   39.316573]   IO window: 8000-8fff
[   39.316576]   MEM window: fdd00000-fddfffff
[   39.316579]   PREFETCH window: fdc00000-fdcfffff
[   39.316581] PCI: Bridge: 0000:00:04.0
[   39.316583]   IO window: a000-afff
[   39.316586]   MEM window: fd800000-fd8fffff
[   39.316588]   PREFETCH window: fd700000-fd7fffff
[   39.316595] PCI: Bridge: 0000:04:08.0
[   39.316598]   IO window: b000-bfff
[   39.316602]   MEM window: fda00000-fdafffff
[   39.316606]   PREFETCH window: fd900000-fd9fffff
[   39.316610] PCI: Bridge: 0000:00:10.0
[   39.316612]   IO window: b000-cfff
[   39.316615]   MEM window: fda00000-fdbfffff
[   39.316618]   PREFETCH window: fd900000-fd9fffff
[   39.316631] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.316636] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   39.316642] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   39.316649] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   39.317447] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   39.318390] audit: initializing netlink socket (disabled)
[   39.318407] audit(1159695015.556:1): initialized
[   39.318689] VFS: Disk quotas dquot_6.5.1
[   39.318717] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   39.318795] Initializing Cryptographic API
[   39.318800] io scheduler noop registered
[   39.318817] io scheduler anticipatory registered
[   39.318829] io scheduler deadline registered
[   39.318856] io scheduler cfq registered
[   47.313979] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   47.314634] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.314639] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[   47.314659] assign_interrupt_mode Found MSI capability
[   47.314707] Allocate Port Service[pcie00]
[   47.314820] Allocate Port Service[pcie03]
[   47.314921] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   47.314925] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[   47.314940] assign_interrupt_mode Found MSI capability
[   47.314966] Allocate Port Service[pcie00]
[   47.315074] Allocate Port Service[pcie03]
[   47.315177] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   47.315181] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[   47.315202] assign_interrupt_mode Found MSI capability
[   47.315224] Allocate Port Service[pcie00]
[   47.315345] Allocate Port Service[pcie03]
[   47.357446] Real Time Clock Driver v1.12
[   47.357520] Linux agpgart interface v0.101 (c) Dave Jones
[   47.357696] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   47.359967] serio: i8042 AUX port at 0x60,0x64 irq 12
[   47.360072] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.360097] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   47.360284] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.360662] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   47.365073] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.366126] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[   47.366215] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   47.366219] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   47.366439] mice: PS/2 mouse device common for all mice
[   47.366995] NET: Registered protocol family 2
[   47.396248] input: AT Translated Set 2 keyboard as /class/input/input0
[   47.422004] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   47.422384] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   47.425257] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   47.426684] TCP: Hash tables configured (established 131072 bind 65536)
[   47.426687] TCP reno registered
[   47.426781] TCP bic registered
[   47.426798] NET: Registered protocol family 1
[   47.426806] NET: Registered protocol family 8
[   47.426809] NET: Registered protocol family 20
[   47.426981] ACPI wakeup devices:
[   47.426984] HUB0 XVRA XVRB XVRC USB0 USB2 AZAD MMAC MMCI UAR1
[   47.426990] ACPI: (supports S0 S1 S4 S5)
[   47.427081] Freeing unused kernel memory: 180k freed
[   47.526880] vga16fb: initializing
[   47.526885] vga16fb: mapped to 0xffff8100000a0000
[   47.708674] Console: switching to colour frame buffer device 80x25
[   47.708681] fb0: VGA16 VGA frame buffer device
[   48.772226] Capability LSM initialized
[   48.885027] ACPI: Fan [FAN] (on)
[   48.894804] ACPI: Thermal Zone [THRM] (40 C)
[   50.394586] SCSI subsystem initialized
[   50.398237] ACPI: bus type scsi registered
[   50.398241] libata version 1.20 loaded.
[   50.401796] sata_nv 0000:00:0e.0: version 0.8
[   50.403135] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   50.403143] GSI 16 sharing vector 0xD1 and IRQ 16
[   50.403151] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 209
[   50.403313] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   50.403448] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
[   50.403491] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xE008 irq 209
[   50.772890] ata1: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3c41 87:4023 88:407f 93:0000
[   50.772896] ata1: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[   50.785466] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff81003bec1b80
[   50.809136] ata1: dev 0 configured for UDMA/133
[   50.821481] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff81003bec1b80
[   50.844484] scsi0 : sata_nv
[   51.215604] ata2: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3c41 87:4023 88:407f 93:0000
[   51.215611] ata2: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[   51.227836] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff81003bec1b80
[   51.250993] ata2: dev 0 configured for UDMA/133
[   51.263213] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff81003bec1b80
[   51.286334] scsi1 : sata_nv
[   51.288675]   Vendor: ATA       Model: WDC WD3200KS-00P  Rev: 21.0
[   51.288687]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   51.292908]   Vendor: ATA       Model: WDC WD3200KS-00P  Rev: 21.0
[   51.292919]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   51.298121] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   51.298148] NFORCE-MCP51: chipset revision 161
[   51.298150] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   51.298156] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   51.298167]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[   51.298178]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[   51.298190] Probing IDE interface ide0...
[   51.313845] Driver 'sd' needs updating - please use bus_type methods
[   51.316891] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   51.316967] SCSI device sda: drive cache: write back
[   51.319487] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   51.319553] SCSI device sda: drive cache: write back
[   51.319567]  sda: sda1
[   51.327473] sd 0:0:0:0: Attached scsi disk sda
[   51.327592] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   51.327654] SCSI device sdb: drive cache: write back
[   51.327802] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   51.327878] SCSI device sdb: drive cache: write back
[   51.327882]  sdb: sdb1
[   51.339926] sd 1:0:0:0: Attached scsi disk sdb
[   51.872008] Probing IDE interface ide1...
[   52.611619] hdc: LITE-ON DVDRW SOHW-1653S, ATAPI CD/DVD-ROM drive
[   53.395104] hdd: LITEON DVD-ROM LTD163D, ATAPI CD/DVD-ROM drive
[   53.451607] ide1 at 0x170-0x177,0x376 on irq 15
[   53.481334] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   53.481346] Uniform CD-ROM driver Revision: 3.20
[   53.988347] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   54.143590] sata_promise 0000:04:09.0: version 1.03
[   54.145469] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   54.145478] GSI 17 sharing vector 0xD9 and IRQ 17
[   54.145486] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 217
[   54.145695] sata_promise PATA port found
[   54.161608] ata3: SATA max UDMA/133 cmd 0xFFFFC2000003E200 ctl 0xFFFFC2000003E238 bmdma 0x0 irq 217
[   54.161649] ata4: SATA max UDMA/133 cmd 0xFFFFC2000003E280 ctl 0xFFFFC2000003E2B8 bmdma 0x0 irq 217
[   54.161695] ata5: PATA max UDMA/133 cmd 0xFFFFC2000003E300 ctl 0xFFFFC2000003E338 bmdma 0x0 irq 217
[   54.365350] ata3: no device found (phy stat 00000000)
[   54.365354] scsi2 : sata_promise
[   54.569215] ata4: no device found (phy stat 00000000)
[   54.569219] scsi3 : sata_promise
[   54.733489] ata5: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:7f09 84:4003 85:7c69 86:3e01 87:4003 88:407f 93:403b
[   54.733494] ata5: dev 0 ATA-7, max UDMA/133, 490234752 sectors: LBA48
[   54.741482] ata5: dev 1 cfg 00:045a 49:0f00 82:346b 83:5b01 84:4003 85:3469 86:1a01 87:4003 88:407f 93:6b00
[   54.741486] ata5: dev 1 ATA-5, max UDMA/133, 156355584 sectors: LBA
[   54.741626] ata5: dev 0 configured for UDMA/133
[   54.741790] ata5: dev 1 configured for UDMA/133
[   54.741810] sata_get_dev_handle: SATA dev addr=0x90000, handle=0x0000000000000000
[   54.741813] scsi4 : sata_promise
[   54.742027]   Vendor: ATA       Model: Maxtor 6Y250P0    Rev: YAR4
[   54.742037]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   54.742158] SCSI device sdc: 490234752 512-byte hdwr sectors (251000 MB)
[   54.742221] SCSI device sdc: drive cache: write back
[   54.742372] SCSI device sdc: 490234752 512-byte hdwr sectors (251000 MB)
[   54.742429] SCSI device sdc: drive cache: write back
[   54.742435]  sdc: sdc1 sdc2 < sdc5 >
[   54.774336] sd 4:0:0:0: Attached scsi disk sdc
[   54.774565]   Vendor: ATA       Model: MAXTOR 6L080J4    Rev: A93.
[   54.774575]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   54.774698] SCSI device sdd: 156355584 512-byte hdwr sectors (80054 MB)
[   54.774769] SCSI device sdd: drive cache: write back
[   54.774906] SCSI device sdd: 156355584 512-byte hdwr sectors (80054 MB)
[   54.774962] SCSI device sdd: drive cache: write back
[   54.774967]  sdd: sdd1 sdd2 < sdd5 >
[   54.799608] sd 4:0:1:0: Attached scsi disk sdd
[   55.312765] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   55.314522] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   55.314531] GSI 18 sharing vector 0xE1 and IRQ 18
[   55.314539] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 225
[   55.314547] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   55.314560] forcedeth: using HIGHDMA
[   55.315487] usbcore: registered new driver usbfs
[   55.315536] usbcore: registered new driver hub
[   55.320769] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[   55.320778] GSI 19 sharing vector 0xE9 and IRQ 19
[   55.320787] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 233
[   55.320939] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   55.320947] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   55.320995] ehci_hcd 0000:00:0b.1: debug port 1
[   55.320999] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   55.321439] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   55.321458] ehci_hcd 0000:00:0b.1: irq 233, io mem 0xfe02e000
[   55.321470] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   55.321647] hub 1-0:1.0: USB hub found
[   55.321664] hub 1-0:1.0: 8 ports detected
[   55.356087] ieee1394: Initialized config rom entry `ip1394'
[   55.364896] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   55.366910] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[   55.366919] GSI 20 sharing vector 0x32 and IRQ 20
[   55.366927] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 20 (level, low) -> IRQ 50
[   55.367106] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   55.367114] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   55.424860] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   55.424876] ohci_hcd 0000:00:0b.0: irq 50, io mem 0xfe02f000
[   55.484393] hub 2-0:1.0: USB hub found
[   55.484417] hub 2-0:1.0: 8 ports detected
[   55.836628] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
[   55.838416] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   55.838430] GSI 21 sharing vector 0x3A and IRQ 21
[   55.838439] ACPI: PCI Interrupt 0000:05:08.2[C] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 58
[   55.838587] ehci_hcd 0000:05:08.2: EHCI Host Controller
[   55.841757] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   55.841766] GSI 22 sharing vector 0x42 and IRQ 22
[   55.841774] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 66
[   55.841915] ohci_hcd 0000:05:08.0: OHCI Host Controller
[   55.842430] ohci_hcd 0000:05:08.0: new USB bus registered, assigned bus number 3
[   55.842445] ohci_hcd 0000:05:08.0: irq 66, io mem 0xfdaff000
[   55.864447] ehci_hcd 0000:05:08.2: new USB bus registered, assigned bus number 4
[   55.864467] ehci_hcd 0000:05:08.2: irq 58, io mem 0xfdafd000
[   55.864479] ehci_hcd 0000:05:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   55.864649] hub 4-0:1.0: USB hub found
[   55.864668] hub 4-0:1.0: 5 ports detected
[   55.912342] usb 2-8: new full speed USB device using ohci_hcd and address 2
[   56.411512] hub 3-0:1.0: USB hub found
[   56.411534] hub 3-0:1.0: 3 ports detected
[   56.928796] ACPI: PCI Interrupt 0000:05:08.1[B] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 217
[   56.928947] ohci_hcd 0000:05:08.1: OHCI Host Controller
[   56.929050] ohci_hcd 0000:05:08.1: new USB bus registered, assigned bus number 5
[   56.929060] ohci_hcd 0000:05:08.1: irq 217, io mem 0xfdafe000
[   57.494360] hub 5-0:1.0: USB hub found
[   57.494376] hub 5-0:1.0: 2 ports detected
[   58.015421] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   58.015454] ACPI: PCI Interrupt 0000:05:0c.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 66
[   58.066375] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[66]  MMIO=[fdafc000-fdafc7ff]  Max Packet=[2048]
[   58.152991] Probing IDE interface ide0...
[   59.338400] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042b5c0007289]
[   60.454305] ISO 9660 Extensions: Microsoft Joliet Level 3
[   60.491026] ISO 9660 Extensions: RRIP_1991A
[   60.530488] loop: loaded (max 8 devices)
[   60.573568] Registering unionfs 1.1.2
[   60.726989] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[  149.114311] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  149.114381] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  149.114454] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  149.114523] sd 4:0:1:0: Attached scsi generic sg3 type 0
[  151.317078] NET: Registered protocol family 17
[  153.694644] NET: Registered protocol family 10
[  153.694863] lo: Disabled Privacy Extensions
[  153.695310] IPv6 over IPv4 tunneling driver
[  154.390775] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  154.419066] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  155.692813] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3C02
[  155.692923] usbcore: registered new driver usblp
[  155.692928] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  156.525922] input: PS/2 Generic Mouse as /class/input/input1
[  156.719096] acx: Loaded combined PCI/USB driver, firmware_ver=default
[  156.719101] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[  156.722446] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[  156.722455] GSI 23 sharing vector 0x4A and IRQ 23
[  156.722462] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 74
[  156.722521] acx: found ACX111-based wireless network card at 0000:04:07.0, irq:74, phymem1:0xFDBFC000, phymem2:0xFDBA0000, mem1:0xffffc200100c0000, mem1_size:8192, mem2:0xffffc20010100000, mem2_size:131072
[  157.154422] ts: Compaq touchscreen protocol output
[  157.561856] parport: PnPBIOS parport detected.
[  157.561922] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  157.574221] irda_init()
[  157.574266] NET: Registered protocol family 23
[  157.725570] acx: firmware 'Rev 2.3.1.31' does not work well with this driver
[  157.725576] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware
'Rev 2.3.1.31' (0x03010101)
[  157.726280] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-26-amd64-generic
[  157.727954] usbcore: registered new driver acx_usb
[  157.857415] Floppy drive(s): fd0 is 1.44M
[  157.878174] FDC 0 is a post-1991 82077
[  158.011984] input: PC Speaker as /class/input/input2
[  158.523072] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[  158.523079] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 209
[  158.523273] PCI: Setting latency timer of device 0000:00:10.2 to 64
[  158.790177] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  158.845884] intel8x0_measure_ac97_clock: measured 58594 usecs
[  158.845888] intel8x0: clocking to 47006
[  160.194485] Adding 2811332k swap on /dev/sdd5.  Priority:-1 extents:1 across:2811332k
[  161.154604] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  161.154609] md: bitmap version 4.39
[  162.167905] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  164.233287] eth0: no IPv6 routers present
[  173.687006] cdrom: open failed.
[  199.753596] ACPI: Power Button (FF) [PWRF]
[  199.753614] ACPI: Power Button (CM) [PWRB]
[  200.006773] ibm_acpi: ec object not found
[  200.077086] pcc_acpi: loading...
[  201.746432] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[  201.746407] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8 (1350 mV)
[  201.746412] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa (1300 mV)
[  201.746415] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc (1250 mV)
[  201.746418] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[  201.746426] cpu_init done, current fid 0xe, vid 0x8
[  231.228766] lp0: using parport0 (interrupt-driven).
[  231.294376] ppdev: user-space parallel port driver
[  240.566382] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[  261.221924] Bluetooth: Core ver 2.8
[  261.221930] NET: Registered protocol family 31
[  261.221932] Bluetooth: HCI device and connection manager initialized
[  261.221955] Bluetooth: HCI socket layer initialized
[  261.621764] Bluetooth: L2CAP ver 2.8
[  261.621770] Bluetooth: L2CAP socket layer initialized
[  262.095437] Bluetooth: RFCOMM socket layer initialized
[  262.095461] Bluetooth: RFCOMM TTY layer initialized
[  262.095464] Bluetooth: RFCOMM ver 1.7
[  959.544110] kjournald starting.  Commit interval 5 seconds
[  959.544789] EXT3 FS on sdd1, internal journal
[  959.545338] EXT3-fs: mounted filesystem with ordered data mode.
[  995.705983] end_request: I/O error, dev fd0, sector 0
[  995.727791] end_request: I/O error, dev fd0, sector 0
[  995.749591] end_request: I/O error, dev fd0, sector 0
[  995.771397] end_request: I/O error, dev fd0, sector 0
[  995.809559] end_request: I/O error, dev fd0, sector 0
[  995.831364] end_request: I/O error, dev fd0, sector 0
[  995.878984] NTFS driver 2.1.25 [Flags: R/O MODULE].
[  995.891321] end_request: I/O error, dev fd0, sector 0
[  995.913122] end_request: I/O error, dev fd0, sector 0
[  995.951281] end_request: I/O error, dev fd0, sector 0
[  995.973081] end_request: I/O error, dev fd0, sector 0
[  996.007609] end_request: I/O error, dev fd0, sector 0
[  996.029408] end_request: I/O error, dev fd0, sector 0
[  996.053030] end_request: I/O error, dev fd0, sector 0
[  996.078466] end_request: I/O error, dev fd0, sector 0
[  996.127532] end_request: I/O error, dev fd0, sector 0
[  996.151146] end_request: I/O error, dev fd0, sector 0
[  996.191123] end_request: I/O error, dev fd0, sector 0
[  996.212924] end_request: I/O error, dev fd0, sector 0
[  996.329869] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  996.330364] SGI XFS Quota Management subsystem
[  996.343750] end_request: I/O error, dev fd0, sector 0
[  996.365557] end_request: I/O error, dev fd0, sector 0
[  996.454479] JFS: nTxBlock = 7521, nTxLock = 60174
[  996.472757] end_request: I/O error, dev fd0, sector 0
[  996.496377] end_request: I/O error, dev fd0, sector 0

I reviewed this log and did not see anything blatantly wrong. It seems to recognise all the drives.

---

### Post by murkydurky on 2006-09-30
i am also having the grub 1.5 error 17..but i don't know how to mount anything...i've had ubuntu running with a dual boot to xp for about 2 months..no problems..i updated yesterday...tried to install MOHAA and it locked up..i shut it down..one time it made it to the screen that would allow me to choose xp or ubuntu...choose xp (the only way i can play bf2)..it never made it into xp...the entire system rebooted and i get the GRUB 1.5 error 17 ](*,)  ... i've got several years of windows under my belt..even a couple of low-level certs..but i don't know jack about linux..is their an easy solution to fix this? i've allready tried to run the xp recovery console and the "fixmbr" command...didn't work.. help please!!! [-o< [-o<

this is my main computer..i have to have it up by monday so ANY help is appreciated!

---

### Post by Bigbluecat on 2006-09-30
Well I have not been using Ubuntu long but i have had my share of boot problems. The last one just today when I did a kernel upgrade.

I found the following site invaluable to help me through:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Also used Super Grub Disk to help diagnose the problems. You can find this here:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

The grub command line has some great tools for identifying and finding drives and partitions. This is in my limited experience what normally goes wrong. If you have the grub boot loader starting you can press c to get to the command line. 

If you read through Hermans guide it will tell you about the command line and how to use null (hd, and tab to find out how grub sees and names your partitions.

If you want to read about my trials and solutions they are here:

[http://ubuntuforums.org/showthread.php?t=259422&highlight=bigbluecat](http://ubuntuforums.org/showthread.php?t=259422&highlight=bigbluecat)
[http://www.ubuntuforums.org/showthread.php?t=268459](http://www.ubuntuforums.org/showthread.php?t=268459)

I also had the problem that FIXMBR did not work when I tried it first time. I believe in my case it was beacuse I did something silly with grub and not only overwrote the MBR but also corrupted the boot sector.

To fix this I used the WinXP recovery console and entered three commands:

FIXBOOT               (this fixes the boot sector)
FIXMBR                (this replaces the MBR with WinXP MBR - Grub is eliminated)
BOOTCFG /rebuild

That did it for me. In my case WinXP was on the first partition of the first drive.

I'm not all that experience here but I'll try to help where I can.

Please take the time to solidly read Herman's grub guide. There are good step by step diagnostic instructions.

Lastly please do your own due diligence. Do not just take my word and plunge in.

Good luck

---

### Post by AstenMarquis on 2006-09-30
Thanks BigBlueCat. That gives me some ideas to try. I had only tried the FIXMBR and got nowhere.

MurkyDurky,
In my limited Linux experience, I found:

From a terminal screen (you can get there from the GUI Apps menu)
type: sudo fdisk -l
This will list all the disks and partitions on your machine that the system sees.

Once you know which drive you want to mount (something like /dev/sda1 for the first SATA or SCSI disk)

type:  sudo mount /dev/sda1 /mnt
This mounts this drive/partition as the /mnt directory.

you can then type: mount to see if this worked.

and then: cd /mnt to get to the folders on this disk.

You then want to get to the /mnt/boot/grub folder to find the menu.lst file. you do this by typing cd /mnt/boot/grub or cd ./boot/grub if you're already at the /mnt folder. You can use cd .. just like in the DOS world to go up a level in the folder tree.

You can view the contents by typing: cat menu.lst (that's the letter ell)

I haven't figured out how to actually change anything in that file yet, but it shouldn't be too long.

---

### Post by bulldog on 2006-09-30
> **AstenMarquis said:**
> Thanks BigBlueCat. That gives me some ideas to try. I had only tried the FIXMBR and got nowhere.

MurkyDurky,
In my limited Linux experience, I found:

From a terminal screen (you can get there from the GUI Apps menu)
type: sudo fdisk -l
This will list all the disks and partitions on your machine that the system sees.

Once you know which drive you want to mount (something like /dev/sda1 for the first SATA or SCSI disk)

type:  sudo mount /dev/sda1 /mnt
This mounts this drive/partition as the /mnt directory.

you can then type: mount to see if this worked.

and then: cd /mnt to get to the folders on this disk.

You then want to get to the /mnt/boot/grub folder to find the menu.lst file. you do this by typing cd /mnt/boot/grub or cd ./boot/grub if you're already at the /mnt folder. You can use cd .. just like in the DOS world to go up a level in the folder tree.

You can view the contents by typing: cat menu.lst (that's the letter ell)

I haven't figured out how to actually change anything in that file yet, but it shouldn't be too long.

I'm not sure if I understand all your steps but if you want to mount your hdd in a live session you have to make a mount folder like this.
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu 
```

Now you van use nautilus to browse to the mounted disk.

If you want to alter your menu.lst or any other file you can use gedit like this ```
gksudo gedit /boot/grub/menu.lst 
```

---

### Post by Bigbluecat on 2006-10-01
AstenMarquis,

There is an interplay between the BIOS boot priority and what grub writes to the menu.lst. This was the essence of my problems. Grub starts counting your disks from 0 so sda1 is hd0,0 sdb1 is hd1,0 etc.

If the bios is set to say that sdb1 is the first boot drive then you may get inconsitencies. This is the exact issue with my setup. My WinXP is on /dev/sdb1 and grub picked this up as hd1,0. However the bios thinks of it as hd0,0.

Your menu.lst has the WinXP entry as hd1,0. That is it will boot the WinXP on the second drive. The MAP commands fool windows into thinking it is on the first drive - it's a windows thing to always want to be first.

Also your linux boot entires seem to be OK. Grub root is hd3,0 or /dev/sbd1.

It was not clear from your first post if you see the grub menu at the start.

If your bios is indicating that a drive other than /dev/sda1 is hd0,0 it may be that the grub IPL has been written to the wrong location. Take a look at your bios and see how it orders the drives.

One more point is that in my first fail and recovery of windows MBR I then had to fix a few corrupted files on one of my drives - not many and all were fixed.

Really can't say why /dev/sda1 looks like FAT16.

---

### Post by BoneKracker on 2006-10-01
Looks like your getting some good advice.

Observation 1:

I may be wrong on this, but I think GRUB notation works like this:

sd0,0 would be "first partition on first scsi drive"
hd0,0 would be "first partition on first ide drive"

So, if that's true (and I could be remembering wrong) given that SATA drives are treated as SCSI, it might be (might be, mind you I said) that your linux boot partition on the fourth drive could be considered to be on your second IDE drive and hence hd1,0 (i.e., hdb).

Observation 2:

From your first post, it seems fdisk is calling all four of your drives "sd".  Strange.  Meanwhile, your dmesg seems to be referring to the first two drives as sd and the second two as hd.

---

