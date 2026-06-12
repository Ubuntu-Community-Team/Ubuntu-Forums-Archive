---
title: "booting a raid with grub"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by LESINTHELOFT on 2007-10-28
i have xp setup on a raid 0 
linux is on a separate drive.
If i set to boot off my raid array then xp boots fine.
If i set to boot off my thirsd drive then ubuntu boots fine.
How do I get grub to boot XP so i dont keep having to change my boot device

---

### Post by confused57 on 2007-10-28
> **LESINTHELOFT said:**
> i have xp setup on a raid 0 
linux is on a separate drive.
If i set to boot off my raid array then xp boots fine.
If i set to boot off my thirsd drive then ubuntu boots fine.
How do I get grub to boot XP so i dont keep having to change my boot device
You could try the Windows entry suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
You might want to add the entry to the very end of your menu.lst, instead of above the line ###BEGIN AUTOMAGIC KERNELS LIST...

---

