---
title: "[SOLVED] Problem with my intel 930m graphics driver"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Rocket2DMn on 2008-03-28
Because you transferred the drives between computers, your video settings are most likely incorrect.  You can fix that by telling X to autoreconfigure itself by doing CTRL+ALT+F1 at the blank screen to get to a tty, then run
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/gdm start
```

---

