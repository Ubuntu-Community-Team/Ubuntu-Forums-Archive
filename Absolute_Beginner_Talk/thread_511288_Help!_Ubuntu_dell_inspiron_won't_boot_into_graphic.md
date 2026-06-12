---
title: "Help! Ubuntu dell inspiron won't boot into graphical mode!"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-07-27
I recently updated my dell inspiron 1420, right after I got it.  Now, I can't even boot into a graphical interface.

there are now two kernels:
Ubuntu, kernel 2.6.22-8-generic
Ubuntu, kernel 2.6.20-16-generic

The first one, when I boot it up, gives this message, then freezes:
[  116.894306] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

The second one boots up, but it can't launch the graphical since it says 'Screen not found'.

---

### Post by Rocket2DMn on 2007-07-27
The problem with the first one is that the drive configuration seems to have changed - this would be a problem with GRUB I think.  

To fix the GUI, you will need to reconfigure the Xserver since your xorg.conf seems to be incorrect
```
sudo dpkg-reconfigure xserver-xorg
```
Then you can start the Xserver
```
startx
```
or you can get to the login screen if you prefer
```
/etc/init.d/gdm start
```

---

### Post by purplearcanist on 2007-07-27
thank you, now I can boot into the graphical interface:).

I'll work on the grub configuration to see if I can get the other kernel to boot.

---

