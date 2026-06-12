---
title: "How to mount NTFS on Feisty?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-06-16
Help me guys the heading says ever thing plz help me in mounting NTFS on Ubuntu 7.04 . Plz tell me each way .. Help would be appreciated

**Output of sudo fdisk -l**

```
  **Device Boot      Start         End      Blocks   Id  System**
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        6949    45576405    f  W95 Ext'd (LBA)
/dev/sda3            6950        9728    22322317+  83  Linux
/dev/sda5            1276        3825    20482843+   b  W95 FAT32
/dev/sda6            3826        6757    23551258+   7  HPFS/NTFS
/dev/sda7            6758        6949     1542208+  82  Linux swap / Solaris
```

Regards plz be a bit quick am on trouble :p Thanks in advance ;):D

---

### Post by dpar on 2007-06-16
I can just go to Places>Computer and double click the volume you want to mount.

---

### Post by bren on 2007-06-16
and if you want to be able to write to the NTFS parition you must install this small utility

> sudo apt-get install ntfs-3g

bren

---

### Post by AlexenderReez on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount)

---

### Post by Dark Star on 2007-06-16
The problem is that 1 cannot caopy paste in NTFS hdd partition.. It says the hdd did not disagree with fstab :( Plz help I install NTFS driver from apt-get install ntfs-3g :) But ain't working :( I cannot paste anything in the dirves :(

---

### Post by AlexenderReez on 2007-06-16
> **Dark Star said:**
> The problem is that 1 cannot caopy paste in NTFS hdd partition.. It says the hdd did not disagree with fstab :( Plz help I install NTFS driver from apt-get install ntfs-3g :) But ain't working :( I cannot paste anything in the dirves :(

lol....follow my link!!!!

> [http://justfuckinggoogleit.com/](http://justfuckinggoogleit.com/)

---

### Post by Dark Star on 2007-06-16
PLz be be clear :S I am in problem :( which link ... :'( And 1 more thing is that I am only using Feisty no other OS :)

---

### Post by AlexenderReez on 2007-06-16
> **Dark Star said:**
> PLz be be clear :S I am in problem :( which link ... :'( And 1 more thing is that I am only using Feisty no other OS :)

> [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+mount)
sorry for being cruel....okay like this....we nned to hack ntfs file system to enable write in it.....that is all...follow that link how to....add repository list.....then...just reload...install ntfs-config.....open it...enable write support...that is all....by the way...it is already in that guide...just follow that all....
understand is better......good luck then....

---

### Post by e30ernest on 2007-06-16
Go to add/remove and search for "ntfs".  "You should see NTFS Configuration Tool".  Download and install it.

The tool you installed should be on your Applications>System Tools menu.  Open NTFS Configuration tool then check the boxes for both internal and external devices.  I hope this helps.

---

### Post by Dark Star on 2007-06-16
Finaaly did it thanks all :)

---

### Post by meborc on 2007-06-16
> **reez0105 said:**
> lol....follow my link!!!!

[http://justfuckinggoogleit.com/](http://justfuckinggoogleit.com/)

this is not tolerated in ubuntuforums! see point no 5 in beginner forum rules thread - [http://ubuntuforums.org/showthread.php?t=65842](http://ubuntuforums.org/showthread.php?t=65842)

this is the beginners forums... no "just google it" replies needed... if you don't want to help - DON'T... but respect the rules!

:) ok... end of my rant...

---

