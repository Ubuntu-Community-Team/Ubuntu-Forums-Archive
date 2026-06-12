---
title: "Partitioning Hard disk for Noobs"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-09
Hey All!

I am 1 week into Ubuntu and liking it alot!

Now I want to partition my hard disk...

At the moment my windows disk is

Primary partition
C:

Extended partition
D:
E:
F:
   
  To do this I used Partition Magic 8, very easy took about 15 minutes to create these partition.
   
  I am hoping Ubuntu, won’t fail me now…. Has a similar Noob Partitioning Program, where I can point and click and create my partition!!!
   
  Primary partition
HDD1:

Extended partition
HDD2:
HDD3:
HDD4:
   
  Thanks for the Read.
   
  Nooby

---

### Post by xyz on 2007-03-09
Hi and Welcome!
[Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning")
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Kateikyoushi on 2007-03-09
Gparted on the ubuntu live disc is very similar to PQ Magic, and works with ubuntu while the former can cause problems.
If you plan to dualboot I recommend to read this user friendly dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by robinlennox on 2007-03-09
I have wiped windows of my box... so I am solely using Ubuntu (Scary!), No Dual Boot for me..... :(. Gparted is worth a look cheers

---

### Post by Kateikyoushi on 2007-03-09
Are you sure about it ? Post the output of the following command to see what happened to your partitions.

```
fdisk -l
```

---

### Post by robinlennox on 2007-03-09
It's OK, I meant to do it! It wasn't an Accident!

However there is an issue with Gparted... how on earth do i edit my hda1 partition?

My Current Partitions are 

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot         Start         End        Blocks          Id   System
/dev/hda1   *           1         11784     94654948+   83   Linux
/dev/hda2           11785       12161     3028252+    5     Extended
/dev/hda5           11785       12161     3028221       82  Linux swap / Solaris

I want to have
/dev/hda1 20gb
/dev/hda2 67gb
/dev/hda5 3gb

Any ideas how to do this in Gparted

Also which file system should I use, if I want to use the partition for Windows/Linux and Web users?

---

### Post by dstew on 2007-03-09
Currently hda2 is an extended partition, taken up entirely by hda5. You propose a scheme that looks like creating a 67gb extended partition, but only using 3gb of it. Is that really what you want to do? You will end up with 64gb of unused space.

Don't you really want to have three primary partitions, hda1, hda2 and hda3? Then, you can always make an extended partition out of hda4 later if you want.

Why are you having trouble editing your hda1 partition? Is it locked? If so, that means you are using it. To edit a partition, you have to be running out of a different partition. Boot the live CD and partition your hd from there.

---

### Post by robinlennox on 2007-03-09
I am wanting a drive to store about 10gb of personal folders for my family and about 10gb of music and videos also possible expansion on both folders

Would it be best to do that on one drive or two?

---

### Post by dstew on 2007-03-09
Your drive is plenty big enough. You can do

hda1 20gb for linux
hda2 20gb for personal folders
hda3 20gb for music
hda4 40gb for other stuff

You could also do

hda1 20gb
hda2 ext 80gb
hda5 20gb
hda6 20gb
hda7 40gb

---

### Post by robinlennox on 2007-03-09
I can't mount my partition after I used gparted

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start    End      Blocks         Id   System
/dev/hda1   *   1         2611     20972826   83  Linux
/dev/hda2        2612    12161   76710375   5    Extended
/dev/hda5        7834    11784   31736376   7    HPFS/NTFS
/dev/hda6        11785  12161   3028221     82   Linux swap / Solaris
/dev/hda7        2612    833      41945652    83  Linux

I have tried going to places, Computer then right clicking on Mount Volume - 

I get this error message: mount: only root can mount /dev/hda5 on none

---

### Post by dstew on 2007-03-09
Mount Volume is a front-end graphics interface for the mount command. You need to do a couple of things to mount your hda5 partition. You need to get root privleges by sudo, and you need to tell the mount command what mount point to put the partition on.

First make a mount point. Make a folder in your home directory, like NTFS_Disk. I have Xubuntu, and I don't know how to get sudo from Mount Volume, but to mount the volume to the mount point ~/NTFS_Disk, enter this in the terminal:

sudo mount -t ntfs /dev/hda5 ~/NTFS_Disk -o rw,uid="your_user_name",gid="your_user_name"

Now, even if you get the partition mounted you may not be able to read it because you need extra software to read and write NTFS files. See [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Lastly, if you want to have this partition mounted automatically at boot time, you need to add an entry to your etc/fstab file (file system table). The entry is similar to the argument of the mount command:

/dev/hda5 ~/NTFS_Disk ntfs rw,auto,uid="your_user_name",gid="your_user_name" 0 0

---

### Post by robinlennox on 2007-03-09
For my hda7 partition would it be

sudo mount -t ext3 /dev/hda7 ~/EXT3folder -o rw,uid="myusername",gid="myusername"

or could I use

sudo mount -t ext3 /dev/hda7 /media/files -o rw,uid="myusername",gid="myusername"

---

### Post by dstew on 2007-03-09
I think either one would work, as long as the mount point directories are there before you issue the mount command. It is possible that you don't need the quotemarks around your username, but I am not sure. Try it.

---

