---
title: "Dual boot.  Finding the other distro's HD."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-10-07
I dual boot Ubuntu with Freespire.  I have some files on Freespire I'd like to try out on Ubuntu. Where are the Freespire drive and files?  I can find Ubuntu's file drive and file structure when in Freespire, but not the other way around.  

Do I need to do an extra step?  When I go to /mnt to look for all the drives, it's empty. Even using terminal and using "gksudo nautilus", the /mnt directory still comes up empty.

---

### Post by Kateikyoushi on 2006-10-07
Check the /media library, /mnt is empty for me as well but have all my drives are mounted in /media.

---

### Post by georgetoon on 2006-10-07
> **Kateikyoushi said:**
> Check the /media library, /mnt is empty for me as well but have all my drives are mounted in /media.

I checked /media and the Freespire partiton is not there.

I went into Administration and checkd the disks. the partiton isn't listed there, either.

---

### Post by zappa on 2006-10-07
Can you enter
sudo fdisk -l 
in a terminal?

---

### Post by georgetoon on 2006-10-07
> **zappa said:**
> Can you enter
sudo fdisk -l 
in a terminal?

Yes. and I got this:

> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12843   103161366   83  Linux
/dev/hda2           12844       24321    92197035    5  Extended
/dev/hda5           12844       23043    81931468+  83  Linux
/dev/hda6           23945       24321     3028221   82  Linux swap / Solaris
/dev/hda7           23044       23434     3140676   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4111    33021576    c  W95 FAT32 (LBA)
/dev/hdd2            4112       24321   162336825    f  W95 Ext'd (LBA)
/dev/hdd5            4112        8286    33535656    b  W95 FAT32
/dev/hdd6            8287       12426    33254518+   b  W95 FAT32
/dev/hdd7           12427       16559    33198291    b  W95 FAT32
/dev/hdd8           16560       20677    33077803+   b  W95 FAT32
/dev/hdd9           20678       24321    29270398+   b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9732    78172258+   c  W95 FAT32 (LBA)



The 200 gig disk should have two partitons.  One for Ubuntu, one for Freespire.

---

### Post by Kateikyoushi on 2006-10-07
How does your /etc/fstab look like ?

```
sudo cat /etc/fstab
```

---

### Post by georgetoon on 2006-10-07
> **Kateikyoushi said:**
> How does your /etc/fstab look like ?

```
sudo cat /etc/fstab
```


Here it is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000 0

I just noticed that the second partton is listed in the dministraton disk utility. it's listed as /dev/hda5 but it labeled as "swap" and there are no controls available to enable it.

---

### Post by Kateikyoushi on 2006-10-07
Great Firefox crashed so have to retype it again.
Does your other linux installation work ?

We need to make a mount folder for your partition.
```
sudo mkdir /media/hda5
```

Then have to add the partition to your fstab and a swap as well, but first a backup.
```
sudo cp /etc/fstab /etc/fstab~
sudo gedit /etc/fstab
```

Now we need to edit the /dev/hda5 line and add a new after.

```
/dev/hda5 /media/hda5 ext3 defaults 0 1
/dev/hda6 none swap sw 0 0
```

Finally this can save you a reboot.

```
sudo mount -a
```

Hopefully it all works.

---

