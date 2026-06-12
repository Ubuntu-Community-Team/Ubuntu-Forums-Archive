---
title: "Help needed with the following...."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Leviathan05 on 2007-08-08
I tried to install my web camera using some of the links I found through out the forum.  However, I never had any success in getting it working.  However, during the process I have messed up something on my install....

When ever I run an 'apt-get install <package>" it will install the package and dependencies.  However I keep getting the following....

Fetched 296kB in 2s (140kB/s)   
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by ThrobbingBrain66 on 2007-08-08
Those are harmless errors.  Usually they refer to the Wacom tablet...Ubuntu loads them even if no tablet is present.  In your case though, it may be errors from your webcam if you've set up a section for it in your xorg.conf.  To get rid of them, just remove or comment out the offending sections.

---

