---
title: "Is it possible to partition too much?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by ElliottMarlow on 2007-07-21
I've been using Ubuntu 7.04 for about a week and I am already greatly impressed, as well as excited to be participating in such a great concept as open source technology, software, etc. As far as my computer-savviness is concerned, I know more than some but much less than most, which will probably be reflected in my misuse of terms, so please bear with me. In addition, I like to thoroughly explain myself (i.e. ramble), so if you'd like to skip all the jibber-jabber, I will highlight my questions/main points in bold.

I have an 80 GB hard drive on a Dell Inspiron 6000. I resized my main partition to leave 15 GB unallocated for Ubuntu to install itself, mostly for fear of completely abandoning Windows XP cold-turkey. While I am still not ready to completely make the switch to Ubuntu, I am ready to devote more of my hard drive to it. **In switching between Ubuntu and XP, I have noticed a definite lag in the functionality of XP.** For example, when I reboot, hibernate, or shut down from XP, it now takes FOREVER to complete. Even opening programs such Trillian or Firefox takes twice as long as before. **Is this in some way due to my newly created partition? ** It seems strange to me that XP would slow down, while Ubuntu runs flawlessly, and seemingly much faster than XP ever did. 

I used Partition Magic to resize my original partition, and** I was planning to use it to enlarge my 15 GB partition to maybe 25 or 30 GB, or probably more in the future. Will this slow XP even more? Is there any danger in continually resizing a partition? ** This is the first time I have ever dealt with partitions, so I really have no idea if, or how risky it can be to the safety of a hard drive. 

Thanks for reading.

---

### Post by sad_iq on 2007-07-21
You can rest assured the newly Ubuntu booting in your machine can not affect Windows Xp. The slowlines that you have on xp is just one of it's "features"...happens to everybody!! Maybe you just got used to the speed of Ubuntu(I know I have!!!). Partitioning your drive shouldn't mess windows...and Ubuntu cannot write by default to a ntfs partition so it cannot touch it!!! The only thing I can think of is if you didn't defrag your windows install before you partitioned...maybe something went wrong thou (however I don't think it ever happend...it's just a theory!!!).
 Unfortunately...I don't have much experience with dual boot (switched directly) so I can't tell you how resizing windows partition to increase the linux one can be done :(

---

### Post by ayenack on 2007-07-21
Have you got a firewall installed on Ubuntu? If you have not it's possible (but uncommon) for a virus to get on to your XP install. Try running your anti virus on XP and see if it comes up with anything. Other than that Ubuntu should not slow XP in any way. Make sure that your XP disk is not write enabled under Ubuntu if it's mounted during boot which it may well be.

---

### Post by louieb on 2007-07-21
May not be a virus. How full is your XP partition? Performance will degrade when it get to about 70% full at around 80% you will see a noticeable drop in performance. May be its time to clean up your XP install.

---

### Post by PilotJLR on 2007-07-21
> **ayenack said:**
> Have you got a firewall installed on Ubuntu? If you have not it's possible (but uncommon) for a virus to get on to your XP install. Try running your anti virus on XP and see if it comes up with anything. Other than that Ubuntu should not slow XP in any way. Make sure that your XP disk is not write enabled under Ubuntu if it's mounted during boot which it may well be.

I'm pretty sure this is not true. While running Ubuntu, this "virus" would need to be executable in Linux in order to even have a chance at writing to a separate NTFS partition.
And packet filtering firewalls have nothing to do with viruses... if a Windows user, for example, receives a virus from a website or email attachment, then a packet filter wouldn't care anyway. Application-aware firewalls, which are usually commercial appliances or software, can filter out viruses at the gateway... but this is not the same as iptables / netfilter.

---

### Post by PilotJLR on 2007-07-21
You may also want to run defrag from within XP.

---

### Post by ElliottMarlow on 2007-07-23
In XP, I used Diskeeper to defrag during idle time. Before I installed Ubuntu, I made sure it was defraged, which it was. Thanks for the reply though, and yes I have noticed how much faster Ubuntu is than XP!

---

### Post by ElliottMarlow on 2007-07-23
> **louieb said:**
> May not be a virus. How full is your XP partition? Performance will degrade when it get to about 70% full at around 80% you will see a noticeable drop in performance. May be its time to clean up your XP install.

The XP partition is about 40 GB, with a solid 38 GB being used. You're right, I think that does probably explain why XP became so slow. Before I reserved 15 GB for Ubuntu, that 15 GB was just free space in XP. 

However, I have another problem now. I decided to back up a lot of my data on DVDRs, and planned to  transfer stuff over to Ubuntu. (Keep in mind my total HD size is 80GB) I freed up an extra 17 GB on the NTFS partition. Using Partition Magic, I shrank NTFS from 65 GB to 48 GB, which essentially turned that 17 GB of free space on NTFS, to 17 GB of an unallocated partition. I assumed that I could just enlarge my Linux Ext3 (which is is 15 GB) by 17 GB (to bring it up to 32 GB) and fill that void of unallocated space, but I was wrong. Partition Magic will not resize Ext 3, in fact it doesn't even present the option.  It also will not allow me to resize, or otherwise edit the new 17 GB partition of unallocated space. 

Is there any way to merge that 17 GB unallocated partition into my 15 GB Linux Ext3 partition?

Thanks for the help.

---

### Post by e_james on 2007-07-24
There seems to be a little piece of information missing. If I understand correctly you had a 65GB ntfs partition follwed by a 15GB ext3 partition which was created by the ubuntu 7.04 live CD install. I have never done such an install so I don't know whether the second partition is primary or a logical partition within an extended partition. The ubuntu live CD has a graphical partition manager "gparted" which is not installed by default on the hard drive. By running the live CD you can resize ntfs, ext2 and ext3 partitions. Unfortunately gparted can't move them. I understand this is because it can't move the lower boundary. I don't know if this is a linux limitation or a gparted limitation. I'm not in a position to check at the moment, but I think it can move the lower boundary of an extended partition. Another thing it can do is copy a partition to an unallocated space on the same drive or an external drive.

There are plenty of things I don't know about partitions but in your shoes I might try copying the existing ext3 partition into the unallocated space, deleting the original and then increasing the size of the copy. There is a risk of getting something wrong so that a fresh install of linux is necessary. The partition numbering may get confused but I think it wiil work if you finish with the same number of partitions you had at the start. You might also want to check out "partimage" for backing up partitions.

If it was my pc I would want more than one partition for linux (and for Windows). I usually make a FAT32 data partition for exchange between Windows and linux and 3 linux partitions; one for "/", one for "/home" and one for swap (you probably have a swap partition). Sometimes I make a small (100MB) partition as well for "/boot". Have a look at this link for some explanation.

[http://www.linuxsa.org.au/tips/disk-partitioning.html](http://www.linuxsa.org.au/tips/disk-partitioning.html)

or this 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

or this

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

or this 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There are other partition managers which may do what you want. One possibility is "qtparted" which is included on the SystemRescue CD. You need a bootable CD to run the partitioner.

---

### Post by koganinja89 on 2007-07-24
The only limitation to partioning is that you have one "primary" and one "extended"; however, you can have as many "logical" drives in the extended partion

---

### Post by splintercellguy on 2007-07-24
> **ElliottMarlow said:**
> The XP partition is about 40 GB, with a solid 38 GB being used. You're right, I think that does probably explain why XP became so slow. Before I reserved 15 GB for Ubuntu, that 15 GB was just free space in XP. 

However, I have another problem now. I decided to back up a lot of my data on DVDRs, and planned to  transfer stuff over to Ubuntu. (Keep in mind my total HD size is 80GB) I freed up an extra 17 GB on the NTFS partition. Using Partition Magic, I shrank NTFS from 65 GB to 48 GB, which essentially turned that 17 GB of free space on NTFS, to 17 GB of an unallocated partition. I assumed that I could just enlarge my Linux Ext3 (which is is 15 GB) by 17 GB (to bring it up to 32 GB) and fill that void of unallocated space, but I was wrong. Partition Magic will not resize Ext 3, in fact it doesn't even present the option.  It also will not allow me to resize, or otherwise edit the new 17 GB partition of unallocated space. 

Is there any way to merge that 17 GB unallocated partition into my 15 GB Linux Ext3 partition?

Thanks for the help.

Perhaps GPartEd?

---

### Post by ElliottMarlow on 2007-07-24
After I posted that message, I went back to Partition Magic to check things out once more. I noticed that there were two new partitions, in addition to NTFS, the nameless unallocated, and Ext3. They were "Extended" and LinuxSwap, both 729 MB. I also noticed that LinuxExt3 was completely used up, with 0 free space! 

I booted back into XP. It took upwards of 10 minutes for XP to fully load. When it finally did, I had no mouse control. Rather than spend the rest of the week dealing with XP's resistance, and since I had backed up everything on DVDRs several days ago, I decided to go balls out and completely abandon XP and my first obviously failed attempt at installing Ubuntu. I reinstalled Ubuntu using the first Guided option (the option to install using the entire hard drive) and if I understood the install prompts correctly, it patched all the partitions back together (or deleted them all) and now exists as one big happy 80 GB Ext3 partition.

Thanks for your advice though, perhaps next time I will have more patience and try to avoid hasty decisions. I'm sure I'll be posting quite a bit now that I've jumped head first into Ubuntu.

---

