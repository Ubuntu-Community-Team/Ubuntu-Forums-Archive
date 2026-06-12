---
title: "Need a little help please"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by reswob on 2007-02-03
Hi, I've just installed Ubuntu 6.10 and I'm having a couple of issues.  My machine has two hard drives and is a dual-boot between Windows XP and Ubuntu.  XP is installed on the primary drive which has two partitions, 31 MB for some Dell junk and 19 GB for XP formatted NTFS.  The second drive is where I installed Ubuntu.  Ubuntu and XP boot just fine, but in Ubuntu I cannot see my NTFS partition.   It doesn't show in *Places -> Computer * and when I navigate to the folder /media/hda3, it is empty.  

I tried the tips in the thread entitled "User Permissions with mounting drive" and here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=10bf2884-3cfd-4d08-ab8c-03d5ceb848d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=8ab7c89c-c460-474a-89ce-53e9f70fe3b2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3	/media/hda3	smbfs credentials=/root/.smbcredentials 0 0

Here is the response from typing 'mount'

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=craig)

and finally, what I get when I type fdisk -l

Disk /dev/hda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1           4       32098+  de  Dell Utility
/dev/hda3   *           5        2431    19494877+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris


Any suggestions would be greatly appreciated.

Thanks

---

### Post by taurus on 2007-02-03
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda3   /media/hda3   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hda3
sudo mount -a
df -h
```

---

### Post by shareMenaPeace on 2007-02-03
Hi,
im curious what does/means ?
```

sudo mount -a
df -h
```[/QUOTE]

---

### Post by reswob on 2007-02-04
That did it!  Thanks.

---

### Post by Cobikegeek on 2007-02-04
mount -a  = mount all filesystems listed in /etc/fstab
df -h  = list free disk space on all mounted filesystems in human readable form.

---

### Post by shareMenaPeace on 2007-02-04
thx

---

