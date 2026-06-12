---
title: "Partition order in installing"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Joiner on 2006-06-26
Hi, I am writing these words from Ubuntu live Cd.Iwant to install it to my hard drive.Bu t I have some problems with disk partitioning part of the installation.I have three partition of one hard disk.F&#304;rst one is 14 gb and there is windows installed.second one is archive of my windows system which is about 35gb.And the last one 9 gb which I want to install ubuntu.

I take the manuel disk partitioning option in the installation.There is a window opened and want me to choose partitions.I want to use windows and ubuntu together.I am confused to make the choices there.Now my questions:

_ there is "root" section I  have to choose, I want my 9 gb empty partition to be root.This root thing can be in windows partition without giving any harm to the files?Or should &#305; put it to the empty 9 gb partition?

_ there is swap I have to choose.This swap has to be in the end of the partition order or should be somewhere else.If I choose 9 gb partition as a root, I guess I  cant  put swap in 9 gb partition.Can &#305;t be possible to put swap in empty parts of the windows partition?

_ After &#305; choose root and swap, is there a must for "home" or smth else?I guess there is a must cause even &#305; made the root and swap, it asks me for to mount these partitions.


_

---

### Post by aysiu on 2006-06-26
I would create a tiny swap partition (twice your RAM size but no bigger than 1 GB) out of the empty 9 GB and use the rest (8 GB or so) for the / (root) partition.

---

### Post by acht on 2006-06-26
so is the 9 gb an logical drive or is it unallocated?

---

### Post by bukwirm on 2006-06-26
If you delete the 9 Gb patition, you can use the automatic partioner - select 'use all free space'.

Otherwise, the only partitons that are nessecary are / and swap, so you do need to break your 9 Gb partion into at least two partions ( swap needs ~ 1Gb and / can have the rest)

---

### Post by aysiu on 2006-06-26
I would use unallocated, but there isn't any one definitive answer.

---

### Post by Joiner on 2006-06-26
Thanks for answers.My 15 gb partition is primary and others are logical including 9gb partition which I want to install ubuntu.

My wonder is, Can I put swap in another partition which is used by windows?

---

### Post by aysiu on 2006-06-26
Swap needs to be its own partition.

You can resize an existing partition and create a new extended partition out of it for swap, though.

---

### Post by Joiner on 2006-06-26
Ok I get it.So there is no need anything else after swap and root is done, right?

---

### Post by Joiner on 2006-06-26
And Should I make the partition for swap primary or logical? I am using Drapper, I guess there is no need for grub in ubuntu, it makes it automatically.Right?Cause as I said I will use two OS.

---

### Post by aysiu on 2006-06-26
I don't know the exact differences between primary, logical, or extended, to be honest.

I've just installed on whatever partition's available. The installer won't let you do something that's not possible.

And, yes, Grub on the Desktop CD will automatically install to the MBR and allow you to dual boot.

---

### Post by Joiner on 2006-06-26
Thank you very much for help.I will try to make a swap partition then install.

---

### Post by wpshooter on 2006-06-26
I would use your open space to partition like this if possible:

/ (root) primary ext2 - 4 gb
/ home  primary ext2 - 4 gb
swap -linux swap      - remainder

My personal preference would be to have a bit more space available to do a Ubuntu/Linux installation on.

Good luck.

---

### Post by e_james on 2006-06-26
A standard hard disc drive can be split into a maximum of 4 primary partitions. The last primary partition can be reassigned as an extended partition. This extended partition can be further subdivided into many logical partitions. Any primary or logical partition can be formatted in a variety of ways such as FAT32 or NTFS for Windows and Swap, ext2, ext3 etc. for Linux. 

Generally the Windows boot partition has to be primary and near to the beginning of the drive. Linux doesn't have that limitation.

---

### Post by Joiner on 2006-06-26
I made a partition for swap 1 gb.And my 8 gb space became the root.I made the 8 gb partition primary.And the other partitions stayed as media.&#304;nstaller said no problem.But when the installatin comes to the %15 all system installation cuts off.It was saying "checking the file system" and then the &#305;nstallation stoped and the installation windows dissappears.Whats wrong I didnt get it.This 8gb partition is in  ntfs  format.While using the manuel partitioning I have choosen the reformate this partition for ubuntu but &#305; guess because of installation is being cut off, the 8gb partitioon stays in ntfs formate. I couldnt understand the problem.The &#304;nstaller already made the swap very well but for the root partition didnt work out.

---

### Post by e_james on 2006-06-26
What I'm about to say may have nothing to do with the failed install, but I would like to clarify a few details. from what you have said so far I think the layout of your drive is as follows

Partition 1 - primary - 14 or 15GB for Windows applications (C: drive) - NTFS
Partition (2) - extended
....Within the extended partition
....Partition 3 - logical - 35GB for windows data - NTFS
....available space - 9GB

The available space is within the extended partiton so any partitions created here must be logical.

wpshooter suggested a space allocation - 4GB / (root), 4GB /home and 1GB swap, but they can't be primary.

I think you may have decided to use 8GB / (root) and 1GB swap. That should work too. A separate /home partition has the advantage that you can reinstall Ubuntu or install a different distribution without disturbing the data in /home (in theory, I have reservations about that). The choice is yours, but if you do make a separate /home partition, at this stage I would include it in any formatting operations.

It might be helpful to do the partitioning using the Live CD facilities before you initiate the install. That way you should be confident that the layout is valid. During the install you can allocate mount points / (root), swap etc. Some of the steps might be repeats of what you did earlier, but that shouldn't hurt. You will, of course, take care that you don't change the Windows NTFS partitions.

If any of the above is not sufficiently clear, please ask questions.

---

### Post by Joiner on 2006-06-26
Your layout is right.9gb partition was logical but because the installation didnt work out &#305; decided to change it to primary.Nothing changed.Still installation is being cut off.I did partitioning with partition magic.I will try your home drive advice but I still didnt understand why the installation is  terminated.

---

### Post by e_james on 2006-06-26
Like I said, my comments might have nothing to do with the failed install. I should point out that, while I have experience with partitioning for multiple OSs (much of which came from reading the Partition magic instruction book), I am very much a beginner with Linux.

The following possibilities come to mind.

-Are you sure you have a good install CD? I think there is a CD test routine when you start it.

-I have a computer (Shuttle XPC) which won't boot up the Live / Install CD and a couple of other recent Linux live distributions. Presumably some sort of hardware incompatibility. I may need to take note of the error messages and ask questions here.

-I think I saw a comment in some forum in the last few weeks that Partition Magic may not create partitions correctly for Linux. The last time I used it for Linux was about a year ago and the partitions were ext2. They worked fine.
When I partitioned the laptop I am using right now (in Windows), it was all Linux software. I also did my Ubuntu install using the Alternate CD where the partitioning, mounting, formatting etc. is set up in text mode.

This link [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) has detailed instructions about setting up dual boot with that CD. I should say that I had the job done before I read it. I might have done things slightly differently otherwise.

---

