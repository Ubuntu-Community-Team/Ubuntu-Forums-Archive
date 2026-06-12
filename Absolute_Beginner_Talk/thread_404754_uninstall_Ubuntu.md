---
title: "uninstall Ubuntu"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by shantz24 on 2007-04-08
Hi, I am looking to uninstall ubuntu from my laptop because the support just isnt there for it.  I am planning on trying a future release of it but for now i guess its going to be vista.  I was just wondering how i should go about unisntalling ubuntu so it will just boot into vista instead of going through grub to get there.  I am probably leaving my partitions there for a future attempt since i have plenty or hard drive space left on my windows partition.  any help would be great and dont think im completely leaving ubuntu, it is on my desktop and i love every moment i spend with it.:)

---

### Post by trent dillman on 2007-04-08
Use your restore cd/partition to rescue windows (reinstall the bootloader).
Then you can reformat the drives in windows through the control panel somewhere.

---

### Post by mac.ryan on 2007-04-08
Assuming windows was installed first on your computer (before ubuntu), you have to restore your MBR (master boot record) to its original status.

You can achieve this under XP (for sure with the installation CD, and maybe even from the installed version of it) through the program "[fixmbr.exe]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")". There are ways to accomplish the same via the ubuntu liveCD, but I honestly don't know the how-to.

---

