---
title: "xorg.conf for ADB Appledesign keyboard+mouse"
date: 2007-04-09
forum: Apple PPC Users
---

### Post by SubGothius on 2007-04-09
What input device settings should I use for my Apple ADB mouse and Appledesign ADB extended keyboard when editing xorg.conf or running "sudo dpkg-reconfigure xserver-xorg"?

Should the 1-button ADB mouse be set as "ImPS/2" or "ExplorerPS/2"?  I assume 3-button emulation should be on.

I presume the kbd should use "xorg" for rules, and some combinarion of "us", "macintosh" (or "macintosh_old"?), and "apple", but which ones correspond to the layout, model, and variant?  Layout=us, model=macintosh, variant=apple?  (I found "apple" in the /etc/X11/xorg/xkb listed under macintosh_vndrs or the like, wondering if I need to use it at all...?)

---

