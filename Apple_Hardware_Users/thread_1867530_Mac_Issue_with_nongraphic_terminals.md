---
title: "Mac Issue with nongraphic terminals"
date: 2011-10-23
forum: Apple Hardware Users
---

### Post by Franscisco_Gallardo on 2011-10-23
Hi everyone:

I have a small issue that maybe someone can tell me how to solve or where can I report the error, I've already looked for this error in the forums and I didn't find anyone who is reporting this malfunction.

I'm using a Macbook with a Intel Core2 Duo CPU 2.26GHz (I'll see what version is if it is really important). Ok, the graphic card is a Nvidia. 

Well, the issue is that I've already installed the graphic card driver and it works really well, but when I try to switch to terminals without graphic (alt+control+F1) I can't see anything, I mean, I see something but it is really distorted. Of course it happens too when the Ubuntu O.S. is loading when you power on the computer.

It doesn't happen when I unistall the graphic drivers but then of course I don't have any kind of graphic features (I mean any kind of graphic acceleration).

Can somebody tell me something about this? Or where to report the isse?

Thanks for you time!

---

### Post by Sileem on 2011-10-23
I didn't have this problem with Ubuntu on my MBP 7,1 but I do have this issue on Arch Linux, strange. I'll keep an eye on this thread. I've also asked in the Arch Linux forums. If they figure anything out, I'll let you know.

---

### Post by tomodachi on 2011-10-25
its always good to mention more specifics on your model.


I have a macbook pro 5.1  15" with a  nvidia 9600Gt and a 9400 card. And I've had the same issue.

Think its related to the framebuffer driver somehow not working at all once the graphical environment launches.

Do miss the "real" console sometimes but dont really have a soluton for it. If you find one. please enlighten me!

---

### Post by Sileem on 2011-10-27
> **tomodachi said:**
> its always good to mention more specifics on your model.


I have a macbook pro 5.1  15" with a  nvidia 9600Gt and a 9400 card. And I've had the same issue.

Think its related to the framebuffer driver somehow not working at all once the graphical environment launches.

Do miss the "real" console sometimes but dont really have a soluton for it. If you find one. please enlighten me!
I'm not sure if it is the framebuffer, I use ArchLinux, and the problem only occurs when I start X.

---

### Post by tomodachi on 2011-10-27
I think that once X starts. There is a hand-over from the framebuffer device to the driver used in X and the framebuffer detactivates. 

This is how it works for the nouveau drivers at least.
reference :[http://nouveau.freedesktop.org/wiki/KernelModeSetting](http://nouveau.freedesktop.org/wiki/KernelModeSetting)

Hence my theory.

---

### Post by Sileem on 2011-10-30
I think I may have found the solution!
[https://wiki.archlinux.org/index.php/GRUB#hwinfo](https://wiki.archlinux.org/index.php/GRUB#hwinfo)
I'm not entirely sure how to get hwinfo for ubuntu, but this should point you in the right direction! For me, I had to add vga=0x361 to my kernel line in my syslinux.cfg, but the same idea will work in grub.

---

