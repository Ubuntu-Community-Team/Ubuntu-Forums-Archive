---
title: "RAID 1 Partitions listed as duplicate devices"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by JohnnyFiver on 2008-03-03
I have a serial RAID 1 configuration on my A7N8X Deluxe (Silicon Image 3112 controller) for my data and such (no OS).  I set up RAID 1 and partitioned the disk before I installed Ubuntu 7.10.  After Ubuntu installed, I see my volumes, but they, and the disks, are each listed twice in /dev (sda, sda1, sda2, sdb, sdb1, sdb2) and are mounted twice.

Here's how Ubuntu set up /etc/fstab for "one" particular volume:

```
# /dev/sda1
UUID=22981D0C981CE059 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sdb1
UUID=22981D0C981CE059 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
```

When I write to a volume, it appears in both "copies" as expected, but I'm confused, because I thought my hardware RAID configuration would appear as one disk and one set of volumes.  Is this not the case?

Why is Ubuntu seeing and mounting two volumes instead of one per RAID partition?

Thank you in advance.

---

### Post by Oldsoldier2003 on 2008-03-04
> **JohnnyFiver said:**
> I have a serial RAID 1 configuration on my A7N8X Deluxe (Silicon Image 3112 controller) for my data and such (no OS).  I set up RAID 1 and partitioned the disk before I installed Ubuntu 7.10.  After Ubuntu installed, I see my volumes, but they, and the disks, are each listed twice in /dev (sda, sda1, sda2, sdb, sdb1, sdb2) and are mounted twice.

Here's how Ubuntu set up /etc/fstab for "one" particular volume:

```
# /dev/sda1
UUID=22981D0C981CE059 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sdb1
UUID=22981D0C981CE059 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
```

When I write to a volume, it appears in both "copies" as expected, but I'm confused, because I thought my hardware RAID configuration would appear as one disk and one set of volumes.  Is this not the case?

Why is Ubuntu seeing and mounting two volumes instead of one per RAID partition?

Thank you in advance.
The reason Ubuntu is seeing them as the same UUID is because the UUIDs aren't unique, it can happen when the drives weren't formatted, or in the case of some RAID 1 setups, cloned by the controller...

look here for a deeper discussion and how to fix it:[http://ubuntuforums.org/showthread.php?t=326871](http://ubuntuforums.org/showthread.php?t=326871)

---

