---
title: "uninstalling ubuntu off 2nd hard drive"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by aliencds on 2006-02-28
i have tried doing a search but its isnt working quite right for some reason. I have ubuntu installed on my 2nd hard drive and xp on my primary. What would be the easiest way to remove ubuntu. Should i just delete the partition in the compter management in xp and then run a fixmbr or because its on the 2nd hard drive is grub on the 2nd hard drive so there would be no need to run a fixmbr?

---

### Post by ajgreeny on 2006-02-28
If you delete the ubuntu partition on drive 2 you will remove the menu.lst file in boot/grub  You will then get an error message when you boot unless you run fixmbr first.

---

