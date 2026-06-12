---
title: "Firefox 2.0.0.11 crash when attempting to print on HP Deskjet 6940"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by udstudent on 2007-12-23
Firefox 2.0.0.11 crashes when I attempt to print a web page.  I am using an HP Deskjet 6940 printer.  The Galeon 2.0.2 browser prints the same page perfectly.  Any ideas?  I was using Edgy Eft but upgraded to Feisty Fawn to see if problem was fixed, but the problem is identical.

Thanks.

---

### Post by zhouxing on 2007-12-24
I would suggest you to update to ubuntu 7.10 and use swiftfox [HTML]www.getswiftfox.com[/HTML]

Even in ubuntu 7.10, firefox 2.0.0.11 also crashes sometimes but swiftfox is much more stable.

---

### Post by udstudent on 2007-12-24
Identified problem.  VLC media player plugin is apparently what is causing Firefox to crash when printing.  Error is segmentation fault.  Removed VLC media player plugin and Firefox is back to normal and printing OK.

---

