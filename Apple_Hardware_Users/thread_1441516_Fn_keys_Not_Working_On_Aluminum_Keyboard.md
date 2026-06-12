---
title: "Fn keys Not Working On Aluminum Keyboard"
date: 2010-03-28
forum: Apple Hardware Users
---

### Post by jaco223 on 2010-03-28
I've noticed that my field keys don't work on my iMac. The  eject key works, but if I try ALT+F2 I get nothing. I there something I need to reconfigure to get my keyboard full functioning?

---

### Post by zacbarton on 2010-03-28
jaco223 try adding "options hid_apple fnmode=2" to /etc/modprobe.d/imac.conf to get the function keys working as normal.

---

### Post by jaco223 on 2010-03-29
> **zacbarton said:**
> jaco223 try adding "options hid_apple fnmode=2" to /etc/modprobe.d/imac.conf to get the function keys working as normal.

zacbarton

Thanks! that did the trick. You help is greatly appreciated.

Jaco

---

