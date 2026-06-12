---
title: "Can grub boot my XP in D:\"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by peter.c on 2007-11-15
Hi all, I installed a VISTA in C: and a UBUNTU in the last partition.
Now I want to ghost a XP to my drive D, how could I do to let the grub boot up my ghost XP?
Can anyone help me, thanks very much.

---

### Post by benerivo on 2007-11-16
You should be able to do this by giving a bootable flag to the drive XP is on, and then adding a few lines to the end of your /boot/grub/menu.lst file. To make the drive bootable you could try installing GParted. Using this program, you can add a bootable flag to the drive. Also take note of what disk and partition it is on (ie. sdb1). The add the following lines to the end of your menu.lst file so it looks like this...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Now just change the numbers "0,0" to match the "drive,partition" that your xp is on (where sda1 = 0,0 and sdb3 = 1,2, etc...)

---

