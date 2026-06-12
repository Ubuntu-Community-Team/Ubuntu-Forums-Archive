---
title: "[SOLVED] Maemo Accessory help"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-18
i tried to download two of these files now from gnome.look.org

and when i open the deb file i get this error 

Status''ERROR wrong architecture 'armel'

whats this mean?

---

### Post by Daveth on 2007-09-18
this looks you are using the "wrong" cpu for your download. As far as I can see from this

"Debian armel runs on a minimum CPU of ARMv4t (e.g. the ones in Cirrus Logic ep93xx and in Compaq iPAQs but not StrongARM) and by default the compiler generates code for armv4t (rather than the usual GCC-4.1 ARM target of armv5t)."

[http://wiki.debian.org/ArmEabiPort#head-c19223b1bb614d3065443309d6b8fedc8944ce46](http://wiki.debian.org/ArmEabiPort#head-c19223b1bb614d3065443309d6b8fedc8944ce46)

your download is specific to this debian architecture. Never come across debian armel before though.

---

