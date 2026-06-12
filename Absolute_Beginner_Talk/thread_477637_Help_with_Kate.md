---
title: "Help with Kate"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-18
Whenever I try to open a file using kate I get the following error:

[1] 7290
sudarshan@Lucky-Linux:~$ X Error: BadDevice, invalid or uninitialized input devi                                                              ce 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.

Even though the file finally opens, these errors bother me. Can anyone help please?
Thanks.

---

### Post by vexorian on 2007-06-18
I also always saw those things back in breezy when I used kate from konsole, I wouldn't worry since they are apparentally for debug or something like that, but report the bug in launchpad.

---

### Post by linuxnovice on 2007-06-18
I dont know how to start launchpad to report bugs. Can you please tell me where to lauch this app? 
Thanks

---

### Post by Bachstelze on 2007-06-18
You must delete the lines about the Wacom devices in your xorg.conf.

---

