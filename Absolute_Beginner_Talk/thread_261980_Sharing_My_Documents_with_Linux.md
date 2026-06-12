---
title: "Sharing My Documents with Linux"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Viral on 2006-09-21
Hello!

I partitioned my Hard Drive (redid everything, reinstalled Windows, Linux) and a Duel Boot.

Everything is working amazingly! UBUNTU ROCKS!

Anyway, I made a partition just for my media (My Documents), and I'm having a problem. The My Documents folder is moved to the "F:" partition. So, on Windows XP everything is perfect!

But...

When I open Linux up, I try to write or delete something on the F drive, the My Music, My Videos folders (Those are the only two folders that are protected). I booted back to Windows, right clicked on "My Music", went down to "Properties", and it says it's Read-Only.

I tried to unbox it, and it did, I clicked Done (and Apply). Then, I repeated the right click and Properties to make sure that it wasn't still "READ-ONLY", and it was. I've tried everything, and it won't work.

I can't write to My Music, or My Videos.

Please help!

Thanks!

---

### Post by Najand on 2006-09-21
Is the filesystem of your share partition "ntfs"? You cannot write to "ntfs" filesystem because it is not supported by linux... The most convinient way to solve your problem is to move your data to somewhere else and format your share partition as FAT32... It can be recognized (Also read/write) by Windows and can be read/write using ubuntu (as well as other distributions of linux.).

---

### Post by Viral on 2006-09-21
The Filesystem IS FAT32.

---

### Post by Najand on 2006-09-21
Oh... Then there is a matter with mounting;
Can you capy/paste your /etc/fstab file here?
you can see it using:
```

cat /etc/fstab

```

---

### Post by Viral on 2006-09-21
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Viral on 2006-09-21
A better image:

[http://img176.imageshack.us/img176/2378/screenshotzx3.png](http://img176.imageshack.us/img176/2378/screenshotzx3.png)


My Media drive is HD5

---

### Post by gils0040 on 2006-09-21
i know this isnt relavent to you but fyi it is possible to write to ntfs partitions under linux (just search the forums for ntfs-3g).
as for your problem you may want to copy this into terminal
"sudo chmod -R 777 /media/hda5"
I have found that often times it is incorrect permissions of the mount point and not incorect mount settings that dont allow write access. if thats the case the code should fix it. good luck

---

### Post by Najand on 2006-09-21
There are two fat partitions? which one has the problem?

---

### Post by Viral on 2006-09-21
Hmmm, that didn't work ;(

I don't know what's wrong.

---

### Post by gils0040 on 2006-09-21
give this a try [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Najand on 2006-09-21
Can you change the "umask" of your vfat partition and mount your partition using:
> sudo mount -o remount PARTITIONNAME

---

### Post by Viral on 2006-09-21
That didn't work, I just tried it :(

---

