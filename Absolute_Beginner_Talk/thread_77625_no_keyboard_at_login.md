---
title: "no keyboard at login"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by andy81 on 2005-10-17
hi, as the title says, I have no keyboard at login..so i cant log in.  I can use the number and symbols on the keyboard, but no letters.....anyone know a way to fix this?  I cant get into linux, but I can use my windows partition like i am now, but I cant access linux files or anything from here. any ideas?

---

### Post by Pausanias on 2005-10-19
This may or may not work. Try passing i8042.noacpi as an option to the bootup process. To do this, reboot the computer. In grub, edit your default boot command. Go to the line which contains the word "vmlinuz." Edit that line. Add the text "i8042.noacpi" to the end of it. Then boot with that command line.

---

### Post by andy81 on 2005-10-20
thanks for the reply.  I still cant get it to work, I dont know if I type it right though, do I have to have the "" when i edit grub, or do I have to type something else?  but anyway, i had this problem when I tryied to configure the ati driver sudo dpkg-reconfigure xserver-xorg. So acpi was on before, i have booted ubuntu before this. i dont even know if i got the driver to work becasue i cant login at all!!!!!

anyone know what to do?

---

### Post by matog on 2005-10-20
Here you have a solution (but it&#180;s in spanish):

[http://www.ubuntu-es.org/node/7981](http://www.ubuntu-es.org/node/7981)

I had the same problem, but now it works!

---

### Post by andy81 on 2005-10-20
I had a look at the link, and I think that I have configured my keyboard as 105 key, keyboard, but I have a 102 or soething.  The problem is that I cant get to a terminal or anything when i choose in grub to start ubuntu.  I can access the xorg.conf in windows, but I cant save the changes I make to it, to say that I have a 102 keyboard.  Does anyone know of a way to do this?  I use a program called "explore2fs" to access my ubuntu partition and the xorg.conf file.  I think that if i can chage it, and save it then maybe I will be able to start ubuntu again....i really dont want to install again!!

---

### Post by LHZ on 2005-10-20
Do you by chance have an Ubuntu Live CD handy? You could boot from the live cd, mount the drive, change the file, and then boot in again.

If you don't have a Live CD yet, you could burn one from windows.

---

