---
title: "Upgrade to -11 mixed up fstab"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-11
Sorry if this post seems disjointed, but I'm not even sure how to ask these questions.
After many hassles I have the -11 upgrade running. However, it changed the partition names of the Ubuntu EXT3 partitions and mis-mounted a FAT32, plus the swap partition is inactive.

I fixed the re-naming of the partitions for GRUB, and can now boot. 

Right now dev/hda9 is mounted at /media/hda10. I change it to /media/hda9 through the terminal but it doesn't stick when rebooting. So I need fix this.

Note that dev/hda10, which is /home, is shown as vfat and is mounted at /media/hda10 rather than as /home

How do I make the swap partition active?

Is there a way to have the system automatically rebuild fstab? 

Here is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda8
UUID=9f8d6e0b-f3b0-40e3-9e26-b3dcc3f84410 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda11
UUID=063da081-4ed5-4c75-a789-81de30b946bb /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/hda1 /media/hda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda10
UUID=4598-9D46 /media/hda10 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hda5 /media/hda5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hda6 /media/hda6 auto users,uid=100,gid=1000,umask=000 0 0
/dev/hda7 /media/hda7 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc1 /media/hdc1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hdc5
UUID=0000-0DAA /media/hdc5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc6 /media/hdc6 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc7 /media/hdc7 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc8 /media/hdc8 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc9 /media/hdc9 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda9
UUID=ee1e76a5-e473-44e6-962f-aec863a5ce92 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda10 /media/hda10 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 0

```

Here is fdisk -l
> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         610     4899793+   b  W95 FAT32
/dev/hda2             611       19457   151388527+   f  W95 Ext'd (LBA)
/dev/hda5             611        5325    37873206    b  W95 FAT32
/dev/hda6            5326       10040    37873206    b  W95 FAT32
/dev/hda7           10041       14749    37825011    b  W95 FAT32
/dev/hda8           19327       19457     1052226   82  Linux swap / Solaris
/dev/hda9           14750       15532     6289416    b  W95 FAT32
/dev/hda10          15533       17559    16281846   83  Linux
/dev/hda11          17560       19326    14193396   83  Linux

If you need more info, just ask. I'd like to get this resolved.

---

### Post by jpeddicord on 2007-02-11
Here is my /etc/fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0df4eb29-0b0e-4e22-87e9-ccd49f89caaa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=87ebb7e0-caa9-4aff-b7a0-08c635f4b258 /home           ext3    defaults        0       2
# /dev/hda1
UUID=7b951aba-a1e7-434e-a3b3-3e992cba10d8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```Your fstab and mine aren't very different in terms of the swap line, so it should work correctly. Check to see if the update made backup files in /etc. It might be named /etc/fstab~.

Jacob

---

### Post by Patrick K on 2007-02-11
It doesn't appear the upgrade made a backup. I'm hesitant to jump in and make changes since I don't understand what the changes might do. As you can see there are a lot of partitions and several need to be changed. 

1) hda9 needs to mounted at media/hda9, it is mounted at hda10. 

2) hda10 is /home. in my fstab it is shown as vfat and is mounted at hda10 but is actually EXT3 and is /home. gparted shows this correctly (both EXT3 and /home)

3) hda8 is the swap but is not shown in fstab as such. hda9 is shown as swap but it isn't. gparted shows hda8 correctly has swap, but swap is turned off. I can turn is on with gparted but it doesn't stick between sessions.

4) hda11 is shown as /home. It actually is "/". gparted shows it properly.

---

### Post by taurus on 2007-02-11
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=ee1e76a5-e473-44e6-962f-aec863a5ce92 none swap sw 0 0
```
with this one.

```
/dev/hda8   none   swap   sw   0   0
```
Save it and reboot.  Then see if your swap partition is activated or not.

```
free
```
Otherwise, post the output of this command.

```
sudo fdisk -l
```

---

### Post by Patrick K on 2007-02-11
Yes, that set the swap partition active between sessions. Thanks.

Any thoughts on the other issues?

---

