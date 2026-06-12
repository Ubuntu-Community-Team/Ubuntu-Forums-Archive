---
title: "Dual-boot root partition resizing"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by chmmr on 2006-05-29
About a month ago I was running Win2k on a 120GB hard drive.  On a whim, I installed Dapper onto a small 15GB partition at the end of the >100GB NTFS partition where Win2k resides.

Time passes.  I decide I like Ubuntu enough to use it as my primary OS.  I no longer need a gigantic NTFS partition, so I resize that down easily enough, to 40GB.  My hard drive now looks like this:

[IMG]http://img264.imageshack.us/img264/8245/screenshot9dd.png[/IMG]

Obviously I'd like to reclaim that big swath of unallocated space in the middle of the drive now.  But searching around, I find that ext2 partitions can only be expanded "forward" (directionally right, in the gparted display) and not "backward".  So I can't simply expand my root partition into the grey space, right?

I'm wondering what the best course of action here is.  I've heard a few in various threads on the subject of repartitioning:

1) Make a new partition in the blank space for /home, and move my existing home dir (currently on root) to that.

This leaves me with a root partition that's a bit too large (~15GB) for just root, and I'd like to waste as little space as possible.  I'm also unclear on all the steps necessary to redirect my current /home to a new partition.

2) Make a copy of my root partition, at the beginning of the unallocated space, then remove the old one and expand the new one to fill all the unused space.

This seems to require more steps, but that's fine.  I'm not sure what all is involved in doing this though... something about reinstalling GRUB?

3) Reformat the drive entirely, and repartition in a more ideal way.

I'm loathe to do this, because it would take a while to get two OSes set back up and I'm busy with other things.  If this is far and away the best option, though, I'm open to it.

4) Something else?  Based on the diagram illustrating my current setup, is there some special magic way to resize my existing root, or is this a basic limitation of partitioning / file systems etc?

I think what I'm looking for here is advice from someone who's done this sort of thing before, and ideally some tutorials on the exact steps necessary to do these tasks.  But not "by rote"... I like to actually understand things rather than copy-paste commands into a terminal.

Thanks for the help in advance.  I'm still kind of a newb about some of this, and I'd rather get the advice of a pro than screw something like this up.

---

### Post by Kilz on 2006-05-29
[QUOTE=chmmr]About a month ago I was running Win2k on a 120GB hard drive.  On a whim, I installed Dapper onto a small 15GB partition at the end of the >100GB NTFS partition where Win2k resides.

Time passes.  I decide I like Ubuntu enough to use it as my primary OS.  I no longer need a gigantic NTFS partition, so I resize that down easily enough, to 40GB.  My hard drive now looks like this:

[IMG]http://img264.imageshack.us/img264/8245/screenshot9dd.png[/IMG]

Obviously I'd like to reclaim that big swath of unallocated space in the middle of the drive now.  But searching around, I find that ext2 partitions can only be expanded "forward" (directionally right, in the gparted display) and not "backward".  So I can't simply expand my root partition into the grey space, right?

I'm wondering what the best course of action here is.  I've heard a few in various threads on the subject of repartitioning:

1) Make a new partition in the blank space for /home, and move my existing home dir (currently on root) to that.

This leaves me with a root partition that's a bit too large (~15GB) for just root, and I'd like to waste as little space as possible.  I'm also unclear on all the steps necessary to redirect my current /home to a new partition.

2) Make a copy of my root partition, at the beginning of the unallocated space, then remove the old one and expand the new one to fill all the unused space.

This seems to require more steps, but that's fine.  I'm not sure what all is involved in doing this though... something about reinstalling GRUB?

3) Reformat the drive entirely, and repartition in a more ideal way.

I'm loathe to do this, because it would take a while to get two OSes set back up and I'm busy with other things.  If this is far and away the best option, though, I'm open to it.

4) Something else?  Based on the diagram illustrating my current setup, is there some special magic way to resize my existing root, or is this a basic limitation of partitioning / file systems etc?

Thanks for the help in advance.  I'm still kind of a newb about some of this, and I'd rather get the advice of a pro than screw something like this up.[/QUOTE]

I have never had luck resizing, but you can try to copy the Ubuntu partition into the free space , then expand it. Then delete the partition you copied. Id do it one step at a time. But make sure to back up anything you need as there is a chance something could go wrong and you would have to reinstall.

---

### Post by aysiu on 2006-05-29
I think you're on the right track.

I don't think 15 GB is too big on a drive that's 120 GB, but since you do...

What I would do is format the huge partition as Ext3 and use PartImage to copy the 15 GB partition to some external hard drive (or even temporarily to the huge partition).

Then delete the 15 GB partition and make a new, smaller one in its place (maybe 9 GB). So you'd still have Windows, a huge partition, and then a root partition and swap.

Then, use PartImage to restore the partition back to the new 9 GB partition and then move the /home folder to the huge partition in the middle.

Instructions for using PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

Instructions for moving /home to its own partition:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

P.S. PartImage copies the *used* space on a partition, not the entire partition. So if you have a 15 GB partition but only 6 GB of it is used, the partition image will be only 6 GB.

---

### Post by chmmr on 2006-06-01
So, I ended up creating a new ext3 partition in the empty space, and followed the tutorial for moving my /home to that.  Works great.

The one thing that threw me for a loop was, after I'd copied over all of my settings to the new /home, I still had to redo some of my customization settings - mostly Gnome stuff, like panel layouts and themes.  Is there any way to preserve this?  I thought it would have been stored in /home rather than /usr or whatever.

---

### Post by aysiu on 2006-06-01
No, that stuff lives in /home

I'm not sure why the transfer didn't work fully. I actually tried it out, and I didn't have to redo any settings. That's weird.

---

### Post by chmmr on 2006-06-01
How exactly did you copy/move the content of your old /home to your new one?

---

### Post by aysiu on 2006-06-02
[QUOTE=chmmr]How exactly did you copy/move the content of your old /home to your new one?[/QUOTE] I used that tutorial (I won't unleash a tutorial on the world until I've tested it out myself).

---

### Post by NJD on 2006-06-14
The first guide says that when you reinstate the backup, it should be on a partition that is equal to the one you installed from. Is this the case? I have a very messed up partition regime going on and I desperately want to do what you are doing. Basically I had a windows partition that I accidentally converted to ext3 and now I have partitions everywhere and I feel my system is not in that respect optimised.

---

### Post by aysiu on 2006-06-14
NJD, can you post the output of ```
sudo fdisk -l
``` so we can see what you mean by "messed up partition regime"?

---

### Post by NJD on 2006-06-14
Yep sure, i'm at work right now but when i get back to my pad i'll post it right over.

---

### Post by NJD on 2006-06-14
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         851     6835626    f  W95 Ext'd (LBA)
/dev/hda2   *        1892        4865    23888623+   c  W95 FAT32 (LBA)
/dev/hda3             852        1891     8353800   83  Linux
/dev/hda5               2         802     6434032+   b  W95 FAT32
/dev/hda6             803         851      393561   82  Linux swap / Solaris

Partition table entries are not in disk order

see what i mean? and this from a PC that now only has Ubuntu on it! and when i try to mount the 22.8 gig drive and the fat 32 drive it tells me 'unable to mount selected volume'

---

### Post by aysiu on 2006-06-14
So Ubuntu is on /dev/hda3.
Swap is on /dev/hda6

So what's on /dev/hda1 and /dev/hda5? Are those just data partitions?

---

### Post by NJD on 2006-06-14
HDA1 is the extended partition and HDA 5 is fat 32, here's a gparted screenshot:

[IMG]http://i20.photobucket.com/albums/b222/humbuck/Screenshot.png[/IMG]

what i'd like in a perfect world is just one unified partition. no mess, no hasstle, oh and to get winows off of my boot options

Basically, this was once a secondary hard drive with a fat32 and an ntfs partition. then my master hard drive died on me, and i installed windows back onto this, onto the bigger fat32 partition. on doing so i lost all faith in microsoft and decided to install Ubuntu, after doing that in an attempt to make the rest of my drive accessable i made the rest of my big fat32 partition a ext3 one and wiped my windows installation.

---

