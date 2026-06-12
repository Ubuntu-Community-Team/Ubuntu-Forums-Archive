---
title: "Errors editing a file"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by letitsnow on 2007-02-13
i get some odd errors when i go to edit a file, they don't seem to cause any problems but it still bothers me. i'm using Kubuntu 6.10 Edgy.

```
bob@thematrix:~$ kdesu kate
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified
```

---

### Post by riven0 on 2007-02-13
I had the same thing happen to me when I last tried Kubuntu. It never gave me problems, though, so I wouldn't worry about it.

---

### Post by aysiu on 2007-02-13
There's a similar "error" for ```
gksudo nautilus
``` or ```
gksudo gedit
``` There's even a bug report for it, but it hasn't been fixed. You can ignore the "error." More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by letitsnow on 2007-02-13
thanks, now i have a bigger problem. when i go to log in a little window pops up and says can't write to /tmp x-server may close in error and when i click ok it brings me back to the login screen.

---

### Post by letitsnow on 2007-02-13
well i found out that thats what happens when you have a full root partition. is it safe to shrink another partition and add to the root?

---

