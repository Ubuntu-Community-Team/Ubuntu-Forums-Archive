---
title: "hide the grub menu?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by jaynyls on 2007-10-03
How do I go about auto-hiding the GRUB menu, so Windows XP loads by default unless I tell the computer to load ubuntu instead?

---

### Post by sc30317 on 2007-10-03
just edit your grub.conf, put the Windows part of the grub above Ubuntu in the boot order, lower your boot menu time, and blamo!  You got yourself a window first boot

---

### Post by ThrobbingBrain66 on 2007-10-03
> **sc30317 said:**
> just edit your grub.conf, put the Windows part of the grub above Ubuntu in the boot order, lower your boot menu time, and blamo!  You got yourself a window first boot

That works, but it's not the "correct" way to do this.  If GRUB is ever updated, things can get messed up.

You still must edit your /boot/grub/menu.lst file, but you need to change the "default       0" entry near the top of the file.  For example, if XP is the second partition on your hard drive, you change this from 0 (zero) to 1.  (0 obviously would be the first partition then).

---

### Post by om1 on 2007-10-03
> **ThrobbingBrain66 said:**
> That works, but it's not the "correct" way to do this.  If GRUB is ever updated, things can get messed up.

You still must edit your /boot/grub/menu.lst file, but you need to change the "default       0" entry near the top of the file.  For example, if XP is the second partition on your hard drive, you change this from 0 (zero) to 1.  (0 obviously would be the first partition then).

thats right you should follow the correct way to edit files like that.... change the default boot partition and the delay time low and your good....
also  change this part of the grub file 
......
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
.........
to
........
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
......
and it will hide the menu unless you press a key

---

### Post by jaynyls on 2007-10-03
Sorry, I'm a little more of a noob.  Could I get step by step instructions?  I'm using 7.04.

---

### Post by ryanVickers on 2007-10-03
the posts by om1 and ThrobbingBrain66 are correct.  Just open the /boot/grub/menu.lst file as root, and then set it to hidden menu, and put the default as "1".

---

### Post by ThrobbingBrain66 on 2007-10-03
> **jaynyls said:**
> Sorry, I'm a little more of a noob.  Could I get step by step instructions?  I'm using 7.04.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0
```

You need to edit the 'default 0' line shown here.  It's near the top of the file.

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

Uncomment the line above that just says 'hiddenmenu'

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         1
```

and change your timeout value to 1, like I have.

---

### Post by ryanVickers on 2007-10-03
OK, just go in the file brwoser to /boot/grub

then open the file called "menu.lst"

just post it here, and I'll do the changes if you want.
(windows boots first, hide menu, right?)

---

