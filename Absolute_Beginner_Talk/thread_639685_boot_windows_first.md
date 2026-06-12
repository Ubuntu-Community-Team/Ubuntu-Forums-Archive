---
title: "boot windows first"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mikeee6562 on 2007-12-13
Hey guys, i want to boot windows first over ubuntu, both are installed. I tried searching for a solution through search but am having no luck. could some one steer me in the right direction

   thanks in advance
mike

---

### Post by stchman on 2007-12-13
> **mikeee6562 said:**
> Hey guys, i want to boot windows first over ubuntu, both are installed. I tried searching for a solution through search but am having no luck. could some one steer me in the right direction

   thanks in advance
mike

This will show you how to safely.

[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

---

### Post by Dr Small on 2007-12-13
You will need to edit /boot/grub/menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

Find the line:
```
default		0
```

0 is currently default (Ubuntu), so you will need to go down and find:
```
title		Ubuntu, kernel 2.6.20-15-generic
```

And count the "title"s down, until you find Windows. Remember, Ubuntu is 0, so get the numbers correct. Then go back up and change "default 0" to "default *numberhere*".

Dr Small

---

