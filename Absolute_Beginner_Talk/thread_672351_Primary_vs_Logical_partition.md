---
title: "Primary vs Logical partition"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-01-19
I'm setting up a dual boot on my computer between Windows and Ubuntu.  Since that means five partitions, I'm going to need at least one logical partition.  Do I need to make all my Ubuntu partitions logical, or can I just make one of them logical?  And what't the difference?

---

### Post by jimrz on 2008-01-19
> **Yes said:**
> I'm setting up a dual boot on my computer between Windows and Ubuntu.  Since that means five partitions, I'm going to need at least one logical partition.  Do I need to make all my Ubuntu partitions logical, or can I just make one of them logical?  And what't the difference?

Welcome

   You are allowed 4 partitions on a single hdd one (only one, but it may contain many additional partitions)) of which may be an "extended" partition. You should create your extended partition and then create whatever additional partitions you need, as logical partitions, within the extended partition. You may, if you like, place all of your Ubuntu partitions with in the logical partition. I would suggest at three for Ubuntu, / + /home + swap (this one will be created automatically by the installer).

---

### Post by Yes on 2008-01-19
When I make the logical partition it won't let me make new partitions in it, it just acts like a normal primary partiton.

---

### Post by thelatinist on 2008-01-19
No, you don't have to make all of them logical.  You can have them in any combination you like.  You could even have your entire linux installation inside an extended partition.  Logical-vs-primary shouldn't make any difference.

---

### Post by thelatinist on 2008-01-19
> **Yes said:**
> When I make the logical partition it won't let me make new partitions in it, it just acts like a normal primary partiton.

To clarify: logical partitions are the pseudo-partitions which are created inside an extended partition to get around the four-partition limit.  You can't create a partition within a logical partition, only an extended one.  You probably have an extended partition completely filled by a logical partition.  In that case you need to resize the logical partition to create free space in the extended one before you can create the new logical partition.

---

### Post by Pogeymanz on 2008-01-19
To keep things the least confusing you should have TWO primary partitions: Your Windows, which should be the first partition on your HD and shout also have the "bootable" flag.

The second primary partition is called an "Extended partition." Make that the whole rest of the hard drive space. (This is where your Ubuntu partitions will go)

Now when you make a Logical partition it will be "under" the extended partition. It is recommended that you make three logical partitions: /home, /, and swap. swap should be 2 times your RAM. / should be 6-10 gigs and /home should be whatever is left.

To summarize: Make an extended partition and then make three logical partitions "inside" of the extended partition.

---

### Post by Yes on 2008-01-19
Ok, I made the swap logical, but then when I made my /home partition it didn't give me the option of logical/primary.  Is that ok?

---

### Post by jimrz on 2008-01-19
sorry ... I inadvertently used "logical" where it should have said "extended" in my previous post, which I have now corrected. I apologize for any confusion this may have caused you.

---

### Post by thelatinist on 2008-01-19
> **jimrz said:**
> sorry ... I inadvertently used "logical" where it should have said "extended" in my previous post, which I have now corrected. I apologize for any confusion this may have caused you.

Since you can only have one extended partition, it should automatically determine whether any new partition you create is primary or logical based on whether you are creating it in your extended partition or not.  Inside extended = logical.  Outside extended = primary.

---

