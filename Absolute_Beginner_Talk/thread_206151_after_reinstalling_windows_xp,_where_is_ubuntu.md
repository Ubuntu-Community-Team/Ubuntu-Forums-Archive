---
title: "after reinstalling windows xp, where is ubuntu?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Heitor on 2006-06-29
Hello.

Thank's to a virus atack, I had to reinstall windows XP.
After reinstalling windows, ubuntu has disappeared.
Do I have to reinstall ubuntu? Is it hidden somewhere inside the hard disk? If yes, how can I bring it back?

Thank you!

---

### Post by Jagot on 2006-06-29
Windows has overwritten your master boot record, so it no longer allows you to choose Ubuntu using the bootloader GRUB.  Ubuntu is still there, but you need to restore GRUB to enable you to choose between Windows and Ubuntu again:

[http://ubuntuos.com/2006/03/howto-restore-grub](http://ubuntuos.com/2006/03/howto-restore-grub)

---

### Post by ovimunt on 2006-06-29
Ububtu is still there but....

When you install Win XP the MBR (Master Boot Record) is erased. It's in the MBR that the multiple boot manager GRUB resides and Win XP has wiped it out. In other words, the little program that gave you the choice of booting Ubuntu has been removed and Win XP has set itself as the only OS.

Well, this at least tells you what the problem is but unfortunately I don't know how to fix it.

---

### Post by njzillest on 2006-06-30
get the ubuntu installer disk (i did this with 5.05) and skip the installation and partitioning. 

Install the grub, and you will be set.

---

