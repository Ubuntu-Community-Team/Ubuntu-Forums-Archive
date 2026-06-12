---
title: "How critical is partitioning in relation to performance"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by soerv on 2007-09-29
Question: Should I startover partitioning manually? What could I expect for improvement?

I am as newbie as they come, less than 24 hours experience with ubuntu, and don't want to go to much further if it is wise to start over.

In another post there is a suggestion that ubuntu first on the harddrive can make improvements.
Ideally Vol(swp) 1st partition then Vol(ext) then Vol(ntfs)

I'm begining to think it doesn't matter to much, yet would still like feedback on what to expect from ubuntu.

Computer: 5yrs old, HP prebuilt in 2001 bestbuy special, my sister was going to throw it out, needed new harddrive that i replaced with Seagate 80GB.
Set up to dual boot XPHome on 20gig partition, ubuntu has the rest.  I used the installer to partition for ubuntu.  I am very pleased with results, documentation on ubuntu site very useful. 
Because I am a new I let ubuntu take all available unallocated space.  Later I read in more advanced setup documentation that better planning of diskusage can increase performance.

I'm looking for opinions on this.  I am not sure if it is slow, little experience to compare to other than windows.  Overall I am very satisfied, however I am wondering about what I should expect.

Ubuntu Filesystem capacity 43.1 GB  Available 40.7GB
vol order and size approximately:
Vol
Vol(ntfs) 20GB  ~ 39%
Vol(swap) 1.5GB ~ 1.9%
Vol(ext3) 47GB  ~ 59%

Processor: Intel Pentium 4 CPU 1.50GHz
Memory 512k
Devices: CDRW, DVDROM, FloppyDisk, EthernetNIC, WinModem(notusing)
Has a JoyStickGame port I'm not using.
Firewire, not sure what to use it for I may remove it.
A couple other gadgets my nephew must of used, that can be removed.

---

### Post by mivo on 2007-09-29
Personally, I would give Ubuntu three partitions. 10 GB for /, 1-2 GB for swap, the rest for /home. No performance gain, but much easier to reinstall if something goes wrong. The data in /home (all your personal stuff, photos, videos, songs and especially settings, etc.) would be left alone, and only the system in / would be deleted/reinstalled.

---

### Post by metroplex on 2007-09-29
> **mivo said:**
> Personally, I would give Ubuntu three partitions. 10 GB for /, 1-2 GB for swap, the rest for /home. No performance gain, but much easier to reinstall if something goes wrong. The data in /home (all your personal stuff, photos, videos, songs and especially settings, etc.) would be left alone, and only the system in / would be deleted/reinstalled.

I totally agree with this. A common "mistake" when installing a system is not to make a separate partition for /home.

---

### Post by Orbital75 on 2007-09-29
I agree with you guys, I'm a Linux newbie and I just let Ubuntu's partitioner make all the partition decisions for me.  
Maybe having Ubuntu create a home partition should be added to the default installer. You could always give the 
option not to have it do it.  :KS

---

### Post by soerv on 2007-09-29
Thank you for the responses,
I changed my mind again, now believe it does matter not just for performance but a little planning to save future headache.

Good suggestions already been brought up in Orbital75's new thread "Good Partition Scheme"

---

### Post by mivo on 2007-09-29
Yes, having /home on a separate partition is going to save you future headaches. Installing the core system and apt-get'ing the programs you use is fast and painless. You can do this  in a few hours, depending on your internet connection. But configuring and setting up everything is a lot more time-consuming: and this information is stored in /home (mail is also kept here, at least if you use Evolution, KMail, etc.).Reinstalling is never pleasant, but you can really minimize the hassle if you have a separate /home partition. :)

---

### Post by BertP on 2007-09-29
Here are a couple noob questions:

 1) how does  one change his Ubuntu configuration so that his home directory is moved another partition?  

2) can GParted *non-destructively* split  into a few partitions  a drive  that  was formatted about 2 weeks ago into one partition for Ubuntu?

Thanks!

---

