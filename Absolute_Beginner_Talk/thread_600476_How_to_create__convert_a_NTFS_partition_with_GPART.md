---
title: "How to create / convert a NTFS partition with GPARTED (URGENT!!)"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-11-02
I bough a new external drive.
This drive doesn't have any partition so, I had to create a new partition with gparted.
I must create a NTFS file partition but I can't create it with gparted.

I have NTFS 3G installed and enabled but I still can't create a NTFS partition. I had to create a FAT32 but this doesn't work for me cuz I need to copy files bigger than 6 GB each one. I can't use EXT3 cuz is for a windows pc.

The question is...
Can I create a NTFS partition in Ubuntu? There is some easy way to do it?? Is really urgent, so, I will really appreciate if someone can help me.

Thank you in advance.

---

### Post by taurus on 2007-11-02
What do you mean you can't use gparted to convert that harddrive from fat32 to ntfs?  Do you have it mount right now?  If you do, you need to unmount it first before you can format it to ntfs.  Otherwise, post the screenshot of gparted.

---

### Post by SOULRiDER on 2007-11-02
Im not too sure of gParted can create NTFS partitions. One thing you could do is create a FAT32 partition so windows can see it and reformat it in windows as NTFS.

---

### Post by Kosimo on 2007-11-02
Using gparted there is an option to create or convert NTFS partitions but the option is uncheckable, so, I can't use it. On the other hand, I can create and convert any FAT16/32 partition .

What I'm trying to understand is why the option to create NTFS partitions is uncheckable.  Cuz as I said I installed the NTFS 3G tool and the support for NTFS is enabled already.  By the way in gutsy NTFS should be enabled by default really??

I can't use windows because I only have Ubuntu in this PC.  I really don't want to depend everytime to go to windows in order to make things. I would like to do almost everything inside Ubuntu. 
I think I should be able to create a simple NTFS partition...  Come on, help!!! :(

---

### Post by Orion2014 on 2007-11-02
I say this all the time and I cant stress it enough, you really need to burn GParted to a bootable disk and boot from it, that way you get the most from the software.

---

### Post by Siddhartha Naik on 2007-11-02
Hi...you can't create an ntfs partition using gparted...download the free and open source image of "parted magic",burn it into a cd,boot it by configuring your dvd/cd rom drive as first boot device.. parted magic is a gui based partition suite..jus try..let me know mate..all the best :-)

---

### Post by Kosimo on 2007-11-02
> **Siddhartha Naik said:**
> Hi...you can't create an ntfs partition using gparted...download the free and open source image of "parted magic",burn it into a cd,boot it by configuring your dvd/cd rom drive as first boot device.. parted magic is a gui based partition suite..jus try..let me know mate..all the best :-)

Thank you so much for your help.

Anyway, I don't have any blank CD/DVD to burn... 
I had to do it in the most bizarre way... Open VMWARE, start my Windows XP virtual, attach my HD to the USB port and allow the Virtual Machine to access to the drive.
Once in windows with one click I formated the partition to a NTFS file type.


Shame...  

Anyway problem solved.

Thank you guys.

---

### Post by hornetcoach on 2007-12-17
I know this is an old post, but figured I'd add what I did to make Gparted work.
-Used Synaptic manager to download/install Gparted.
-Discovered it wouldn't do NTFS...read some documentation at the Gparted website
-Used Synaptic manager to download/install NTFSprogs
-Restarted Gparted and it resized and formated NTFS with zero problems.
I haven't used any other Linux partition managers, but Gparted was about as straightforward and easy to use as I could imagine.  OBTW...I first tried to resize the partition using XP and Partition Magic...it crashed and corrupted the XP partition.
I think I'm pretty much an Ubuntu convert at this point.

Thanks to all who monitor this forum - I have probably referenced it over 100 times since I found Ubuntu.

---

### Post by jako91 on 2008-01-18
> **hornetcoach said:**
> I know this is an old post, but figured I'd add what I did to make Gparted work.
-Used Synaptic manager to download/install Gparted.
-Discovered it wouldn't do NTFS...read some documentation at the Gparted website
-Used Synaptic manager to download/install NTFSprogs
-Restarted Gparted and it resized and formated NTFS with zero problems.
I haven't used any other Linux partition managers, but Gparted was about as straightforward and easy to use as I could imagine.  OBTW...I first tried to resize the partition using XP and Partition Magic...it crashed and corrupted the XP partition.
I think I'm pretty much an Ubuntu convert at this point.

Thanks to all who monitor this forum - I have probably referenced it over 100 times since I found Ubuntu.


Thank you, worked a treat!

---

### Post by ocr14a on 2008-01-24
> **hornetcoach said:**
> I know this is an old post, but figured I'd add what I did to make Gparted work.
-Used Synaptic manager to download/install Gparted.
-Discovered it wouldn't do NTFS...read some documentation at the Gparted website
-Used Synaptic manager to download/install NTFSprogs
-Restarted Gparted and it resized and formated NTFS with zero problems.
I haven't used any other Linux partition managers, but Gparted was about as straightforward and easy to use as I could imagine.  OBTW...I first tried to resize the partition using XP and Partition Magic...it crashed and corrupted the XP partition.
I think I'm pretty much an Ubuntu convert at this point.

Thanks to all who monitor this forum - I have probably referenced it over 100 times since I found Ubuntu.

Dude, this was so easy. Why do you suppose they didn't just make this step part of the install for Gparted? 

Oh...thanks a lot, by the way. 
This is very cool to know. I made the changes you pointed out and it works...immediately. 

:guitar:

---

### Post by stchman on 2008-01-24
> **Kosimo said:**
> I bough a new external drive.
This drive doesn't have any partition so, I had to create a new partition with gparted.
I must create a NTFS file partition but I can't create it with gparted.

I have NTFS 3G installed and enabled but I still can't create a NTFS partition. I had to create a FAT32 but this doesn't work for me cuz I need to copy files bigger than 6 GB each one. I can't use EXT3 cuz is for a windows pc.

The question is...
Can I create a NTFS partition in Ubuntu? There is some easy way to do it?? Is really urgent, so, I will really appreciate if someone can help me.

Thank you in advance.

Use the gparted on the LiveCD.  You can create NTFS partitions there.

---

