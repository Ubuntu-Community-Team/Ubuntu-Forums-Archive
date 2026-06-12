---
title: "Dual boot reformat"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2007-04-16
I've set up a Duel boot system; XP/Ubuntu 6.10 but I've messed up my Ubuntu so much I want to format it and re-install - is this possible? How can i avoid multiple Grub menus? Is there anything I should watch out for?

---

### Post by bulldog on 2007-04-16
Nope,no tricks,if you have a separate /home ,don't format this one.
Set the / root and swap to reformat and install again.
Grub will be updated you won't get multiple GRUB's :D

---

### Post by norton1 on 2007-04-16
hey - just a quick question vaugely related to this - i've just updated the kernel from .10 to .11 and now i have 5 or so options on the grub menu - eg kernel .11, kernel .11 recovery mode, kernel .10, kernel .11 recovery mode, some others i cant remember and the other operating system bits.

is this right? and am i able to change this to just show kernel .11 and other operating systems part?

thanks

---

### Post by My-dial-up on 2007-04-16
Many thanks.

---

### Post by zvacet on 2007-04-16
You can go to the synaptic and search linux image and delete version you don´t want to use anymore.Naturaly it is lower number version.Other possibility is to edit grub
```
sudo gedit /boot/grub/menu.lst
```

and comment(put # sign)  all grub versions you don´t want to use.

---

### Post by norton1 on 2007-04-17
thanks zvacet i will try that tonite!

---

