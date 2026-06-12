---
title: "New Computer ubuntu questions"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by lotus.monster on 2007-01-04
So I have just ordered a shiny new computer much bigger stronger faster than my current dinosaur and am excited about running ubuntu on it, but have a few questions:

1. I think Ubuntu can do everything that I would like it to EXCEPT write to my iPod and play Civilization IV (yes I am addicted).  If I could do those two things, I wouldn't need windows at all.  Is that possible?  (from what I have read so far, wine is not yet equipped to handle those programs)

2. I will probably install XP  Pro in a dual platform primarily for the aforementioned compatibility.  Will it cause me great headaches if I do not set up the dual platform when I first get the machine?

3.  Some people online say use NTFS and others say use FAT - can someone explain the pros and cons of these two formatting systems?

4. Also, in partitioning, I notice many people split their hard drives in half. I don't understand why?  why wouldn't they want to access files from both systems?  

I think I would prefer to have the vast majority shared by both OS's.  I have 320 GB hard disk, 2 GB RAM and 2.4 ghz Dual Core Processor. Can someone recommend the size of my partitions?

I apologize for the length of my questions.  I am just getting confused by all the information out there.

---

### Post by riven0 on 2007-01-04
> **lotus.monster said:**
> So I have just ordered a shiny new computer much bigger stronger faster than my current dinosaur and am excited about running ubuntu on it, but have a few questions:

1. I think Ubuntu can do everything that I would like it to EXCEPT write to my iPod and play Civilization IV (yes I am addicted).  If I could do those two things, I wouldn't need windows at all.  Is that possible?  (from what I have read so far, wine is not yet equipped to handle those programs) 

It's quite easy to write to an iPod on Ubuntu, you just need the correct app. I recommend GTKPod, since that's what I use, but I've heard Yamipod, Banshee and Amarok are also good.

> 2. I will probably install XP  Pro in a dual platform primarily for the aforementioned compatibility.  Will it cause me great headaches if I do not set up the dual platform when I first get the machine?

If you're going to install XP, install it *FIRST*! This is very important, because otherwise XP will mess up the Linux grub menu and you'll have to repair it, which can be a pain.

> 3.  Some people online say use NTFS and others say use FAT - can someone explain the pros and cons of these two formatting systems?

The difference between the FAT and NTFS is that Linux is able to read and write to a FAT, (FAT32), filesystem out-of-the-box. You'll need a third party app to be able to read and write to an NTFS partition. And it may be buggy, too; I don't know, I haven't tried it.

As far as partitioning and stuff, I'll leave that to the professionals, since I haven't done it in so long.

---

### Post by punx45 on 2007-01-04
check out [http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php") its a good guide written with the XP dual booter in mind.   has some good info on partitioning, and stuff.

---

### Post by jpeddicord on 2007-01-04
> **lotus.monster said:**
> 1. I think Ubuntu can do everything that I would like it to EXCEPT write to my iPod and play Civilization IV (yes I am addicted).  If I could do those two things, I wouldn't need windows at all.  Is that possible?  (from what I have read so far, wine is not yet equipped to handle those programs)I have an iPod that seems to work find in Ubuntu Edgy. It was all plug and play here.> 
2. I will probably install XP  Pro in a dual platform primarily for the aforementioned compatibility.  Will it cause me great headaches if I do not set up the dual platform when I first get the machine?You must install XP before you install Ubuntu. If you do not, Windows will overwrite the boot record, preventing you from booting Ubuntu. If you do accidentally install Windows overtop of Ubuntu, then there are some recovery disks on the internet that may help you.> 
3.  Some people online say use NTFS and others say use FAT - can someone explain the pros and cons of these two formatting systems?If you use Linux - don't use either. NTFS and FAT are both Microsoft filesystems. Linux systems generally use Ext3, or sometimes ReiserFS. I recommend whatever the installer chooses for you.> 
4. Also, in partitioning, I notice many people split their hard drives in half. I don't understand why?  why wouldn't they want to access files from both systems?Partitioning is required to install more than one OS. You can still easily access both Windows and Ubuntu files from inside Ubuntu.> 

I think I would prefer to have the vast majority shared by both OS's.  I have 320 GB hard disk, 2 GB RAM and 2.4 ghz Dual Core Processor. Can someone recommend the size of my partitions?I recommend at least 50GB for Ubuntu if your HD is that big.

Good luck with Ubuntu!

Jacob

---

### Post by srirammurali on 2007-01-04
> **riven0 said:**
> 
The difference between the FAT and NTFS is that Linux is able to read and write to a FAT, (FAT32), filesystem out-of-the-box. You'll need a third party app to be able to read and write to an NTFS partition. And it may be buggy, too; I don't know, I haven't tried it.

As far as partitioning and stuff, I'll leave that to the professionals, since I haven't done it in so long.

[FONT="Tahoma"]well i haven't had any problems whatsoever so far dude.. either writing from ext to ntfs or ntfs to ext... as most ppl have been saying "**ntfs drivers might be buggy**", the truth is quite contrary.. **_its quite stable_**... well its ur take anyways..
[/FONT]

---

### Post by riven0 on 2007-01-04
> **srirammurali said:**
> [FONT="Tahoma"]well i haven't had any problems whatsoever so far dude.. either writing from ext to ntfs or ntfs to ext... as most ppl have been saying "**ntfs drivers might be buggy**", the truth is quite contrary.. **_its quite stable_**... well its ur take anyways..
[/FONT]

True, but for new users, it's always good to be a little cautious... ;)

---

### Post by IYY on 2007-01-04
> 1. I think Ubuntu can do everything that I would like it to EXCEPT write to my iPod and play Civilization IV (yes I am addicted). If I could do those two things, I wouldn't need windows at all. Is that possible? (from what I have read so far, wine is not yet equipped to handle those programs)

Ubuntu has good iPod support. There are several applications that can be used for this purpose, like gtkPod and Banshee. 

You could try to run Civ IV with Wine, though I am not sure how good the results will be. Here is the appropriate page: [http://appdb.winehq.org/appview.php?iVersionId=4036](http://appdb.winehq.org/appview.php?iVersionId=4036)

Of course, there is also FreeCiv, which is in the Ubuntu repositories and is very similar to Civilization.

> 2. I will probably install XP Pro in a dual platform primarily for the aforementioned compatibility. Will it cause me great headaches if I do not set up the dual platform when I first get the machine?

You should install Windows first, and then Ubuntu. This is because Windows overwrites the boot manager and "hides" the other operating systems from you, so you will not be able to boot into them.
> 
3. Some people online say use NTFS and others say use FAT - can someone explain the pros and cons of these two formatting systems?

There is no doubt about it; NTFS is the better file system for Windows. However, when mounted in Ubuntu, NTFS will be read-only (write support is possible, but can be risky). FAT has a limit on the maximum size of a file, so if you plan to store big files on the partition, you can't use FAT. 

A good option is to install Ubuntu on its default ext3 partition, and then download software that will enable Windows to read it.

> 4. Also, in partitioning, I notice many people split their hard drives in half. I don't understand why? why wouldn't they want to access files from both systems?

They can split in half and still have access to the files from both systems. Windows can mount ext3, and Ubuntu can mount NTFS (though only for read-only).

---

### Post by lotus.monster on 2007-01-05
WOW.  Thank you all for the advice.  I have follow up questions

1. Does anyone anticipate problems with running ubuntu and vista in a dual platform?  Will the FS drive program work on Vista to make it read ext2 hard discs?

2. Can ubuntu re-partition a hard drive if windows has been installed with its default settings?

3. I think it might make the most sense to wait until vista has been installed to then add ubuntu, but that might take a month or so.  do you agree?

Thanks again for all the help, you guys are amazing!

---

