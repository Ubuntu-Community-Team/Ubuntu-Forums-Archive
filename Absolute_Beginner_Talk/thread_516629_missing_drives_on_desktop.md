---
title: "missing drives on desktop"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by garyflynn on 2007-08-03
When I boot into my installed 7.04 partition, most of my ntfs drives are represented as icons on my desktop, but two are not.

I installed pysdm, but I don't want to use it until I've heard from someone because when I click on hda6, which is an NTFS drive that has an icon, pysdm says it has not yet been configured.  Same for hda1, which does not have an icon.

Gparted has exclamation point icons listed next to the partitions.

Come to think of it, I only need three of the drives, including the two that are not found to appear.

Here are my questions:

1 - What program does the automount, or produces the icons at boot time?  Can I manually decide which drives should appear on the desktop?

2 - How do I resolve the exclamation point icons to the left of the partition in gparted? What do they mean?

---

### Post by nitro_n2o on 2007-08-03
did you try to go to Places->computer-> and double click the drive name.. ubuntu will automount them (at least on my computer its true) 
can you post sudo fdisk -l

---

### Post by garyflynn on 2007-08-03
Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/hda2            1786        3442    13309852+  83  Linux
/dev/hda3            3443        5099    13309852+   7  HPFS/NTFS
/dev/hda4            5100       48641   349751115    5  Extended
/dev/hda5            5100        5418     2562336   82  Linux swap / Solaris
/dev/hda6            5419       10007    36861111    7  HPFS/NTFS
/dev/hda7           10008       17401    59392273+   7  HPFS/NTFS
/dev/hda8           17402       48641   250935268+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1715    13775706    7  HPFS/NTFS
/dev/hdb2            1716        2288     4602622+  83  Linux
/dev/hdb4            2289       30401   225817672+   5  Extended
/dev/hdb5            2289        2575     2305296   82  Linux swap / Solaris
/dev/hdb6            2576       16282   110101446    7  HPFS/NTFS
/dev/hdb7           16283       24898    69207988+   7  HPFS/NTFS
/dev/hdb8           24899       30401    44202816    7  HPFS/NTFS

When I ran gparted, it did a scan of the disk and found hda8 and hda1 - when I reboot, those do not come up automatically.  It comes up after I've run gparted in places -> my computer.

When I next reboot the machine I'll post another fdisk.

I also would like these drives to be editable.  I'll look that up now but if you have anything its appreciated.

---

### Post by garyflynn on 2007-08-03
I installed and ran ntfs-3g conf.  I just rebooted and again I'm not autodetecting hda1 or hda8.  I have not run gparted yet but I expect that to pop them back up.

fdisk -l looks the same:

Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/hda2            1786        3442    13309852+  83  Linux
/dev/hda3            3443        5099    13309852+   7  HPFS/NTFS
/dev/hda4            5100       48641   349751115    5  Extended
/dev/hda5            5100        5418     2562336   82  Linux swap / Solaris
/dev/hda6            5419       10007    36861111    7  HPFS/NTFS
/dev/hda7           10008       17401    59392273+   7  HPFS/NTFS
/dev/hda8           17402       48641   250935268+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1715    13775706    7  HPFS/NTFS
/dev/hdb2            1716        2288     4602622+  83  Linux
/dev/hdb4            2289       30401   225817672+   5  Extended
/dev/hdb5            2289        2575     2305296   82  Linux swap / Solaris
/dev/hdb6            2576       16282   110101446    7  HPFS/NTFS
/dev/hdb7           16283       24898    69207988+   7  HPFS/NTFS
/dev/hdb8           24899       30401    44202816    7  HPFS/NTFS

update:

running gparted did cause a rescan and did find the partitions again.  They have reappeared on my desktop.

There are still exclamation points in triangles to the left of the partition names.  Gparted help is not yet implemented so I'm not sure what the exclamation points mean or what to do about them.

---

### Post by Inxsible on 2007-08-03
post the ouput of 
```
gksudo gedit /etc/fstab
``` Those 2 drives probably do not have the automount option enabled in fstab

---

### Post by garyflynn on 2007-08-03
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=d28032a9-f8e5-49ab-b9b5-5634c51ede5b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=5F43ABE15F898B95 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda3 :
UUID=350EF67101775C23 /media/hda3 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=1B35F93D7B602128 /media/hda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda7 :
UUID=5C8042B22DBC4329 /media/hda7 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=2FA599FA2AF1365D /media/hda8 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda1 :
UUID=3670F65C70F62273 /media/hdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdb2 :
UUID=72632053-7b03-453e-961f-6d8566e92b71 /media/hdb2 ext3 defaults 0 2
# Entry for /dev/hda8 :
UUID=5E904B0C904AE9DB /media/hdb6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdb7 :
UUID=E4405FDB405FB352 /media/hdb7 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdb8 :
UUID=62AC6A8AAC6A5895 /media/hdb8 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=023a88eb-06aa-4699-a4ce-37b6397cfd5c none swap sw 0 0
# Entry for /dev/hdb5 :
UUID=1a2cbeea-3b8a-4ca7-9b01-a6a8d65ae8c1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by garyflynn on 2007-08-04
Would it help to say that the two drives that are not detected are copies, made using driveimage xml, of two drives on the other disk?

Maybe the drives have some name or drive information in common.

1 - If it is the case that there is information on duplicated drives that cannot or should not conflict, how would I change that information?

2 - If I was to make a manual fstab with just the minimum options to work, how would the entries look?

# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=5F43ABE15F898B95 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

What would that be changed to so that I would have a vanilla functional automounting, read-write fstab entry?

---

### Post by nitro_n2o on 2007-08-04
i'm not sure about drive image but try changing the 2 lines before the last to "auto" instead on "noauto" and reboot.. that might work give it a shot

---

### Post by garyflynn on 2007-08-04
I'm not having any problems with the cd-roms.

1 - The two partitions hda1 and hda8 give exclamation points in gparted.  Anyone know what those exclamation points mean?  Those are the copied partitions - they are copied from hdb1 and hdb6 I think.

2 - In my fstab file there are lines:

# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=5F43ABE15F898B95 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

Can I replace that with
/dev/hda1 /media/hda1 ntfs-3g users 0 0

For read/write access or would I be missing something?

Also is there a forum that specializes in hard disk mounting or ntfs-3g where I'll find people who focus more narrowly on problems like mine?

---

### Post by Inxsible on 2007-08-04
> **garyflynn said:**
> I'm not having any problems with the cd-roms.

1 - The two partitions hda1 and hda8 give exclamation points in gparted.  Anyone know what those exclamation points mean?  Those are the copied partitions - they are copied from hdb1 and hdb6 I think.

2 - In my fstab file there are lines:

# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=5F43ABE15F898B95 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

Can I replace that with
/dev/hda1 /media/hda1 ntfs-3g users 0 0

For read/write access or would I be missing something?

Also is there a forum that specializes in hard disk mounting or ntfs-3g where I'll find people who focus more narrowly on problems like mine?
```
 /dev/hda1 /media/hda1 ntfs-3g defaults 0 0
``` is what you want. Check this [link]("http://doc.gwos.org/index.php/Understanding_fstab") out for a great info on fstab

---

