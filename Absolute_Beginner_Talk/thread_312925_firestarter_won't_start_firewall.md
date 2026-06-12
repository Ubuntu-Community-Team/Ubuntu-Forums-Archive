---
title: "firestarter won't start firewall"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-12-05
Hi everyone. a small problem thats been hanging around - Firestarter tells me that my device eth0 isn't ready so the firewall can't startup, however as I'm using the net at the time and its own network activity monitor registers activity whenever I access a site, I think its hallucinating.
How can I put it in detox?
screenshot attached

---

### Post by pay on 2006-12-05
Do you have 2 network cards? Try eth1.

---

### Post by rajeev1204 on 2006-12-05
hi

i read a similar thread somewhere in the forums (dont remember where -sorry)

about firestarter not starting at boot up and seems to be a security issue.a bug report also exists for this i believe.

so maybe u should not be using it unless u have more unfo on it?! 

check this link [https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647]("https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647")


regards

rajeev.

---

### Post by pandu.rs on 2006-12-05
In preferences, there is a option to select the interface thro which your computer is connected to the Internet. select it appropriately (may be eth1 or eth2...). Then it shld work fine.

---

### Post by carloslosgrande on 2006-12-06
[I][FONT="Comic Sans MS"]Hi guys and thanks for your replies. I only have the one ethernet card eth0 and the modem isn't configured, however, assuming that firestarter really is flipped out I selected the modem device. see attached. This works!
What the hell does that mean? I don't have a local network, its just me and my machine. Weird, but working and that's all I ask.
Thanks again guys.[/FONT][/I]

---

