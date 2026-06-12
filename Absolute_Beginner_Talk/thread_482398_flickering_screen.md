---
title: "flickering screen"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by james1978 on 2007-06-23
I have ubuntu 7.04  and for some weird reason  when im watching vids on youtube   the desktop has black lines on it  and its like the screen is bouncing   any ideas guys  ?

---

### Post by Rabindranath on 2007-06-24
My friend had the same problem in XP and after installation of the chpset utility it was ok. Or try changing the screen refresh rate.

---

### Post by RealG187 on 2007-06-24
Happened to me too. had crappy montior:
[http://kubuntuforums.net/forums/index.php?topic=3084435.0](http://kubuntuforums.net/forums/index.php?topic=3084435.0)

Goto recovery mode from grub and type "sudo dpkg-reconfigure xserver-xorg" at promt, just BS through the options until you get to refresh rate, the best bet is to chose "medium" it displays the display modes, pick on u know will work, for me I picked the lowest "640 X 480 60 HZ"

---

### Post by RealG187 on 2007-06-24
> **Rabindranath said:**
> My friend had the same problem in XP
XP is worse, I had to blindly do it, had the PC on and an other one to guide me, I used key board short cuts and did both steps twice on each machine!

---

