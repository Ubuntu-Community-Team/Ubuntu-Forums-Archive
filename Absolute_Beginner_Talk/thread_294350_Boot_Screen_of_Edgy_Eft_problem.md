---
title: "Boot Screen of Edgy Eft problem"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by rajeshgovindan on 2006-11-06
Boot Screen resolution of Ubuntu 6.10 is not supported by my monitor so it says"Sync out of range¨. I am not able to view it (but I just loved the modified Ubuntu boot screen,saw it at my friends house)....is there any way to solve this problem......plz help guys


Rajesh

---

### Post by steve.horsley on 2006-11-06
Try putting vga=xxx at the end of the GRUB entry (in /boot/grub/menu.lst". Replace the xxx with a value from the table of values in this article:
[http://www.digitalhermit.com/linux/hiresconsole.html](http://www.digitalhermit.com/linux/hiresconsole.html) (search for "friendlier" near the bottom). 769 looks like a safe bet. Or "vga=ask".

---

