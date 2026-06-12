---
title: "[SOLVED] re install of 7.04"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rlj999 on 2007-10-24
I'm about to try a reinstall of 7.04  on my laptop  -currently running xp-7.04 -- having a great deal of trouble w/all internet connections  and feel a reinstall might help  -- my current partitions are listed below.

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1        9334    74975323+   b  W95 FAT32 
/dev/sdb2   *        9335        9975     5148832+  83  Linux 
/dev/sdb3            9976       10011      289170    5  Extended 
/dev/sdb5            9976       10011      289138+  82  Linux swap / Solaris 

robert@robert-laptop:~$ 


XP shows7GB  free -- but feel that I should delete the above listed Linux/extended/Linux swap partitions.
checking some earlier posts it appears that 7.04 does not automatically overwrite.

Can some one give me exact steps to follow  so I can get this done  I am not at all sure as to how to delete the Linux files  

Robert

7.04 on Toshiba Laptop

---

### Post by logos34 on 2007-10-24
You don't need to delete anything--just reinstall using the same / and /swap...it will format them beforehand.

---

### Post by mikewhatever on 2007-10-24
Please review the following thread [http://ubuntuforums.org/showthread.php?t=589718](http://ubuntuforums.org/showthread.php?t=589718)
You do not have to delete any of the partitions, if you are happy with their present setup.

---

### Post by rlj999 on 2007-10-25
Thank you --worked like a charm --wireless ok -XP / 7.04 Feisty all happening 

Robert

---

