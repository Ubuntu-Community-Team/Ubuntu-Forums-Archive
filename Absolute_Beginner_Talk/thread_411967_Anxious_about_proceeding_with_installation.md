---
title: "Anxious about proceeding with installation"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by jackson_philip on 2007-04-17
I run a hotel business and use Windows XP for all my business. I am interested in eventually migrating to Linux. I have made a ubuntu boot-disc with the file (desktop) from the ubuntu site.

I would like to install it on my HD and be able to dual boot, but I am terrified about losing vital data during a partition. I don't quite understand how partitions work, but I am running a Dell machine with 500GB of HD. I think it is configured as two 250GB drives using an Intel Array (I hope this is making sense).

Can anyone assure me that I can 1) achieve a partition safely and 2) not lose any data, 3) be able to access files from either partition and, 4) can anyone tell me how to do it?

I would be very grateful for any assistance (preferably an idiot's guide) from anyone in the know.

Thanks,

Phil J.

---

### Post by Swab on 2007-04-17
I would seriously urge you to backup your data before attempting an install.   Things can and do go wrong.

---

### Post by earobinson on 2007-04-17
you should have your data backed up at all times (not just when your upgrading or installing an os) computers fail all the time for no reason.

---

### Post by Seisen on 2007-04-17
If one of the 2 250 GB hard drives has free space on it when you install Ubuntu select the option that says use free space and won't write over Windows.

---

### Post by shae on 2007-04-17
I have a feeling you may be running a RAID array from your description.  You should proceed with EXTREME CAUTION if you are not sure what you are doing and have critical files on the system.  I would recommend backing up all of the data onto DVDs as well as an online backup system to ensure that your mission critical data will remain safe not just because you are installing an operating system but also because computers fail all the time, as aforementioned.

If your computer has the HDs in a RAID array, I am not sure how to tell you to move forward with your change.  I am not lucky enough to have had one.  (Although I might make a foray into it as I set up a file server this summer for private use.)

Several important things should be considered if you want to make the switch with your hotel business.  First you need to make sure any special software that you need to run your business has either a Linux version, a open source alternative, or can run reliably under wine.  What I would suggest is to first set ubuntu up on a non-mission-critical machine.  Then try out the appropriate programs to see if Linux and Ubuntu are your future solution.  

Partitioning is always a tricky thing.  Especially resizing partitions.  The scary truth is sometimes it fails and sometimes the data is not recoverable.  But in terms of access, you can gain ext3 (Ubuntu's default file system) Read/Write access with drivers from the web as well as gain FAT32 Read/Write support in Ubuntu by default.  However, NTFS by default is read-only.  Drivers can be installed to gain Read/Write support, but they are still experimental.  

I think before you should proceed you should consider what I mentioned as well as better understand the internals of your machine ( i.e. is it RAID or JOBD? )  

[A Little More about What a Partition is]("http://www.tech-faq.com/hard-disk-partition.shtml")

[What RAID is]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks")

[What JOBD is as well as other RAID levels]("http://en.wikipedia.org/wiki/Standard_RAID_levels")

I would love to help you in your move from Windows to Linux, and I hope what I have said helps.

---

### Post by jackson_philip on 2007-04-20
Thanks for all the help. Sorry I haven't answered sooner, but I've been working away for a few days.

I am running a RAID array, and the file system is NTFS.

I am very wary about proceeding, but I do have an older machine, currently running W98 that I am going to use to experiment on.

Thanks again,

Phil J.

---

