---
title: "Can only boot in recovery mode"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by achelis on 2008-03-05
Hi.
I'm new to Ubuntu (and Linux) and have just finished installation on my computer using the LiveCD. However when I try to boot I simply get a black screen and nothing happens.
I can however boot in recovery-mode and everything seems to be working fine so far (I changed single to multi in the "boot-line" which has given me a friendly desktop with a working internet-connection over the command-line no-network boot I got using 'single').
I've updated everything (using the automatic update) and installed the proprietary driver for my graphics card (8800GTS 320mb) from nvidia (which I thought might be causing the problem originally, but getting the drivers changed nothing.)
So the only real problem right now i guess is having to enter the boot menu every time I boot, which just doesn't seem quiet right.

Hope someone can help :)

EDIT: Removing quite splash --help from the "boot-line" lets me boot in normal mode. 
Is there some way to make this change permanent so I won't have to hit escape everytime I boot... which is kinda annoying

---

### Post by jken146 on 2008-03-05
To make it permanent, you need to edit the file /boot/grub/menu.lst and make the same change in the same line.

If you're in the GUI, use ```
gksu gedit /boot/grub/menu.lst
```
If you're at the command line, use ```
sudo nano /boot/grub/menu.lst
```


Post the contents of the file if you need more help.

---

### Post by Iowan on 2008-03-05
Don't forget to **sudo update-grub** before you reboot...

---

### Post by achelis on 2008-03-06
Thanks a lot. It all works now :)

---

