---
title: "access rights to partitions and external hard drives"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ~sparkles~ on 2007-06-14
I have been trying to get the external hard drive I have to appear on the desktop. Somehow in the process of changing the system settings/system administration/disk and filesystems I now cannot access partitions that I previously could and get the message:

[IMG]http://i90.photobucket.com/albums/k257/Solar66/snapshot1.png[/IMG]

This remains even after I changed everything back and rebooted... I've been loving the last four days of newbie problem solving but this is weird stuff...

---

### Post by KIAaze on 2007-06-14
What does the following command give you?:
```
ls -ld /media/sda5
```

You might want to look into the chmod, chgrp and chown commands to know how to change file permissions:
> man chmod
man chgrp
man chown


Please post the outputs of the following commands here:
```
cat /etc/fstab
```
```
df -h
```
```
sudo fdisk -l
```

I don't know if they are really necessary to solve your exact problem, but they are usually useful for any mounting problems since they give an overview of your filesystem setup.

---

### Post by ~sparkles~ on 2007-06-14
Thank you so much for the reply.. I've been going nuts...

here's what i get

[PHP]ls: /media/sda5: No such file or directory[/PHP]

[PHP]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        1154     9213277+   7  HPFS/NTFS
/dev/sda3            1155        9650    68244120    f  W95 Ext'd (LBA)
/dev/sda5            3123        9650    52436128+   6  FAT16
/dev/sda6            1155        2127     7815559+  83  Linux
/dev/sda7            2128        2224      779121   82  Linux swap / Solaris
/dev/sda8            2225        3122     7213153+   b  W95 FAT32

Partition table entries are not in disk order


[/PHP]

[PHP]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        1154     9213277+   7  HPFS/NTFS
/dev/sda3            1155        9650    68244120    f  W95 Ext'd (LBA)
/dev/sda5            3123        9650    52436128+   6  FAT16
/dev/sda6            1155        2127     7815559+  83  Linux
/dev/sda7            2128        2224      779121   82  Linux swap / Solaris
/dev/sda8            2225        3122     7213153+   b  W95 FAT32

Partition table entries are not in disk order


[/PHP]

[PHP]Filesystem            Size Used Avail Use% Mounted on
/dev/sda6             7.4G  2.8G  4.2G  40% /
varrun                248M  104K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb            248M  140K  248M   1% /proc/bus/usb
udev                  248M  140K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.20-15-generic/volatile
df: `/media/sda1': No such file or directory
df: `/media/sda2': No such file or directory
df: `/media/sda5': No such file or directory
[/PHP]



The weird thing is that this seems to change every third or fourth time I reboot and I'll be able to breifly access partitions.

---

### Post by vanadium on 2007-06-14
Is this external drive an USB drive? If it is, it should automatically be mounted after plugging it in, and an icon should show on the desktop. I am not sure what the behaviour is if such a disk contains multiple partitions: I would suspect that an icon then appears for each partition.

If it is a drive that is permanently present, it should be declared in /etc/fstab. the only alternative would be to mount it manually each time. In your reply, you forgot to post the output of /etc/fstab (you erroneously posted two times the output of fdisk -l): post it also.

---

