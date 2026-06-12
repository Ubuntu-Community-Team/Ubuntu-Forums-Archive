---
title: "Problems with Ubuntu and OS X dualboot"
date: 2010-01-10
forum: Apple Hardware Users
---

### Post by hobbleDHoy on 2010-01-10
I recently used BootCamp on my MacBook(2.1) to partition my hdd and install Ubuntu(karmic), and Im having trouble with the wireless connection. On the mac partition it works fine, but on Ubuntu there are no wireless networks shown in the network-dialog. Previously I had only a Linux-partition on the same machine, and this was not a problem. Also the trackpad does not work at all. Does anyone know what to do about the network connection? Also I should mention that I first installed the AMD64-version of Ubuntu, which worked fine even though my macbook uses intel. Im tempted to just go back to the amd-version, any views on that?

---

### Post by Sef on 2010-01-10
Moved to Apple Users.

---

### Post by linuxopjemac on 2010-01-11
Hook your computer up to a wired connection and update your software:

```
sudo apt-get update
sudo apt-get upgrade
```

Then try to look into the Administration -> Hardware, maybe you'll find the wireless driver there. If not we have to manually do it.

Your apple touchpad works with the appletouch module

```
modprobe appletouch

```
If you want to have it at boot add it to the /etc/modules list

---

