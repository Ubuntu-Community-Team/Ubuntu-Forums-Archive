---
title: "NTFS disk problems"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-11-23
Hi there
Heres a quick breakdown: Last night I triued to access my old laptop HDD because I wanted some data off it (yes, its just music). Anyway, I created a mountpoint (/media/windows) and tried to mount the thing( it has XP on ??? partition) and 'mount' asked me to specify the partition type. I read through the man pages and read up on the how tos and finally tried again. Nothing. GParted doesnt even pick up the disk, and Disks doesnt either. I KNOW Ive installed it properly (as primary slave, with correct jumpers) and I know it works, because I can still use it to boot up the PC  (Yes, I set it as primary master and it worked, or at least XP booted and crashed to BSOD). Any ideas????
I DID try passing filesystem type to 'mount' but that didnt work ( -t vfat and -t ntfs)

Please help!!!
B.

---

### Post by taurus on 2006-11-23
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
sudo fdisk -l
```
The command to mount NTFS filesystem is

```
sudo mount -t ntfs /dev/hda1 /media/windows
(or whatever the drive is...)
```

---

### Post by Bachstelze on 2006-11-23
Please paste the output of

```
sudo fdisk -l
```

---

