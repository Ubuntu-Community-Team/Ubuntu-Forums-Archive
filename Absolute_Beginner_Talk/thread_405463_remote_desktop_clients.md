---
title: "remote desktop clients"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2007-04-09
I'm running a remote server that I need to connect to with my laptop. The server is running Ubuntu 6.10 and has remote desktop enabled. I can connect to it fine using Real VNC on windows or through wine, but does anyone know of any decent remote desktop viewing clients that are for linux? Thanks.

---

### Post by Albi on 2007-04-09
Is it on the same network?

If so,
System-->Admin-->Login Window

Go toRemote tab
Style: Same as local

Click configure XDMCP
Make sure Honor Indirect Requests is checked

On your other laptop, go to session, XDMCP chooser, and it should scan/automatically appear there.

---

### Post by cptjaben on 2007-04-09
while the desktop is on the same network, I need to connect to it when I am away, so it's not going to be on the same network.

---

