---
title: "Initializing modules..........failed"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by adam.tropics on 2005-12-01
I get a fail message on boot at 'initializing modules'. Is there a way to display the specific proble, ie, what modules are failing?

---

### Post by 23meg on 2005-12-02
Enable boot logging by turning on bootlogd. Edit the second line of the /etc/default bootlogd file to look like this: ```
BOOTLOGD_ENABLE=Yes
```
Reboot, and check out your /var/log/bootlog file to see which modules fail and how.

---

