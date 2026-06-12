---
title: "booting menu on kubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-24
just installed kubuntu, i'm running windows vista on another partition... can anyone tell me how to get the booting options back on so i can still boot into vista if i want to?

at the moment the computer loads straight into kubuntu

---

### Post by manuleka on 2007-06-24
now i restarted my computer and pressed excape when kubuntu was about to load (grub) and the boot options comes up, windows vista isn't there????

how do i enable vista to be on the boot options? do i edit grub menu.list??? 

help please!

---

### Post by overdrank on 2007-06-24
> **manuleka said:**
> now i restarted my computer and pressed excape when kubuntu was about to load (grub) and the boot options comes up, windows vista isn't there????

how do i enable vista to be on the boot options? do i edit grub menu.list??? 

help please!

Hi I just have to ask, are you sure that you left the vista partition intact?

---

### Post by manuleka on 2007-06-24
yes! i can see the vista and recovery partitions from kubuntu...

i shrinked the main vista partition and reboot, installing kubuntu to the available free space

---

### Post by Clay_Banger on 2007-06-24
open the terminal and type:
```
kdesu kate /boot/grub/menu.lst
```
then copy this into the bottom of the file, changing "hd0,1" to what ever partition/drive vista is on.
```
title Windows Vista
root (hd0,1)
makeactive
chainloader +1
```
save & exit, you should be able to boot into vista at the grub menu now..

---

