---
title: "Some NTFS drives/partitions do not show up in feisty"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by whee on 2007-04-26
After having run Dapper for some period of time i switched to Feisty and all has been good except for 1 thing.
In Dapper i always used to see my disks which have Windows on them and other NTFS partitions.
Now i only see the disk with Feisty on it and some other windows NTFS partition.
Now the missing partitions/disks only do not show up on the desktop, but they do when i open Places>This Computer.
Then the disks and partitions do show up, when i try to double klik on 1, it says i need root privileges to access/mount them, but i never needed this in Dapper, what's going on?
Maybe it also has to do with the fact i installed the ntfs-3g drivers?
Does someone know what might be the problem and how to fix it?

---

### Post by Iceni on 2007-04-26
I think you could simply try :

```
sudo mount -a
```
and post eventuel errors?

Could you also post your /etc/fstab and the output of "sudo fdisk -l" ?

---

### Post by sailor2001 on 2007-04-26
easy way to get your windows access and also windows recovery partition is go to automatix2

---

### Post by whee on 2007-04-26
Odly enough, now that i booted the system after having not booted it for several days the disks and partitions show up. But the weird thing is when i rebooted several days ago to see if that made any difference the disks/partitions would not show up. I don't know why this is so.

This command:
```
sudo mount -a
```
gives this output:
```
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/4670AFC570AFBA57 ()
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/5C2C8DE82C8DBE10 (NieuwVolume)
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/D6F8C247F8C22599 (NieuwVolume)
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/A25049A650498251 ()
```

/etc/fstab contains this:

```
proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=0035d057-6497-4b09-a660-bb94723066b8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=4670AFC570AFBA57 /media/hda1 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=5C2C8DE82C8DBE10 /media/hda5 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=D6F8C247F8C22599 /media/hda6 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
# Entry for /dev/sdb1 :
UUID=112C-1A01 /media/hdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb5 :
UUID=A25049A650498251 /media/hdb5 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
# Entry for /dev/sdb6 :
UUID=C4DE-F7CF /media/hdb6 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda8 :
UUID=ac9962b7-cfcd-469c-a6aa-6ab03677c0e3 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

This command:

```
sudo fdisk -l 
```

gives the following output:

```
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38912   261361485    f  W95 Extend. (LBA)
/dev/sda5            6375       19122   102398278+   7  HPFS/NTFS
/dev/sda6           19123       37637   148721706    7  HPFS/NTFS
/dev/sda7           37638       38848     9727326   83  Linux
/dev/sda8           38849       38912      514048+  82  Linux swap

/dev/sdb1   *           1        2503    20105316    c  W95 FAT32 (LBA)
/dev/sdb2            2504       10011    60308010    f  W95 Extend. (LBA)
/dev/sdb5            2504        6182    29551536    7  HPFS/NTFS
/dev/sdb6            6183       10011    30756411    b  W95 FAT32
```


@sailor2001
I used to have Automatix2 on Dapper, but i found out it messes some things up, i used to think it was great, but now i rather not have it interfere with standard operations in Ubuntu.

---

### Post by Iceni on 2007-04-26
Did you by any chance run the Feisty beta and have now upgraded to final? I had some toruble with disks and mounting myself during the last days of the beta, but fixed it only to have the final change something...:) 

Anyway the "mount-a" errors are of course because your disks are already mounted. Good to see it worked out:)

---

### Post by whee on 2007-04-26
> **Iceni said:**
> Did you by any chance run the Feisty beta and have now upgraded to final?

No, i installed the final version of Feisty after i wiped the diskspace where Dapper used to be. So i did a clean install. I have no idea why the disks/partitions didn't show up earlier, but do now. Spooky :)

---

