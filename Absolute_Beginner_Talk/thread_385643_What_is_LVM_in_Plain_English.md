---
title: "What is LVM in Plain English?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-15
I'm installing Xubuntu using the alternate CD, I have an empty hard drive, and I'm confronted with these options:

Erase entire disk: IDE1 master (hda)
Erase entire disk and use LVM: IDE1 master (hda)

Not knowing what LVM is, I Googled it and got a bunch of technical explanations for hardware geeks.  I think LVM might be a sort of magical dynamic partitioning system, where if I need more space for my swap partition or any other partition, LVM will make that happen automatically, and if I add a second hard drive, LVM will be able to make one "partition" reside on two hard drives.  It basically adjusts my partitions according to the space needed and available. I doubt I've got that right, though.  Anyone care to enlighten me?

---

### Post by bodhi.zazen on 2007-03-15
LVM = Logical Volume Management.

The easiest way of explaining it may be like this ...

Imagine your hard drive. Now say you want to partition it ... You can go the traditional way, or usre LVM.

LVM makes the entire HD a pool. You then create logical partitions "on the fly" from the pool. Say you create a logical partition 10 Gb in size. Later you need more space. Assuming you have space in the pool you can add to you partition making it say 15 Gb. No need to boot gparted, you can add on the fly.

LVM may span physical HD. Say you have a 20 Gb HD and a second 20 Gb hd ... You can make a 40 Gb pool and then make a 30 Gb logical partition from the pool.

Cleas as mud ? no ?

See if this link helps : [http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

---

### Post by kelbizzle on 2007-03-15
> **bodhi.zazen said:**
> LVM = Logical Volume Management.


LVM may span physical HD. Say you have a 20 Gb HD and a second 20 Gb hd ... You can make a 40 Gb pool and then make a 30 Gb logical partition from the pool.

Cleas as mud ? no ?

See if this link helps : [http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

just what he said. check out the picture. 
[IMG]http://www.linuxdevcenter.com/linux/2006/04/27/graphics/lvm.gif[/IMG]

---

### Post by pdxuser on 2007-03-15
Well, this sounds so good, I'm just wondering why anybody wouldn't use LVM?

---

### Post by kelbizzle on 2007-03-15
Say you did go out and buy another hard drive because you wanted to check it out. If you look you see how because of the logical volumes the home folder is kinda on both of the drives. Well if one of the drive were to fail (god forbid) you'd loose the data.

---

### Post by kelbizzle on 2007-03-15
using it in a raid 1 configuration would basically be an entire copy of what is on the logical volume. so if you have 3 hard drives. 2 of them setup to be a logical volume and the third to be an entire copy of that volume.  you could survive a hd failure.

---

### Post by seshomaru samma on 2007-03-16
I would go for the first option

---

### Post by dunomous on 2007-03-21
**Another Article:**

[Here](http://blog.supportpro.com/2007/03/lvm-an-introduction/)

   Which of you are/plan on using LVM right now? I would like to hear some feedback on comparing it to the current LVM that most users have now. 

   If positive, I plan on giving LVM a try when the Feisty discs are ready for distribution (no pun intended).

---

### Post by Twist on 2007-03-22
Well, LVM is sorta like JBOD on a drivecontroller. Only real difference is that you can dynamically add space to any partition without using expensive software. 
Like people said, It's kinda bad because if a SINGLE drive fails, you loose everything. BUT, it's REALLY cool if you set it up mirrored over many disks. 
Assume you have say 2x400GB disks, and you want to use these for data. If you want the data to be safe, you need to mirror the disks, and this means you loose one (or have to buy another 2 disks). 
Now your only other options are to either get another 400GB drive and run RAID5 (slow). OR when using Linux and LVM, you can grab 3 of your old 250GB disks, and put them in a second LVM that mirrors the first. Because the 3 disks are older, they're probably slower, but because you have 3 of them vs. two of the others, it's likely that the data will be distributed more evenly among the disks, thus if you're lucky, allowing you a good throughput, same as on your newer 400GB disks. While there's probably a lot of good software to allow for a great distribution, I haven't tried any yet, because my installation is so small as not to need it. But I'm sure someone will give a link or information about a project looking at this.
ADDITIONALLY, you get the EXTREMELY cool option of being able to mix ATA, SATA, SCSI, FLASH & USB disks etc (presumably even an optical or other backup drive, but I haven't tried that yet either) in the SAME "mirror". 

While my installation is a LOT smaller than this, I do still use LVM, but that's for entirely different reasons. I'm running my server on a couple of Compact Flash drives (this cuts down on noise and power consumption, which is ideal for a small, private webserver that's located in my hobbyroom). Putting the two CF drives in LVM means that data gets pulled from the CF drives more or less at random rahter than having a single CF drive take majority of the strain (that still happens, but less often). This is very usefull because the CF drives are rather old and thus individually they're very slow (about 20x, or roughly 3Mb/s each). Thus with LVM I can reach an average throughput that somewhat higher than 3MB/s. 
And I usually find that using LVM on your root volume is a VERY good thing, because you (or at least I) frequently run out of space (probably because I suck at doing my regular administratioon and maintenance) and have to move some things around and create new mountpoints. Using LVM I can easily reclaim and reuse space from one abandoned mount in a very used one. A lot easier than without LVM at least.
And finally, I find that the LVM is a lot easier to use because I run in terminal mode only. While I've once seen KDE, and once read about Gnome, I've never used them. And I suspect that LVM will be hard to describe graphically, I may be wrong about that though.

That being said, I DO NOT use LVM on my backup/file drives, because they're just two single drives that only need to mirror eachother, and both disks are the same size, and I have all the space allocated at once to a single mountpoint which I do not plan on extending anytime in the near future.

In other words, LVM is really cool for the root volume, for stuff that changes a lot, and especially for stuff that continually needs more and more space (databases, backups, mailservers, networkdrives etc.), but rather useless for (semi) static information (archives, binaries, copies of installation CDs, etc.)

So yes, I use LVM right now, but I have no plans of changing my non-LVM drives to LVM anytime soon because, they're not LVM for a very good reason.

---

### Post by sicofante on 2007-03-31
> **Twist said:**
> Like people said, It's kinda bad because if a SINGLE drive fails, you loose everything.
Well, I've spent the last couple of hours googling for this and it's not that clear. Actually, many people seem to have partially recovered data from a single disk failure in an LVM (data residing in the surviving disks). If the Volume Group is built concatenating Physical Volumes (disks), instead of striping, it seems you won't loose but the data residing in the dead disk.

I'm amazed that this issue is not clearly explained in the LVM documentation I've come across during my research. Maybe my research has not been that good, but my impression so far is that answering the question "What if one drive in my LVM fails?" is amazingly hard.

If you could point to some docs that clarify this issue, I'd be really grateful.

---

