---
title: "ndiswrapper trouble"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by jimi_bond on 2006-12-13
Hi I'm quite new to this. I've been trying to get a wireless usb device to work using ndiswrapper. The first thing it says is "make sure there is a link to the kernel source from the modules directory. The command 
ls -l/lib/modules/'uname -r'/build 
should have at least 'include' directory and .config file. When I run this command I get. No such file or directory.
If I look in the /lib/modules/2.6.17-10-386/build dirctory there is a modules file but it says link broken, but there is no config file. The broken link is looking for /lib/modules/2.6.17-386/linux-headers-2.6.17-10/modules, and there is no modules directory there. How do I get roumnd this or fix it?
Cheers.

---

