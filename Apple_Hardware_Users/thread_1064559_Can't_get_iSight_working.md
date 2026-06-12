---
title: "Can't get iSight working"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by -nat- on 2009-02-08
Like the title says i can't seem to get my isight camera (built-in) working with Ubuntu 8.04.

I've followed the tutorials [here]("https://help.ubuntu.com/community/AppleiSight") and [here]("http://ubuntuforums.org/showthread.php?t=766866"), but when I try to install the isight-firmware-tools I get this error:

The following packages have unresolved dependencies.
Make sure that all required repositories are added and enabled in the preferences.
[I]isight-firmware-tools:
  Depends: libgcrypt11 (>=1.4.0) but 1.2.4-2ubuntu7 is to be installed[/I]

I've added the repositories it says to in the tutorial, so I don't know what the problem is. :(
If someone could tell me what I need to do, or an alternative method, that would be great! :)

---

### Post by flaggh on 2009-02-09
Have you tried:
```
sudo apt-get install libgcrypt11
```

If that doesn't work, you can use getlibs to resolve all your dependencies.  Check out this thread:
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---

### Post by -nat- on 2009-02-09
Hmm.. I already have libgcrypt11 installed, but it is only version 1.2.4 and the error seems to be saying that I need at least 1.4.0. 
So I've looked for version 1.4.x and found [this]("http://packages.ubuntu.com/intrepid/libgcrypt11"), but it looks to be for 8.10. I downloaded and installed it anyway, re-installed isight tools, rebooted and still the camera doesn't work :(

thanks for the sugestions anyway!

It doesn't really matter if I can't get it working, but it would be nice a nice feature to be able to use.

---

### Post by flaggh on 2009-02-09
Assuming that you've followed the instructions correctly and loaded the firmware correctly, I've found that after upgrading the kernel or installing the isight firmware for the first time, I must turn off and on the computer, a simple reboot does not do the trick.  There's something about turning it off and on that resets the firmware.

---

### Post by cyberdork33 on 2009-02-09
> **-nat- said:**
> i downloaded and installed it anyway, re-installed isight tools, _rebooted_ and still the camera doesn't work :(

> **flaggh said:**
> i've found that after upgrading the kernel or installing the isight firmware for the first time, i must turn off and on the computer, a simple reboot does not do the trick.
+1

---

