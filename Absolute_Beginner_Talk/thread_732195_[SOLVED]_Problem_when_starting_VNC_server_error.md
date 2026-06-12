---
title: "[SOLVED] Problem when starting VNC server error"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-22
Not sure what I've done, but even after I reboot, I get the following error... my guess is that something is already running or some permissions changed:

$ vncserver

xauth: /home/xx/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/xx/.Xauthority  

New "X" desktop is xxxxxxxxx.xx.xxx.xxx:2



I know I've seen xxx:1 before, so leads me to think an instance of vncserver is already running.

---

### Post by BlizzofOZ on 2008-03-22
Found my solution:

xauth -b quit


That did the trick!

---

