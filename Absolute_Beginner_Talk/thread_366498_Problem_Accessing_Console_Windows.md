---
title: "Problem Accessing Console Windows"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Steel Bovine on 2007-02-20
I have an ATI Radeon X1900GT.  After losing the monitor signal just after selecting "Install Ubuntu" from the Live CD menu, I knew I was in for problems.  I heard the drums of the startup sound, though, and I knew something must have happened: so I pressed ctrl-alt-F1 to get a console window.  Signal OK!  Now Ctrl-alt-F7..  Gnome OK!  All's well?  No.  On reboot, I get the same problem.  So I get new drivers from ATI for my sweet card.   Reboot, check to make sure I'm okay, and I am.  When I reboot, I go straight to Ubuntu's GUI.  But now let's say I press ctrl-alt-f1..  I get a bunch of weird colors.  Same for F2-F6.  Can't get to a console window.  ctrl-alt-f7 brings me back to GUI just fine.

Anyone have any idea what's up?

---

### Post by n8bounds on 2007-02-20
anything interresting in any of your logs?

/var/log/syslog or /var/log/messages 

say ```
 dmesg >> ~/mydmesg.tx 
``` and read that text file looking for odd stuff...maybe even post them up here...

there's also a /var/log/Xorg.0.somethingoranother

---

