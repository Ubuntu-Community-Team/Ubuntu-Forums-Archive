---
title: "[SOLVED] partitioning frustration"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by mr tim esquire on 2008-02-06
I have a 500gb SATA HD and i want to partition it as follows
[LIST]
[*]1gb swap
[*]9 gb root (ext3)
[*]40gb Windows (NTFS)
[*]400gb shared media partition (fat?)
[/LIST]

When i try to create the last partition with the ubuntu setup CD it leaves lots of unpartitioned space and says something about having too many partitions

I leave the 400gb unpartitioned and try to format it in windows but it will only let me format as NTFS, which i know ubuntu dosn't like!

What is the best way of achieving what im trying here!

Thanks for the support!!

---

### Post by mysticrider92 on 2008-02-06
Ubuntu 7.10 has almost no problem reading NTFS partitions. The problem is Windows drivers, which are not very good. 

That aside, you probably just need to put one or two partitions in logical space. Have you already installed Windows and Ubuntu? If not, I would partiton it with the 40gb Win partition first, then the 9gb Ubuntu partition. Now create a logical (extended) partition, and use up the rest of the space (probably some 360-370+ gb). Make all but 1gb of this FAT32, and the rest swap. 

That should solve the too many partitions problem. If you have already installed the os, you should be able to make the current free space into an extended partition and fill that with one FAT32 partiton.

---

### Post by mr tim esquire on 2008-02-07
OK ive started from scratch, first installing Ubuntu I made an 20gb EXT3 partition for Ubuntu (thought it mike like a bigger slice)  and left everything else unpartitioned, NO SWAP SO FAR. 

I then installed windows on a 50gb NTFS partition i made with that installer.  Grub got wiped and  boots straight to XP now.

I use supergrub CD to boot into linux and have a look at grub:-

```

grub> find /boot/grub/stage1

Error 15: File not found
```

Can i edit /boot/grub/menu.lst  i think windows is in partition (hd0,1) but not confident enough to edit file without some advice

Thanks again!

---

### Post by dstew on 2008-02-07
If you are running grub from the mounted Ubuntu hard disk installation, it will not be able to find anything, because it has to be able to mount the filesystem to do that, and if the filesystem is in use, it won't be able to mount it. If you want to look at the /boot/grub directory, just navigate to it using the file manager.

What you really need to do, if indeed you have Ubuntu installed, is to re-install the grub boot loader. When you installed Windows, it wiped out the grub loader. You should be able to re-install grub using the supergrub disk. You do not need at this point to edit the menu.lst file.

---

### Post by mr tim esquire on 2008-02-07
I reloaded grub using supergrub CD and added windows to /boot/grub/meun.lst

```

title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1
```

so far so good! Now i have 2 partitions; ubuntu and windows, and a whole lot of unpartitioned space.
I want to use the remaining space as a shared ubuntu / windows drive.  What is the best way to go about formatting this?

Windows disk managment tool will only let me format it as NTFS and my version of ubuntu has problems reading that.

I had a look at fdisk in ubuntu but got this message

```
tim@tim-machine:~$ fdisk /dev/hda
You will not be able to write the partition table.
Note: sector size is 2048 (not 512)
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel

```

---

### Post by dstew on 2008-02-07
If you can boot Ubuntu, you can look at the partitions using **gparted**. I think it is already installed in Gutsy, but if not, use synaptic to install it. I wouldn't use fdisk to do the partitioning.

---

### Post by mr tim esquire on 2008-02-07
Thanks that worked a treat gparted is great little tool!

---

### Post by jan quark on 2008-02-07
if everything is alright please mark this thread as solved
thank you

---

### Post by bodhi.zazen on 2008-02-07
+1

Like this : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

