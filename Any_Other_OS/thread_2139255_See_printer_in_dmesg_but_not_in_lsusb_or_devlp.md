---
title: "See printer in dmesg but not in lsusb or /dev/lp"
date: 2013-04-26
forum: Any Other OS
---

### Post by dargaud on 2013-04-26
Hello all,
ok, I'm more familiar with Ubuntu and usually post here, but that's actually a problem with a RedHat system. When I plug in a new printer, I don't see it in dmesg / lsusb / dev/lp unless I do:
```
sudo /sbin/rmmod ehci_hcd
```
How can I fix this permanently ? Probably something to do with /etc/modprobe.d/ or /etc/modprobe.conf but I'm not familiar enough with it.
Thanks

---

### Post by howefield on 2013-04-26
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by dargaud on 2013-04-26
Sorry, I didn't see there was a specific forum for that.

---

