---
title: "Grub modding"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Ubuntuud on 2006-04-10
How can I modify grub so that it autostarts Dapper and doesn't start my Breezy server install (needed it to get Grub, something seriously wrong with Espresso). Thanks in advance!

---

### Post by waster on 2006-04-10
look in /boot/grub/menu.lst

you will see a block for each OS in the last section. You can either shuffle their order, or set the "default" param (I think) to point to the number you want, numbered from 0, I think.

---

### Post by Ubuntuud on 2006-04-10
OK. Thanks!

EDIT: It isn't that easy, isn't there. Guess I have to do it in nano in Breezy...

---

