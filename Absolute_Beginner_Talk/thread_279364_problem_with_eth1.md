---
title: "problem with eth1"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-10-17
i have eth1 deconfigured in menu-system-admin-network but when i reboot eth1 still runs..i have to sudo ifdown eth1 and the reconfigure eth0 to get my connection right...can someone help me shutdown eth1 from booting

---

### Post by jimrz on 2006-10-17
> **swp6499 said:**
> i have eth1 deconfigured in menu-system-admin-network but when i reboot eth1 still runs..i have to sudo ifdown eth1 and the reconfigure eth0 to get my connection right...can someone help me shutdown eth1 from booting

do you have 2 network cards and only ever want to use 1?
if so,check in /etc/network/interfaces and see if both eth1 and eth0 are listed. if they are then you could comment out the eth1 reference (you will need to sudo this) and then it should go to eth0 straightaway.

---

### Post by Iowan on 2006-10-17
> **swp6499 said:**
> i have eth1 [COLOR="Red"]deconfigured[/COLOR] in menu-system-admin-network but when i reboot eth1 still runs..i have to sudo ifdown eth1 and the reconfigure eth0 to get my connection right...can someone help me shutdown eth1 from booting
Disabled, deactivated, or both?
If you don't want to comment out the entire eth1 reference in **/etc/network/interfaces**, you could remove the **auto**.

---

### Post by swp6499 on 2006-10-17
thanks to both of u i got it fixed...i really appreciate it...that was eally annoying..

---

