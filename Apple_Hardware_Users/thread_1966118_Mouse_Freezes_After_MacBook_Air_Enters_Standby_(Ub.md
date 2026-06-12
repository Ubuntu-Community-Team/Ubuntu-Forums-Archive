---
title: "Mouse Freezes After MacBook Air Enters Standby (Ubuntu 12.04 LTS)"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by inspiredbylasers on 2012-04-26
After my computer goes to 'sleep', it will return to the log-in screen smoothly. All the keys will be working, but the mouse will be frozen and will remain that way until a restart.

Any fixes? Is this a known bug?

Best,
Y.

---

### Post by davidryderuk on 2012-04-27
The bug is reported below:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/968845](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/968845)

The fix involves updating the 'xserver-xorg-input-synaptics' package to a version present in Ubuntu proposed.

---

### Post by Kallun on 2012-04-28
> **inspiredbylasers said:**
> After my computer goes to 'sleep', it will return to the log-in screen smoothly. All the keys will be working, but the mouse will be frozen and will remain that way until a restart.

Any fixes? Is this a known bug?

Best,
Y.


Take a look at [my thread](http://ubuntuforums.org/showthread.php?t=1952532)

Quick and dirty fix, just uses a bash script called by pmutils to kill and restart the touchpad driver.

There's also an easier fix posted by alx80.

---

### Post by inspiredbylasers on 2012-04-28
Fixed!

Didn't know there was a reported bug, thanks for the link.

Best,

Y.

---

### Post by bradleyjones on 2012-04-28
Best off using the quick and easy SUSPEND_MODULES fix until the new synaptics package gets pushed through the main updates in my opinion

---

