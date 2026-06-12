---
title: "2 ubuntus installed, want to boot sda3, use its grub and format sda1"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by eternal-one on 2008-02-11
so how do i make sda3 the boot partition, using its grub, so I can wipe sda1 to use as free space?

(right now the only reason i have ubuntu still on sda1 is to boot sda3)

Any help would be much appreciated!

thanks

---

### Post by logos34 on 2008-02-11
> sudo grub

> root (hd0,2)
> setup (hd0)
> quit

after you boot back into into sda3 run

gksudo gparted

unmount sda1 first, then format

---

### Post by eternal-one on 2008-02-12
awesome thnx, now i get how it works. pretty easy. 

However now I get error 15 press a key to restart.

figured it was because of grub startup software i had. So I restored defaults and uninstalled startupmanager.

then changed back to hd0,2 and get the same damn error 15.

arg!

---

### Post by logos34 on 2008-02-13
maybe menu.lst is wrong.

Press 'e' on the ubuntu kernel in grub menu screen...the 'root' line should read (hd0,2).  If not change it ('e' again).  Then press 'enter' and 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

Or maybe there's a typo somewhere. more on [Error 15 here]("http://users.bigpond.net.au/hermanzone/p15.htm#15")

---

