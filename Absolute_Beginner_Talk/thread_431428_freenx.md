---
title: "freenx"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jackmorelli on 2007-05-03
hi everyone,

i installed freenx exactly as an ubuntu forum post suggested, recommending checking out the ubuntu dot com slash community slash FreeNX website suggests.  no problems.

i think downloaded version 1.5 of the nxclient on my windows xp machine.  when i try to remotely access my unix machine, i get the following details (w/error)

> NX>203 NXSSH running with pid: 3772
NX>285 Enabling check on switch command
NX>285 Enabling skip of SSH config files
NX>200 Connected to address: XXX.XX.XXX.XXX on port: XXXX
Read from socket failed: Connection reset by peer

does anyone have any suggestions?  much love from a total newb.
jack

---

### Post by sloarch07 on 2007-05-26
Take a look at [this post]("http://ubuntuforums.org/showthread.php?t=204976"), on your linux box when you run 
```
sudo /usr/NX/bin/nxserver --status
```
This should return:
```
NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.
```

---

