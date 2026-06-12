---
title: "How can I set certain commands to autorun on startup?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-04
I'm trying to get a command to auto mount two of the hard disk's partitions on boot-up so I don't have to do it manually each time I boot-up.

Do you know how I could do this? 
Thanks!

---

### Post by spin2cool on 2007-05-04
You can add startup commands in System > Preferences >Sessions

---

### Post by Xarok on 2007-05-04
I forgot to mention that I'm using KDE...

---

### Post by mcduck on 2007-05-04
> **Xarok said:**
> I'm trying to get a command to auto mount two of the hard disk's partitions on boot-up so I don't have to do it manually each time I boot-up.

Do you know how I could do this? 
Thanks!

Automounting of hard disks is best done by adding them to /etc/fstab.

If you need help doing that, post the outputs of 'cat /etc/fstab', sudo fdisk -l' and 'ls -la /dev/disk/by-uuid' here & tell what partitions you wish to mount and where. :)

---

### Post by Xarok on 2007-05-04
> **mcduck said:**
> Automounting of hard disks is best done by adding them to /etc/fstab.

If you need help doing that, post the outputs of 'cat /etc/fstab', sudo fdisk -l' and 'ls -la /dev/disk/by-uuid' here & tell what partitions you wish to mount and where. :)

well I figured out how to mount via GUI (KDE):
System Settings > Advanced > Disk & File systems > Administrator Mode > right-click"Modify" > fill out mount point > check "enable at start-up"

---

### Post by Xarok on 2007-05-04
Here's that info anyways 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda4
UUID=2c390119-7f1f-4bd5-9d51-79dfaf62e636 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=8bc490a1-7065-4fc8-a937-8567e4b03580 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda6 /home/daniel/Desktop/yuzu auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/hda3 /home/daniel/Desktop/tenshi auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0



total 0
drwxr-xr-x 2 root root 120 2007-05-04 00:21 .
drwxr-xr-x 6 root root 120 2007-05-04 00:21 ..
lrwxrwxrwx 1 root root  10 2007-05-03 22:24 2c390119-7f1f-4bd5-9d51-79dfaf62e636 -> ../../hda4
lrwxrwxrwx 1 root root  10 2007-05-04 00:21 47A5509958136181 -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-05-04 00:21 8A4A2600085BDC23 -> ../../hda6
lrwxrwxrwx 1 root root  10 2007-05-03 22:24 8bc490a1-7065-4fc8-a937-8567e4b03580 -> ../../hda5






/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 96731201  (977.0k)  NewWorld bootblock
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1  96468993 @ 262208    ( 46.0G)  HFS
/dev/hda4         Apple_UNIX_SVR2 untitled            17459201 @ 96733155  (  8.3G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                  969272 @ 116240968 (473.3M)  Linux swap
/dev/hda6               Apple_HFS untitled             2048612 @ 114192356 (1000.3M)  HFS
/dev/hda7              Apple_Free Extra                 262144 @ 64        (128.0M)  Free space

Block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0

---

