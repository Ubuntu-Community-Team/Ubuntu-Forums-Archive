---
title: "Boot Sequence"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by dbuss63 on 2007-07-01
I am now using Ubuntu through the Wubi installation and I am greatly enjoying the Linux alternative to Windows.  

When I first turn on my computer, a screen pops up giving me the choice to boot either Windows or Ubuntu.  The Windows choice is highlighted which means it will boot automatically unless I highlight the Ubuntu choice below with my arrow key.  Is it possible to reverse the sequence so that Ubuntu is the first choice and thus will boot automatically?
Dennis

---

### Post by adamklempner on 2007-07-01
This post should help you:  ;)

[http://ubuntuforums.org/showthread.php?t=473802](http://ubuntuforums.org/showthread.php?t=473802)

---

### Post by Famicommie on 2007-07-01
Yes. First, type ```
sudo gedit /boot/grub/menu.lst
```
Look for the section that says:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

At the bottom of the file, it will list all of the various options from the boot menu. Starting from the first entry, count to your Windows entry. Keep in mind that grub starts counting with the number 0. Therefore, if Windows is the fourth entry in the list, then grub considers it to be number 3. You would simply edit the above section to read:

default         3

---

