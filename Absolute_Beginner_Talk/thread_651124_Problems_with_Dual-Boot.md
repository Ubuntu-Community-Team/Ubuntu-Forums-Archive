---
title: "Problems with Dual-Boot"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by zeca2k4 on 2007-12-27
Hi all

I sincerely apologize if this is an issue you're all fed up of handling.

I have searched the forums and elsewhere and had no luck so far.

My setup consists of a Core 2 Duo with 4 SATA drives and an IDE.

I have 2 SATA drives set up in RAID 0 with Windows XP on and would like to leave that alone as I explore Linux further.

So, I set up UBUNTU on partitions on the 3rd SATA, leaving the 4th for backups and storage, etc.

The IDE has some more personal, less intensive files.

Among my explorations, I found Wingrub and according to this, my partition list looks like this:
(hd0,0)  - Linux Ext2(83)
(hd0,1)  - ExtendedX (0F)
(hd0,4) G FAT32 (0B)
(hd0,5) - Linux Swap (82)
(hd1,0) H NTFS (07)
(hd1,1) - ExtendedX (0F)
(hd1,4) I NTFS (07)
(hd2,0) C NTFS (07)
(hd2,1) - ExtendedX (0F)
(hd2,4) D NTFS
(hd3,4) E NTFS (07)
(hd4,0) J NTFS (07)
(hd4,1) - ExtendedX (0F)
(hd4,4) - NTFS (07)

Attached is the Windows XP disk management image.

OK, now the problem: GRUB doesn't show up so I can never boot into UBUNTU.

I accepted all defaults after specifying where I wanted what, like root, boot and swap.

In my BIOS I can't see the remaining drives to boot from, only the RAID volume and CD's.

I don't mind booting with a CD in the drive if need be.

Thanks for any assistance and may the best moments of 2007 be the worst of 2008.

---

### Post by nick_h on 2007-12-27
Please boot to a Live CD and post the output of:
```
sudo fdisk -l
```
It looks like you just need to install grub.  You can also do this from the Live CD.

---

### Post by zeca2k4 on 2007-12-27
Thanks for replying, here is the output:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3450fd80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  83  Linux
/dev/sda2            4865       20023   121764667+   f  W95 Ext'd (LBA)
/dev/sda5            6205       20023   111001086    b  W95 FAT32
/dev/sda6            4865        6204    10763487   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15bba2c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10059    80798886    7  HPFS/NTFS
/dev/sdb2           10060       20023    80035830    f  W95 Ext'd (LBA)
/dev/sdb5           10060       20023    80035798+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e159e15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdc2           12749       20021    58420372+   f  W95 Ext'd (LBA)
/dev/sdc5           12749       13797     8421504    0  Empty

Disk /dev/sdd: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00140000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e8d74e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       15272   122672308+   7  HPFS/NTFS
/dev/sde2           15273       30401   121523692+   f  W95 Ext'd (LBA)
/dev/sde5           15273       30401   121523661    7  HPFS/NTFS

---

### Post by Tyke91 on 2007-12-27
to install grub

boot from your live CD and enter a shell

```
sudo grub
```
```
find /boot/grub/stage1
```
you will be given a list of hard drives, choose your ubuntu one for the next step

insert your ubuntu hd into the question marks
```
root (hd?,?)
```

```
setup (hd0)
```

I hope this works for you, and welcome to ubuntu :D

---

### Post by jas0 on 2007-12-27
Hmm... from prior experience I have to assume that the problem you have is related to the RAID array being the first boot device. When you were installing Ubuntu, it probably did not detect your RAID 0. The MBR was setup on the Ubuntu drive, but this drive is not even looked at when booting your computer. 

For testing purposes, try disconnecting your RAID 0 drives and see if Ubuntu boots up. If it does, you will have to setup your Ubuntu drive as your first boot device and then somehow make sure that it recognizes the RAID 0 array so that it can also include the option of booting Windows.

---

### Post by dstew on 2007-12-27
To get Ubuntu to see your RAID appropriately, you will need to use the dmraid program. You can install it from Synaptic on a LiveCD Ubuntu system. Then when you install Ubuntu, it should recognize your RAID properly, and hopefully you will be able to dual-boot. See [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto).

The other way you can try this is to change your BIOS so it boots from the IDE drive, and install Ubunutu on that. Right now, with Ubuntu on one of the SATA drive, and with the other SATA drives in a RAID, you might not be able to properly boot Ubuntu. It depends on your BIOS. That is, even if the grub boot loader is on the MBR of the Ubuntu SATA, maybe your BIOS will not let you boot it if you also have a RAID configured, but I don't really know about this for sure.

One more thing: I am told that the Alternate Install CD will install Ubuntu onto a RAID (if that is what you want to do) without going through all the commands as shown in the Fake Raid How-To. If you do not want Ubuntu on the RAID, it might be that the Alternate Install CD will still do a better job, because maybe it will handle the RAID more appropriately than the LiveCD installer.

---

### Post by nick_h on 2007-12-27
> Hmm... from prior experience I have to assume that the problem you have is related to the RAID array being the first boot device. When you were installing Ubuntu, it probably did not detect your RAID 0. The MBR was setup on the Ubuntu drive, but this drive is not even looked at when booting your computer.

Yes, I would expect this to be the case.

> If it does, you will have to setup your Ubuntu drive as your first boot device

I am not an expert on this, I did a quick google for "grub raid" and suggest the OP does the same.  It seems that grub needs to be installed on the RAID drives.

[This](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html) looks like a relevant link.
Ubuntu is installed in the first partition of drive 1 so the root command should be "root (hd0,0)" and then the RAID drives are (hd1) and (hd2).

```
root (hd0,0)
setup (hd1)
setup (hd2)

```

Perhaps someone with a greater knowledge than me could confirm this is the way to go.

---

### Post by zeca2k4 on 2008-01-02
OK, Holiday Season is over and I could get back to this issue.

The combination of suggestions from Tyke91 and nick_h managed to get GRUB to load, but now I'm faced with something potentially worse>

When I choose a UBUNTU option, I get an error "Could not mount partition".

When I choose Windows XP, my computer reboots, tells me that windows failed to boot and choose an option.  Even if I choose SAFE MODE, I'm stuck in a reboot cycle.

What now? Help!!!

---

