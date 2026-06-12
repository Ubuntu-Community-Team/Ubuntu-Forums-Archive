---
title: "Hardware RAID 1 - is this going to be a problem?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by DeltaHF on 2007-06-10
My new computer has an [Intel D975XBX2 "Bad Axe 2"]("http://www.intel.com/products/motherboard/d975xbx2/index.htm?iid=mbd_main+xbx2") motherboard, which includes a hardware RAID controller.  I want to set up a RAID 1 array and dual boot Vista x64 and Ubuntu 7.04, but my preliminary research is turning up all kinds of disconcerting discussions.  Most of the comments seem to be targeted to "fake RAID" users interested in a software solution, and I can't seem to find any clear-cut confirmation that I will or will not be able to install Ubuntu on a RAID 1 installation.  Can anyone cut through the clutter to confirm or deny my speculations?

---

### Post by dave-5B on 2007-06-11
i am by no means an expert but anyway..

i think the whole point of hardware raid is that it presents ONE volume to the opreating system and all the RAIDy stuff is taken care of by the BIOS, so in theory linux/windows shouldn't even notice you have a raid array

also maybe the lack of comments about hardware raid means good things? (ie its relativley easy)

---

### Post by gridsleep on 2007-06-12
DO NOT UNDER ANY CIRCUMSTANCE TRY TO INSTALL UBUNTU ALONGSIDE XP64 ON A RAID SYSTEM.

I just tried it and it was nearly a disaster.  First, there is no partitioning software I have found that works 100% reliably with XP64 RAID.  Second, Ubuntu from the Live CD does not recognize hardware RAID.  It sees the RAID mirrored drives as two separate drives.  I also have a third drive for extra storage.  All are SATA II and stable under XP64.

I tried to install Ubuntu on the RAID disk but the Grub installation failed.  I then tried to install it to the third non-RAIDed disk.  It installed, but again the Grub presented a problem.  After the RAID setup screen during boot, the XP64 start screen would flash on for a moment, then there was a moment of a blue screen too quick to read, and the system would reboot.  I thought the RAID was damaged, and it was, but the solution was to physically disconnect the third drive.  XP64 was then allowed to boot properly.  I had to wait until the XP64 booted up, and then plug the third drive back into the motherboard hot while the power was on so I could access it.  No amount of FIXBOOT or FIXMBR attempts would fix the problem.  I had to repartition and reformat the third drive to get rid of the Ubuntu, and copy back all the data I had fortunately backed up previously.

The XP64 boot was still failing, though.  I had to use the RAID utility to rebuild the primary disk from the secondary.  Apparently Ubuntu puts the Grub onto only one disk, which disrupts the RAID striping.  The second disk had not been affected and I was able to recover.  Thus, this was not a total disaster and a very good learning experience.

My recommendation is to get another drive, and SATA II 80GB drives are only $40 these days.  Use that drive to experiment with Ubuntu.  Unplug the RAID drives from the motherboard completely before attempting to install the Ubuntu.  DO NOT DUAL BOOT.  It will be troublesome swapping cables on the motherboard, but it is the only way with this particular distribution.  I don't know if Ubuntu or any other Linux will work properly with the RAID.  My motherboard utility CD does not have Linux drivers for the RAID.  Maybe Linux doesn't really need RAID, but having been able to recover with the RAID rebuild, I don't think I will build another computer without RAID.

The only reason I'm not using Ubuntu on my workstation is the lack of support for ATI Theater 550 Pro TV card.  I want to work on that and get it going.  Then, I can get rid of Windows once and for all, as I have on my laptop.

---

### Post by DeltaHF on 2007-06-13
Wow, that sounds like quite an ordeal - thank you very much for your knowledge!  I do find it rather surprising that Ubuntu has such difficulty with hardware RAID configurations, especially considering the countless Linux servers which depend on a reliable RAID array.  Perhaps someone else will be able to come along and clarify.  So much to learn, so little time!

---

### Post by scribles on 2007-06-13
There are two reasons why hardware raid is poorly supported in Linux (this isn't unique to just Ubuntu)

1. Most raid controls (especially the ones that come on a motherboard) don't actually do anything. They come with drivers that allow the operating system to manage the raid array. So in fact they are not hardware raid arrays they are just hardware that come with raid software.

2. There is only minimal performance improvement in using hardware raid as opposed to software which is offset by the cost of hardware raid (real hardware raid, not the controllers that comes on a motherboard). So most Linux servers either use software raid and use the money they save to buy faster servers or spend the extra money on hardware raid that is supported.

Of course if you are dual booting Linux and Windows software raid wont work on both. My solution is to set up software raid for Linux and install Windows without raid, but I very rarely use Windows at all. Installing another drive for Linux and using the raid array for Windows will also work and It is possible to dual boot with Grub, but it is very possible that you may run into problems similar to what gridsleep described.

The bottom line is that installing a raid array is never trivial and if you are going to install a dual boot system with any kind of raid you should be prepared to spend a great deal of time getting it working and BACKUP ALL OF YOUR DATA FIRST because things can and likely will go wrong.

P.S. I just realized some I wrote needed to be clarified. Dual booting to a raid partition with Grub is only possible if the raid array is raid1. Grub cannot boot to a raid0 array.

---

### Post by la3875 on 2007-06-13
:KSOutstanding thread! I'm about to embark on building a network storage box at home and was going to set up Ubuntu Server on a hardware RAID1. I may reconsider the hardware solution after seeing your responses.

Looking forward to monitoring your progress and experiences.  All the best!

---

