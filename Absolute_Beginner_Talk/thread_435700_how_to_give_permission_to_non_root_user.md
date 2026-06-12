---
title: "how to give permission to non root user"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-05-07
[running ubuntu 7.04]

How would I go about giving my normal user total control (read,write) over a folder?

Basically, It has all my music in it, but I cannot edit the songs tags because they ae read only for me.

Thanks in advance...

---

### Post by justleen on 2007-05-07
is it a NTFS partition by any chance? If so, thats read only.. You'd have to install the ntfs-3g drivers to get access.

If not, the quickest way would be to change the ownership ```
 chown -R username /foldername/ 
```
the -R for recursive..

---

### Post by moredhel on 2007-05-07
when i did this it said:

chown: changing ownership of `/media/hdb1/Music/My Chemical Romance': Operation not permitted

on everything. I also tried with sudo and it said the same thing :(

any ideas?

(and how do i tell what format each drive is?)

---

### Post by seshomaru samma on 2007-05-07
```
sudo fdisk -l 
```
will give you information about partitions

---

### Post by moredhel on 2007-05-07
Ok, It is fat32 as I thought - I thought it would be a quick way for both my xp and ubuntu to access it (as it has all my documents,music etc on it).

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14591   117202176    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4845    38917431    b  W95 FAT32
/dev/hdb2            4846        5100     2048287+  82  Linux swap / Solaris
/dev/hdb3            5101        9729    37182442+  83  Linux
daniel@fingolfin:~$ 

```

^ It is hdb1 ^

So any ideas on how to get this working?

---

### Post by justleen on 2007-05-07
in your fstab, you should mount it with
```
/dev/hdb1 /fat vfat umask=000 0 0
```
where /fat is the dir where you want it mounted

---

### Post by moredhel on 2007-05-07
mounting it isn't a problem, as it has to already be mounted because I can edit/save other files onto it - surely?

---

### Post by moredhel on 2007-05-07
well currently my fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=c801cfe5-5036-4805-b049-5f6fad264df0 /               ext3    
defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=660C824F0C821A67 /media/hda1     ntfs    
defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=45CC-EFD7  /media/hdb1     vfat    
defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=742d9ec7-e15b-486c-b5d1-ac9c51963aef none            swap    
sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by mbirkis on 2007-05-07
.

---

### Post by justleen on 2007-05-07
> **mbirkis said:**
> . yes he did :)


change ```
# /dev/hdb1
UUID=45CC-EFD7  /media/hdb1     vfat    
defaults,utf8,umask=007,gid=46 0       1 
```

to
```
# /dev/hdb1
UUID=45CC-EFD7  /media/hdb1     vfat    
defaults,utf8,umask=000 0 0      1

```

remount the drive, and you should have write access..
(or, make sure your user is in group ID 46..)

---

### Post by moredhel on 2007-05-07
um, how to i remount it and make sure my user is in group id 46?

---

### Post by justleen on 2007-05-07
um, better leave the umask at 000 0 0 :)
that sets it to group 0, which gives everyone access..

to unmount ```
 sudo umount /media/windowsdrivename 
```
to mount ```
 sudo mount -a 
```

---

### Post by moredhel on 2007-05-07
ok, I unmounted without problem, but when I do mount -a it says:

mount: mount point 0 does not exist

and also, i can still open the harddrive, but now it's all read only, where as before only some was.

;_;

---

### Post by moredhel on 2007-05-07
redid it, and now i can't access the umounted one ;)

but still it won't remount :(

here is my fstab incase:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=c801cfe5-5036-4805-b049-5f6fad264df0 /               ext3    
defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=660C824F0C821A67 /media/hda1     ntfs    
defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=45CC-EFD7  /media/hdb1     vfat    
defaults,utf8,umask=000 0 0      1
# /dev/hdb2
UUID=742d9ec7-e15b-486c-b5d1-ac9c51963aef none            swap    
sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by justleen on 2007-05-07
are you sure its on one line?
UUID=45CC-EFD7  /media/hdb1     vfat    
defaults,utf8,umask=000 0 0      1


that should be 
UUID=45CC-EFD7  /media/hdb1     vfat    defaults,utf8,umask=000 0 0

---

### Post by moredhel on 2007-05-07
ok, that's succesfully remounted, but when i right-click > properties >permissions, it's still owned by root.

Plus, the chown still won't work.

---

### Post by moredhel on 2007-05-07
anyone?

---

### Post by justleen on 2007-05-07
its shouldnt matter thats its owned by root, really.. you should be able to write to it..
did you get any more errors on the mount -a (after unmounting the drive)?

Are doing a sudo chown?

---

### Post by moredhel on 2007-05-07
it's working now :)

thanks for your time ;)

---

### Post by justleen on 2007-05-07
glad its fixed!

---

### Post by hellblade on 2007-05-07
fat32 partitions don't support owner, permissions etc so the owner "is" the one who mount it. chown, chmod and the likes do nothing.

---

