---
title: "Now 100% Ubuntu, need help turning XP partition into data storage?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by marco123 on 2007-05-03
Hi.  After a few weeks learning I can now do absolutely everything in Ubuntu that I used to do in windoze. (Better)

I currently have a dual boot with xp and Ubuntu, and was wondering if there was a way to format the windows partion from within Ubuntu and use it for storage?

Any help extremely appreciated, windows is now useless to me.  :) :popcorn:

---

### Post by Jazztux on 2007-05-03
Hi, if you are a GNOME user, you can easily install GNOME partition editor with synaptic ;)

---

### Post by Cypher on 2007-05-03
It's great that you've converted to Ubuntu from Windows..to reclaim the Windows partition for Ubuntu, let's start with the current partition scheme..

Go Applications->Accessories->Terminal, then
```

sudo fdisk -l

```
This will show us where your Windows partition is located, then you can format the appropriate partition to EXT3 and modify the /etc/fstab file to mount your newly created partition.

---

### Post by davezac on 2007-05-03
i use gparted (gnome partition editor) you can get it for ubuntu but also you can run it as a live cd. download and burn as an iso.
take care when you partition

---

### Post by marco123 on 2007-05-03
I dis that fdisk command, is it the bottom one? -

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         605        3230    21093345    7  HPFS/NTFS
/dev/sda2               1         604     4851598+  12  Compaq diagnostics
/dev/sda3            3231        7123    31270522+  83  Linux
/dev/sda4            7124        7296     1389622+   5  Extended
/dev/sda5            7124        7296     1389591   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by Cypher on 2007-05-03
So you have two NTFS partitions../dev/sda1 and /dev/sdb1. I would suggest that now you load up gparted (**sudo apt-get install gparted** if not installed) and you can format to EXT3 from within there.

---

### Post by marco123 on 2007-05-03
It says one is "Recovery"(FAT32), and the other is "File System".

The second NTFS is my external storage drive I think.

So  I right click on it and select Format to-ext3?

Do I need to change permissions or anything? (Sorry for all the questions-  first time I,ve done this.)

---

### Post by totalnub on 2007-05-03
depends on what you want to save.....if your external is ready to be wiped, then go ahead. be sure to unmount first. also, you can just delete all ntfs and the recovery fat32 partition and merge them all to one big ext3.

---

### Post by marco123 on 2007-05-03
All done.  Thank you very much.   (Was like having a virus left on the PC ,lol):)

---

### Post by rcmullins on 2007-05-08
Will gparted  format fat32?

---

### Post by Cypher on 2007-05-08
[GParted]("http://gparted.sourceforge.net/") will format [many things]("http://gparted.sourceforge.net/features.php")..

---

### Post by rcmullins on 2007-05-08
Awesome! Thanks for the reply, I guess I should have read the site.

---

