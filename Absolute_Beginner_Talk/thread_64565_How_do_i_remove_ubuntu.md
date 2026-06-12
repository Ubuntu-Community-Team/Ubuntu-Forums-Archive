---
title: "How do i remove ubuntu"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by Lateralus on 2005-09-11
I have a computer with 2 hdd's. 1 with XP and the other with ubuntu on it and I would like to remove ubuntu from the second hdd and make that second hdd my d drive again in XP. HOw do I do this?

---

### Post by Leif on 2005-09-11
if you installed a bootloader (ie grub) and want to remove it, start your computer using the xp install disc, choose repair, and at the command prompt type fixmbr. then, choose the disk manager in windows, delete the ubuntu drive and create a new one.

sorry for any inaccuracies, but I haven't used xp for a long time, and I've never removed ubuntu.

---

### Post by Lateralus on 2005-09-11
[QUOTE=Leif]

sorry for any inaccuracies, but I haven't used xp for a long time, and I've never removed ubuntu.[/QUOTE]
That no prob I'm just taking ubuntu off of this computer and putting it on anther one. After I remove grub will I be able to acess the second hdd via the D: drive from XP?

---

### Post by Leif on 2005-09-11
no, you will only be able to access d: once you've created it.

---

