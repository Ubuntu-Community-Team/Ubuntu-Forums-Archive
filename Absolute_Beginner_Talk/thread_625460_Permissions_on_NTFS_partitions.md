---
title: "Permissions on NTFS partitions"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by cherry316316 on 2007-11-28
I have mounted my windows drive in 
"/media/c , /media/d , /media/e"
when i goto /media and do ls -l
it gives me 
```

drwxrwx---  9 root plugdev 16384 1969-12-31 16:00 c
drwxrwx--- 22 root plugdev 16384 1969-12-31 16:00 d
drwxrwx---  8 root plugdev 16384 1969-12-31 16:00 e

```

i tried to change the permission, so that the normal user can also use it for read and write
by using command
chmod ugo+rwx /media/d 
and I also tried to change the owner of /media/d by becoming a root.
but its not working.

any idea , how to change the file system permission for windows partition.

Thanks

---

### Post by bodhi.zazen on 2007-11-28
Permissions of FAT and NTFS drives are set at the time of mounting.

So ...

mount /dev/hda1 /media/c -o uid=1000,gid=100,umask=007

Or update fstab (/etc/fstab)

> /dev/hda1  /media/c  users,uid=1000,gid=100,umask=100  0 0 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

