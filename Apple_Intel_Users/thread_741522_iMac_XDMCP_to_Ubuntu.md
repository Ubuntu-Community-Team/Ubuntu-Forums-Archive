---
title: "iMac XDMCP to Ubuntu"
date: 2008-03-31
forum: Apple Intel Users
---

### Post by PatrickNZ on 2008-03-31
Hi there, apologies if this is posted in the wrong place...

I'm using my Leopard machine (iMac 10.5.2) to log into my new Ubuntu server (7.10), using XDMCP, but I'm getting some strange results.

When use the command '/usr/X11R6/bin/X -query xxx.xxx.x.xxx' but then the Ubuntu log in window slowly loads, not in a separate window, but as the desktop for my current screen. It takes ages to load, and I can't actually use it to log in. I figure it's a configuration problem with X, but I don't know if it's on the Ubuntu or Mac end. 

Any ideas would be greatly appreciated!

---

### Post by bronkeydain on 2008-04-07
I am trying to do the same, but I have been reading this functionality has been taken out of Leopard... Not sure why??? I am still investigating further though as I have just started on this today. If I find something I'll let you know.

---

### Post by bronkeydain on 2008-04-08
It seems that since Leopard, X11 server has changed and that most people are having trouble getting XDMCP to work. I actually managed to get the login screen and was able to log in once. After that it has not worked again for me. 

I found these instructions on how to install the old Tiger X11:
[http://lists.apple.com/archives/x11-users/2007/Nov/msg00005.html](http://lists.apple.com/archives/x11-users/2007/Nov/msg00005.html)

The reason I wanted XDMCP is because connecting to my Ubuntu box using Chicken of the VNC was so slow it was unusable. Then I found that in Leopards finder my Ubuntu box was showing, and it has the option to "share screen". When I clicked on it Leopards build-in VNC client popped up and is a lot faster than Chicken of the VNC. I can live with this for now, but next weekend I will have another go at XDMCP.

---

### Post by cyberdork33 on 2008-04-08
JollysFastVNC is a a good one too.
[http://www.jinx.de/JollysFastVNC.html](http://www.jinx.de/JollysFastVNC.html)

---

