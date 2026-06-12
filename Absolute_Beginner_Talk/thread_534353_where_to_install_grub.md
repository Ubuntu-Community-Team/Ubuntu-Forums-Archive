---
title: "where to install grub ?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2007-08-25
HI friends,

   Here is a view of my partition table.

#1 primary 21.0 GB B K   FAT32 /media/sda1
#5 logical 21.0 GB B     FAT32 /media/sda5

I'm planning dual-boot :  Win XP in #1, ubuntu in #5.

I dont know where to install GRUB; whether in MBR (i.e. #1 primary) or in the partition containing "/" (root) directory (i.e. in #5 logical) ?

---

### Post by bme on 2007-08-25
No harm in selecting the default-usually (hd0) when installing ubuntu. windows will automatically be included in the grub menu....be it vista or xp or even 98.

---

### Post by nosrednaekim on 2007-08-25
like bme said, put it on the MBR, everything is easier that way.

---

### Post by por100pre1 on 2007-08-25
You're using xp, so your best bet would be to put it in MBR. :)

---

### Post by alienexplorers on 2007-08-25
I just let Ubuntu install it to the default location on my first hard drive.  It over wrote the MBR, but since it works who cares.

---

