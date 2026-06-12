---
title: "Nautilus Major Error"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-18
Today I started my system and the nautilus did not launch. So i decided to open it via terminal using the command nautilus.It showed the following error:
> 
** (nautilus:6164): WARNING **: Unable to add monitor: Not supported
nautilus: symbol lookup error: /usr/lib/libeel-2.so.2: undefined symbol: gnome_bg_new


---

### Post by billgoldberg on 2008-03-18
> **adi_das said:**
> Today I started my system and the nautilus did not launch. So i decided to open it via terminal using the command nautilus.It showed the following error:

I've had that a few times, mostly after tinkering with the system a bit.

Resetting X (ctrl + alt+ backspace) or resetting the system fixed it.

---

### Post by haytona on 2008-05-20
See here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4)

I had a similar problem and needed to manually tweak some libeel2 symlinks.

---

