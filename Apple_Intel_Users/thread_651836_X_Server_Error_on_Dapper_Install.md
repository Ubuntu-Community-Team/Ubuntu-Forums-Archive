---
title: "X Server Error on Dapper Install"
date: 2007-12-28
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2007-12-28
I must admit that this is very agrevating. On attempting to boot from the dapper live CD using my macbook, I get the x server error relating to the lack of drivers for my screen, which I have by now come to expect. I have tried numerous ways to get around this problem, but all of the "howtos" I follow leave me stranded. Any suggestions?

---

### Post by angryfirelord on 2008-01-02
Have you tried setting your driver to vesa?

You may also want to play around with this tool:
```
sudo dpkg-reconfigure xserver-xorg
```
It helps you generate a new xorg.conf.

---

