---
title: "How can i use my windows partition disk"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-03-28
I am using linux on different disk...
On the other disk i have all my files and music..but there is my windows partiotion in NTFS format..
The ubuntu dont see or recognise at all the other disk...
What can i do to use them..?

---

### Post by taurus on 2007-03-28
You need to mount it before you can access it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by tyboon on 2007-03-28
Thanks..i tried that..i got a folder named widows..but it appears to be empty...
How was it supposed to look...i dont know..i am really a beginner..just installed yesterday tryin to get rid windows once and for all..
may be i did something wrong..
Can you help me out please..
Thanx..

---

### Post by dstew on 2007-03-28
Let's try something simple first, just to mount the ntfs partition using the command line. You need to know the name of the partition first. You can get a list of your partitions, with their names, by entering **sudo fdisk -l** on the command line. It will prompt you for your password, then display the list. Do that and post the list to this forum. Then we can make the correct mount command for you.

---

### Post by wgw on 2007-03-28
I have forgotten how I got it working (and for the moment, it is still read only), but here are the links I sifted through:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

and 

[http://www.ubuntuforums.org/showthread.php?t=217009&page=2&highlight=Deficient+FUSE+kernel+module+detected](http://www.ubuntuforums.org/showthread.php?t=217009&page=2&highlight=Deficient+FUSE+kernel+module+detected).

I believe I had to use the fuse thingy...Sorry I can't be more specific. It is a bit of a blur, but I think it took a bit of fiddling (welcome to linux world...). BUT! it does work, finally! (Though, as I said, I still have some work to do to get write permission -- yes, now I remember, that was why I got the fuse package; for write support. )

---

### Post by NicoleM on 2007-03-28
the fuse thing is automatically added to the fstab if you run the ntfs-g configuration utility (not sure about manual configuration)

i'm pretty sure that's only an issue if the original poster wants write access to his NTFS partition.

once he gets it mounted though it's definitely the next logical step.

---

### Post by tyboon on 2007-03-28
hvasss@hvasss-desktop:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/hda5            3825       11600    62460688+   7  HPFS/NTFS
/dev/hda6           11601       19456    63103288+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris

WGW this is what i get...
if you could help me or anybody else ..i d be most thankfull

---

### Post by dstew on 2007-03-28
You have three different NTFS partitions, named /dev/hda1, /dev/hda5, and /dev/hda6. To mount a partition on your linux filesystem tree, you have to select (or create) a directory to serve as a mount point. I think from your post you created the directory /windows, so we can use this as a mount point. Enter the following command into the terminal:

sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/hda1 /windows

If it gives you an error message, please post it. If not, go to the windows directory and see if you can see any files.

---

### Post by tyboon on 2007-03-28
thanks mate...
that worked just fine...
i really appreciate....
do you know anything about tha ATI drivers for linux...?

---

### Post by tyboon on 2007-03-28
what about the other partitions?I cant see my D local disk and F local...do you think i should do the same things as before..?

---

### Post by wgw on 2007-03-28
Yep: whole process (with different directory names like /windowsF and /windowsD to go along with the different hda), at least for hda5 and hda6 -that is the case -- I'm not sure what to do with hda2.  Probably the same thing. But I would wait for a more knowledgeable reply for that....

---

### Post by dstew on 2007-03-28
The word on the street is use envy for ATI driver setup:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

