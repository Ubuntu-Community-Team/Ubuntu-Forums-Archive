---
title: "Error message from macfanctld on my iMac"
date: 2012-08-17
forum: Apple Hardware Users
---

### Post by LtTuvok on 2012-08-17
Hello,

I installed macfanctld amd it is running now on my iMac. macfanctld -f shows me the following error messages:

Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual

The command ps -ef |grep macfanctld shows me the following:
root      1111     1  0 06:24 ?        00:00:19 /usr/sbin/macfanctld

Does any one knows how to solve this issue?

Regards, Lt.Tuvok

---

### Post by LtTuvok on 2012-08-17
I changed permissions and the problem is solved.

---

