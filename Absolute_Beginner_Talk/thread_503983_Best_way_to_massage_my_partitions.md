---
title: "Best way to massage my partitions?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by tryte on 2007-07-18
I'm looking to dual-boot my current Windows box with Ubuntu.  I originally had 3 partitions--15gb for the OS, 5 for a second Win install to boot to if I needed to reformat, and 90gb for my data.  I deleted the 5gb part, intending to install Ubuntu there, until reading that 11 was the minimum recommended  (and a little while later, found 20gb was highly recommended)  

I then attempted to resize my 90gb part, as I have a good chunk of free space, and ended up creating a 6.8gb extended part that I can't combine with the 5gb.
Before I muddle things further, can anyone suggest the best optimization to get a 18-20gb part out of my drive?  

Not sure if PartitionMagic is an option, I've used it in the past and would prefer to avoid it if possible.
At this point I've booted back to windows and am running a defrag right now as I forgot to do so before I started mucking about with my partitions.

Thanks!

---

### Post by Happy_Man on 2007-07-18
Hmmm..... can you boot up a LiveCD, open up Gparted (System --> Administration --> GNOME Partition Editor) and post a screenshot of how it looks? Sometimes, it's easier for us to see the table rather than work off a description.

---

### Post by tryte on 2007-07-18
Will do--I thought of this after I had started the defrag, of course.    I may not get to it until tomorrow, hadn't realized how late its gotten.  Thanks for the reply.

---

### Post by cotcot on 2007-07-18
For partitioning i use the Gparted LiveCD. Do do not need partition magic.
5 + 6.8 GB is OK for installing ubuntu. 5 GB is OK to use as root ( / ). I have pretty full size ubuntu install with 3.5 GB as root.. Split the 6.8 GB in 0.5 GB to use as swap (swap) and 6.3 GB to use as home (/home). 
What is the file system type of the 90 GB partition  (NTFS , FAT) ? If it is FAT then it is easy to read/write to it from linux. If it is NTFS you can read/write  on it as well with NTFS-3G, but there is a small risk here because writing to ntfs is still considered as experimental. Nevertheless it works good in my case. Please ensure a backup, especially when write to NTFS from linux.

---

### Post by candtalan on 2007-07-18
I usually use gparted live cd, and it has always done well.

You can only have a maximum of four primary partitions, so the best philosophy is to get a large free space and create an extended partiton as soon as you can. Then inside this you can create a lot more partitions. If you can backup your large data partition, and delete all but the windows then as I understand it you have a lot of flexibility. If you use a fat32 for your data partition it is easy to use it for both linux and windows data.

There are various options I guess. I know that leaving the whole non windows space as an unformatted partition should mean you can install ubuntu into it semi automatically easily. 

You may subsequently be able to shrink the ubuntu system  /  partition easily and make it into a data one.

A more elegant way is to manually create the partitions and manually edit the install conditions.

Use the extended partition approach, with a 500 mb swap and a 7 gb root (install) partition, and the remainder can be fat32 data partition.

As a beginner this is not too hard, if you are cautious with the manual install - ask details here to understand what you need to do.

If I had 6GB unallocated space on a drive I would happily install ubuntu into it, but space might become tight if I then became more ambitious and did not have a data partiton.

hth

---

### Post by tryte on 2007-07-19
[IMG]http://i18.photobucket.com/albums/b112/ronnehxmp/mydrive.jpg[/IMG]

Ideally, I like the idea of sharing the large data partition--perhaps I can get ahold of an external drive, move my data there, then reformat to fat32 and move the data back.

I'll use the smaller 3.91g part as /root, larger 5g as /home for now (I cut 500mb out of the 5.59 for swap) 
Thanks for the insight!

---

### Post by Happy_Man on 2007-07-19
Well...... if you are not going to be putting much on it anymore, I suggest cutting most of the white part out of the big partition -- leave 2 gigs for buffer space, just in case you do. Then, cut out 500 MB of swap, keep the 3.91 GB as /root, give the empty space to /home. And if you're worried that you won't be able to read your Linux-formatted data in Windows, there are drivers for that, so don't worry. Have fun partitioning! (But not too much, otherwise you could format it. That's bad. :p)

---

