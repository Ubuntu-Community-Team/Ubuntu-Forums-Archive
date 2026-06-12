---
title: "Default boot"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-01-19
Hello.
I have installed Ubuntu 5.10 with dual boot WindowsXP on my computer. I have recently update Ubuntu, and now the default boot option is memtest. I'd like it to be WindowsXP. 
What file should I edit? I think it's the /boot/grub/menu.lst , but I'm not sure. And what should I edit?  

Thanks, 
Klaidas

---

### Post by lha on 2006-01-19
[QUOTE=Klaidas]Hello.
I have installed Ubuntu 5.10 with dual boot WindowsXP on my computer. I have recently update Ubuntu, and now the default boot option is memtest. I'd like it to be WindowsXP. 
What file should I edit? I think it's the /boot/grub/menu.lst , but I'm not sure. And what should I edit?  

Thanks, 
Klaidas[/QUOTE]

Yes, /boot/grub/menu.lst needs to be edited. Find a line with "default 3". (The number might be different for you.) Every menu item has a number, starting from 0 for first item and 1 for the second item. Change the number after "default" to point the item you want to be selected at default. Most likely you need to add 2 to your current number, so the line would be "default 5".

---

### Post by Klaidas on 2006-01-19
I have done it, it works.  Thank you very much! :)

---

