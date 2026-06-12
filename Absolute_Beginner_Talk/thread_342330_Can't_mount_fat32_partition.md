---
title: "Can't mount fat32 partition"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-01-19
Hi
Could someone help me mount a fat32 partition.
I had win xp on 60gig out of 80gig as well as ubuntu. Since i wasn't using win and my ubuntu was kind of running out of space, i used Gparted to resize it and carve a 40 gig of fta32 file system partition out of the window one, so i'd be able to store information or access it from windows, should i need to do that. Now I have /dev/hda1 ntfs type, /dev/hda3 fat32 and /dev/hda2 ext3 type in Gparted. Thing is then when i rebooted in ubuntu, it didn't see it but windows did see it and named it as drive c.
 I had a go with the information of the other threads here but no luck.
can someone help me and i will be a very happy chap:wink:

---

### Post by taurus on 2007-01-19
Edit /etc/fstab with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end and add these three lines.

```

/dev/hda1   /media/hda1   ntfs    nls=utf8,umask=0222   0   0
/dev/hda2   /media/hda2   ext3   defaults   0   1
/dev/hda3   /media/hda3   vfat    iocharset=utf8,umask=000   0   0

```
Save the changes.  Then, create three mount points and mount them.

```
sudo mkdir /media/hda1 /media/hda2 /media/hda3
sudo mount -a
df -h
```

---

### Post by sn0m on 2007-01-19
mate u're a legend, worked fine.
cheers
koli:guitar:

---

### Post by taurus on 2007-01-19
Good deal.

---

### Post by sn0m on 2007-01-19
mate sth else.
As ubuntu was loading up, i got this message in terminal mode:

after 2  partitions were checked ok, this follwed:
 checking file system............
fsck 1.39 (29May 2006)
/dev/hda2 is mounted
e2fsck cannot continue, aborting

fsck died with exit status 8

when i exit it, it gives a brief message which says -UTF8 is not recommended for FAT32.. then it returns in graphic mode and loads up ok. There's nothing wrong with th OS, i can do whatever i like.


the following is the log file created.

/var/log/fsck/checkfs

Log of fsck -C -R -A -a 
Sat Jan 20 04:13:38 2007

fsck 1.39 (29-May-2006)
/dev/hda2 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Sat Jan 20 04:13:38 2007
----------------


last hitch to sort out i guess
Ta
Koli

---

### Post by taurus on 2007-01-19
Are you sure /dev/hda2 is ext3?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by sn0m on 2007-01-20
sudo fdisk -l

sn0m@sn0m-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            7650        9733    16739730   83  Linux
/dev/hda3            2551        7649    40957717+   b  W95 FAT32

Partition table entries are not in disk order
sn0m@sn0m-laptop:~$

---

### Post by taurus on 2007-01-20
Okay, we need to unmount /dev/hda2 first before we can reformat it to ext3.

```
sudo umount /dev/hda2
sudo mke2fs -j /dev/hda2
sudo mount -t ext3 /dev/hda2 /media/hda2
```
Or reboot.

---

### Post by sn0m on 2007-01-20
not much luk mate. this is the output

sn0m@sn0m-laptop:~$ sudo umount /dev/hda2
Password:
sn0m@sn0m-laptop:~$ sudo mke2fs -j /dev/hda2
mke2fs 1.39 (29-May-2006)
/dev/hda2 is mounted; will not make a filesystem here!
sn0m@sn0m-laptop:~$ 

tried again
sn0m@sn0m-laptop:~$ sudo umount /dev/hda2
umount: /: device is busy
umount: /: device is busy
sn0m@sn0m-laptop:~$ 

Will i still be able to unmount it if ubuntu is running?

---

### Post by taurus on 2007-01-20
Edit /etc/fstab and place a # in front of the entry for /dev/hda2.  Reboot and make sure /dev/hda2 doesn't show up on this list.

```
df -h
```
Then, format it and see if you can mount it.

```
sudo mke2fs -j /dev/hda2
sudo mount -t ext3 /dev/hda2 /media/hda2
```
If everything is okay, then edit /etc/fstab again except this time, remove the # from the /dev/hda2 entry.  Save it and reboot.  

See if you still get an error message regarding /dev/hda2 when it boots up.

---

### Post by sn0m on 2007-01-20
not much luck mate

sn0m@sn0m-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              16G  7.1G  7.9G  48% /
varrun                442M  180K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
procbususb             10M   96K   10M   1% /proc/bus/usb
udev                   10M   96K   10M   1% /dev
devshm                442M     0  442M   0% /dev/shm
/dev/hda1              20G   18G  1.7G  92% /media/hda1
/dev/hda3              40G   16K   40G   1% /media/hda3
sn0m@sn0m-laptop:~$ sudo mke2fs -j /dev/hda2
Password:
mke2fs 1.39 (29-May-2006)
/dev/hda2 is mounted; will not make a filesystem here!
sn0m@sn0m-laptop:~$

---

### Post by taurus on 2007-01-20
Wait.  /dev/hda2 is your / (where you installed Ubuntu on) so better not format it or you will wipe out Ubuntu.  Actually, you can't format it right now anyway since it won't allow you to format while it is being mounted.  Therefore, everything is good with you now.  To make sure, what does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by sn0m on 2007-01-20
sn0m@sn0m-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=51894118-a070-4ccc-abe4-590193a6ddde /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=027C1D867C1D759F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   /media/hda1   ntfs    nls=utf8,umask=0222   0   0
#/dev/hda2   /media/hda2   ext3   defaults   0   1
/dev/hda3   /media/hda3   vfat    iocharset=utf8,umask=000   0   0
sn0m@sn0m-laptop:~$

---

### Post by sn0m on 2007-01-20
This is interesting, since I put #in front of /dev/hda2 it did't do it. ? Could this be some sort of a bug...
thanks
Koli

---

### Post by taurus on 2007-01-20
So you did install Ubuntu on /dev/hda2.  You mount /dev/hda1 twice so edit /etc/fstab and put a # sign in front of this line.

```

UUID=027C1D867C1D759F /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

```
Save it and reboot.  See if everything is still working.

```
df -h
```

p.s.  Looks like you don't have any swap partition.

---

### Post by taurus on 2007-01-20
> **sn0m said:**
> This is interesting, since I put #in front of /dev/hda2 it did't do it. ? Could this be some sort of a bug...
thanks
Koli

The # means comment so whatever after the # will not be read.  Don't remove any # in /etc/fstab except you have to add one for /dev/hda1 as described from previous post.

---

