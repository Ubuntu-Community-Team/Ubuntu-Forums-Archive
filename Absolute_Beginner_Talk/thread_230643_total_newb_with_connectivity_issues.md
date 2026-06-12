---
title: "total newb with connectivity issues"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by sjewenp on 2006-08-06
ok, i am an absolute linux virgin but i'm trying to break in.  i installed ubuntu and everything seems to be going allright, but i can't connect to the internet.  i've searched the forums but they are huge and i can't find anything on just basic connections.  i've pinged both a site and an ip address with no response.  in the networking menu it says i'm receiving and sending information but i can't connect.  is it a firewall problem or am i just an idiot?

---

### Post by MikeMLP on 2006-08-06
First, make sure that your connection name reads either eth1 or eth0, and not Io (right click on the (hopefully familiar) two-computer-screens icon in the upper right, and click properties).  Io, as far as I can tell, is just a fake placeholder that pops up when you have no internet connection at all (and if the name is set to Io, it can look like you actually have a real connection to the internet, when you aren't connected at all.)  Then make sure you have your connection configured properly (configure button at the bottom of the connection properties window).

If you've already done all this, please give some more details about how you connect to the internet so that we can help point you to properly configuring your connection.

---

### Post by sjewenp on 2006-08-06
my connection name is eth0.  i think i have it configured correctly.  i have dhcp set and am using a cable modem.  it is showing that i am sending and receiving, but it won't ping.  my windows pc will connect no problem.

---

### Post by annda on 2006-08-06
if you are using a MODEM and not a router, eth0 is not your connection. you need to setup pppoe e.g. using pppoeconf.

both go through your ethernet card, but a modem needs dialing instructions, while a router stores and executes them by itself (a modem needs the computer to tell it what to do.

---

### Post by sjewenp on 2006-08-06
i am using a router.  i still can't connect.

---

### Post by drtvasudevan on 2006-08-06
maybe it is an ipv6 issue.search forum for solution.

---

