---
title: "create ntfs partition"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by robbie carrobie on 2007-05-07
how can i create an ntfs partition so that i can load xp as well as Ubuntu, i feel like i am hassling this forum but i really wanna learn - kind regards Robert.

---

### Post by alienexplorers on 2007-05-07
First thing, If you load XP after windows you will overwrite the MBR and will only be able to boot windows xp.  You have to reload grub to allow dual booting.

If you have free space on your drive (empty partition or unformatted space) then you can just load windows and have it create the ntfs partition.

---

