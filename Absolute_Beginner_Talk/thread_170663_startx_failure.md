---
title: "startx failure"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-05
This is probably an easy fix, but when I run startx I get the following failure:

~$ startx
xauth:  creating new authority file /home/chris/.serverauth.9491

X: user not authorized to run the X server, aborting.
Couldnt get a file descriptor referring to the console

I think this problem is also the root of others I'm having.

Cheers,
Chris

---

### Post by Borniet on 2006-05-05
Have you tried sudo startx?

---

### Post by cl3ellio on 2006-05-05
When I try sudo startx I get a nice longer failure:

~$ sudo startx
Password:
xauth:  creating new authority file /home/chris/.serverauth.9916

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.


Hope this sheds more light on it.

---

### Post by bon on 2006-05-30
i have the exsact same problem. i have tryed ever thing, 

- 

x: warning; process set to priority -1 instead of requested priority 0 
giving up

then it says 

xinit: no such process (errno03) :server error
xinit: connection refused (111): unable to connect to xserver

any help would be good this is doing my nut in

---

