---
title: "i need step by step help!!"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by e6600 on 2008-02-23
[http://ubuntuforums.org/showthread.php?t=97043](http://ubuntuforums.org/showthread.php?t=97043)
this is what i want to do, but im completely lost!!
if anyone can help me with this i would be very grateful.

thanks for your time

---

### Post by bschleusner on 2008-02-23
If you can't figure out how to do that comfortable by yourself, I would not recommend doing it.

Maybe you should start by making yourself comfortable with the terminal first.

---

### Post by bobbybobington on 2008-02-23
Wow, I think I would need help doing that. Last post said it best.

---

### Post by nick_h on 2008-02-24
First of all read the warnings in the [gentoo link](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU).

Then have a look at the [Master Kernel](http://ubuntuforums.org/showthread.php?t=311158) thread which explains how to compile a kernel.

Step 4 in this thread downloads and unpacks a vanilla kernel.  You will probably want to use the Gutsy kernel.  Type:
```
uname -r
```
to check your kernel version.
You will probably want to install linux-source-2.6.22 instead of linux-source-2.6.12 mentioned in the really old thread you linked to.

Instead of steps 6 and 7 you will need to download and install the patch referred to in the gentoo link (section 3.1).

---

