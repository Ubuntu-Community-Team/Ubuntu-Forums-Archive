---
title: "Ubuntu wont let me install edgy"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Sheepish on 2006-11-25
Hi im currently using Dapper with a kde desktop, i tried this, and THIS is all i got;
```
joe@OsX:~$ gksu "update-manager -c"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  warnings.warn("apt API not stable yet", FutureWarning)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
extracting '/tmp/tmpW9iWQn/edgy.tar.gz'
authenticate '/tmp/tmpW9iWQn/edgy.tar.gz' against '/tmp/tmpW9iWQn/edgy.tar.gz.gpg'
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/tmp/tmpW9iWQn/DistUpgradeViewGtk.py:360: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
  self._term.realize()
joe@OsX:~$ gksu "update-manager -c"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

and back to the command line! im confused, i miss the nice high res usplash.

Please help

another thing it says it cannot update libwnck

maybe this will help.

thanks

---

### Post by mackyman on 2006-11-25
This might not help you fix your problem, but it solves it in a way...

Backup your home folder and do a fresh install with edgy instead. 

The upgrade broke quite much for me, so I did a fresh install instead.
Edgy have a bit of "unstable feeling" about it... At least for me.

---

### Post by cilynx on 2006-11-25
try:
```
sudo update-manager -cd
```

---

