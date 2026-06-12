---
title: "Unmount primary hard disk when Boot up system"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by nb123 on 2007-09-13
Hi, I have ubuntu installed on my external hard disk, when I boot it up, it mounts 3 partitions from my primary hard disk and 3 more from my external. I want to unmount all of them but the fat32 on the external hard disk. How do I make sure this happens everytime I boot ubuntu? I've tried to read up on this in the tutorial, but I don't think I'm understanding it clearly... I tried to right click and select a new mount point for one of the partitions, but when I rebooted it, it said that it couldn't mount it cos the mount point was wrong or something, I tried to mount it at '/media/abc' .... 

1) Should I have tried to mount it at '/dev/abc'? 

2) Also, I know that I can use the 'sudo umount .....' command to unmount the partitions when I'm in ubuntu, but how do I make this unmounting happen everytime I boot the system?

---

### Post by felicity on 2007-09-13
/etc/fstab is the file containing the drive information that is loaded on boot. You may want to comment out the lines for the drives you don't want mounted on boot.

---

### Post by nb123 on 2007-09-13
Thanks, I'm off to try this

---

### Post by tszanon on 2007-09-13
> **nb123 said:**
> 1) Should I have tried to mount it at '/dev/abc'?
No. It's correct to mount in in /media/abc. But you have to make sure that this directory exists. I think that this error message you're seeing is because the folder doesn't exist.

---

### Post by nb123 on 2007-09-13
Ohhh ok I'm understanding this better, so I should create a folder first then mount it there... ok, but I can't seem to create a folder in the /media folder? Do I need root permission or something? Why is it that I mounted a partition at /backtrack and it just created the folder automatically for me, but I couldn't do this in /media/abc? I tried to go to the /etc folder and view the file fstab but there's also another file fstab.pre-uuid, when I opened fstab, I got the following :---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sdb1
UUID=550dcdce-4296-40af-a95f-5f94873d7080 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sdb3
UUID=22822267-5db7-4007-b911-ab2089b163cf /backtrack      ext3    defaults        0       2


# /dev/sda1
UUID=07D7-0102  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda2
UUID=9ED020C3D020A38D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda5
UUID=07D7-0102  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdb2
UUID=ed3e91f8-ac4a-420c-b6bf-98f8dc5c9b58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0




fstab.pre-uuid ---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sdb1
UUID=550dcdce-4296-40af-a95f-5f94873d7080 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sdb3
UUID=22822267-5db7-4007-b911-ab2089b163cf /backtrack      ext3    defaults        0       2

# /dev/sda1
UUID=07D7-0102  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda2
UUID=9ED020C3D020A38D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda5
UUID=07D7-0102  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdb2
UUID=ed3e91f8-ac4a-420c-b6bf-98f8dc5c9b58 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM


I don't seem to see where /dev/sdb5 and /dev/sdb6 are, out of which /dev/sdb6 is my fat32. Currently I mounted my fat32 partition at /media/sharedxp, but like you said, the folder doesn't exist, so how can I rectify this mistake?

---

### Post by tszanon on 2007-09-13
> **nb123 said:**
> Ohhh ok I'm understanding this better, so I should create a folder first then mount it there... ok, but I can't seem to create a folder in the /media folder? Do I need root permission or something?
Yes:
```
sudo mkdir /media/abc
```

> **nb123 said:**
> Why is it that I mounted a partition at /backtrack and it just created the folder automatically for me, but I couldn't do this in /media/abc?
I don't know. Based on your fstab, I know you're using Edgy or Feisty. Since I use Dapper, I don't know if they changed anything regarding this.

> **nb123 said:**
>  I tried to go to the /etc folder and view the file fstab but there's also another file fstab.pre-uuid, when I opened fstab, I got the following :---
(...)
I don't seem to see where /dev/sdb5 and /dev/sdb6 are, out of which /dev/sdb6 is my fat32. Currently I mounted my fat32 partition at /media/sharedxp, but like you said, the folder doesn't exist, so how can I rectify this mistake?
I would not consider fstab.pre-uuid. As far as I know, the file used still is /etc/fstab.
To the point: if you're mounting /dev/sdb6 in /media/sharedxp, then what you need to do is just create the folder:
```
sudo mkdir /media/sharedxp
```
and it's gonna work:
```
sudo mount /dev/sdb6 /media/sharedxp
```
If you want it to be automatically done every boot, I'm afraid I can't help you, but do a little search and you will find out how to do it.
And, if you don't want to mount any partitions from /dev/sda, then just comment the lines, like this:
```
# /dev/sda1
#UUID=07D7-0102 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1

# /dev/sda2
#UUID=9ED020C3D020A38D /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda4 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1

# /dev/sda5
#UUID=07D7-0102 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1

```

Hope it helps.

---

