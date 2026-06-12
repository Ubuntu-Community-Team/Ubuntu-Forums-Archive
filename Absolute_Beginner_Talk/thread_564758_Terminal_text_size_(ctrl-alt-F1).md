---
title: "Terminal text size (ctrl-alt-F1)"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by poiiop on 2007-10-01
Hi

Sometimes my movieplayer (Gstreamer) freezes in full screen mode.

When i go to the console mode with ctrl-alt-F1 to make a kill -9 to totem, the textsize is very large, about 10 line on the screen. 

It's very diffecult to write anything because the text disapear down.

Any hints for changing the textsize on the terminal windows (ctrl-alt-F1) ??

/poiiop

---

### Post by meborc on 2007-10-01
in feisty, you can just add vga=773 or vga=791 (both 1024x768 but with different colors) to the end of the kernel line you are booting from...

to test it, reboot your comp... in the grub menu hit E (for edit)... choose the kernel line... hit E again... then delete word splash and type vga=773... enter... B (for boot) [this will only change the line for one boot... when you restart, it will be changed to default]

if you now see small text flying by, then it works :) and you can continue making it default...

the file you must edit is /boot/grub/menu.lst ... BACKUP it first before starting... you can do it like this:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```then edit the file```
sudo nano /boot/grub/menu.lst
```scroll down to the kernels section... and edit the line like you did in the grub menu... if you like to see the usplash, leave the word splash there... just add the vgs bit :D

report here, if something is non-understandable

---

### Post by fynlam on 2007-10-01
I found this tread related to the subject.
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by poiiop on 2007-10-02
Thanks many times - very nice service ..... first time here .. :)

./poiiop

---

