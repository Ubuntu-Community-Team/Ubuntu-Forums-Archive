---
title: "Second HardDrive"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by aredash on 2007-02-14
Hi, 
I just installed Ubuntu a few hours ago (I am completely new to this).  I have a slave drive that I had been using as backup space on my windows machine.  Now that Ubuntu is installed, I can't find that hard drive to recover all the music/video/documents that I backed up on it.  I went into the media folder and all I see are my two cdrom drives.  Is there a way for me to recover these files short of reinstalling windows?
Thanks.

---

### Post by taurus on 2007-02-14
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tronica on 2007-02-14
here's a guide on just that:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

---

### Post by aredash on 2007-02-14
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/hdb5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sda: 262 MB, 262144000 bytes
32 heads, 33 sectors/track, 484 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         485      255984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)

---

### Post by aredash on 2007-02-14
also, I tried that guide, and when I mounted the drive, it was just empty.. and I know that it definitly is full of files...

---

### Post by taurus on 2007-02-14
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb5   /media/hdb5   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb5
sudo mount -a
df -h
```

---

### Post by aredash on 2007-02-14
When I put in "sudo mount -a" I got:
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And when I put in df -h I got:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G  1.9G   67G   3% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  204K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda1             250M  152M   99M  61% /media/MINIDASH

wth MINIDASH being my USB stick.

---

### Post by taurus on 2007-02-14
Can you post your /etc/fstab here?

```
cat /etc/fstab
```

---

### Post by aredash on 2007-02-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5       /media/hdb5     ntfs    nls=utf8,unmask=0222    0       0

```

---

### Post by aredash on 2007-02-14
I had tried that tutorial, mounting a drive as "Windows", that might have messed it up?

---

### Post by taurus on 2007-02-14
> **aredash said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5       /media/hdb5     ntfs    nls=utf8,unmask=0222    0       0

```

It should be **umask**, not u**n**mask.

```
/dev/hdb5       /media/hdb5     ntfs    nls=utf8,umask=0222    0       0
```

---

