---
title: "possible newby stuff"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by jdh102680 on 2008-01-06
I have had a windows install get damaged. I am trying to recover the data so i can format and reinstall. I have tried xp recovery console, numerous live cd's (including knoppix, ubuntu, and bartpe). the problem I am having is: the live cds will not recognize the hard drive on the system. it is recognized in the bios, so I know it is working. please help me, or point me in the right direction.

:confused::confused::confused::confused::confused:

---

### Post by bumanie on 2008-01-06
Try test disk. It is an open source partition/data recovery program. It may help.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by llamakc on 2008-01-06
TestDisk should be on the Knoppix LiveCD.

---

### Post by jdh102680 on 2008-01-06
do ubuntu and knoppix work w/ sata drives, or do they need drivers (like win xp)?

---

### Post by llamakc on 2008-01-06
> **jdh102680 said:**
> do ubuntu and knoppix work w/ sata drives, or do they need drivers (like win xp)?

Yes they work very well.

---

### Post by jdh102680 on 2008-01-06
i think this may be a mounting issue. is there a "device manager like" program in knoppix that i can use to get the address of the hard drive, or would the bios address be the correct one to use?

---

### Post by philinux on 2008-01-06
Boot the ubuntu live cd, open a terminal and post the output of

[FONT="Times New Roman"]```
sudo fdisk -l
```[/FONT]

---

