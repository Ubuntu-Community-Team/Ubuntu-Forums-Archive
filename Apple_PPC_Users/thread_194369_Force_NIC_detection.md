---
title: "Force NIC detection"
date: 2006-06-11
forum: Apple PPC Users
---

### Post by Agent124 on 2006-06-11
I have a B&W G3 that 5.10 will run on just fine using the live cd but when I use the 6.04 live cd, it doesn't show my NIC at all. Is there a way to force the detection on this?

---

### Post by nkbj on 2006-06-11
When you have booted the live cd start a terminal and run **sudo modprobe bmac** to load the ethernet driver. If you want to install use the alternate cd - it detects the ethernet driver correctly.

Regards,
Niels Kristian

---

### Post by Agent124 on 2006-06-11
Thank you. Another question. While waiting for a reply, I went ahead and installed 5.10. Can I upgrade without problems, or should I start fresh?

---

### Post by nkbj on 2006-06-11
You should be able to upgrade using these steps:

1. Change all instances of "breezy" to "dapper" in /etc/apt/sources.list.

2. Add these lines to the top of /etc/modules to make sure network is working after the upgrade.
```
genrtc
bmac
```
3. Run **sudo apt-get update && sudo apt-get dist-upgrade** to make the upgrade.

Regards,
Niels Kristian

---

