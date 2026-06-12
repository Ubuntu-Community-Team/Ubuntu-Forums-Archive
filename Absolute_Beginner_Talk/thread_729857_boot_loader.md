---
title: "boot loader???"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by iwallet on 2008-03-20
hello everyone and thank you for reading this... and thank you even more if you actually respond...

i have an hp laptop with 2 HD, i found out after i bought it that hp has set the second HD so i can not boot from it... i was wondering is there a boot loader i can install on the first HD so i can "trick" the computer into booting from the second hd?!
if i need to be more clear please tell me...

---

### Post by Dr Small on 2008-03-20
Yes, I did this with Grub before on my server.
I had 2 hard drives in it. The first one was the server hard drive, the second one was a desktop hard drive. The server hard drive booted first, and so I edited GRUB around to add an entry to boot the desktop hard drive while the bootloader on the server hard drive was loaded.

Very confusing?
It was to me, and took me 2 days to figure it all out.....

Dr Small

---

### Post by bumanie on 2008-03-20
Do you know what has been put there to stop it booting? How do you know it won't boot, ie have you tried to boot from it?

---

### Post by iwallet on 2008-03-22
well i tried for about 30 minutes.. then i got bored :P i can click f2 on startup to choose boot from cd or HD 
 but it will give me only one hd.. i tried going on the bios but my keyboard doesnt seem to work when i enter the bios... so i dont know... i guess i will try with grub... :P

---

### Post by Dr Small on 2008-03-22
What is the connection for the keyboard? Is in PS/2 or USB? Sometimes a USB keyboard can mess up, expecially if the BIOS can not handle it.

Dr Small

---

