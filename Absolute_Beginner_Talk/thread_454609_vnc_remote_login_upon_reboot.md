---
title: "vnc remote login upon reboot"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by norcal on 2007-05-25
I am using fiesty and followed the tutorial  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC).

after rebooting my remote machine i attempt to login (this is on a home network). there is like this flash on my screen then nothing here is the output from the terminal. 

vncviewer 192.168.1.20:1

VNC Viewer Free Edition 4.1.1 for X - built Jan  7 2007 17:30:38
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri May 25 14:26:17 2007
 CConn:       connected to host 192.168.1.20 port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
 main:        End of stream
any help appreciated.

---

### Post by Ek0nomik on 2007-05-25
You are using the built in remote desktop I presume?

I don't know if you can allow it to login from the "login" screen.  That would require it to be working on display 0.

In order to allow myself to login using VNC on the logon screen, I had to use x11vnc.

---

