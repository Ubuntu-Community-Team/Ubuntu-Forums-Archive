---
title: "A couple of questions about partitioning"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-06-20
So I finally got my computer back to were I can install Linux (long story involving new mobos, not enough IDE controllers, failing HDs, and Dapper not liking my new config), and I plan to triple boot XP, Vista, and Feisty. I already have XP on a 30GB HD, and I plan to replace my failing 40GB HD with a brand new 500 GB Maxtor HD (All ATA/100). I plan to leave my 30 GB entirely given over to XP, and put the 500 GB on the same cable as a slave. Then I want to split it into 4 partitions

100 GB for Vista
50 GB for Feisty
2 GB for swap (twice my RAM, right?)
348 for shared data that all three can access

I'm a bit nervous about this, as I've never installed an HD on my own, and I've never partitioned at all, so I have several questions, which are probably quite simple (I hope). I'm probably more worried about this than I should be... If I bork it, all I have to do is reformat, right?

Do the numbers I'm considering look reasonable for the OSs involved?
Is it better to get my partitions set up before I install OSs, or let them do their own partitioning?
If I do it before, should I use the manufacturer's partitioning program, or GParted?
Is it okay for all of these to be primary partitions, or is it better for some to be logical?
What format should my shared data partition be? I was considering NTFS, now that r/w support seems to be stable. (I have a 64 bit processor, which, last I checked, the Windows program that let it read ext2/3 did not support)

Any help would be very much appreciated! I look forward to being able to run Linux again. Feisty looks very shiny, and I can't wait to give it a go.

---

### Post by mikewhatever on 2007-06-20
> Do the numbers I'm considering look reasonable for the OSs involved?
Is it better to get my partitions set up before I install OSs, or let them do their own partitioning?
If I do it before, should I use the manufacturer's partitioning program, or GParted?
Is it okay for all of these to be primary partitions, or is it better for some to be logical?
What format should my shared data partition be? I was considering NTFS, now that r/w support seems to be stable. (I have a 64 bit processor, which, last I checked, the Windows program that let it read ext2/3 did not support)

Yes, the numbers look OK, but where is the XP partition?

I think it is easier, but can't say if better or worse.

Gparted worked fine for me. What is the manufacturer's program?

All of those primary would by fine, but remember the four primary partitions limit. You will not be able to create another partition on that hdd without deleting one first.

Any format should be fine. ntfs, ext3 or FAT32. I am not aware of 64 bits CPU limitation.

---

### Post by Celegorm on 2007-06-20
> Is it better to get my partitions set up before I install OSs, or let them do their own partitioning?
Probably best to let them do their own partitioning (and install Vista first). I don't have much experience with Vista though, so if someone else knows more, listen to them instead. Although I have heard Vista has problems if you use anything but its own tools to resize its partition.
> Do the numbers I'm considering look reasonable for the OSs involved?
Looks good as far as I know. And swap is usually double your RAM, yes.
> Is it okay for all of these to be primary partitions, or is it better for some to be logical?
Swap is usually (always?) logical.

---

### Post by Hitchhiker42 on 2007-06-20
> Yes, the numbers look OK, but where is the XP partition?

XP has a drive of its very own. I thought about replacing both HDs, but then I realized that installing one copy of Windows at a time was quite enough for this project. :) 

> Any format should be fine. ntfs, ext3 or FAT32. I am not aware of 64 bits CPU limitation.

Just checked out the Ext2 IFS website, and they say it only works with x86 CPUs, and it doesn't look like they have support for Vista yet.

---

