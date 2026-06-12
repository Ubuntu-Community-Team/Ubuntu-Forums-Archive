---
title: "OS selection screen"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by gman_01au on 2007-04-20
hi, just downloaded and installed ubuntu feisty 7.04 on my PC. I am dual booting it with windows xp pro, just wondering if there is a program around to get a more user friendly OS selection screen rather than the black screen with a few selections (ubuntu, ubuntu rescue, windows xp n a couple others) with ubuntu automatically selected and a countdown timer of 10 secs. this is a bit inconvenient as my parents/sister are kind of computer illiterate and are complaining they only get a few seconds to choose. (they would prefer to use windows xp for some strange reason).

---

### Post by Stickymaddness on 2007-04-20
> **gman_01au said:**
> hi, just downloaded and installed ubuntu feisty 7.04 on my PC. I am dual booting it with windows xp pro, just wondering if there is a program around to get a more user friendly OS selection screen rather than the black screen with a few selections (ubuntu, ubuntu rescue, windows xp n a couple others) with ubuntu automatically selected and a countdown timer of 10 secs. this is a bit inconvenient as my parents/sister are kind of computer illiterate and are complaining they only get a few seconds to choose. (they would prefer to use windows xp for some strange reason).

The OS selection screen is a program called grub. You can edit your settings but typing the following into a terminal

```

gksudo gedit /boot/grub/menu.lst

```

Just be sure to make a backup, and be careful when you're editing!

---

### Post by AndrewNi on 2007-04-20
The shareware boot manager BootIt Next Generation is extremely user friendly - it supports the mouse and all.

---

### Post by gman_01au on 2007-04-20
Thanks :)

---

### Post by Pobega on 2007-04-20
Add/change these values in your menu.lst, it's the Debian default and I think it looks a lot nicer than Ubuntu's;

```
timeout         10
color cyan/blue white/blue
```

That alone makes GRUB nice enough to look at, without going over the top with images and stuff. If you really want images look into GRUB splashes at [http://gnome-look.org/](http://gnome-look.org/), but it's been so long since I set one up I forgot how to do it; I just remember that it's extremely easy.

---

