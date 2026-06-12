---
title: "Grub Error 15 Stage 1.5 after install Mythbuntu"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by mike struc on 2008-04-14
I started this mess by screwing around in partition magic and trying to transfer partitions from one hard drive to another. Anyway I installed Mythbuntu no problems and was going fine until the part where you have to restart. When I restart it it says Grub stage 1.5 drops a couple lines and says Error 15. I searched around but can't find any answers. I have messed around for hours on the super grub disc with no success. I remember something in partition magic something about an active partition but I tried to activate my root partition and I still get the same error. Any ideas?

---

### Post by bumanie on 2008-04-14
Have you got any idea what operating system you have on which hard drive and as to what partition you have the OSes on? Would it be possible to to post a screenshot of your partitions via a live ubuntu cd or from gparted cd? By changing your partitions with partition magic, grub is probably looking at the wrong partition. If you boot from a live ubuntu cd, could you try command > sudo fdisk -l in terminal (can't remember if this works off a live cd) and post the output (if any).

---

### Post by mike struc on 2008-04-14
Using that command
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

I deleted the windows and linux that were on my first drive and installed this linux over entire disc. The second drive only has media and docs on it so I disconnected it to make super grub disc easier. Which it didn't.

---

### Post by bumanie on 2008-04-14
Try booting with live cd and in terminal type > sudo grub > root (hd0,0)>  setup (hd0) > quit  Try to reboot and if that doesn't work:
Could you go to Places --> Computer --> and double click file system. Then double click boot folder, then double click the grub folder and open the text document menu.lst and post it.

---

