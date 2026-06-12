---
title: "xubuntu - vnc4server - end of stream error"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by madhatter563 on 2008-03-05
I am attempting to install vnc4server and followed all directions on the tutorial:
[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)
I am getting the error: 
```
:/etc/xinetd.d$ xvnc4viewer :1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Mar  5 18:49:26 2008
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
[U]
Wed Mar  5 18:49:28 2008
 main:        End of stream[/U]
$ 

```

I did follow the step as instructed to Add "-extension XFIXES" to the end of the "server_args" line to get past the End of Stream problem.

Is there something im missing here?

btw I am using a box with xubuntu 7.10 updated.  

Here is my Xnvc file located in /etc/xinetd/
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
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5901
}
```

---

### Post by ctyc on 2008-03-10
I got nothing

---

