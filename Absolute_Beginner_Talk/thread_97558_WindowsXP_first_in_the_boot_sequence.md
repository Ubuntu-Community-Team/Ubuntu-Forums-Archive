---
title: "WindowsXP first in the boot sequence"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by mr2v6 on 2005-12-01
Hello,
I just installed UBUNTU, and would like Windows XP to be the first in the boot seqence. How do I adjust GRUB?

Thanks,
MR2V6

---

### Post by super on 2005-12-01
you need to edit /boot/grub/menu.lst
[FONT="Courier New"]
sudo cp /boot/grub/menu.lst /boot/grub/menu.old
sudo gedit /boot/grub/menu.lst[/FONT]

abot 3/4 of the way down the file you will see the boot menu entries. cut the winxp entry and paste it just above the first ubuntu entry.

or if you just want winxp to boot first, you can just change the default number at the top of the file.

save and exit.

---

