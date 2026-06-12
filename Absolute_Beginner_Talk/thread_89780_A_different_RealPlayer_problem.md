---
title: "A different RealPlayer problem"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by beijingjj on 2005-11-13
I've read the other recent threads on installing RealPlayer10Gold.bin.  My problem seems to be different.

It installed correctly but when I attempt to run it I get this error:

$ realplay

(realplay.bin:9932): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:9932): Gdk-WARNING **: cannot set locale modifiers
Pango:/etc/pango32/pangorc: Error opening config file: No such file or directory
/usr/bin/realplay: line 75:  9932 Segmentation fault      $REALPLAYBIN "$@"

Any idea what's wrong?

---

### Post by beijingjj on 2005-11-14
I found that uninstalling scim (for Chinese input) fixed this problem.

---

