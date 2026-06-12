---
title: "Getting Ubuntu to the edge of monitor screen"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by simonfoley on 2007-02-13
I was having a problem with Ububtu with my Panasonic monitor in that there was a 25mm/1 Inch border all the way around the outside of the window, making the Ubuntu Window quite small.  I can change this with the monitor setting but then have to change the settings back when I go back to Windows.

I installed the Nvidia drivers for my PC as it was really jerky but this had no effect on the border issue. I tried changing the resolution and so via Ubuntu but had no success.  Any ideas anyone?

S

---

### Post by Crooksey on 2007-02-13
In Linux set it up how you like, no edges etc, then in windows use the nvidia control program to "move" or "stretch" the screen so it fits the outside, this will be independent of the OS and will then have no effect when you boot into ubuntu.

---

### Post by teaker1s on 2007-02-13
terminal
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

find out the technical spec's for your monitor and you can set them with the graphical program this command launches

after above
also on system tab on desktop you can select screen and change there-once xserver has been set up

---

### Post by Crooksey on 2007-02-13
I remember an old command I use to run to fix this on Linux aswell, sorry not to mention before but its 

```

xvidtune

```

---

### Post by simonfoley on 2007-02-14
You are stars guys.  Thanks

S

---

