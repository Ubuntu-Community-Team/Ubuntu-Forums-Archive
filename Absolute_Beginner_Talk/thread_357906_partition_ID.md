---
title: "partition ID"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-02-10
Background -  I had Edgy installed on an a single drive (160Gig). I messed it up and had to start over. During reinstall I opted for using half the drive and save second half for storage as another partition. Everything went well. 

Now  -  I went looking for the second partition. It looks like the new install split the drive but kept the old install also. 

Question - How can I determine which partition belongs to the new install and which are from the old so I can use them for storage or is it better to start all over again.

===========================================
mar@mar-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9772    78493558+  83  Linux
/dev/sda2           18703       19457     6064537+   5  Extended
/dev/sda3   *        9773       18702    71730225   83  Linux
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
/dev/sda6           18703       19080     3036222   82  Linux swap / Solaris

Partition table entries are not in disk order
=============================================

Geesh what a mess

---

### Post by taurus on 2007-02-10
What's the output of this command from a terminal?

```
mount
```

---

### Post by mar225 on 2007-02-10
mar@mar-desktop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by taurus on 2007-02-10
Looks like /dev/sda3 is the current version that you are running.  Therefore, /dev/sda1 is the old version that you want to remove.

---

### Post by mar225 on 2007-02-10
What about the swap parts sda5 and sda6  Do they both belong to the new install.  
This gets gooier the further I go.

---

### Post by taurus on 2007-02-10
I think /dev/sda5 belongs to the old install and /dev/sda6 belongs to the new one.  To be sure, can you post your /etc/fstab here then?

```
cat /etc/fstab
```

---

### Post by mar225 on 2007-02-10
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c86115df-bdce-47f3-90a5-e0cbce55e51a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=12f1c46a-f893-4ab8-b836-7a0c94ae3449 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Here it is.   My grandad got me into this mess. He said if he was going to buy my computers I had to run something besides the Redmond special. Damn him.

---

### Post by taurus on 2007-02-10
Yip.  /dev/sda3 is the new install and /dev/sda6 is the new swap partition.

---

### Post by mar225 on 2007-02-10
I really need to clean this up.   If I do a partimage ??  and then reformat the drive into two pieces can I put the result of the partimage on half and have the other clean half for storage. Gramps will have a moose if he sees this cobbled up double vision mess. I really want to keep the setup like it is. It took a lot of time to set it up just right.

---

### Post by taurus on 2007-02-10
If you want to clean it up and since it's a new install, I recommend you boot with the LiveCD.  Use gparted on the LiveCD to delete everything, making it a one harddrive again.  Then, use gparted to resize it into two partitions, installing Ubuntu on one and using the second one as storage.  

That way, gramp will be happy and maybe you will get something nice from gramp too.

---

### Post by mar225 on 2007-02-10
It is a new install but it has all the programs and special tweeks installed. I spent two nights getting it just right.   If I could hide it I would put the Redmond special on the other half. LOL

---

