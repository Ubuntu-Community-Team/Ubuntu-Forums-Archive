---
title: "Graphical Interface"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ledzeppelin265 on 2006-06-18
Hi im new to ubuntu and was just trying to load the live cd and i got a message saying that there was a problem with the X server and that it might be because my graphical interface isnt working properly. I'm not sure if this matters but i have a dual monitor set up with my primary monitor plugged into an ATI radeon 9250. im not sure if more information is needed but any help would be greatly appreciated

---

### Post by Winblowz on 2006-06-18
I don't know anything about dual-monitor setups, but did you try using the "boot from safe mode" option? That usually solves the problem most of the time. If it still does the same thing again, then post back.

---

### Post by ledzeppelin265 on 2006-06-18
that seems like it should work but Im not sure how to boot from safe mode

---

### Post by bruce89 on 2006-06-18
There is another option in GRUB, It's called "Recovery Mode", not sure how booting into it would help.  What should work is ```
sudo dpkg-reconfigure xserver-xorg
```

---

