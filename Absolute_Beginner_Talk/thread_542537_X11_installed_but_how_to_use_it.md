---
title: "X11 installed but how to use it?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by gokul_ifs on 2007-09-04
Hi,

I have installed x11-common_7.1.1ubuntu6_i386 in my PC. 

And started it by```
 sh /etc/init.d/x11-common start
```

I want to make remote login to a linux server(not in terminal, i want to use the desxtop of that remote server) and access some applications in it. 

I have the IP address and root password of the remote linux server with me.

I would like to know how can i do it using x11?



Thankx in advance,
Gokul

---

### Post by mckryptyk on 2007-09-04
Most would do SSH via SSL instead if RDP/VNC via SSL in this case. (you want graphical so RDP/VNC is a must) 

Make sure protocol is encrypted over SSL for system security this is the correct way to do it.

Have a look around the forums, there are whole guides dedicated to these kind of things in the "Servers and Security" section that will do a better job of explaining it than I could.

Cheers.

---

