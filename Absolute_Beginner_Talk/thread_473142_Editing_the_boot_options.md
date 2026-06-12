---
title: "Editing the boot options?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Morsolo on 2007-06-13
Hey,
I've been playing with my Ubuntu, and to my dissapointment, I still have no games to play...
This is partially my fault, as I know you CAN run most (well, the ones I have) games, I just don't have the HDD space...I'm working on that...

My question is...
How do you edit the options of the Grub (I think it is) boot loader?
Such as to boot "X" as default, or edit the names of some things?
- Morsolo

**(Offtopic)**
Yay, I've "Spilled the beans"

---

### Post by Inxsible on 2007-06-13
you need to edit the /boot/grub/menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```

To change a default OS you need to change the line default 0 to anything you want as default. Check this site for a detailed info on [GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Morsolo on 2007-06-13
Ah ok...I'm going to reboot into Ubuntu and check that out :)

Thanx mate

---

