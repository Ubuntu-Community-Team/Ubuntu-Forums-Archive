---
title: "Problems with Orig. 15&quot; MBP Fan"
date: 2008-01-20
forum: Apple Intel Users
---

### Post by benzmacx on 2008-01-20
Hi,

  My laptop runs hot (normal for the orig. MBP, but still unconfortable) and in OSX I just bump up the fan speed using smcfancontrol and I have a cooler laptop.  I tried using this command:

   sudo echo 3000 >/sys/devices/platform/applesmc.768/fan1_min

however, this resulted in a Permission denied error, which just confuses me as I ran it with the sudo command...

Any Ideas?

Thanks,
Jim

---

### Post by cyberdork33 on 2008-01-20
you have to enable manual control before you can set a value.

[http://ubuntuforums.org/showthread.php?t=611596](http://ubuntuforums.org/showthread.php?t=611596)

---

