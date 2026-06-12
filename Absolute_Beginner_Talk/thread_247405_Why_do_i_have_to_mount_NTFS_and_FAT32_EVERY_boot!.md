---
title: "Why do i have to mount NTFS and FAT32 EVERY boot?!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-08-30
Is this normal, how do I have them permanently or automatically mounted?

---

### Post by taurus on 2006-08-30
You can do that with /etc/fstab.  Edit /etc/fstab and add two lines at the end, one for NTFS and one for FAT32.

Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/fstab
```
Now, use the arror key and move down the to bottom of it.  Then, add those two lines, assuing that /dev/hda1 is your NTFS and /dev/hda2 is your VFAT...

```

/dev/hda1   /media/windows   ntfs   defaults,umask=0222   0   0
/dev/hda2   /media/share     vfat   defaults,umask=0000   0   0

```
Save it and then create those two mount points and mount them with

```

sudo mkdir /media/windows /media/share
sudo mount -a

```
From now on, those two partitions will be mounted automatically each time you boot Ubuntu...

---

### Post by pbaehr on 2006-08-30
Here is a guide which explains how to mount both NTFS and FAT partitions at boot using fstab. fstab is a file which the system looks at to determine what partitions get mounted where. By adding the entries in the link the partitions will be found and mounted on boot.
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

*EDIT* Beat to the punch. Oh well, good luck, anyway.

---

### Post by systemintheglitch on 2006-08-30
Thanks a lot guys, helpful as usual..

But one newbie question, whats sudo vs. gksudo?

---

### Post by aysiu on 2006-08-30
> **systemintheglitch said:**
> Thanks a lot guys, helpful as usual..

But one newbie question, whats sudo vs. gksudo?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by systemintheglitch on 2006-08-30
> **taurus said:**
> You can do that with /etc/fstab.  Edit /etc/fstab and add two lines at the end, one for NTFS and one for FAT32.

Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/fstab
```
Now, use the arror key and move down the to bottom of it.  Then, add those two lines, assuing that /dev/hda1 is your NTFS and /dev/hda2 is your VFAT...

```

/dev/hda1   /media/windows   ntfs   defaults,umask=0222   0   0
/dev/hda2   /media/share     vfat   defaults,umask=0000   0   0

```
Save it and then create those two mount points and mount them with

```

sudo mkdir /media/windows /media/share
sudo mount -a

```
From now on, those two partitions will be mounted automatically each time you boot Ubuntu...


Um.. Whats vfat? My drive is a fat32. Does linux refer to them as vfat?

---

### Post by aysiu on 2006-08-30
Yes, as far as your /etc/fstab is concerned, *vfat* covers both FAT32 and FAT16.

---

