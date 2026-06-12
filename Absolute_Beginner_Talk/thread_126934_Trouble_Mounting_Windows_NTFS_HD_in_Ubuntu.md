---
title: "Trouble Mounting Windows NTFS HD in Ubuntu"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by ubuntnoob on 2006-02-07
Hello all,

I am very new to linux.  This is my first time attempting a HD install.  So far Ubuntu works great.  Except I have a lot of files I would like to access on my Windows HD.

I have 40GB Master - windowsXP NTFS
and 10GB Slave  for Ubuntu

I followed the instuctions in this thread:
[http://ubuntuforums.org/showthread.php?t=126724&highlight=mount+HD]("http://ubuntuforums.org/showthread.php?t=126724&highlight=mount+HD")
Because I had the exact same problems when i tried to mount my HD.

After following the instructions the windows drive is now visible when I run fdisk:

```
nick@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1200     9638968+  83  Linux
/dev/hdb2            1201        1245      361462+   5  Extended
/dev/hdb5            1201        1245      361431   82  Linux swap / Solaris

Disk /dev/sda: 1008 MB, 1008730112 bytes
64 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         962      984816    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(774, 63, 32) logical=(961, 47, 32)
```

This is the line I added at the end of /etc/fstab:

```
/dev/hda1	/media/win 	ntfs	nls=utf8,mask=0222 0	0
```

However after remounting or rebooting  /media/win is still empty and I still can't access my other HD.

I hope this is enough information.

I apprecieate any help.

Thanks,

---

### Post by goatflyer on 2006-02-07
umask=0222

---

### Post by ubuntnoob on 2006-02-07
Thanks for the reply....

That'll teach me to be too proud to cut and paste.

---

