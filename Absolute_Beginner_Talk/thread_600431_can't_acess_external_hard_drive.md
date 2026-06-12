---
title: "can't acess external hard drive"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-02
Hi
I have just installed Ubuntu, and i have an 500gb external seagate hard drive. When i try to look at the files in the hard drive ubuntu tells me that "the folder contents could not be displayed". The file type is NTFS, how can i see my file? I have googles it to no avail. I know how to do a little more than the basics in computers, but not much more.
Thanks for the help

---

### Post by taurus on 2007-11-02
How do you mount that external harddrive?  Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
mount
```

---

### Post by john lejeune on 2007-11-02
Try
```
sudo ntfs-3g  /dev/locationOfMySeagate /media/myFolder -o rw
```

---

### Post by Falc7 on 2007-11-02
from the first query
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors



2nd
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              87G  2.2G   80G   3% /
varrun               1007M   96K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   84K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             466G   30G  437G   7% /media/FreeAgent Drive


3rd
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


@john, it said failed to acess, no such file or directory

I am using 64 bit ubuntu if that is relevant

---

### Post by Falc7 on 2007-11-02
any ideas?

---

