---
title: "Dual boot XP"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-02-16
I've only tried the Dapper LiveCD once, but I know I'll want to install it to get full benefits from it!

I'm running XP Home SP2, on an Athlon 2100 processor, 256Mb RAM.

I have two physical drives, the first is FAT32, two partitions, and contains 
 C: drive with Windows and installed software, 19.5GB, about 4GB free
 D: drive with My Docs for three users plus myself, and downloads. 18.5GB, about 14GB free. 

The second (E: ) drive is NTFS, and contains my backups, 38.5GB, of which 18GB is free. 

Where would be the best place to install Ubuntu? Not C:, I know! I've tried to keep my E: purely fo rbackups, as I've had two hard drive crashes in four years, and it's a separate drive.

TIA

---

### Post by mikewhatever on 2007-02-16
Hi freesitebuilder,
what you call drives(C,D,E) are really just partitions on one physical hard drive. Anyway, to install Ubuntu, you'd need to resize one of those partitions. C has the least amount of free space that Windows probably needs, so the other two should be fine.

---

### Post by bjornolai on 2007-02-16
Hi,

My suggestion is resize what windows calls your d:\  freeing 12 gig. Then you make this space into an extended partition, and inside it you make three logical partitions. Format one around 7 gigs as ext3, another one at 2gig for/as swap, and the third 3 gigs as ext3 for home. 

Since your windows is on a fat32 drive ubuntu will read and write to it. Your backup drive however ubuntu will (without some tweaking which I haven't bothered trying to do) only read from. 

My suggestion is you fire up the live cd and use gparted to do the partitioning before running the install program :) You will find it under system > administration > gparted

Remember to backup important data. I've done similar partitionings many times and nothings ever happened, but you never know.

---

### Post by freesitebuilder on 2007-02-16
I've been reading up on psychocats.net and the Gparted site on this - if I want to use D: will I need to use the manual option, rather then let gpart do it all for me? Or will gpart realise that there's not enough room on C: ?

---

### Post by Tomosaur on 2007-02-16
> **freesitebuilder said:**
> I've been reading up on psychocats.net and the Gparted site on this - if I want to use D: will I need to use the manual option, rather then let gpart do it all for me? Or will gpart realise that there's not enough room on C: ?

I always prefer manually editing the partitions - I don't trust software to make smart decisions!

If C: is out of the question, and you want to keep E: for backups, then your only real choice is D:. Depending on your configuration - the various drives could either be partitions on a single hard drive, or completely different drives. If the former, you will only need to shrink your D: partition (it should appear as the 'middle' chunk of hard disk). If the latter, you'll need to point gparted at the D: hard drive (although it won't be called D: in the program itself, it will be /dev/hdb or something similar to that). Then, shrink that partition.

In the free space created, you will need to create a minimum of two partitions. The largest should be formatted as a linux filesystem, most people use ext3. You should format the smallest part as swap. The swap partition should be around twice the size of your installed RAM. Once these partitions are correctly formatted, you can proceed with installation :)

---

### Post by hanexar on 2007-02-16
For our Ubuntu installation, I suggest you manually build 3 partitions:

1- Primary Ext3 mount on "/" (it will be your systems files, the root, actually 7~10 Gig is enough)
2- Primary Ext3 mount on "/home" (to save your preferences, like that you can reinstall "/" without loosing your preference, quite usefull. It is like the document and setting in windows. Put a few gig here, or more if you want to store file there)
3- and a Swap (Your swap should be twice your RAM, no need for more)

At first view, your "D" drive seems to be fine, but you'll be limited with the storage place since Ubuntu will take all the rest of your space. I suggest you put Ubuntu on your second hard drive (the backup one). Like that your NTFS partition will be reformat :) . Just put your backup somewhere else if you can (DVD?). Also, you won't have to resize existing partition. Just my 2 cents ;)

Good luck, and welcome to ubuntu

---

### Post by freesitebuilder on 2007-02-17
Having looked at GParted, I've realised that it uses GiB and MiB, rather than Gigabytes and megabytes. Do I need to be this accurate when partitioning? Or is this simply referring to "real" megs and gigs, rather than the common usage nowadays where they're often rounded to 1000's (rather than 1024) base?

---

### Post by freesitebuilder on 2007-02-18
Found the answer - international standards strike again!

---

