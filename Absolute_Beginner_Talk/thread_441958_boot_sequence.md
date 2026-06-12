---
title: "boot sequence"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by johnthebee on 2007-05-13
can anyone tell me how i can make xp the default boot system rather than ubuntu. I'm just beginning to play with ubuntu and would like just to go into xp if i just switch the machine on and leave it but be able to select ubuntu if i want to

---

### Post by tkjacobsen on 2007-05-13
You can edit /boot/grub/menu.lst to start windows by default.

open a terminal:
type "sudo gedit /boot/grub/menu.lst"

locate the line
default 0        

0 is the entry to start by default. 1 is the second and 2 is the third entry. Windows is probably your fourth because ubutnu usually takes three ubuntu/ubuntu recovery/memtest. so this number should be 3. (But see four your self) <-- You can find all the entries in the button of the file.

---

### Post by Aryra on 2007-05-13
I was also looking for how to do this. Not for my sake...if possible, I would have Ubuntu on the whole drive of this computer, but for my family...

They get confused if anything other than that annoying blue login appears :lolflag:

---

