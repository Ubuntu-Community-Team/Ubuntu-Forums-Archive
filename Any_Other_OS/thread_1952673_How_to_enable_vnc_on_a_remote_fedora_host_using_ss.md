---
title: "How to enable vnc on a remote fedora host using ssh?"
date: 2012-04-04
forum: Any Other OS
---

### Post by legolas_w on 2012-04-04
Hi,

I have ssh access (root) to a remote fedora machine but I want to install GUI on that machine and then use VNC to connect to it. Would you share the steps to do it.

Thanks.

---

### Post by markbl on 2012-04-04
> **legolas_w said:**
> 
I have ssh access (root) to a remote fedora machine but I want to install GUI on that machine and then use VNC to connect to it. Would you share the steps to do it.


On your client:

sudo apt-get install x11vnc
man x11vnc

You don't need root access to the remote box, just regular user ssh access.

---

### Post by CharlesA on 2012-04-05
If you decide to install vnc, ensure it's tunneled over SSH and password protected. It would also be a good idea to set it to listen on localhost only.

---

### Post by markbl on 2012-04-12
> **CharlesA said:**
> If you decide to install vnc, ensure it's tunneled over SSH and password protected. It would also be a good idea to set it to listen on localhost only.
All that and much more is documented in that "man x11vnc" I quoted the OP to read.

---

