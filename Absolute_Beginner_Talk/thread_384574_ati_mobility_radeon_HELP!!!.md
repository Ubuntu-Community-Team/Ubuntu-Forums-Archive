---
title: "ati mobility radeon HELP!!!"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by qyte on 2007-03-14
I have found the following and did it but still the whole system is too laggy without it even consuming half my ram :(

[http://ubuntuforums.org/showthread.php?t=99395&highlight=M6](http://ubuntuforums.org/showthread.php?t=99395&highlight=M6)

Video card:
---------------
If you have an ATI Mobility Radeon M6 LY card which is installed in laptops like the Dell c610 Latitude, then remember to switch the driver in xorg.conf from "ati" to "radeon" otherwise 3D accelleration will not work. The 3D acceleration also requires quite a bit of video memory so you may have to switch your color depth from 24 bit to 16 bit in xorg.conf.

Is there still something i need to do?
HOW DO I ENABLE THE DAMN 3D ACCELERATION?
PLEASE!!!

---

### Post by finer recliner on 2007-03-15
take a look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

