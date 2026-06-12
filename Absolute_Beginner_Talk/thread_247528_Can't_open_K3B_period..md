---
title: "Can't open K3B period."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-08-30
I can't run K3b off of Kubuntu 6.06. It's really really wierd. I go to the Multimedia -> K3B path and it sits there, without a graphical interface, but it says it's loading - then nothing.

So I try to run it in the terminal with sudo (giving it root privilages)... I've had it running literally now for a full 24 hours and the text hasn't changed after the word "password" after using sudo. Like as if it's *still loading*.

I've tried uninstall and installing it. Still the same.

Can anyone help out?

---

### Post by croak77 on 2006-08-30
Run top from a terminal and see if there is an instance of K3B running.

---

### Post by AntiFlash on 2006-08-30
i have experienced the same thing with QTparted in Kubuntu...

---

### Post by SZF2001 on 2006-08-30
I restarted my computer just to be sure. Ran from the terminal again. Same thing happened.

I remember when I had Kubuntu 5 (Breezy), there was a K3B setup thing somewhere. Anyone have a clue where it is? Is it even necessary for version 6? I've had 5 forever and I'm trying to adjust to 6, I used a fresh install and now K3B won't open. It's odd.

---

### Post by msak007 on 2006-08-31
Not sure about the specific problem you're having, but the k3b setup is a module in kcontrol - it's not available in "System Settings" for some reason. Open a terminal and type
```
kdesu kcontrol
``` and type in your password. Once it opens up, k3bSetup should be in the "System Administration" group.

---

### Post by SZF2001 on 2006-08-31
OK, so something came up in the terminal now. Looks like I have a "bad device" even though it worked fine in Breezy.

```

Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
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
DCOP aborting call from 'anonymous-9423' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9414' to 'kcontrol'
ERROR: Communication problem with kcontrol, it probably crashed.

```

EDIT: I did it without sudo and this came up:

```

Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
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
DCOP aborting call from 'anonymous-9423' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9414' to 'kcontrol'
ERROR: Communication problem with kcontrol, it probably crashed.
coleman@coleman-desktop:~$ kdesu kcontrol
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /root/.kde/socket-coleman-desktop.
Created link from "/root/.kde/socket-coleman-desktop" to "/tmp/ksocket-root"
Creating link /root/.kde/tmp-coleman-desktop.
Created link from "/root/.kde/tmp-coleman-desktop" to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Link points to "/var/tmp/kdecache-root"
Invalid entry (missing '=') at /tmp/kde-root/kconf_updatejFB2uc.tmp:1
kdeinit: Shutting down running client.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_coleman-desktop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.

```

Now I can follow the rest of your instructions. But I'm waiting for the KDE Control Center to respond - it's taking forever for the K3B setup to load.

---

