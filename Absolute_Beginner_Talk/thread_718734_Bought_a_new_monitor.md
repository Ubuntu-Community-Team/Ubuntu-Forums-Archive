---
title: "Bought a new monitor"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2008-03-08
Hey all,
 
Bought a new Westinghouse 22 inch flat screen - I had an old KDE 17 inch flat screen before.
 
Everything was fine with the 17 inch - but with the 22 inch I can't even load Ubuntu anymore.  I get GRUB just fine, but when it starts to load Ubuntu the screen goes black and it says "out of range"
 
What do I do to fix this??

---

### Post by taurus on 2008-03-08
You need to reconfigure your X server for the new monitor.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

