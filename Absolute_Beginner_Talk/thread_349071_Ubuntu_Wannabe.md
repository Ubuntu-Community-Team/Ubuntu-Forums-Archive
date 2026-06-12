---
title: "Ubuntu Wannabe"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-01-29
I want to move from MS (Win 2000) and have established a duel boot on my primary disc as a staging post.  However Win 2000 lets me read/write to Data on my FAT 32 Ancillary Hard Disc, but Ubuntu in Disk Manager displays:

Access Path: none

and

Status: Inaccessible

Is this why i can't r/wr to the same data from Ubuntu? 

Please tell me how can i remedy it?

Also; clicking on my HD 2 in Computer Browser, i get

“Unable to mount selected volume”

and Properties reveals:

Read
Read
Read
only.

I presume u'd like to see


Code:

sudo fdisk -l

AND
Code:

cat /etc/fstab

Which are...

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2932 23551258+ 7 HPFS/NTFS
/dev/hda2 3825 6374 20482875 83 Linux
/dev/hda3 2933 3824 7164990 f W95 Ext'd (LBA)
/dev/hda5 * 2933 3783 6835626 83 Linux
/dev/hda6 3784 3824 329301 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 2 19457 156280320 f W95 Ext'd (LBA)
/dev/hdb5 2 19457 156280288+ b W95 FAT32

Disk /dev/sda: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3932 1006576 e W95 FAT16 (LBA)
nnjond@nnjond-desktop:~$
nnjond@nnjond-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
nnjond@nnjond-desktop:~$


Thankyou for your interest.

---

### Post by Spr0k3t on 2007-01-29
The partition doesn't look like it's fat32, rather NTFS.  There is a very good guide in the forums here on how to setup NTFS partitions as read/write.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Oh yeah, once you have NTFS readable, you will need to make sure the drive is not using compression, otherwise you will not be able to write to it as well.

---

### Post by nnjond on 2007-01-29
Thankyou for your reply. 

As i understand it, my data is on an ancilary disc and is FAT 32. My Primary is NFTS with the Duel boot. MS r/wr to the Data, y not Dapper?

---

### Post by Spr0k3t on 2007-01-29
Perhaps I would understand it better if I knew what the ancilarry thingy is.  Give me a laymans terms of your config and how it's all attached.

Dapper is a good release, I just haven't used it myself.  I try to be more of the cutting edge but without the bleeding part.  I've only used Ubuntu for a little under two weeks.

---

### Post by ultima on 2007-01-29
This is more likeky to do with permissions. 

can you run

ls -l /media/hdb5 

where hdb5 is the partition/s you want to be able to write to. Let me know the output and I'll tell you is its a permissions problem :)

It will give you a read out similar to lrwxrwxrwx 1 root root

---

### Post by ultima on 2007-01-29
Actually, looking more closely it appears that you don't have any fat32 drives in /etc/fstab

You need to add something like

/dev/hda3       /media/hda3     vfat    rw,defaults,user,gid=1000,umask=0222 0

just replace hda3 with the partition you want mounted.

---

### Post by nnjond on 2007-01-29
I have a Primary Hard Drive useualy called "C". This is partitioned in order for my Duel boot to exist. In addition i have a separate, physical, Slave or ancillary hard drive, "F" witch is FAT 32 and has my data on it. But i cannot r/wr to it in while in Dapper.

---

### Post by nnjond on 2007-01-29
Re; ls -l /media/hdb5 

I typed that in Terminal and got..

: No such file or directory

---

### Post by ultima on 2007-01-29
Okay by the looks of it the partition you want to mount is /dev/hdb5 
Just to verify this is the 160Gb Hard drive.

so try this

Open a terminal

open /etc/fstab
```
sudo gedit /etc/fstab
```

and add the following line to fstab
```
/dev/hdb5 /media/hdb5 vfat rw,defaults,user,gid=1000,umask=0222 0
```

and then save it

you will also want to make sure /media/hdb5 exists
(if you get an error on this command is okay it just means the directory already exists)
```
sudo mkdir /media/hdb5
```

You may need to reboot but you should now be able to access the drive.

---

### Post by nnjond on 2007-01-30
Is this what my fstab should look like?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto   
/dev/hdb5 /media/hdb5 vfat rw,defaults,user,gid=1000,umask=0222 0  0       0

I was unable to open/mount the 160g HD.

I got no reply to:	sudo mkdir /media/hdb5

---

### Post by nnjond on 2007-01-30
Wait, maybe i typed too soon.

---

### Post by igknighted on 2007-01-30
Just for future reference, these are what all the columns in fstab mean:

col 1) path to partition (e.g. /dev/hda1)

col 2) mount point (e.g. /media/hda1)

col 3) file system (e.g. ext3 or vfat)

col 4) mount options (e.g. rw (read/write), or I usually just use 'defaults')

col 5) dump... in almost all cases leave this as 0

col 6) fsck, tells the system how often to check the file system (e.g. 0 (for never), use 1 for root partition, use 2 on other partitions if you want them checked periodically (always a good idea))

hope this helps, I stole it from Gentoo way back when and it stays on a post it note on my desk because I never know when I'll need it.

---

### Post by jvc26 on 2007-01-30
You wont get any reply to sudo mkdir x commands as they just make the directory and then the command finishes. Has your mounting completed successfully. It could be that it didnt work this time as you didnt have that directory when you added the lines to fstab, and now you have then on rebooting it may work.
Il

---

