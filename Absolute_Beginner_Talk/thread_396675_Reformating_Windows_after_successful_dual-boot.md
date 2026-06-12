---
title: "Reformating Windows after successful dual-boot"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by joshswan13 on 2007-03-29
I successfully installed a dual-boot with windows xp and ubuntu which booted correctly through grub booter. However, when I reformated the windows partition, I was no longer able to access ubuntu. The computer would boot straight to windows. So I had to reinstall ubuntu to fix the problem.

I am about to format windows again. How do I avoid the problem I had last time?

---

### Post by NicoleM on 2007-03-29
i *think* that when messing with windows it overwrites the MBR which is where GRUB is located.

you can avoid reinstalling ubuntu altogether and just reinstall GRUB to regain access to ubuntu.  I'm sure someone will come by with more detailed instructions, but I'm pretty sure this can be done from the ubuntu livecd.

---

