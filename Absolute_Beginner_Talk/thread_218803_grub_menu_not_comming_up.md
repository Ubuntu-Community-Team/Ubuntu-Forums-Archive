---
title: "grub menu not comming up"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-07-19
Hi ive got a 3rd hdd with winxp on it(hd2). How do i make grub ask me with a say... 10 sec then default to linux(hd0)

this is in my menu.lst:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

but Grub doesnt display the menu on boot

---

### Post by richbarna on 2006-07-19
> **dgrafix said:**
> Hi ive got a 3rd hdd with winxp on it(hd2). How do i make grub ask me with a say... 10 sec then default to linux(hd0)

this is in my menu.lst:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

but Grub doesnt display the menu on boot

You need to change the "timeout line" in the menu list:-
> ...
timeout     3
... 
Just change it from 3 seconds to a higher number.

Also, for practically every "Grub+Menu.lst" solution, check out my signature.
|
|
v

---

### Post by dgrafix on 2006-07-19
thanks it was set to 0

---

