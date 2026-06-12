---
title: "Help to make XP Boot first?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by hulland on 2007-03-29
1) Have installed Ubunutu on  a new Volume--but want to change the boot order of pc--must be a simple help file somewhere?

2) I never use the desktop or mouse in XP--how can I set up Ubuntu to be similar? i.e.  hot key oreintated please? ( aka fast, fast, no drilling down through menus) 

List of shoirtcuts needed if possible? Thanks for any help. Ian.

---

### Post by AtrejuT on 2007-03-29
change the booot order:
```

sudo nano /boot/grub/menu.lst

```

find the entry
default 0
and change 0 to the number of the entry of windows. (so if you have ubuntu kernel, ubuntu recovery and windows set it to 2)

---

### Post by cyberdork33 on 2007-03-29
It is easier to just move the Windows entry in the menu.lst file from the bottom to just above the "BEGIN AUTOMAGIC KERNELS" Section. This will make your windows option appear first in grub and, upon getting a new kernel for ubuntu, you will not have to edit the menu.lst file again to fix the "default" line (since adding another kernel will move the windows entry down the list, and it no longer being the default)

---

### Post by raul_ on 2007-03-29
> **cyberdork33 said:**
> It is easier to just move the Windows entry in the menu.lst file from the bottom to just above the "BEGIN AUTOMAGIC KERNELS" Section. 

But it's not l33t :cool:

I agree with moving it though...just my 2 cents. It's easier than to count every entry you have, specially because you'll keep installing kernels till the end of your days in linux =\

but the first one is a good solution too

---

