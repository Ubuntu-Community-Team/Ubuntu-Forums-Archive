---
title: "MythTV setup"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by flatfish on 2007-01-28
I am trying to set up MythTV on Edgy using the instructions  at:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

However, mythtv-setup returns the following:

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
2007-01-28 17:30:06.419 Using runtime prefix = /usr
2007-01-28 17:30:06.461 Gnome-Screensaver support enabled
2007-01-28 17:30:06.462 DPMS is active.
2007-01-28 17:30:06.462 Unable to read configuration file mysql.txt
2007-01-28 17:30:06.463 Trying to create a basic mysql.txt file
2007-01-28 17:30:06.463 Could not open settings file /home/bender/.mythtv/mysql.txt for writing
2007-01-28 17:30:06.463 Failed to init MythContext, exiting.

Any Ideas?  Thanks.

---

### Post by crispy_420 on 2007-01-30
Try this guide:

[http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv+dapper](http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv+dapper)

Worked for me.

---

### Post by Roebi on 2007-01-31
> **flatfish said:**
> 
2007-01-28 17:30:06.462 Unable to read configuration file mysql.txt
2007-01-28 17:30:06.463 Trying to create a basic mysql.txt file
2007-01-28 17:30:06.463 Could not open settings file /home/bender/.mythtv/mysql.txt for writing
2007-01-28 17:30:06.463 Failed to init MythContext, exiting.

Any Ideas?  Thanks.


Looks like a permission problem.
Check if the mysql.txt file is existing, and if yes, that it is not owned by root.

---

