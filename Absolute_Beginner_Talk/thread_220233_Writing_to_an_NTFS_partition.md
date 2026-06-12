---
title: "Writing to an NTFS partition"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-07-21
Hi

Ive seen the how too's in the How To section but none of them have worked, im not sure what im doing wrong. Id appriciate it if someone could help me.

Some of the guides are double dutch lol.

Its a 200gb External drive. All my important stuff on it is backed up so thats no problem.

Here are the contents of Fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/media/External Storage/       /media/<mount point>     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    
```

As you can see the external disc is the bottom one and ive already tried to get NTFS working on it, but at present, it doesnt.

What have I done wrong?

---

### Post by givré on 2006-07-21
A post at the end of the appropriate HowTo is always better i think ;) 
That said, i guess you were a bit confuse by the difference between device name & mount point. 
1.In the first column of /etc/fstab, you have to put your device name. This name can be found with
```
sudo fdisk -l
```
Find your device (this should be an NTFS one) and note is name (first column, something like /dev/sd...)

2.Now you have to create a directory where the device will be mount, so you will be able to browse it. If it's not already do:
```
sudo mkdir /media/<choose the name that you want, don't use <mount point> :cool: >
```
That's done, note your mount point

3.And now we have to put all that in /etc/fstab so it will be mount at startup.
```
gksu gedit /etc/fstab
```
and change
```
/media/External Storage/       /media/<mount point>     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    
```
to
```
<the name of the device>       <your mount point>     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
```
Of course, change what the <..> by the correct name 8) 
And don't forget that you have 2 zero at the end.

---

### Post by James_N on 2006-07-21
Thank you :)

sudo fdisk -l produces:

```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19552   157051408+  83  Linux
/dev/sda2           19553       19929     3028252+   5  Extended
/dev/sda5           19553       19929     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
jimbo@jimbo-desktop:~$

```

and my fstab looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb       /media/External     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0

```

but for some reason, i still cant write / delete files on this drive :(

---

### Post by givré on 2006-07-21
ok,
change
```
/dev/sdb       /media/External     ntfs-3g  silent,umask=0,locale=en_US.utf8    0    0
```
to
```
/dev/sdb[COLOR="Red"]1[/COLOR]       /media/External     ntfs-3g  silent,umask=0,locale=en_US.utf8    0    0
```
and remount your drive
```
sudo umount /dev/sdb1
sudo mount /dev/sdb1
```
an that should work :D

---

### Post by James_N on 2006-07-21
thanks but

```

root@jimbo-desktop:/home/jimbo# sudo umount /dev/sdb1
umount: /dev/sdb1: not found

```

---

### Post by James_N on 2006-07-21
right i unplugged it and plugged it back in. its now sdc1.

ive changed it to that in fstab, unmounted it, and now get this trying to mount it again:

```
Couldn't mount device '/dev/sdc1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.
root@jimbo-desktop:/home/jimbo#

```

---

### Post by James_N on 2006-07-21
ok i rebooted and its now back to sdb1 so changed it again in fstab but i still get the error on tryng to remount :(

---

### Post by givré on 2006-07-21
External drive are a pain to manage because of the fact that it's device name change. The solution is to have no mention of it in /etc/fstab, and let pmount do the job automaticly. But pmount is not cofigure to use ntfs-3g. I try to change that, but until it's work you'll have to wait.

P.S : Did you unmount you device before unplugging it, this is important to do (or you could have some bad surprise ;) ), and if you didn't do it, that's could be the reason you have this error.
If this is the case:
- unplug your device
- Comment the line about /dev/sd* in /etc/fstab
- plug it, and you should have it in read only.

And wait a bit the better solution. see my thread to have some news

---

### Post by geco on 2006-07-21
Quoting from [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)
> 
There is currently lots of progress being made in the linux-ntfs project, and we are once again moving one step closer to a full implementation of a read/write ntfs driver for linux.

On 07/14/2006, Project Member Szabolcs Szakacsits presented a new version of our ntfsmount and libntfs, currently given the project internal title ntfs-3g. This version has, apart from several rather unlikely cases, full read/write capabilities and has improved performance. As news spreads quickly, it has already been downloaded and tested by many users, and no incident has been reported so far. **Despite of that it is still to be considered beta**, and will upon successfull testing (in some way or the other) merge into the linux-ntfs ntfsprogs package.

So be **very careful** in writing on your ntfs!


One more suggestion:
for test purposes you don't need to edit your /etc/fstab

you can just do
```

sudo mount /dev/device /media/mount_point

```

when all will work you can edit your fstab

---

### Post by James_N on 2006-07-21
I'll follow your advice and leave it a bit then!

If i got an internal hard drive, would this make writing to NTFS easier?

Many thanks :)

---

### Post by givré on 2006-07-21
sure, cause the name is fix.

---

### Post by geco on 2006-07-21
> **James_N said:**
> I'll follow your advice and leave it a bit then!

If i got an internal hard drive, would this make writing to NTFS easier?

Many thanks :)

You will always risk in writing on NTFS because it not depends on the device type (fix or removable) but on the driver, anyway it will be easier for linux to "remember her name"

you're welcome ;)
byebye

---

