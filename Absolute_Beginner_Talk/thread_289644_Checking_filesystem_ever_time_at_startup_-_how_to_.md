---
title: "Checking filesystem ever time at startup - how to disable?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by pjotter on 2006-10-31
Hi everyone,

Everytime I boot, Filesystems are being checked. I dont think this is normally, because this check only has to run every 30 boots.

I ran tune2fs to change the check interval, but I got the next message:
 sudo tune2fs -l /dev/hda2
tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/hda2
Couldn't find valid filesystem superblock.

"$ sudo gedit /etc/fstab" gives me the next info:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

I think the root is ok, but I'm a linux-noob so I hope you can see the problem and have a solution.

thnx
Pjotter

---

### Post by kidders on 2006-10-31
Hi there,

tune2fs is part of the Linux Extended filesystems' utils package, so it won't be of much use with FAT :-(

Afaik FAT filesystems can be flagged as unclean by an OS, prompting a filesystem check. The flag doesn't seem to want to clear on your /dev/hda2, possibly because Linux tends to run checks before it's mounted filesystems in read/write mode. If I were you, I'd install the FAT filesystem tools, or maybe run chkdisk in Windoze (if you have it).

---

### Post by pjotter on 2006-10-31
Hey kidders,

Thank you for your reply. The windows chkdsk returns no errors or problems.
Could you be a bit more specific on the FAT filesystem tools, where can I get these? or how do I use them?

thnx!

---

### Post by kidders on 2006-10-31
Hmm... If Windoze says there's nothing wrong with the filesystem, I'd be inclined to believe it. So much for my suggestion :-( Is there anything posted in your dmesg that might help?

If you're looking for FAT filesystem tools for Linux, I think [http://packages.ubuntu.com/dapper/otherosfs/dosfstools](http://packages.ubuntu.com/dapper/otherosfs/dosfstools) is what you need.

---

### Post by pjotter on 2006-11-01
Thnx kidders, 
there was a problem with differences between flesystem and its backup. I solved it by the actions described in: [http://ubuntuforums.org/showthread.php?t=32531](http://ubuntuforums.org/showthread.php?t=32531)

I hope this is a proper solution, or trick....

thnx again
bye!

---

