---
title: "Solution: Windows and Ubuntu dualboot"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by speeddemon_dk on 2005-05-11
Hello all!

I am a newbie to linux.
Every time I have tried installing Ubunto my MBR crashes.
Only if I choose the automatic setup of my partition it succeed.

But i finaly have figured it out:

First install windows (then GRUB can find it under installation)

You need to set the bootflag at your new Ubuntu partition.

Then doring the installation you choose install GRUB in the MBR


Speeddemon
Denmark

---

### Post by XDevHald on 2005-05-11
[QUOTE=speeddemon_dk]Hello all!

I am a newbie to linux.
Every time I have tried installing Ubunto my MBR crashes.
Only if I choose the automatic setup of my partition it succeed.

But i finaly have figured it out:

First install windows (then GRUB can find it under installation)

You need to set the bootflag at your new Ubuntu partition.

Then doring the installation you choose install GRUB in the MBR


Speeddemon
Denmark[/QUOTE]
 This is the kind of posts we need in here, pure basic newbie setups and knowings of how to overcome the problem by creating a solution without using any tech support to the backend.

Also this is a great way to start conversations so other newbies can learn this same technique as well, but keep a low profile of showing mostly tech support. We understand that sometimes the questions come, but please do keep those in their proper forums as recommended by the rules given in each forum, and displayed on each forum link with the description of what that forums purpose is used for.

Very well done on following the rules and showing you had an error, but created a solution for your problem, and great to see you figured it out on your own, and learned the process as you went :D

---

### Post by | MM | on 2005-05-12
I have a question, i dont really know much about partitioning.  I already have an installation of Windows XP on a single NTFS partition of my entire drive.  I have allot of uni files/music/games etc. ... so it would be a real hassle to start afresh at this point in time.

What i would like to know ... 

...  is it possible to shrink my current NTFS partition, create a new partition for ubuntu, and maintain my current WinXP installation?

Or, as another possibility;

I am tempted to buy another hard drive, just a small cheapy, intented as a backup drive for my uni work.
But could this also serve as a partition that i could install ubuntu on?

Furthermore, would i be able to send/access files from Windows to the Ubuntu partition (and vica versa)?  Or the fact that Windows is running on an NTFS partition mean this is impossible?

Any advice would be much appreciated.

Cheers 
Matt

---

### Post by Arjen on 2005-05-12
MM, while it is possible to shrink your existing NTFS partition using commercial applications like PartitionMagic I would recommend your second solution. This is mostly because I don't know exactly how good those applications work, having never used them, and because of your second question.

It is not possible to write to a NTFS partition from Linux. Well technically it's possible, but it isn't supported and the chances that you lose data is rather high. Accessing your linux partition from Windows is possible, although I can't tell you the name of an application that does this. I'm sure someone else reading your question will be able to answer that though. (And if someone happens to know a free alternative to PartitionMagic I'd like to hear about it myself.)

However, if you plan to buy a second harddisk you could divide this into a Linux partition and a FAT32 partition. This way you could use that partition to move files from Linux to a partition that can easily be accessed from Windows.

I hope this helped, and if you want a more detailed explanation of anything I said, just ask.

---

### Post by wxm505 on 2005-05-12
[QUOTE=| MM |]
...  is it possible to shrink my current NTFS partition, create a new partition for ubuntu, and maintain my current WinXP installation?

Cheers 
Matt[/QUOTE]
U can use a software called "Partition Magic"  which can manage the existing
partitions in ur machine. With this software u can create a partition with the format
Linux. Then install Ubuntu . U can have two OS .
But I must warn u that this way could lead to an unstable system.U may lost some space in ur harddisk for backing up some data of ur current system.
Anyway I followed this way , Now two systems are running very well. I seldom use windozXP.After a while u would find u needn't windows any more. hehe.
Good luck mate.

---

### Post by | MM | on 2005-05-13
[QUOTE=wxm505]U can use a software called "Partition Magic"  which can manage the existing
partitions in ur machine. With this software u can create a partition with the format
Linux. Then install Ubuntu . U can have two OS .
But I must warn u that this way could lead to an unstable system.U may lost some space in ur harddisk for backing up some data of ur current system.
Anyway I followed this way , Now two systems are running very well. I seldom use windozXP.After a while u would find u needn't windows any more. hehe.
Good luck mate.[/QUOTE]
 Ah, some good replies.
Im quite excited about the prospect of 64bit computing, just have to wait for a linux driver for my relatek AC97.  I dont wanna try WinXP64bit atm bcos of the loss of the 32bit licence.  In the meantime im really eager to try 32bit ubuntu.  Looks nice and clean, and well thought out.  Plus the development cycle seems fast, as far as OSs are concerned so i look foward to the future developments.  Very exciting all-in-all.  I just wish Valve would port Steam and Source.  :P

Thanks people.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=| MM |
I am tempted to buy another hard drive, just a small cheapy, intented as a backup drive for my uni work.
But could this also serve as a partition that i could install ubuntu on?
[/QUOTE]

Do this. Then use the instructions on the Ubuntu guide to mount the NtfS as ready only when you boot:

[www.ubuntuguide.org](www.ubuntuguide.org)

---

