---
title: "Can you have Windows listed first on the Grub menu at bootup?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-07-30
I'd like to do this so my kids and wife can boot up windows first.

---

### Post by taurus on 2006-07-30
You can do that by editing your /boot/grub/menu.lst.  Open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo gedit /boot/grub/menu.lst

```
Now, look in it to see which entry is for your Windows (at the end).  If it is the fifth entry, then change the "default" (near the top) to 4 instead of 0...  (Remember, Unix/Linux counts from 0, not 1 like the other OS does!)

```

default     4

```

---

### Post by izle on 2006-07-30
you just have to edit manually the menu.lst file and to move the section concerning window on top

concretely, in a terminal type 

```
sudo gedit /boot/grub/menu.lst 
```

the first lines should look like this

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0


By default the system boot on the first entry of the grub menu which in case you have have just ubuntu and windows on your machine should have four items in the grub list: 
-ubuntu
-ubuntu(recovery)
-memtest
-windows
You can set it to boot on any entry by changing the value default value which appear above and is set to 0, change it to 3 and your system will boot on windows after the countdown.

---

### Post by bamend on 2006-07-30
Help.  I tried this and now just get the grub menu on startup.  How can I get back to where I was?  I tried doing the install disk route without partitioning the hard disks but it hangs up. :confused:

---

