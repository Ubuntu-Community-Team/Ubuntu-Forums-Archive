---
title: "Macbook Lion Triple Boot Ubuntu 11.04"
date: 2011-08-11
forum: Apple Hardware Users
---

### Post by jettechfsr on 2011-08-11
[FONT=Arial][SIZE=2][COLOR=Black]OH boy Apple really messed up with the Lion upgrade for us multi-OS users this week has been crazy was able to keep MAC previous and got upgrade to go ok love the new interface but had to wipe Windows 7 and Ubuntu off and start over which was not so bad I have the new [/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][FONT=Arial][SIZE=2][COLOR=Black]Ubuntu 11.04[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] but have just one hang up I'm using ReFit and when I click the windows Icon it starts Grub2 and I can select Windows and it starts ok but would like to get back to the old way and have Windows start normal I tried to fix with the Windows CD but still have the same google'd about moving Grub2 but more confused now hope someone can help [/COLOR][/SIZE][/FONT]
[/COLOR][/FONT][/COLOR]

---

### Post by crook17 on 2011-08-13
refit scans the hdd for the installed os on each of the partition, i have found the best way to triple boot is to install grub to the Ubuntu partition and let Windows overwright the MBR (keeping it happy). so when refit scans the 1 partition it sees OSX another MS Windows and then  Linux, or vise verse. Hope this helps;)

---

### Post by Krim on 2011-08-15
You are right, Lion is now very particular - I just recently deleted my ubuntu partition and just made it a vm. Much easier to use and you don't have to deal with many of those issues.

---

### Post by cropr on 2011-11-03
> **crook17 said:**
> refit scans the hdd for the installed os on each of the partition, i have found the best way to triple boot is to install grub to the Ubuntu partition and let Windows overwright the MBR (keeping it happy). so when refit scans the 1 partition it sees OSX another MS Windows and then  Linux, or vise verse. Hope this helps;)

There is still an issue using refit, specific to Lion.  The number of MBR mapped partitions is limited to 4.  In a triple boot scenario Lion uses 5: EFI, MacOS, MacOS recovery, Windows and Linux.  Refit cannot cope with this during the gptsync.  Probably we can just remove the MacOS recovery, but I am not sure

---

### Post by viniciolindo on 2011-11-09
yes this resolve but the problem is that lion cannot install future update firmware

---

