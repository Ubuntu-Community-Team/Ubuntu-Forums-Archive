---
title: "DPI is not changing on Asus Infinity Pad TF700T with 12.04"
date: 2012-12-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by snakerock on 2012-12-08
Hello.

I have installed Ubuntu 12.04 (Unity version) to my Asus Infinity Pad TF700T from this forum _[http://forum.xda-developers.com/showthread.php?p=34027577]("http://forum.xda-developers.com/showthread.php?p=34027577")_
Everything works fine, but I can`t manage Ubuntu to use 220 dpi instead of default 96 dpi - interface elements are too small.

**I have tried several solutions:**

**1.** Increasing font scaling in environment configuration, but it only enlarges text, not controls.
**2.** Calling *"xrandr --dpi 220"*. System stores current dpi value as 220, but nothing changes. Seems like Ubuntu doesn`t recognize my real screen size as calling after *"xrandr -q"* I get* "0 mm x 0 mm"* size.
**3.** Editing *Xorg.conf*. Default and edited versions of *Xorg.conf* are attached, as well as *Xorg.log*

Could anybody help me with that? I will provided additional needed information.

---

