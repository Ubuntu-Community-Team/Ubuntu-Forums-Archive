---
title: "getting write permissions."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by cleverlyinsane on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=12](http://ubuntuforums.org/showthread.php?p=12) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In trying to do several different configurations on my computer i get the following message.


X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0

Which I understand are due to some lines in my xorg.conf file that need to be deleted? but when i open the file in Kate and goto to do anything and then go save I get the following message. same message for other files as well.

The document could not be saved, as it was not possible to write to file:///etc/X11/1111.
Check that you have write access to this file or that enough disk space is available.

Hopefuly someone can help me out, by the way I'm using Kubuntu 6.04

Thank you

---

### Post by kernel tom on 2007-05-29
open up the document thru the terminal

sudo kate /etc/X11/xorg.conf

then you can save it after you edit it

suggest making a backup first

---

### Post by cleverlyinsane on 2007-05-29
Thanks for your help, tried it, and this is what i got,

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
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
Uh oh.. can't write data..
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kio_uiserver: cannot connect to X server :0.0
DCOP aborting call from 'kate-5686' to 'kio_uiserver'
DCOP aborting call from 'anonymous-5714' to 'kio_uiserver'
ERROR: Communication problem with kio_uiserver, it probably crashed.

this seems to be the cyle i go in... :(

---

### Post by kernel tom on 2007-05-29
hm

did you try using the in terminal editor?

not sure which one is with kde, but try this

sudo nano /etc/X11/xorg.conf

if not you may have to create your own file and overwrite the one that doesnt seem to be working

---

### Post by cleverlyinsane on 2007-05-29
thank you, seems to have solved the issue. Now on to the next challenge.

---

