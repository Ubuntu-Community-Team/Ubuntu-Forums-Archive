---
title: "no bootable device ?"
date: 2008-04-20
forum: Apple Intel Users
---

### Post by JMC_Rimmer on 2008-04-20
So I thought I would try to put the Hardy Heron release candidate on my Macbook Pro.  Install seemed to work fine.  rEFIt has an entry for Linux but when I select it, a black screen with "no bootable device -- insert boot disk and press any key" appears.  It's very strange because I installed Gutsy multiple times on this laptop and it always worked perfectly.

Any suggestions would be appreciated.

---

### Post by bluemoth on 2008-04-20
I got the same problem installing hardy. I ran the refit partition tool which ran some sync tool. It asked me something like "would you like to update you MBR table".

I have no experience with the refit partitioning tool, so run it at your own risk. Back up your data.

Let us know how you go.

---

### Post by cyberdork33 on 2008-04-20
looks like they may have regressed in the installer's partitioning... syncing the partition tables should be done by the installer, but you can use refit to do it.

---

### Post by JMC_Rimmer on 2008-04-21
> **cyberdork33 said:**
> looks like they may have regressed in the installer's partitioning... syncing the partition tables should be done by the installer, but you can use refit to do it.

Resyncing the tables (using the rEFIt partition manager) seemed to fix the issue... but only after I booted the Mac OS to remove the Ubuntu disk.  Not sure why this would matter but my problem seems to be solved.

---

### Post by bozhifan on 2008-04-22
I have the same problem,
but I still don't get the solution.

Would anyone please tell me how to fix my problem?

How to resyncing the tables?

---

### Post by cyberdork33 on 2008-04-22
> **bozhifan said:**
> I have the same problem,
but I still don't get the solution.

Would anyone please tell me how to fix my problem?

How to resyncing the tables?
install refit
reboot
in the refit menu, choose to start the partition tool

---

### Post by OleR on 2008-04-25
Hey, I have been having the same Problem, only that I also have a Windows XP installed on the last Partition of my Harddrive, which was not working either. I did the Rebuild of the MBR as described above and am actually able to boot Linux. However, whenever I try to boot Windows, it now tells me "Non System Disk" - whereas it was "No bootable device" before the syncing. Any ideas? Macbook Pro here as well. The Disksetup is

EFI           FAT32
MAC OS X      HFS+
KUBUNTU 8.04  EXT3
DATA          FAT32
WINDOW XP     NTFS

When I boot Linux, Grub comes up and offers me the choice to boot windows - which then gives me the <windows root>/system32/hal.dll not found or corrupted error.

---

### Post by cyberdork33 on 2008-04-25
> **OleR said:**
> When I boot Linux, Grub comes up and offers me the choice to boot windows - which then gives me the <windows root>/system32/hal.dll not found or corrupted error.
Even though you really didn't, it looks to windows like you changed the partition table which gives that error. Unfortunately there is no known fix.

---

### Post by ThatGuyThere on 2008-04-26
I had the same problem. When i went into rEFIt, and sycned the tables, it synced. I then tried to boot up linux (xubuntu, if that makes a difference). It just hangs there for a few mins. I force-rebooted a few times and tried again, with the same results. Should i wait longer or is there a fix?

---

### Post by cyberdork33 on 2008-04-26
> **ThatGuyThere said:**
> I had the same problem. When i went into rEFIt, and sycned the tables, it synced. I then tried to boot up linux (xubuntu, if that makes a difference). It just hangs there for a few mins. I force-rebooted a few times and tried again, with the same results. Should i wait longer or is there a fix?
there is another bug that causes a hang at the refit bootscreen. try holding Option on bootup and choosing the partition there.

PS there is a new Apple forum now. please try to keep posts there.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by ThatGuyThere on 2008-04-27
> **cyberdork33 said:**
> there is another bug that causes a hang at the refit bootscreen. try holding Option on bootup and choosing the partition there.

PS there is a new Apple forum now. please try to keep posts there.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

That worked, thanks :D

---

### Post by SiduSahib on 2008-04-28
well i had the same problem.
i installed ubuntu 8.4 on my macbook D2C
and also install refit program.
and when i boot ubuntu the msg says no bootable device... please insert a bootable disk and press any key.
i formated couple of times and tried again and again. same msg.

what i did.
you should do the same if havent solved the problem yet.
delete the rEFiT program folder from your drive.
restart ur mac, hold down the option key and choose windows thats ubuntu
it will reboot ubuntu. working fine.
it works for me.

---

### Post by cyberdork33 on 2008-04-28
please post in thew new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

