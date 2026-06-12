---
title: "File system error after install"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by svoltmer on 2008-01-26
After a install when I boot to Ubuntu it gets to checking the file system and then throws an error and goes into shell mode. I can still start Ubuntu with ctrl +d but I wonder what I can check to correct the file system? Thanks!

---

### Post by kellemes on 2008-01-26
> **svoltmer said:**
> After a install when I boot to Ubuntu it gets to checking the file system and then throws an error and goes into shell mode. I can still start Ubuntu with ctrl +d but I wonder what I can check to correct the file system? Thanks!


What's the error?

---

### Post by taurus on 2008-01-26
It's real important to know the exact error message is.  Otherwise, you probably need to fsck the partition where / is.

```
fsck -y /dev/sdaX
```

---

### Post by svoltmer on 2008-01-26
What I am seeing is :

fsck died with exit status 8

*File system check failed
A log file is being saved in /var/log/fsck/checkfs  (note: this dir doesn't seem to exist)

Please repair the file system manually

Then the shell starts and I get this:

bash: no job control in this shell
bash: groups: not in this shell
bash: lesspipe: not in this shell
bash: Command: not in this shell
bash: The: not in this shell
bash: dircolors: not in this shell

Is that any help?

---

### Post by taurus on 2008-01-26
Try to run fsck it by hand then as I've described in my previous post.  Replace /dev/sdaX with the actual partition where / is.

---

### Post by svoltmer on 2008-01-26
I get a warning about running fsdk on a mounted filesystem. is it OK to run?

---

### Post by taurus on 2008-01-26
If the partition is mounted, do not run fsck on it.  However, don't you get an error message about unable to fsck your root filesystem and it drops you into a shell, telling you to fsck it manually?

Otherwise, you can do it from the LiveCD.

---

### Post by svoltmer on 2008-01-28
Here is some info I didn't notice during boot:

/dev/sdb5: 120918/1627688 clusters
fsck.ext3: unable to resolve 'UUID=0559e-e9a4-11d8-993d-d462dee94e6c'
dev/sdc5: clean, 11/6111232 files 237855/1207384 blocks
fsck died with exit status 8

so is the dev/sdb5 the one fsck is having problems with?
If so it is a FAT32 partition on another physical drive that has Windows Game files.

What can I do to make Ubuntu boot without the fsck error on that drive? Since they are Windows files? Thanks!

---

### Post by taurus on 2008-01-28
You need to edit /etc/fstab and make sure the last two digits for /dev/sdb5 are 0's--0 0.

```
gksudo gedit /etc/fstab
```
Please do not run fsck for fat32 or ntfs filesystems.

---

### Post by svoltmer on 2008-01-28
I opened it up and I see the device listed as:

# /dev/sdc1
UUID=62f4a2fa-7b9d-45ef-a7c0-f937877c2744 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4AFC7FF3FC7FD7A1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=5ad0559e-e9a4-11d8-993d-d462dee94e6c /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=faf02063-57fb-4b13-aa04-f89b6a75ffe9 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=412E-4B31  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=6648256F48253EE5 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=3EAF-084E  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=3EAF-084E  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=e228feb9-e0f0-47c3-9499-95ea4411e313 /sg1            ext3    defaults        0       2
# /dev/sdc2
UUID=5291d416-6125-4664-b9cb-494ff88f8eff none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

What should be 00?

The one that  fsck stated: unable to resolve "UUID=xxxxx" looks like it is /dev/sda3?
I wonder why the error happend after /dev/sdb5 during the boot then?

---

### Post by taurus on 2008-01-28
> **svoltmer said:**
> I opened it up and I see the device listed as:

# /dev/sdc1
UUID=62f4a2fa-7b9d-45ef-a7c0-f937877c2744 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4AFC7FF3FC7FD7A1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sda3
UUID=5ad0559e-e9a4-11d8-993d-d462dee94e6c /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=faf02063-57fb-4b13-aa04-f89b6a75ffe9 /media/sda4     ntfs    defaults,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sda5
UUID=412E-4B31  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sdb1
UUID=6648256F48253EE5 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sdb5
UUID=3EAF-084E  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sdb6
UUID=3EAF-084E  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       **[COLOR="Blue"]1[/COLOR]**
# /dev/sdc5
UUID=e228feb9-e0f0-47c3-9499-95ea4411e313 /sg1            ext3    defaults        0       2
# /dev/sdc2
UUID=5291d416-6125-4664-b9cb-494ff88f8eff none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

What should be 00?

The one that  fsck stated: unable to resolve "UUID=xxxxx" looks like it is /dev/sda3?
I wonder why the error happend after /dev/sdb5 during the boot then?

Have you moved or rearranged your partition table lately?  Look at the output of this command to make sure that the UUIDs for the partitions are matching up with what you have in /etc/fstab.

```
ls -la /dev/disk/by-uuid
```

---

### Post by svoltmer on 2008-01-28
drwxr-xr-x 2 root root 240 2008-01-28 16:08 .
drwxr-xr-x 6 root root 120 2008-01-28 11:07 ..
lrwxrwxrwx 1 root root  10 2008-01-28 16:08 3EAF-084E -> ../../sdb6
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 412E-4B31 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 4AFC7FF3FC7FD7A1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 5291d416-6125-4664-b9cb-494ff88f8eff -> ../../sdc2
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 5ad0559e-e9a4-11d8-993d-d462dee94e6c -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 62f4a2fa-7b9d-45ef-a7c0-f937877c2744 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 6648256F48253EE5 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 861CC4531CC44043 -> ../../sdc4
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 e228feb9-e0f0-47c3-9499-95ea4411e313 -> ../../sdc5
lrwxrwxrwx 1 root root  10 2008-01-28 11:07 faf02063-57fb-4b13-aa04-f89b6a75ffe9 -> ../../sda4

Before the install of Ubuntu I had joined 2 partitions in windows on the sdb drive but not the sba drive. It does appear that the two list are matching up UUID's (sort of, there is no /dev/sdc3 or /dev/sdc4 on fstab list as well as showing sda3 as being formated with ext3, but it is not. What should I do?

---

