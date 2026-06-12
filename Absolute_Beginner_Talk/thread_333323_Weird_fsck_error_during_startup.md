---
title: "Weird fsck error during startup"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-01-07
My Ubuntu install has started generating this error while loading:

fsck 1.39 (29-May-2006)
/dev/hdb3: clean, 4761/2606080 files, 124309/5242880 blocks
fsck.ext3: Unable to resolve 'UUID=b203d351-4329-4797-b4f8-972ffc65087e'

fsck died with exit status 8


Once I CTRL-D the bootup keeps going and everything seems to be running fine...the error message says I should fix my file sytem...any ideas?

---

### Post by xyz on 2007-01-07
[T H I S]("http://ubuntuforums.org/showthread.php?p=1943342") for a start and post what you'll see is needed to better understand your problem.
Good luck.

---

### Post by kexodusc on 2007-01-07
> **xyz said:**
> [T H I S]("http://ubuntuforums.org/showthread.php?p=1943342") for a start and post what you'll see is needed to better understand your problem.
Good luck.

Okay, fdisk -1 provides:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1305    10482381   83  Linux
/dev/hdb2            7170        7476     2465977+  82  Linux swap / Solaris
/dev/hdb3            1306        3916    20972857+  83  Linux
/dev/hdb4            3917        7169    26129722+  83  Linux

Partition table entries are not in disk order


And fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=5c0e0a2e-4a41-4329-81d8-7746427c5cb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E294AD75FC4162F5 /Windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=d92e80be-b567-48b7-81a5-e9e18b6754e7 /home           ext3    defaults        0       2
# /dev/hdb4
UUID=b203d351-4329-4797-b4f8-972ffc65087e /media          ext3    defaults        0       2
# /dev/hdb2
UUID=9ca03f79-df40-4b43-a1f9-03892832d4d3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Hmm, think you're pointing me in the right direction here - I have Kubuntu on that /hdb4 which shows as being /media somehow.  Oh dear.  What have I done?

Any suggestions?

---

### Post by kexodusc on 2007-01-07
Thanks, xyz...your link led to other links, which led to hours of reading.  Didn't really provide a clear solution...but I learned a crap load about fstab, fsck, and filesystems in Linux.

Turns out, the other Linux install must have changed the UUID# for dev/hdb4.  I ran

```
ls /dev/disk/by-uuid/ -alh
```
 to find what the UUID tag was now and changed it in fstab....
Ubuntu found my hdb4 right after that and the fsck error is gone.
Hopefully all is good.

---

### Post by NZ-Wanderer on 2007-01-07
Looks like copying partitions generates the same error on boot up...

I just had exactly the same error occur on my system after I had backed up my /home partition to another partition (I like keeping a backup of it) hda5 is where I copied it to, and hda5 is the one that gave the error..

I did a 

```
ls /dev/disk/by-uuid/ alh
```

which you mentioned above, then I just loaded fstab into an editor and edited the UUID of hda5 with the value I got in the command above.

Rebooting the system and I got no errors at all...

Thank you for giving me the command to fix it :)

---

### Post by kexodusc on 2007-01-08
Hey glad it worked for you too...Just don't come chasing this newbie if your machine goes kaputz tomorrow :D

---

