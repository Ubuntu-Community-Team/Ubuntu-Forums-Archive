---
title: "Mount Issues"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by rpalmer on 2007-06-14
I have two hard drives installed on my ubuntu box. a 20GB for the OS and a 120GB for sharing files. I created a folder for the 120GB to mount to,(/mnt/mirror) and added an entry in fstab. It appears that I've done it correctly but for some reason the folder only shows 17GB of space even though it's mounted to a 120GB drive. What am I doing wrong?

*Here's the output of df*
rpalmer@rypp-ubuntu704:~$ df
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/hda1 18398028 3820092 13643360 22% /
varrun 192992 272 192720 1% /var/run
varlock 192992 0 192992 0% /var/lock
procbususb 192992 84 192908 1% /proc/bus/usb
udev 192992 84 192908 1% /dev
devshm 192992 0 192992 0% /dev/shm
lrm 192992 33788 159204 18% /lib/modules/2eneric/volatile

---

### Post by Ek0nomik on 2007-06-14
You should do...

```
df -h
```

...so it's readable.  ;)

Can you also post

```
mount
```

and

```
cat /etc/fstab
```

---

### Post by rpalmer on 2007-06-14
Okay, a little messy but here it is...

**df -h**
rpalmer@rypp-ubuntu704:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  3.7G   14G  22% /
varrun                189M  272K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
procbususb            189M   84K  189M   1% /proc/bus/usb
udev                  189M   84K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   33M  156M  18% /lib/modules/2.6.20-16-generic/volatile

**mount**
rpalmer@rypp-ubuntu704:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

**fstab**
rpalmer@rypp-ubuntu704:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=19a9a1f8-277b-4e8b-9776-bf677a36eb63 /               ext3    defa                                  ults,errors=remount-ro 0       1
# /dev/hda5
UUID=cdd16027-e144-4da7-8dc4-810c191f08c8 none            swap    sw                                                0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1       /mnt/mirror

---

### Post by Ek0nomik on 2007-06-14
Dang!  I knew I wanted one more command.  Can you post

```
fdisk -l
```

:)

Also, you actually have one hard drive, correct?  Just split up into 3 (ext3, swap, and xxx) partitions?  What file system did you make the "sharing" partition?  FAT32 I presume?

---

### Post by rpalmer on 2007-06-14
**fdisk -l**

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        2491    19904535   8e  Linux LVM

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  83  Linux

---

### Post by rpalmer on 2007-06-14
Sorry forgot to answer that last question.

I have 3 physical drives, two 20GB and one 120GB drive.  I formatted the 120GB to the ext3 file system. (I'm not a fan of FAT32 ;p) I shared out the /mnt/mirror folder which is housed on the 20GB OS partition but linked to the 120GB drive.  I am under the impression that the mount point is the same as  A: B: C: drives in Windows so actually the mirror folder should be able to store 120GB of data.

---

