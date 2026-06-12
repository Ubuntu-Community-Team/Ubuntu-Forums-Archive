---
title: "help me: i've destroyed partitioning"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-09-06
hi,
i had a residual ntfs partition on my hd. Seen that the home started becoming to small for me, i wanted to stretch it and cancelling the ntfs one. I looked for gparted but i couldn't find the cd with it. So i used qtparted and i formatted it in ext3 format. Since that time it seem that i've lost the home. i reboot and it advised me to run fsck (it asked me to rename inode, clear etc ect). Now the partition seen full of 6gb. Before i had 100GB! Then  i cannot login because it says that /home/lillux was missing. So i created it and i changed fstab putting a diesis before ntfs partition line. 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=4aac655b-fe21-4cbf-96a0-87f943ee6907 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=385E-12F0 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb5 -- converted during upgrade to edgy
# UUID=F488A7C788A786A8 /media/hdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb7 -- converted during upgrade to edgy
UUID=8d42df8e-0aa3-4b53-bd73-9425eaa26fca /home ext3 defaults 0 2
# /dev/hdb6 -- converted during upgrade to edg
UUID=ed5f63c5-9a2d-4c76-bfcb-83f018fb773a none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
```

now it says, aftre login,

"the Home/.dmrc of the user will be ignored. That's to avoid to save the session and predefined languages. The file'd have to be owned by the user and to have pewrmission 644.  The directory $Home of the user must be owned by the user and not writeble by other users"

and if i click over ok it says it dosn't continue loading the systems and it says that it impossible to create /.gnome2 because it hasn't the permissions.

 I don't care too much the loss data (most of them is bakuped), but i've not a broadband connession i wouldn't format and install everything again, with my isdn i'd take too much time. And in a month will be release the new ubuntu version...
Then if it's possible to recover the lost data,it's better.
I'm desperate i need my computer working, please help me.
thanks

---

### Post by logos34 on 2007-09-06
Can you mount and read /home (hdb7) on the ubuntu live cd?  If so, copy remaining files to hda1, the fat32 partition.  Also, mount the / root partition and copy **/var/cache/apt/archives **over--it contains all the .deb packages you installed.  It'll save you all that time downloading again.  Then reinstall.  Copy the packages back.

---

### Post by ubunlilluz on 2007-09-07
i've tried to use the only ubuntu live i have: the breezy one, but it mounts only cdrom, not windows partition, no home (on hd). :(

---

### Post by logos34 on 2007-09-07
> **ubunlilluz said:**
> i've tried to use the only ubuntu live i have: the breezy one, but it mounts only cdrom, not windows partition, no home (on hd). :(

type this in a terminal to mount partitions:
> 
sudo mkdir /mnt/hdb1
sudo mount -t ext3 /dev/hdb1 /mnt/hdb1

sudo mkdir /mnt/hda1 
sudo mount -t vfat /dev/hda1 /mnt/hda1

sudo mkdir /mnt/hdb7 
sudo mount -t ext3 /dev/hdb7 /mnt/hdb7

cd /mnt/hdb7/<user>   (gets you into your /user dir on /home partition)

etc,

---

### Post by ubunlilluz on 2007-09-08
> **logos34 said:**
> Can you mount and read /home (hdb7) on the ubuntu live cd?  If so, copy remaining files to hda1, the fat32 partition.  Also, mount the / root partition and copy **/var/cache/apt/archives **over--it contains all the .deb packages you installed.  It'll save you all that time downloading again.  Then reinstall.  Copy the packages back.

once copied back all packages, what's the instruction to install them all?
thanks

---

### Post by logos34 on 2007-09-08
Wait, I think I've got an easier way...There is a application called [APTonCD]("http://aptoncd.sourceforge.net/") which would do all of that for you.  Install it on the live cd into ram, run it and make an image of all the packages. (I hope it will work from the livecd).

-enable 'universe' repos
-sudo apt-get install aptoncd

 The 'metapackes' option is enabled by default, meaning it takes care of dependencies during retore--you just click on it and it drags everyhting back and reinstalls.  Then save the iso/image to the fat32 partition.

---

