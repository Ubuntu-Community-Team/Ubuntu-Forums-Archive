---
title: "Need some help making major changes"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2007-03-20
I am looking at making some major changes to my ubuntu install.

1) Set-up my Home dir in its own partition.
2) reinstall Edgy as the Ubuntu Ultimate Edition latest release
3) profit

Currently I don't have the know how or exp to properly learn and install all the current apps I want, and UUE seems to offer a lot to the linux layman.  Saying that, I have a few road bumps that present themselves and they are what prompted me to ask for advice during this process.

1)I have a dual boot machine and I do not want to lose that
2)I want to put the home dir on the HD that XP currently resides on

I have a vague idea on how to go about this adventure, and the first step would be to make an ext 3 partition on XP's HD for my home dir.  I will wait on advice.

fdisk

>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12043    96735366    7  HPFS/NTFS
/dev/hda2           12044       14593    20482875    b  W95 FAT32

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7109    57103011   83  Linux
/dev/hdb2            7110        7297     1510110    5  Extended
/dev/hdb5            7110        7297     1510078+  82  Linux swap / Solaris


---

### Post by dbbolton on 2007-03-20
if you do a fresh install from a livecd, you can use Gparted to set up the partitions you need, then it will ask you which mountpoints to assign to them. for instance, let's say you split the hard drive with XP into four partitions.
```

partition......mount point..........description
/dev/hda1...../media/hda1.........windows
/dev/hda2...../home.............home
/dev/hda3...../....................filesystem
/dev/hda5.........................swap
```

---

### Post by seshomaru samma on 2007-03-21
for making a /home partition read [this ]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Cornbreadly on 2007-03-25
I dont really want to do a fresh install without out backing up all that i have now.  I think I just  need some help planning out my partition layout for the two hard drives along with securing that home partition.

Also, currently my box is a dual boot and i go through grub at start-up.  Upon reinstall, will whichever partition that handles that be re-written?  I ran into problems a few months ago when I reinstalled XP after ubuntu.  I couldnt boot into anything other than XP.

 After this planned reinstall, I just want to go straight into ubuntu.

> if you do a fresh install from a livecd, you can use Gparted to set up the partitions you need, then it will ask you which mountpoints to assign to them. for instance, let's say you split the hard drive with XP into four partitions.
Code:

partition......mount point..........description
/dev/hda1...../media/hda1.........windows
/dev/hda2...../home.............home
/dev/hda3...../....................filesystem
/dev/hda5.........................swap

Can I do that now with gparted?  What about UUE?  Could I just back-up everything and then install UUE through synaptic like I did when i upgraded to 6.10?

And as far as my second HD, just make it all ext3, right?

---

