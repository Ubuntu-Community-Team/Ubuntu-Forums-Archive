---
title: "Resolution missed up"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-15
The resolution using the default Xorg driver is completely missed up in my PC. I get 1024x768 but only at 60 Hz. The problem is that, this is my 4th Ubuntu installation. The first 2 times, I got normal resolutions and refresh rates, but now, I only get this.

Is there some way to change this, without installing video card drivers?

---

### Post by xXx 0wn3d xXx on 2006-04-15
Here is how to fix the screen res problem. In terminal type:

> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

---

### Post by user1397 on 2006-04-15
[quote=Amorphous_Snake]The resolution using the default Xorg driver is completely missed up in my PC. I get 1024x768 but only at 60 Hz. The problem is that, this is my 4th Ubuntu installation. The first 2 times, I got normal resolutions and refresh rates, but now, I only get this.

Is there some way to change this, without installing video card drivers?[/quote] I use 1024X768 resolution @ 60 Hz and it looks fine.

---

