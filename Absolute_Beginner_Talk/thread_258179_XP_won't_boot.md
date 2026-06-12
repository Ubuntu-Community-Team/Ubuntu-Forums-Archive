---
title: "XP won't boot"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Jouhou on 2006-09-15
I installed Ubuntu a couple days ago, did the automatic partition thing, and got it up and running (yay). Unfortunately, when I try to boot xp, grub just displays the following:

Microsoft Windows XP Home Edition

root		(hd0,0)
   filesystem unkown, partition type 0x7
savedefault
makeactive
chainloader	+1

I've looked through other threads and tried adding 'boot' to the bottom of menu.lst, but grub just adds the word boot to the bottom of the printout. I've also tried using supergrub, but when i go to boot windows i get a similar result.

I'm able to mount the windows ntfs partition, so I'm hoping not all hope is lost. Here's what fdisk gives me:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4556    36596038+   7  HPFS/NTFS
/dev/hda2            4557        7180    21077280   83  Linux
/dev/hda3            7181        7296      931770    5  Extended
/dev/hda5            7181        7296      931738+  82  Linux swap / Solaris

Is there anyway for me to boot windows or do I have to reinstall?

---

### Post by Orbit45244 on 2006-09-15
You basically have no options except deleting Windows and installing Windows again.  I had the same problem, and there are no other options except this one because the Repair Console and the System Repair options on the Windows install CD are useless and don't work.  You are getting this error because you've messed up your core Windows files somehow by repartitioning.  In the future, don't use a partition tool outside of Windows to repartition.

---

### Post by mikewright on 2006-09-15
Please explain:
In the future, don't use a partition tool outside of Windows to repartition.

What partitioning software works from within windows?

I had the same problem when installing Ubuntu last weekend, and I ended up doing a hard drive wipe, and going with a sole OS... It's a little irritating to do a dual boot so you can give a new OS a try, only to have it blow away the other one!

I used "partition magic" rather than fdisk, but i seem to recall that it won't run in windows if you try and repartition the system drive.

---

### Post by confused57 on 2006-09-15
Instead of root (hd0,0), replace it with:
```
rootnoverify (hd0,0)
```

sometimes rootnoverify works, when just root doesn't...

---

