---
title: "battery icon and tab not displaying on gnome-power-manager"
date: 2010-12-05
forum: Apple Hardware Users
---

### Post by johnbendie on 2010-12-05
even after applying the patch from this thread [http://ubuntuforums.org/showthread.php?t=1469819&highlight=power+icon&page=2](http://ubuntuforums.org/showthread.php?t=1469819&highlight=power+icon&page=2)  my battery is still not displaying an icon and a tab is not present on the power manager. I use an ibook g3 dual usb. though i didn't restart after applying the patch as it was not mentioned to do so.

---

### Post by linuxopjemac on 2010-12-06
```
modprobe pmu_battery
```

I would add pmu_battery it to /etc/modules...

---

