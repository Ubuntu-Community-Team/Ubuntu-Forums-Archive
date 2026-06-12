---
title: "Dual Booting"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-02-29
I'm interested in dual booting my old laptop.  I have an AMD Athlon mobile XP 1600+ processor, 256mb RAM of which 32 mb of that is graphics memory and 30 gb hard disk.

My question is, I would like to dual boot Windows XP and Ubuntu but use Ubuntu as my primary operating system with XP there as backup if anything goes wrong with Ubuntu.  I would like 3 partitions with Ubuntu on one, my documents and files on another and XP on the third.  How much space would you advise me to give to each partition?  What is the minimum that XP would work on?

Thanks in advance for your help and advice :)

---

### Post by JawsThemeSwimming428 on 2008-02-29
It depends how big the HDD is. How much space to you have to work with?

---

### Post by Duck2006 on 2008-02-29
These links may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by housam on 2008-02-29
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.( you already have two of them , one has windows and the other for the recovery )
-I suggest to create one more primary partitions for your data and another one as extended partition which can be devided to many logical partitions.
 - the extended partition can be devided to 2 partitions : one EXT3 ( 10 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

### Post by mikeypc2006 on 2008-02-29
> **JawsThemeSwimming428 said:**
> It depends how big the HDD is. How much space to you have to work with?

I have a 30 gb HDD drive to play with.

I want to format and rebuild my PC.  So reinstall Windows and put Ubuntu on.

EDIT - I want three partitions, one with Windows, one with Ubuntu and one with all my data.

Yes I will backup all my data as I will be reinstalling Windows, so formatting the hard drive.  Should I create the three partitions when I install Windows or let Ubuntu do all that?

---

### Post by HermanAB on 2008-02-29
OK, that can do.  WinXP can run in very little disk space so if Ubuntu will be your primary system, you can allocate 10GB to Windows and 20GB to Ubuntu.

Note: INSTALL WINDOWS FIRST!
Let Windows grab the whole disk.

Before you install Ubuntu, partition the disk to give Ubuntu 20GB using Partimage and all should be well.

Hope that helps!

Herman

---

### Post by mikeypc2006 on 2008-02-29
> **HermanAB said:**
> OK, that can do.  WinXP can run in very little disk space so if Ubuntu will be your primary system, you can allocate 10GB to Windows and 20GB to Ubuntu.

Note: INSTALL WINDOWS FIRST!
Let Windows grab the whole disk.

Before you install Ubuntu, partition the disk to give Ubuntu 20GB using Partimage and all should be well.

Hope that helps!

Herman

That helps but I want a third partition for my data so that I stand less chance of data loss if either OS messes up.  How should  I format this 3rd partition so that both XP and Ubuntu can have access?

---

### Post by forrestcupp on 2008-02-29
Just make 3 10 GB partitions with the file backup drive being NTFS.  Linux does a good job at reading and writing to NTFS now, Ubuntu Gutsy does it out of the box.  You will need a small partition for swap, though.  You could probably get by with 256 megs.

you may be ok with regular Ubuntu, but you might want to look into Xubuntu since you only have 256 megs of RAM.

---

### Post by Xorg.conF on 2008-02-29
Well if you want three partitions then you can easily do it with just the windows install disk.  Obviously you first must backup all your data, then pop in the XP cd and restart your computer.  From there it will have its own partitioner, which then lets you resize or delete partitions that are presently on the disk.  So you delete everything, afterwards it should say free space ###w/e your hard disc can hold, all you do then is specify how much you want for the windows partition so let’s say 10000mb or 10gb. You install Xp and it works, so you run the live ubuntu cd, when you install that, the partitioner should show the NTFS 10gb windows partition with 20 gb of free space.  There you can do more partitions, for ubuntu and for your documents, so depending on how much data you backed up, let’s say your docs are 5gb,  You partition ubuntu with 14gb with a primary partition, another 5gb for your docs, and 1gb for swap (yes you'll end up with 4 partitions, you do need swap space.  

After you install ubuntu, your partitions should be mounted and you will be able to access them while running in ubunu.

---

### Post by regbsn on 2008-02-29
I also am restoring an old computer but I have 20G HHD (190077 available for partitions). I was planing on reformatting was wondering how to partition HHD.

Do I have a small NTFS for windows and larger NTFS partition that will be resized durung Ubuntu install?
-OR-
Do I have a Small NTFS partition for windows, a smaller one for data, and leave a large unpartitioned space for Ubuntu?

Does choice one allow me more freedom with deciding later partition sizes for data (NTFS), "/", "/ home", LINUX-SWAP.

I have already deleted my old partition and am  awaiting your suggestions.

---

### Post by Xorg.conF on 2008-02-29
regbsn if you want to resize partitions that have been formated, then look up an open a program called Gparted, its open source and it works by booting a cd or a usb.

---

