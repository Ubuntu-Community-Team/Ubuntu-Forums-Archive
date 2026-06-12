---
title: "FreeNX help"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-31
Im tryign to get freeNX to work. It seems to authenticate fine but it never starts and ends up timing out. I can access SSH over Putty fine...

Here is what i get from FreeNX ](*,) ](*,) 

```
NX> 203 NXSSH running with pid: 2440
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xx.xxx.xxx.xxx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-44 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: joe
NX> 102 Password: 
NX> 103 Welcome to: localhost user: joe
NX> 105 listsession --user="joe" --status="suspended,running" --geometry="1280x1024x32+render+fullscreen" --type="unix-application"
NX> 127 Sessions list of user 'joe' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: joe
NX> 105 startsession --session="Xorg" --type="unix-application" --application="startxfce4" --cache="8M" --images="32M" --cookie="******" --link="wan" --virtualdesktop="1" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x1024x32+render+fullscreen" 

NX> 1000 NXNODE - Version 1.4.0-44 OS (GPL)
NX> 700 Session id: localhost-1006-06D3A6E9BA2982DF8398DDD2D5FD6A2A
NX> 705 Session display: 1006
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: e4cd8932d80fd284028c467e63409139
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 18126e7bd3f84b3f3e4df094def5b7de
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.
```

---

### Post by dermotti on 2006-03-31
Refresh for help :confused:

---

