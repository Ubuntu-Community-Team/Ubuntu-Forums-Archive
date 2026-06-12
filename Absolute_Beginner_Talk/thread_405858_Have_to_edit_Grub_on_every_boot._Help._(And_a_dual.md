---
title: "Have to edit Grub on every boot. Help. (And a dual boot question)"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by sit properly on 2007-04-10
Hi folks!

I am dual booting XP and Edgy.

I'm getting Error 17 because it's "looking for" (hd0,2), when really it should be looking for (hd0,1). 

To get around it, I can highlight Ubuntu, hit "e" and change the 2 to a 1, press "enter" and then "b" for boot and it works fine. 

However, is there any way to get Grub to remember that it's a 1, not a 2?



Also, since I'm dual booting for the purpose of two programs that I use regularly, is there a detailed tutorial about getting that instance of XP to run in a virtual machine program? Or would it just be easier to scrap that install of XP and reinstall it via a virtual machine program?

---

### Post by dstew on 2007-04-10
I can answer your first question. You need to edit the /boot/grub/menu.lst file to make that change permanent.

sudo nano /boot/grub/menu.lst

---

### Post by tchoklat on 2007-04-10
edit your grub file and amend the command so that it looks for the right drive
 
/boot/grub/menu.lst is the file you need to edit

---

