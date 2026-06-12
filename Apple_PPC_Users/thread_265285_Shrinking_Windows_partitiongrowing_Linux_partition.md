---
title: "Shrinking Windows partition/growing Linux partition"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by think13 on 2006-09-25
OK, what I want to do is shrink my Windows NTFS partition by about 5 gigs, move my ext3 Linux partition right behind that, and then expand the Linux partition to fill up the freed space.

I have been attempting to do this with QTParted.  Before, it wouldn't let me do anything with the NTFS.  But I installed this NTFSProgs package, and now it will let me resize it.  I resize that to the size I want (without commiting the change) and then try to move the ext3 partition.  It won't let me do anything with the ext3 partition!

Anyone know how to solve this?

---

### Post by avtolle on 2006-09-25
IIRC, you cannot move the "beginning point" of the ext3 partition; you can only move the "other end" to enlarge. So, what it seems to me you will need to do, is to make a backup copy of your ext3 partition; then resize your ext3 partition after reformatting the exisiting partition. Sorry this is so general; I'm going from memory. I trust those reading this post who see any error in my ways will correct same for your benefit.

---

### Post by think13 on 2006-09-25
Could I shrink the NTFS partition, create a new ext3 partition in the freed space, and then somehow merge the two ext3 partitions?

The thing is, now I only have 5.11 Gigs on my Ubuntu side, and I would like about 10 gigs.  Is reinstalling Ubuntu an option? If so, how would I go about doing that? I just installed it yesterday, so I don't have much on it yet.

---

### Post by think13 on 2006-09-25
I think I am going to reinstall Ubuntu.  

All I need to do for that is to restore the Windows boot with fixmbr, put in a Knoppix Live CD and delete my linux partitions, resize the windows one to how large I want it, then install ubuntu, right?

---

