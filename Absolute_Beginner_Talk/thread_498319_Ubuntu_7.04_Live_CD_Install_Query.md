---
title: "Ubuntu 7.04 Live CD Install Query"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by BruisedQuasar07 on 2007-07-11
Ubuntu 7.04 live CD is the most newbie friendly Linux distro I have checked out. It fails in one area only, the Install process. I found the Desktop newbie friendly and Install goes fine until you get to the partition part!
If a newbie wants to try allowing the system on the live CD to partition a Windows hdd, which does he pick
"Guided-use entire disk\name of your hdd", or "manual"

If you use "manual" What do you do with the very foreign (to Windows users) terms?

I searched help but it does not include installation. Ubuntu could bring linux to many users if it had plain language step by step install instructions included on the desktop you see after the live CD installs into RAM memory and puts up the desktop. 

Is there a text file somewhere that walks a newbie through dual partition installation from the live cd?
Windows would face serious competition if a Linux distro group put themselves into newbie shoes. 10s of millions of PC users would use Linux, instead a tiny percent of users, if Linux distro teams had a member who understands newbies will stick with a distro, provided installation onto a Win system was explained step by step in English or whatever lanuage, not in Linux-ese. 

For instance, automatic partition and installtion means automatic to consumers. Not partly automatic, until a user gets to the Linux-ese part and the help section addresses only installations beyond installing Ubuntu from the live CD. Its been how many years that Linux Distros have tried and failed to bring Linux to the people?
You'd think at least one distro team would have figured out by now that so-called newbie friendly distros must be tested using total newbies, not insiders and especially not using Linux macho power users. The same mentality kept most people from the early online system, the BBS (Bulletin Board System). AOL became huge fast by first changing this and then bringing Internet to the people. Their secret? COMMUNICATION for the busy non-technically inclined.

---

### Post by az on 2007-07-11
> **BruisedQuasar07 said:**
> 
For instance, automatic partition and installtion means automatic to consumers. Not partly automatic, until a user gets to the Linux-ese part and the help section addresses only installations beyond installing Ubuntu from the live CD. Its been how many years that Linux Distros have tried and failed to bring Linux to the people?

Er, you should be shown the option to use Guided Partitioning (hand-off partitioning).  If you don't get that option, try defragmenting your windows partition and then try again.

See here:
[https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf](https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf)


The installer does do automatic partitioning by default, with the user only asked how small to shrink the windows partition.  If you don't see that option, either:
1- you don't have enough space
2- The partition table on your drive is corrupt / the partitioner cannot safely do anything
3- It's a bug.

---

### Post by LaRoza on 2007-07-11
> **BruisedQuasar07 said:**
> 
Is there a text file somewhere that walks a newbie through dual partition installation from the live cd?
Windows would face serious competition if a Linux distro group put themselves into newbie shoes. 10s of millions of PC users would use Linux, instead a tiny percent of users, if Linux distro teams had a member who understands newbies will stick with a distro, provided installation onto a Win system was explained step by step in English or whatever lanuage, not in Linux-ese. 

For instance, automatic partition and installtion means automatic to consumers. Not partly automatic, until a user gets to the Linux-ese part and the help section addresses only installations beyond installing Ubuntu from the live CD. Its been how many years that Linux Distros have tried and failed to bring Linux to the people?
You'd think at least one distro team would have figured out by now that so-called newbie friendly distros must be tested using total newbies, not insiders and especially not using Linux macho power users. The same mentality kept most people from the early online system, the BBS (Bulletin Board System). AOL became huge fast by first changing this and then bringing Internet to the people. Their secret? COMMUNICATION for the busy non-technically inclined.

The Ubuntu installer is the easiest installer for any operating system I have ever seen. The Windows installer is...heck. It is just that the average computer user never installs an OS.

Here is the computer people perspective: [http://computerjokes.net/105.htm](http://computerjokes.net/105.htm)

I am writing this because although you stated your problem, you added a lot of filler that makes you question difficult to understand.

If you say what is on you computer now (partitions, other OS's, etc), and what you want to do, it will be easier to help you.

---

### Post by BruisedQuasar07 on 2007-07-14
AZ. thank you for the quick reply. I have the CD that the Ubuntu project sends out. I wondered if something wasn't working correctly. I am trying to dual boot onto a Thinkpad T23. My information from a Thinkpad board I am active on is that my CD should do exactly what you post. I do not get an auto installer, other than live CD install, which is unbelieveably smooth and easy. I get everything but Wifi handed to me on a platter. Everything works without my answering any questions. I did run defrag three times and I ran System Mechanic deep analysis and repairs prior to trying to dual boot install. I get only two choices, manual and make a single Ubuntu partition. 

I will get another disk. What is Alternative Disk? I understand it installs better.

---

### Post by e_james on 2007-07-14
Perhaps I could illustrate the situation with reference to a purely Windows installation. If I had a new Windows XP machine with a hard drive of about 200GB, the first thing I would do is to repartition it (if possible). I would resize the C drive to about 15 to 20GB and create at least 2 new partitions (if they don't already exist). The first new partition would be approximately the same size as the C drive and formatted to FAT32. The second would be the remaining space and can be either FAT32 or NTFS. NTFS is more reliable and secure but, if it breaks, it is harder to fix. Let's say drive E at 20GB FAT32 and drive F at 160GB NTFS.

The next step is to make a backup image of the C drive in drive E. Windows itself can't do the partitioning and backup image but there are many choices of bootable CDs which can, some of which are Linux (e.g. Ubuntu Live CD or Knoppix). After the initial backup image, I would then install any desirable additional software and also redirect the "My Documents" folder to a suitable folder on drive F. The final step would be a second backup image of the C drive again using the E drive. The F drive will be the main data drive and a suitable data backup strategy is desirable. The images on the E drive can be written to DVDs for security.

A total hard drive failure is a possibility but it is more likely that data corruption of the C or F drives will be the problem. The above procedure provides as many recovery options as possible.

Depending on the intended use of the PC and the actual size of the hard drive(s), there are many other useful configurations. If I wasn't sticking only to Windows, I would add partitions for Linux as well, in which case it is probably best to make the data drive FAT32.

The Ubuntu Alternate Install CD uses text only screens and offers more options. It is therefore more flexible but also requires more knowledge of linux installations. Bearing in mind my partition preferences I have always used the Alternate CD for dual boot (or triple boot) installations. One of the advantages of dual booting Windows / Linux is that the Linux installation gives you more options for repairing Windows e.g. connecting to the internet or reading / writing external drives.

PS. I have no experience of Windows Vista and I don't want any.

---

### Post by Hendrixski on 2007-07-14
I see that you're new so I fhtough I'd say **WELCOME TO THE COMMUNITY!**
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others. A lot of the people on these forums are also the same people who write software or documentation or other contributions that make up Ubuntu.    Why? because we love freedom.

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

