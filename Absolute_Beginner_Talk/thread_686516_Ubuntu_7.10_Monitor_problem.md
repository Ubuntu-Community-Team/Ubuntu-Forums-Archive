---
title: "Ubuntu 7.10 Monitor problem"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by ROCValmont on 2008-02-03
I've installed 7.10 and it was working fine until I tried to select monitor setting for my Viewsonic E70. The settings were accepted but now the screen is unreadable - it's divided into three sections with the images superimposed on top of each other so I can't read them or select anything so I can put things right. Help! Is the only solution to reinstall 7.10? And if I do can I just reinstall it on top of my current installation using the same partition?

---

### Post by taurus on 2008-02-03
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by ROCValmont on 2008-02-04
Taurus, Thanks a lot - very quick reply, easy to follow instructions, now up and running again with a screen I can read! Ain't Ubuntu wonderful! Cheers...Robin

---

