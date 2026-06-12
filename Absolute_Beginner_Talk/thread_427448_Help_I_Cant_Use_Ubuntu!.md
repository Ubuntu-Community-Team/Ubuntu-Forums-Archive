---
title: "Help I Cant Use Ubuntu!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-04-29
I tryed to use envy to configure my graphics driver after months of driver problems.

Although after a reboot it wont open ubuntu because xorg is incorrectly configured (well it said something like that) 

how can I get recover it?

---

### Post by taurus on 2007-04-29
There should be a backup copy of your /etc/X11/xorg.conf so you can either copy it back or reconfigure X again.

Boot into recovery mode from GRUB menu and post the output of this command here.

```
ls -la /etc/X11
```
Assuming it's called /etc/X11/xorg.conf.backup, copy it back with

```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Or reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```
Then, reboot.

```
shutdown -r now
```

---

### Post by gamer91 on 2007-04-29
Ok, so ive managed to recover it (just), still have all the graphical related crashed (beryl, nexuiz - both crash on start).

I now also have a scrolling problem - scrolling in all programs is extremely slow, as is moving windows around the desktop.

---

