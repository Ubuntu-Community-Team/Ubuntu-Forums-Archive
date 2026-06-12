---
title: "Natty Install changed Partition scheme (MacbookPro 8,1)"
date: 2011-05-05
forum: Apple Hardware Users
---

### Post by jmueck on 2011-05-05
Hello,

i was experiencing slow start ups since i installed ubuntu 11.04. it took about 20-30sec for the apple logo to come up (or rEFIt).
today apple released EFI firmware updates which doesn't seem to install. reason is that the partition scheme is not compatible. EFI Firmware updates only install from GUID partition schemes.
DiskUtility tells me i have MBR.

So it seems like Ubuntu changed the Partition Scheme.

Can any body confirm that?

how can i make sure ubuntu installs into existing GUID?

i will re-partition later today and give you an update if the EFI firmware update installs and boot time is faster.

---

### Post by srs5694 on 2011-05-05
Before you repartition, please install the gdisk package ("sudo apt-get install gdisk") and post the output of the following two commands (typed in Linux):

```

sudo fdisk -lu /dev/sda
sudo gdisk -l /dev/sda

```

Those commands should reveal how your system is partitioned. It's possible that the firmware updater is getting confused because of some peculiarity in your partition table that's easily corrected, rather than something that requires a wipe and re-install.

If the disk *has* been converted to MBR, then you can convert back to GPT by using gdisk; however, this might disrupt your ability to boot the system, so I don't recommend you do this without preparing for such an eventuality.

---

### Post by b16a2smith on 2011-05-06
**FDISK**
```
b16@ubi:~$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   105878391    52734376   af  HFS / HFS+
/dev/sda3       105878392   226626438    60374023+  83  Linux
/dev/sda4       226626439   234440892     3907227   82  Linux swap / Solaris
b16@ubi:~$ 

```

GDISK

```
b16@ubi:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ED0674E9-4216-4AE5-A78A-97FAD96D7B98
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 1-sector boundaries
Total free space is 728 sectors (364.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       105878391   50.3 GiB    AF00  MBP SSD
   3       105878392       226626438   57.6 GiB    0700  
   4       226626439       234440892   3.7 GiB     8200  

```

---

### Post by srs5694 on 2011-05-06
Your partition scheme definitely has *not* changed to a conventional MBR setup. Most likely, the reason the updater is refusing to work is that your partitions have no gaps between them. According to Apple's [Technical Note 2166](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html) (see the "Partitioning Policy" section in particular), most partitions should have a trailing 128 MiB gap. OS X won't install if such a gap is absent (I've tested this myself), and my suspicion is that the firmware updater has a similar issue (although I've not tested this myself).

As a practical matter, this means that you can probably get by with resizing either /dev/sda2 or /dev/sda3 by 128 MiB, to provide the gap between those two partitions. Resizing /dev/sda2 is probably safer, but I'm not sure if Apple's Disk Utility will do it, since that gap isn't present. GParted will shrink (but not grow) HFS+ partitions, but I'm not sure how reliable its HFS+ support is. Resizing /dev/sda3 with GParted should work, but you'd need to move the start of the partition, which is always riskier and usually more time-consuming than moving the end. Thus, whichever way you choose to do it, I recommend you back up all your important data from both those partitions before you proceed.

While you're at it, you may want to create a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) You've got a 361 KiB chunk of unused space at the very end of your disk that will serve this purpose fine, or you can shrink /dev/sda2 or /dev/sda3 by 129 MiB rather than 128 MiB and put a 1 MiB BIOS Boot Partition right before /dev/sda3 (leaving 128 MiB unpartitioned after /dev/sda2). Your computer is probably booting Linux in BIOS mode, making the presence of a BIOS Boot Partition advisable, for reasons described on the BIOS Boot Partition Web page I've just referenced.

Another caveat: You're currently using a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) This is an ugly and dangerous hack, but your system probably relies on it to boot Linux in BIOS mode. GParted will almost certainly convert from a hybrid MBR to a conventional protective MBR, which may render Linux unbootable. You can restore your hybrid MBR afterwards by using gptsync, gdisk, or possibly an option on the rEFIt menu. You may also need to restore Linux's GRUB boot loader once this is all done. I like to do this by using the [Super GRUB 2 Disk](http://www.supergrubdisk.org) to boot Linux and then re-installing by typing "sudo grub-install /dev/sda" in a Terminal; but it's possible to do it by using the Ubuntu installation disc and jumping through a few extra hoops. (I don't happen to have a reference to the precise procedure offhand, though.)

---

