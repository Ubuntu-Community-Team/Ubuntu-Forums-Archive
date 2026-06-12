---
title: "Bootloader"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by revdg on 2007-02-01
Can someone tell me simply how to alter my Grub bootloader so that Windows is the default (necessary for work!). Have found the grub menu document but cannot save an edited copy of it as I am denied permission and cannot find out how to change this.

---

### Post by igknighted on 2007-02-01
First you need to open the file /boot/grub/menu.lst as root
```
gksudo gedit /boot/grub/menu.lst
```

There should be a line somewhere well above where the boot choices are listed that says "default 0".  You need to change the 0 to whatever number Windows is, so Ubuntu has the first three slots usually (0,1, and 2) so windows is probably 3.

---

### Post by linux_kid on 2007-02-01
First type
```
/boot/grub/menu.lst cp /boot/grub/menu.lst.old
```
To make sure we have a backup in case we mess up.

Then type
```
sudo gedit /boot/grub/menu.lst
```
The terminal will ask you for your password, and then a text editor should come up after you have typed your password.

Find the menu entry labled
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
And see how far down it is. (Chances are it is the fourth boot option)
Subtract one (1) from how far it is (so if it's the fourth entry, remember three) and then find the entry looking like this
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```
Change the last  zero to which ever number you previously came up with, and save the file.

I know this is about the most confusing answer I could give, but it explains it in full.

Good Luck :D

---

### Post by revdg on 2007-02-02
Thank you for your help which quickly solved my problem!

---

