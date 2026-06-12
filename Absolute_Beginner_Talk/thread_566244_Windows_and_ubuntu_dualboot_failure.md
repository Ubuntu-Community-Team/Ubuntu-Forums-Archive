---
title: "Windows and ubuntu dualboot failure"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Simplechat on 2007-10-03
Hey, i've installed ubuntu and windows xp. (set up and partitioned, how they are doesn't seem to matter, windows always bluescreens once ubuntu is installed).

Once i installed ubuntu, xp bluescreens once the loading bar starts. (which is a problem for me)

I then changed the partition table from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) this tutorial.

I then ran Fixmbr from the windows recovery console, and now my computer completely refuses to boot. 

I start my computer, bios comes up, once that stops, I get the message "No bootable media."

Ubuntu is version 7.0.4
Windows is xp, no service packs.
This is running on a single sata disk currently partitioned into three partitions: NTFS (100 gig), swap (4 gig) a spare 10 gig and root being the rest (100 gig i think). this is a 300 gig drive.

When ubuntu first started, it detected an error in its file system about 94% of its way through, it corrected it and restarted.

---

### Post by Terl on 2007-10-03
Are these fresh installs of each o/s?

How did you install exactly?  Usual method is windows first on first partition (windows needs to be first to keep it all simple-not just for Grub but also it likes to be "C drive" first partition of first disk-it can be tricked but easiest is to install it where it wants to be from the get-go).  Then install Ubuntu and allow Grub to be in the MBR of the drive.

---

### Post by weed-n-linux on 2007-10-03
Terl is right Windows should be installed before linux because if not so , Grub or Lilo(any boot utility) are going to be deleted by the beast ;)

---

### Post by Simplechat on 2007-10-03
These are fresh installs of each os.

Teri: i format a 80 gig partition with windows, and i then install ubuntu with the remaining space.

atm i've set up windows (which never seems to recognise its own partition anymore), and i'm going to set up ubuntu, but is there any way to get ubuntu to stop overwriting the mbr? (that seems to be the cause of windows's lockups).


Also: after using gparted to partition off 80 gig of space for windows (formatted ntfs) windows didn't recognise it, and ubuntu didn't boot. (after installing ubuntu).

---

