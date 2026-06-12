---
title: "Can't mount Windows partition within Ubuntu"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-01-28
Hi Guys,

Having followed the advice in [this thread]("http://www.ubuntuforums.org/showthread.php?t=339803") and then had problems with permissions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=347060"), I am now left unable to mount my Windows partition (hda1).

If I type 'sudo mount -a' I get the following:

```

mount: special device /dev/disk/by-uuid/22A45277A4524D83 does not exist

```

Here's the result of 'sudo fdisk -l'

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2167     2048287+  82  Linux swap / Solaris
/dev/hda3            2168        5991    30716280   83  Linux
/dev/hda4            5992        7296    10482412+  83  Linux

```

Here's a copy of '/etc/fstab'

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5e656ecc-b906-44b3-8645-334114dcdf33 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=c74cc6aa-97ba-40d3-b857-91cec17dd797 /home           ext3    defaults        0       2
# /dev/hda1
UUID=22A45277A4524D83 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       1
# /dev/hda2
UUID=94e5c730-a404-4d91-8c55-bb03a517a61d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

And here's the result of 'cd /' followed by 'ls -l'

```

total 112
drwxr-xr-x   2 root root  4096 2007-01-16 12:22 bin
drwxr-xr-x   3 root root  4096 2007-01-16 12:25 boot
lrwxrwxrwx   1 root root    11 2007-01-15 15:36 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13540 2007-01-28 15:53 dev
drwxr-xr-x 113 root root  4096 2007-01-28 16:22 etc
drwxr-xr-x   5 root root  4096 2007-01-16 14:57 home
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 initrd
lrwxrwxrwx   1 root root    33 2007-01-15 16:19 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  17 root root  8192 2007-01-26 12:11 lib
drwxr-xr-x   2 root root 49152 2007-01-15 15:35 lost+found
drwxr-xr-x   6 root root  4096 2007-01-28 16:22 media
drwxr-xr-x   2 root root  4096 2006-10-19 23:49 mnt
drwxr-xr-x   6 root root  4096 2007-01-26 18:56 opt
dr-xr-xr-x 110 root root     0 2007-01-28 15:50 proc
drwxr-xr-x  15 root root  4096 2007-01-28 16:53 root
drwxr-xr-x   2 root root  4096 2007-01-26 12:11 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 srv
drwxr-xr-x  11 root root     0 2007-01-28 15:50 sys
drwxrwxrwt  17 root root  4096 2007-01-28 17:10 tmp
drwxr-xr-x  13 root root  4096 2007-01-26 11:31 usr
drwxr-xr-x  15 root root  4096 2006-10-25 14:39 var
lrwxrwxrwx   1 root root    30 2007-01-15 16:19 vmlinuz -> boot/vmlinuz-2.6.17-10-generic

```

I would appreciate some help getting this sorted, if there's any other information needed please let me know.

Thanks.

---

### Post by taurus on 2007-01-28
Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```

UUID=22A45277A4524D83 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       1
```
with this line.

```

/dev/hda1   /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       0
```
Save it and reboot.

---

### Post by ComplexNumber on 2007-01-28
i've gathered that the UUID uniqely identifies a particular user(or is a particular computer?), so i guess because the user groups were changed, this would make that particular UUID to be inconsistent with the present state. therefore the UUID stated in the fstab would not be the same as mrcatsworth's present UUID (after the change of usergroup)

---

### Post by Catsworth on 2007-01-28
> **taurus said:**
> Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```

UUID=22A45277A4524D83 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       1
```
with this line.

```

/dev/hda1   /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       0
```
Save it and reboot.

That worked a treat, thanks very much for that.  

I really appreciate the help, if you wouldn't mind could you possibly explain what happened there and how your fix sorted it out?  I'm really new to all of this so the more I can learn the better.

Thanks again.

---

### Post by Catsworth on 2007-01-28
> **ComplexNumber said:**
> i've gathered that the UUID uniqely identifies a particular user, so i guess because the user groups were changed, this would make that particular UUID to be inconsistent with the present state. therefore the UUID stated in the fstab would not be the same as mrcatsworth's present UUID (after the change of usergroup)

Hmmm....

That seems to make a lot of sense.  What I don't get though is how changing the reference from one containing the UUID for mrCatsworth to /dev/hda1 could be right in that case.

Surely if the line needs my UUID then replacing it with a pointer to the HDD makes little sense.

Of course, it could just make no sense because I'm a seasoned Windows user and therefore no nothing about the way that things should *really* work :)

Thanks again guys, this is all a really good learning experience.

---

### Post by ComplexNumber on 2007-01-28
i don't really understand about UUID's, so your guess is as good as mine :D. my ntfs mount point in fstab has an ntfs partition, and i have no problems with permissions (except i can't write to the windows partition, but thats to be expected).

---

### Post by hyper_ch on 2007-01-28
the UUIDs are unique hardware identifiers... so it will always use that specivied hardware (in yourcase the harddisk/partition). However the location of a harddisk can change.. e.g. if you change cable setup... then you will need to adjust everything if you use like /dev/hdX...
If you use UUIDs you aren't required to do so.

---

