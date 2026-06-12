---
title: "Stopping and Restarting Processes"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-01-11
How do you stop a running process and then restart it.  
If my network manager (/usr/bin/nm-applet) drops my connection it can never regain it.  It connects perfectly at startup (asks for permission for my keyring).  When the connection is dropped, rebooting is the only way I have gotten it to reconnect.  So next time it drops my connection I want to be able to see if stopping the process and then restarting it will fix the problem without rebooting the entire computer.

As I said, the program is /usr/bin/nm-applet.  What would my command line be to stop and then restart it?  If it makes a difference it puts a system tray icon up next to my clock and I don't know if that requires any additional code to get it to re-appear up there.

---

### Post by jd65pl on 2007-01-11
For stopping and starting network cards try where ethX is your network decive (wifi should be like wlan0)

to stop
```
sudo ifdown ethX
```
to start
```
sudo ifup ethX
```

---

