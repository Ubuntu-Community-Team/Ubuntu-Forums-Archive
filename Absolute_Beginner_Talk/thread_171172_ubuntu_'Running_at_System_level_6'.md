---
title: "ubuntu 'Running at System level 6'??"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-05-06
QuestioN:
does anyone know what Running at System level 6 means?
------------------------------------------------------------------------
I've checked the log files and seen on startup that it's switched from 5 to level 6 and thought that might be an error at the root of my ubuntu problems. 
------------------------------------------------------------------------

---

### Post by Mustard on 2006-05-06
I think that might be the runlevel for shutdown.  Don't quote me on that though. :)  If I recall correctly thats what I see when I give the order for the system to shutdown, so your log might just showing your the entries for when you tell the system to shut down.

What are your 'problems' btw?

---

### Post by Rinzwind on 2006-05-06
Normal Linux runlevels:

Runlevel 0: Halt System - To shutdown the system
Runlevel 1: Single user mode
Runlevel 2: Basic multi user mode without NFS
Runlevel 3: Full multi user mode (text based)
Runlevel 4: unused
Runlevel 5: Multi user mode with Graphical User Interface
Runlevel 6: Reboot System 

Ubuntu does not make any difference between runlevels 2 to 5 (they are all there for the local admin to configure to his or her taste):

1 	Single-User Mode 	Does not configure network interfaces or start daemons, provides a login prompt.
2-5 	Multi-User Mode 	Normal operation. X Windows is started if configured to do so.


6 is reboot. So yes it's weird if you are running on 6.

---

### Post by N3wtR0ckn13 on 2006-05-06
[QUOTE=Rinzwind]Normal Linux runlevels:

Runlevel 0: Halt System - To shutdown the system
Runlevel 1: Single user mode
Runlevel 2: Basic multi user mode without NFS
Runlevel 3: Full multi user mode (text based)
Runlevel 4: unused
Runlevel 5: Multi user mode with Graphical User Interface
Runlevel 6: Reboot System 

Ubuntu does not make any difference between runlevels 2 to 5 (they are all there for the local admin to configure to his or her taste):

1 	Single-User Mode 	Does not configure network interfaces or start daemons, provides a login prompt.
2-5 	Multi-User Mode 	Normal operation. X Windows is started if configured to do so.


6 is reboot. So yes it's weird if you are running on 6.[/QUOTE]

eh, i don't think i'm running on runlevel 6 anymore. i've just seen this a few times and was curious what this waas.

---

### Post by ncappel1 on 2006-05-07
isn't there also a runlevel "S"?

---

