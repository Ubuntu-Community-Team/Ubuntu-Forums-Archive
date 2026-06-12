---
title: "ATI remote wonder issues"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by cptInsane0 on 2007-08-22
I have been looking around, and apparently the ATI remote wonder is supposed to work with ubuntu. Everywhere I look people say it worked automatically. However, mine didn't do anything whatsoever. People mention ati_usb, but I have no idea where to get that and install it. What do I need to do to make it work?

---

### Post by dwhitney67 on 2007-08-22
Try running this command:

[FONT="Courier New"]$ sudo modprobe ati_usb[/FONT]

Then see if your remote works.  If it doesn't, then perhaps there is the slight possibility that you need modprobe (insert) another kernel driver, or worse, the kernel driver(s) you need are not present on your system, thus requiring you to rebuild the kernel from the source code (it's doable, but not for a newbie).

---

### Post by cptInsane0 on 2007-08-23
Thank you, I'll try it when I get home.  If I do end up having to rebuild my kernel, it isn't that big of a deal.  People at work can help me.  I should be good though.

---

### Post by cptInsane0 on 2007-08-24
**Updatet**: Unfortunately it says I don't have the ati_usb module. Does that mean I need to rebuild my kernel? Or can I just do an update?

---

