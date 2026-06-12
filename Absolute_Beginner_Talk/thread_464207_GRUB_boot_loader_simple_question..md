---
title: "GRUB boot loader simple question."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-04
I recently upgraded to kernel .16, this appeared as the top and default option on my GRUB boot loader at the beginning.  Wireless internet refuses to work on it so I would like to revert to having .15 as my default so I don't have to select it at start up. 

.15 is the third option down, after .16 and .16 recovery.  

Please give me simple instructions on how to do this.  I've checked the GRUB documentation and it's complex. 

Thanks.

---

### Post by daimaru on 2007-06-04
edit your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```
locate the lines with kernel .16 and comment them out (##) or delete them
edit: comment out the whole block (title kernel etc)

---

### Post by aberadam on 2007-06-04
Great, that worked perfectly.  Thankyou.

---

### Post by ncappel1 on 2007-06-04
edit: sorry, i acidentally double posted.

---

### Post by ncappel1 on 2007-06-04
> **daimaru said:**
> edit your menu.lst file
locate the lines with kernel .16 and comment them out (##) or delete them

This is an option, but it will disable you from using that Kernel at all. If you change the value of "Default" in the menu.lst it will load the number kernel you specify. For example, changing it to read "Default 1" will load the first kernel on the list, default 2 is the second, and so on.

---

