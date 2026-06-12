---
title: "Dual boot, partition set-up options"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by susan_1890 on 2007-06-06
I've just order a Dell Latitude D630 with Vista Business that should arrive in another week or two. When I get the machine, I want to set it up as dual boot with Ubuntu and I'm trying to decide the best way to partition my drive. 

In both installations, I want to set up a partition for just the OS and programs and keep all my data on separate partitions.

My new hard drive is 120 GB. Here's my planned partitioning:

1) 15GB NTFS for Vista and Windows programs
2) 10GB ext3 for Ubuntu and programs
3) 1GB swap for Ubuntu
4) 40 GB for music and videos which I plan to access from both Ubuntu and Vista.
5) 20 GB partition for current documents (office docs, computer code, etc) that I want to read/write from both Ubuntu and Vista. I'd like to set it up so most things I read/write in either OS on a regular basis are here. 
6) ~25 GB for less frequently accessed data.

I'm trying to figure out the best format for 4,5, and 6. I'd originally figured they'd have to be FAT32, but I've been reading a lot of stuff about the new NTFS support in linux and about possibilities for reading ext3 files in Windows.

In the short term, I'll probably use Vista more than Ubuntu, but if I can make moving back and forth as painless as possible, I think the chances of migrating to primarily Ubuntu are pretty good.

Any thoughts on which format (FAT32, NTFS, or ext3) is likely to work best for me?

---

### Post by Zzl1xndd on 2007-06-06
1) Fat32 will be no problem at all really easy to do. pro by far the easiest route, con really old 

2)Ext3 as I understand needs some extra's installed to work with windows and doesnt need to be defraged. never done it myself as I dont use windows anymore but im told its not too much work

3NTFS I use a drive that is formatted in NTFS and works great (need the extra's installed to write from Ubuntu) but it does need to be defraged, the install was easy and quick

---

### Post by Nikron on 2007-06-06
If I were you I'd just make 1 NTFS partition, 1 ext3, 1 swap.

---

### Post by testube_babies on 2007-06-06
I use a combination of all three options :)

1) NTFS partition with ext2ifs
2) ext2 partition with ntfs-3g
3) FAT32 partition for extra data

note:  15GB for Vista is probably not enough.  My Vista install + Programs (no docs/music/etc) is 22GB alone!
note2: One hard drive can only have 4 physical partitions.  You can work out the physical vs. logical stuff on your own, but 6 partitions might get difficult to manage.

So, if I were you, here's how I would do it:

25 GB NTFS for Vista
25 GB ext3 for Ubuntu (includes /home)
70 GB FAT32 for documents, music, etc
~1GB swap

---

### Post by Bohlio on 2007-06-06
My shared Data is NTFS and accessable for read and right through ubuntu by the use of NTFS-3G... Thats what I vote for. I dont know why i chose it, but i did and it works just fine :-) I dont think it really matters too much, as long as you can find a way to read and write to it.

---

### Post by bren on 2007-06-06
I agree with testube_babies - not a phrase i thought I would say today.

i have all three and all three work great on my machine

no long term use here yet though......

bren

---

### Post by susan_1890 on 2007-06-06
Wow! Thanks for all the quick advice. I'd completely forgotten about the primary versus extended partition thing and the limit on primary partitions.

Given that, I'll probably take most of your advice testube_babies. I'll make the two 25GB primary partitions for Vista and Ubuntu.

Then I'd like to make the rest of the disk a single extended partition and divide it logically. I like keeping the stuff I use regularly on a separate partition from music and old files to make back-ups easier. Can I put the linux swap partition in a logical partition on the same extended partition as other NTFS/FAT32 partitions?

---

