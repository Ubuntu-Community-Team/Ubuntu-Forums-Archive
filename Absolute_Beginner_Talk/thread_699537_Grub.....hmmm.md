---
title: "Grub.....hmmm"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-02-17
i duel boot with grub.  I have two hard drives, one for Ubuntu and one for windows.  When my computer starts up and i select Ubuntu, it comes up with an error.  It is easy to go around, all i have to do is press e(edit) 3times and then change the HD from (0,1) to (0,0).  Then i press enter and then b and it boots up successfully.

I have been trying (unsuccessfully) to change the file itself in terminal, but my code must be wrong.  I tried;

sudo gedit/boot/grub/menu.lst

(and) sudo nano/boot/grub/menu.lst

...but none of them worked :( and i dont know why because the file is in (boot/grub) and is called menu.lst.

:confused::confused:

can anyone help me?

---

### Post by sb12 on 2008-02-17
you are leaving out a space.  the correct code is:

sudo nano /boot/grub/menu.lst

---

### Post by Nick8692 on 2008-02-17
perfect :) Thanks!

---

