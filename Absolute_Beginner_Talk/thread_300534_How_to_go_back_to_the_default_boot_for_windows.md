---
title: "How to go back to the default boot for windows???"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by crashedoverride on 2006-11-15
Hi!i need ur help..i currently installed Ubuntu on my slave hard disk and my primary hard disk is a microsoft xp...and now its using GRUB as the booting device...and whenever i dont connect the slave drive, it still uses GRUB and windows cant boot.. when the slave drive isnt there..how can i restore the default boot for my windows??thanx

---

### Post by d3v1ant_0n3 on 2006-11-15
I'm guessing that when you installed Ubuntu, your primary (Windows) drive was plugged in. When the install wrote GRUB, it wrote it on the primary HDD.

You should be able to boot into windows by choosing Windows from the GRUB menu.

---

### Post by crashedoverride on 2006-11-15
yeah it was!...and yes i could choose to where i want to boot..but i need to go back to the default boot of windows since the hd that i installed Ubuntu to is almost busted..it making sounds already..and if it gets busted i cant also use the windows os..since grub is the booting device it gives me an error..so how can i go back to the default boot??thanx very much..

---

### Post by confused57 on 2006-11-15
Here's how to restore your Windows mbr(you won't be able to boot Ubuntu, though):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

After you get your Windows mbr repaired, you might want to read over this option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

