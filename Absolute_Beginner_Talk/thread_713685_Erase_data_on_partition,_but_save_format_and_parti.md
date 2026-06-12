---
title: "Erase data on partition, but save format and partition"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Jre35 on 2008-03-03
Hey, I have a dual boot between XP and Ubuntu. I recently upgraded to XP pro. I forgot that it would change the boot record and ignore Ubuntu in the boot menu. Anyways, The installation didn't work right. I want to erase all the data on the windows partition, but save the formatting and the partition itself, so I can just reinstall windows. Is it possible to do that, or would just deleting the partition and recreating it, then reinstalling windows be the best route, and secondly, if I do erase the data (and subsequently windows) will linux then become the default boot OS, or would my computer not find Ubuntu since grub was erased as well as the windows boot.ini file?

---

### Post by Gepetto on 2008-03-03
Reformatting the windows partition and reinstalling it would be the best route, IMO.

When you do erase Windows, you have to make sure that Ubuntu is the boot partition, else you'll get a cool error that says "Boot Sector Not Found" or something along those lines. In which case, just boot into Gparted and marke your Ubuntu partition the boot one.

---

### Post by bodhi.zazen on 2008-03-03
+1 on re-installing windows.

After installing Windows you need to restore grub, see this link :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

