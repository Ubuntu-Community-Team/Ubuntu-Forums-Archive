---
title: "Incomplete installation repeats in Synaptic"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Zeedok on 2007-09-06
I have recently switched from Ubuntu to Xubuntu on my old laptop (BTW it's fantastic, can't believe I didn't think of it earlier, it's way more responsive, with all the great features I'm used to from my Ubuntu boxes - Bravo Xubuntu!!) and have had an error message pop up when installing VMware player. This was also occurring in Ubuntu.

I installed the player in Synaptic and I think it failed to establish a NAT connection or something. It tries two or three times then declares failure, even though the program runs fine (with some minor tweaking I can even get the virtual network connection sorted). The problem is that every time I update my system or install new software, synaptic has another go (and fails again!).

My question is: How can I stop Synaptic from trying to install VMware player all over again, without removing the program?

---

### Post by bodhi.zazen on 2007-09-07
Can you post the error message ?

---

### Post by caseface on 2007-09-07
This seems to be along the same lines:
I am trying to install vmware-server, and I was interrupted by a power failure. since then further attempts are met by the following report in "changes applied" details: 
Preconfiguring packages ...
(Reading database ... 136144 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb (-unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

I appreciate any help.

---

