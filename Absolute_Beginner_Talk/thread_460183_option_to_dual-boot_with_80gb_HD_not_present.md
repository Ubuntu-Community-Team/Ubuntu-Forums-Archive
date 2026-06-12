---
title: "option to dual-boot with 80gb HD not present?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-05-31
I have an 80gb HD, its all in one piece except for two unused bits at the end 8mb each that I can't send anywhere or make into a new partition.  I want to install Ubuntu and see how it interacts with everything we do on XP here at work, because some of our more tech-savvy people(i.e. Me) want to use a different OS.  

I used the livecd before and got a resolution of 1200x1024 or whatever that main big one is, and I went to do it this time and the only resolution i can use is 640xsomething, and I only get the option to use the entire disk.  Is there something I have to do on my main machine to fix this foobar?

---

### Post by keith19 on 2007-05-31
Hi nintennuendo,
I think you maybe need to partition your 80Gb drive. Then Ubuntu will see the new partition and ask if you want to use that.

If XP is already installed on the 80Gb drive, you need to figure how much of the drive you will continue to need for XP stuff in future, especially if it's a works machine.
Ubuntu will go into a new 10Gb partition, but 20 or 30 Gb is better.

You can either partition the drive from XP if you have admin rights, or use a floppy or CD with Partition Magic, or download a Linux partition manager like QTParted. But I'm not sure whether Ubuntu would let you use that from a Ubuntu CD loaded into RAM (live disk).

Make sure your office administrator knows what you're doing if you are on a machine at work, as partitioning is a serious business - you don't want to lose Windows just yet. 
If you haven't used a partitioner before, please read the help files or the manual pages carefully before you start. Best wishes with this project.

keith19

---

