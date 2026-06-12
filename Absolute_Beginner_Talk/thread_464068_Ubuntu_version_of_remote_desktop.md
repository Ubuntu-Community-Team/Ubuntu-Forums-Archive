---
title: "Ubuntu version of remote desktop"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Dudeman02379 on 2007-06-04
Is it possible to enable a remote desktop equivilent on my ubuntu fiesty machine?  I want to be able to connect to it from a windows machine to do work on it from outside my home.  I am pretty familiar with the workings of remote desktop and terminal services in a microsoft environment but I'm a linux newb.  I'm sure there are ways to connect to a linux machine from another linux machine but just to be clear I want to be able to connect to my linux machine from a microsoft machine if that is possible.  Any information about remote desktops in ubuntu would be really helpful.  THANKS!!

---

### Post by Kidge on 2007-06-04
i use tight VNC for both OS's

[http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by Dudeman02379 on 2007-06-04
Thanks I'll check that out.  Hopefully it will run on a port other than 3389 so I can leave my routes in place for my windows servers and setup new routes to my linux machine.

---

### Post by lazyart on 2007-06-04
VNC generally runs on port 5900.

---

### Post by Dudeman02379 on 2007-06-04
After looking at the TightVNC website it looks like it runs on ports 5800 and 5900.  Can't wait to try it out.  How easy is it to install on the linux box?

---

### Post by mattva01 on 2007-06-04
FreeNX is also very good (extremely fast) .

Here's a  guide: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by lazyart on 2007-06-04
You all ready have vino on ubuntu. Go to system> administration> remote desktop and enable sharing, then make sure port 5900 is open.

Now, if you are using compiz or beryl it won't work correctly and you'll need x11vnc (in the repositories).

---

### Post by Dudeman02379 on 2007-06-04
Oh cool so there is software called vino built in that I can use.  How would I connect to that with a windows machine?  Or do I need to use one of the other programs mentioned to connect with a windows machine?

---

### Post by Dudeman02379 on 2007-06-04
bump...  I just want to make sure that vino will work with windows.  I assume that there would be a client I would install on my windows machine to connect with.  Thanks.

---

### Post by phr0ze on 2007-06-04
Linux Remote Desktop (VINO) is the same VNC stuff. Just find any VNC viewer. TightVNC, RealVNC, etc some are better than others. There are also VNC viewers for other platforms like PDA, Mac, etc.

FREENX is known for its speed if you want a faster experience. But I would start with what's included and works from there.

---

### Post by Dudeman02379 on 2007-06-04
Sounds great thanks for all the help guys!

---

