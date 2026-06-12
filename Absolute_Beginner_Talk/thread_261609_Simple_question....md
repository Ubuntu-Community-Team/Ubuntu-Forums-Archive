---
title: "Simple question..."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by mstrat on 2006-09-20
I may be dumb, how do I edit the menu.lst file?

---

### Post by colo on 2006-09-20
Open up a Terminal, then type the following stuff in:

```
sudo su -
nano /boot/grub/menu.lst

```

(You'll be prompted for your password after the first command. Your input - hopefully your password ;) - won't be printed, but don't worry about that.)

After the second command, you're supposed to edit the file with nano. Its usage is pretty straight-forward. You could also use `vim` instead of `nano`, it's a much better text editor, but awkward to use at first. Don't bother about it (yet) if you're not already familiar with its controls.

After you're done with editing, hit the <CONTROL> (<CTRL>) and <O>-Keys together, that will save your edits to this file. Exit nano by pressing <CTRL> and <X> at once. Close your terminal - you're done.

---

### Post by ironfistchamp on 2006-09-20
Another way would be to use

```


sudo gedit /boot/grub/menu.lst


```

That way you use the graphical gedit app. Only works if you are in GNOME. 

Ironfistchamp

---

