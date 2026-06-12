---
title: "Macbook 5.1: Touchpad is not working properly after upgrade to jaunty"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by acron on 2009-04-24
Hi there,

after upgrading to jaunty may MacBook suffers from the bug described here.
[https://bugs.launchpad.net/linux/+bug/337935](https://bugs.launchpad.net/linux/+bug/337935)

The short story is that usbhid is loaded before bcm5974 and grabs the touchpad instead of bcm5974 which should control the touchpad.
Removing usbhid and bcm5974 and inserting first bcm5974 and then usbhid fixes the issue. 

Still the supposed walkaround to blacklist usbhid by adding 
```
blacklist usbhid
```
to /etc/modprobe.d/blacklist.conf
and adding the following
```
bcm5974
usbhid
```
to /etc/modules does not work for me.
What can be the problem here? Any hints how I could debug this issue?

Greetings from Germany

acron

---

### Post by cyberdork33 on 2009-04-24
IDK how to fix the issue (yet) but please post to that report and let them know that it is still an issue in the final version of jaunty.

---

### Post by acron on 2009-04-25
I could fix the issue be running:
```

sudo depmod -ae
sudo update-initramfs -u

```
as described here:
[http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)

Thanks for your answer cyberdork.
> **cyberdork33 said:**
> IDK how to fix the issue (yet) but please post to that report and let them know that it is still an issue in the final version of jaunty.
I can do this no problem, but why would they assume the issue has been fixed? No patch or anything has changed the situation 'til now.

Edit: I commented the bug with the information above...

Greetings acron

---

### Post by cyberdork33 on 2009-04-25
> **acron said:**
>  I can do this no problem, but why would they assume the issue has been fixed? No patch or anything has changed the situation 'til now.
The problem was identified, there doesn't have to be a patch posted for a dev to fix the problem before release. This just confirms the bug against the final jaunty... not just a bug in the alpha/beta/RC. Thanks for your help.

---

