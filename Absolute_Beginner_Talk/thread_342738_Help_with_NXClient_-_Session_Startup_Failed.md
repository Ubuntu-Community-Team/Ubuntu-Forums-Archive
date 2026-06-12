---
title: "Help with NXClient - Session Startup Failed"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by pimpaulogy on 2007-01-20
I have searched through these forums for this error, and other have had the same issue, but no resolution has been posted yet.

I launch NXClient and it Authenticates, but fails at Session Startup.  Here are the details:

NX> 203 NXSSH running with pid: 4844
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.119 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: paul
NX> 102 Password: 
NX> 103 Welcome to: paul-ubuntu user: paul
NX> 105 listsession --user="paul" --status="suspended,running" --geometry="1400x1050x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'paul' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: paul
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="Home-Home" --type="unix-gnome" --cookie="******" --geometry="1024x768+188+114" --kbtype="pc105/us" --screeninfo="1024x768x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: paul-ubuntu-1000-531E6551EE8E5BF9B58B669E364DAA11
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: acfe24b70625000bd409026837739796
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 426dea9932211fbafb099051a861b9c6
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 891:  8408 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.



Could somebody please shed some light on this?  I have it working on my other laptop, which was upgraded from Dapper to Edgy.  This error occurs on a laptop with a clean install of Edgy.

Thank you in advance.

---

### Post by pimpaulogy on 2007-01-20
Well, I finally found my own answer.

I was installing/using the 2.10 version of NXClient and getting the error.

I then found the 1.5 version, installed it, and bam, it worked.

I found version 1.5 at:

[http://www.industrial-statistics.com/info/nxclients?IndStats=55d83422ff4ca2d3c3e3d2703ed051b9](http://www.industrial-statistics.com/info/nxclients?IndStats=55d83422ff4ca2d3c3e3d2703ed051b9)

Hopefully this is helpful to others out there that experience the same issue.

---

### Post by antibios on 2007-03-26
I had the same error:
nxagent failed to start with: Unrecognized option: 1

and downloading the 1.5 version of the client fixed the problem

sweet :)

---

