---
title: "error editing right on sources.list"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by did_skyline on 2007-10-14
I've tried editing the rights on sources.list so i can edit it, but during the process i got the 
next error message:

computer@computer-desktop:~$ gksudo gedit etc/apt/sources.list
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
computer@computer-desktop:~$


I got a popup where i can enter my pwr but i got no further response, rights haven't changed.. Can someone help me?

---

### Post by ThrobbingBrain66 on 2007-10-14
Those errors have nothing to do with editing the rights to your sources.list file.  They come from xorg,conf trying to find devices that you computer doesn't have (wacom tablet).

The command is:
```
gksudo gedit /etc/apt/sources.list
```
(you were missing the '/' before etc)

---

