---
title: "GRUB order"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-04-20
Hello fellow Ubuntu people !
I'd like to know, is there anyway to change the default OS to boot ?

When i boot my PC, the default OS that grub loads after 10 seconds is Ubuntu, is there anyway to change it to my windows XP installation ? Thanks for any help !

---

### Post by hanexar on 2007-04-20
Hi, you can edit the grub file:
type in a terminal:

```
 sudo gedit /boot/grub/menu.lst
```

Find this text

```
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default	0	
```

Change the default value for your windows partition (to find out, go to the bottom, and count in which place it is, starting with 0.

```

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true
```
Put this option to false, so it won't change after every update.

I hope it helped.

---

### Post by taurus on 2007-04-20
Yes.  Just change the **default** from 0 to whichever entry Windows is in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```
Remember, the first title counts 0, the second title counts 1, the third title counts 2, and so on.

---

### Post by hanexar on 2007-04-20
Actually, once you opened the file, the instruction in the file are clear, you should have a look of the stuff you can change.

---

