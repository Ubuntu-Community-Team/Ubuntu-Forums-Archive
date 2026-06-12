---
title: "problems with kwrite"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by tao_of _pi on 2006-07-09
I just installed Kubuntu 6.06 and was trying to install automatix using this link [http://www.ubuntuforums.org/showthread.php?t=203294]("http://www.ubuntuforums.org/showthread.php?t=203294"). i entered this into the terminal > Code:
sudo kwrite /etc/apt/sources.list
Then this error came up > X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
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
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_admin-desktop__0
and start dcopserver again.
---------------------------------

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
KCrash: Application 'kwrite' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

can anyone help?

---

### Post by Rackerz on 2006-07-09
Is this a completely new install of Kubuntu?

---

### Post by jlacroix on 2006-07-09
I'm having the exact same problem. My installation of Kubuntu was just done today. I have already configured X to use nvidia drivers, and I tested that it works by playing Penguin Racer which is showing fast OpenGL support.

I am trying to add a line to my sources.list via konsole, but I can't get in.

---

### Post by Rackerz on 2006-07-09
Kwrite is buggy from experience, have you tried kedit? It's more light weight, usually I have nothing but trouble from Kwrite.

---

### Post by aysiu on 2006-07-09
Sometimes when you run certain graphical programs from the Konsole, you get a lot of "errors." Just ignore them.

For example, I get this, but I'm still able to edit my sources.list: ```
**kdesu kwrite /etc/apt/sources.list**
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
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
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
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
ScimInputContextPlugin()
~ScimInputContextPlugin()
```

---

### Post by jlacroix on 2006-07-10
Well in my case, it causes it not to load the command at all. I'm basically at a loss as to how to add sources to my sources.list, the command line is the only way I know how.

---

### Post by aysiu on 2006-07-10
Well, first of all, try ```
kdesu kwrite /etc/apt/sources.list
``` instead of ```
sudo kwrite /etc/apt/sources.list
``` See if that makes a difference.

If not, try ```
sudo nano /etc/apt/sources.list
``` which lets you edit it totally from the command-line.

If you prefer the GUI, create a launcher for the command ```
kdesu konqueror
``` and you can temporarily browse as root and make changes to the sources.list file in the /etc/apt folder.

---

### Post by jlacroix on 2006-07-10
That did the trick, thanks!

---

### Post by Jun-Dai on 2006-07-16
FYI, regarding the **BadDevice** error: [http://ubuntuforums.org/showthread.php?p=1264009#post1264009](http://ubuntuforums.org/showthread.php?p=1264009#post1264009)

---

