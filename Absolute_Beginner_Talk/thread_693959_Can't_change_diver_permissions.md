---
title: "Can't change diver permissions"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Kurosaki_Ichigo on 2008-02-11
Hi I'm pretty new to Linux and I'm having a problem changing the permissions of one of my drives

The drive is called "Expanded" and I tried to use:
```
sudo chmod 666 Expanded
```

while in the media directory, which I heard will give all users access but I just get a messag that says: 

chmod: changing permissions of `Expanded': Read-only file system

can someone please help?

---

### Post by taurus on 2008-02-11
What filesystem is Expended?  Bet it's ntfs.  Is it external or internal drive and how did you mount it?

Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Kurosaki_Ichigo on 2008-02-11
Its an Internal SATA Drive and its NTFS.
I think the drive mounted itself cuz it was just there in My computer after installing ubuntu but I can only access the files on it, I cant delete them or change them

---

### Post by taurus on 2008-02-11
Can you at least post the outputs of those commands?  You just need to mount it again in /etc/fstab with ntfs-3g driver so you can write to it.

---

### Post by Kurosaki_Ichigo on 2008-02-11
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      484521   244198552+  42  SFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bfa8ed0d-db2a-43a8-810f-1af2760ab8ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ca07e1c2-99d5-4172-bbe7-6e28bb22624f none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


ichigo@ichigo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              71G   12G   56G  17% /
varrun                760M  104K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  108K  760M   1% /proc/bus/usb
udev                  760M  108K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             233G  220G   14G  95% /media/Expanded

---

