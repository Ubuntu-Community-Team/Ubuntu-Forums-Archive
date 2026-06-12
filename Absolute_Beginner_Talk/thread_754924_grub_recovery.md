---
title: "grub recovery"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-14
I have a dual boot vista and ubuntu.
Recently i had to reinstall vista and recover grub.
Since then ubuntu doesn't detect my vista c:\.

---

### Post by ibutho on 2008-04-14
Are you saying that Ubuntu does not list Vista in grub (or you can boot into Windows from grub) or can you not access your Windows partition from within Linux. If you cannot access your windows partition from within Linux, can you post the output of running
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by ikonia on 2008-04-14
does grub boot sucessfully into windows ?

What happens when you try to mount your wndows hard disk manually in grub ?

Can the windows partition be seen from say the output of fdisk -l against the hard disk ?

---

### Post by sameer.india on 2008-04-14
cannot access your windows partition from within Linux
sameer@sameer-laptop:~$ sudo fdisk -l
[sudo] password for sameer:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003ae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5100       18183   105088000    7  HPFS/NTFS
/dev/sda3           18183       19204     8203125   83  Linux
/dev/sda4           19205       19457     2032222+  82  Linux swap / Solaris

---

### Post by sameer.india on 2008-04-14
grub boots successfully into windows

---

### Post by sameer.india on 2008-04-14
sameer@sameer-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2946bc29-bb7c-466c-823e-86394c27eed3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=26A40C6DA40C4233 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=A26E18426E1811A1 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=9e904b2b-6cfc-4ad2-bdeb-f77f39217d8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by ikonia on 2008-04-14
I assume your windows environment is /dev/sda1  or /dev/sda2

what happens when you try to mount them manually

"sudo mount /dev/sda1 /mnt"

---

### Post by sameer.india on 2008-04-14
Thanks Guys  I got it

---

### Post by ibutho on 2008-04-14
Edit your /etc/fstab (back it up first) and change the lines below
```

# /dev/sda1
UUID=26A40C6DA40C4233 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda2
UUID=A26E18426E1811A1 /media/sda2 ntfs defaults,umask=007,gid=46 0 1

```
to
```
# /dev/sda1
/dev/sda1 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda2
/dev/sda2 /media/sda2 ntfs defaults,umask=007,gid=46 0 1
```
After that run
```
sudo mount -a
```

---

