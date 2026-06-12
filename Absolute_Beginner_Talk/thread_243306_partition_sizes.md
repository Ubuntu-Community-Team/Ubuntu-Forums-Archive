---
title: "partition sizes"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by b1g4L on 2006-08-24
Here is what I have partitioned:

1GB swap
5GB home
remaining 17Gb root

My question is this...Do you usually give the remaining space to home or root? I got confused while re-installing Ubuntu. Thanks!

---

### Post by o_fortuna on 2006-08-24
> **b1g4L said:**
> Here is what I have partitioned:

1GB swap
5GB home
remaining 17Gb root

My question is this...Do you usually give the remaining space to home or root? I got confused while re-installing Ubuntu. Thanks!
You usually give most of the space to home -- that's where you keep most of your data (music, etc.).

Personally, I recommend that you not separate the partitions since it just means that you have a better chance of running out of space.

---

### Post by b1g4L on 2006-08-24
So when I have to partition, I can just create a swap and root partition? Giving swap 1 GB and root the rest?

---

### Post by o_fortuna on 2006-08-24
Yeah, essentially. Having a separate /home can be useful, but with such a small amount of space (as what you have), it's probably better to stick with a single root partition.

About swap, you could go with less depending on how much RAM you have. If you have at least 1GB of RAM, you can go with 512MB of swap. Otherwise, you're fine with what you've got.

---

### Post by mssever on 2006-08-24
For swap, the old rule of thumb was to make it twice the size of your RAM. But nowadays, you probably don't need much more than 500-600 MB for swap.

I think that having a separate /home partition is a really good idea, since it helps protect your common data and enables you to easily re-install without losing your files. There have been several occasions when I've been really glad that I have the separation. The downside is that you have to play a bit of a guessing game as to how to size your partitions. I recomend trying to leave as much space as possible on your hard disk unpartitioned. That way you can use it however you need it down the road. Also, something that I'm planning to look into eventually is LVM, which allows you to dynamically resize your partitions. Don't know much about it right now, though.

---

### Post by b1g4L on 2006-08-25
Alright. Thanks alot!

---

