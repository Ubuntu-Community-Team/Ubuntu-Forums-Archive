---
title: "[SOLVED] Recommended partition/directory sizes"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by vwilson on 2008-01-29
The new Ubuntu 7.10 Desktop Training Manual discusses Partitioning and Booting in chapter 11. 
It suggests making separate partitions/directories for root , swap, /var, /tmp, /usr and /home. 
I'm assembling a new system that will have a clean install of Ubuntu 7.10, no dual boot, 4 G of RAM, a 500 G hard disk to put the system on and a large RAID5 array for media file storage. I'll be using the system for a NAS and also to learn Linux on, with the intent of eventually replacing my Windows systems.
Considering I want to "future proof" as much as possible (not have to resize partitions):
How much disk space should I allocate for each of the partitions/directories above?
What do you suggest be located on primary versus extended partitions?
In other words, what's a suggested partition scheme?

Thanks for your suggestions.

---

### Post by banda on 2008-01-29
i suggest only having partitions for /, /boot, /home. the rest are unnecesary. the root partition can be of 20GB and the home according to your requirement (keeping raid in mind). 200mb for the /boot will be more than enough and you can make them all primary partitions if you have only 4
personally i also have a big ntfs partition so that windows can read it incase i ever have to put the hard drive into a comp running windows(also helps with a dual boot)

---

### Post by forrestcupp on 2008-01-29
It's a matter of choice and opinion.  I, personally, don't see any reason to have so many partitions.  For me, I only make a root, swap, and /home partition.  And the only reason I would make a /home partition is to save all of my data and settings if I need to reinstall.  If you just leave all of the system stuff on one partition, you don't need to worry about how much room it will take up.

As far as the size of your /home partition, that just depends on what you will be doing.  If you will have a lot of pictures, music, and videos, you will want to make it pretty big.  If not, you may want to make more room to install apps with in your root.

---

### Post by vwilson on 2008-01-29
Let me add a little clarification.

Assume I want to have all the suggested separate partitions/directories.
and
The /home directory will occupy the remaining disk space not taken up by the other partitions/directories.

Thanks.

---

### Post by p_quarles on 2008-01-29
Since you have plenty of space, I'd give liberal partition spaces to the directories you mentioned. 2 GB for var, 6-10 GB for /usr, and 1 GB to /tmp. For / (i.e., "root"), let's say 3 GB. You have plenty of RAM, so the Swap partition doesn't need to be any more than 500 MB at most. 

And, like I said, that's a very liberal allocation of space. Gives you plenty of room to work with.

---

### Post by MoToR on 2008-01-30
As far as I understood if your swap partition is smaller that you RAM, you won't be able to Hibernate. Which sometimes is a good feature to have.

I use hibernation on my laptop for obvious reasons, and on my desktop in case of power interruption for a period longer than my UPS can hold.

Correct me if I'm wrong. I'll be glad not to waste 2GB of quite limited laptop HDD space for swap partition if there's another way to hibernate.

---

