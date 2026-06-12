---
title: "Can't Connect to OSX Server screen sharing with VNC"
date: 2011-10-28
forum: Apple Hardware Users
---

### Post by mm144 on 2011-10-28
I have a OSX Lion Server that i often have to administer and i can use vnc viewers on windows and osx to connect to this server but when i try to connect with Ubuntu 11.10 like this

vncviewer 192.168.1.106:5900

my output comes out like this:

VNC Viewer Free Edition 4.1.1 for X - built Sep  7 2011 11:16:25
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Oct 28 16:14:12 2011
 CConn:       connected to host 192.168.1.106 port 5900
 CConnection: Server supports RFB protocol version 3.889
 CConnection: Using RFB protocol version 3.8
Password: 
Fri Oct 28 16:14:20 2011
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
 main:        End of stream

Where no display actually appears.

Does anyone have any idea how to get around this issue?  I'd love to use linux full time.

---

### Post by mm144 on 2011-10-30
I've got an update, i changed vnc clients to svnc and had to deactivate ssl and ssh (scary) and it finally displays an image.  However, the image displayed is a static image of the background of the login screen.

Any known reason why it would do this?  The thought that i have is that the stream is freezing for some reason.  At any case, is there a solution for that?

---

