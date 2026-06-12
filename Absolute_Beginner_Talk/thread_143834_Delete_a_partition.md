---
title: "Delete a partition"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Tortanick on 2006-03-13
I have one Hard Drive on my computer, on it I have a three primary partitons and a swap partition. I want to delete one of the priamry partitons and give the space to the other two primary partitions (in non-equil amounts) How do I do this?

---

### Post by frodon on 2006-03-13
I think gparted(gnome) or qparted(kde) allow you to do that.

---

### Post by 4dz0 on 2006-03-13
Install gparted from the repositories, this should help.

---

### Post by GeirG on 2006-03-13
Try fdisk.

fdisk /dev/hda

... then you can list, create, delete partitions.

I'm sure there are many potential pitfalls, so be sure to check up on the man pages (man fdisk) first, and be sure of what you are trying to do :-)

---

### Post by Tortanick on 2006-03-13
I allready tried Gparted and I was able to delete the partition but I couldn't get it to add the space to the other partitions, when I tried to unmount them It said they were in use.

I'll look up Fdisk, Thanks for the quick replies

---

### Post by chuckyp on 2006-03-13
Try booting off of a live cd and using gparted.

---

### Post by Tortanick on 2006-03-13
Sounds easier than learning fdisk :)

---

### Post by AtinLango on 2006-03-13
You want to re-distribute disk space.

As far as I know, GParted or QTParted will not do that. They are really limited to reducing partition size, and thereafter allowing you to increase up to the limit of the original partition size, provided they are not already detatched. They cannot cross the boundary between partitions.

In my own words, GParted and QTParted can only reduce a partition size (re-sizing is not even a good term to use). They are very effective in this. However, if you want to redistribute space, use Paragon Partition Manager or some other commercial partition manager.

EDIT:
I bet even fdisk won't re-distribute space.

---

### Post by plors on 2006-03-13
[QUOTE=AtinLango]
In my own words, GParted and QTParted can only reduce a partition size (re-sizing is not even a good term to use). They are very effective in this. However, if you want to redistribute space, use Paragon Partition Manager or some other commercial partition manager.[/QUOTE]

huh? gparted and qtparted can move/shrink/grow filesystems very well. some options may not be available due to filesystemlimitations (e.g. moving the start of an ntfs filesystem), but afaics the TS can do what he want with any OSS partitionmanager.

see also [http://gparted.sourceforge.net/features.php]("http://gparted.sourceforge.net/features.php")

---

### Post by AtinLango on 2006-03-13
[QUOTE=plors]huh? gparted and qtparted can move/shrink/grow filesystems very well. [/QUOTE]

I have tried several times with various file systems. Granted it can grow, but not beyond the point from which you initially reduced it. In essence, it cannot grow into any other partition! Can only grow within its original partition. Which is why I say effectively, it cannot increase partition sizes.

---

### Post by psusi on 2006-03-13
[QUOTE=AtinLango]I have tried several times with various file systems. Granted it can grow, but not beyond the point from which you initially reduced it. In essence, it cannot grow into any other partition! Can only grow within its original partition. Which is why I say effectively, it cannot increase partition sizes.[/QUOTE]

What are you talking about?  As long as there is free space on the disk beyond the end of the partition, it can grow it.  

As for the OP, you need to run gparted from the livecd and you might have to get a bit tricky depending on your current configuration.  For instance, if the partition you are trying to get rid of is in the middle of the disk, then you can delete it and expand the partition before it into some of the new space.  To extend the partition at the end of the disk though, you might have to first move it down, and then extend it.  Depending on the filesystem on the partition, this may not be possible.  

This kind of dynamic repartitioning goes much more smoothly and can be done without a livecd if you originally format the drive to use LVM.

---

### Post by plors on 2006-03-13
i guess he's talking about merging 2 partitions into one?

Anyway. for someone who doesn't know exactly what he's talking about he shouldn't make such bold statements. Those can be very confusing to users.

---

### Post by AtinLango on 2006-03-13
[QUOTE=plors]i guess he's talking about merging 2 partitions into one?

Anyway. for someone who doesn't know exactly what he's talking about he shouldn't make such bold statements. Those can be very confusing to users.[/QUOTE]

Apologies for the bold statements. It is possible that it worked for you and failed to work for me, or it is possible there is a misreading of  my statement.

Forget about it. I think the most important thing is lets make it work for Tortanick.

---

