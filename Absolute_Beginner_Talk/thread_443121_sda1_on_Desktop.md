---
title: "sda1 on Desktop"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by HornedBeast on 2007-05-14
I have an icon for my first partition on my hard drive called sda1 which is my Windows XP partition.

I do have read and write access to it from my Ubuntu intall on my second partition and its all working hunky dorey!

However, I was wondering if there was a way of removing the icon from the desktop at all? I dont mind being able to get to it from the "Computer" menu using Nautilus, but I just didnt really want the icon on my desktop all the time? It seems to appear automatically at boot.

Any ideas how to make it not automatically get put on the desktop?

Thanks in advance.

HB

---

### Post by HornedBeast on 2007-05-14
Oooooo. Actually figured this out for myself in the end.

Heres how:

Loaded "gconf-editor" and found "Apps - Nautilus - Desktop" and unchecked 'Volumes Visible'.

Hope this helps other peopl!

---

