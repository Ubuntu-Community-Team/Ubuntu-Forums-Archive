---
title: "Screen resolution to small for Dell Inspiron 9300"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-04-20
The previous linux ubuntu I had installed worked fine and let me have the full resolution possible - 1900-1200.  Now it is back to 800x600.  I installed the drivers that were restricted and it allowed me to get to 1024x768.  I have a geforce go 6800 graphics card. What do I do?

---

### Post by edgecoug71 on 2007-05-09
I had this problem on my HP laptop.....try this in terminal and see if it works for you....

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hope everything works out for you.....

---

