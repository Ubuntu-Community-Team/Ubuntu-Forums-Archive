---
title: "No scroll"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-03-03
My mouse has a scroller, but it doesn't work. Why? Ubunutu 5.10.

---

### Post by soce_32 on 2006-03-03
Try running `sudo dpkg-reconfigure xserver-xorg`.  It should ask you a question about detecting scroll events.

Basically, this will add 'Option "ZAxisMapping"   "4 5"' to your /etc/X11/xorg.conf file under the mouse section.

---

### Post by Zdravko on 2006-03-03
soce_32, thank you!

---

