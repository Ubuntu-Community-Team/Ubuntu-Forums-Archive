---
title: "I am afraid to start"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-05-26
I have two hard drives one of which, an 80 gig drive, has Win-XP-home and all my programs and data on it.  

I also just had a new motherboard installed on my computer and did the XP-home installation on a 160 gig drive without the second drive in the computer.  I would like to be able to double boot Windows and Ubuntu. I have the Ubuntu live CD and am ready to install it.  I am afraid because I have read that I am likely to lose the XP-home installation when I parttiton and install Ubuntu from the live CD. Is this still an issue or has this problem been addressed?

My goal is to have the two OS's and all my programs and data on the one disk and use the other as a back up.  However I am unsure of that because things haven't worked out as I had hoped.

The new disk with XP-home and AVG on it was named C when only the one disk was in the computer.  When I installed the other disk as a slave disk the first disk was named G and the slave disk was named C.  Was that because there was an operating system on both disks?

I tried to go back to the 80 gig disk tthat had he OS and all my programs and data on it so I took the 160 gig drive out and put the 80 gig drive in as master.  When it booted it did not return to the way it had been.  instead it saw all my hardware as new hardware and now some of it doesn't work.  I can't use my old HP 9100 CD-writer to make copies of my data.

Should I just take the 80 gig drive out and put the 160 gig drive back in, try to partition and install Ubuntu and then reinstall all the programs before I try to recover data from the old drive?  Should the programs be installed in the Windows partition or can they be installed a a partition called home along with the data if I am able to recover it? 

Another question: (I am full of them due to complete computer ignorance) Rather than copy folders and files, will I be able to drag and drop them from one disk to another if the computer changes the disk names at reboot?

---

### Post by starcraft.man on 2007-05-26
A quick note right off the bat, the live cd does not erase your XP partition unless you choose to. You the user have to pick the wrong option to get that done, it's never failed me or a lot of other people.

Ok, I got a bit lost as to what you did what with install both drives with two different installs of XP, thats not really advised and I guess you confused windows bootloader. Download and burn this bootloader, its called [GAG,]("http://gag.sourceforge.net/") it will detect both drives in your computer and allow you to boot to both. Only reason for it to fail is if you've corrupted them.

Once you get all your data to one, I'd say delete the other. No point IMO in two copies of XP.

This is a [good guide]("http://www.psychocats.net/ubuntu/installing") to installing from live CD (can do a dual boot with this also), and this one for setting a [dual boot]("http://users.bigpond.net.au/hermanzone/p2.htm") with alternate and a fat share. Remember to think carefully when you partition, the only way something gets deleted is if you approve it.

So, in summary, just use GAG and get to your files, pick one copy to keep and move your data there. Then wipe the other drive and format it for data storage. Then, use the installer and make your drive (with XP) dual boot Ubuntu. That should have you running in no time :).

---

### Post by init1 on 2007-05-26
Ok, so you have two drives, both with winxp, one with 80gb and the other with 160gb, right? If the ubuntu installation is done correctly, you will not lose any data from you winxp. I have had issues with ubuntu and repartitioning, but all that did was tell me that I had not specified a root (/) partition when I already had. I think you can tell it to resize your largest partition, so that you can tell it how much free space off your winxp partition to remove. About your second  hard drive, ubuntu can recognize it, but the device syntax is very different from windows
Steps:
Insert only the hard drive you wish to have ubuntu on
Install (make sure you choose the choice with the slider so you can choose the amount of space you want. The first choice removes ALL and the third is custom and very difficult for beginners)
Reboot
It should allow you to boot ubuntu and winxp.
If you need help with the ubunut device syntaxes, just ask me

---

### Post by seshomaru samma on 2007-05-26
Read starcraft.man 's link in the second post very carefully and remember it's only Windows that names partitions C , D or G. In Linux they are named differently (often hda1,hda2...) .
If you are running the live CD now , open a terminal (look for 'terminal' in the menu that opens up on the top panel) and copy-paste this command :
```
sudo fdisk -l
```
it will show you your current partitions the way Linux sees them with their Linux name

---

### Post by henthorn on 2007-05-26
Thanks to all who answered.  Is there a reason to use FAT32 as a data instead of ntfs?

---

### Post by dptxp on 2007-05-26
Yes, Linux shall not R/W NTFS.
Best is ext3, you can make Windows r/w to ext3.
Maybe some FAT32, some EXT3.

---

### Post by starcraft.man on 2007-05-26
> **henthorn said:**
> Thanks to all who answered.  Is there a reason to use FAT32 as a data instead of ntfs?

FAT32 is natively supported by Ubuntu, you can read and write with no extra hassle. NTFS requires you to install ntfs-3g drivers (without drivers, you may only read and NOT write to NTFS), you install those separate and then configure/remount the drives. Unless you must use a NTFS partition or use an existing one, Fat is just easier to me. Go with NTFS if you wish, remember to get the drivers. Search forums for guides on ntfs-3g config.

---

