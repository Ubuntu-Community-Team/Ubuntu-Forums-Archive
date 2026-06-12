---
title: "NTFS partitions missing in /dev"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by tomerwe on 2007-06-10
Yesterday installed the latest Ubuntu.
I have 3 NTFS partitions on 2 Harddrives. However only one of them (the main one) appears in /dev and thus is the only one I'm able to mount. fdisk does shows me the other partitions. 
using the ntfs-3g package.
attached mount output, fstab related lines and fdisk output.

any help appreciated,
Thanks.

root@Tomer:/home/tomer# mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
root@Tomer:/home/tomer# 

fstab - 
/dev/sdb1 /media/sdb1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdb5 /media/sdb5 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdc1 /media/sdc1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1


root@Tomer:/home/tomer# fdisk -l


Disk /dev/sda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1578    12675253+  83  Linux
/dev/sda2            1579        1653      602437+   5  Extended
/dev/sda5            1579        1653      602406   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sdb2            4463        9963    44186782+   f  W95 Ext'd (LBA)
/dev/sdb5            4463        9963    44186751    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4864    39070048+   7  HPFS/NTFS

---

### Post by meborc on 2007-06-10
have you tried to mount them using the "ntfs-conf" package? install it by doing "sudo apt-get install ntfs-config" afterwards, it should be in your menu... it detects the ntfs partitions and helps you to mount them

---

### Post by Najand on 2007-06-10
Can you mount them manually or by "ntfs" filesystem instead of "ntgs-3g"?

---

### Post by tomerwe on 2007-06-10
the ntfs_confg package doesn't seem to help.
I tried to mount them manually and with the ntfs option, the problem remains.
sdb5 and sbc1 devices which the fdisk claims to exist aren't actually in the /dev folder.

to clear thing up : 
sdb1 - NTFS primary partition mounts.
sdb5 - NTFS logical partition inside the extended partition DOESN't mount.
sdc1 - NTFS primary partition DOESN't mount.
 
example :  
root@Tomer:/home/tomer# mount /dev/sdb5
Failed to access '/dev/sdb5': No such file or directory

suggestions ?

---

