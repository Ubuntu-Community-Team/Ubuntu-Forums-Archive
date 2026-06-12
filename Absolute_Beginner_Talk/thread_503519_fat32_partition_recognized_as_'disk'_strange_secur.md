---
title: "fat32 partition recognized as 'disk' strange security issue"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by lbthrice on 2007-07-18
hi all,

i spent a good amount of time googling this issue today bit did not find anyone with the issue that is frustrating me:

I just partitioned my 60 gig laptop harddrive (dell inspiron 700 m), installed xp, then ubuntu 7.04.  I had made a logical partition formatted as fat 32 as a shared data drive for the OSs also.

Here's the issue:

gparted had some issue with formating the logical partition and I chose to have it mount as /windows.  that worked fine.

then I thought i would try to get a little fancy pants and try to edit the old fstab to make it mount in  /media/sda6....because I wanted it to appear on my desktop with the dell utility and the sda2 windows partition...i just changed the mount point in the fstab from /windows to /media/sda6...(i made the /media/sda6 directory first).  

after i did that it made the drive appear only in the "computer" window that can be selected under the 'places' menu on the desktop...  it appears as '27.5 gb volume' there...and when i click on it it asks for my password before i can gain access....after i acces it it then appears as 'disk' in the computer window.

it works ok just inconvient to not have it appear on the desktop and to have it be password protected...also i am curious about these shenanigans

I wonder if anyne knows what is going down?

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ad1979bd-bd2c-4946-9441-51db62733c2a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-0804  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=92CC5000CC4FDD5B /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8ECD-3918  /media/sda6        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=16443ba8-d936-4c5b-b08f-9b5e14b8a67c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0 
```


fdisk -l:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
```
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        1918    15358140    7  HPFS/NTFS
/dev/sda3            1919        3448    12289725   83  Linux
/dev/sda4            3449        7296    30909060    5  Extended
/dev/sda5            3449        3703     2048256   82  Linux swap / Solaris
/dev/sda6            3704        7296    28860741    b  W95 FAT32
```

---

### Post by Foxmike on 2007-07-23
The partition is not mounted by default. That is why when you double-click on the drive under the "Computer" window, GNOME is asking you for a password. It tries to mount your partition, but because mounting a partition is an administrator task, GNOME is asking you for a password.
 
Now, the left column of your fstab is representing the physical partition to mount. It is referred by an ID number provided and recognized by udev. I suspect that ID number no longer being used, that is why your partition is not auto-mounted. You can use the block special file under /dev to refer to your partition in fstab. To do so, make this line:
```
UUID=8ECD-3918  /media/sda6        vfat    defaults,utf8,umask=007,gid=46 0       1
```
look like this:
```
/dev/sda6  /media/sda6        vfat    defaults,utf8,umask=007,gid=46 0       1
```
Then, in a terminal, do:
```
sudo mount -a
```
Then, your partition should correctly appear on your desktop.
 
Now, did you know that there is a driver that allows you to use an ext2fs partition in Windows? It worked well for me back when I was dual-booting with Windows, it might sork for you as well! Here it is:[http://www.fs-driver.org/](http://www.fs-driver.org/)
 
Good luck!:)

---

### Post by lbthrice on 2007-08-13
Thanks FoxMike!  :)  all is well...also, thanks for the tip on the extfs driver!

---

