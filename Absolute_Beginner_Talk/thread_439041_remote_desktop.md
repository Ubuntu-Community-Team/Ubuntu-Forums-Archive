---
title: "remote desktop?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-05-10
Hi!
I need to remote desktop over internet (not lan). Is there any application that makes it possible?

Regards

---

### Post by BHelts on 2007-05-10
You can try hamachi, which is a virtual VPN client which doesn't need port forwarding.
If you have control of your routers, you can use any vnc, i use tightVNC and forward your chosen port to your machine.

---

### Post by Ek0nomik on 2007-05-10
You have two options really.

SSH & VNC.

Both have their benefits.

Ubuntu comes with remote desktop support by default.  System/Preferences (or Administration, I can't remember.  I'm sitting in lecture right now).  It uses a program called Vino.  It isn't the best software out there.  With Edgy, I used something called x11vnc.  It worked much better, but I don't know if it works on Feisty yet.

As far as viewing on VNC goes, I always use xvnc4viewer.

---

### Post by mlentink on 2007-05-10
Feisty is Remote Deskop enabled. Go to System>Preferences>Remote Desktop to enable it. You can then control your Fesity-machine form any machine capable of running a vnc-viewer (I use RealVNC viewer, which works), if you eable port-forwarding in your router to the correct port.

I use it daily without a hitch.

You can also control a windows desktop from Feisty if you want, and have enabled it on the windows machine. The client for this is built into FF

---

### Post by MOS95B on 2007-05-10
What if you want to go the other way, run a Win machine from feisty??  (Hoping this helps the OP and not hijacking)

---

### Post by mlentink on 2007-05-10
Windows also has a facilty for remote desktop control (RDP), I don have a windows machine at my disposal here, so I can tell you exactly which commands to use. But it can be controlled with the Terminal Services Client, which incidentally also handles VNC, XDMCP (for remote login to a Linux desktop) and ICA (for Citrix-based systems).

---

### Post by mlentink on 2007-05-10
Just heard that in Windows, you enable remote desktop through the sytemconfigurations Right click on This Computer, select the remote connections tab and check enable remote desktop

---

### Post by silent1643 on 2007-05-10
[http://www.tightvnc.com](http://www.tightvnc.com)

---

### Post by mlentink on 2007-05-10
Yeah. Or [www.realvnc.com]("http://www.realvnc.com")
But why not use the built-in facilities first? If the OP finds them lacking he can always look for something more suitable later on.

---

### Post by the_axiom on 2007-05-11
What do I need to use the built-in remote desktop?
I've tried it allready. My friend enabled it and gave me "the command". It typed it in the terminal but it didn't work. But it worked when trying on myself. One thing i can't understand is how the command line I get can use the computers name to indentify the computer you want to connect. There could be multiply computers with same name...

---

### Post by llamakc on 2007-05-11
What command did your friend give you?

---

### Post by the_axiom on 2007-05-11
Now I'm not in ubuntu. But it was a command which he got when he activated the built-in remote-desktop.
And compared to mine, the only unique thing was the name of the computer e.g. mycomp-desktop.

---

### Post by the_axiom on 2007-05-11
bump

---

### Post by lazyart on 2007-05-11
Find the Terminal Services Client in Applications>Internet

If it's across a lan you enter the computer name.  If it's the internet you'll probably need the IP address (which can change day-to-day or even hour-to-hour) instead of the name.  Select VNC as the protocol (not RDP).  Click connect.

If you're using Windows and trying to connect to a Ubuntu box you'll need a VNC viewer (there are dozens of 'em).  When asked for the Server, enter the name or IP address.

If the port is open/forwarded correctly (usually 5900) you should see the desktop.

---

