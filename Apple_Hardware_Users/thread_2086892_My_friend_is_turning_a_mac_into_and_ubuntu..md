---
title: "My friend is turning a mac into and ubuntu."
date: 2012-11-22
forum: Apple Hardware Users
---

### Post by jonathandawdy on 2012-11-22
simple question my friend is wanting to fully delete Macintosh and get Ubuntu he has a live boot of Ubuntu but mac wont let him open it he doesn't know how to live boot in mac.

---

### Post by howefield on 2012-11-22
Thread moved to the "*Apple Users*" forum.

---

### Post by sahabcse on 2012-11-22
What error you getting when you booting into the Live CD

---

### Post by jonathandawdy on 2012-11-23
> **sahabcse said:**
> What error you getting when you booting into the Live CD

----------------------------------------------------------------
I'm sorry hes real young so not really bright but when he restarted the computer he pressed alt dozens of times when he saw the white screen but then it just showed a padlock.

---

### Post by sahabcse on 2012-11-23
If you press the Alt-key the menu of boot options appear and you will be able to select to boot from CD. On some Macs holding down the C-key will work and directly boot from CD without the hassle of selecting something in a menu.

Some MacBook Pro s (notable MBP 5,1-3) will show just a white underscore instead of booting to the LiveCD's graphical user interface. That is due to nouveau failing on NVidia's 9600MGT. Enabling nouveau.noaccel=1 as a kernel boot option (will fix this. Also pressing F6 during LiveCD boot and selecting nomodset or using save graphics mode with F4 has proofed to work.

---

