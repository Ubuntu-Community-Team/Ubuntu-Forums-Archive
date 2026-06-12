---
title: "Screen resolution won't change!"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by XLostSpartanX on 2007-01-20
So I have a Gateway laptop that I just installed Ubuntu 6.10 on.  Everything works great except for the fact that I can't change the resolution.  I have searched around and found a few ways to do it, but it still doesn't work.  I added it to the file, and I used the little GUI based thing, but the resolution of 1280x800 still wont show up.

-Nick

---

### Post by XLostSpartanX on 2007-01-20
Bump.... I need help pretty quickly.

---

### Post by Duppy on 2007-01-20
Can you use that resolution on WindowsXP?

---

### Post by jonny on 2007-01-20
Most laptops use Intel integrated graphics.  For some reason, Ubuntu doesn't by default install an incredibly useful program called 915resolution that gives you better control over the resolutions on offer with Intel graphics.

Use Synaptic Package Manager to install 915resolution and reboot.  You'll probablly find that your panel's native resolution is selected automatically; if not, try running ```
sudo dpkg-reconfigure xserver-xorg
``` and then restart again.  If all else fails, try reading the manual for 915resolution and  make adjustments accordingly.

---

### Post by XLostSpartanX on 2007-01-20
> **jonny said:**
> Most laptops use Intel integrated graphics.  For some reason, Ubuntu doesn't by default install an incredibly useful program called 915resolution that gives you better control over the resolutions on offer with Intel graphics.

Use Synaptic Package Manager to install 915resolution and reboot.  You'll probablly find that your panel's native resolution is selected automatically; if not, try running ```
sudo dpkg-reconfigure xserver-xorg
``` and then restart again.  If all else fails, try reading the manual for 915resolution and  make adjustments accordingly.
I love you.

---

