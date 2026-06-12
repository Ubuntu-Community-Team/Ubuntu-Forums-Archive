---
title: "Do I need a shared partition on a dual boot?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Bombdogs on 2007-01-24
Hi all,

Finally made my first tentative steps in the wonderful world of linux last night.... lots to learn it seems....

Anyway I set up a dual boot on my laptop & was advised that a FAT32 partition for sharing between windows & ubuntu would be a good thing to do.

Installed everything OK, but I haven't worked out how to access the FAT32 partition yet... something to do with editing fstab if I'm reading it correctly.

But I noticed that I could access the windows NTFS partition directly anyway & copied some files from there which seem to work OK.

So, do I even need the FAT32 partition? Seems not to me, but thought I'd ask in case I'm missing something.

Many thanks,

PMF

---

### Post by Pobega on 2007-01-24
If you plan on sharing files between the two, yes. It's much safer to do it through FAT32, since Linux can natively read/write from it.

Don't make the FAT32 too big though; 2GB should suffice.

---

### Post by phiphedog on 2007-01-24
You need to mount the partition in Linux to be able to see it.

your hard disk partitions are named as follows:
The 1st primary partition on an IDE drive is hda1 the second prmary is named hda2 the third primary partition is called hda3 and the fourth hda4

if you install qtparted with the command
**apt-get install qtparted**
run it as root ( **sudo qtparted** ) and it will tell you what your fat32 partition is named

you then need to create a folder to mount it in 
             **mkdir /share**
or whatever you want to name it
you can then mount the partition in the /share folder with the following command
             **mount /dev/hda -t vfat /share**
(that's assuming your fat32 partition is named hda)
you should now be able to see the files in there using
              **ls /share**

You can make it mount at atsartup by adding the following line to your /etc/fstab file
[B]/dev/hdb1	/share3		vfat	defaults,rw		0	0
[/B]

---

### Post by Pobega on 2007-01-24
He's not asking how to do it, he's asking if it's worth using a FAT32 partition to swap data.

---

### Post by Bombdogs on 2007-01-24
Thanks for the quick replies. The walkthrough of how to do it is still appreciated, the more times I read the process the easier I'll be able to do it when the time comes.

I will definitely need to share files => media, blender & python files mainly. So, the upshot is I do need it then?? When you say it's safer, is that from a security point of view or from a reliability point of view? As I say it seemed to read from the NTFS partition perfectly well last night.

Currently I have it at 5gig (the size of a DVD) which I thought was sensible. Lot of space to waste on a smallish laptop drive though, so if it's possible to do away with it that would be my prefered option.

Thanks again,

PMF

---

### Post by Pobega on 2007-01-24
Well, it's safer to use FAT32 because I'm not sure if NTFS is 100% supported. Also, it makes it much easier to share the files, and in my opinion it's easier to just share data through a third partition rather than keeping it on a Linux or Windows folder within the ext3/NTFS filesystems.

---

### Post by bodhi.zazen on 2007-01-24
One other option is to install a driver to windows to allow access to ext2/3.

See these links:

ntfs read-write AKA ntfs-3g : [http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009)

ntfs-3g is "beta"

Ext3 on windows : ttp://www.fs-driver.org/

HTH

A FAT 32 partition will be stable rw access form both OS.

In the end it is up to you.

The only other caution is scan any file you transfer from Linux to Windows ...

---

### Post by houstonbofh on 2007-01-24
I do not use a FAT32 partition.  The Linux NTFS RW driver is much better now with the new config tool. [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)  And you can RW ext2/3 fs from Windows quite well now. [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)  No longer a need to break up the HD into even smaller chunks.

---

