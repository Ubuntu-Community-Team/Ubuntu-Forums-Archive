---
title: "remote desktop solution (osx client, ubuntu server)"
date: 2006-09-16
forum: Apple PPC Users
---

### Post by brettfavre on 2006-09-16
I would like a way to use a remote (graphical) desktop to connect to my ubuntu server.  I have tried the vnc solution and the performance is terrible.  I've heard of the possibility of using X11 forwarding through ssh but I can't seem to grasp the concept.  I realize apple packages the xwindow system with osx, so it shouldn't require too much configuration should it?

In a nutshell have no problem connecting a terminal through ssh, but have no idea how to get the graphical desktop running on os x.  

Thanks in advance

---

### Post by ristosu on 2006-09-16
In principle, you add -X when starting an ssh session (X11Forwarding has to enabled on server side; you can check this, after logging in, with 'echo $DISPLAY', it should show 'localhost:10'). Then you can run any X program on the remote host and will get the window on your local screen. Maybe you can start a whole gnome-session, not sure...

I should add that, since X was designed for LANs and VNC for (slower) WANs, the performance can be even more terrible...

---

### Post by piccard on 2006-11-01
First of all, you've got to use the X11 terminal that you can install from your OS install disk.  then, when ssh'ing to the remote machine, you have to use the -Y option.  example:
```
> ssh -Y [hostname]
```

---

