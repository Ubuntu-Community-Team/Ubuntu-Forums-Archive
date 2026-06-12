---
title: "Using Remote Desktop to control several machines behind a router/firewall"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by gewitty on 2008-02-12
I need to access/control several remote Ubuntu machines sitting behind a router/firewall. I have the individual vncviewer commands for each machine, but presumably need to prefix these with the router's public IP address or DynDNS web address.

Can someone give me the correct syntax that I need to use in Terminal in order to successfully connect to the various desktops, please?

---

### Post by maybeway36 on 2008-02-12
The ports need to be forwarded in the routers settings. Forward one computer's port 5900 to 5900, another's 5900 to 5901, and so on. Then use one of:
```
vncviewer public-ip-address:0
vncviewer public-ip-address:1
```
etc.

---

### Post by gewitty on 2008-02-12
Great! Thanks for that.

---

### Post by gewitty on 2008-02-16
I have VNC working on remote machines successfully now, but there appear to be a number of security concerns: Traffic is unencrypted and leaving port 5900 open seems to be inadvisable.

I gather that I can initiate an SSH session before using VNC and that this will take care of the encryption issue. I have also heard that when using SSH I do not open port 5900, but use port 22 instead.

Can anyone advise on the set-up for both client and server machines, plus the correct addressing syntax where multiple remote machines exist (see my earlier post).

---

