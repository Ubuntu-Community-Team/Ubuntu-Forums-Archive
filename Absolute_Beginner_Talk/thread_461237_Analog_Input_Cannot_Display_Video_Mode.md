---
title: "Analog Input: Cannot Display Video Mode"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by gamewolf on 2007-06-01
After the orange loading bar goes back and forth, I get this error message. I have tried installing fedora as well with the same results. Any help would be appreciated. (I am trying to install v6.1)

---

### Post by greenstar on 2007-06-01
Using the Esc key at boot time, boot into the diagnostic mode option. 

There should be 3 options:
1. Regular startup
2. Diagnostic startup
3. Memtest

You'll want option 2. Then at the terminal try:
-if root:
```
cp /etc/X11/xorg.conf /etc/x11/xorg.conf.backup
dpkg-reconfigure xserver-xorg
```-if user:
```
sudo cp /etc/X11/xorg.conf /etc/x11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```This will reconfigure your graphical server (aka X) and hopefully fix the problem.

HTH,
Greenstar

---

### Post by secretkeeper81 on 2007-11-27
Thanks so much, this solved it for me:

```
dpkg-reconfigure xserver-xorg
```

I was having problems with and old Philips 140S LCD monitor.
It kept telling me "Cannot display this video mode" immediately after the splash screen, and I had tried both Edgy and Gutsy clean installations. It was saying it could only display 1024x768 @ 60 Hz.
I tried editing the X configuration file, but no luck either.
After I run that command you suggested, it asked me a couple of times what resolution it should display, and when I restarted X, it worked! (Actually it started with a weird 1328x768 resolution, but I was able to fix it through the System setting panel in KDE).

---

