---
title: "dual boot question"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-05-21
I have a laptop with two hard drives, one with windows and one with ubuntu. How do I set up grub so that it gives me the option to boot from 1 hard drive or the other?

---

### Post by alienexplorers on 2007-05-21
Boot your live CD.
Bring up Terminal end enter
sudo grub
> Enter find /boot/grub/stage1
You will get something like (hd#,#)
enter > root (hd#,#)
enter > setup (hd#)
exit grub
reboot

---

