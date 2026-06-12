---
title: "removed restricted driver, white screen only"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by jettapup on 2007-07-28
Had original problem which snow-balled 
original problem was terminal window was "blank, but hovering curser along top of window caused context menues to appear, 
Found advise on forums that restricted driver, (nVidia) was the problem
removed restricted driver, rebooted, and get log on screen, then get a a white rectangle in the middle of a black field, then a completey whit screen.:(
what next if not a reinstall??  Its a stand-by box but would rasther not reinstall as the TV Tuner card et.al worked.
Jetta

---

### Post by 5-HT on 2007-07-28
Did you change the video driver in /etc/X11/xorg.conf from 'nvidia' (nvidia's binary) back to 'nv' (open source 2d alternative)? You could always try using 'vesa' if 'nv' is giving you those problems.

---

### Post by nesman89 on 2007-07-28
go to terminal  ctrl-alt-F1

type sudo dpkg-reconfigure xserver-org (it might be xserver.org) i can't remember

go through the setup and select Vesa driver and 1024x768 resolution.

hope this helps.

---

### Post by fistfullofroses on 2007-07-28
or ctrl+alt+f1

sudo nano /etc/X11/xorg.conf

then change 'nvidia' to 'vesa'

then change the first resolution listed on 16 and 24 to 1024x768

---

### Post by jettapup on 2007-07-28
well its xserver-xorg, got the program to run, changed to vesa from nv, 1024 x 768, no change, still white screen after log in.
tried to do something with xorg.conf... started vi, no clue as to how to get the file to be eddited, no help available from vi
Thanks
jetta

---

### Post by jettapup on 2007-07-31
Thanks for the nano suggestion, was able to change .conf to vesa , but still a blank white screen after log in..sigh

---

