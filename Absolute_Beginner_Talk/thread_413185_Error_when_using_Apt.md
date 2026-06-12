---
title: "Error when using Apt"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by blankhorizons on 2007-04-18
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 4 during global destruction.


Basically I get this error whenever I use apt-get. Any clues?

---

### Post by Neg127 on 2007-04-19
Not to hijack your thread, but I am getting the same error while trying to run opera.  At first I was getting an error and noticed that I did not have java installed.  I installed java and now I am geting this error.

```
mike@smeagol:~$ opera
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
```

I was lazy on the initial configuration and used automatix to install a a few applications.  Have you your self used automatix to install any software?  I'm just trying to solve the issue my self but want to know if you have an altered install from automatix, or if it may be some thing else causing the error.

I will continue to work on the issue my self and let you know if I come up with a solution.


*EDIT*

Seems there is a bug with opera and and the latest libc so the issue probably is not related.
[BUG REPORT]("https://bugs.launchpad.net/ubuntu/+source/libc/+bug/103230")

*EDIT*


Thanks
Neg127

---

