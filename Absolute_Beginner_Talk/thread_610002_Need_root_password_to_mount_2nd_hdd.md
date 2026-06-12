---
title: "Need root password to mount 2nd hdd"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by xcaos on 2007-11-11
Hi,

I'm having problems allowing other users to mount a 2nd hdd. Every time I try to mount it I get a pop message asking for sys admin password (if I'm currently logged as a sys admin), if I'm logged as a "normal" user I get a message saying "Cannot mount volume" and clicking on the detail tab gives me "hal-storage-fixed-mount refused uid 1001".

If I mount it as sys admin than it becomes available to  everyone. The hdd is formated as NTFS and I'm using Gutsy.

Any ideas would be extremely appreciated.

Thanks,

---

### Post by elmosera on 2007-11-11
Mounting disks is something only superusers (root) can do, so what you're describing makes sense.

---

### Post by kellemes on 2007-11-11
How are you mounting the disk?

---

### Post by xcaos on 2007-11-11
I'm mounting it just by double clicking on it.

If only superusers can mount hdd, how can I make it so that the hdd gets automatically mounted so that it's available to all users?

---

### Post by DutyDuty on 2007-11-11
System >> Administration >> Users and Groups

Edit users' general permissions here.

---

### Post by xcaos on 2007-11-12
hummm!

All users have "access external storage devices automatically" enabled, but it still asks for root passwd. Isn't there a way to automount all hdd so that all users can read/write on them?

---

### Post by kpkeerthi on 2007-11-12
Can you post your /etc/fstab content and the output of ...
```

sudo fdisk -l

```

---

### Post by Partyboi2 on 2007-11-12
You’ll need to edit /etc/fstab: ```
gksudo gedit /etc/fstab
```Add this line to the end:
 ```
/dev/hdd1    /media/mynewdrive   ext3    defaults     0        2

```*change /dev/hdd1 to what your one is




 The “2&#8243; at the end instructs your system to run a quick file system check on the hard drive at every boot. Changing it to “0&#8243; will skip this. 





 If you want to allow a normal user to create files on this drive, you can either give this user ownership of the top directory of the drive filesystem: (replace USERNAME with the username)
 ```
sudo chown -R USERNAME:USERNAME /media/mynewdrive
```or in a more flexible way, practical if you have several users, allow for instance the users in the plugdev group (usually those who are meant to be able to mount removable disks, desktop users) to create files and sub-directories on the disk:
 ```
  sudo chgrp plugdev /media/mynewdrive
  sudo chmod g+w /media/mynewdrive
  sudo chmod +t /media/mynewdrive
```The last “chmod +t” adds the sticky bit, so that people can only delete their own files and sub-directories in a directory, even if they have write permissions to it.
Hope this points you in the right direction
:)

---

### Post by xcaos on 2007-11-12
here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c4ea5156-8e5e-4e0b-8096-082be09685b2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=8f70c186-3db9-44e6-b3ca-a05490219267 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

and here is the output that fdisk -l gives me:

```

nuno@nuno-desktop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22632263

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS
/dev/sda2            7297        7297        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdb: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e2a86c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1186     9526513+  83  Linux
/dev/sdb2            1187        1245      473917+   5  Extended
/dev/sdb5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e2cbdee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS


```

The hdds that I'm having problems with are /dev/sda1 and /dev/sdc1

Please note that the output of fdisk -l is after both hdd are mounted using root passwd

---

### Post by bulldog on 2007-11-12
Was there a valid reason why you disconnected those hdd's when you installed ubuntu?
In most cases this isn't the best solution.

You have to edit the fstab and add line for each partition you wnat to mount.
The best mountpoint would be /media,but it's your choice where to put them
You need to find the UUID for each partition to add in fstab.

To find the UUID```
ls /dev/disk/by-uuid -lh
```

This is how a NTFS partititon shows up in fstab,you have to use your own UUID and partition number ```

# Entry for /dev/sdb1 :
UUID=10B45E06B45DEEAA /media/sdb1 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
```

Note that my native language is Dutch,so you can set your own locale or leave it out.

Before editing fstab it could be a wise thing to make a copy,just in case.
```
sudo cp /etc/fstab /etc/fstab_copy
```

---

### Post by kpkeerthi on 2007-11-12
Partyboi2 has already provided a solution. 

The only thing you need to take care is a small change in /etc/fstab to properly support your NTFS partitions:

```

/dev/sda1 /media/windows1 ntfs-3g defaults 0 0
/dev/sdc1 /media/windows2 ntfs-3g defaults 0 0

```

And reboot. This would auto mount the partitions.

---

### Post by xcaos on 2007-11-12
AHAHAH

It works!!!!

the:

```

/dev/sda1 /media/windows1 ntfs-3g defaults 0 0
/dev/sdc1 /media/windows2 ntfs-3g defaults 0 0

```

was all that I needed.

Thank you very much for your help:):):):):)

---

### Post by kpkeerthi on 2007-11-13
You are welcome

---

