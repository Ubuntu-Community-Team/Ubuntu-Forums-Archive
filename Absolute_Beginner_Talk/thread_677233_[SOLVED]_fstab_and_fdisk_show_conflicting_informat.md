---
title: "[SOLVED] fstab and fdisk show conflicting information"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by quickk on 2008-01-24
Hi everyone, 
  
   I have this strange problem with the ubuntu boot process.  Booting works fine, until about 3/4 through the splash screen.  At this point it goes to a terminal display and starts checking my disks.  For one of the disks it always says something like: "the disk appears to be read only" or something like that.  

I have a fresh install of ubuntu 7.10.  The problem happens every time the system boots.

Anyway, I think that this is because I have a partition on the drive with no mount point.  I looked in the forums about how to automatically mount drives and looked at fstab and did sudo fdisk -l.  

Strangely enough, I get conflicting info.  I have 2 drives (250GB and 750GB) called sda and sdb, however the names are not consistent in the sense that fdisk things that sda is the 750GB one and fstab thinks it is the 250GB one.  Should I be worried?

here is the fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4a5e4728-5488-4b35-902c-e3ac1ec2d1d4 /               reiserfs notail          0       1
# /dev/sda4
UUID=a265447a-6138-43d9-bf9e-4eaf811cb6b3 /backup         reiserfs defaults        0       2
# /dev/sdb1
UUID=763da517-b37a-4996-9a22-8e98bbbf8868 /home           reiserfs defaults        0       2
# /dev/sda3
UUID=15581bd5-2987-486e-bb4b-c26f2d6b2a7c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0    

```

here is the fdisk output:

```

sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008dcd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc8b933d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217        3648    19535040   83  Linux
/dev/sdb3            3649        4256     4883760   82  Linux swap / Solaris
/dev/sdb4            4257       30401   210009712+  83  Linux
    /media/floppy0  auto    rw,user,noauto,exec 0       0 
```

---

### Post by peitschie on 2008-01-24
Hi quickk,

The read-only disk isn't referring to drives being mounted, but rather to the fact that some of the existing partitions being mounted are not able to be written to.  I have seen this caused by a corrupted partition or file system issues... is there any details given about which partition is thought to be read only?

Also, can you post the output of the following pieces of code here please?
```
ls -l /dev/disk/by-uuid
```
```
mount
```

For clarification too, the difference between fstab and fdisk, is that fstab is what is *expected* by linux to exist on the disks, and how to mount these results, while fdisk reads the actual information from the disks.  That is, fstab is what linux expected, fdisk is what physically exists... so in this case fdisk is more representative of what your computer actually contains :)

It may also be worth checking the file system for errors by running the following on each of the mounted reiserfs partitions:
```
reiserfsck --check */dev/diskname...*
```

This will only check for errors, and will not try to fix them yet.  For more information about this command see [http://linux.die.net/man/8/reiserfsck](http://linux.die.net/man/8/reiserfsck)

---

### Post by quickk on 2008-01-24
Thanks for the help.  The message that I get when it boots up is: "File system seems mounted read-only."  I didn't have time to write down the rest.  Here's the output that you requested:


ls -l /dev/disk/by-uuid

```
ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-01-24 17:27 15581bd5-2987-486e-bb4b-c26f2d6b2a7c -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-24 17:27 4a5e4728-5488-4b35-902c-e3ac1ec2d1d4 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-24 17:27 5a7aa863-2dd6-4f6a-9f8a-c08f8a126f78 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-01-24 17:27 763da517-b37a-4996-9a22-8e98bbbf8868 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-24 17:27 a265447a-6138-43d9-bf9e-4eaf811cb6b3 -> ../../sda4
 
```

and 

```
 /dev/sda1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda4 on /backup type reiserfs (rw)
/dev/sdb1 on /home type reiserfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=myusername)
 
```

Could this problem be related to the fact that during the installation, I created a partition on the first disk of 20GB, but didn't assign a mount point?  I did that because I wanted this partition to be simply a placeholder in case I wanted to install a different operating system.

---

### Post by peitschie on 2008-01-24
Hmm... there are no file systems obviously mounted as ro in your mount code, and the uuid's all match the fstab entries...

I believe the boot sequence is logged in the file: /var/log/messages.  You should be able to open it by typing in the following in a terminal or alt+f2 (run app):
```
gedit /var/log/messages
```

Have a browse through there and see if you canfind your error message maybe?  Does anything on your computer seem affected by the error?

---

### Post by quickk on 2008-01-24
I fixed the problem by assigning a mount point for that 20GB partition:

-First I found the uuid for the partition:

```
ls -l /dev/disk/by-uuid/
```

-then I edited the fstab to add the partition sdb2

```
sudo gedit /etc/fstab
```

Here's what the new fstab looks like

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4a5e4728-5488-4b35-902c-e3ac1ec2d1d4 /               reiserfs notail          0       1
# /dev/sdb2
UUID=5a7aa863-2dd6-4f6a-9f8a-c08f8a126f78 /othersystem    reiserfs defaults        0       2
# /dev/sdb4
UUID=a265447a-6138-43d9-bf9e-4eaf811cb6b3 /backup         reiserfs defaults        0       2
# /dev/sda1
UUID=763da517-b37a-4996-9a22-8e98bbbf8868 /home           reiserfs defaults        0       2
# /dev/sdb3
UUID=15581bd5-2987-486e-bb4b-c26f2d6b2a7c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Notice that I changed the sdb's to sda's and vice-versa to make things consistent with what fdisk says.  I'm not sure what the <dump> and <pass> numbers are for so I just used the same ones as for the other partitions.

-Finally, I added the directory /othersystem (that's what I decided to call the mount point) so that the drive can mount (I had forgotten this the first time, and upon booting there was a message like: could not assign mount point .

```
sudo mkdir /othersystem 
```

Now when I boot, everything is back to normal.  I don't see any terminal display text, and I don't get any messages about read only partitions.  Thanks for the help!

---

### Post by peitschie on 2008-01-24
Cool.  Thats a new one on me!  Congratulations on figuring it out in spite of my continual doubting :)... the next question is why it was complaining...

---

### Post by quickk on 2008-01-25
Thanks!  I'm happy that you told me why there was difference between fstab and fdisk!

---

