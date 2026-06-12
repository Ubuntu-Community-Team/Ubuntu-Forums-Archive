---
title: "Can't change screen resolution."
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by minsin on 2006-05-23
Im on a laptop which normal resolution is 1280 * 1024 but when I use a live cd to go into ubuntu the resolution is like 1400 something. I tried to change it by using the change resolution option but it doesn't change. 

P.S. Im on two monitors. The smaller monitor attatched to my laptop is cracked so Im using an external monitor.

---

### Post by xXx 0wn3d xXx on 2006-05-23
Here is how to fix the screen res problem.
> 
sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

I'm not sure if it will work in the Live cd but it will work on an installed system.

---

### Post by tlogank on 2006-05-24
cool info...thanks for sharing

---

