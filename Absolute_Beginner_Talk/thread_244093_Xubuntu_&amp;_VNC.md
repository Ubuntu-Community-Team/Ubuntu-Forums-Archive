---
title: "Xubuntu &amp; VNC"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by WesleyWex on 2006-08-25
I'm trying to get used to the linux world, first I've managed to install Ubuntu and configure it to use my serial mouse, among other issues... but Gnome was very heavy for my K6-2 550 MHz machine, so I'm trying Xubuntu now...

The only issue is I can't run VNC in any way.

I've followed this thread to install it:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

But I get this on my syslog for "xinetd":
```
Aug 24 15:39:09 servidor xinetd[4830]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Aug 24 15:39:09 servidor xinetd[4830]: Started working: 1 available service
Aug 24 15:40:00 servidor xinetd[4831]: warning: can't get client address: Transport endpoint is not connected
Aug 24 15:40:00 servidor xinetd[4832]: warning: can't get client address: Transport endpoint is not connected
Aug 24 15:40:00 servidor xinetd[4833]: warning: can't get client address: Transport endpoint is not connected
.
.
.
Aug 24 15:45:18 servidor xinetd[11181]: warning: can't get client address: Transport endpoint is not connected
Aug 24 15:45:18 servidor xinetd[4830]: Exiting...

```

I've googled the error message but found nothing but other people posts without 1 clear answer. What's going on?

PS: I've seen that the system isn't able to read my other machine host name (synergy only worked with the machine IP address), could this be the issue? How can I fix it?

Ubuntu worked perfectly with both synergy and vnc.

---

