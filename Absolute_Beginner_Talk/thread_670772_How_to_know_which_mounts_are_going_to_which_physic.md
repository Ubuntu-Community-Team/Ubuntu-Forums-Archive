---
title: "How to know which mounts are going to which physical drive?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by loverboyj on 2008-01-17
Im still very green on using Linux, although I have taken basic classes for Unix systems on our community schools to get started.

Now, I have installed Ubunto 7.10 Server to build a Samba file server box.  My hardware consist of 2 drives, first drive is an 80GB (boot drive and for some file storage) and a second 500GB drive specifically for important file storage.

During the partitioning, I did a manual setting for partitions to get the max space available for file storage for the 80GB drive , and everything went smoothly during the install.  This is where I totally forgot to write down which mount names that I specified for the drives. 

Here my simple question, how do I get the partitioning information (ie. mount names) for each drive.  

Thanks for any information, I'm still learning the ropes on using linux since I'm trying to get away from Winblows.

---

### Post by spiderbatdad on 2008-01-17
```
sudo fdisk -l
```??

---

### Post by loverboyj on 2008-01-17
Thanks, it gave me this information

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029bef

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  83  Linux
/dev/hda2            9486        9729     1959930    5  Extended
/dev/hda3            2433        9485    56653222+  83  Linux
/dev/hda5            9487        9729     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order


Additional Question, How do I know what is mount names on HDA1, HDA2,HDA3 AND SDA1.  I know HDA5 is the /swap partition

TIA

---

### Post by PeterJS on 2008-01-17
sudo is only needed with fdisk if you are running a hardened install, and generally it's best to only use sudo when absolutely necessary. There are two files that a primarily concerned with mountings /etc/fstab (FileSytem TABle), and /etc/mtab (Mount TABle). Fstab tells you where things are supposed to default to and what options they're use when they mount. /etc/mtab tells what mounted where and how right this second.

---

### Post by loverboyj on 2008-01-18
Thank you, thats what I was looking for.:)
on the terminal I issued "sudo nano /etc/fstab" and it showed me the mount names to partition

---

### Post by vanadium on 2008-01-18
Head the advice: do not use sudo unless necessary. To safely read a file, use

cat /etc/fstab

or

less /etc/fstab

To view what is currently mounted, you can indeed display mtab, but

mount

is another way.

There are always various approaches in linux

---

### Post by thelatinist on 2008-01-18
> **PeterJS said:**
> sudo is only needed with fdisk if you are running a hardened install, and generally it's best to only use sudo when absolutely necessary.

What is a "hardened install"?  I have a pretty default installation of 7.10 and I can't run fdisk as user.

---

### Post by compwiz18 on 2008-01-18
You can also run the command mount, which will give you something like ```
$ mount                                                                                                                                                                           (01-18 07:51)
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda6 on /files type ext3 (rw)
/dev/hda5 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/external-3 type jfs (rw,nosuid,nodev)

```

---

### Post by loverboyj on 2008-01-18
Thanks guys, I'm learning as much as I can, I'm marking this thread as solved since I got the information that I need

---

### Post by PeterJS on 2008-01-18
> **thelatinist said:**
> What is a "hardened install"?  I have a pretty default installation of 7.10 and I can't run fdisk as user.

The Bastile Hardening script is the particular tool that I was thinking of, one of the things that it does is set the permissions on everything in /sbin and /usr/sbin to 700, so that non root accounts can't even run the program. In a standard install the permissions are 755, so a user can run the programs in sbin, but the program will most likely fail and print an error message saying it wants root privileges. In the case of fdisk, sudo is needed if you actually want to change anything, but to just use the -l flag to list the partitions does not require elevated privileges.

---

### Post by thelatinist on 2008-01-18
> **PeterJS said:**
> The Bastile Hardening script is the particular tool that I was thinking of, one of the things that it does is set the permissions on everything in /sbin and /usr/sbin to 700, so that non root accounts can't even run the program. In a standard install the permissions are 755, so a user can run the programs in sbin, but the program will most likely fail and print an error message saying it wants root privileges. In the case of fdisk, sudo is needed if you actually want to change anything, but to just use the -l flag to list the partitions does not require elevated privileges.

I haven't done any of the things you describe, but the result of fdisk -l as user is to return me to the prompt, without even any error message.  sudo fdisk -l gives the expected output.  And, yes, /sbin and /sbin/fdisk are both set to 755.

---

