---
title: "MacbookPro w/Dapper and an External HD"
date: 2007-06-29
forum: Apple Intel Users
---

### Post by makaira on 2007-06-29
Here's the idea: I would like to instal ubuntu on a small (10GB) partition on the internal HD and use it to control the external harddrive (Which, of course, Mac OS X can also do). Here are my questions:

(1) If I format the external harddrive to a file system that OS X and Dapper both like, will iTunes on my OS X partition be able to access the music on the external harddrive without a problem? Likewise, will Dapper be able to do the same? Which format is best?

(2) Can I do all of this without interfering with the data currently stored on the internal HD?

(3) For general use applications, will 10GB be enough? I would like to keep the Dapper partition as small as possible without needing to expand it later. The idea is, of course, that I would use the external to store most of the data.

(4) Just for fun: is it completely rediculous to attempt to install Dapper on the external HD and just keep the internal the way it is (using rEFIt/bootcamp to do a dual boot)?

Thanks.

---

### Post by cyberdork33 on 2007-06-29
> **makaira said:**
> Here's the idea: I would like to instal ubuntu on a small (10GB) partition on the internal HD and use it to control the external harddrive (Which, of course, Mac OS X can also do). Here are my questions:

(1) If I format the external harddrive to a file system that OS X and Dapper both like, will iTunes on my OS X partition be able to access the music on the external harddrive without a problem? Likewise, will Dapper be able to do the same? Which format is best?
Yes. I access iTunes music over a network share (samba) at the moment. iTunes will crash if the drive is not available and you try to use it, but other than that it works fine. FAT32 is probably the most compatible filesystem, but you can mount ext2/3 partitions in OSX (ext3 is the default for Ubuntu) conversely, you can also mount hfs+ partitions in Ubuntu (the default for OSX).

> **makaira said:**
> (2) Can I do all of this without interfering with the data currently stored on the internal HD?
you are going to have to expound on that question a bit... If you are asking if you will have to wipe your Mac's hard drive to install Ubuntu, then no.

> **makaira said:**
> (3) For general use applications, will 10GB be enough? I would like to keep the Dapper partition as small as possible without needing to expand it later. The idea is, of course, that I would use the external to store most of the data.
Yea, that should be ok unless you are planning to install a lot of applications. I currently am using about 4.5 GB on my install and that includes a bunch of extra packages, plus some dev libraries and source code. If you are worried about maxing it out, make it 15 or 20.

> **makaira said:**
> (4) Just for fun: is it completely rediculous to attempt to install Dapper on the external HD and just keep the internal the way it is (using rEFIt/bootcamp to do a dual boot)?

Many people have attempted this (including myself) and had some trouble with it. I don't know if it works any better than when I last tried it. You might want to search around a bit. You can always try it, as you can just wipe the drive if it won't boot.

---

### Post by ronocdh on 2007-06-30
I suggest using nonjournaled HFS for the external drive. You can use Disk Utility in OS X to disable journaling, and presto, your drive is now able to be read and written to by Ubuntu.

I think 10GB is *plenty* for Ubuntu, given that you'll be keeping your media on your external drive.

---

