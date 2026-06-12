---
title: "How do I mount new ext3 partition? [Resolved]"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by El Jamo on 2007-04-01
Hi,

This is definitely an absolute beginner quesion.  I'm on an IBM R51 laptop that is booting into three operating systems, 2 of which are WinXP and the other is Xubuntu Edgy.  (One WinXP is filled with school programs and boots painfully slow.  I never use it, but keep it around b/c sometimes I have to use it for certains schoolwork.  The other WinXP is a very basic install that only runs Firefox and Warcraft III.  I only use it to play Warcraft).  When I first set up my system, I thought that I might want a fat32 partition to swap data from linux to WinXP, so I made a 20GB fat32 partition.  While working with some audio files, I realized that fat32 has some restrictions on filenames that I couldn't work around, and so I needed an ext3 partition that I could use as a workspace.  So I used gparted to resize my fat32 partition and created a 5GB ext3 partition from the newly-freed space.

Wow, too much description so far.  Anyway, now I need to know 2 things:
1. How do I mount the new 5GB ext3 partition I've made?  I'd like to mount it at /workspace
2. How do I make it mount at bootup?  I'm guessing this has to do with my fstab file.

Here's some additional info:

Output of "sudo fdisk -l"
```
james@james:/$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4741    35841928+   7  HPFS/NTFS
/dev/hda2            4742       10337    42305729    f  W95 Ext'd (LBA)
/dev/hda5            4742        6096    10243768+   7  HPFS/NTFS
/dev/hda6            6097        7963    14105038+   b  W95 FAT32
/dev/hda7            8681        9222     4097488+  83  Linux
/dev/hda8            9223       10120     6788848+  83  Linux
/dev/hda9           10121       10337     1640488+  82  Linux swap / Solaris
/dev/hda10           7963        8680     5421906   83  Linux

Partition table entries are not in disk order
james@james:/$ 

```

Contents of /etc/fstab
```
james@james:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=b5fee4b9-c4ff-42ce-8dbe-2cfb9f04dae4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=8ca0123d-4639-4f2d-9563-886b24e3eee7 /home           ext3    defaults        0       2
# /dev/hda6
UUID=7869-52D7  /storage        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=5ACC50F8CC50CFBD /windowsmine    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=00000000447425E1 /windowswake    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda9
UUID=fff652aa-9d06-4089-95ba-27bda63c7b45 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
james@james:/$ 

```

I think my new 5GB ext3 partition is the one at /dev/hda10.

Thank you for any help you can give me

---

### Post by plb on 2007-04-01
To mount it simple do this:

mount -t ext3 /dev/hda(insert number here) /workspace

And yes you are correct you must edit your /etc/fstab and add it in there...something along the lines of:

/workspace           ext3    defaults        0       2

---

### Post by El Jamo on 2007-04-01
Thanks, I'll try that.

Is it possible to be more specific about exactly what goes in fstab?

---

### Post by plb on 2007-04-01
It should be something like:

/dev/hda(number) /workspace ext3 defaults 0 2

First part the partition, 2nd is the mountpoint, 3rd filetype, the rest are just flags to pass which should work fine for you.

---

### Post by aysiu on 2007-04-01
This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by El Jamo on 2007-04-03
Thanks very much for all of the help.  Thanks to you guys, it's working great now.  Btw, aysiu, I appreciate those tutorials on your site.  This is one of several times that those have been very helpful to me.

---

