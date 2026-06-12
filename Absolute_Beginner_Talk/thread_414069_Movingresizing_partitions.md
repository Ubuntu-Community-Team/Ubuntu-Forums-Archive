---
title: "Moving/resizing partitions"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-04-19
Is it possible to resize and/or move partitions (including the beginning) without messing GRUB up?

Acronis software for Windows can do it, but I've found GRUB gets confused, naturally. Thanks.

---

### Post by markitect on 2007-04-19
Grub works off the drive and partition number, so when you change the order of partitions or anything like that you need to change references in /boot/grub/menu.lst to match the new order.  for more info just google grub tutorial

---

### Post by ImpelGD on 2007-04-19
Okay... so as long as the partition order doesn't change, GRUB should be okay with Acronis software resizing the partitions?

Is there any Ubuntu/Linux software that does the same thing?

---

### Post by eyelessfade on 2007-04-19
gparted do the trick, or so I've been told. There is live cd of the program you can use. Just ask google where :)

---

