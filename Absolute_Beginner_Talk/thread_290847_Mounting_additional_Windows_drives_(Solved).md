---
title: "Mounting additional Windows drives (Solved)"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by requiem_gr on 2006-11-01
> **aysiu said:**
> I'll give you the commands to copy and paste.

Whenever possible, copy and paste--do not retype. Retyping takes longer and is more prone to errors.

Make a mount point: ```
sudo mkdir /media/windows
``` Edit your /etc/fstab ```
sudo nano -B /etc/fstab
``` Add this line: ```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Save (Control-x, y, Enter). Remount ```
sudo mount -a
```

Worked for me, as I am a total newbie in Linux world and I was completely lost. My only problem is that I have 2 more drives that I need to mount. My sudo fdisk -l, command looked like this :


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7693    61793991    7  HPFS/NTFS
/dev/sda2           11128       30401   154818405    f  W95 Ext'd (LBA)
/dev/sda3   *        7694       11127    27583605   83  Linux
/dev/sda5           11278       17652    51207156    7  HPFS/NTFS
/dev/sda6           17653       30401   102406311    7  HPFS/NTFS
/dev/sda7           11128       11277     1204812   82  Linux swap / Solaris

Partition table entries are not in disk order
... I know asking about the commands, at this point may seem stupid to you, but I hadn't touched a console since I was 12, and I am 20 now (and that was in ms-dos, so I think it does not count.)

Any help will be greatly appreciated.

---

### Post by aysiu on 2006-11-01
The same principle applies for each NTFS drive.

Each one needs its own mount point and its own line in the /etc/fstab

So you would need something like /media/windows1, /media/windows2, and /media/windows3.

You would also need three lines in your /etc/fstab for each one--/dev/sda1, /dev/sda5, and /dev/sda6.

---

### Post by housam on 2006-11-02
Hi, try this link :
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
 Housam

---

### Post by requiem_gr on 2006-11-02
It worked. Thank you :)

---

