---
title: "Kismet install"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Panganat on 2007-08-02
followed all i could find on installing Kismet and have gotten to point where the reult is listed can anyone point out what i may have missed in installing?




cis7850@cis7850-laptop:/$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission deniedcis7850@cis7850-laptop:/$

---

### Post by Panganat on 2007-08-03
it seems my error is finding an appropriate source to id on line 22 of kismet config file. i have a Linksys WPC54G which is broadcom 4318......  I have tried bcm43xx,wlan0,broadcomsource; bcm43xx,eth1,bcm43xx and receive the same errors FATAL: Unknown capture source type 'bcm43XX' in source 'bcm43XX,wlan0,broadcomsource'

what source should i be entering for a broadcom what an i missing??:confused:

---

