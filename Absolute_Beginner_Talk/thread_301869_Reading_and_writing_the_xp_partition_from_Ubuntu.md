---
title: "Reading and writing the xp partition from Ubuntu"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-17
I was following a guide from here [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)
to be able to use my files from xp. The problem is that when I use the
/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0 command from
the last step (changing the information according to my system, of course)
the terminal returns
bash: /dev/sda2: Permission denied

Could someone help me?

---

### Post by taurus on 2006-11-17
What does your /etc/fstab look like and this command?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by japc126 on 2006-11-17
the first one:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=730cf83c-aad6-495e-930a-5dc36d17923e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=959d340f-82d8-4ae1-a695-fb842e6dfd3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


the second one:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        7113    57078945    7  HPFS/NTFS
/dev/sda3            9270        9726     3670852+  82  Linux swap / Solaris
/dev/sda4            7114        9269    17318070    5  Extended
/dev/sda5   *        7114        9177    16579048+  83  Linux
/dev/sda6            9178        9269      738958+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000      255983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(998, 15, 32) logical=(999, 15, 31)


the actual line that I input and that returns me the error is:

/dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by taurus on 2006-11-17
Do you have mount point /media/windows?

```
ls -la /media
```

---

### Post by japc126 on 2006-11-17
I think I do... look at the end of the last line.

total 48
drwxr-xr-x  7 root root  4096 2006-11-17 18:14 .
drwxr-xr-x 21 root root  4096 2006-11-17 07:11 ..
lrwxrwxrwx  1 root root     6 2006-11-17 06:53 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2006-11-17 06:53 cdrom0
drwxr-xr-x  2 root root  4096 2006-11-17 06:53 cdrom1
lrwxrwxrwx  1 root root     7 2006-11-17 06:53 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2006-11-17 06:53 floppy0
drwx------  7 jose jose 22016 1969-12-31 18:00 usbdisk
drwxr-xr-x  2 root root  4096 2006-11-17 15:25 windows

---

### Post by Buck2348 on 2006-11-17
For what it's worth I got my Ubuntu to write to an NTFS partition with no hitches at all by following [this]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs").  I also enabled Windows to mount as a drive letter and read/write to my /home partition by following [this]("http://www.fs-driver.org/").  (The guide says this is for an ext2 partition but it works with ext3 too.)

---

### Post by taurus on 2006-11-17
I don't have a floppy in my machines but the last line of your /etc/fstab looks a little funny to me!!!

```
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```
Shouldn't it be something like /dev/hdc for your floppy drive!  If you are not sure which device, look in dmesg.

```
dmesg | more
```
Then, add that new line for your XP to the end of that and save it.  See if you can mount it this time with

```
sudo mount -a
```

---

### Post by japc126 on 2006-11-17
Thanks, I can access my entire drive at last

---

### Post by taurus on 2006-11-17
> **japc126 said:**
> Thanks, I can access my entire drive at last
So, everything is working fine for you now!

---

