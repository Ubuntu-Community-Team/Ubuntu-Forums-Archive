---
title: "weird partitioning problem"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by oxboy on 2006-03-15
Hi all!

I tried installing 5.10 on my laptop (Dell Latitude D600).  I have a 40 gig hard drive that says it has 37.2 for NTFS.  I have 20.3 gigs free, and was hoping to make a 10 gig partition for Ubuntu.

I get to the partitioner, and I see 3 things.  I have Primary#1 thats about 30 MB (FAT),  Primary#2 thats 40 gigs (NTFS), and about 8 MB (free), which does not add up to 40 =/.  

I tried just going along with the partition for my 40 gigs, and I tried resizing it to 30 gigs, but it says my partition is too small  (Apparently, I can only resize it to 37.2 gigs, which what my current C: drive is when I'm looking at it from windows).  I'm too afraid to hit the continue button cause I don't think thats supposed to happen!  

Does anyone have any insight?  Thanks so much!

---

### Post by SpectralDesign on 2006-03-15
I'm hardly an expert, but....

re-sizing in-use partitions is a bit risky, so first be sure to backup anything in Windows that's irreplaceable, or otherwise important to you.

Second, it sounds like you've got very little space to work with... if it's a 40GB disk with 37.2 in use by Windows, plus what seems like perhaps some sort of recovery (or hibernation?) partiton @ 30MB then you only have about 2ish GB to work with, not 20....

So, I'd do some things in windows like: run "disk cleanup", empty the Trash, empty your browser cache, launch Add or Remove Programs, sort by size, and find if there are a few big, un-needed programs you xan zap....

Try to clear up at least a few more GB... maybe you have a lot of music you could shuffle off to CDROM?

After you get some free space, run disk defrag, it'll stack the files toward the center of the disk, which should reduce any risk of doing a partition resize.

My 5.10 install takes about 6GB, but I have a lot of development tools installed, you could certainly run a smaller install depending on your needs!

---

### Post by oxboy on 2006-03-16
My NTFS partition is 37.2 gigs, but I actually have 20.3 gigs free inside that partition.  I'm under the impression that I have to resize that partition to get that free space.... right?

Sorry if I misunderstood something... I'm a noob (although.. I did try this on a desktop and it was fine =/)

---

### Post by oxboy on 2006-03-16
I just tried using 3 different ubuntu cds ( just to see if it was the CD that was the problem) but no luck.

Sorry about the confusing numbers, but I'll try to be more clear.   I looked over it again, and heres what I have:

My 40 gig hd seems to have 2 partitions, according to the ubuntu partitioner:

#1  32 MB for a FAT
#2  40 GIG for NTFS
and then 8 MB free.

This does not make sense to me, because when you add those up I get more than 40 gigs =/.

When I look at windows, I see that my C: drive is 37.2 gigs, and that I have 21.3 gigs free.  When I use the windows disk manager, I do see 2 partitions, one that is about the size that the partitioner said (the smaller, 32 MB one) and the other is my C: Drive at 37.2 GIGs (which the ubuntu partitioner is telling me is 40 GIGs)

I think the partitioner is not reading my partitions correctly.   It says that my partition #2 is 40 Gigs when it shouldn't, and that my minimum resize is 37.7 Gigs (when I have 21.3 gigs free!).  I don't know what to do =(

Sorry for the long, double post.   Thanks very much for any help!

---

### Post by SpectralDesign on 2006-03-16
ohhhh okay, I think I get it now :)

Well, remember when dealing with KB, MB, GB, etc, that it's not base 10 it's base 2, so it's a little wonky trying to add up numbers like that...

1GB is 1024MB, which is 1024KB, so 40GB is 41,943,040KB, or something like that... anyway, then I guess my next question is:  did you run disk-defrag? (right-click the drive while in windows, bring up the properties, go to the tools tab (I think) run defrag....)

If so (or when you do) look to see if everything moves to the left, or if you're left with a chunk far to the right....

I honestly don't know the ins and outs of the repartitioning tools, and weather they can move your windows files into the free available space -- I'm pretty sure they can't, and so maybe you're being limited to 37.2 in your resize operation because there's data way out there at the end of the partition....

Let me know about that, and we'll take it from there!

---

### Post by oxboy on 2006-03-16
I ran a disk defrag a couple of times, and I still get the same problem.  Maybe its something to do with the way dell pre-formatted my hd?

Ack sorry about the bottom post.. My comp laggs.  How do i delete it?

---

### Post by oxboy on 2006-03-16
EDIT: Deleted Post

---

### Post by oxboy on 2006-03-17
Does anyone think that it would be a bad idea if I partitioned it anyway?  With 20 gigs of free space maybe it won't overwrite something?

Any comments or suggestions would be much appreciated.

---

