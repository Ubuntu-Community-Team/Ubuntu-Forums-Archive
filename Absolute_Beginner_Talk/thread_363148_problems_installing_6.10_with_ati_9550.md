---
title: "problems installing 6.10 with ati 9550"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by greggeise on 2007-02-16
i have installed 5.10 with no problem ,6.06 ihad to install the ati drivers manually ,but  6.10 blanks out on the splash screen and then freezes ,i have tried the install using ultimate dvd and cd ,also tried to run live but my system shuts down when loading the gui....
is there any way to load the ati drivers during install or after install perhaps prior to the load of the splash screen? will  7.04 come with the proper drivers?

---

### Post by ed-j on 2007-02-16
> **greggeise said:**
> i have installed 5.10 with no problem ,6.06 ihad to install the ati drivers manually ,but  6.10 blanks out on the splash screen and then freezes ,i have tried the install using ultimate dvd and cd ,also tried to run live but my system shuts down when loading the gui....
is there any way to load the ati drivers during install or after install perhaps prior to the load of the splash screen? will  7.04 come with the proper drivers?

Caution: Reply from a Novice!

Press "esc" when it says "grub loading........etc". This will give you an option for recovery mode where you can specify your graphics card. When you have chosen all your settings. Restart.

If this works, you will find ATI drivers in Add/Remove. Best of luck!

---

### Post by nickoli_02 on 2007-02-16
Boot in recovery mode, then type dpkg-reconfigure xserver-xorg. Select "vesa" as your driver and go through the rest of the options to configure xserver. When you're finished type startx and it should work. From there you can install the fglrx driver

---

