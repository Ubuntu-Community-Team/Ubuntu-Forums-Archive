---
title: "Partitioning trouble with feisty"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by jsangre on 2007-04-27
I have a 160gig desktop computer running 2000XP. Downloaded the and burned the boot CD successfully. Now, I am installing Ubuntu, and I have encountered the following problem:

My harddrive is 160gigs. 52.9 are being used by XP. I would like to reserve another 50 for future use. That leaves 56gigs for Ubuntu (more than enough I would say). I partitioned the NTFS partition that already existed from 160gigs to 100gigs. Now, I have 56gigs left for Ubuntu. I tried to partition this free space into the root and swap partitions. However, I can only make one partition from this free space; after I do, the remainder is 'unusable'. I have tried making a partition that covers the entire free space and then resizing it smaller, but I am not allowed to do this...HELP!...plus, now i have 56gigs of randomly sectioned off harddrive...yeah.

Thank you in advance. I'm new here, so please explain as if I were 2. no, seriously.
Jsangre

---

### Post by antoz on 2007-04-27
You should be able to partition this unlalocated space by using the Live cd (it has Gparted on it) do it before you start installing, 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
When using Gparted just right click the unlalocated space and create your partitions. You can only create 3 primary partitions I think but if you make an extented partition you can have multiple partitions within. Hope this helps.

---

### Post by jsangre on 2007-04-27
OK, thank you for the link. Just so I know that I got this right:

Root Partition: The large partition (30gigs+). It should be a primary extension, ext3, mounted as "/"
Swap Partition: The small partition (1gig or less). It should be a primary extension, ext3, no mount

Is that correct? As I have 56gigs to work with, will it benefit my linux experience to create a larger swap partition then suggested (256MB)?

Thank you for the help.

---

### Post by jsangre on 2007-04-27
The problem behind the symptoms: I had three primary partitions already (there were two besides the XP root; who knows what they are, but I'm not screwing with them. So when I tried to create the second linux partition, I was creating 5 primaries which is not allowed. Instead, I will create an extension partition, and put two logicals on that for linux. I will repost if this doesn't work; for now, thank you for your help.

jsangre

---

### Post by antoz on 2007-04-27
It doesn't have to be a primary partition, the file system is linux swap
To give you an idea I attach a screen shot of my partition table

---

### Post by jsangre on 2007-04-27
Actually one more thing: When I use GParted to partition, the used sections are shown in yellowish. If my new partitions do not intrude upon this used section, do I need to back-up the data? In essence, does the GParted just create partitions, or wipe the whole disk and redo it all?

jsangre

---

### Post by jsangre on 2007-04-27
Should I make an extension anyway in case I wanted to make a /home partition or fat32 partition in the future?

Can you answer the other question about data backing up to plz. thank you

---

### Post by Gina on 2007-04-27
For each drive, the limit is 4 primary partitions.  I think only one extended partition is allowed but you can partition that into any number of logical partitions.  That is what I have done on my main PC.  All the Linux/Ubuntu partitions are logical. When I wanted to upgrade to Feisty Fawn I created another logical partition to install it into - keeping Dapper on another in case I had any problems with Feisty .  I also have a separate partition for **/home**.  I now have multi-boot into Feisty, Dapper and Win XP.

As for backing up... I always recommend backing up anything wanted before altering partitions or installing OSs etc.  Either back up individual files (difficult to be sure you've got everything you want) or whole partitions.  I used **partimage** from a live CD to backup my partitions to an external HD.  (I also separately backed up /home and /root trees in just in case)

GParted will not touch any partitions it's not asked to but you have to be careful, of course.  Before confirming you want changes applied, check that you are doing what you want to do.

---

### Post by antoz on 2007-04-27
You can resize partitions with data on it without any problems, (it pays to back up though)
Once you install use "/" for ubuntu and the other one is "swap" [COLOR="Red"]just make sure they are the only ones checked to format[/COLOR]
[http://www.users.bigpond.net.au/hermanzone/p17.htm](http://www.users.bigpond.net.au/hermanzone/p17.htm)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The above links are very helpful

---

### Post by jsangre on 2007-04-27
Thank you very much mate. I appreciate all the help and GREAT links :)

jsangre

---

### Post by antoz on 2007-04-27
Glad I could help, have fun cheers,A

---

