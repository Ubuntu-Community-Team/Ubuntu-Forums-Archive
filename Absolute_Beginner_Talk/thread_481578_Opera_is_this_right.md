---
title: "Opera: is this right?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by corney91 on 2007-06-22
Randomly I decided to run Opera from the terminal instead of the shortcut and to my surprise I got the following response:
```
dan@dan-laptop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
Opera did open, but very slowly. What does this output mean and is this restricting my ability to browse?
Thanks in advance

---

### Post by NeoLithium on 2007-06-22
The X- errors you see, are most likely the wacom devices inside your xorg.conf. It doesn't harm anything, it just means the X-server is looking for the device which isnt' there. As for the top errors...no idea what that would be.

---

