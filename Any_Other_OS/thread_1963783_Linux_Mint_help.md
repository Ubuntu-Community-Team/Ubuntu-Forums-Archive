---
title: "Linux Mint help"
date: 2012-04-22
forum: Any Other OS
---

### Post by jroa on 2012-04-22
I posted this in the Linux Mint forums, but did not get a reply.

I am helping out a friend who has Mint 11 installed onto a USB drive. When booted, it will not auto mount another USB drive, although Disk Utility recognizes the drive. I tried to manual mount using Disk Utility and got the following error.

> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed


I tried this with two separate drives and got the same results. In Windows XP, both drives work fine. Here is the output of fdisk. sdc1 is the drive that will not mount.

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d2f3ee

Device Boot Start End Blocks Id System
/dev/sda1 * 1 19456 156280288+ 7 HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
64 heads, 32 sectors/track, 15267 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ac53

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 7630 7812500 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2 7630 15266 7819265 5 Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb5 7631 9537 1952768 82 Linux swap / Solaris
/dev/sdb6 9539 15266 5865472 83 Linux

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58e10cca

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 7840 2007024 e W95 FAT16 (LBA)


Any help with this would be appreciated.

---

### Post by grahammechanical on 2012-04-22
From that error message I would say that you are trying to mount the USB drive with the Linux operating system on.

I cannot say anything about Linux Mint but if this was Ubuntu from a USB memory stick I would use the file manager and if it showed that there was another USB memory stick in the machine I would click on its icon and that would mount the USB drive as far as I would understand.

Regards.

---

### Post by Lateralis on 2012-04-22
Can you post the contents of /etc/fstab and /etc/mtab, and of

```

sudo blkid

```

when the USB drive is connected?

---

### Post by jroa on 2012-04-23
> **grahammechanical said:**
> From that error message I would say that you are trying to mount the USB drive with the Linux operating system on.


Thanks for the quick reply.  One of them did in fact have a bootable Linux on it: Fedora 16.  The other only had data, mainly pictures.  Neither would auto mount and both gave the same error message.

The file manager (I think it was Nautilus) did not list it at all.  And, there was no desktop icon for the newly inserted drive.  This was the reason I used the disk utility.  

Thanks again for your help.

---

### Post by jroa on 2012-04-23
> **Lateralis said:**
> Can you post the contents of /etc/fstab and /etc/mtab, and of

```

sudo blkid

```

when the USB drive is connected?

Thanks, I will give it a try tomorrow.  I do not have access to the memory stick right now, but my friend will have it at work tomorrow.

---

### Post by Perfect Storm on 2012-04-23
Moved to Other OS/Distro Talk.

---

### Post by anejo on 2012-04-24
Yeah I remember in my Mint days that this... *"/dev/sdnn is already mounted on /"* message occurred enough times for me to try and get a handle on it.

If I recall correctly... the clue is in 'mtab'--or sometimes 'fstab'--after all. Once I commented out the offending line that was similar, like a *"sdb1"* it sorted out future mount failures.

---

