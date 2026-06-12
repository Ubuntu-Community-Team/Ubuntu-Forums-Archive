---
title: "failing to start the x server"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by dzebras on 2006-12-28
Hi,
i just installed ubuntu 5.10 and everytime I rebot the system I get the same message: failed to start the X server (your graphical interface). It is likely that it is not set up correctly... I have no idea what to do... Please help me ;)
p.s. I guess I should mention that I formatted my hard disk before installing ubuntu. Could there be some problems with drivers or.. I don't know

---

### Post by tseliot on 2006-12-28
Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.
Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by dzebras on 2006-12-28
Thanks a million! It works. God that's great ;)

---

### Post by wpshooter on 2006-12-28
Do you mean the 6.10 version ?  Have you tried installing with the safe graphics mode parameter ?

---

