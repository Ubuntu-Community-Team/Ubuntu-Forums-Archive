---
title: "Monitor resolution and refresh rate won't change"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2007-06-10
Almost a year i wrote my first message on this Ubuntu forum about a problem: changing monitor resolution and refresh rate. Maybe i didn't read all the post or i don't know, but to this day i haven't found a solution to fix this annoying problem. I like Ubuntu, so i don't want to throw it away because of some driver problem.
   I have a monitor from Samsung (793 DF) and a graphic card Ati Radeon 9600 Se. I tried changing the resolution and refresh rate, but nothing happens. It is alway on 800x600 (which suppose to be on 1024x768 at least with 75Hz refresh rate) with 60Hz (or 65Hz -forgot the correct number) refresh rate.

---

### Post by reclusivemonkey on 2007-06-10
Can you attach (not post) your /etc/X11/xorg.conf please.

---

### Post by alienexplorers on 2007-06-10
Have you tried adding a modeline to your monitor section of your xorg.conf file.

> # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

---

### Post by yasirm on 2007-06-11
Well, Same problem @ my side...

I can't work on refresh rate below 75 hz...

I manage to set my resolution to 1024 x 800

But in** System->Prefrences->Screen Resolution** I can not find refresh rate above 60 hz

Can any 1 guide me please.

---

### Post by Sterbik on 2007-06-16
Thanks! I'll try it!

---

