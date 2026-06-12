---
title: "out of space, partition question"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by walker_aj on 2008-03-20
i have been playing with linux for 2 weeks and have run out of space wanting to install kde, 

The 1st partition on the disk is Win NT and NTFS which I now want to trash/convert for linux use,
 
I have been reading up but because this partition is before and not after I dont think it is possible/easy?

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         783     6289416    7  HPFS/NTFS
/dev/sda2   *         784        1216     3478072+  83  Linux
/dev/sda3            1217        1244      224910    5  Extended
/dev/sda5            1217        1244      224878+  82  Linux swap / Solaris

Any suggestions? or start again.  I'm sure I selected 'use the complete disk on installation',

---

### Post by uberlube on 2008-03-20
format that partition to ext3 and then mount it so you can store files on it.

---

### Post by uberlube on 2008-03-20
sorry, i didnt read that you wanted to install KDE. Grab partedmagic from their website (just google) and then burn it to disk and boot it. Then delete the NTFS partition and resize your ubuntu partition with the extra space.

---

### Post by walker_aj on 2008-03-20
sounds straight forward, I will give it a try.

thanks

---

### Post by billgoldberg on 2008-03-20
I would use the[ gparted]("http://gparted.sourceforge.net/") *(gnome partition manager)* live cd to format the drives to ext3 *(and maybe making one big partition out of them again, or use a partition for the /home folder**)*.

And if you are going to use kde anyway, you might as well download, burn and install kubuntu instead of ubuntu. So your system will be less polluted with gnome programs.

---

