---
title: "Mouse scroll wheel issue"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by aeroRunner on 2006-03-17
While I am browsing the internet if I spin the scroll wheel on my mouse too fast it tells Firefox to go foward or back one page depending on which way I am spinning the scroll wheel.

This is very annoying because I had not intended to go foward or back.  Can anyone explain how I might fix this problem?  Thanks.

---

### Post by fog on 2006-03-18
Add in Section "Input Device", in your /etc/X11/xorg.conf, this line:
Option  "ZAxisMapping"  "4 5"

---

