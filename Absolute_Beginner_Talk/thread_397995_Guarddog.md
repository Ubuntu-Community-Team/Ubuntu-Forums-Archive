---
title: "Guarddog"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Punker on 2007-03-31
anyone get this error message while starting and closing guard dog / iptables
```


myusername@ect:~$ sudo guarddog

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
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
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
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
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
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 5119
OggS-SEEK: at 0 want 78328 got 68160 (diff-requested 78328)
OggS-SEEK: at 78400 want 520 got 0 (diff-requested -77880)
OggS-SEEK: at 0 want 78328 got 68160 (diff-requested 78328)
OggS-SEEK: at 78400 want 520 got 0 (diff-requested -77880)
myusername@ect:~$ ICE default IO error handler doing an exit(), pid = 5116, errno = 0

```

---

### Post by drakos on 2007-04-25
Yeah, I'm getting that too. Anyone have any idea why it's doing this? I It doesn't seem like it's affecting the firewall, but I'm a tad concerned by the repeating bad device error.

---

### Post by anv on 2007-05-05
same here, I'm not sure but I have extra numpad and pentablet would it possibly relate on those?!?

---

### Post by brownds on 2007-08-13
Hello Anv, Drakos, Punker.

By now you have probably solved your problem but for the record, the xorg.conf file contains references to wacom tablet devices that give rise to these errors.   Edit /etc/X11/xorg.conf to comment out (add a leading # character) all the Section..End Section lines that refer to wacom.

Importantly *also* comment out the three lines later on in the file in the ServerLayout section that refer to stylus, eraser and cursor.   Failure to comment out these lines will cause your xserver to not restart!!

Oh, and you do need to restart X for the changes to take effect.

HTH,
Denis

---

