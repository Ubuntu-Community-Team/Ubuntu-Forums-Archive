---
title: "How can I my ATI restricted driver?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by g0kb3rk on 2007-10-22
Hello, I have an ATI Mobility Radeon 9600 (with 15.4" monitor) graphics card in my laptop. I re-installed Ubuntu and I don't know why it didn't work in 1280*800 resolution, this has never happened before. I installed ATI restricted driver and now all I can see is a black screen when Ubuntu starts. How can I disable the restricted driver or do I have a better choice?

---

### Post by Meson on 2007-10-22
It sounds like more of a problem with your xorg.conf, or possibly with grub.  Try waiting a few minutes, if it comes up but after a long time, there is a fix.  

in /boot/grub/menu.list look for something like this (near the bottom):
```
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash
```

change splash to nosplash on that last line

---

