---
title: "New to Ubuntu,I have an iMac question ?"
date: 2008-04-04
forum: Apple Intel Users
---

### Post by locostlee on 2008-04-04
Can Ubuntu be loaded onto an iimac, 
I have a dual boot system at the moment running "XP" and "OSX 10" but i want to remove the 'XP" and replace it with something that will actually replicate the speed that the mac can deliver, and not a whiny, lousy. useless, wast of my time system like 'XP'. please advise me what to i can install. thank you.

Lee:confused:

---

### Post by cyberdork33 on 2008-04-04
first boot to OSX and install rEFIt:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Then boot from the Ubuntu CD

Start the Partition editor, select and delete the windows partition (last one)

Exit partition editor and start ubuntu installer, when prompted, choose to install to the largest free space.

Done.

you will need the proprietary ATI driver for graphics and use ndiswrapper for WiFi after you get it all installed.

---

