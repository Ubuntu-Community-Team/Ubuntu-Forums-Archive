---
title: "Seagate USB hard drive not recognized"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by mkeithcloud on 2007-06-20
My seagate 80GB USB hard drive is not recognized in Ubuntu 7.04. Is there any way to make it recognize it without reformatting it and losing everything on it?

---

### Post by Nezing on 2007-06-20
I'm using my Seagate 160gig usb drive,and listening to my media files,as I type this.For me Ubuntu 7.04 recognised it instantly.Silly question,make sure your usb connections are working.Unplug your drive,and plug it in again,in another usb port if necessarry.
Try to hold off formatting for now,as I'm sure someone will solve this.I just wanted to point out that Seagate drives are normally fine.

---

### Post by molly_001 on 2007-06-20
Very likely the path to your success is in this thread:
[http://ubuntuforums.org/showthread.php?p=2864654](http://ubuntuforums.org/showthread.php?p=2864654)
 
regardless, you should read the thread and post (** in a New Post)
the output of some of the commands you will read about in that thread.  
You'll get success much quicker in that way when you share
information from the output of those commands.

---

### Post by mikesignguy on 2007-06-20
post your result of 


mount 
and

cat /etc/fstab

---

### Post by mkeithcloud on 2007-06-20
root@pkiflptmrk:~# mount
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
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
root@pkiflptmrk:~# cat/etc/fstab
bash: cat/etc/fstab: No such file or directory

---

### Post by Inxsible on 2007-06-20
> **mkeithcloud said:**
> root@pkiflptmrk:~# mount
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
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
root@pkiflptmrk:~# cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
 
There should be a space between cat and /etc/fstab

---

### Post by Inxsible on 2007-06-20
Post the output of ```
sudo fdisk -l
``` -l is lowercase L. Make sure your seagate drive is connected when you do this

---

### Post by Bonnobo on 2007-10-25
HI there,
I have the same problem with my Seagate 320Gb external drive.  Now I have recently installed upgraded to 7.10, but the drive was recognised on 6.10. my results from -mount are:-

warmdent@warmdent-desktop:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda5 on /media/NOEL type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)


and from fdisk are:-

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb24281d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4660    37431418+  83  Linux
/dev/hdc2            4661        4865     1646662+   5  Extended
/dev/hdc5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x17a2a492

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       44718    22537840+   7  HPFS/NTFS
/dev/sda2           44719      155061    55612872    f  W95 Ext'd (LBA)
/dev/sda5           44719       99603    27662008+   b  W95 FAT32
/dev/sda6           99604      155061    27950800+   b  W95 FAT32

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

..where /dev/sda is my external drive.

From cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=6944632d-3664-4115-aee2-abd17bb3f0ac /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=e67b70ce-8986-49f1-8d27-6252973b8816 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

sorry for the amount of code, but I haven't got any idea as to what to do.  As I am a beginner, desperately trying to shake off Microsoft

Thanks for any help........

---

