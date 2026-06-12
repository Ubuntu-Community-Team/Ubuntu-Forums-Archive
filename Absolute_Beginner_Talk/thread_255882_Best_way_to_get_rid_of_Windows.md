---
title: "Best way to get rid of Windows"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Boomfelled on 2006-09-12
Hello,

Im using an old laptop running windows 2000.

Id like to clean this OS from my machine before installing Xubuntu.

Can anyone advise on the best way to do this, for example, would a complete reformat be the best way? And if so can anyone point to any tutorials regarding partioning in relation to Ubuntu.

Many thanks

---

### Post by xyz on 2006-09-12
Hi-
Check this here:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Not sure this is absolutely necessary but when I did what you want to do, I also ran a "total wipe" of my HD using, for instance UltimateBootCD.

---

### Post by arsadogi on 2006-09-12
Hi

If you want to get rid of your windows 2000 completely you can simply make a boot diskette from your windows.restart your pc boot from floppy (check your bios for boot priority so first floppy then hard disk) then run fdisk command from dos.From here you can delete the whole partition(s)[COLOR="Red"]WARNING:if you do so you'l lose all your data so backup[/COLOR].Next you don't have to format.live your hard disk in unpartitioned space condition.Then boot from your bootable ubuntu install cd.ubuntu will handle the partitioning and format.

---

### Post by catlett on 2006-09-12
You do not have to do anything besides boot to the xubuntu install cd. The installer has a partitioner. It will reformat the drive and make new partitions. Just select the option 'use entire disk for install'. The process will remove windows.
If you still want to reformat and remove windows before you install xubuntu, another simple way is to download and burn the iso to disk of Gparted Live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)  It is a pretty straight forward interface. Just delete the existing partition or partitions and then make a new partition. Make the new partition an ext3 primary partition. Then boot to your Xubuntu cd and let it use the entire drive.

---

### Post by stig on 2006-09-12
> **xyz said:**
> Hi-
Check this here:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I've just used this guide to partition a second disk and to make a separate Home partition (which is very useful!) and I have little experience with computers and software and have never partitioned before.

The only problem was due to my own mistake. Fitting the hard disk and doing the partitioning went OK but when I used the commands to move my home partiton to the new disk I wrote in "hdb" when it should have been "hdb1". Had to do a recovery and repeat it.

The guide uses the Ubuntu CD as a Live CD and the gparted software (which was already installed on my CD). I found gparted very friendly!

---

### Post by xyz on 2006-09-12
I posted this link mostly because I learned a lot there. It's not the only one: for instance, click on some of the links **catlett** has in his signature. These great HowTos help me to understand how it works partitions is one among a lot of other stuff.

The way the Ubuntu's install CD comes these days almost does everything automatically  which is certainly a good thing but it didn't help me understand how it works. And I like that.

I also used UltimateBoot CD at the time because I didn't know anything about it. I found great tools on there and ,again, learned stuff.

I wiped off my entire HD  1. to see how it works  2. to make sure Windows wasn't there anymore which was a thing I needed only "in my head"...totally ridiculous.

I also tried gpartedBootCD, great tool, too...anyway, to make a (too) long story short, doing it various ways led me to a better overall understanding.

Sorry about that...didn't mean to bother you with so much writing!!!

---

