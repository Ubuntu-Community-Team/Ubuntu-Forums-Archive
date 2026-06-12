---
title: "KDVI crashes"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Celil Rifat on 2006-10-10
I installed Kile and its default DVI browser KDVI, but I am having problems with KDVI. Whenever I start it it crashes and I get the following output 
--------------------
#kdvi
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QApplication::notify: Unexpected null receiver
kio (KMimeType): WARNING: KServiceType::offers : servicetype KViewShell/MultiPage not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KViewShell/MultiPage not found
KCrash: Application 'kdvi' crashing...
KCrash cannot reach kdeinit, launching directly.

------------------

I uninstalled and reinstalled kdvi, but that did not have any effect. Does anybody who has installed Kdvi with Kile successfully, have an idea how to solve this?

Regards

---

### Post by yurtfg89327tfg0o on 2006-11-15
Sorry I can't help. I've had the same problem myself.
All I can suggest is that you install xdvi (or similar) and configure kile to use that instead of kdvi.

---

