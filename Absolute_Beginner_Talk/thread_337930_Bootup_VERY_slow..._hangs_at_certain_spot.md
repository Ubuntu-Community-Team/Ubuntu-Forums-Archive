---
title: "Bootup VERY slow... hangs at certain spot"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-13
For some reason the last couple times I've started up my laptop ubuntu loads very slowly. It seems to hang at a specifc point. Since i don't know how to cut the gui and watch it, i switched kernels to recovery mode and had the same thing. It seems to hang between mounting drives from fstab and booting my network card. Now I did change my fstab but I didn't even mess with my network card, and my network card wasn't working for some reason. Eventually I just disabled and re-enabled it and it worked, but it still seems to be booting really slowly. Again the only thing I've done is install Wine and configure it and change my fstab so it auto-mounts windows.
Any info is greatly appreciated.

---

### Post by riven0 on 2007-01-13
Will, if your bootup started slowing down after messing with fstab, that is most likely the culprit. Can you post your fstab here? Perhaps someone can help.

---

### Post by rj686 on 2007-01-13
I ended up doing a full re-install becuase I broke a lot of things :(. lol Anyway, is there a way to get to terminal while it's booting?

---

### Post by riven0 on 2007-01-13
Not while it's booting. But if you want to see what exactly is booting up and where it's hanging, take out the **quiet** from the kernel line. When you get to the GRUB, highlight the kernel line and hit **e**, then go to the line that looks similar to this:
> 
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash 

Delete the **quiet**, hit enter and then **b** and it should bootup with the scrolling text.

---

