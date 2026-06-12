---
title: "Dual Boot Order"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-05-14
Folks

Did this before (I upgraded to 7.04) and have to do it again (as I have forgotten). I want my dual boot to default to XP. What is the file I have to edit. Many Thanks.

---

### Post by icechen1 on 2007-05-14
/boot/grub/menu.lst

---

### Post by Duck2006 on 2007-05-14
Then change 

default		0

to

default		2

I think it will be change to

---

### Post by linuxforrealpeople on 2007-05-14
And how do I edit the file - I seem to be opening it in read-only mode? Thanks.

---

### Post by Milt888 on 2007-05-14
You can save yourself a lot of trouble by installing GrubEd. Solves OS booting problems.
I highly recommend it.
Just do a forum search.

---

### Post by Duck2006 on 2007-05-14
sudo gedit /boot/grub/menu.lst

Edit and save then close and reboot to see if it's what you want.

---

### Post by linuxforrealpeople on 2007-05-14
Excelent, Thanks

---

