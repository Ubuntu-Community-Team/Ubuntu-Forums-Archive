---
title: "Apple Remote Desktop VNC Server Unable to Connect"
date: 2009-12-30
forum: Apple Hardware Users
---

### Post by gargaralarga on 2009-12-30
Hi,

I recently installed Ubuntu at my office and today I tried to control my Mac OS X using the Apple Remote Desktop. For that I followed the guidelines from [https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop) but when I try to connect a window appears showing that was unable to connect to the VNC server. Specifically it says

**"vncviewer: ConnectToTccpAddr: connect: Connection timed out Unable to connect to VNC server"**

what's wrong?

Thanks!

---

### Post by tom4everitt on 2009-12-31
Time out errors generally depends on either: there's no one waiting for the call or there is someone blocking the call on the way (usually a firewall or a router). 

Exactly how are the computers connected to each other: are they both connected to the same network, or will they connect over internet? If over internet, do you know if they are connected through some router?

---

