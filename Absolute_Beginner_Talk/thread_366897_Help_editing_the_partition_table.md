---
title: "Help editing the partition table"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by natman on 2007-02-21
I got  anew laptop and it has a 5 gb partition for restoring windows vista ( i made back up dvd and images of the instead ). Now i cant seem to get rid of the left over 5 gb, currently its called "unallocated" i cant seem to merge it into anything ,partition magic couldn't do it ( something about sserial numbers)
So i have decied to put ubunt on, could i just give that 5 gb as swap (or is it too large for that ) , if i do that do i tell gpart to make it primary-linux swap and resize the manin to primary ext3?
Any help?

Am i right?
Thanks:

---

### Post by mikewhatever on 2007-02-21
If you are able to resize the main partition with Vista or whatever, will the freed space add up to the unallocated space, or is it somewhere else?

---

### Post by natman on 2007-02-21
When i resize the main partition i see 70GB ntfs 80GB ( free'd up ) and the little 5GB still left all by itsself, i formatted it as ntfs but i couldnt find anyway to merge it back to the main.

---

### Post by mikewhatever on 2007-02-21
I always thought unallocated space doesn't need to be merged to the other unallocated space, but who knows. Right, I'd say make a swap partition out of it (about 1GB) and a storage partition of the rest. I assume you want to give the 10 GB freed from the main partition to Ubuntu root, right?

---

### Post by natman on 2007-02-21
Thats what i planned on doing but if i make the 1gb swap, im left with 4gb of unallocated ?? what do i do with that?

---

### Post by mikewhatever on 2007-02-21
A storage partition for either Vista or Ubuntu. I made a FAT32 partition to exchange stuff between XP & Ubuntu, but don't really know it is good for Vista.
Let me ask you, is that restore partition before or after the main one?

---

