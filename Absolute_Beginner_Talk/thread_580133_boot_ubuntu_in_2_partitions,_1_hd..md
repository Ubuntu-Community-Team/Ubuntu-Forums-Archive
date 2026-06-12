---
title: "boot ubuntu in 2 partitions, 1 hd."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by BlueNosE on 2007-10-18
hello,
in the moment i have 1HDD with 160GB: 120 of them for windows and the rest of them for linux.
the problem is that the last time i tried to install ubuntu on the small partition (40GB), the content on the bigger one just disappered with the windows and i had to format windows again.

my question - can i install ubuntu on 2 partitions on 1 hard disk?
and if so, how? by the manual installation?

thank u!

---

### Post by Pumalite on 2007-10-18
Vista or XP?

---

### Post by BlueNosE on 2007-10-18
oh XP.

---

### Post by Pumalite on 2007-10-18
Defrag several times, erase all temp files. Get Gparted Live CD. Boot from it. Resize XP partition, then install Ubuntu.

---

### Post by BlueNosE on 2007-10-18
Resize XP partition - why?
and again - how? by manual installation?

thank you for the fast replies.

---

### Post by Hobo Joe on 2007-10-18
> **BlueNosE said:**
> Resize XP partition - why?
and again - how? by manual installation?

thank you for the fast replies.

If you already have a separate partition, don't worry about it. 

Also the LiveCD has Gparted(at least, it did on the Feisty install, I didn't check on this disk) on it, so no need to get the Gparted disk.

Just install Ubuntu from the LiveCD like you normally would.

---

### Post by BlueNosE on 2007-10-18
look, i followed an installation guide which tells me about automatic Gparted installation - i couldn't find it so i went to the manual one.
do you have a screenshot for me? i just cant understand where is the Gparted installation.

---

### Post by Pumalite on 2007-10-18
Manual is better.

---

### Post by BlueNosE on 2007-10-18
ok,
1. go to the live cd
2. go to manual installation
3. choose the right partitions (1 for os, 1 for swap)

that wont delete anything, right?

---

### Post by Pumalite on 2007-10-18
It will reformat only the partitions you choose.

---

### Post by BlueNosE on 2007-10-18
ok ill try it
tyvm =)

---

### Post by BlueNosE on 2007-10-19
oh crap.
i have system crushes, and now i just found why.

the hard disk makes crushes while installing, playing, etc.

now, if i will install ubuntu on another HD without the first HD connected, grub will identify the first HD after installing it on the second one? (i mean, 1. unplug the first HD with windows XP, 2. install ubuntu on second HD, 3. plug the first HD with windows XP to make dual boot)

---

