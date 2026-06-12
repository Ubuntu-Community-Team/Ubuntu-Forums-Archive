---
title: "Can I run 32 bit applications on a 64 bit operating system"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by jmucha on 2007-11-23
Can I run 64  bit Ubuntu 7.1 on a 32 bit laptop with a 2310 processor? I didn't realize I had a 32 bit but my 64 bit installation appears to be okay other than no wireless which I'll fix later. Can I leave it the way it is?

---

### Post by ptn107 on 2007-11-24
Ubuntu 32-bit (i386) can run on a 32 or 64-bit** processor.  Ubuntu 64-bit (amd64) only runs on 64-bit processors.  Your laptop must be 64-bit capable in this case.  Otherwise you would get this error on boot: **"Your CPU does not support long mode use a 32 bit distribution."**

To answer your question, yes you can use 32-bit applications on a 64-bit operating system, but it's kind of a waste of processing power.  (You cannot use 64-bit applications on a 32-bit operating system however.)

***Running Ubuntu 32-bit on a 64-bit capable processor is basically a waste of the processor's capabilities.  If you have a 64-bit cpu use Ubuntu 64-bit unless problems arise that you cannot fix.*

---

### Post by rsambuca on 2007-11-24
Open a terminal and post the output of this command:

uname -m

---

