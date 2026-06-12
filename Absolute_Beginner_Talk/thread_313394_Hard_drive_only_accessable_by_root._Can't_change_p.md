---
title: "Hard drive only accessable by root. Can't change permissions"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Zensunni on 2006-12-06
I can mount and access a hard drive in root, but I can't let normal users use it. This is my HD setup:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3837    30820671    7  HPFS/NTFS
/dev/sda2            3838        7674    30820702+  83  Linux
/dev/sda3            7675        7805     1052257+  82  Linux swap / Solaris
/dev/sda4            7806       14593    54524610    7  HPFS/NTFS

The hard drive I'm trying to share with all users is the /dev/sda4. I've tried chown and chmod, but they both do nothing. All I wanna do is play some movies that are on the sda4 drive and not worry about being root all the time.

This is my fstab:
=====================================================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bb7ab5d0-1bd1-428a-9d58-ba921065cc50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D230173530172051 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=e301b40b-9b38-4637-96e6-3f91e1360c3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

=====================================================================

Looks all messed up, if you ask me. Like, what are these all about?:
# /dev/sda2
UUID=bb7ab5d0-1bd1-428a-9d58-ba921065cc50 /               ext3    
UUID=D230173530172051 /media/sda1     ntfs   
UUID=e301b40b-9b38-4637-96e6-3f91e1360c3a none            swap    sw

This seems like a pretty simple thing, but for some reason, nothing is working. Is there a different set of rules for permissions on a mount point or something I'm missing?

Thanks for any help

---

### Post by aysiu on 2006-12-06
Read this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by zedfrugnug on 2006-12-16
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


I have this problem with external HD SDA1.
Seems it's owned by root because I left it plugged in while installing dapper:confused: 

I tried loggin in as root, but even then couldn't change much in the permissions;
couldn't change permissions for users; couldn't change the owner, or owner group:confused: 

I'll try remounting this like suggested, but this problem seems to me (being the noob that I am) like a bug; Why would I not have permissions to this HD?
I think little things like things like this, that go all wrong, scares off newbies:(

---

### Post by aysiu on 2006-12-16
> **zedfrugnug said:**
> 
I'll try remounting this like suggested, but this problem seems to me (being the noob that I am) like a bug; Why would I not have permissions to this HD?
I think little things like things like this, that go all wrong, scares off newbies:( Yes, it's annoying, which is why I don't suggest Ubuntu to absolutely new users. I suggest Mepis instead.

---

### Post by zedfrugnug on 2006-12-16
I tried The discription of psychocats for my external HD; but this didn't work. edit: didn't change anything; root is still owner

What I did:

sudo umount /media/SDA1

sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        1116      771120   82  Linux swap / Solaris
/dev/hda3            1117        1881     6144862+  83  Linux
/dev/hda4            1882        4864    23960947+   f  W95 Ext'd (LBA)
/dev/hda5            1882        4864    23960916    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

sudo mkdir /WD

sudo cp /etc/fstab /etc/fstab_backup

sudo nano /etc/fstab

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0    1   
/dev/hda1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0   $
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
_/dev/sda1       /WD vfat iocharset=utf8,umask=000 0 0_ <--added

sudo mount -a

reboot

Anyone? aysiu? What did I do wrong?

---

### Post by aysiu on 2006-12-16
Root will **always** appear to be the "owner" of a FAT32 partition because FAT32 doesn't support permissions. But if you have that line, you should be able to read/write to it, regardless.

---

### Post by zedfrugnug on 2006-12-17
Thanks for helping.

Actually I'm having problems with one folder in particular; my music folder.
To this folder I can't write or delete. Properties tells me I don't have permissions. 
To the rest of the external HD I can.
All of the HD is owned by root, so I can't change the permissions.

I use dapper dual boot with xp.  On earlier installations of dapper I did somehow lose permissions to write to my music folder after using it on xp. I don't remember the owner of the disk then, but I could change permissions, so I could write to it again. 

Could It be that the disk is not an actual FAT32, but a something like a simulated FAT?
I think I remember reading this somewhere.

---

### Post by chettyk on 2006-12-17
> **zedfrugnug said:**
> _/dev/sda1       /WD vfat iocharset=utf8,umask=000 0 0_ <--added


See if changing that one line in fstab helps:
```
/dev/sda1       /WD vfat **rw**,iocharset=utf8,umask=000 0 0
```

---

### Post by zedfrugnug on 2006-12-17
> **chettyk said:**
> See if changing that one line in fstab helps:
```
/dev/sda1       /WD vfat **rw**,iocharset=utf8,umask=000 0 0
```

Didn't do anything :(

---

### Post by chettyk on 2006-12-17
Try making the following change:
```
/dev/sda1       /WD vfat noauto,users,rw,iocharset=utf8,umask=000 0 0
```

Save the file and reboot the computer. That way, all parititions will be unmounted and then remounted in accordance with the fstab changes.

This time, the windows partition will not be automatically mounted. Instead, the user who wants to access the partition will need to mount it:
```
mount /WD
```

**[SIZE="2"]DON'T[/SIZE]** use 'sudo' before the mount command.

I don't have a vfat partition on any of my computers and so there is no way I can test what my suggestion. If it doesn't work, I'd suggest you try a Google search:
[http://www.google.com/search?hl=en&q=linux+mount+vfat+read+write&btnG=Search&meta=](http://www.google.com/search?hl=en&q=linux+mount+vfat+read+write&btnG=Search&meta=)

Good luck!

---

### Post by zedfrugnug on 2006-12-17
> **chettyk said:**
> Try making the following change:
```
/dev/sda1       /WD vfat noauto,users,rw,iocharset=utf8,umask=000 0 0
```

Save the file and reboot the computer. That way, all parititions will be unmounted and then remounted in accordance with the fstab changes.

This time, the windows partition will not be automatically mounted. Instead, the user who wants to access the partition will need to mount it:
```
mount /WD
```

**[SIZE="2"]DON'T[/SIZE]** use 'sudo' before the mount command.

I don't have a vfat partition on any of my computers and so there is no way I can test what my suggestion. If it doesn't work, I'd suggest you try a Google search:
[http://www.google.com/search?hl=en&q=linux+mount+vfat+read+write&btnG=Search&meta=](http://www.google.com/search?hl=en&q=linux+mount+vfat+read+write&btnG=Search&meta=)

Good luck!

Thanks.

It seemed to work; after mounting the partition again it was owned by me.
However on rebooting again ownership was back to root...](*,) 

I think I'll let it be this way for now; next time I install ubuntu I'll be sure not to mount my external HD with the installation.

---

