---
title: "Partition resize reliability"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by wwbdd on 2005-12-17
I have a 60 gb hard drive with a 60 gb NTFS partition on it.  I want to dual boot the system so I need to resize the partition to make a partition for ubuntu.  I have read that the ubuntu install cd can resize the partition during the installation process but I dont know how reliable that program.  I've read several warnings that your data should be backed up before you run it and that you should defrag your drive neither of which are very reassuring as to the reliability of the resize partition program.  I'm hesitant to install ubuntu on this machine because I dont want to have to go through the windows installation process again.  Can I trust the resize partition method to keep all of my windows stuff safe?

edit: of the 60 gb available now I am only using 10 gb of it.

---

### Post by joshuapurcell on 2005-12-17
I'm not sure what resize program the Ubuntu installation uses, but it is never a good idea to resize your partitions without a backup of your data first. The thing is that just because you are only using 10GB of the 60GB allocated, you can't be sure that none of that data is in the portion you would be taking from the partition. That's why it's a good idea to defragment your hard drive before trying to resize the partition. I personally wouldn't worry about having problems with the resize if I were only using 10 out of 60 GBs, and I probably wouldn't even take a full backup just because I don't keep anything important on my computer that I don't already have somewhere else. If you did the same, the only thing you would be out of is time if it turns out the resize messes up your Windows partition.

---

### Post by stuporglue on 2005-12-17
I've used the resizer several times with success. I've never had a failure yet. 

That said, yes, you really need to back up. I've had friends using Partition Magic who've lost data when it died. Causes other than the resizer can cause problems too...like if someone trips over the power cord, or whatever. 

In Windows you should delete anything you don't need, then defrag. It will clump all the data closer together and reduce chances of bad stuff happening. 

The installer doesn't have a progress bar for the resizer, don't worrry it's not frozen! It probaly won't take too long since you've got a lot of free space, but you really really don't want to power it off during the resize. 

The first time you boot into Windows after resizing, it will want to do a file system check. This is normal, as it realizes that the partition isn't how it left it.

---

### Post by az on 2005-12-17
The partitioner is very reliable.


Very very reliable.

It will not do anything if it thinks there is a chance it cannot do it.

Backup your important data.

---

### Post by aysiu on 2005-12-17
[QUOTE=azz]
Backup your important data.[/QUOTE] I agree. 90% of the time repartitioning does no damage to your data (in fact, for my computer, it's been 100%, and I've done *a lot* of repartitioning), but you've got to anticipate the possible arrival of that 10% of the time.

Don't ride a motorcycle on the highway without a helmet.
Don't repartition without backing up your data.

---

### Post by earobinson on 2005-12-17
Never failed for me..... But if its important always back up. But if its important it should be backed up anyways HD's die all the time

---

### Post by wwbdd on 2005-12-20
thanks everyone for your help.  I'll install ubuntu this weekend and hope for the best.  thanks again.

---

### Post by az on 2005-12-20
[QUOTE=aysiu]I agree. 90% of the time repartitioning does no damage to your data .[/QUOTE]

If the failure rate was anything greater than 0.0001 per cent, we would not be here.


Probably the vast majority of the forum members have dual-booted at least once in their life.  I cannot think that 6000 people out of the 60 000 are here after parted ate their data.

---

### Post by aysiu on 2005-12-20
[QUOTE=azz]If the failure rate was anything greater than 0.0001 per cent, we would not be here.


Probably the vast majority of the forum members have dual-booted at least once in their life.  I cannot think that 6000 people out of the 60 000 are here after parted ate their data.[/QUOTE] You're right. It's probably closer to 1 out of every 60,000 times. I just picked 90% because it sounded high, but it's probably even higher a success rate than that.

For me, personally, it's been 100%.

---

### Post by Herman on 2005-12-20
I've had a 100% success rate, and I've only got one of those old PC Chips 'Book PCs for an experimental computer. I use it for experiments with the installer and partitioner it quite a lot. The installer and partitioner have never let me down.
I suspect that there might be other factors involved in some cases when people do have a problem, (which would be rare, but can happen with any partitioner).
For example, was a UPS being used or not when the problem occured? Where I live we get power fluctuations often.  A slight electrical or power supply problem could be the cause of the trouble sometimes, but the partitioner might get the blame if someone happened to be using it at the time.
(Come to think of it, I forgot to add that to my website, a few people might not know to use a UPS unless they are reminded or informed).
It would be interesting to have an idea what the real statistics might be for all of the things people do when they are installing.
It would be nice to know how many get away with using old faulty hardware and hard drives too, compared with the number installing on brand new computers fresh from the factory. (Herman)

---

### Post by anil_robo on 2005-12-22
I had a  bad experience with partition magic software when I used it from windows to resize my partitions. I thought I had only one partition in my dell laptop (as shown by windows explorer). But partition magic showed me two hidden partitions - created by Dell to contain backup utilities etc.

I ordered partition magic to create a fourth partition for Linux (two dell hidden partitions, third windows original partition, and a new linux partition).

It said it needed to restart the system, and upon restart, it said "can't create more primary partitions. Error".

All my data was gone! Fortunately the only thing I needed was my school research proposal, which I always keep on my webspace.

I installed Ubuntu on a 7GB partition with 1GB swap, thinking that I'd just try it out. But now I know I want to keep it. So I need to resize the partition. Probably I'll probably let Linux partition eat up windows XP partition (freeing up another 10GB). I'll try that in a few moments from now, after backing up all my data. I'll use Ubuntu breezy install CD to see how far I can go. And I'll post the results here!

---

### Post by anil_robo on 2005-12-22
Ubuntu Breezy partition resizing failed for me.
Here is my experience, if anyone is interested: [http://www.ubuntuforums.org/showthread.php?p=597926#post597926](http://www.ubuntuforums.org/showthread.php?p=597926#post597926)

---

