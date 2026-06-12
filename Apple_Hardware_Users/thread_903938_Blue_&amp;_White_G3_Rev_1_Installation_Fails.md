---
title: "Blue &amp; White G3 Rev 1 Installation Fails"
date: 2008-08-28
forum: Apple Hardware Users
---

### Post by heroes_on_a_half_shell on 2008-08-28
hey guys,

i took a break for a while but now i'm back at it again with my g3's.  i think i may have lucked up on the revision of g3's which -will not- take linux, but i'm still trying.  

this time, i've managed to get the firmware update from an os 9 cd. also, i can complete a command line installation w/ the 8.04.1 cd.

now, the problems:

-when i complete a cli, i cannot enter any sudo commands or else i receive a "Segmentation Fault" - so no graphical environment

-i cannot make it through a standard ubuntu install.  it -always- fails during the select and install software phase (the base system phase installs fine)

-i cannot get my 2006 manufactured date WD caviar 80 gb drives to format.  depending on how it feels, the installer tells me either that the filesystem failed to mount on my particular partition or that the hard drive failed to set to mac.  as a result i am using a questionably reliable 40 gb maxtor (it has a smart trip - but i really don't know what that means).

-partitioning -- i have been allowing the guided partitioner to create the partitions, the i go back and delete all but the first two partitions and create a 7 gb root partition and a 1.5 gb swap.  these partitions are formatted w/o hassle.  however, if i attempt to create a separate home directory with the remainder of the disk, this partition will invariably fail to mount the filesystem

any help would be appreciated as i am quite stuck

---

