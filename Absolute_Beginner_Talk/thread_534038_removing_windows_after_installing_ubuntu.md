---
title: "removing windows after installing ubuntu"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by faultedperfection on 2007-08-24
Okay, I installed ubuntu, and have XP dual boot...now i want to totally get rid of XP, and use just ubuntu, so I was wondering if I format the xp disk, will I loose grub, and if I do, can I reinstal it without reinstalling ubuntu...

Basically I want to get rid of windows, and use the spare HD for space on ubuntu...?

Any help would be appreciated thanks

---

### Post by Tyke91 on 2007-08-24
grub is on your MBR, so formatting windows will not do anything...

simply destroy your windows partition and grow ubuntu into it :D

---

### Post by wormser on 2007-08-24
Also, you should delete the entry for Windows in Grub.  

```
sudo nano /boot/grub/menu.lst
```

---

### Post by bernied on 2007-08-24
> **Tyke91 said:**
> grub is on your MBR, so formatting windows will not do anything...

simply destroy your windows partition and grow ubuntu into it :D
But the OP said 'format the xp disk' which might just destroy the mbr, depending on what is meant by 'format'.

You can remove everything from the Windows partition(s) and/or repartition the disk, but beware that your system is still booting from the windows disk, so if you were to remove it, ubuntu would no longer start.

---

### Post by p_quarles on 2007-08-24
> **bernied said:**
> But the OP said 'format the xp disk' which might just destroy the mbr, depending on what is meant by 'format'.

You can remove everything from the Windows partition(s) and/or repartition the disk, but beware that your system is still booting from the windows disk, so if you were to remove it, ubuntu would no longer start.
True, but it's relatively simple to use the Ubuntu installation disk to reinstall GRUB. 

That said, it's *always *a good idea to back up everything the least bit sensitive before doing any partition table editing.

---

### Post by faultedperfection on 2007-08-24
If and when I do format the xp drive, and I loose the MBR, I should be able to reinstall the MBR with the live disk right?

---

### Post by faultedperfection on 2007-08-24
> **faultedperfection said:**
> If and when I do format the xp drive, and I loose the MBR, I should be able to reinstall the MBR with the live disk right?

Sorry...you answered my question before I got done posting...

---

