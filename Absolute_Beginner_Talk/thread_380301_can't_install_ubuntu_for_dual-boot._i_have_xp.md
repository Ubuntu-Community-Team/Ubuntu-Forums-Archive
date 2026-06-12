---
title: "can't install ubuntu for dual-boot. i have xp"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-03-09
i don't have the option to resize the partition.
when i select manually edit partition table, the partition is an "unknown filesystem"

---

### Post by Kateikyoushi on 2007-03-09
I would recommend to give the gparted live cd a try. [LINK]("http://gparted.sourceforge.net/livecd.php")
Run a checkdisk from windows and defragment it few times before you try to resize it.

Also give us the output of this command from the live cd, copy paste it to applications > system tools > terminal.

```
fdisk -l
```

---

