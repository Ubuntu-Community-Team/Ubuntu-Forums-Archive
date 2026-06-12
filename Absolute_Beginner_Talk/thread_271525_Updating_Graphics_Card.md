---
title: "Updating Graphics Card"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by nagates on 2006-10-04
can some tell me how to check and install the lastest drivers for my graphics card

---

### Post by az_human on 2006-10-04
If I were you, I would include the type of video card you have in your system.

---

### Post by nagates on 2006-10-04
> **az_human said:**
> If I were you, I would include the type of video card you have in your system.
i tired that once no replied, but anyways ATI Radeon 9100 128mb pci

---

### Post by podunk on 2006-10-04
Ouch! Try method 1 (2 for sure won't work for us older ATI card ownewrs) but don't expect blazing speed here.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by nagates on 2006-10-05
> **podunk said:**
> Ouch! Try method 1 (2 for sure won't work for us older ATI card ownewrs) but don't expect blazing speed here.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)that sucks, because with windows i can play most of the newer games fine, granted i still doo need to date my card, when i get the chance

---

### Post by petri on 2006-10-05
Well tell that to ATI, they have the ball.

Do use the link above, I used method 2. You just need to download the older drivers from ati.com. You can check your current driver version with pasting this in your terminal: ```
fglrxinfo
```
and in the answer the last line in parenthesis(?) you'll see
```
ubuntu@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
```
I have 8.28.8 which is the last supported driver from our precious ATI for cards below Radeon 9500.

---

