---
title: "grub bootloader is messy"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by radiantarchon on 2007-08-05
i don't want to to boot up into multiple kernals but it gives me like 6 choices. 3 being backups

like

2.6.20-15
2.6.20-20
2.6.22-9

plus some memtestx86
and something i don't remember

how do i edit this. it just looks messy

---

### Post by joe.turion64x2 on 2007-08-05
Open a terminal and type:

sudo gedit /boot/grub/menu.lst

That will open it for you.
You can either delete lines (just be careful) or comment them (with a # at the beginning of the line).

Joe.

---

