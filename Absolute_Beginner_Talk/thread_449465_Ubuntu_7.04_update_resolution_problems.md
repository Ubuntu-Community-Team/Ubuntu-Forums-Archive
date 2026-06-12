---
title: "Ubuntu 7.04 update resolution problems"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by dz0004455 on 2007-05-20
I was running Ubuntu 6.06, and i updated it to 6.10, then to 7.04, and when i turned my computer back on, it was running in 800x600 resolution.  I ran dpkg-reconfigure xserver-xorg and told it to use 1280×1024, but i restarted the computer and it was still running in 800x600, please help

---

### Post by taurus on 2007-05-20
What video card do you have and have you installed any driver for it?

```
lspci
cat /etc/X11/xorg.conf
```

---

### Post by zodmaner on 2007-05-20
Also, try to check xorg.conf file in /etc/X11 and see if it display the correct horizontal & vertical sync rate of your monitor. On my Ubuntu 7.04 machine, I originally have the similar problem as you do. My machine can't display any resolution above 1024x768 no matter what I do. Edited xorg.conf file with my monitor horizontal & vertical sync rate fix this problem.

---

