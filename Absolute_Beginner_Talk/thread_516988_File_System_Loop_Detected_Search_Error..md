---
title: "File System Loop Detected: Search Error."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-08-03
Hello All,

Have given up on Mondo/Feisty fixes so I recently completed a Fresh Install after crashing my system trying to create a partition for data so I can try PartImage again. It took awhile before I got to Search because there were so many things to do to get my system back to where it was. Still not there. My original Fresh Install was Dapper followed by Upgrades to Edgy and Feisty with no problems.

When I did my first search on the Filesystem I received: "The search results may be invalid. There were errors while performing this search" followed by these Details. Find: Filesystem loop detected; '/media/hda2' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.

If in Search I select Other>Filesystem>media>hda2 and press Open it works with no problems or warnings.

1) Places>Computer shows Filesystem and hda1 (XP) but not hda2 (Ubuntu).
2) Desktop has icon for hda1 but not hda2.
3) Places>Computer>Filesystem>media> shows hda1 and hda2.
3) Search shows Filesystem and hda1 but not hda2.

I have installed Beagle and Catfish as backup but would like very much to correct the problem causing the search error.

Attached are 4 screenshots I hope will give you something to work with.

Thanks for your time.


Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 notebook w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge [IGP 340M].

---

### Post by meierfra on 2007-08-03
All you need to do:  


```
gksudo gedit /etc/fstab  
```

and remove the line

/dev/hda2   /media/hda2  ext3  defaults 0 0 

Save the file and  reboot.

---

### Post by ityro on 2007-08-03
meierfra,

Thanks for your response. I will follow your instructions asap and get back to you as soon as the forums let me sign-in with less than 10 tries.

Thanks again.

---

### Post by ityro on 2007-08-04
meierfra,

Amazing!  I made the change you recommended, then ran fsck using "Check Disks and Halt", then started the system and tested Search 5X using the Filesystem as the "Look in folder" with no problems or warnings of any king.

I can't thank you enough, thought I had a real problem. Hope I can repay you by helping someone else with a problem I know how to solve.

Thanks Again.

---

