---
title: "How long should the partitioning take?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-10-04
I'm currently setting up a 50/50 partition on a 150GB hard drive. How long should it take to do this? It's been going at it for a good 10+ minutes...

Can I cancel the partition? Or will this mess up my computer?

---

### Post by odinfromvalhalla on 2006-10-04
my current setup has a 250GB HDD which took less than 1 minute to partition using reiserfs.

i think i should not take more then a few minutes max. 10 i think it's a bit too much, but hey, if you selected some kind of "check for bad blocks" or anything like that it might take longer.

i remember back in the days of slack that formattin a 10GB partition took long enough when checked for bad blocks.

---

### Post by Jordan Meeter on 2006-10-04
Can I cancel the partition process?

PS - The CD drive keeps cycling. It slows down for a couple seconds, then speeds up for a couple minutes. Just keeps doing it and doing it and doing it...

---

### Post by rccharles on 2006-10-04
> **Jordan Meeter said:**
> I'm currently setting up a 50/50 partition on a 150GB hard drive. How long should it take to do this? It's been going at it for a good 10+ minutes...



It will depend on what filesystem you choose to install.  My understanding is the ext2&ext3 write multiple copies of the root directory to the disk for data recovery purposes.

What is up?
When I am not sure what is going on with a machine, I run top in a terminal session.  In a terminal/console session, type in:

top

You will see lost of info, I focus on CPU utilization.

Robert

---

