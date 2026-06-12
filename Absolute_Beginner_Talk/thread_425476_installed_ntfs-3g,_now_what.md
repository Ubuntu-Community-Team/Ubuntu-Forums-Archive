---
title: "installed ntfs-3g, now what?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-04-27
how do i mount the 2 ntfs partitions i have? they are /media/hda1 (C:) and /media/hda5 (D:)

and how do i make it mount on boot (automatically)

---

### Post by starcraft.man on 2007-04-27
I believe your looking for this... [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows")

---

### Post by supersonicdarky on 2007-04-27
what i was looking for is a few lines down
" How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access"

i forgot to mention that i wanted to be able to write. ntfs-config helped =]

---

### Post by whee on 2007-04-27
After you installed ntfs-3g go to applications>tools>ntfs configuration tool
There you can check which type of ntfs drives(internal/external) should be mounted.
Ubuntu/ntfs configuration tool remembers the settings after reboot if i'm not mistaking.

---

