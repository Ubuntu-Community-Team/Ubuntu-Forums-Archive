---
title: "Ethernet Problems"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-04
Hi, i seem to be having problems with ethernet settings, i took my computer and hooked it up to download updates, and such, now i know this works, because it worked in the live CD, but now, not so much, im not sure exactly whats wrong with it, it reads that eth0 is active, but i cant load a webpage, P.S. im using v.6.06.

---

### Post by dwhitney67 on 2007-09-04
> **xxhaloownerxx said:**
> Hi, i seem to be having problems with ethernet settings, i took my computer and hooked it up to download updates, and such, now i know this works, because it worked in the live CD, but now, not so much, im not sure exactly whats wrong with it, it reads that eth0 is active, but i cant load a webpage, P.S. im using v.6.06.

What do you mean "it" reads that eth0 is active?  Did you run this command:

[FONT="Courier New"]$ /sbin/ifconfig eth0[/FONT]

What results are shown?

Also try:

[FONT="Courier New"]$ ping [www.google.com](www.google.com)[/FONT]

Any luck?  If not, then you do not have connectivity to an access point.

Are you using DHCP or do you have a static IP?  Was your Ethernet card detected (use [FONT="Courier New"]$ dmesg | grep eth0[/FONT])?  Please feel free to furnish any and all information because your OP does not tell anyone much other than you don't have network connectivity.

---

### Post by alienexplorers on 2007-09-05
Are you running a wired or wireless configuration.  If wired did you change anything in the network settings since you said the ethernet was connecting to the internet through the live-cd.

---

