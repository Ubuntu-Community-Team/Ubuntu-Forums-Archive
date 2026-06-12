---
title: "Seagate Won't Mount: Please help"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by suki on 2007-05-02
I followed the instructions in this thread
[ http://ubuntuforums.org/showthread.php?t=415769]("http://ubuntuforums.org/showthread.php?t=415769") 
but still no luck.

I put everything on the Seagate external hard drive when I was switching over from edgy to feisty. It would be a terrible loss if I couldn't everything off there and back on the computer, I have important documents on there. :(

If anyone has a solution please post a comment.
```
user@laptop:~$ sudo fdisk -l
Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11763    94486266   83  Linux
/dev/sda2           11764       12137     3004155    5  Extended
/dev/sda5           11764       12137     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

```

```

user@laptop:~$ sudo gedit /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c22244d3-70f9-432b-941b-5798645befb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0db85f4c-38b0-414c-8e5a-c24b31f0e011 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1   /media/windows   vfat   iocharset=utf8,umask=000   0   0

```

:confused:

I know others still have this problem, so it may be of use to them if this gets resolved.

---

### Post by chalex on 2007-05-02
Your settings seem fine.  What doesn't work?  Does the directory /media/windows exist?

---

### Post by suki on 2007-05-02
> **chalex said:**
> Your settings seem fine.  What doesn't work?  Does the directory /media/windows exist?

```

bash: cd: /media/windows: No such file or directory

```

To be more precise, I cannot gain access to what's on the external hard drive. It does not mount to the desktop. I cannot transfer fires from it to my laptop.

---

### Post by confused57 on 2007-05-02
Maybe you need to make a directory:
```
sudo mkdir /media/windows
```

after making the directory, you might need to:
```
sudo mount -a
```

---

### Post by suki on 2007-05-02
Okay, so I followed confused57's instuctions and got the following
```
>>  fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

 >>sudo mount -t vfat /dev/sdb1 /media/windows
mount: /dev/sdb1 already mounted or /media/windows busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/windows

```

Sorry, for the slowness. I can now access what's on the external hard drive. It doesn't have an icon that shows up on the desktop that's it has mounted but that's fine. 
Thanks so much everyone!

---

