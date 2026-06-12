---
title: "Boot Problems"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-04-06
Ubuntu 7.10

Often when I attempt to boot into ubuntu the boot status bar sits at about 1%.  After I hit shift+f5 i get this message a minute or so later
268.547094 atal.00: failed to set xfermode (err_mask=0x40)

If I shut down the machine and try to reboot 2 or 3 times it works.

Whats going on?

---

### Post by Michael.Godawski on 2008-04-06
Try this:
[http://ubuntuforums.org/showpost.php?p=2513159&postcount=4](http://ubuntuforums.org/showpost.php?p=2513159&postcount=4)

To add the irqpoll do the following:

```
gksudo gedit /boot/grub/menu.lst 
```
Look for the kernel line and add the entry. Save the file and reboot.

---

### Post by dreadh3ad on 2008-04-09
I have been using ubuntu for months now and this problem just appeared.  Any thoughts?

---

