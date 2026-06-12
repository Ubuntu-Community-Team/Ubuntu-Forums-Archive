---
title: "How to shut down/restart headless server using vnc"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-22
I have my server up and running and successfully remote into the desktop with Putty and TightVNC.

I have found commands to shut down and restart from the command line.

While in VNC GUI, I can click on Applications to shut down, restart, etc, but nothing happens.

Is there a way to shut down or restart in GUI VNC?

---

### Post by njparton on 2008-03-23
If I were you I'd install openssh server and use putty in windows to connect to it. You can then use the command line directly from your windows computer to do as you wish (including shutting down and rebooting).

Most people who use servers don't have a desktop installed :)

---

### Post by Dr Small on 2008-03-23
+1
SSH on the server and Putty or SSH-Client on the other machine makes a beautiful setup for all your needs. No need for a desktop on a server.

Dr Small

---

### Post by ghost_ryder35 on 2008-03-23
> **BlizzofOZ said:**
> I have my server up and running and successfully remote into the desktop with Putty and TightVNC.

I have found commands to shut down and restart from the command line.

While in VNC GUI, I can click on Applications to shut down, restart, etc, but nothing happens.

Is there a way to shut down or restart in GUI VNC?
open a terminal window and type
```
halt
``` to shutdown
or "ALT+F3"
```
halt
``` to shutdown

---

