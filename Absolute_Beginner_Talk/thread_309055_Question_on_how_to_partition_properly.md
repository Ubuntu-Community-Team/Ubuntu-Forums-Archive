---
title: "Question on how to partition properly"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Flying Nosehair on 2006-11-29
OK, so I have this laptop whose label says it has 80 GB of hard disk space. 

When I look at its hard disk in Windows, it turns out that there are a drive C and a drive D that each take up about 35 GB. I used to think that, for whatever reason, the manufacturer saw it fit to give the laptop two separate hard drives each about 35 GB rather than one about 70 GB. My plan was to use drive D to hold Ubuntu since drive C already holds Windows. 

However, when I start using the partitioner that comes with Ubuntu, it seems that drive C and drive D are actually two different partitions. I also notice some 5 GB partition that's "in front of" drive C and that I did not notice when looking at the different drives on Windows. 

I try to move ahead by decreasing the size of drive D to make room for the root partition and the swap partition because I noticed a message below saying that I would need at least 2 GB for the root partition and 256(?) MB for the swap partition. However, after I make a partition for the root partition and then try to make one for the swap partition, I end up not being able to because I'm told that I can't have more than four primary partitions. 

So I decide instead to delete the partition for the D drive and put an extended partition that's about 35 GB in its place. Then, within that part partition, I make an logical partition that's about 3 GB for the root partition as well as one that's about 900 MB for the swap partition. I then have the computer "carry out" the orders that I have given it and then click "Next". 
Well, once I've done that I notice that the 5 GB partition and the 32 GB partition holding Windows are the only two partitions that appear on the next screen. So I remove them by selecting the blank space for what kind of partition I want them to be as well as the blank space for their names. 

I then select the names for the partitions for the partitions I want to hold Ubuntu proper, the root, and the swap. I also label them accordingly by selecting their appropriate types (I select /home for the partition to contain Ubuntu proper) from the bars on the left. Then I go ahead and click "Next". 

When I decide to have the computer carry out my orders, I am warned that all the data on those three partitions as well as on any that I might have removed shall be deleted. 

Worried that this would delete the data on the partition containing Windows as well as on the 5 GB partition (whatever it may contain), I go back and redo everything I did except that this time, instead of removing the 5 GB partition and the one containing Windows, I leave them the way they are as "/mount/hd1" and "/mount/hd2" (or something like that) as their types. Then I add the other three partitions the exact same way that I did earlier and click "Next". 

However, this time I'm told that I haven't designated a partition as the root partition even though I designated the approximately 3 GB partition as the root partition just like the previous time. So my question is what am I doing wrong?

---

### Post by DerHesse on 2006-11-29
you have to give the mount options as well.

/ for your root drive.  swap does not need a mount point.

The Partition you have at first place (5GB) are probably for restore of C-Drive from OEM.

Primary Partitions:

1st. The Recovery-Partition,
2nd  Windows
3rd  Data
4th  ext3

Should work fine.

Do your readers a favor and use breaks while typing.
Your post is almost impossible to read.

---

### Post by Flying Nosehair on 2006-11-30
OK, I'm sorry about the lack of breaks. I shall endeavor to remember to break any long posts into paragraphs from now on. Thanks for having the patience to read it all, though.
Having said that, though, to reiterate, I have 35 GB for Ubuntu as I said in my earlier post (and hard to read) post. With that in mind, how much should I set aside for the 3rd partition (i.e. the Data partition)?

---

### Post by bodhi.zazen on 2006-11-30
> **Flying Nosehair said:**
> OK, I'm sorry about the lack of breaks. I shall endeavor to remember to break any long posts into paragraphs from now on. Thanks for having the patience to read it all, though.
Having said that, though, to reiterate, I have 35 GB for Ubuntu as I said in my earlier post (and hard to read) post. With that in mind, how much should I set aside for the 3rd partition (i.e. the Data partition)?

How much data ?

IMO 20 GB for /data

---

### Post by Flying Nosehair on 2006-11-30
So 20 GB for the Data partition and 15 GB for the ext3 one, right?

---

### Post by bodhi.zazen on 2006-11-30
IMO yes, go for it....

---

### Post by Flying Nosehair on 2006-11-30
OK then, but what purpose does the ext3 partition serve?

---

### Post by seshomaru samma on 2006-11-30
If I understand correctly 
what you are advised to do is to make 2 partitions for Ubuntu (3 if we include the Swap) 
In one partition called '/home 'you put your data (somewhat similar to 'my documents' in Windows)
In the other called '/ ' (or 'root')you have Ubuntu
this way if you want to reinstall or upgrade you keep all your settings and data

---

### Post by bodhi.zazen on 2006-11-30
> **Flying Nosehair said:**
> OK then, but what purpose does the ext3 partition serve?

The ext3 partition is for / or root or your Ubuntu OS.

Small problem however. You need 5 partitions and can only have 4 primary partitions.

I would advise 2 primary partitions and an extended partition with 3 sub-divisions called logical partitions.

See here for some basic information : [Basic partitioning](http://www.ubuntuforums.org/showthread.php?t=282018)

You will end up with 5 partitins:

[list=number][*]your restore partition
[*]Your windows partitin (NTFS ?), AKA c:\
[*]Ubuntu root partition. Size = 10-15 Gb
[*]Swap. Size = RAM X 2, 1 Gb max
[*]Data partition. ? FAT although you could go ext2 or ext3. Size = "the rest"[/list]

Hey, don't forget to defragment and backup your windows partition....

---

### Post by Flying Nosehair on 2006-11-30
Thanks a bunch. I'll read that section on basic partitioning. I'd like to get one thing straight, though: My root partition should be a primary partition; my data partition should be an extended partition with 3 logical partitions: the main data partition, a swap partition, and one more partition for "everything else", right?

---

### Post by Circus-Killer on 2006-11-30
> **Flying Nosehair said:**
> Thanks a bunch. I'll read that section on basic partitioning. I'd like to get one thing straight, though: My root partition should be a primary partition; my data partition should be an extended partition with 3 logical partitions: the main data partition, a swap partition, and one more partition for "everything else", right?

there is no set ruling on how partitions should be set up. it depends drastically on what you want to be doing on your machine and also your own personal preferences. here's how mine are set up:

/dev/hda1 = /boot     (150MB)      (ext2)
/dev/hda2 = swap      (1GB)        (i have 512MB RAM)
/dev/hda3 = /         (+-38GB)     (ext3)
/dev/hdb1 = /home     (+-78GB)     (ext3)

all are primary partitions. this is just my prefered layout of my partitions, but as i said before, its got a lot to do with personal choice and what the machine will be doing.

---

### Post by bodhi.zazen on 2006-11-30
> **Flying Nosehair said:**
> Thanks a bunch. I'll read that section on basic partitioning. I'd like to get one thing straight, though: My root partition should be a primary partition; my data partition should be an extended partition with 3 logical partitions: the main data partition, a swap partition, and one more partition for "everything else", right?

Some OS, particularly Windows and most BSD, must be installed into a primary partition.

Linux (root, swap, or data/home partitions) can go into a primary or extended (logical) partition.

I am not aware of any particular advantage to installing into a primary vs an extended partition.

---

