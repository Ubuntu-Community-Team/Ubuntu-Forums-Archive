---
title: "How to mount and show my other hard drives...?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by VimesUK on 2007-03-04
Hello

I am quite new to this and so I have now managed to get Ubuntu installed on my hard drive (IDE) and I have three other SATA drives.

All that I'm seeing as available to me when I open up Computer (under Places) is my optical drives, card reader, floppy and one called file system.

I know when I tried PC Linux I just showed all of my hard drives on my desktop and was able to access them as well, even though the three SATA drives are NTFS formatted.

So how is it possible (simply I hope) to have the equivalent of being able to see and access my other hard drives and my other partitions on the IDE drive that I have installed Ubuntu on...? 

Also how do I resize any of my partitions on my IDE drive, I did have the use of Gparted when using the LiveCD, where is that now...?

I did open a terminal window and type sudo fdisk -l

/dev/sda1   *           1        2630    21125443+   7  HPFS/NTFS
/dev/sda2            2631       24792   178016265    f  W95 Ext'd (LBA)
/dev/sda5            2631       24792   178016233+   7  HPFS/NTFS

/dev/sdb1   *           1       30515   245111706    7  HPFS/NTFS

/dev/sdc1   *           1        2199    17663436    7  HPFS/NTFS
/dev/sdc2            2200       19929   142416225    f  W95 Ext'd (LBA)
/dev/sdc5            2200       19929   142416192    7  HPFS/NTFS


/dev/hda1               1        1306    10490413+   c  W95 FAT32 (LBA)
/dev/hda2   *        1307       29644   227624985   83  Linux
/dev/hda3           29645       30401     6080602+   5  Extended
/dev/hda5           29645       30401     6080571   82  Linux swap / Solaris


Thanks for any help

---

### Post by annda on 2007-03-04
gparted is in the repositories, you can install it through synaptic.

as to mounting your other drives, you will have to manually modify your /etc/fstab file
explanations and instructions are here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by basho007 on 2007-03-04
I'm having the same issue with seeing partitions in Ubuntu.   my machine picks up the Linux partition, cd rom and external USB devices.  

you want to find out about a file called fstab, probably found in etc/fstab.

first thing is to look at it and understand what it all means. 

then you can edit it to add the partitions you want mounted.  

make a backup!   

sudo cp /etc/fstab /etc/fstab.backup


there is a lot of good help available by google.

here's one link

[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29)

---

### Post by VimesUK on 2007-03-04
Thanks so much for the advice from both of you :)

When I used Windows I just played games, now I play at Linux :D

I have now got and used Gparted but, due to me, I have got dev/hda2 as my / drive (boot) which is locked and that is 217GB in size and 6GB used - would it be possible to change that say to 40GB and then create a FAT32 partition from the rest..?

---

### Post by annda on 2007-03-04
of course you can, but you cannot resize a mounted partition, since you are working on it.

get gparted live cd
gparted.sourceforge.net
and boot from that to resize your current ubuntu partition.

---

