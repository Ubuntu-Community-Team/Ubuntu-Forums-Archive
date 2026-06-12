---
title: "Backup NTFS partition to DVD"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by ugm6hr on 2008-01-01
I got Vista pre-installed on my Acer laptop (5051AWXMi) hard drive.  I did not get a boot CD/DVD with it.  It also came with a primary NTFS *recovery* partition for Vista.  I did initially try to create a Recovery DVD from the Vista Acer software before wiping the Vista partition, but it wouldn't work.  I wiped Vista anyway, safe in the knowledge that I have my recovery partition if I ever want it back (i did pay for it, after all).

**sudo fdisk -l** returns the following (sda1 is the recovery partition):
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e769501

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020        2903    15133230    7  HPFS/NTFS
/dev/sda3            2904        7296    35286772+   5  Extended
/dev/sda5            2904        5253    18876312   83  Linux
/dev/sda6            7175        7296      979933+  82  Linux swap / Solaris
/dev/sda7            5254        7174    15430401   83  Linux
```

GParted reports sda1 as **NTFS**, but fdisk sees it as **Compaq diagnostics**.

I would still like to create a recovery DVD so that I can free the extra 7.81GB (4.51GB used) for a separate */home* partition for Ubuntu without sacrificing Vista forever.

I have seen partimage and clonezilla, but am uncertain whether they will work on this unusual NTFS format.  Do you have to run these programs from a LiveCD, or will they work from within Ubuntu?  Ideally, I would want the backup to fit on a single DVD (is this realistic?), but 2 DVDs is an acceptable solution.  Otherwise, an external backup on a USB HD is OK.

Thanks for any advice...

---

### Post by bigken on 2008-01-01
personally I would contact acer tell them you have tried to create the system discs with no luck and now the restore partition is corrupted they might or should send you the recovery discs good luck

---

