---
title: "Best way to install Ubuntu"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-20
Hey everyone,

I'm a total Linux newbie.  I saw a web site earlier today where this kid talked about installing Ubuntu on his dad's PC instead of Vista and his dad loves it (and doesn't know it's not Vista).  Anyway, the story piqued my interest once again in Linux so here I am.  I have DL'd the 6.10 Desktop version and am running it off of the CD now.  It's very cool.  As is expected I have a few questions for you.

First, is there a way to access my Windows drives from this CD version (uninstalled) of Ubuntu?  While test driving this OS that would be a great way for me to try out some of the apps that come with it.

Second, here's the hardware I have in my system.  If you see any red flags let me know before I begin installation onto a hard drive.

ASUS M2NPV-VM Socket AM2 AMD Motherboard
AMD Athlon 64 X2 3600+ Brisbane 1.9GHz Socket AM2 Processor
NEC 18X DVD±RW Burner
Western Digital Caviar SE WD2500JS 250GB 7200 RPM SATA II
WINTEC AMPO 1GB (2 x 512MB) DDR2 800
SAPPHIRE Radeon X1600PRO 512MB GDDR2 PCI Express x16

Third, I could install an additional hard drive just for a Ubuntu installation if that would make sense to you guys.  It makes sense to me, but again I'm a Linux newbie...  At the moment I have a single 250GB hard drive split into two partitions.  One is for the Windows OS and programs and the other is for data.  I was thinking that instead of installing Ubuntu onto one of those drives I could just install a 40GB drive I have sitting around and dedicate that drive to the Ubuntu install.  Does that sound like a good idea?

And finally, if I do choose to install Ubuntu should I go with 6.10 or 6.06?

Oh yeah, one more question.  What's the difference between the CD download and the DVD download?

---

### Post by Bachstelze on 2007-02-20
Yes, you can do that very easily. Run *sudo fdisk -l* fro ma terminal ans pastebin what you get.

Second, ATi cards are known to be a bit more troublesome than nvidias but nothing you won't be able to sort out with a bit of work.

Thirdly, of course it does make sense tough personnally I prefer to have all my OSes installed on the same drive and have al the other drives used purely for data storage.

And finally, some people are experiencing problems with Ubuntu 6.10 (aka Edgy) but in most cases, it works fine. I'd suggest trying Edgy and going back to Dapper (6.06) if you have problems.

---

### Post by Thrasonic on 2007-02-21
Hi HymnToLife,

Thanks for the information.  The biggest reason I didn't want to install Ubuntu on the same drive as XP is in case I decide I want to remove Ubuntu entirely and stop using it.  How hard is it to completely remove Ubuntu from a partition that has an existing XP installation on it so that XP boots like it did before Ubuntu was installed?

Also, am I correct in my thinking that Linux has an issue with NTFS partitions?  I remember reading about that in the Ubuntu documentation, something about read only versus read/write.  Would it be best to maybe use a tool to convert the NTFS partitions to FAT32?

---

### Post by Maestro23 on 2007-02-21
Yeah, NTFS and Linux don't like each other.  You can install a program though, that will make them friends.:) 

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

I dual boot myself, still have XP around for my gaming, but I just made me a FAT32 partition that both Ubuntu and XP can read/write to.  You can use Gparted which comes on the Live CD.

---

### Post by Thrasonic on 2007-02-21
Thanks for the reply, Maestro23.  That's a good idea.  I could just make my data partition a FAT32 partition.  That would solve that problem.  What is the Live CD?  I'm guessing it's the same thing as the ISO I dl'd to create the Ubuntu CD?

---

### Post by fjf314 on 2007-02-21
Yes, it's the same thing.  "Running the Live CD" refers to using the system from the CD without installing it like you said you had been doing.

---

### Post by Thrasonic on 2007-02-21
Hey Maestro23, the way you are using XP is the way I was thinking I'd continue with it, assuming I fall in love with Ubuntu (Linux).  I'd need it around for my gaming, but could possibly use Ubuntu for everything else.

fjf314, thanks for the clarification.  I wasn't sure.

---

### Post by Thrasonic on 2007-02-21
Yet another question.  Why use the DVD iso versus the CD iso, or vice versa?

---

### Post by Thrasonic on 2007-02-21
> **HymnToLife said:**
> Yes, you can do that very easily. Run *sudo fdisk -l* fro ma terminal ans pastebin what you get.

Second, ATi cards are known to be a bit more troublesome than nvidias but nothing you won't be able to sort out with a bit of work.

Thirdly, of course it does make sense tough personnally I prefer to have all my OSes installed on the same drive and have al the other drives used purely for data storage.

And finally, some people are experiencing problems with Ubuntu 6.10 (aka Edgy) but in most cases, it works fine. I'd suggest trying Edgy and going back to Dapper (6.06) if you have problems.

So I opened a terminal window and typed the command above.  Sure enough it showed me a list of my drives.  They're all HPFS/NTFS, but one of them is readily available while the others aren't.  The one that i can get into is an external USB hard drive.  I have an internal SATAII drive partitioned into two drives - a 60 GB operating system/apps drive and a 180 GB data drive.  How do I gain access to those?  The external USB drive shows up on my desktop when Ubuntu loads, whereas the other two do not.  How can I gain access to them?

---

