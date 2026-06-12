---
title: "problem with partitioning"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-09-13
Hi everyone. I'm trying to resize my existing partitions, but I have two problems. First, here's what I want to do:

1. resize my /home partition
2. resize my shared partition
3. resize my / partition

So I booted up the Live CD and went to GParted, made these three changes, but I did not see a way to then reuse that extra space that I freed up (I sized these partitions down). I want to add it back to my main Windows partition, but I didn't see how to do so. It wouldn't let me change the maximum size of that partition.

So that's the first issue, but this is the bigger one for now: after making those three changes, I clicked "Apply" and it started to do them. But then I got an error message saying an operation failed because it was trying to work on a mounted partition. Not sure which, though, because I was on the Live CD as far as I know.

The resizing of the shared partition seemed to work though, but the other two didn't, so I assume that the failed operation occurred on one of those two (and then the third one was skipped as well).

So, not sure what to do, I decided to just resize the shared partition back to how it was and come here and ask my question. I did that but again got the same error message (this time it had to be referring to the shared partition, right?). Yet it applied that change anyway and now I'm back to the way I was 10 minutes ago.

So my questions are:

1. How do I reuse the freed space?
2. How do I avoid this operation failure error?

Thanks!
John

---

### Post by sawjew on 2006-09-13
Do you have a swap partition?  If so I think the live cd mounts an existing swap partition to allow it more available memory.  I have found that the Gparted livecd is the best way to repartition a hard drive. 

the Gparted live cd is available here [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Try it with that and see if it works any better.

---

### Post by bodhi.zazen on 2006-09-13
FYI this is "complex" re-partitioning.

The Ubuntu live CD will not do it. The new GParted CD (see link above) claims to be able to do it, but I do not know if it is reliable.

In a nutshell, you can add free space to the Right of a partition easily, but not if it is to the left. Clear as mud ?

Also, if the HD is mounted (swap) you can not re-size the partitions.

---

### Post by JohnJSal on 2006-09-13
Thanks guys. I will try the GParted CD and see how it goes!

---

### Post by JohnJSal on 2006-09-14
Ok, I think this will take care of the second problem, but I still see no way to reclaim the space I'm freeing. Please tell me there's a way!

---

### Post by bodhi.zazen on 2006-09-14
You will have to move rather then resize the partitions.

This is the experimental part.

---

### Post by JohnJSal on 2006-09-14
> **bodhi.zazen said:**
> You will have to move rather then resize the partitions.

This is the experimental part.

How is this done? When I choose "Move/Resize", the only options seem to be adding or subtracting space. Does moving involve putting space before it? I tried this with one partition, but I still could do nothing with the extra space. Does this have anything to do with the fact that the partitions I'm trying to resize are on an extended partition, and the main partition is not?

---

### Post by bodhi.zazen on 2006-09-14
Not sure. Where is yor "extra space"? between partitions or at the end of your partitions?

---

### Post by JohnJSal on 2006-09-14
How can you tell where it is? All I see is that when I size down a partition, it puts the "unused space" right beneath that partition. Does that mean to the right?

But I also tried, when resizing, to put the space "before" the partition, but that still showed the unused space in the same spot, beneath it, so maybe that doesn't mean anything.

---

### Post by bodhi.zazen on 2006-09-14
This is a very new feature in GParted.

Try the Gparted forums:

[GParted Forums](http://gparted-forum.surf4.info/)

Or documentation:

[GParted Documentation](http://gparted.sourceforge.net/documentation.php)

---

