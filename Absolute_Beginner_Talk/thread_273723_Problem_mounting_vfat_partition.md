---
title: "Problem mounting vfat partition"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-10-08
I'm trying to mount a partition that I created so that I can share my files from Ubuntu and also from XP Pro. Here is the output from df -h :

> simon@simon-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hdb3              15G  9.6G  4.1G  71% /
varrun                506M  104K  506M   1% /var/run
procbususb             10M  152K  9.9M   2% /proc/bus/usb
udev                   10M  152K  9.9M   2% /dev
/dev/hda3             134G   57G   78G  43% /media/hda2
/dev/hdb1              22G  7.7G   15G  36% /media/hdb1
/dev/sda1             494M  441M   53M  90% /media/usbdisk


I am trying to mount /dev/hdb3 as it contains all of my music that I copied into there from my ntfs partition /dev/hdb1.

After I read a few other posts regrading mounting vfat partition I added the following line to my /etc/fstab file:

> /dev/hdb3   /media/hdb3 vfat defaults,umask=000 0

I had already created the folder /media/hdb3 as the mount point. I have tried restarting the machine and nothing is appearing in the /media/hdb3 folder. I have also tried unmounting and remounting all of my other mounted drives by typing: **sudo umount -a** and then **sudo mount -a**. When I do this, however, I get this error message:

> simon@simon-desktop:~$ sudo mount -a
mount: /dev/hdb3 already mounted or /media/hdb3 busy
mount: according to mtab, /dev/hdb3 is mounted on /


So it seems that /dev/hdb3 is already mounted in the root folder but not showing up as far as I can tell.

Can anybody help me out here? I'm starting to feel a bit like this:](*,) 

Thanks in advance :)

---

### Post by CatKiller on 2006-10-08
I think you might have got confused as to your partition numbers. According to your df output, hdb3 **is** your root filesytem. Your music must be somewhere else.

---

### Post by aysiu on 2006-10-08
Can you post the output of these two commands? ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Clark Nova on 2006-10-08
Oops, now I look again I think you are right about me getting mixed up. The drive I'm trying to mount in that case is probably /dev/hda5 according to my **fdisk -l** below:

> Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2423    19454715    f  W95 Ext'd (LBA)
/dev/hda2            2424        2550     1020127+  82  Linux swap / Solaris
/dev/hda3   *        2551       20023   140351841    7  HPFS/NTFS
/dev/hda5               2        2423    19454683+   b  W95 FAT32

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2827    22707846    7  HPFS/NTFS
/dev/hdb2            4732        4998     2144677+   5  Extended
/dev/hdb3   *        2828        4731    15293880   83  Linux
/dev/hdb5            4906        4998      746991   82  Linux swap / Solaris
/dev/hdb6            4817        4905      714829+  82  Linux swap / Solaris
/dev/hdb7            4732        4816      682699+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 524 MB, 524288000 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          63      506016   83  Linux


Here is my **cat /etc/fstab**:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3 -- converted during upgrade to edgy
UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb7 -- converted during upgrade to edgy
UUID=002a21bc-cc35-4fe7-823f-978f742218f6 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
# /dev/hda2 -- converted during upgrade to edgy
UUID=3E5CA18C5CA1400F /media/hda2 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
# /dev/hdb1 -- converted during upgrade to edgy
UUID=1A60BBF260BBD32D /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0

/dev/hdb3   /media/hdb3 vfat defaults,umask=000 0


So, do I just need to change the bottom line in my fstab file to:

> /dev/hda5   /media/hda5 vfat defaults,umask=000 0

and change the name of the mount folder accordingly?

Thanks for your help guys :)

---

### Post by CatKiller on 2006-10-08
Makes sense. Don't forget to create the mount point.

Oh, and you can call the mount point whatever you want. It doesn't have to be /media/hda5, it could be /media/music, or whatever.

EDIT: Really must learn to read properly :) You were already on the ball with the mount point.

---

### Post by Clark Nova on 2006-10-08
> **CatKiller said:**
> Makes sense. Don't forget to create the mount point.

Oh, and you can call the mount point whatever you want. It doesn't have to be /media/hda5, it could be /media/music, or whatever.

EDIT: Really must learn to read properly :) You were already on the ball with the mount point.

Thanks very much, I tested it out with **sudo mount /dev/hda5 /media/hda5** and it worked fine so I've now added to my fstab file so it mounts automatically when I start up.

I should learn to read properly too, I was only looking at the partition sizes the first time around and I thought the partition I was looking for was about the same size as /dev/hdb3 so I tried to mount it :whoops: I should be checking /dev/hd* in future to make sure I'm looking at the right hard drive.

Thanks again :)

---

