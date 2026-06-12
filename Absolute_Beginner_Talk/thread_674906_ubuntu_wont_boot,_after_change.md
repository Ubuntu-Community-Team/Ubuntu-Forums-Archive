---
title: "ubuntu wont boot, after change"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-22
I changed the graphics settings and now it just boots to a blank page.  How do I reset this without reinstalling ubuntu?

Thanks
Kezz

---

### Post by stump138 on 2008-01-22
if you don't have a backup copy of your xorg.conf you should try this:
```
sudo dpkg-reconfigure -phigh xorg-xserver
```

that should hopefully get you going again :)

---

### Post by philinux on 2008-01-22
2 ways.

1. sudo dpkg-reconfigure -phigh xserver-xorg from recovery mode boot.

2. Live cd browse to folder containing xorg.conf find its backup and restore it.

---

### Post by stump138 on 2008-01-22
If you plan on playing with your graphic settings you should make a copy of a working xorg.conf.  When you have a regular working x system make a backup copy:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

That way if things go wrong you can just boot into a terminal repair by:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

ctrl + alt + backspace and off you go again :)

---

### Post by KezzerDrix on 2008-01-22
thanks that fixed me.

---

### Post by philinux on 2008-01-22
Curious, which method did you use?

---

