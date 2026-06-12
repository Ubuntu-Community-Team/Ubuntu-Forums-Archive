---
title: "Need help editing fstab..."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by whoami1988 on 2007-08-12
I am having problems mounting burned dvds. If I leave my fstab as is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8cd09ea4-e41c-4b99-b431-d463c1dd6fe5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1A9913452A715227 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=08f8a1de-35ad-45d4-920f-7a257e13f9d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

When I put in a dvd-r, my filesystem recognizes the dvd as CD-ROM 1, but it says that it cannot mount it because:

> mount: block device /dev/scd0 is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/scd0,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

My workaround is getting annoying. I use 

> sudo mount -t udf /dev/scd0 /media/cdrom0/ to mount, and 
> sudo umount /media/cdrom0 to unmount. This mounts as CD ROM 1: ISO 9660 Volume.

How can I edit my fstab, so that the drive mounts automatically. I don't have this problem with cd's... if that helps any. Also, VLC won't play the avi's (I don't know if that's just a problem with vlc or it not recognizing the burned dvd), but Miro plays the files. 

Thanks so much, and if you have a solution, please be detailed because I'm still fairly new to the command line and filesystem of linux. If any other information is needed, I would be happy to post it. 

;9

---

### Post by creedog on 2007-08-12
is it just me or are you trying to mount it as two different filesystems in the fstab...?


Also, why is it not automounting?

---

### Post by whoami1988 on 2007-08-12
If I'm mounting as 2 separate filesystems, it is totally unintentional. This is the only way I have been able to access the files on the dvd. If it helps... k3b doesn't recognize it either. Others have said that they have been able to mount the dvd via k3b and then access the files.

---

### Post by whoami1988 on 2007-08-12
btw, sda1 is my windows partition. Is that what you thought my 2nd filesystem was?

---

### Post by creedog on 2007-08-13
no I was looking that this entry from your fstab

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


See udf and iso9660

but when you are mounting it manually you are only using udf

sudo mount -t udf /dev/scd0 /media/cdrom0/


Try removing the iso9660 from the fstab and trying again.

---

