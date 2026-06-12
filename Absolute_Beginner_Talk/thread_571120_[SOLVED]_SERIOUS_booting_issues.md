---
title: "[SOLVED] SERIOUS booting issues"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by razgriz413 on 2007-10-08
Hey guys!
Sorry my first post has to be about an issue I am having with Ubuntu. I have been running Ubuntu 7.04 in a dual-boot Toshiba Satellite M55 laptop since June, and so far it had been fairly smooth sailing. Every once in a while during booting, Ubuntu would start a forced check. This forced check would complete, but its frequency increased slightly before coming to the point I am now. Right now, not a single version (either normal or safe) will boot properly because during this forced check, Ubuntu declares that an error has been found (getting a zero value when it expected a nine-or-so digit string. After looping through what I can only assume to be different parts of the partition, it asks me to log in as root to do manual maintenance to fsck. I have no idea how to do this. After rearranging the boot order on my BIOS, I have tried to boot a new live CD iso, but to no avail. Just to try, I downloaded and burned a repartitioning tool for Linux which boots at startup, but this does not work either. It seems like the system tries to load from the CD first, but it doesn't load anything and moves on to the hard drive.

At this point, I have run out of ideas, and I apologize in advance for the lack of more specific details. At the very least, I'd like to be able to recover a few important (sentimentally, i guess) files that were not part of my back-up when I initially added Ubuntu, and bring them to Windows, where I can burn them. My knowledge on terminal commands is minimal. Most of my stuff is in folders on the desktop, and I know the folder names. I truly appreciate any help I can get. I am ready to repartition from Windows using RepatitionMagic 7.0, but I'd like to salvage what I can before finding myself being forced to delete my Ubuntu partition. I can try to dig up specifics upon request.

Thanks, everyone
-Razgriz

---

### Post by greenstar on 2007-10-09
Run Memtest and see if your RAM passes. It's available from the boot menu or on the live CD.

Greenstar

---

### Post by HW_Hack on 2007-10-09
I think you need to break things down a bit and verify whats working - whats not.  And don't feel bad ....  goofy - crazy - bad stuff happens to all of us 

First off - if your laptop is still booting the XP partition and running fine then the problem is not with your memory (most likely --- Unix / Linux is more demanding than XP etc.) - so if you laptop is still booting XP thats good. And most likley you either had some nasty file corruption occuring in the Linux partition - or your disk is starting to fail. Either way - you should back-up anything of value on the XP partition before proceeding !!!!

If your laptop is not booting anything - hopefully you have a bootable XP CDROM ..... booting the XP CDROM is a good general test of your PC and you can exit at any time. 

Hopefully someone here can help you - but at the same time you have one of the best debugging tools always ready  ---- google          try a google on    ubuntu manual maintenance fsck     or linux maintenance   etc.

---

### Post by razgriz413 on 2007-10-09
fortunately, I can still boot windows just fine, and I ran the memtest just for the heck of it, and it passed.

---

### Post by philinux on 2007-10-09
when it says run fsck manually it means just that 

type fsck /dev/hd?? wherever your ubuntu file partion lives

---

### Post by razgriz413 on 2007-10-10
during fsck, I get a cycle that looks like this:

ta 4096 in
[  999.9nnnn (this section varies per cycle)] ata1.00: SET of native returned 0. expected 234441648


finally,
[999.nnnn] Buffer I/O error on device sda2, logical block 14639619
Error reading block (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 7307415

---

### Post by razgriz413 on 2007-10-10
thanks, phil! I was able to fix the problem. Apparently a lot of values got corrupted, but it seems that they have been corrected now.
Again, thanks for the help!
-razgriz

---

### Post by greenstar on 2007-10-11
> **razgriz413 said:**
> thanks, phil! I was able to fix the problem. Apparently a lot of values got corrupted, but it seems that they have been corrected now.
Again, thanks for the help!
-razgriz

Please mark this thread as [SOLVED], so that others may benefit from this solution also. See my signature for instructions.

Thanks,
Greenstar

---

### Post by razgriz413 on 2007-10-13
done

---

