---
title: "Help a newbie! How should I do it?"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by SeaBear on 2005-09-08
Hello,

First post! Feels great to post it at "absolute Beginner Talk! :razz: ! 

I'm pretty used to work with Windows, but has really got fed up with all this cracking and looking for serials and blablablabla... 

Well, well...

I have some questions before I do the big move, and maybe some one here can help me out?

To start I’m planning on a dual boot system (newbie). 
I still want to keep two partitions with Windows (NTFS or FAT) one for the windows folder and programs and one for all my files. 
But how do I set the rest of my disk space up?
What would be the best??? I would prefer to do this only once… 
I know I read here somewhere that the swap should be in the end of the disc, no problem – how big?  
What format should I use on the boot? 
How do I do to be able to reach my files (documents photos, MP3s) from both Windows and Ubuntu? FAT16 or FAT32 doesn’t seem to work… 

And a final question (for now), maybe stupid but what the h***… I’ve done a test installation on one of the pc’s at work (busy guy!) and if I go to “computer:///” in Nautilus I cans see “Floppy Drive” “CD-ROM Drive” and “file system”. 
If I would have two disks that Ubuntu could read would I have another icon for that then? Or where does it end up?  (do I feel stupid or what!!)

I would really appreciate any help I can get! 

Thanks
/SeaBear

---

### Post by Wolki on 2005-09-08
> **SeaBear]I still want to keep two partitions with Windows (NTFS or FAT) one for the windows folder and programs and one for all my files. [/quote]

FAT is better for the data partition, since linux can read and write it said:**
> But how do I set the rest of my disk space up?

Two popular choices:
-One big Linux partition + a Swap Partition
-One Partition for system files, one for user files & data + a swap partition.

Many people (including me) like the second one best. There are of course more possibilities, but they are usually only intersting for servers.

Now, how big should these partitions be? It depends on how many programs, desktop environments etc you want to install and how big your hard disk is. I think the minimum for the system partition is 3 gigs, 5 is much better (but some may still find it's not enough), 10 is lots. If your hdd has space left and you plan on playing around a lot with different things, go for something around 10, If you're not or tight on disc space use 5. 
(If you really have lots of disk space you can go for even more, though i doubt much of it would be used ^^;;;)
Swap space, there is a calculation but I forgot ^^;; I have half a gig ram and half a gig swap space and dont have problems with that.
Simply use the rest for your Home. Minimum I'd say 500 mb, if you dont plan on saving much data there.

Use either ext3 or ReiserFS as file systems.

> How do I do to be able to reach my files (documents photos, MP3s) from both Windows and Ubuntu? FAT16 or FAT32 doesn’t seem to work… 


All FATs work. You can also read some linux file systems from windows with special drivers, iirc. But for data Fat is best, because it's the easiest.

> 
And a final question (for now), maybe stupid but what the h***… I’ve done a test installation on one of the pc’s at work (busy guy!) and if I go to “computer:///” in Nautilus I cans see “Floppy Drive” “CD-ROM Drive” and “file system”. 
If I would have two disks that Ubuntu could read would I have another icon for that then? Or where does it end up?  (do I feel stupid or what!!)


Yes, but you have to enable them. This currently requires editing a text file where partition information is stored, but the process is quite easy and well-documented on the Ubuntu wiki, for example. People here can also help you.

The next version of Ubuntu, released next month, will make this easier, but it's not really hard now. :)

---

### Post by davmac on 2005-09-08
> Yes, but you have to enable them. This currently requires editing a text file where partition information is stored, but the process is quite easy and well-documented on the Ubuntu wiki, for example. People here can also help you.

The next version of Ubuntu, released next month, will make this easier, but it's not really hard now. :)

This procedure is covered in detail in the Windows section of the Starter Guide ([http://ubuntuguide.org/#windows)](http://ubuntuguide.org/#windows)).

---

### Post by SeaBear on 2005-09-09
Thanks for you help!  :-P 

That did it! 

Installing did'nt work though... SATA discs... Can't get my computer to boot to Ubuntu, only XP... 

So I'm back to searching the forum!

---

