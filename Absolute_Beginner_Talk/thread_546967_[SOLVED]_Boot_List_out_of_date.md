---
title: "[SOLVED] Boot List out of date"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-09-09
Hi,

I had installed 2 times ubuntu in my laptop. So I used to have windows, ubuntu 1 and ubuntu 2.
The first ubuntu was for my studies about linux, the one that I could mess without anyproblem. The second one, is the one that I use for all other reasons, like surfing the internet, e-mails, messenger, videos, music and others. But now, I deleted the partition of the first ubuntu and formated it as fat32, to use it as a partition to exchange data between windows and ubuntu.

The problem is that when I boot my laptop, it always shows me 3 options of boot, the ubuntu that I still have, windows and the ubuntu wich doesnt exists anymore.

Does anybody know how do I take it off from the boot list??

Thank you very much.
Bruno Krebs

---

### Post by mikewhatever on 2007-09-09
To edit the boot menu, run > gksudo gedit /boot/grub/menu.lst

---

### Post by alienexplorers on 2007-09-09
you have to edit your menu.lst file using:
> gksudo gedit /boot/grub/menu.lst
Remove the offending ubuntu and save the file
reboot

---

