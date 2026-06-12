---
title: "GRUB error 22"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by draze on 2008-01-27
i got my new hard drove and installed ubuntu on it.
the i discovered i did it worng and my whole drive is for the linux wich i didn't want. so i formatted my second drive form XP wich i had on my primary hard drive. 

then i rebooted. and i got GRUB error 17
then i did smthng i don remember i got GRUB error 22

i tried going itno recovery console from my win xp, or just reinstalling ubuntu. but none of my discks load.

helppp/

---

### Post by ajmorris on 2008-01-27
hi there,
grub 22 is an error, that means the partition it is trying to boot grub off, no longer exists. Please boot off the live cd of any linux distribution, and do the following things:

1) Open up a terminal
2)```
sudo grub
```
3)```
grub> find /boot/grub/stage1
``` (**note: **the grub> is to show that i mean in the grub command line that appears from typing sudo grub, and this does not need to be entered, only the find command)
4)```
root (hd#,#)
``` (Replace the '#'s that step 3 tells you.
5)```
setup (hd0)
```
6)```
quit
```
and finally 7) ```
sudo reboot
```

---

### Post by draze on 2008-01-27
thnx for help

---

