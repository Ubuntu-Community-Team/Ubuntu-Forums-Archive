---
title: "Ubuntu newbie having problems with remote desktop"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by martydavis on 2008-03-15
Hi all.  I'm usually pretty good at researching out solutions to issues I'm having, but I keep running into dead end after dead end with this problem.

I am trying to remote into a Ubuntu 7.10 PC on my home network from my wireless connected Windows XP laptop.  I'm trying to remote admin the Linux PC for practice for when I dump my Windows Server 2003 and go Ubuntu Linux for my home file server.  I want to be able to do everything on my test PC before wiping my existing server.

I have Remote Desktop running on my Linux machine and the screen locked.  

I've unchecked the box "Ask you for confirmation" because nobody is sitting there watching for somebody to log in.

I've enabled remote login from >System >Administration >Login Window >Remote tab

When trying to connect with the VNC viewer my connection errors out with "Unable to connect to host: Connection timed out (10060)

I can ping my Linux PC

Anybody have an idea why I can't get to it?  Any config files I need to edit?

---

### Post by handydan918 on 2008-03-15
One possibility is your firewall settings. If you have a firewall tool installed (firestarter, guarddog, etc.) check and see if it is configured to open the relevant ports. 
( Can't recall for sure which ports - 5001 maybe? Depends on the remote desktop protocol in use, I think.)

---

### Post by rug77 on 2008-03-15
I'm not on XP at the moment, so take this with a pinch of salt, but from memory I use PUTTY to establish a connection to <IP address of Ubuntu machine:5000), and then I could use the VNC viewer.

PUTTY is easily found as a free download, and is tiny prog.

Good luck.

Rug.

---

### Post by ghost_ryder35 on 2008-03-15
Putty would be good for SSH into the Linux server box on port 22

---

### Post by ghost_ryder35 on 2008-03-15
> **martydavis said:**
> Hi all.  I'm usually pretty good at researching out solutions to issues I'm having, but I keep running into dead end after dead end with this problem.

I am trying to remote into a Ubuntu 7.10 PC on my home network from my wireless connected Windows XP laptop.  I'm trying to remote admin the Linux PC for practice for when I dump my Windows Server 2003 and go Ubuntu Linux for my home file server.  I want to be able to do everything on my test PC before wiping my existing server.

I have Remote Desktop running on my Linux machine and the screen locked.  

I've unchecked the box "Ask you for confirmation" because nobody is sitting there watching for somebody to log in.

I've enabled remote login from >System >Administration >Login Window >Remote tab

When trying to connect with the VNC viewer my connection errors out with "Unable to connect to host: Connection timed out (10060)

I can ping my Linux PC

Anybody have an idea why I can't get to it?  Any config files I need to edit?

Make sure you have the port forwarded on your router :) And make sure you are using the right port for VNC viewer (VNC uses ports 5900-5906)

---

### Post by martydavis on 2008-03-15
I have putty for when I had an AIX server set up.  It worked great for a terminal connection. I tried it on my Linux PC, but it wouldn't connect either - on port 22, 23, 5000, 5001 or 5900.  My Linux PC won't let me in for nuthin' remotely.  Anybody have any other ideas?  Is there something locked down that I need to enable.

Oh, yeah - there is no firewall program running as far as I can tell.

I forwarded VNC ports 5900-5906 in my Linksys Router (WRT54G), but saw nowhere in my VNC viewer (Real VNC) to set the ports.  Is that a gimme for which ports it uses?  Opening those ports on my router isn't going to open me up for somebody to attack me from the outside is it?

---

### Post by martydavis on 2008-03-16
problem solved.  I had set the IP address of this server to the same IP address as the second network port on my Windows Server.  Fixed the IP conflict and connected just fine.

---

