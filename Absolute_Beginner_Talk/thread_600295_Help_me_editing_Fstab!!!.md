---
title: "Help me editing Fstab!!!"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Gstyle on 2007-11-02
Hi!
I installed Ubuntu yesterday, creating 4 partitons on my 40Gb HDD drive.
They work fine, but how can I see them under Computer as seperate hard disks.
Also I want to change mount points to different directories, like Music, Movies.
Thanks!
P.S. Sorry for my bad English, I am Latvian! :)
Here goes my fstab:
----------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8c207f0-681d-4538-9a12-6ac31fffa348 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=61ee8309-b1b9-46a8-bd44-019c7a9bd4c7 /home           ext2    defaults        0       2
# /dev/sda3
UUID=4bd8ab84-9543-4785-b561-090b12b161dd /usr            ext3    defaults        0       2
# /dev/sda4
UUID=05a83bbf-88e4-441a-855c-094c21ff896b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
-----------------------------------------------------------------------------------------------------

---

### Post by julian67 on 2007-11-02
I'm not using Gnome so I won't answer about how Gnome desktop displays drive/partition icons.

Changing Mount Points

I can only see 3 partitions and swap on your fstab. I doubt you should change any of those. I assume your directories like Movies and Music are somewhere in ~/ ? Why not just use the Nautilus bookmark/favourites facility and have direct access to them via an icon or a launcher?

If you do have some other drives that are not shown in the fstab you posted then you can simply edit /etc/fstab to change the mount points, create the folders in ~/ and then reboot. I'll show you my /etc/fstab as an example:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=12b62fe1-3d9a-4836-8d1d-7dc7130b7642	/	ext3	defaults,noatime,errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=3843518f-76a5-4f5d-be13-ef88b6ca694f	/home	ext3	defaults,noatime	0	2
#Entry for /dev/sdb3 :
UUID=cf5e0cc2-8713-410e-a3fd-73851132203c	/home/julian/Photos	ext3	defaults,noatime	0	2
#Entry for /dev/sdb2 :
UUID=aacc74c6-678a-4612-8304-2e9eadbf8b80	/home/julian/lossless	ext3	defaults,noatime	0	2
#Entry for /dev/sdb1 :
UUID=29114b58-8387-411e-a099-9fde9cf12be1	/home/julian/music	ext3	defaults,noatime	0	2
#Entry for /dev/sda2 :
UUID=c669cd77-10b6-4274-9c8e-fb494f6e34e2	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto	0	0



```

You can see I have a second hard disk with 3 partitions (lossless, music, Photos) and each of those partitions is mounted in ~/  where they appear as directories.

If your Music and Movies folders are already simply directories in ~/ then that would seem ideal. I would leave them like that.

---

### Post by jw5801 on 2007-11-02
Umm... for starters, [please don't make two threads about the same issue](http://ubuntuforums.org/showthread.php?p=3690111)

Secondly, moving these partitions at this point is a VERY bad idea, unless you're going to copy everything that is in /usr to a new /usr folder on the root partition and similarly with /home. You can't make them appear as "separate drives" under the Computer menu. This isn't Windows! You can create a soft link to it's mount point in the directory that makes up the Computer folder if you want. But it's much easier to simply right click on it and make it a bookmark/favourite in nautilus, then it will appear under the Places menu anyway!

If you want to change the mountpoint of those partitions at this stage, then you're going to need to boot off a LiveCD, mount the three partitions, copy everything on the old /usr partition to the /usr directory on the first partition, you'll have to use the command line so you can easily give it root permissions however. So, if this is still a relatively fresh install, then it's probably easier just to start over. Tell the installer to use the first partition (/dev/sda1) as / and then install there. Then after the install has run, all on that partition, add a couple of folders like ~/music and ~/movies or whatever you like and edit your fstab accordingly as suggested above!

---

