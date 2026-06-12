---
title: "Remote Desktop Question"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-05-01
Hi,

what's equivalent of pcanywhere for linux/ubuntu:

1) for ubuntu-windows machines
2) for ubuntu-ubuntu machines

Thanks,
Alex

---

### Post by Cypher on 2007-05-01
VNC is your answer. There are many variants, [RealVNC]("http://www.realvnc.com/"), [TightVNC]("http://www.tightvnc.com/")..

---

### Post by Argeroth on 2007-05-01
I've had success using a Program caled No Machine NX.  If you search the forums there are HOWto's

---

### Post by slamdunk on 2007-05-01
Thanks for replies.

I would like avoid commercial solutions. And so VNC could be good but:

1) is it difficult to configure? (add user etc)

2) is it insecure? (I read in anywhere that could be security problem - not exactly what:))

3) using application for RDP protocol could be  an alternative?

---

### Post by SendDerek on 2007-05-01
> **slamdunk said:**
> Hi,

what's equivalent of pcanywhere for linux/ubuntu:

1) for ubuntu-windows machines
2) for ubuntu-ubuntu machines

Thanks,
Alex

Depends on how much stuff you want to setup.  I hear that pcanywhere is really easy to setup, but as you've already figured out, it's not capable enough.

If you're not afraid of configuring your router for port forwarding, then this would be the best way to go:

1.)  configure port 3389 (RDP) and 177 (XDMCP) to forward to the IP address of the computer that you want to connect to.
2.)  install xnest by using sudo apt-get install xnest

For connections from ubuntu to windows, use RDP connection method found in the Terminal Services program located in Applications->Internet.

For connections from ubuntu to ubuntu, use XDMCP connection method found in the same Terminal Services program.

That's a start...

---

### Post by lsutiger on 2007-06-13
What about wimdoze machines ( win98 ) that can't run RDP ( on the receiving end )?

---

