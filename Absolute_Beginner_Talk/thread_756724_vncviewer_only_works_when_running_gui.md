---
title: "vncviewer only works when running gui"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-04-16
Hi

I've got two ubuntu servers running 7.10. One I can happily VNC onto once it's got to the login scren, but the other gives me:

> Connection Refused (111)

However, if I log the server on locally and then return to my PC from which I run vncviewer I can log onto the desktop fine. I'm wondering if the services aren't running on the problematic server until I'm logged into the GUI.

Any ideas?


Mark

---

### Post by wesleybailey on 2008-04-16
When you reboot the "problematic server" does it automatically start vncserver?

To check from command line
```

ps aux | grep xvnc

```

If it is not running, try starting the VNC Server from command line, without logging into the GUI.
```

vncserver

```

vncserver's output  message that looks something like:
> 
    New 'myhost:1 (src)' desktop is myhost:1

    Creating default startup script /home/user/.vnc/xstartup
    Starting applications specified in /home/user/.vnc/xstartup
    Log file is /home/user/.vnc/myhost:1.log


---

### Post by NeonSamurai on 2008-04-17
Hi Wesley, Thanks for the response.

Here's what I get when I follow your lead:

> mark@Cans:~$ ps aux | grep xvnc
mark  5984  0.0  0.3   2984   768 pts/0    S+   09:36   0:00 grep xvnc
mark@Cans:~$ 

Which I guess means that the service is running.

> mark@Cans:~$ vncserver

New 'Cans:3 (mark)' desktop is Canis:3

Starting applications specified in /home/mark/.vnc/xstartup
Log file is /home/mark/.vnc/Cans:3.log


I ran these commands remotely using ssh from a different PC on the same network, and like I say I can use vncviewer on the server, if I've logged into the GUI. Normally I just use ssh though.

Any thoughts?


Mark

---

### Post by wesleybailey on 2008-04-17
This proves that the vnc server does not start. 

This means "grep" found it's own process(PID), but xvnc is not running. 
> mark 5984 0.0 0.3 2984 768 pts/0 S+ 09:36 0:00 grep xvnc

Q:If you ssh into the problematic server, and run **vncserver**. Can you vnc into that server, without starting the GUI?

If you can do that, then the answer is simply to add the "vncserver" command somewhere into the server's start up.

---

### Post by bodhi.zazen on 2008-04-17
It depends on what you are using for a vnc server.

The default in Ubuntu is vino. Both vino and x11vnc log into a single, shared X session.

vncserver and vnc4server start separate X sessions for the vnc connection.

Clear as mud ?

[uwiki]VNC[/uwiki]

I advise you ssh into the server , start vncserver or vnc4server, and tunnel VNC over SSH.

[uwiki]VNCOverSSH[/uwiki]

---

### Post by wesleybailey on 2008-04-17
Oh **bodhi.zazen**, once  [again]("http://ubuntuforums.org/showthread.php?t=756939") you make a good point, and show off your well versed knowledge...

---

### Post by NeonSamurai on 2008-04-18
Thanks chaps. Here's what happens:

> mark@Cans:~$ vncserver

New 'Cans:4 (mark)' desktop is Cans:4

Starting applications specified in /home/mark/.vnc/xstartup
Log file is /home/mark/.vnc/Cans:4.log

mark@Cans:~$ vncviewer localhost:4

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""
mark@Cans:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""
mark@Cans:~$ 


This is me running vncviewer locally on the troublesome server. Does the new error message relate to a different problem rather than not having vncserver running?

Thanks


Mark

---

### Post by wesleybailey on 2008-04-18
> 
mark@Cans:~$ vncserver

New 'Cans:4 (mark)' desktop is Cans:4

Starting applications specified in /home/mark/.vnc/xstartup
Log file is /home/mark/.vnc/Cans:4.log

Good, the vncserver started on display 4.



> 
mark@Cans:~$ vncviewer localhost:4

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""
mark@Cans:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""
mark@Cans:~$

Yes these new errors refer to a new problem(X is not running).

These tests don't really prove anything because X is not available from the command line. You need a GUI to open a GUI program.

A little legend so we  don't get confused.
@Cans=NotWorkingServer
@Bottles=WorkingServer

1. Boot  @Cans server, leave at GUI login screen.
2. From @Bottles server ssh into @Cans server, and issue
```
vncserver
```
3. From @Bottles, issue(substituting the 192.168.x.x ip where @Cans is stated)
```
vncviewer @Cans:4
```

I really hope, i am not confusing you.

---

