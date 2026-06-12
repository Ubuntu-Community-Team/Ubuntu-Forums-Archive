---
title: "Setting a partition mount point / moving My Documents"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by philipt1969 on 2007-06-23
Hi all

The story so far

I have partitioned my 80G hard drive with the following partitions using gparted live cd

/dev/hda1 - 20 Gig NTFS (windows xp - including current data in my documents)

/dev/hda2 - 20 Gig Ext3 (ubuntu-installed)

/dev/hda3 - extended partition containing
/dev/hda5 - 1 Gig swap

/dev/hda4 - 35Gig Ext 3

which is to be used to share files between xp and ubuntu

I want to set the mount point of /dev/hda4 to /home, and got the impression I would be able to this this in gparted when setting up the partitions, but at no point during the set up of the partitions was I asked to give a mount point.

How can I set the mount point of hda4 to /home?

The next step will be to move the contents of My Documents in windows to /dev/hda4. (I have downloaded the necessary package to allow windows to recognise the ext2 (3) filesystem, and it recognises the drives, but will moving these files present any problems?

Thanks in advance, from an almost complete nooby!

---

### Post by Inxsible on 2007-06-23
In Gparted while installing, it does provide you with the options of listing the mount points. Its strange that you didnt get any.

Post the ouput of

```
sudo fdisk -l
``` -l is lowercase L

and ```
gksudo gedit /etc/fstab
```

---

### Post by philipt1969 on 2007-06-23
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2        2551    20482875    7  HPFS/NTFS
/dev/hda2            7039        9588    20482875   83  Linux
/dev/hda3            9589        9729     1132582+   5  Extended
/dev/hda4            2552        7038    36041827+  83  Linux
/dev/hda5            9589        9729     1132551   82  Linux swap / Solaris

and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8e9d1e22-ba6e-4f87-a2b0-df6d6a8a95e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e77f4bfc-256f-4842-8acd-1ca625b0c693 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Inxsible on 2007-06-23
Add this line to your fstab

```
/dev/sda4 /home ext3 defaults 0 2
```

You will have to be a little careful here, since you are changing mount points and drives. After you add this line, copy all the contents of your current /home folder into this drive.

Then delete the existing /home folder like so
```
sudo rmdir /home
```

Or better yet rename is so that you can go back in case you have problems. You can delete it later once you know everything works. Rename it like this
```
sudo cp /home /homeBackup
```


Then try and reboot. See if the new drive and mount point is accepted and all your applications work normally. If they do, you can delete the /homeBackUp

---

### Post by philipt1969 on 2007-06-23
Thanks for that, now up and running. Although I did notice that it needed to be /dev/hda4 - not sd4 I was including in fstab

---

