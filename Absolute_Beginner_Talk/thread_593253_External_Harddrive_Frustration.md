---
title: "External Harddrive Frustration"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by brokenlighter on 2007-10-27
I have a 200GB external Formatted in half. Half NTFS half ext3. I need to know how to be able to read/write to at least the ext3 half. I'm helluh new with Linux so I don't know what I'm doing hardly at all. Someone helped get to read/write by mounting as root or something but that was only for a little bit. I want to be able to read/write all the time without having to do anything.

---

### Post by taurus on 2007-10-27
Assuming the ext3 half is /dev/sdb2, open a terminal and do

```
sudo mkdir /media/sdb2 (If you get a message about there is already /media/sdb2, then just move on.)
sudo mount -t ext3 /dev/sdb2 /media/sdb2
df -h
```
Now, if you want to write to /media/sdb2 without using sudo, then you need to change the ownership if that mount point from root to your login name.  Again, assuming your login name is **broken**, do

```
sudo chown -R **broken**:**broken** /media/sdb2
ls -la /media
```

---

### Post by brokenlighter on 2007-10-27
How do i find out if the drive is "/dev/sdb2" or whatever.

---

### Post by taurus on 2007-10-27
```
sudo fdisk -l
```
Lower case letter l, not number 1.

---

### Post by brokenlighter on 2007-10-27
It still doesn't let me do stuff like rename the drive either. How can I rename the drive, and there is stuff like the other half of the drive that is ntfs that is on my desktop. I cant do anything with it and I cant get it off my desktop either. same with the ntfs partition of my internal harddrive.

---

### Post by taurus on 2007-10-27
Can you post the outputs of these commands?

```
sudo fdisk -l
df -h
id
```

p.s.  What do you mean renaming the drive?

---

### Post by brokenlighter on 2007-10-27
> :~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fa98fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1246    10008463+   7  HPFS/NTFS
/dev/sda2            1311        2491     9486382+  83  Linux
/dev/sda3            1247        1310      514080   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10704    85979848+   7  HPFS/NTFS
/dev/sdb2           10705       24321   109378552+   f  W95 Ext'd (LBA)
/dev/sdb5           10705       24321   109378521   83  Linux

> r:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.0G  5.1G  3.5G  60% /
varrun                125M   92K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  100K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   92M  28% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             9.6G  7.3G  2.3G  77% /media/hda1
/dev/sdb5             102G   31G   66G  32% /media/Moving
/dev/sdb1              82G   48G   35G  59% /media/External


> r:~$ id
uid=1000(brokenlighter) gid=1000(brokenlighter) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(brokenlighter)


External = NTFS partition of external drive
Moving = ext3 Partition of external

---

### Post by taurus on 2007-10-27
```
sudo chown -R brokenlighter:brokenlighter /media/Moving
ls -la /media/Moving
```

---

### Post by brokenlighter on 2007-10-27
> **taurus said:**
> ```
sudo chown -R brokenlighter:brokenlighter /media/Moving
ls -la /media/Moving
```

I did that, and it worked (thank you). But the other partition of the external is still on the desktop and I cant get rid of it. the other partition of the internal is still there too. 

and I cant rename the ext3 partition from "Moving" to anything else.

---

### Post by taurus on 2007-10-27
If you want to unmount the ntfs partition, you need to run

```
sudo umount /media/External
```
And if you want to mount /dev/sdb5 to somewhere else instead of /media/Moving, then you need to unmount it first, create a new mount point, and mount it.

```
sudo umount /media/Moving
sudo mkdir /mnt/storage
sudo mount -t ext3 /dev/sdb5 /mnt/storage
sudo chown -R brokenlighter:brokenlighter /mnt/storage
ls -la /mnt/storage
```

---

### Post by brokenlighter on 2007-10-27
I still don't get how to rename the drives.

---

