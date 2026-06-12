---
title: "[SOLVED] manual partitioning required? how?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by adh2 on 2008-03-20
Hi,

I'm very very new to Ubunutu, haven't even got it installed yet. Which is the reason for me writing this post..
I wrote another post with some other questions which were solved, but then I realized that my problems weren't solved anyhow.
So this is the situation; I have the liveCD, but in the installation process things go wrong.
I get to the window where I'm supposed to "prepare disk space", and where I chose "guided -resize". But this just doesn't work, instead it wants me to "prepare partitions" manually, and shows this screen;
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
Note that this is not my actual screen, the table for me looks something like this:
/dev/sda            			size		used
/dev/sda1 	fat16 	/media/sda1 	90MB 		33MB
/dev/sda2 	ntfs 	/media/sda2 	114596MB	90000MB
/dev/sda5 	fat32 	/media/sda5 	2146MB 		1800MB
/dev/sda4 	fat32 	/media/sda4 	3234MB 		2200 MB
From my previous thread I quote hyper_ch:
"fat16?

what's on sda5 and sda4?

The problem is those are all primary partitions (I think) so you can't create anymore partitions."
I dont know what is on those partitions.. notwen said:
"It looks as if your current system may have a restore option. What kind of system do you have and do you know if it has a Windows/System Restore option? Those FAT32 and FAT16 partitions generally turn out to be partitions used in a System Restore."
This seems reasonable to me, seing how the computer has a "fast format" option, which resets the computer to what it was like when new, more or less, with the same programs being installed etc.
My computer is a Dell inspiron 6400 with xp.
So now you got the background.. any ideas? :)

---

### Post by adh2 on 2008-03-20
I would really really really appreciate some help.. just don't know what to do:confused:

---

### Post by wolfen69 on 2008-03-20
this may help [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by billgoldberg on 2008-03-20
> **adh2 said:**
> Hi,

I'm very very new to Ubunutu, haven't even got it installed yet. Which is the reason for me writing this post..
I wrote another post with some other questions which were solved, but then I realized that my problems weren't solved anyhow.
So this is the situation; I have the liveCD, but in the installation process things go wrong.
I get to the window where I'm supposed to "prepare disk space", and where I chose "guided -resize". But this just doesn't work, instead it wants me to "prepare partitions" manually, and shows this screen;
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
Note that this is not my actual screen, the table for me looks something like this:
/dev/sda            			size		used
/dev/sda1 	fat16 	/media/sda1 	90MB 		33MB
/dev/sda2 	ntfs 	/media/sda2 	114596MB	90000MB
/dev/sda5 	fat32 	/media/sda5 	2146MB 		1800MB
/dev/sda4 	fat32 	/media/sda4 	3234MB 		2200 MB
From my previous thread I quote hyper_ch:
"fat16?

what's on sda5 and sda4?

The problem is those are all primary partitions (I think) so you can't create anymore partitions."
I dont know what is on those partitions.. notwen said:
"It looks as if your current system may have a restore option. What kind of system do you have and do you know if it has a Windows/System Restore option? Those FAT32 and FAT16 partitions generally turn out to be partitions used in a System Restore."
This seems reasonable to me, seing how the computer has a "fast format" option, which resets the computer to what it was like when new, more or less, with the same programs being installed etc.
My computer is a Dell inspiron 6400 with xp.
So now you got the background.. any ideas? :)

I suggest you download the gparted live cd.

Use it to delete those unneeded partitions.
 
Merge them.

Take some space away from the windows install. And merge it together with the other merged partitions to one big partition.
Format the partition as "ext3". Then run the installer again and select the second partition to install it on.

---

### Post by adh2 on 2008-03-20
Thank you for the replies!

That guide was very extensive, gave me a better idea of how partitions work.

I have the gparted cd. When I boot from it, there's a long list of things to do, which one shall I pick?

Billgoldberg:
I'll have to ask you to explain your answer..:)
 shall I merge the FAT32 and FAT16 partitions? What partitions shall I delete?
And how do I take space away from the windows install?
Then I merge the FAT partitions with the windows partition, that is /dev/sda2 right, and format it as "ext3". And that's the one I install on?
cheers!

---

### Post by adh2 on 2008-03-20
Hmm.. do I need to create a swap partition as well?

---

### Post by wolfen69 on 2008-03-20
if you are choosing to install to an entire drive, no. it will do it automatically.

---

### Post by barbedsaber on 2008-03-20
In my (almost certainly wrong) opinion, it is best if you do all your partitioning from windows. because windows will not accidentally wipe your stuff. then when you are in the install for ubuntu, you can choose largest free space, and know that you only have 1 free partition..

DO NOT DO THIS UNTIL SOMEONE WHO KNOWS WHAT THEY ARE TALKING ABOUT (defiantly not me) CHECKS WHAT I HAVE SAID ANS CONFIRMS IT.

otherwise it will be the blind leading the blind, big time. :cool:

---

### Post by adh2 on 2008-03-21
I don't want to install ubuntu on the entire drive, but keep windows as tp create a dual-boot.

I'll wait for someone to confirm what you said, but what programs can be used to partition the disk inside windows?

---

### Post by SpongeBob SquarePants on 2008-03-21
Hi adh2,

Just a few observations. Firstly, you don't seem to have a partition big enough to install UBUNTU on. As has already been said, you'd need to merge some of those smaller partition to make room. The problem with this is, one of those smaller partitions (maybe even two of them), almost certainly holds your Windows restore data, meaning that if (or should I say when), your Windows OS needs reinstalling, if you only have a restore disk (and not an original Windows install disk), you'll be knackered. 

Really, you either need a free partition big enough to house MEPIS, or a genuine Windows disk.....not a restore disk. 

Of course, a third option would be to try resizing your NTFS partition and taking some of the free space for Linux. But be aware that it might destroy your Windows OS, necessitating a Windows restore. One thing I'm not sure about is whether the restore process would need it's original partition size or not. For example...if your original NTFS partition is say 90 GB, and you shrink it to say 45 GB, using the other 45GB for Linux, if Windows went belly up and you had to use the restore disk, would it either (a) restore everything back to default, thus restoring your NTFS partition back to 90GB's  and re-installing windows there....thus wiping out  UBUNTU, (b) not restore anything because of the change in partition size or (c) just install Windows on the available partition regardless of size?

Of course none of the options are too bad. The first option you'd be back at square one, so no harm done...apart from wasting a bit of time. The second option you could just resize your NTFS partition back to 90GB's again, and then re-try the install. And of course, the third possibility is the one that would be ideal.

With regards partitioning, after resizing your windows partition, you'll need at least two partitions....but better three. Certainly a root partition and a swap partition (the size is usually your ram plus half again...so if you have 1GB RAM then make the swap around 1.5 GB). Also recommended, but not essential, is a home partition. If you have a home partition, if you ever need to reinstall Ubuntu, it will save all your settings and private files, meaning you won't need to back them up and then restore them after boot.

You can use UBUNTU's partitioning tools to resize etc. during install.

---

### Post by adh2 on 2008-03-21
Spongebob, thanks for your reply!
It's true that I don't have a windows disk, only various restore disks.
What I was thinking was that the NTFS partition would have to be changed, in windows it says that there is 25 gb free disk space on (C), i guess that is the NTFS partition?

That's some interesting points you bring up. I have no idea what the answer is tho :)
I feel pretty convinced that I want to change to Ubuntu, but while learning the programs and making sure everything works properly, I want to have Windows installed.
So if my windows would go belly up, then that wouldn't be the end of my life, as long as ubuntu works...

So what I should do is to merge the FAT-partitions, and then shrink the NTFS, and create a 1,5 gb swap (1gb ram), and a root of some 20 gb? I think I'll wait with the home partition.
Or is it pointless to merge the FATs?

cheers!

---

### Post by adh2 on 2008-03-21
Are the FAT-partitions primary partitions, meaning that I cannot create any more primaries?
Or can I create the root as a secondary or logical?
If so, how..?
Cheers!

---

### Post by bumanie on 2008-03-21
Could you possibly post a screenshot of what gparted shows?

---

### Post by SpongeBob SquarePants on 2008-03-21
Hello again,

If there's 25 GB left on your C: partition, based on your first post, the C drive would be your NTFS drive and the one you need to shrink. I wouldn't actually shrink it by 25 GB exactly. Maybe just 20GB, leaving yourself enough space to do/install stuff in Windows. Maybe defragment windows too before resizing.

With regards your FAT partitions, I'd just leave them for now. They're pretty small, and if something goes wrong, at least you'll be able to reinstall windows again. Just in case UBUNTU doesn't work out for you. If you get on OK with UBUNTU you can always merge them later and use them for storage or swapping information/files between the two operating systems. if you plan to dump Windows at some point, then just try UBUNTU for a while, and if it works out wipe and repartition the whole lot.

If I were you I'd defrag windows, then shrink the NTFS partition by 20GB and make that whole 20GB's an extended partition. Then make two or three logical drive in that space......your root, your swap and your home (if you deem it necessary). So that would be a root of say 6GB's, a swap of 1.5GB's and the rest home......or 1.5GB's swap, and the rest as root should you decide not to go with the three partitions option.

As for how to make a logical drive, the partitioner should walk you through that. You can choose what the partition type is you create...so just create an extended partition in the empty space left by the resize, then create your logical partitions in there.  If you try to create a primary partition, it won't let you anyway. If you load up gparted/qtparted it will tell you whether the partitions on your existing drive are extended or primary. I'd imagine they'd be primary.


Bob

---

### Post by Junglizer on 2008-03-21
And to think I thought this thread was gonna be about `fdisk`

---

### Post by adh2 on 2008-03-21
bumane: I can't post a screenshot of gparted, it doesn't start properly for me.

I've tried shrinking the drive, but it doesn't work.. just get an error message.

Thinking about formatting the drive entirely, and install Ubuntu only. Then Ubuntu will take care of SWAP and I don't need to bother about all this, right?

I checked Dell's site, and at least I can order a copy of Windows, if I'll want to switch again.. or if anything  would go wrong with a dual boot.

Hm a bit tired now, will take a break from this. But I'll be back... :)

Again, thanks for the help!

---

### Post by SpongeBob SquarePants on 2008-03-21
> **adh2 said:**
> bumane: I can't post a screenshot of gparted, it doesn't start properly for me.I've tried shrinking the drive, but it doesn't work.. just get an error message.

Qparted doesn't start so you can't shrink the partition? Or it didn't start, but you got it started, and then you couldn't shrink the partition? Is your hard drive a SATA drive? I ask because for some reason I've had problems in the past with gparted, when I've had a SATA drive as my OS installation drive. When I installed my OS's to my IDE drive instead (using my SATA drive for storage), gparted worked just fine. No idea why. 

To get round the problem you could try using something like qtparted from the Linux System Rescue CD, downloadable at......

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Boot up the disk, load qtparted and then shrink your NTFS partition....create an extended partition.... and then create logical partitions as already discussed. Hit apply. Then start up the UBUNTU live CD and use your newly created partitions for installing UBUNTU on. That way you won't have to rely on gparted to do the partitioning for you.

> **adh2 said:**
> Thinking about formatting the drive entirely, and install Ubuntu only. Then Ubuntu will take care of SWAP and I don't need to bother about all this, right?

Well hopefully the installer will chose one of your smaller FAT partitions as SWAP. If it decides to use your biggest partition and make you a new SWAP partition, then if it uses gparted to partition things, you may be back at square one again....with the errors.

[QUOTE=adh2;4558415]I checked Dell's site, and at least I can order a copy of Windows, if I'll want to switch again.. or if anything  would go wrong with a dual boot.]/QUOTE]

Well looking on the positive side, your system restore disk might work just fine without the restore partitions. It might just take longer. So hopefully you won't have to shell out for a new Windows disk. If you're buying Vista it can be an expensive affair.

---

### Post by adh2 on 2008-03-21
Well, funny how events turn out sometimes :)
Apparently, when I last tried to get through with GParted, I had in fact shrunk the main partition, and had 13 gb free.. And with those 13 gb i managed to create a swap and a root, and now I'm writing this from my newly installed UBUNTU!!!!! WHich feels pretty **great**!
Only one more thing to do; check if windows is still there.. hehe :D
So again, thank you **so** much! Would never been able to do this without you :)
Again, I'll be back...   with more questions :) But on another topic then.
Cheers!

---

### Post by adh2 on 2008-03-21
> **SpongeBob SquarePants said:**
> Qparted doesn't start so you can't shrink the partition? Or it didn't start, but you got it started, and then you couldn't shrink the partition? Is your hard drive a SATA drive? 

 If you're buying Vista it can be an expensive affair.

GParted did start, and I tried different things, but I couldn't get to the step from which I've seen pictures.. and I honestly don't know how I did, just that I was about to do something I thought would format the drive or such, and aborted it, and then now there was 13 gb free.. windows seems to have survived that at least.. :)

I shouldn't have to pay for vista then, just get a new install disk I think.. anyhow, shouldn't need that now I hope :D

---

### Post by bumanie on 2008-03-21
Is it possible to get a gparted screenshot now (as it is working) with a clear explanation of how you want your drive to be partitioned.

---

### Post by adh2 on 2008-03-21
Not everything in GParted works.. so, no, I can't really post a screen-shot..
My aim was to get Ubuntu running next to Windows, which it does.It might not be the optimal solution but it works,.. so I'm perfectly satisfied :)
Thank you for you help!

---

### Post by SpongeBob SquarePants on 2008-03-21
Oh well, all's well that ends well...as they say. Good news you're set up. Well done :)

---

