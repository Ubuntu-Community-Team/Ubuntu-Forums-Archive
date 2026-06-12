---
title: "Dual-Boot windows XP and Ubuntu 6.1 on a single drive."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Kossilar on 2007-01-08
Hello.

I recently installed Ubuntu 6.1 on my other computer and got it working acceptably. I find installing software to be ludicrously complicated compared to the Windows XP installation on my main computer, however, the advantages of having an opensource OS and software vs. proprietary Microsoft nightmares is too tempting to pass up. 

That said, I'd like to get my main system dual booting Windows XP and Ubuntu 6.1. 

Here's my harddisk setup:

One 300gb Maxtor 6V300F0 hard drive(SATA2) partitioned into 4 smaller drives. C: & D: are 50gb and E: & F: are 100 gb each.

Windows is on C, obviously. I'd like to put Ubuntu 6.1 on D, formatting it entirely and dedicating it to the new Linux install. 

However, I have no clue how to go about doing this. I realize there are already plenty of threads talking about this, but because of the wide range of variables involved in a person's specific hardware and installation choices, I'd like to have advice specific to my setup rather then risk using somebody elses instructions and destroying my system.

Thanks so much everyone.

---

### Post by Tomosaur on 2007-01-08
Ok firstly, pop in the live CD, then run the partition manager. It should be in the 'System' menu.
Once it starts up, select the partition you wish to edit. You will need to split it into two partitions (one for Ubuntu, the other for swap). The format you should choose is ext3 for the larger partition, and swap for the smaller. The swap partition should be roughly twice the size of your RAM, although it depends on other things too. If you have any more than 512MB RAM, then 1Gig of swap should be fine.

So to summarise:
Open partition manager.
Select desired partition (it won't be labelled C:, D: etc, you need to know the size of each partition).
Add a task to shrink this partition, chopping enough space off for the swap partition.
Format the shrunken partition to ext3.
Format the newly created unused space as swap.
Start the installation procedure and select the option to manually set up your partitions.
Select the ext3 partition for the linux root.
Select the swap partition for swap. (These two steps may not be necessary, the installer should be able to guess what you want to do).

Then just continue with the installation and you should be ok :)

---

### Post by oilchangeguy on 2007-01-08
see the article, on page 129, in the feb. 07 issue of pc world.

---

### Post by Kossilar on 2007-01-08
hmmm... There isn't more configuration then that? I thought you had to fiddle with Boot.INI on the Windows system or some such thing?

---

### Post by mystdragon on 2007-01-08
I have never touched a boot.ini in windows when dual booting.  The Ubuntu installer you will install a boot manager (grub), and it will be configured to boot into Ubuntu automatically.  It is generally superior to allow grub to be in charge of booting, as opposed to windows (in which case you might have to play with files like boot.ini, I don't really remember)

---

### Post by Kossilar on 2007-01-09
hey you're right! It worked! Thanks a lot guys.

---

### Post by Thena on 2007-01-10
> **Tomosaur said:**
> 
Once it starts up, select the partition you wish to edit. You will need to split it into two partitions (one for Ubuntu, the other for swap).

So to summarise:
Open partition manager.
Select desired partition (it won't be labelled C:, D: etc, you need to know the size of each partition).
Add a task to shrink this partition, chopping enough space off for the swap partition. 

So what happens, if I already have Windows of one partition on one disk and an unpartitioned part, that I wanted to reserve for Ubuntu? How can I figure out the size I have to hand to the program?

---

### Post by Bachstelze on 2007-01-10
How much space do you have on the "unformatted part" ? You''ll need about 10 GiB to be comfortable with Ubuntu.

---

### Post by Thena on 2007-01-10
I have about 13,83 GB saved for that.

---

### Post by Bachstelze on 2007-01-10
Then just install Ubuntu in it :) When it will come do disk partitioning, the installer will give you the option to "Use the largest continuous free space", choose it for a low-hassle partitioning, though it's always recommended to partition manually.

---

### Post by Thena on 2007-01-10
Thanks for the quick reply!

Well, I have a 23,44GB-partition for Windows with 14,2GB of free space on that very same disk and about 60 GB free space on another disk installed. Will it not install Ubuntu there then?

---

### Post by Bachstelze on 2007-01-10
That's precisely why it's better to partition manually, it will install where you tell it to :p

---

### Post by petriomelony on 2007-01-10
> **Thena said:**
> Thanks for the quick reply!

Well, I have a 23,44GB-partition for Windows with 14,2GB of free space on that very same disk and about 60 GB free space on another disk installed. Will it not install Ubuntu there then?

if by "installed" you mean already formatted, then you will need to delete/recreate and format that first if you want to install ubuntu on the 60 GB disk.  this can be done by manually editing the partition tables when it asks you in the installation.

---

### Post by Thena on 2007-01-10
> **HymnToLife said:**
> That's precisely why it's better to partition manually, it will install where you tell it to :p

Ok, that´s what I want to do then: partitioning manually.
I want to install Ubuntu on my 13,83GB unformatted part of my 39GB disk, where the other 24 GB are already running with windows. 
@petriomelony :  I don´t want to do it on the 60GB of free space I have.
How do I know, from which sector (or so) on I can install it? I mean, how can I figure out the bytenumber where I can start with the second partition for Ubuntu?

I mean, you said, it would not install it, where I would want it, so I need to do it manually. 
I just don´t plain know, how to do these very steps. (What to enter as starting point for the second partition.)

Thanks a lot for your help.

---

### Post by Thena on 2007-01-10
Well, I´m in the manual part now, where it says "Preparing the Partition".
It shows my ntfs windowspartition as /dev/hda1, and a not assigned part (where I want to install Ubuntu on). When I go right-click "new" (next to "deactivate" the only possible option) it wants to start a new partition, and I am a little bit confused, which values I have to type in for: 
"previous free disk space", "build as", "filesystem"(well, I guess, I need ext3).
Well come to think of it, I guess, this is all about the unformatted part, and one part needs to be the swap-partition (like choosing "linux-swap" as option), as stated in this thread on page 1, right?
So the difference in "New size in MB"=14167 and 13.83GB is just because of the decimal and binary counting, right?

I hope, I´m not bothering you too much with this- I just can´t figure it all out, and I don´t want to destroy anything.

Edit: Should I do the new partition as a primary partition (only this way, I can choose ext3 as filesystem) or as extended partition, as it extends my windowas partition?

---

