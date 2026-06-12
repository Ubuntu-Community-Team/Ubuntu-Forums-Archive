---
title: "Can't find files on drive after trying to mount a separate drive..."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by jjjjti on 2007-12-26
For some background... I have 3 hard drives in my computer, a boot drive with the OS (/dev/hdb), a second drive with a ton of files (/dev/hdc), and a third empty drive (/dev/hdd). I attempted to create a mountpoint for the third drive using this tutorial:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

And made an error when I edited my /etc/fstab file. My second drive (with all my files) was mounted to a folder called "storage", and my third, to-be-mounted drive was to be mounted to "storage2". When editing /etc/fstab, I mounted the third empty drive to "storage", instead of "storage2" by accident, and now I can't seem to access any files on the second drive, or figure out how to undo what I've done. Hopefully someone here will tell me that I haven't lost all my files on the second drive. :)

Here is what my drives look like:

> Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006107d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18700   150207718+  83  Linux
/dev/hdb2           18701       19457     6080602+   5  Extended
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb2904544

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241   83  Linux

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6e09f94

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       10011    80413326   83  Linux


Here is my mountpoint info:

> Filesystem             Size   Used  Avail Use% Mounted on
/dev/hdb1              152G   101G    44G  71% /
varrun                 1.1G   242k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    95k   1.1G   1% /dev
devshm                 1.1G      0   1.1G   0% /dev/shm
lrm                    1.1G    36M   1.1G   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc1               82G    55M    77G   1% /storage
/dev/hdd1               82G    55M    77G   1% /storage
/dev/hdd1               82G    55M    77G   1% /storage2


And here is my /etc/fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=7972dee3-89c8-4a0d-89e3-03a0b1b45df3 /               ext3    defaults,erro$
# /dev/hdb5
UUID=70edca2e-15e1-4c0b-b4a1-32ec2a194a55 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/hdc1 /storage ext3 defaults 0 0
/dev/hdd1 /storage2 ext2 defaults 0 0


And I'm thoroughly lost... I'm a budding Ubuntu user but this is over my head as of now. Anyone willing to help me out and guide me through accessing my files on the second drive?

Thanks!

---

### Post by Cypher on 2007-12-26
If Ubuntu is installed on HDB and HDC/HDD are just storage drives, then do the follow in the command prompt
```

sudo umount /storage
sudo umount /storage2
sudo mount /dev/hdc1 /storage

```
This will unmount both the drives, and just mount HDC. Now check on your files with
```

cd /storage
ls -l

```
If everything looks good to you, then with your fixed /etc/fstab in place, you can reboot the machine and have both HDC and HDD mount into the right folders automatically.

Just FYI, mounting HDD over where HDC was mounted doesn't necessarily erase anything as the mount point is just your "window" or "view" to the drives content. So you can mount a particular drive to any directory you want. Unmounting and remounting it to a different location will "fix" everything..

---

### Post by dannyboy79 on 2007-12-26
sounds right on to me, although he doesn't have to restart his machine to get everything where he wants it. Just umount storage, fix fstab, then type in sudo mount -a. That will mount everything per the fstab file without having to restart your machine. let us know how it goes.

---

