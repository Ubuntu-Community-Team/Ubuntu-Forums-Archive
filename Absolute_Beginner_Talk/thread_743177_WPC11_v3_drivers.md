---
title: "WPC11 v3 drivers"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2008-04-02
Hello!

I just got a laptop, not new, but not shabby. None the less, I am running Xubuntu. I am using a WPC11 v3 wireless card. I was on the Linksys website and they now have a Linux driver. I went to install it but it asked for this when creating an install package:

Linux source directory [/usr/src/linux]: /usr/src/linux
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

Any help?

---

### Post by iamclueless on 2008-04-09
im also trying to do the same and im digging through the forum

have you read this?

[http://ubuntuforums.org/showthread.php?t=112526&highlight=howto+wifi](http://ubuntuforums.org/showthread.php?t=112526&highlight=howto+wifi)

ill give it a try tomorrow.

---

### Post by Dalej on 2008-05-06
Several sources show that the linksys WPC11 v.3 uses the "Prism" chipset and that the driver should be Orinoco.  I could not get it to work until I removed the card and reinstalled Ubuntu.  The driver now is hostap and it works without a problem so far.

---

