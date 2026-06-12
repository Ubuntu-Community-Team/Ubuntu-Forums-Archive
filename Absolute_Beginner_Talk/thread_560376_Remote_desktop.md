---
title: "Remote desktop"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by generious on 2007-09-26
Hey Guys,

Trying to figure out what is the best way of setting up a connection from home to work.
So i can access my ubuntu box from work using either Vnc or else Nomachine Nx.

I have tried both so far and failed on both occasions.
Using Vnc i installed firestarter Firewall and added several rules for the ports being used in vnc, can't remember them of the top of my head but something like 5900 and 5800 and the last one think it was 5600.
On the router ( linksys wrt54gs v1 ) i have enabled port forwarding added the ports ( again can't remember the last port but its done anyway ) to the ubuntu box that has no-ip configured and running on it innit shows it as running. ( comfirmed everything from the no-ip homepage ) 

From work when i start vnc up and try to connect to the system at home it throws out a "Unable to connect to host: Connection Refused ( 10061 ) this to me seems like a port problem but it ain't.

On the ubuntu box ran netstat to see what was and wasn't open ports required are all open....
The client i'm using to connect with is the windows version of realvnc.
From the xp client running cmd/ ping whatever.no-ip.org results in a timeout this again looks like the router isn't accepting or acknowledge the packets coming in...

I have looked for a somewhat decent guide to set this up but most aren't very clear and don't even get me started on nomachine nx thats impossible to get it up and running.

If anyone could shed some light on this that would be brilliant.

Cheers for reading 
Generious

---

### Post by hyper_ch on 2007-09-26
could be that you are being blocked at work.

---

### Post by HereInOz on 2007-09-26
The first thing to do, if you have another machine, is to attempt access from your local area network.  If this is possible, then it is clearly the router.  If it is not possible, then the router is probably an innocent party.

You are right with port 5900 (this is the port used by VNC Viewer to access a VNC Server) and 5800 (this is the port used when accessing the Java http server in VNC Server - validation, though, is still using 5900)

If the ports on the Ubuntu machine are open, and the firewall has the ports open, and the router has the ports open, then you should be able to go to Steve Gibson's site - [http://www.grc.com](http://www.grc.com) - then go through to Shields Up and have that site probe ports 5900 and 5800, and they should show as open, or at least closed, but certainly not stealthed.

Lastly, is there any other application using those ports?  

I know it is fishing a little, but hopefully this will help in some way.

---

### Post by generious on 2007-09-26
> **hyper_ch said:**
> could be that you are being blocked at work.

Do you know i was just thinking about that myself.... will have a look in a few mins and reconfigure the swicthes if thats the case.

Everything from the lan side at home works fine vista, xp, rhes 3.0 and can connect to it, so that rules out the internal routing set up ect.
No other applications apart from vnc on the lan are using 5900 the ubuntu box is a clean install only thing running on it at the moment is cedega :)

Cheers for the replys guys at least that has given me a few more bits and bops to look at :)

Generious

---

### Post by hyper_ch on 2007-09-26
well, install the openssh-server on your computer and forward port 22 from the router to your computer at home and check if you can setup a connection by ssh.

Putty is a good windows ssh client.

Because if you have SSH running, you can do everything on your computer at home.. you could then try to pinpoint the problem down whether it's work or at home...

---

### Post by generious on 2007-09-26
Found the problem switches and proxies blocking 5900 and 5800.
Only port that isn't blocked is surprise suprise windows rdp client port 3389 and 80.

---

### Post by hyper_ch on 2007-09-26
a switch should not block anything ;)

then use port 3389 for vnc ;)

---

### Post by Malibu Illusion on 2007-09-26
Do not recommend unencrypted VNC over any network.

Suggest installing OpenSSH and creating a secure SSH tunnel to your home box, then accessing a VNC window that is piped through the SSH tunnel.  Not only does that encrypt and compress the data, but it also means you don't have to open your VNC port to the public internet either.

---

