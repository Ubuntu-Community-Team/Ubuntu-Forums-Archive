---
title: "Create NTFS partition for Windows?"
date: 2012-08-06
forum: Any Other OS
---

### Post by Krayzieness on 2012-08-06
I do apologise if you find this post in the wrong area or what not. But I have dual boot problem. Here goes. Ubuntu 11.04 is my primary OS. Installed on a 40 gig drivewith 12 gigs free space and I want to install win 7 to that free space. Majority of my research has suggested formating the drive and nonsense. I would prefer to svoid this. Ive tried gparted but cant unmount drive. All I want to do is partition the 12 gigs for win 7 install. Pls help!

---

### Post by Krayzieness on 2012-08-06
I do apologise if you find this post in the wrong area or what not. But I have dual boot problem. Here goes. Ubuntu 11.04 is my primary OS. Installed on a 40 gig drivewith 12 gigs free space and I want to install win 7 to that free space. Majority of my research has suggested formating the drive and nonsense. I would prefer to svoid this. Ive tried gparted but cant unmount drive. All I want to do is partition the 12 gigs for win 7 install. Pls help!

---

### Post by oldfred on 2012-08-06
Moved to Other OS as it is a Windows question.

You cannot use your install to use gparted as partitions are mounted. You can use gparted from LiveCD but still may have to click on swap and right click swap off as liveCDs usually mount swap if found to speed things up a bit.

Can you install Windows 7 in only 12GB? The smallest suggestion I have seen is 20GB with 30 usually suggested. But sometimes it may fit in less?

Windows needs primary partition (sda1 thru sda4) formated NTFS with the boot flag to install. Gparted may create the XP version of a NTFS partition. Some have said it works others said they had to reformat it again from the Windows installer.

---

### Post by Mr.Plex on 2012-08-07
Windows is kind of a best when it comes to installing it post-ubuntu.  If you install win7 it will remove grub and redo the master boot record. Which is hell to describe how to fix (just involves booting into ubuntu live disc and removing MBR and replacing it with grub(legacy/2).  But I will post this tutorial when I get home as it was recently featured in a linux pro magazine I buy in a very logical way.

---

### Post by Mr.Plex on 2012-08-07
> **oldfred said:**
> 
Can you install Windows 7 in only 12GB? The smallest suggestion I have seen is 20GB with 30 usually suggested. But sometimes it may fit in less?


Great point. Maybe you could allocate another 15 gigs to win7 partition by booting live ubuntu cd and using gparted to shrink your primary partition down a notch.

---

### Post by Aquanet on 2012-08-11
40GB is too small for dual boot, in my opinion, especially if you're installing Windows which is pretty bloated.

I think the ideal setup here is to have only Windows on the whole HDD, and then just use Ubuntu Live with Persistence from a usb stick.

---

