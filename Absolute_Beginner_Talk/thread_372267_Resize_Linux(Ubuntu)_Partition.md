---
title: "Resize Linux(Ubuntu) Partition"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by !nvincible on 2007-02-28
Hi All,

      I am running short of space in my Ubuntu Partition I just want to resize my partition to provide extra space 
When issue parted command it gives me following structure of Harddrive

[COLOR="Blue"]Disk geometry for /dev/hda: 0kB - 40GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    5240MB  5239MB  primary   ntfs         boot
2       5240MB  40GB    35GB    extended               lba
5       5240MB  10GB    5239MB  logical   fat32
6       10GB    16GB    5239MB  logical   fat32
7       16GB    17GB    1053MB  logical   linux-swap
8       17GB    27GB    10GB    logical   fat32
9       27GB    39GB    12GB    logical   ext3
10      39GB    40GB    1020MB  logical   ext3[/COLOR]

In this case I want to merge my 9 and 8 partition since I have nothing important in **partition no 8** I can even format it...so no issue regarding that, but the problem is I am having linux partition in **partition no 9 ** and when I issue **resize 9 17GB 39GB** command it gives me an error ...

This is I get when I do fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        4865    33961410    f  W95 Ext'd (LBA)
/dev/hda5             638        1274     5116671    b  W95 FAT32
/dev/hda6            1275        1911     5116671    b  W95 FAT32
/dev/hda7            1912        2039     1028128+  82  Linux swap / Solaris
/dev/hda8            2040        3314    10241406   83  Linux
/dev/hda9            3315        4741    11462346   83  Linux
/dev/hda10           4742        4865      995998+  83  Linux


**How can I solve this problem**
Thankx in advance...

---

### Post by louis_nichols on 2007-02-28
EXT3 isn't extendible, unless you use LVM. My suggestion would be to simply format your 8 partition a ext3 and mount it in some convenient folder. It will save you some trouble.

---

### Post by steven8 on 2007-02-28
> **louis_nichols said:**
> EXT3 isn't extendible, unless you use LVM. My suggestion would be to simply format your 8 partition a ext3 and mount it in some convenient folder. It will save you some trouble.

Sorry to intrude, but this statement brings up a question.  I have not yet deleted my windows partition, but everyone tells me it's easy and then you let linux take up the whole space.  Now, are you saying I can't increase the size of my linux partition to fill the empty space if I delete my windows partition?

---

### Post by bodhi.zazen on 2007-02-28
I think you can resize your partitions with gparted, either with the ubuntu desktop CD or the gparted live CD.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Resize a partition : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)

---

### Post by steven8 on 2007-02-28
I know that gparted is the tool to use.  No problem there.  This just made me worry that I might not be able to increase the size of my ext3 partition to fill the available space.

---

### Post by bodhi.zazen on 2007-02-28
The only problem I could foresee is you can not resize a partition if it is mounted.

Thus, for your root partition, you will need to resize from a live CD.

Otherwise I've done it all with the gparted live CD, it is a handy tool.

---

### Post by STREETURCHINE on 2007-02-28
yes you can with gparted i recently resized all mine with no problems,

got rid of fedora,suse,and mandriva and made one partition as fat 32

---

### Post by steven8 on 2007-02-28
Whew!  I got scared there for a moment. :)  I will, of course, use the livecd.  I would never dream of making those kind of changes while in the system.  

Thanks guys!

---

### Post by louis_nichols on 2007-02-28
> **bodhi.zazen said:**
> I think you can resize your partitions with gparted, either with the ubuntu desktop CD or the gparted live CD.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Resize a partition : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)

All that shows me is how Gparted resizes a ntfs partition. 2 years ago I wanted to resize an ext3 partition and I had to do it the hard way: backup all data, delete the partition, merge it with some other empty space, reformat as ext3, then restore data.

Sorry if I am wrong on this (I really wish I am actually, as it raises some nice possibilities), but I wouldn't want to give anyone false hopes. Nowadays, I use and VERY STRONGLY recommend LVM, with reiserfs. It allows resizing logical volumes on the fly, without even unmounting them or as little as logging out. When a new physical volume comes along, you can hotplug it, add it to a volume group and then just resize logical volumes to occupy that space.


[QUOTE=steven8]Sorry to intrude, but this statement brings up a question. I have not yet deleted my windows partition, but everyone tells me it's easy and then you let linux take up the whole space. Now, are you saying I can't increase the size of my linux partition to fill the empty space if I delete my windows partition?[/QUOTE]

There is no real difference between really resizing a partition and just mounting another one in a folder. It's as easy as creating the folder and then making a few clicks.

---

### Post by steven8 on 2007-02-28
What is "LVM, with reiserfs"?

---

### Post by bodhi.zazen on 2007-02-28
[QUOTE=louis_nichols;2224581]2 years ago I wanted to resize an ext3 partition and I had to do it the hard way: backup all data, delete the partition, merge it with some other empty space, reformat as ext3, then restore data./QUOTE]

That was then, this is now. the gparted live CD will resize an ext3 partition no problem.

Your information on that is out-of date ;)

steven8: LVM = Logical Volume Management

[http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

---

### Post by louis_nichols on 2007-02-28
LVM is short for [Logical Volume Management]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29"). Here is a [howto ]("http://tldp.org/HOWTO/LVM-HOWTO/")on how you can use it. You can safely jump to the chapter on [common tasks]("http://tldp.org/HOWTO/LVM-HOWTO/commontask.html"), which contains most of the good stuff. Reiserfs is a filesystem. It is recommended because it allows, as I said, to resize the filesystem without un(re)mounting, as explained [here]("http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html").

In short, here's how it works:
I have 3 or 4 partitions on my HDD (funny that I don't even remember anymore :) ). These are remnants of the dual booting I used to do. Now, GRUB needs it's own partition, not under LVM, so I gave it a 100MB partition with ext3. The other partitions are merged in what LVM sees as a volume group. Such a volume group can contain any number of partitions and/or entire hard disks in any combination. All this will be seen by the system as one "partition". Then, this volume group can be re-divided into logical volumes, which will be seen by the system as partitions.

How do I use it?
Well, I installed Ubuntu on a 2gig logical volume and allocated 5 gigs for /home. The rest of my HD was unused at the time, except for some 20gigs used by windows. Then, I resized both the logical volume for / and the one for /home as needed. At one point, I decided to remove windows completelly and added that partition to my volume group. I now have more space to allocate. I do this on a need-to-use basis. I just resize / and/or /home with 1 or more gigs at a time. It's fun and very flexible. If I later buy another HDD, I can just plug it, without even shutting down the system, then add it to the volume group and start allocating that space too. It's much less hassle than resizing partitions.

---

### Post by steven8 on 2007-02-28
> **bodhi.zazen said:**
> [QUOTE=louis_nichols;2224581]2 years ago I wanted to resize an ext3 partition and I had to do it the hard way: backup all data, delete the partition, merge it with some other empty space, reformat as ext3, then restore data./QUOTE]

That was then, this is now. the gparted live CD will resize an ext3 partition no problem.

Your information on that is out-of date ;)

steven8: LVM = Logical Volume Management

[http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

> LVM is short for Logical Volume Management. Here is a howto on how you can use it. You can safely jump to the chapter on common tasks, which contains most of the good stuff. Reiserfs is a filesystem. It is recommended because it allows, as I said, to resize the filesystem without un(re)mounting, as explained here.

In short, here's how it works:
I have 3 or 4 partitions on my HDD (funny that I don't even remember anymore  ). These are remnants of the dual booting I used to do. Now, GRUB needs it's own partition, not under LVM, so I gave it a 100MB partition with ext3. The other partitions are merged in what LVM sees as a volume group. Such a volume group can contain any number of partitions and/or entire hard disks in any combination. All this will be seen by the system as one "partition". Then, this volume group can be re-divided into logical volumes, which will be seen by the system as partitions.

How do I use it?
Well, I installed Ubuntu on a 2gig logical volume and allocated 5 gigs for /home. The rest of my HD was unused at the time, except for some 20gigs used by windows. Then, I resized both the logical volume for / and the one for /home as needed. At one point, I decided to remove windows completelly and added that partition to my volume group. I now have more space to allocate. I do this on a need-to-use basis. I just resize / and/or /home with 1 or more gigs at a time. It's fun and very flexible. If I later buy another HDD, I can just plug it, without even shutting down the system, then add it to the volume group and start allocating that space too. It's much less hassle than resizing partitions.

Great information.  Thanks!

---

### Post by louis_nichols on 2007-02-28
> **bodhi.zazen said:**
> [QUOTE=louis_nichols;2224581]2 years ago I wanted to resize an ext3 partition and I had to do it the hard way: backup all data, delete the partition, merge it with some other empty space, reformat as ext3, then restore data./QUOTE]

That was then, this is now. the gparted live CD will resize an ext3 partition no problem.

Your information on that is out-of date ;)

steven8: LVM = Logical Volume Management

[http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

OK. Thanks for the update! It's good to know. And sorry for the wrong info earlier. I haven't really tried to update that info, since I started using LVM.

---

### Post by bodhi.zazen on 2007-02-28
> **louis_nichols said:**
> [QUOTE=bodhi.zazen;2224630]

OK. Thanks for the update! It's good to know. And sorry for the wrong info earlier. I haven't really tried to update that info, since I started using LVM.

LOL, no problem. I am always learning myself, that is what I love about these forums.

---

### Post by !nvincible on 2007-02-28
Thankx for your reply...sorry for delay .
I am unable to understand why fdisk and parted are showing different filesystems for hda8??:confused: 
And I had tried with live CD of Ubuntu but couldn't get success ,I think because of this filesystems:confused:

---

### Post by Elaztic on 2007-03-10
Have you tried with gparted live cd?
You can read more about it and get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

