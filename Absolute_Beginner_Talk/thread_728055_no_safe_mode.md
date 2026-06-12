---
title: "no safe mode"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-18
i have windows xp and ubuntu 7.10 both installed on my PC.during the startup,when the computer boots,the grub loads,and i can't get xp in safe mode despite repeatedly pressing F8.even after choosing xp as the OS ,i don't get the safe mode for xpeven on continuing to press F8.it has been so since i installed ubuntu7.10.how can i get into the xp safe mode.before installing ubuntu,merely by pressing F8 during booting used to get the job done.

---

### Post by philinux on 2008-03-18
You need to be really quick pressing the F8 repeatedly!

---

### Post by sub2007 on 2008-03-18
I *think* that you have to select Windows XP on the Grub screen and then immediately after you press enter to select Windows start pressing F8. 

It won't work if you press it before Grub because it's still in BIOS, just like it doesn't work with the Windows bootloader until the bootloader kicks in (after it says "Boot from CD").

---

