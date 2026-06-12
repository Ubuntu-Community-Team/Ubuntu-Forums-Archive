---
title: "How to change GRUB's list?"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by commodore on 2005-10-04
My father thinks GRUB makes our comp too complicated :D He said that our comp is the most complicated comp in the world :D He would let me keep ubuntu installed if I would put windows first in GRUB's list. How to do that?

---

### Post by SilentCacophony on 2005-10-04
Hi. The easiest way to handle that would be to change the default entry in the list, like so:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup** to backup the file, in case you make a mistake.

**sudo gedit /boot/grub/menu.lst** and find this section:

[I]# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0[/I]

Then change that 0 to the index number of the Windows entry by counting the entries. Or you could make sure that *only* the Windows entry has **savedefault** and enter **saved** for the default, though I've never tried that. Then save the file.

---

### Post by aysiu on 2005-10-04
```
sudo nano /boot/grub/menu.lst
```

Find which entry Windows is and make that the default.
If Windows is the fourth entry, change default 0 to be default 3. If Windows is the fifth entry, change default 0 to default 4, and so on.

Control-x
y
Enter

---

### Post by commodore on 2005-10-04
o.0 and one of my friends said it's hard for a n00b like me :D

---

### Post by commodore on 2005-10-19
I updated my kernel. The old kernel version is still in the list! Did it install the new kernel as extra or overwrite the old? How can I remove it from the list?

---

### Post by commodore on 2005-10-19
Hello?

---

### Post by Dr. Nick on 2005-10-19
The "old" kernel is probably still installed, you can remove it from the list if the new one works fine by deleting the lines in menu.lst, then if your daring you can remove the old kernel using synapitc, but be sure to remove the right one. I think removing it from synsptic will clear if from the list.

---

### Post by commodore on 2005-10-19
I'm afraid :( There was a patch for the kernel to fix what I had problems with but I chose to update.

---

### Post by Dr. Nick on 2005-10-19
Does everything work right now? Its really no big deal if you have multiple kernels installed,as long as you boot into the right one that everything works in. If you update to a new kernel in the future and something stops working you can simply reboot into the one you had been using before and it will work again.

---

### Post by commodore on 2005-10-20
For me it seems a waste of space.

---

