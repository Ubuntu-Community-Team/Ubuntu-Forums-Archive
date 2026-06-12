---
title: "fat32 folder permissions"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by mevan on 2007-06-19
Hello!

I have recently installed a fresh copy of ubuntu feisty on my pc
I have this problem regarding one of my drives: It is a FAT32 drive containing multimedia files and it mounts automatically at boot. 
Though I can read/write almost in every dir in the drive and I can create new directories and files, there are some dirs appearing with a lock icon next to them and I only have read access to them. I tried to change the specific permissions of those dirs but i get an "operation not permitted" error.

While I was using ubuntu dapper, I had rw access to all the dirs of the drive with no problems.

Any help?

ps: after some reboots and playing with fstab (and only with fstab), one of these directories became fully accessible. The funny thing is that the final (working) version of the fstab is the same with the original one!

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=de4a037e-0a68-4ddb-a4f6-1c6e2b05ae53 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=2ec8e24e-fd0c-427a-846a-08597aad09d7 /home           ext3    defaults        0       2
# /dev/sda3
UUID=1AE41978E41956FB /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=01C67DDC5E2380E0 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
[COLOR="Red"]# /dev/sdb5[/COLOR]
[COLOR="Red"]UUID=0000-0EA5  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1[/COLOR]
# /dev/sda2
UUID=96ff2575-368c-4915-935d-8be6df34a570 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by benfindlay on 2007-06-20
I take it you formatted the ubuntu partition and replaced it with a newer version?

If this is so, I suspect that the new ubuntu version is detecting these partitions as being owned by the old installation.

Not sure how you have already gona about changing the partitions, but I would recommend typing ```
sudo chown [your_username] /drive/location
```

If that doesn't work, launch a terminal and type ```
gksudo nautilus
``` but be VERY careful that you don't change anything else while that nautilus session is running, as you have TOTAL power over everything until you close nautilus down. Make a mistake and you could trash the entire OS by accident...

But on a more happy note heres a copy of my fstab for comparison!

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0


Hope this helps

---

### Post by mevan on 2007-06-20
Hi

Yes I formatted the / partition and installed a fresh ubuntu copy on it.

The problem is not the ownership of the entire partition but the permissions of some specific folders in the partition. I cannot remember when I created them but I think I did it under windows 98 (a long long time ago...) and up to now I had no problem accessing them (before ubuntu 7.04 I had ubuntu 6.06 and before that I had fedora 4).

I did the *chown* exactly as you mention but with "operation not permitted" results. The same happens when I try to change permissions from a *sudo nautilus*... I'll try the fstab settings when I get to home and I'll let you know if anything happens...

thanx!

---

### Post by mevan on 2007-06-29
Nothing... I still have permission to the whole drive *except* some folders in it...

Anything else to try?

---

### Post by woyzeckswoe on 2007-07-28
i've got exactly the same problem, and it sucks because i can't save firefox options!!!

i'd really love to solve this problem

thanks all

---

### Post by woyzeckswoe on 2007-07-28
solved!

just changed etc/fstab umask=007 to 000

i love ya all!

---

