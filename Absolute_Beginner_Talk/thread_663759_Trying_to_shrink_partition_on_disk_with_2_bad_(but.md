---
title: "Trying to shrink partition on disk with 2 bad (but repaired) blocks"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-01-10
I just bought a used Dell D400 laptop which came with XP Professional freshly loaded, and working well. I booted to the Parted Magic livecd and opened gparted with intent to shrink the partition so I could put Gutsy on as dual boot, but gparted said there is "at least 1 be sector" on the disk and so it refused to shrink the partition using the GUI. But it said if I want, then using the same livecd I could open a terminal window and, using cli (command line interface), shrink first the file system using "NTFSresize", and then the partition using fdisk. 

My questions below are with regard to the cli process. (But if anyone knows of any other partition livecd I could use which has a GUI and which will allow me to use it even though there are some bad blockss on the disc, please let me know!) Also note: I did use the Hitachi Diagnostics utility to check the disk in detail and repair the bad blocks (of which there are only two), so that that diagnostics utility now checks out the disk as being fine. But even then, the gparted GUI still says there are "at least 1 bad sector" and refuses to do the partition shrink for me.

So I went through the Parted Magic Doc on cli, but some of the instructions are not clear. In the doc, they teach how to shrink a file system and partition, by way of example-- they show how to decrease a 512 MB USB drive to a 100 MB partition. They say the first command is:

```
ntfsresize --size 100M /dev/sdb1
```

So here, the abbreviation for MB is "M". Well, what is the abbreviation for GB? Is it "G"? If one wanted to go from a 40 GB size partition down to a 15 GB partition, then would the command be:

```
ntfsresize --size 15G /dev/hda
```

Is the above correct? or should the reference to the partition read as "/dev/hda1"?

And then, to resize the partition one opens fdisk according to the directions in the doc. At the place where it requests the Partition number, is the default "1"? If XP is the only OS, I guess it would have to be partition number 1?

Then, what about where it asks for the "first cylinder"? Is that also "1", as given in the example?

I think those are the main places where I needed clarification about the example given in the doc. Thanks.

One other question: Is the procedure any different if there is a bad block on the disc? I ask because gparted had made some reference to using the "bad-sectors option" of ntfsresize.

---

### Post by marufaberlin on 2008-01-11
Try running fsck. What does it turn up with?

---

### Post by swarup on 2008-01-11
As I understand, fsck is a Unix utility used to check and optionally repair one or more Linux file systems. But the hard drive in question is Win XP, with NTFS format. Can fsck be used to check/repair that? If so, how would I access fsck-- through the magic parted livecd?

---

