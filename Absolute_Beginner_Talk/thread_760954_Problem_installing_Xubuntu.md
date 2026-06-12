---
title: "Problem installing Xubuntu"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by mzbeg on 2008-04-20
Hi all,

I am absolute bigner. I tried to install Xubuntu 7.10, and I get the following error :

[81.61366] ata 5.00: failed to set xfermode (err-mask (0x40)

It says type 'help' at the prompt. After typing 'help' what I see is ailen english language. Can not make a head of tail of it.

I have used different CDs and all verified correct.

I am running Windows XP, SP2, I have already partitioned Hard Drive and have allocated 25 GB for Xubuntu. There are six partition on my disk. C: is for Windows XP, D: for Ubuntu; E: for Edbuntu and the rest are for different uses, all for XP.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - Samsung SH-S203LJ DVD RW- EZCOOL Case

---

### Post by LeoSolaris on 2008-04-20
I found this on the forums. It is for Feisty, but it may apply. Couldn't hurt to try.

[http://ubuntuforums.org/showthread.php?t=417961](http://ubuntuforums.org/showthread.php?t=417961)

Leo

---

### Post by mzbeg on 2008-04-21
Hi all,

I have added partition info of my hard disk to my original query, which I think is relavent to my problem.

> **mzbeg said:**
> Hi all,

I am absolute bigner. I tried to install Xubuntu 7.10, and I get the following error :

[81.61366] ata 5.00: failed to set xfermode (err-mask (0x40)

It says type 'help' at the prompt. After typing 'help' what I see is ailen english language. Can not make a head of tail of it.

I have used different CDs and all verified correct.

I am running Windows XP, SP2, I have already partitioned Hard Drive and have allocated 25 GB for Xubuntu. There are six partition on my disk. C: is for Windows XP, D: for Ubuntu; E: for Edbuntu and the rest are for different uses, all for XP.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - Samsung SH-S203LJ DVD RW- EZCOOL Case

---

### Post by nicedude on 2008-04-21
I have already partitioned Hard Drive and have allocated 25 GB for Xubuntu. There are six partition on my disk. C: is for Windows XP, D: for Ubuntu; E: for Edbuntu and the rest are for different uses, all for XP. 

You can only have 4 primary partitions per hard drive of this I am pretty certain. So I count 3 primary just for C: D: E: since they are OS partitions, This means if one of the other 3 was partitioned as primary when created that you are now out of primary partitions on this disk and Xubuntu wants to partition one during install. Could this be your problem? If so you will have to get rid of a primary and make it logical as you can have unlimited logical partitions.

If im wrong somebody speak up.

---

### Post by mzbeg on 2008-04-21
> **nicedude said:**
> I have already partitioned Hard Drive and have allocated 25 GB for Xubuntu. There are six partition on my disk. C: is for Windows XP, D: for Ubuntu; E: for Edbuntu and the rest are for different uses, all for XP. 

You can only have 4 primary partitions per hard drive of this I am pretty certain. So I count 3 primary just for C: D: E: since they are OS partitions, This means if one of the other 3 was partitioned as primary when created that you are now out of primary partitions on this disk and Xubuntu wants to partition one during install. Could this be your problem? If so you will have to get rid of a primary and make it logical as you can have unlimited logical partitions.

If im wrong somebody speak up.

My 500GB hard drive is partitioned like this :

C: Primary 50 GB and 2nd Primary has 4 partitions all Logical.

Since your letter I have merged D and E. Tried again and still get the same problem. I do not know perhaps is it some thing to do with SATA ?

Thanks for your help.

---

### Post by mzbeg on 2008-04-22
Hi all,

I used iqrpoll switch in command line, it reached up to desktop, either it did not recognize my USB Wacom tablet mouse and I do not know any shortcut to exit or the Desktop itself was frozen, so I had to hard boot it.  Since then it loads kernel, the black screen with a blinking cursur comes up and stays there. Nothing happens.

  Now what next ?

---

