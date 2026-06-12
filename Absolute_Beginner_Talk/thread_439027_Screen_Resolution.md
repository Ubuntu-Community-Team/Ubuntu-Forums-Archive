---
title: "Screen Resolution"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-05-10
Hi,
I installed Feisty and Beryl using the AIGLX HOWTO, but i cannot change the screen resolution.
Oh well i CAN but it gives a weird picture! like "mosaiques" if i should describe it.
but beryl is working fine.
Any ideas?
Thanks

---

### Post by LaRoza on 2007-05-10
Try:

sudo dpkg-reconfigure -phigh xserver-xorg

If that doesn't fully resolve it, you'll have to edit the xorg.conf file.

---

