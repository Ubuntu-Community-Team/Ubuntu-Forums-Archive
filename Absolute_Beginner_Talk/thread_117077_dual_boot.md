---
title: "dual boot?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2006-01-14
i want to make a dual boot ubuntu 5.04 and xp in tha same hd (different partition of course). can anyone help me? when i install ubuntu it doesn't scan my xp installation .what do i have to change in grubloader?

---

### Post by sharke on 2006-01-14
Take a look here     [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Regards
Sharke

---

### Post by aysiu on 2006-01-14
I, too, would recommend the hermanzone guide for dual booting (it's the fifth link of my sig because I recommend it so highly). Nevertheless, there are some times (rare though they are) when Grub will *not* add Windows to the boot menu even when Grub is installed to the MBR.

Please consult hermanzone's guide, and if you're pretty sure you're installing Grub to the MBR, please post the output of these two command: ```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

