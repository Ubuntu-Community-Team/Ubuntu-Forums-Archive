---
title: "Problems with partioning PPC during install"
date: 2012-06-27
forum: Apple Hardware Users
---

### Post by krespim on 2012-06-27
Hi all,

during a clearance sale at my place of work I got a G5 PPC with 4 processors for 25 euros. Not had (gloat mode).

So the 1st thing that came to mind, and since my laptop is already running dual-boot win7+Ubuntu, was to install dual boot Mac OS 10.5+Ubuntu to make better use of the computer. 

I've download the latest 12.04 installation CD (for PPC) and using the disk utility in Mac OS partition the disk (500GB) in 2: 100GB for OS X and 400 for linux. Both partitions have the OS X extended file system.

After rebooting the computer and going through the initial steps I've ran into problems at this step (taken from the FAQs for PPC installation):

> **What do I need to know for dual-booting?**

 See [here]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"), as it has some additional information for you. 
Assuming  you have the other OS already installed, then the easiest thing to do  is shrink an existing partition so that there is free space available on  your hard drive.  You can then choose the "Use the largest continuous  free space" optition when installing Ubuntu. Remember to backup any  important data before repartioning. I select the ""Use the largest continuous  free space" option and get an error:
>  Failed to partition the selected disk
This probably happened because the selected disk or free space is too small to be automatically partitioned.
 Any suggestions on how to solve the problem? if I go medieval (= manual partition option) will the OS X installation be lost? 

Cheers.

---

### Post by rsavage on 2012-06-27
That'll be my unclear instructions then.  To be honest they were written when I didn't really have a clue how things worked (and when no current live cd was available).  They could do with an update by somebody with Mac OS/X experience.

If you've already set the 400GB partition  type then it is not classed as free space even if there is no data in the partition.

The manual partition option would be the way to go.  Unless you do something wrong it won't touch your Mac OS X install.  You can delete the 400GB partition there.  If you are not confident setting up the required partitions you can  go back to the 'Use largest free space' option once you've deleted the 400GB partition.

As an aside, the live CD (and alternate CD) does have options for shrinking partitions which is supposed to make setting up dual booting easier.  How well they work with mac partition types I have no idea, but they work for dual booting two linux systems.

---

### Post by krespim on 2012-06-28
Thanks rsavage.


> **rsavage said:**
> 
The manual partition option would be the way to go.  Unless you do something wrong it won't touch your Mac OS X install.  You can delete the 400GB partition there.  If you are not confident setting up the required partitions you can  go back to the 'Use largest free space' option once you've deleted the 400GB partition.


My first attempt was before partioning the disk and the same error  occurred. There might be something funky going on. Anyway, I'll remove  the partition and give it another go with largest free space and if that fails -> live CD. manual partion will be the last option as I feel very queasy when having to partition stuff in a minimal interface and without actually knowing what I'm doing. 

> **rsavage said:**
> 
As an aside, the live CD (and alternate CD) does have options for shrinking partitions which is supposed to make setting up dual booting easier.  How well they work with mac partition types I have no idea, but they work for dual booting two linux systems.

Ah ok. I thoutgh of using a LiveCD but could not find one that is specific for PPC. So I guess I would install a "normal" distro and then change it for PPC in Ubuntu. Is that correct?

---

### Post by rsavage on 2012-06-28
For some reason the PPC live CD is called a desktop CD.  You'll find the links on the PPC downloads page.
  
> 
My first attempt was before partioning the disk and the same error  occurred


If you had just one big partition then you could of maybe tried the 

'Guided - resize "drive details" and use freed space'

option, but I don't it would work for hfs+.  Same for the live/desktop CD.  You'd need to install some extra packages to be able to shrink partitions and preserve data.

Once you delete your 400GB partition then the installer should recognise the free space and you'll be away.

---

### Post by krespim on 2012-06-29
> **rsavage said:**
> For some reason the PPC live CD is called a desktop CD.  You'll find the links on the PPC downloads page.
  
If you had just one big partition then you could of maybe tried the 

'Guided - resize "drive details" and use freed space'

option, but I don't it would work for hfs+.  Same for the live/desktop CD.  You'd need to install some extra packages to be able to shrink partitions and preserve data.

Once you delete your 400GB partition then the installer should recognise the free space and you'll be away.


I'm struggling with it. I've started OS X, deleted the 400GB partition to have only one partition at the time the Linux installation starts. Re-boot, re-boot again and start from the Ubuntu CD. Progress as normal to the partition step, choose "use large continuous space" and get the error again.

I'm probably doing some daft mistake. I'll try it again soonish but this time I'll write here what is the partition table that the installation detects/recommends - it might help to spot the mistake.

Thanks for your patience.

P.S. I should add that the OSX is a fresh installation and I have no data in the drive. The reason why I want dual boot is because I use OSX at work and it might come handy to have at home as well.

---

### Post by rsavage on 2012-06-29
Hmm... I'd try the live CD and make sure the computer can see your hard drive.  Maybe you are missing a kernel module or something?

---

### Post by krespim on 2012-07-01
> **rsavage said:**
> Hmm... I'd try the live CD and make sure the computer can see your hard drive.  Maybe you are missing a kernel module or something?

The solution was simpler than that and it was mostly my bad.

There were 2 things I was doing wrong:
 1. Major issue: In OSX I was creating a new partition when I should have  simply resized the existing one and leave the space "empty". I went  back to the instructions and suddenly it all became clear.
 
 2. Minor issue: I was trying to install Ubuntu straight from the CD  without starting a "live session". When the 1st prompt appears one must  write "live" to start the Live session. Once I go live and with the  empty space in the HD, installing Ubuntu in Dual boot was a matter of a  couple of clicks (as expected).
 
 I still don't know if OSX was left unmarked but I assume so. A couple of  things are not quite working and I am looking for solutions online now:
 
 - Internet access is through a ASUS wireless USB adaptor N13. It was  immediately recognized and started working with Ubuntu 12.04 (not in the  live session) but the download speed is quite slow. That seems to be a  reported problem and workaround should be available. 
 
 -Icons in the side bar of Unity are a white square. Again this seems to have reported.
 
 -I need to install the support for multicore processing (the machine is quadcore). From here:
 > Before 12.04, the default 32 bit PowerPC Ubuntu kernel image does not  support SMP. This should not prevent installation, since the standard,  non-SMP kernel should boot on SMP systems; the kernel will simply use  the first CPU only.  In order to take advantage of dual processors,  you'll have to replace the standard Ubuntu kernel with the SMP version.   [Install]("https://help.ubuntu.com/community/InstallingSoftware") the [linux-powerpc-smp]("apt:linux-powerpc-smp") meta-package. 
 
 I am updating the packages now and perhaps some of the issues will go  away but if you could redirect me to some solutions I'll appreciated. 
 
 Thank you for your help.

---

