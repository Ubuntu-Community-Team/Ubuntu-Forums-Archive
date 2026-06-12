---
title: "Assistance with re-install of Dapper Drake"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ebony_rogue on 2007-08-28
I've installed Dapper but as dual boot with XP on the same hard disk, but, first I'll share my frustrations:

I have been trying for weeks to upgrade from Dapper to Edgy, but with no success, see my earlier post here: [http://ubuntuforums.org/showthread.php?t=460764](http://ubuntuforums.org/showthread.php?t=460764)

No one gave me anything that worked so I gave up. Then my screen resolution changed (I'm assuming all by itself because I certainly don't know how to change it!). So I asked for help in forums again but nothing I was given worked. 

So now I'm sick of asking around in forums (see why we like Windows?) and feel like I'm about to give up on ubuntu.

So I now have two other questions, apart from the ones above because no-one's helped yet:
1: How to un-install ubuntu so I can get back to windows, (I don't have the XP installation cd that was used to install it on my PC, I didn't do the installation) I don't have a back up of the MBR-whatever that is and I certainly don't want to loose my work and sart all over agin.

2: So I'll admit ubuntu is kinda cool so I won't gie up just yet, is there a way I can re-install it without hurting Windows? My original partitioning sucks (all unallocated space is AFTER everything else, so I can't increase Windows, which my family wants increased)
I've done some reading around the forums and alot of people have complained that reinstalling by deleting ubuntu partitions the reinstalling ubuntu with newly created partitions crashes the whole system and that is not a desired result. So how do I go about it?

---

### Post by r4ik on 2007-08-28
-

---

### Post by oilchangeguy on 2007-08-28
> **ebony_rogue said:**
> I've installed Dapper but as dual boot with XP on the same hard disk, but, first I'll share my frustrations:

I have been trying for weeks to upgrade from Dapper to Edgy, but with no success, see my earlier post here: [http://ubuntuforums.org/showthread.php?t=460764](http://ubuntuforums.org/showthread.php?t=460764)

No one gave me anything that worked so I gave up. Then my screen resolution changed (I'm assuming all by itself because I certainly don't know how to change it!). So I asked for help in forums again but nothing I was given worked. 

So now I'm sick of asking around in forums (see why we like Windows?) and feel like I'm about to give up on ubuntu.

So I now have two other questions, apart from the ones above because no-one's helped yet:
1: How to un-install ubuntu so I can get back to windows, (I don't have the XP installation cd that was used to install it on my PC, I didn't do the installation) I don't have a back up of the MBR-whatever that is and I certainly don't want to loose my work and sart all over agin.

2: So I'll admit ubuntu is kinda cool so I won't gie up just yet, is there a way I can re-install it without hurting Windows? My original partitioning sucks (all unallocated space is AFTER everything else, so I can't increase Windows, which my family wants increased)
I've done some reading around the forums and alot of people have complained that reinstalling by deleting ubuntu partitions the reinstalling ubuntu with newly created partitions crashes the whole system and that is not a desired result. So how do I go about it?


there's nothing to be gained by going from 6.06 to 6.10. if it ain't broke, don't fix it. that being said, you're going to have problems, because you don't have a windows cd. you'll need this to repair windows master boot record. the easiest way to remove ubuntu is to (and i'm not sitting at a windows computer, so the steps may not be in order) go to start, control panel, computer management, disk management. locate the ubuntu partition and format it. you won't be able to add it back to the c: drive. but you can create another local drive. you can assign the drive letter of f: (if the picture of the f: drive in my computer, doesn't match that of the c: drive. change the drive letter, until it does). now go to [www.bootdisk.com](www.bootdisk.com) and create an xp boot disc. or just start fresh. reinstall 6.06 and allow it to use the entire drive, and do away with windows.

---

### Post by Daveth on 2007-08-28
whilst the "ain't broke" sentiment is a good one, feisty is nice. I waited a while with dapper before moving straight to  feisty. I would advise getting a live cd for feisty and do the upgrade that way. I'd skip edgy. You might want to explore Supergrub which also runs live and fixes windows as well as grub mbr problems and issues. This is a good place to start exploring:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you are re-partitioning windows you should certainly defrag the windows partitions beforehand. If you want to go with Ubuntu then GParted on a live cd with let you partition; I suggest you make a separate /home partition onto which all you data will then reside, keeping the system files entirely separate in case you need to re-install (or move to new versions). The only "breakage" you will get with dual boot is grub failures which stop you getting to the boot options, but this is easily resolved either with supergrub or a live cd.

There is lots on the forum about setting up the best partition options and how to do them. I think you have been a little unlucky as help is often most forthcoming. Don't give up!

---

