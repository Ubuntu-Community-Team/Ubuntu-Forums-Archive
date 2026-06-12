---
title: "VNC Server Not Working"
date: 2009-01-24
forum: Apple Hardware Users
---

### Post by jbiggs12 on 2009-01-24
Hello,
I've built a computer to act as a server, but I want to ditch the monitor and keyboard and go for just a VNC Connection. When I try to connect to the machine from my mac using the Screen Sharing utility, however, it just shows "connecting to 10.0.1.10..." the entire time and doesn't do anything. When I look at the monitor of my server, I notice that the mouse flickers whenever I try to connect. FTP works without a hitch, but VNC won't work as of yet.

Any suggestions?

---

### Post by cyberdork33 on 2009-01-24
> **jbiggs12 said:**
> Hello,
I've built a computer to act as a server, but I want to ditch the monitor and keyboard and go for just a VNC Connection. When I try to connect to the machine from my mac using the Screen Sharing utility, however, it just shows "connecting to 10.0.1.10..." the entire time and doesn't do anything. When I look at the monitor of my server, I notice that the mouse flickers whenever I try to connect. FTP works without a hitch, but VNC won't work as of yet.

Any suggestions?
try using a different client first like Chicken of the VNC or Jolly's Fast VNC, and if it still has issues, then it is likely something in how ou setup the server.

---

### Post by jbiggs12 on 2009-01-27
thanks cyberdork! it turns out that i had "require encryption" selected in my remote desktop options, as soon as I unticked it it worked like a charm.

---

