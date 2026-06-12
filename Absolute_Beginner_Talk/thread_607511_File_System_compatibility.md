---
title: "File System compatibility?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by alnilamski on 2007-11-09
This question is likely really obvious, but it is so general that I am having a really hard time finding an answer (though I'm sure it's out there somewhere...)

I don't know incredibly much about file systems (NTFS, FAT32, etc.), but I know what they are.

I plan to install Kubuntu on a dual-boot on my windows machine. I am going to use GParted (unless you suggest something else?) to create a ~20gb partition on my second SATA hard drive. Does all of this sound kosher so far?
Anyway, my main question is this: Does Ubuntu need/prefer any particular kind of file system to install onto?

---

### Post by Nulifier on 2007-11-09
It usually installs on a ext3 partition with a swap space Gutsy (the latest version of Ubuntu) can read NTFS (the kind that windows uses) by default and thus can read from your windows drive.

There are methods of making windows read your EXT3 partitions but you have to install a driver, there are walkthroughs here on the forums.

When you install Ubuntu you should install Windows first and then install Ubuntu which will have an option for resizing your hard disk, select this one and it will resize your hard disk and set up the partitions for you.

You can of course get more complex by adding a /home partition which will help if you need to resinstall but as this is your first foray in Ubuntu you may want to try different setups and see what works for you.

And also as always BACKUP your data before resizing your partiion

---

### Post by hyper_ch on 2007-11-09
easiest way is just to create empty/unpartitions space... in the installer you can then choose "select largest continous empty diskspace" or something similar... make sure you do select that option... otherwise you can do manual partition and als create a home folder. In that case you should make those partitions:

(1) SWAP (about twice the size of your ram but not more than 2 GB) - filesystem type will be SWAP
(2) root (5-10 GB), filesystem EXT3, mounting point "root" or "/" (not sure what is being displayed) and make that one bootable!
(3) home (rest of the diskspace), filesystem EXT3, mounting point "/home"

And as the previous poster said:  BACKUP YOUR DATA (on a regular basis anyway...)

The home partition is the one where normally your user settings and user files will be stored. Most people prefer putting in there the mediafiles like music and videos also... so this should be as large as possible.

---

### Post by alnilamski on 2007-11-09
Thank you, folks!

Wish me luck.

---

### Post by alnilamski on 2007-11-12
So I am about to go through with it, and I just want to make sure of two last, little things!

So when I use the installer to create the partitions, and tell it to use the largest continuous disk space, it will non-destructively create a partition, yes? As in, it will do so without formatting the disk or anything (I know you all say backup my data anyway, but theoretically speaking).

Furthermore, I can install it to a hard drive that is NOT the same system drive as my Windows XP boot, yes? Namely, if Windows XP is on my "C:" drive (hda), but space-wise, my "G:" drive (hdb) would work better for the Linux partitions, that's fine, yes?

---

### Post by hyper_ch on 2007-11-12
well, if you have the option "largest continuous space" it will just use that space... doesn't matter on what harddrive it is... if you have multiple harddrives with unpartitioned space, it'll just use the largest ones of those.

---

