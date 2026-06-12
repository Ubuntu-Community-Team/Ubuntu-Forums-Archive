---
title: "3 simple questions about a smoothwall setup"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-07-24
1) Someone suggested I could run smoothwall on an old server for around $100. What would be the difference between this and a desktop pc?

2) Could the smoothwall box provide a firewall to windows vista as well as ubuntu 7.04?

3) Could smoothwall work with a usb modem?

Thanks

---

### Post by Eddy Dean on 2007-07-24
> **nite owl said:**
> 1) Someone suggested I could run smoothwall on an old server for around $100. What would be the difference between this and a desktop pc?

There is no difference between a desktop and a server, except that servers are made for stability and for high uptimes. Also the network connections in servers is often better then the onboard network thingies in a desktop PC.

> 
2) Could the smoothwall box provide a firewall to windows vista as well as ubuntu 7.04?


Certainly, smoothwall will create a transparant proxy, which should work on every OS out there.

> 
3) Could smoothwall work with a usb modem?


That depends on the modem. If Linux has drivers for it it will work, if there are no (working) drivers you're screwed.

---

### Post by nite owl on 2007-07-24
Thanks for your reply Eddy Dean, I am suprised then that most people don't recommend servers more instead of old desktops for this sort of use. So that means I can install  Smoothwall exactly as I would on a desktop? I have gotten the modem working on 7.04, so would I be able to complete the same steps in a smoothwall setup?

---

### Post by Dedoimedo on 2007-07-24
Hello,

Smoothwall is a great solution for home network. You get a router, with ability to dial a variety of connections, web interface, and if you want, intrusion detection and more.

Machines connected to the computer with Smoothwall via switch or such will run just like any other LAN machine in a LAN environment, regardless of the OS.

Very recommended,
Dedoimedo

---

