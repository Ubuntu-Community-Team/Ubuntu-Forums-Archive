---
title: "Lost connection: Internet and networking how to?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-03-17
Hi There,

I'm running Ubuntu 6.10 and Gnome, and I have a DSL - > Router - > PC setup.   My net worked fine when I first installed 6.10.  The problem was my ethernet cable from my computer got plugged directly into the modem recently and now I can't connect.  When I switch my cable back to the original setup (i.e. back to the router) I still can't connect.  

Everything still works in windows no problem.  Does anyone have any suggestions?  Ideally if you had a link for a "connectivity how to" that would be great to help me in the future.

Thanks,

---

### Post by meborc on 2007-03-17
hmm... what happens when you do ```
sudo dhclient
```?

---

### Post by civilmonkey on 2007-03-17
> **meborc said:**
> hmm... what happens when you do ```
sudo dhclient
```?

```
paul@paul-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:f2:99:9e:cd
Sending on   LPF/eth0/00:15:f2:99:9e:cd
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.103 -- renewal in 236492 seconds.

```

192.168.0.103 is my dynamic IP in windows as well, makes sense I guess.  Does this point to any solutions?

---

### Post by meborc on 2007-03-17
you should be able to connect to the internet now :D just try firefox :)

---

### Post by civilmonkey on 2007-03-17
Sweet :) Thanks!

One day I'll learn all these little commands...

---

### Post by meborc on 2007-03-17
no problem :)

i used to have the same problem when taking the cable from one box and switching it to another... i rebooted every time as simple "sudo iwup eth0" didn't help...

then someone gave me that command... and :) well, my life has never been the same since

we all start at one point... soon you will know enough commands to help another person, and the ubuntulove is carried on...

---

