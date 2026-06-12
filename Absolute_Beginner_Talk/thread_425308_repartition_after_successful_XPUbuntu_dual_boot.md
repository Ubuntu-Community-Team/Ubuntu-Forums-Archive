---
title: "repartition after successful XP/Ubuntu dual boot"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by patnshan on 2007-04-27
Hello,
I am looking for additional help.  I successfully installed XP Pro and Ubuntu 7.04 on a new hard drive (they both work, they both boot, grub works right) with the help of someone over on the linuxforums.  I was unable to get it to work when I partitioned manually using Gparted.  What I had to do was let the ubuntu installer install itself onto the largest free space available (250GB minus the 10GB XP partition).  My intention was to use 10GB each for the OS's, then use the rest as a FAT32 partition for media that could be shared.  Now, I have a hda2 partition that is much larger than I want.  I want to resize that one into 10GB for the OS (which is installed on it), and then create a new large FAT32 partition.  I was directed to boot into the live CD, which I did. Then to use Gparted to change the partition size (which I tried).  I got an error.  

Here is what I have now:
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 1275 10241406 7 HPFS/NTFS
/dev/hda2 * 1276 30047 231111090 83 Linux
/dev/hda3 30048 30401 2843505 5 Extended
/dev/hda5 30048 30401 2843473+ 82 Linux swap / Solaris
patnshan@basementHTPC:~$ 


Here are details of the error I get (note: I did right click on hda2 to unmount prior to attempting resizing):

The following operation could not be applied to disk:

Resize /dev/hda2 from 220.40 GiB to 9.76 GiB

See the details for more information

Here are the details:
GParted 0.2.5
Resize /dev/hda2 from 220.40 GiB to 9.76 GiB ( ERROR )
check filesystem on /dev/hda2 for errors and (if possible) fix them ( ERROR )
e2fsck -f -y -v /dev/hda2
dev/hda2 is mounted.
e2fsck 1.40-WIP (14-Nov-2006)e2fsck: Cannot continue, aborting.

It appers that the error says the drive is mounted, despite me selecting unmount (right click on hda2, left click unmount)

What do I need to do to get this done?  As of now, XP can only "see" it's own 10GB partition, so I cannot share files between the OS's.

Thanks for any feedback,

Pat

---

### Post by dstew on 2007-04-27
I do not know about Feisty, but in Edgy when you boot the live CD, the hard disks are not mounted unless you tell it to. It is odd that the Feisty live CD causes the disk to mount.

Maybe you can boot a 6.10 live CD, or the GParted Live CD, and try the resize operation that way.

---

### Post by zvacet on 2007-04-27
Download Gparted Live CD.It is very good tool and you will probably use it in the future.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by patnshan on 2007-04-27
Thanks guys (or gals, not sure:D), I will download and burn it when I get home from work.  If that doesn't work, I'll be back.

Pat

---

### Post by patnshan on 2007-04-27
> **dstew said:**
> I do not know about Feisty, but in Edgy when you boot the live CD, the hard disks are not mounted unless you tell it to. It is odd that the Feisty live CD causes the disk to mount.

Maybe you can boot a 6.10 live CD, or the GParted Live CD, and try the resize operation that way.


I am wondering if somehow despite booting with CD, it is using the installed Gparted?????  I am new to this, but just a thought. 

Pat

---

