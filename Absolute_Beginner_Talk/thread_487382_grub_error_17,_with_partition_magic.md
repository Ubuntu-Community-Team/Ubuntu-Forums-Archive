---
title: "grub error 17, with partition magic"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mister_g on 2007-06-29
I just did a new install of XP and ubuntu. both booted up normally. i installed partition magic 8 and wanted to resize the ext3 partition used by linux; it was much to big. I guess I should only do this in linux? anyway, I wasn't allows to, so I just reformatted my applications partition (NTFS) prior to reinstalling all my programs. Rebooted and now I get this GRUB error 17. Anyone else experience this?

sorry but I'm a total newbie to all this

---

### Post by mister_g on 2007-06-29
ok I just went ahead and reinstalled ubuntu, but now it appears I have two separate installed versions? getting confused with all this. I want to delete the first one, which I presume has problems from GRUB and my messing with the partitions in partition magic in xp. How do I uninstall the previous ubuntu from the version that running right now.

---

### Post by alienexplorers on 2007-06-29
You could boot off your live-cd and run terminal.  Type sudo gparted.  Delete the unwanted partition and risoze the one you want.  Not positive this will work, but I would give it a try.

---

