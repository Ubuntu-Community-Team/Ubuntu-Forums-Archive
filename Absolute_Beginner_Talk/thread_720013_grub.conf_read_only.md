---
title: "grub.conf read only?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by nocturnalsixer on 2008-03-09
I have a acer laptop so it means i have to hit E when grub start up then choose kernel boot then hit E again and type in "all_generic_ide"  then it will boot up no problem everytime if i didnt do that itd just lock up right as soon as ubuntu boot up screen comes up.   

so i tried to do this command  sudo nano -w /boot/grub/grub.conf   then all i see is an blank file with no text at all so i opened the directory by gpu and looked into the folders and found the grub.conf and opened it up and it was blank also  i tried to just type in all_generic_ide in the empty file and save it wouldnt let me save it said i dont have the permission and i clicked on properties of the file and it said read only.  i wonder if i have to make it read and write and then open it up and find the kernel line and add the command to it?

---

### Post by Tatty on 2008-03-09
I think you might be looking to edit /boot/grub/menu.lst perhaps?

---

### Post by munkyeetr on 2008-03-09
You're probably looking for /boot/grub/menu.lst

---

### Post by nocturnalsixer on 2008-03-09
yep thats just exactly what i was looking for, thanks a lot guys

---

### Post by seijling on 2008-03-09
nice. thanks!

---

