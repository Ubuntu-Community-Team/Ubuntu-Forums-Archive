---
title: "slimserver on ubuntu 6.06"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by thoeng on 2006-10-07
Hi all,

Is there anybody here who is using slimserver on ubuntu??
i tried to download and install it and so far its been successfull however i don't know how to tell the server where is my music folder :(
i tried with /media/hda2/music (its d:/my files/music on windows) but server still does not recognized it. Some people said perhaps that my disk still unmount or slimserver does not have permission yet so how do i check those possibility out ?

my HD condition is partition:

1. windows NTFS
2. media FAT32
3. linux EXT3
4. swap

---

### Post by btdown on 2006-10-07
Are you able to navigate to, and play music from your windows partition from Ubuntu (using Rhythmbox or another music player)?

Please post the contents of your /etc/fstab file.
BT

---

### Post by thoeng on 2006-10-07
Yes and yes. i am able to view as well to run it on xmms apps. music also sounds well with no detected problem.

this is my fstab content:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


there was a guy who recommend me to slip some code on fstab file but i can't do that as my user (eri) does not allow me to write on this file (with reason i am not the owner) but i am the owner !!! 

BTW slimserver running fine without a glitch. thanks for the reply mate.

---

