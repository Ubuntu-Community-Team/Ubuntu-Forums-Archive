---
title: "How to remotely access ubunto on lan"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by has981 on 2007-01-12
Hello forum,

My Ubuntu version is 6.06 LTS Dapper Drake, my logging account is a user (limited previliges), and I'm not sure what more info to provide.. My question is: How is it possible to connect to another ubuntu computer (same release) within the LAN!!

execuse me If there are any details missing :-?
Many thanks in advance!

---

### Post by annda on 2007-01-12
if you want to log into the computer, use this link:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

if you just want to share some files, someone will surely post instructions here.

---

### Post by moshuptrail on 2007-01-12
depends what you mean by "connect"
there are ways to 
a) share and transfer files
b) log in with a terminal
c) do full screen control

---

### Post by has981 on 2007-01-13
> **moshuptrail said:**
> depends what you mean by "connect"
there are ways to 
a) share and transfer files
b) log in with a terminal
c) do full screen control

Thanks alot Annda and Moshuptrail,

Well, to answer your question Moshuptrail, what I had in mind in the first post is only b (log in with a terminal) but I guess now I got greedy and I'd like to know how to do the three choices. but mainly I'd have two main scenarios, they are:

1st scenario: I want to carry out two (or more) different rendering jobs, each one would take a considerable amount of time, so rather than performing them both one after another on one computer, I want to make use of the other ubuntu computers within the LAN and carry out the jobs simultaniously.

2nd scenario: I would like to have access the computer that is connected to the projector and the speekers so that I can play my cd's and music (or even brows then internet) without having to get off my chair... (Now I'm not that lasy but just imagine how cool that sounds 8))

I have tried to look at ssh, now I need to have the IP address of the other pc that I'm accessing and I'm not sure but I guess the network is configured using DHCP! so I'm not sure if ssh is the solution I'm looking for... any thoughts!

---

### Post by moshuptrail on 2007-01-13
1) for file sharing, read up on ftp, nfs and samba

a) ftp is basic,, you probably already have some familiarity
b) nfs is way to "mount" a directory on another computer as if it were just another HD on yours (probably the best way for linux-linux sharing)
c) samba is a tool for windows file sharing, if you want to share with windows use that.

2) for ssh, IP addresses, hmmm.  In my house I have a powerful desktop in the same room as the cable modem and my wireless router.  So it's plugged into one of the wired ports and I use a fixed IP address for that one.  Then I add an entry in each laptop (/etc/hosts) around the house for the one with a fixed address.  Since I don't ssh the other way, I don't need to know the address of the laptops. I assume you've figured out how to turn on ssh.  You only need to do that on the PC's that will host incoming connections.

Having said that, I have learned that my linksys router seems to keep track of which laptop is which and tends to always give them the same IP address.  I think it loses track if it gets reset or powered down.  Pretty rare.  This aso allows me to configure the desktop as a WINS server and I put the WINS server address into the router so DHCP tells the laptops where this WINS server is.  This REALLY helps samba (my wife insists on XP)

So I use ssh and just a single name with no dots to access the desktop.
example:
$ ssh baggins
me@baggins password:

3) full screen is a bit tricky.  There are three protocols available.  RDP, RDPv5, and VNC.  You want to use VNC.  RDP protocols are for connecting to windows PC's.  oops, I'm assuming you are connecting linux to linux.  On the host machine I don't think you need to do anything.  On the client, you might need to install tightvncviewer.  At least, that's the one I like.  There's a vncviewer, but it doesn't have as many command line options.  There is a program called GnomeRDP that you can install, but all it does is formulate a command line and then call xtightvncviewer or vncviewer.  I mean there's not much added value there. Once you figure out the command line options its simple enough to create desktop launcher with the right command line.  (mine is $ xtightvncviewer baggins:0 -compresslevel 8 -quality 5)

4) lastly, don't overlook the multi-workspace capability of your linux desktop.  You can start something on one workspace, switch to another, and do other things.  Also you can open many terminals.

write back for specific details, or search the forum

---

### Post by has981 on 2007-01-15
Wow, thats a whole load of info.. much appreciated.. I was able to connect to other pc's using the ssh with the ip... anyway.. seems like I have lots of reading to do, thnx again.

---

