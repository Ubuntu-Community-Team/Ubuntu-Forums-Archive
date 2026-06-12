---
title: "Network check at startup takes TOO long"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-05-09
Okay, when I start my laptop, about half the time, i don't have a networking device (ethernet or wireless) plugged in. During the startup, if this is the case, Ubuntu freezes for quite a long time while, I'm guessing, looking for the device.

Is there any way I could just tell it not to worry about it for the time being?

If so, how would i start the networking back up?

---

### Post by shdgrao on 2006-05-09
If you press Ctrl+c you can skip that wait. After if you want to set the network up you only have to go the administration menu, network administration and desativate and reactivate the network.
Hope it helps

---

### Post by adam.tropics on 2006-05-09
You should make sure the network is correctly configured, and actvated. If activated and incorrectly configured it will more than likely wait till time out, throw an error then continue to boot, all of which takes time.

Also check whether you are losing time when it tries to sync the clock with online NTP servers. In Breezy, this would always cause me problems at boot time, because it was trying to sync clock, before wireless had logged onto the net!

---

### Post by Henry Rayker on 2006-05-09
the problem is, more often than not, I boot without being connected to a network at all, so it waits until time-out. This no-network booting is what I want to speed up.

the ctrl-c works, but is there an automatic way? I don't mind activating the connection each time I boot, by the way.

---

### Post by Omnios on 2006-05-09
There is a post about turning off network set up on start up but forget where I read it it was a while ago. YOu might want to do a forum search.

---

