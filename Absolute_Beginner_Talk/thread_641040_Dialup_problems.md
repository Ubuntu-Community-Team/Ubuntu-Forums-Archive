---
title: "Dialup problems"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by starkey on 2007-12-14
I've installed Feisty on a Dell D430 laptop with a Conexant internal modem.  I got the Linuxant driver and installed it, and configured it in the Networking section.  From a terminal, I ran wvdial and successfully dialed up and logged into my ISP.

However, nothing works.  No web; no email; no ping from a terminal.  Obviously, I'm missing something - anyone have any advice?
Thanks,
Starkey

---

### Post by ectospasm on 2007-12-15
When you connect to your ISP, what does your routing table look like?  I'm guessing you don't have a default route to the dial-up server on the other side.  You may also want to look at your interfaces.  Do this from a terminal shell:

```
# route
```

That should show you the routing table.  To see your interfaces, do this:

```
# ifconfig
```

You should see a ppp0 device.  I'm not 100% sure where you should find your default gateway, you'll probably have to contact your ISP about that.

---

### Post by Irihapeti on 2007-12-15
Are you using the network manager applet to configure your modem? It seems to be broken. It just connects but doesn't let you get any further.

For a new install, use "sudo pppconfig" in a terminal. It probably won't find your modem automatically - just put it in manually. Then you can type "pon" to connect and "poff" to disconnect.

---

### Post by starkey on 2007-12-15
Routing table looks like this:

stark@stark-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
quincy-asx-1.zi *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

...and *this* time, I'm connected.

---

### Post by Irihapeti on 2007-12-15
> **starkey said:**
> ...and *this* time, I'm connected.

Cool!

---

