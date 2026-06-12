---
title: "Boot Order"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Darzinho on 2006-11-23
Hi,

Another question!

After installing Ubuntu, when I boot up I am presented with about 5 options.

3 of them are normal and 2 are for Windows. Any idea why 2 are there for Windows XP?

One is Windows XP and the other says Windows 2000/NT/XP or something to that effect. I definitely don't have any other Windows' OS installed on the system. Any idea what this might be?

Also, does anybody know how to change the default operating system?

Thanks!

---

### Post by BarfBag on 2006-11-23
That's bazaar.  When you select the option that shouldn't be there, what happens?

You can change your default OS by editing your Grub config file.  Forget how to do it.

---

### Post by Average Joe on 2006-11-23
You have to edit your /boot/grub/menu.lst file. In there is an entry saying default=0, which means it boots the first entry in your grub menu. You can change the 0 to something else.

At the end of this file are also your Windows grub menu entries. You could comment out the obsolete Windows (by putting a # before it).

---

### Post by mcduck on 2006-11-23
to expand the last reply, 0 is the first entry, second one is 1 etc..

You can also use 'default=saved' to make the last used OS as default.

and the command to open the file for editing is 'gksudo gedit /boot/grub/menu.lst'

---

### Post by sailor2001 on 2006-11-23
ubuntu is your default (0) and xp is 5  If you want xp to be your default
sudo gedit /boot/grub/menu.lst and in the 2nd paragraph change the 0 to 4 at the beginning and ending of that paragraph...
the boot sequence is ubuntu (0), ubuntu safe (1) memtest (2) xp safe (3) xp (4)

---

