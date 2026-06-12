---
title: "Resolution Problem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by pawansingh9 on 2007-12-10
I have 15 inch CRT monitor ,
I used to run ubuntu using live cd but later i decided to install it on the hard disk
when installation completed i restart my PC now as my default resolution setting is 800X600 due to 15 inch PC, when ubuntu starts my Monitor starts blinking and nothing is displayed as ubuntu is running o higher resolution

So, Kindly tell me how to set ubuntu resolution to 800x600 using commands ?

---

### Post by nikoPSK on 2007-12-10
try using xander. You can set the resolution using:

xrandr -s <resolution index from the resolutions list>
or
xrandr -s <x_res>*<y_res>

If you need help type:
```
man xrandr
```

---

