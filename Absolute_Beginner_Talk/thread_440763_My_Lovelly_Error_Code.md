---
title: "My Lovelly Error Code"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-11
```
nic@nic-desktop:~$ sudo kate /etc/apt/soruces.list
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-7980' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
 
```

My Source list is skrewed up, how can I fix it?

---

### Post by taurus on 2007-05-11
```
sudo nano /etc/apt/**sources.list**
```

Which release are you running anyway?

---

### Post by vigleik on 2007-05-11
The first error has to do with the wacom drivers in your /etc/X11/xorg.conf file. This probably always happens when you launch a graphical program from the command line. Try something simpler, like launching kate without sudo to see if that's the case. The solution is to remove anything wacom related from your xorg.conf file. Search the forum for "X Error: BadDevice, invalid or uninitialized input device" and you'll find many, many howtos for exactly how to do that.

The second error comes because you're not supposed to use sudo for launching graphical programs as root. Use gksudo or kdesu instead. Of course, using nano works as well.

---

