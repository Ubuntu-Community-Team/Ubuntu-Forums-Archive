---
title: "about recovery mode"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by gumara on 2006-11-12
Can i disable "recovery mode" access.

---

### Post by professor_chaos on 2006-11-12
you can disable recovery access from the boot loader by commenting out that section in /boot/grub/menu.lst

---

### Post by amunimanghi on 2006-11-12
Yes, you can (see above poster). Make sure to comment out the recovery mode line with ##. EXAMPLE: 
##Kernel number-generic (recover mode)
 but I wouldn't do it. It is useful when you can't login using the gui and you need to fix something.

---

### Post by aysiu on 2006-11-12
Anyone who has physical access to your computer has root access.

I don't see what the point of disabling recovery mode is.

---

