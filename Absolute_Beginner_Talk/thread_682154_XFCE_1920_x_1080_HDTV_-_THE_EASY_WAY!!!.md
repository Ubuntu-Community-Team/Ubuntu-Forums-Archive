---
title: "XFCE 1920 x 1080 HDTV - THE EASY WAY!!!"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by 01000111 on 2008-01-29
Well...  after spending quite a bit of time trying to get xfce working with my 61" HDTV I've finally found the EASY way to do it.  Simply follow these steps:

1. Make sure your TV is connected to your PC and it's on and using the correct source.  (Mine is connected via a VGA cable)

2. Boot Xbuntu to the console

3. At the prompt, enter the following:

Xorg -configure
Xorg -config xorg.conf.new

The 2nd command should cause a black and grey grid and the mouse as an X to appear.

4.  Assuming you saw the black and grey grid, enter:

cp xorg.conf.new /etc/X11/xorg.conf


5. Reboot

That's it!  Easy as can be.  I did the above, and the hours of struggling could have been replaced with seconds of ease.  I'm now running a 61" HDTV at 1920 x 1080 and it looks GREAT!!!

If I can only fix the tiny fonts on the login screen, it'd be perfect....  ah well, I'm sure I'll figure it out eventually.


01000111

---

### Post by Joeb454 on 2008-01-29
Why is your username "71" but in binary? Lol, completely off topic, but I'm curious.

Also The above should work provided that your TV doesn't require any special drivers, and your graphics card is capable of displaying such resolutions

---

