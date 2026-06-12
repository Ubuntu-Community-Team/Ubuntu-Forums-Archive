---
title: "Browser won't load webpaes"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by baLes on 2006-12-16
Hi, I am new to Linux. Everything seems to be going fine since a couple days ago when I installed Ubuntu. However, today my internet browser is unable to load any webpages. I tested my internet connection on my Windows partition and the internet works just fine. Back on Linux, I am able to ping many websites fine, but when I go to load them in Firefox it cannot connect (although sometimes it wil load google but take a very long time). If anyone can help me out I would appreciate it very much, thank you.

---

### Post by baLes on 2006-12-16
And by the way, I am using DSL modem. Thanks.

---

### Post by aysiu on 2006-12-16
I'm not very good at network troubleshooting, but I know a few other things you might want to try apart from pinging:

1. Install another browser  (Epiphany, Konqueror, Opera, Lynx, Dillo, Galeon, etc.) and see if that browser has the same problem as Firefox. If that works, it's a Firefox problem for sure. If not...

2. Open up Synaptic Package Manager and see if you can **Reload** the repository information. If that works, it may be a web browser thing?

3. Launch Firefox from the terminal: ```
firefox
``` and then post the output back here.

---

### Post by baLes on 2006-12-16
None of those 3 things worked.

I've been looking around for possible problems and I noticed in my "Active User List" from my modem it is saying I have a static connection. The list reads:

STATIC  00:0c:f1:75:2f:77  192.168.0.3   <-- Linux
DHCP    00:0f:b3:61:64:69  192.168.0.2   <-- this computer on Windows

However, when I go to System>Administration>Networking and go under properties it says it is using Automatic Configuring (DHCP).

Not sure, if that has anything to do with it, just something unusual I noticed.

---

