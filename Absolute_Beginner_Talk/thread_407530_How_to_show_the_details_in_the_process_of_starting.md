---
title: "How to show the details in the process of starting."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by henry0712 on 2007-04-12
hi,
     I was used to the starting details with RedHat. Now , when I starting the Ubuntu, I felt a little upset about the dark screen in the starting process. Can I get the details back ?
    thanks.

---

### Post by justleen on 2007-04-12
hit ESC, the splash screen will go..

---

### Post by taurus on 2007-04-12
Yes.  Just edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and replace **quiet splash** with **vga=791** at the end of the kernel entry.

---

### Post by mcduck on 2007-04-12
> **taurus said:**
> Yes.  Just edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and replace **quiet splash** with **vga=791** at the end of the kernel entry.

..or just remove the 'quiet' part to get nice graphical boot with scrolling boot messages :D

Also, I recommend vga=792 if it works for you, as it gives nicer colors for text in boot splash (blue with 791, brown with 792)

---

