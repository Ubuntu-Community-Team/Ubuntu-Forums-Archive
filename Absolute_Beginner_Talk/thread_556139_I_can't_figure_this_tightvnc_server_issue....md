---
title: "I can't figure this tightvnc server issue..."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-09-20
I'm trying to get xinetd to launch tightvncserver, but it just doesn't seem to want to do it.

my /etc/xinetd.d/Xvnc file:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = :1 -inetd -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -nocursor
        port = 5800
}

```
I restart /etc/init.d/xinetd, watch /var/log/syslog, and when I try to connect it just spams:
> 
Sep 20 23:16:34 localhost xinetd[3999]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4000]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4001]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4002]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4003]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4004]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4005]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4006]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4007]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4008]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4009]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4010]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[4011]: warning: can't get client address: Transport endpoint is not connected
Sep 20 23:16:34 localhost xinetd[3913]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.

Wash, rinse, repeat.

If I execute "Xvnc :1 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -localhost -rfbport 5800 -nocursor"
it seems to work just fine... I'm at a complete loss as to where to look and how to get this thing working.. Any help would be awesome.

---

### Post by mongrol on 2007-09-22
I have the same issue. Yet to find a fix for it.

---

### Post by HermanAB on 2007-09-22
Well, xinetd was useful back in the day when the Linux scheduler was really bad.  Nowadays, the scheduler is really good and xinetd doesn't buy you anything anymore., so just start vnc up and run it permanently.

---

