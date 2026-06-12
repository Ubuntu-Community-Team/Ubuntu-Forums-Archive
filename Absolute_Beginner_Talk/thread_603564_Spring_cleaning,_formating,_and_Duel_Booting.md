---
title: "Spring cleaning, formating, and Duel Booting"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-05
I've asked something similar to this but not as detailed. 
I plan on duel booting XP and Ubuntu 7.10 but I'd like
to ask a few question before I make the leap.

My Partition plan will look like this.

Windows:
C:  ( Operating System Partition )
D:  ( Programs and Personal Files Partition )

Ubuntu:
/
Swap
Home

1st. question....  
Since windows slows down and needs to be reinstalled about every year
how hard will it be just to reinstall windows with a duel boot and not mess
up ubuntu?

2nd question.....
I know I will need to eventually reinstall Ubuntu at some point so kinda the
same question, with it being a duel boot can I reinstall ubuntu without 
messing up windows?

3rd question.....
If I did have to reinstall Ubuntu and I had a separate home partition, I am
assuming I could just reinstall Ubuntu and all my configurations files would
still be there in my Home partition but I'd have to reinstall the programs 
the conf files use. If I decided not to use that program any more and the 
program wasn't installed after reinstalling Ubuntu, could I just delete that 
programs conf file folder  in my home and not have to worry about deleting 
anything else?

Thanks

---

### Post by Inxsible on 2007-11-05
1) Doable but difficult and a pain in the a$$. It is always a good idea to install Windows first and then Ubuntu/Linux. Windows tends to mess up the MBR (meaning, it does not cleanly recognize the other OS'es on your hard drive)and then you cannot login to Ubuntu. This can be avoided if you take precautions and are extremely careful though.

2) Extremely easy and a piece of cake. All you do is install the OS in the root partition.

3) Yes.

---

### Post by dwblas on 2007-11-05
3) Yes - but, when you install you have to tell the installer that you have a separate partition for /home.  This is done in the disk formatting portion which is where you also tell the installer what partition you want to mount as root, "/".  This is not only possible but a good idea.  If you want to try X/KUbuntu in another partition, you will still have the same /home across all distros.  Also, it is often the one partition that you want to back up more often.

1) There are programs like SuperGrub that allow you to reinstall grub.  I think you boot from a CD and then tell the program that you want to boot the MS Windows kernel on /dev/hda1, and the Linux kernel on /dev/hda2, etc.  It will find them and write the MBR -- but -- I am not at all familiar with it, so check this forum, Google, or the SuperGrub website for specifics.

"Spring cleaning"?? You must be south of the equator.

---

### Post by az on 2007-11-05
1.  You will have to take care to not delete your other partitions in the process.  Other than that, you will need to reinstall grub.  You can do this from the Ubuntu live cd.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

2. It will work by default.

3.  I do not recommend a separate home partition.  You run the risk of running out of space.  As for your configurations, they are simple to back up.  Backing them up to a different disk is easier, more reliable and safer.  Also, sharing configurations of the same application between different versions of those apps can be problematic.  

It may sound cool, but there is no really good reason to have a separate home partition.

---

