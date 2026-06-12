---
title: "Screen Res"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by drunk_monkey711 on 2006-06-07
Hi, I just installed ubuntu today and i am compleatly new to it. 
I have a widescreen Monitor and i can't change the res to anything other than 1280 x 1024, 1024 x 768, 800 x 600 and 640 x 480. I am currently using 1280 x 1024 but everything is stretched horizontaly. Im not sure what the exact res size i need is but could someone please suggest a way for me to get more sizes.

thanks

---

### Post by xXx 0wn3d xXx on 2006-06-07
Here is how to fix the screen res problem.

> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

---

### Post by xXx 0wn3d xXx on 2006-06-07
Here is how to fix the screen res problem.

> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

---

### Post by drunk_monkey711 on 2006-06-07
Thanks alot for the help, i really appreciate it.
I hope to become a active member of this community :D

---

