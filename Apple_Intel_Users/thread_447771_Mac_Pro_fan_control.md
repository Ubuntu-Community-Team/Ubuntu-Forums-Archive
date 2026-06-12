---
title: "Mac Pro fan control"
date: 2007-05-18
forum: Apple Intel Users
---

### Post by jdemesse on 2007-05-18
I'm trying to control the fans of my Mac Pro. From what I understand, I should first load the applesmc kernel module. If I try to load the module I get:

johan@ubuntu:~$ sudo modprobe applesmc
FATAL: Error inserting applesmc (/lib/modules/2.6.20-15-generic/kernel/ubuntu/mactel/applesmc.ko): No such device

How can I solve this ??

---

### Post by stmiller on 2007-05-18
There are several fixes for this driver in the newest 2.6.21 kernel from kernel.org. 
The error message you are getting means that ubuntu did not include that driver.

You may have to compile a kernel from kernel.org and make sure that driver is enabled:

[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

---

### Post by jdemesse on 2007-05-19
When I try to apply the mactel patches to the 2.6.21 kernel I get:

[: 6: ==: unexpected operator
applesmc-mm.patch
applesmc-mm.patch would not apply cleanly

I double checked the version of the mactel patches to make sure that isn't the problem.

---

