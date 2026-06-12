---
title: "Unable to mount NTFS partition without ntfs-3g"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by colossus73 on 2007-09-29
Hi,

before upgrading to Gutsy I could double click on the NTFS device icons on the desktop and mount them. Now after the ugrade I get this message:

```
The volume 'Games' uses the ntfs-3g file system which is not supported by your system.
```

I can mount the above partition with the mount command in the terminal but NOT anymore by double clicking on its icon. I don't need write access so I don't want to install ntfs-3g.

How can I mount NTFS partitions by double clicking as I was used to do before the upgrade?

---

### Post by BrownCoal on 2007-09-29
Perhaps the file /etc/fstab isn't configured properly. Can you post the contents of it please?

---

### Post by Obor on 2007-09-29
Look at [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only"). Its well explained there.

---

### Post by colossus73 on 2007-09-29
> **Obor said:**
> Look at [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only"). Its well explained there.

I quote from that URL:
> 
 How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access
Warning: The software you will use is still in Beta. You should not enable it on production machines
    * Read #General Notes 
    * Enable universe. Read #How to apt-get the easy way (Synaptic) 
    * Applications -> Add/Remove -> search for 'NTFS', you should find NTFS Configuration Tool, install it. 
    * Applications -> System Tools -> NTFS Configuration Tool -> Enable Write Support (depending on your device internal/external) 
    * Further troubleshooting is listed at this comprehensive howto thread. 


This info do not apply to me because I CAN mount from the command line but NOT from double-clicking on the partition icon.

---

### Post by colossus73 on 2007-09-29
> **BrownCoal said:**
> Perhaps the file /etc/fstab isn't configured properly. Can you post the contents of it please?

Here it's:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=14e44662-0d3d-4f92-beac-e004832c20e7 /               reiserfs notail          0       1
#/dev/sdb7
/dev/sdb7 /media/sdb7   xfs     defaults        0       2
# /dev/sdb10
UUID=9f48edce-112b-4011-9ea6-b14475a809c0 /media/sdb10    xfs     defaults        0       2
# /dev/sdb5
UUID=e9e4501a-b016-4786-ac6b-4d3697883ee3 /home     xfs     defaults        0       2
# /dev/sdb6
UUID=88956cf5-021f-482b-8ede-a648c569e37e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

192.168.178.21:/home/gt         /media/pentium3/gt      nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media           /media/pentium3         nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hda7      /media/pentium3/hda7    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb1      /media/pentium3/hdb1    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb6      /media/pentium3/hdb6    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb7      /media/pentium3/hdb7    nfs rsize=8192,wsize=8192,timeo=14,intr

```

I think the rows related to the NTFS partitions are missing.

---

### Post by BrownCoal on 2007-09-29
Is the icon still present for the ntfs drive? If so, what message does it give you when you double-click on it?

---

### Post by colossus73 on 2007-09-30
Yes it's still present on the Desktop. When I double click I get two error dialogs one after another. One says:

"Unable to mount "62G Volume":
Failed to determine the mount point for /dev/sda1

and the other one:
Cannot mount volume.
The volume uses the ntfs-3g file system which is not supported by your system.

Before upgrading to Gutsy i was able to mount them by double clicking on it WITHOUT ntfs-3g (infact it's not installed). Do you have any clue?

---

### Post by BrownCoal on 2007-09-30
> **colossus73 said:**
> I think the rows related to the NTFS partitions are missing.

Yes, there doesn't seem to be a line for /dev/sda1. I've added it below. First check that the directory "/media/sda1" exists. If it doesn't then create it with the command "sudo mkdir /media/sda1". Once it exists copy the fstab below and save it into your current one (using sudo).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1 /media/sda1 ntfs defaults,user 0 0 
# /dev/sdb1
UUID=14e44662-0d3d-4f92-beac-e004832c20e7 /               reiserfs notail          0       1
#/dev/sdb7
/dev/sdb7 /media/sdb7   xfs     defaults        0       2
# /dev/sdb10
UUID=9f48edce-112b-4011-9ea6-b14475a809c0 /media/sdb10    xfs     defaults        0       2
# /dev/sdb5
UUID=e9e4501a-b016-4786-ac6b-4d3697883ee3 /home     xfs     defaults        0       2
# /dev/sdb6
UUID=88956cf5-021f-482b-8ede-a648c569e37e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

192.168.178.21:/home/gt         /media/pentium3/gt      nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media           /media/pentium3         nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hda7      /media/pentium3/hda7    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb1      /media/pentium3/hdb1    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb6      /media/pentium3/hdb6    nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.178.21:/media/hdb7      /media/pentium3/hdb7    nfs rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by colossus73 on 2007-10-03
The problem is gnome-mount, I have this in the process list when I'm unable to mount an NTFS partition:

gnome-mount --fstype ntfs-3g --mount-options locale=en_US.UTF-8,exec
-h /org/freedesktop/Hal/devices/volume_uuid_DE44C09C44C07933

I even tried to modify ntfs-3g to ntfs in /usr/share/gconf/schemas/gnome-mount.schemas but with no luck. Shall I file a bug report?

---

### Post by Cannaregio on 2007-10-05
> **colossus73 said:**
> The problem is gnome-mount, I have this in the process list when I'm unable to mount an NTFS partition:

gnome-mount --fstype ntfs-3g --mount-options locale=en_US.UTF-8,exec
-h /org/freedesktop/Hal/devices/volume_uuid_DE44C09C44C07933

I even tried to modify ntfs-3g to ntfs in /usr/share/gconf/schemas/gnome-mount.schemas but with no luck. Shall I file a bug report?

I think you should.
I have the same problem:
external hard disk with TWO partitions on it.
The first one is mounted (and appears on the desktop) the second one is not (and does not appear on the desktop, with error message:
```
The volume 'so_and_so' uses the ntfs-3g file system which is not supported by your system
```

Here what gutsy sees:

```
fdisk -l

Disk /dev/sdf: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed34567c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       25496   204796588+   b  W95 FAT32  <--- this partition is seen & mounted
/dev/sdf2           25497       36483    88253077+   f  W95 Ext'd (LBA) <--- this partition is not mounted
/dev/sdf5           25497       36483    88253046    7  HPFS/NTFS          <--- same partition, not mounted

```

It worked flawlessly in Feisty.

---

### Post by colossus73 on 2007-10-05
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/149608](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/149608)

---

