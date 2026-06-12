---
title: "Quick partition question"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by kizmet_x on 2007-12-29
Let me start by saying that I am going to finally move to Linux after about 10 years of wanting to learn it and try it out. I will be dual booting with Windows xp, and I have ordered a new hard drive that will be my seperate, dedicated Linux hard drive.

The question I am going to ask you guys is I read a guide to dual booting. Dont remember where. But the author recommended that in addition to the main ext3 partition and the swap partition, that you setup a fat32 partition to share between windows and Linux. The more I think about this, the more it seems like this is the way to go. But would this really be necessary? On the Ubuntu Live CD, I can access my NTFS partitions and access files from them. I am just guessing you can do this in the actual Ubuntu as well.

And say I wanted to make a fat32 partition. I am guessing I would have to set this up in Windows and format the drive in Windows. I am not familiar with Linux, so this seems like the way to do it.

Let me just thank you guys ahead of time for helping a noob like me out :)

---

### Post by overdrank on 2007-12-29
> **kizmet_x said:**
> Let me start by saying that I am going to finally move to Linux after about 10 years of wanting to learn it and try it out. I will be dual booting with Windows xp, and I have ordered a new hard drive that will be my seperate, dedicated Linux hard drive.

The question I am going to ask you guys is I read a guide to dual booting. Dont remember where. But the author recommended that in addition to the main ext3 partition and the swap partition, that you setup a fat32 partition to share between windows and Linux. The more I think about this, the more it seems like this is the way to go. But would this really be necessary? On the Ubuntu Live CD, I can access my NTFS partitions and access files from them. I am just guessing you can do this in the actual Ubuntu as well.

And say I wanted to make a fat32 partition. I am guessing I would have to set this up in Windows and format the drive in Windows. I am not familiar with Linux, so this seems like the way to do it.

Let me just thank you guys ahead of time for helping a noob like me out :)

Hi and yea some say that is a good way to share the files and either NTFS or fat32 would work. And it setting up that partition in windows is more comfortable then by all means. It does make it easier to back up your data on that partition if you have to reinstall either OS. Good luck!

---

### Post by Pogeymanz on 2007-12-29
You can access your Windows data from Ubuntu, but not vice-versa. 

You can still copy files from Ubuntu to Windows too; that's what I do. But I don't have a lot of hard drive space to spare. 

I personally think it's a waste to make a whole seperate storage partition, unless you plan on using it to back stuff up for reinstalling either OS, like the above poster said.

---

### Post by twin_57103 on 2007-12-29
Ubuntu can natively read NTFS, but not write to it.  You can easily implement NTFS read-write (see [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")).  The NTFS write support is relatively new, and has historically been less reliable.  However, both systems can read fat32 reliably.  This is why a lot of people favor a fat32 partition for data.  My data partition is NTFS and I've never had any trouble with it.

If you're going to be sharing common files (emails, etc.), be sure to allot plenty of space on your data partition, whichever file system you choose.  I like having a separate partition for data because Windows won't even be able to see the ext3 drive, much less write to it.  I prefer having a go-between rather than working directly to my Windows partition from Linux.

Hope that helps!

---

