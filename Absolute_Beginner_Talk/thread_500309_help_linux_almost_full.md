---
title: "help linux almost full"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-07-13
My linux partition is about 10GB and based on the information, already 96% is used. I want to increase it to 15 or maybe 20GB. 

I have: [10GB + linux] [60GB + storage] [swap]

Even if I resize the storage partition, the free space is after it and not before. How can I make the linux partition bigger.

*I'm on the LiveCD

---

### Post by freebird54 on 2007-07-13
I gather you have the free space already created by shrinking a storage partition?  Assuming (scary word, that) that the partition you WANT to increase is next to the one you have shrunk, all you need to do is MOVE the shrunken one over, then expand the other.  If this is not sufficiently clear, I would need more information (like your partitioner screen shot, or a list of partitions) to be more specific.

I hope you have things backed up - I find that all goes without problems as long as having a problem wouldn't hurt anything :)

Also - you may find that cleaning out /var/cache/apt/archives would give you some space (those are the .deb files that apps were installed from) - which could mean you could put it off for a while! :)

---

### Post by Nessa on 2007-07-13
[IMG]http://h1.ripway.com/jgd0m/foredit/gpart.gif[/IMG]

How can I move that unallocated space next to the first partition? I can't seem to figure it out.

---

### Post by anarchyreigns on 2007-07-13
Use Gparted to shrink your storage partition, doing so creates unallocated space. Then take the 10GB partition and resize it to make it larger. Make it as large as it can be, and it'll add the unallocated space that was created when you shruk your storage partition.

UPDATE:
Okay I just saw your new post. Now just grow hdb1. You'll be able to enlarge it by the amount of unallocated free space that you have.

---

### Post by Nessa on 2007-07-13
I can't seem to make it grow.It doesn't have that option. But hdb3 can. How can I move the unallocated space between hdb1 and hdb3?

---

### Post by laidback on 2007-07-13
Try this:-
Shrink hdb3, then move it to the right leaving enough vacant space to the left of hdb3 to allow you to subequently enlarge hdb1.
or
Move hdb3 as is over into the unallocated space to its right. This will leave a similar space to the right of hdb1 into which you can enlarge hdb1.
but.... for either of these to work you cannot have the drive active (mounted). Instead boot from the Ubuntu Live CD and run Gparted from there. There is also a Gparted Live CD, a search on Google will get the site, download the ISO and burn your own bootable CD.

---

### Post by Nessa on 2007-07-13
Can't move it. So I went ahead and deleted the whole storage partition. Resized the linux partition and formatted the unallocated space to ext3.

It didn't work the way I expected it to be but problem is solved. 

Thanks guys!:)

---

