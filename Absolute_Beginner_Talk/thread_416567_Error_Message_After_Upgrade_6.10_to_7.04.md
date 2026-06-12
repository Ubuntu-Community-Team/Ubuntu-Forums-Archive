---
title: "Error Message After Upgrade 6.10 to 7.04"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-04-21
After upgrading from 6.10 to 7.04, I get this error message:
*Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/hdb1
/dev/hdb1:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternative superblock:
e2fsck -b 8193 <device>
fsck died with exit status 8
*file system check failed
I can ctrl-D and 7.04 boots...but I have to connect to my dsl modem manually
(click the network icon and select "wired network")

Suggestions....thanking you in advance

---

### Post by Sef on 2007-04-21
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

From the site:

> free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy.

---

### Post by shoog on 2007-04-21
> **deaster2 said:**
> After upgrading from 6.10 to 7.04, I get this error message:
*Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open **/dev/hdb1**


Feisty uses /dev/sd* instead of /dev/hd* so you should change your fstab accordingly (or switch to UUID's to avoid these kind of problems)

---

### Post by deaster2 on 2007-04-21
> **shoog said:**
> Feisty uses /dev/sd* instead of /dev/hd* so you should change your fstab accordingly (or switch to UUID's to avoid these kind of problems)

Hit nail right on the head...editing my fstab to what gnome
partition manager said was the CORRECT name solved my
problem. I had installed a second hard-drive-that was causing
the problem with the incorrect name.
Many, many Thanks for this fix.

---

### Post by wormie_dk on 2007-04-24
I have the same problem...

**/boot/grub/menu.lst**
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

**/etc/fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#/dev/hda5 / 
fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce /               ext3    defaults,errors=remount-ro 0       1

#/dev/hda3 /data
2dac612a-c3fd-4a45-9557-d714b3b6347b /data               ext3    defaults  0       1

#/dev/hda6 
ce4190ba-fba2-4c35-9624-d862dbcf7a4a swap		sw 	0	0

proc            /proc           proc    defaults        0       0

```

**/var/log/fsck/checkfs**
```

Log of fsck -C -R -A -a 
Tue Apr 24 07:33:23 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open 2dac612a-c3fd-4a45-9557-d714b3b6347b

2dac612a-c3fd-4a45-9557-d714b3b6347b: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Tue Apr 24 07:33:23 2007
----------------

```

**Output from ls -l /dev/disk/by-uuid**
```

lrwxrwxrwx 1 root root 10 2007-04-24 08:34 2dac612a-c3fd-4a45-9557-d714b3b6347b -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-04-24 08:34 BEF81DDAF81D91AF -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-04-24 09:32 ce4190ba-fba2-4c35-9624-d862dbcf7a4a -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-04-24 09:32 fcd7dd8e-1ea2-47e5-bf9f-f1cb2a3ea3ce -> ../../sda5

```

**Output from fdisk -l**
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            8200        9729    12289725    f  W95 Ext'd (LBA)
/dev/sda3            1913        8199    50500327+  83  Linux
/dev/sda5            8200        9602    11269566   83  Linux
/dev/sda6            9603        9729     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order

```
SDA3 is a data partition usually mounted in /data 
SDA5 is the root partition
SDA6 is the swap partition

Is anything else needed?

---

### Post by elektronaut on 2007-08-14
A bit late, but it might still be useful, at least for others with a similar problem. I'm no expert on this, but to me your partition table looks weird. The fsck output was: ```
fsck.ext3: No such file or directory while trying to open 2dac612a-c3fd-4a45-9557-d714b3b6347b
```
That should be sda3. If you look at the partition table and compare the sector values you will find that you have a Win95 entry AND a Linux entry for the same sector offset. I might be wrong here, so please correct me then. I had a similar problem, in my case it turned out to be a forgotten entry in fstab - the disk was simply not connected, and i had added the entry manually. Ouch!

---

