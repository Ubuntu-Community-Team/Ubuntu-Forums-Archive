---
title: "Resize partitions After installing Ubuntu"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-30
Hi everyone, 
Right now I have 4 partitions on my HD, 

10gb for Windows, 8gb FAT32 for Shared Windows/Linux, 18gb ext3 for Linux, and 1.5gb partition for Swap.

Can I safley use a GParted LiveCD and make the FAT32 smaller and ext3 Ubuntu bigger?

Thanks! :p

---

### Post by nikku_neko on 2006-07-30
i've never tried such, though i'd assume it would be safe to try as long as data on the respective drives was safely backed up and the fat32 portion had been defragmented as well as possible (to ensure the data was all grouped in one safe place at the beginning of the partition)... that's what i'd think, anyway.

hmm.  well, good luck, either way.



nick

---

### Post by ajgreeny on 2006-07-30
You certainly can though you should back up everything first just in case.

---

### Post by GStubbs43 on 2006-07-30
Well, acording to jdong's pyfragtools Defragmenter, > /media/Shared/ is not fragmented. Go home.

And Everything is backed up, so off I am! I'll letchya know how it goes!

---

### Post by GStubbs43 on 2006-07-30
Okay, that didn't work... I'm back to this:
```
|    10g NTFS Windows XP   |8gb FAT32|       18gb ext3 Linux       |Swap|
```

I mmanaged to get the FAT32 doen to 3gb, but since the ext3 is after, I couldn't move it to the unalocated space. hmm.... is there still a way to do it? Should I do it in a different order?

---

### Post by ajgreeny on 2006-07-30
I think the problem is that you can't move the start of any partition back in the disk, you can only enlarge a partition by moving the end away from the start, if you see what I mean.  I think you wil have to make a disk image with partimage and then copy that to a newly made partition taking the whole size you want.

If anyone else knows a different way perhaps they will enter this discussion.

---

### Post by jdong on 2006-08-18
> **GStubbs43 said:**
> Well, acording to jdong's pyfragtools Defragmenter, 

And Everything is backed up, so off I am! I'll letchya know how it goes!


Note that my defrag script only defrags files (data), it does not consolidate free space for safety reasons.

However, the resize utilities are all capable of recognizing the situation, and some of them are even capable of moving data aside safely.

---

### Post by gn2 on 2006-08-18
I know it's a paid for Windows application, but if you know someone who has a copy..... Norton Partition Magic 8.0 will allow you to increase the size of a partition in the middle of the drive using space in a drive nearer to the start of the drive.

---

### Post by alan yeates on 2006-08-18
I used partition magic, it can not only resize but merge as well, including formatting. I found a free version on a mag disk, but maybe it exists on a 30 day trial somewhere. Not knocking any Linux app, it's just that I have done this stuff with no prob several times with PM.

---

### Post by jrjr on 2006-08-18
.

---

### Post by stoer on 2006-08-22
> **jrjr said:**
> BUT, can PM do this with an ext3 format? I read somewhere that gparted is working on the data movememt part so maybe it won't be too long and that will have the ability too....

Not sure about pm 8, Acronis doesn't like adjusting the ext3 partition though, gives several warnings and advises that you'll need your linux  boot disk to make "adjustments" after the partition has been changed.

I'm in the same situation as yourself,
eg.
win partition - unallocated space (400mb) - ext3 partition - swap file -win data partition-fat32 partition

sure could use that extra 400mb in my linux partition, my windows partition sure doesn't need it! :)

PM 8 just doesn't like my partitions, complains about how the linux is set up!  gives errors on start and end points being unclear.

---

### Post by kircher on 2006-08-22
I just did a similar job myself about 10 minutes ago. My ext3 partition was getting full, and I wanted to make it bigger. I first used a linux boot cd with a tool called qtparted and realised that it didn't adjust ext3 (only ext2), so I deleted my fat32 partition anyway, which was at the end of my drive. I then moved my swap up to the very end of the drive (it was originally in between my ext3 and fat32 partitions), and then booted into ubuntu using the live cd. I then opened gparted with 'sudo gparted' in a terminal, and resized the ext3 partition to use up the rest of the drive (up to the swap) I had cleared with the other tool (this could have all been done in the ubuntu live cd I later realised). I still have a 3GB Windows XP partition at the begginning. Since you backed everything up in the first place, there's no real harm in just deleting the fat32 partition, resizing the ext3 and then creating a new fat32 one. It may be easier than searching around for a tool that can move the beginning of a partition.

---

### Post by Indra on 2006-08-22
Hi,

I would like to change the size of my partitions as well without needing to copy everything to a CD, delete partitions, create partitions, copy back the data etc. I used PartitionMagic on Windows for this, but I believe GParted can not change ths size of an existing Ext3 partition if this means moving the start sector of the partition.

I was a fool when installing Ubuntu since at that time I chose the desktop layout (should have chosen server or just fill in the details myself).

So now I have two partitions, one 6 Gb for the OS, and one 105 Gb for /home.

Since I am the only user on this machine, I'd say this is a little inconvenient. My OS partition has now 940 Mb empty space, but i'd rather have this a lot more, to be able to install new software normally.

I would be very happy to be able to for instance: shrink a partition, then move it more to the end of the disk, then enlarge the other partition using the then available free space next to it.

Even better: just enter the new sizes of all partitions and let the program figure it out. All assuming enough free space is available of course.

Any news on gparted supporting this in the near future?

---

### Post by kircher on 2006-08-22
> I would like to change the size of my partitions as well without needing to copy everything to a CD, delete partitions, create partitions, copy back the data etc. I used PartitionMagic on Windows for this, but I believe GParted can not change ths size of an existing Ext3 partition if this means moving the start sector of the partition.

I was a fool when installing Ubuntu since at that time I chose the desktop layout (should have chosen server or just fill in the details myself).

So now I have two partitions, one 6 Gb for the OS, and one 105 Gb for /home.

Since I am the only user on this machine, I'd say this is a little inconvenient. My OS partition has now 940 Mb empty space, but i'd rather have this a lot more, to be able to install new software normally.

I would be very happy to be able to for instance: shrink a partition, then move it more to the end of the disk, then enlarge the other partition using the then available free space next to it.

Even better: just enter the new sizes of all partitions and let the program figure it out. All assuming enough free space is available of course.

Any news on gparted supporting this in the near future?
Reply With Quote

I'm pretty sure the qtparted tool I used allowed me to move partitions around, but it didn't support ext3 (it must be an old tool). In fact I just opened gparted and it does have a move function, but you can't adjust a partition that is mounted, so I would try (I can't guarantee success) booting to ubuntu using the live cd (so your hard drives aren't mounted) and then going to a terminal and running the command 'sudo gparted', (without the apostrophes of course) and see how that goes. I would recommend backing up anything that is very important though before doing this. It's unlikely anything would screw up, but it could happen (I didn't backup actually, but I tend to take risks)

---

### Post by matteospqr on 2007-06-03
Hi!

I am trying to do the same! I have an NTFS partition, then 5gb of free space, then the linux ext3 ubuntu partition etc...

How can I merge the 5gb of free space with the ext3 ubuntu partition?? Gparted doesnt seem to let me do that!

THanks!

---

### Post by yuku-aki on 2007-10-24
I'm going to try a similar situation... but I have an idea.

So, here I am with 3 partitions: 

sda4 (30GB, The one I want to keep.)

sda1 (30GB, and does not boot into Gnome for some odd reason.. it says that X is failing or something, so I just gave up on it and grabbed a copy of my /home when I made a new partition), and

sda3 (15GB, I don't want this one anymore either, because I have Beryl and Compiz now, and have copied over all the data I need.)

That is the order the partitions are in on the drive.  GRUB boots to sda4 first, then has the choice of 1 or 3.  This leads me to believe that I can at least delete the other two partitions and still be able to boot into sda4.

I can't remember how I ended up that way, but it had something to do with me copying the hard drive I wanted to the front, and then deleting the original copy at the end.  So I will attempt this idea again, with documentation this time so I (and you) know how it was done.

My hypothesis:  I should be able to successfully delete sda1 and sda3, then copy sda4 into the freed space in the front of the drive, then delete the original and expand the size of sda4 all the way to the end.

Anyone know of any possible complications with my fstab and GRUB files in general if I do this?  Or any precautions to prevent them?

I'll wait a day or so to try it, after I look into it a bit more. I don't have anything to back up to, besides some DVD-R's I can put my important stuff on, so hopefully this time I don't have as many complications as last. 

I had no access to my data for a few days the last time I tried, trying to repartition and reinstall to get to my old /home files.  But nothing was lost, except for some software I never used, so maybe it was a blessing in disguise.  :)

---

