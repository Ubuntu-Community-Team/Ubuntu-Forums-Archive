---
title: "Adding a mouse(plug 'n play?)"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Matusel3 on 2006-10-20
I saw some Microsoft laptop optical mice at Best Buy, my first question is: if I plug it in and reboot, will Ubuntu start using it and be happy?

Second, does Ubuntu have drivers for specific mice, or does it have a "generic" wireless driver that just works.

---

### Post by Klaidas on 2006-10-20
It depends on the mouse model. Some is not a model name :)

---

### Post by barkej on 2006-10-20
Most any mouse should work. Sometimes you may have to do a little tweaking if the mouse has "special buttons" aside from the scroll wheel.

---

### Post by CatKiller on 2006-10-20
Mouse configuration is done by the InputDevice section of your xorg.conf.

---

### Post by Matusel3 on 2006-10-20
So if I buy this mouse, will I be required to make changes in order for it to work, or will it be recognized and take off on it's own?

If I DO need to make changes, could someone either point me in the right direction of information on how to do so, or explain it for me?

Thanks a lot!

---

### Post by Rhubarb on 2006-10-20
Wireless mice are essentially the same as normal corded mice to an OS.  It should work within a second of you plugging it in.
No need to reboot.

If you've got a tilt wheel or any other fancy buttons on your mouse that you'd like enabled, just edit your /etc/X11/xorg.conf - This depends what mouse model you have.

---

