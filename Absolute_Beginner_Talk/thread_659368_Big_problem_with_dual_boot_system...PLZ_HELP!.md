---
title: "Big problem with dual boot system...PLZ HELP!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by AggieTwist on 2008-01-05
Hey guys, I have been running my system with XP and Gutsy Gibbon Dual boot for about 2 months now but for some reason today it won't give me the GRUB menu and boots directly into Ubuntu.  I'm needing to do some stuff in Windows but no matter how many times I have restarted my system it boots to Ubuntu.  How can i fix this? Please help asap!

---

### Post by lswest on 2008-01-05
does the boot menu show up at all?  and could you also paste the output of ```
 cat /boot/grub/menu.lst
```?  might help

---

### Post by AggieTwist on 2008-01-05
nevermind, it was just me making a stupid mistake. i had plugged in my external monitor and when I booted it chose that as the main monitor for some reason, and it was off at the moment so the GRUB was appearing over there and my screen was staying black until it went into Ubuntu, which is my default if nothing is selected at the GRUB.  so, in short, problem solved...thanks though!

---

