---
title: "MBR / Grub Error"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-01-07
I tried running FreeBSD and it wrote a boot loader to MBR.  I did not like it and removed it from my system.  It left in the MBR a boot loader that I have to first hit F1 then the grub loader loads.  How do I rid myself of this MBR press F1 to load crap.

---

### Post by ajmorris on 2007-01-07
Re-wrtie GRUB to the MBR. To do this go into a command line and type [PHP]sudo grub.[/PHP] type root (hd"hard disk number",partition number) hit return. then type setup hd0 hit return. If you don't know your hard drive and partition number there is a command "find ..../stage1" but i don't remember where to look for stage1. I think it is /boot/grub/stage1 but i am not sure.

---

### Post by alienexplorers on 2007-01-07
Thanks for the help.  Got rid of the F1 prompt.  Boots normally into the grub loader.

---

