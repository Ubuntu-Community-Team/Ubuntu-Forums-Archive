---
title: "Screen Size, Changing"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by deantn on 2007-01-31
Using dual boot with XP Pro and Ubuntu 6.06.
When rebooting to install Ubuntu, clicked F4 and changed screen size to 1280X1024, that worked fine for Live CD. When I deceided to install 6.06 did the same when first screen showed up. Then went through the install process and screen size comes up as 800x600.
 Have tried to change resolution by all the meathods I have read about in other parts of this forum with no luck.
 Maybe it has something to do with SATA drive not sure about that either.
 Am new to Linux period.
Still learning command line but this really bugs me having to "move" page around with Right click all the time.
 Have tried Kubuntu with same results, cannot change screen size in it either.
 Any ideas would be appreciated.:mad:

---

### Post by taurus on 2007-01-31
What other methods have you tried?  You can either reconfigure X (only the resolution section) or you can edit /etc/X11/xorg.conf and add in the resolution you want to use.

Reconfigure:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

Edit /etc/X11/xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by deantn on 2007-01-31
Have tried /etc/X11/xorg.conf with no luck. will try the other and see what happens. Using Wins right now.

---

### Post by Archmage on 2007-01-31
CTRL+ALT+(+ on the num-pad)

---

