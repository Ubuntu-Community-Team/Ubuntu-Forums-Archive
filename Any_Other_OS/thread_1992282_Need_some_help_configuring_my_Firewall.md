---
title: "Need some help configuring my Firewall"
date: 2012-05-31
forum: Any Other OS
---

### Post by MonctonJohn on 2012-05-31
I searched but I couldn't find anything related to my current situation. My router connects to the internet and connects the 10.25.1.0 clients together. I have 2 windows clients and this Mint client on that Lan. Now I just added a second card to my Mint machine so that I could segment the LAN and attach another switch. The reason for this is:
[LIST=1]
[*]All the wires are run and I can't run anymore
[*]The router is gigabit and so are the clients except the 2nd Mint card I just installed
[*]I do lots of computer repair work and I want an internal private LAN to connect suspect computers
[/LIST]
Basically I want the 2nd internal LAN to be able to access the internet but not talk to any of the 1st LAN clients and vice versa.
I tried a few things with Firestarter but I can't seem to get from my Windows machine to the SMB share on my Mint box.

In the meantime I will keep searching. Thanks

---

### Post by papibe on 2012-05-31
Hi MonctonJohn.

Here's an idea, that I've been researching myself lately. I don't have all the details, but so far I know this is possible

The ideal situation would be to have another device that serves as a firewall/router. For example, you can buy another router to that job, or configure your Mint machine to do that.

Here's come virtual machines to the rescue. You can create a virtual machine in your Mint computer that is dedicate 100% to handle all firewall tasks, routing, DNS, restrictions, etc.

There are several distributions that need very low resources, and are designed to do just that: firewall and router tasks. They are usually install in minutes, and are easily admin by a web interface. For instance: IPCop, M0n0wall and PfSense.

In particular PfSense has a very good reputation, and for a lot of people is the best firewall around.

Just my thoughts.
Regards.

---

### Post by Perfect Storm on 2012-05-31
Thread moved to Other OS/Distro Talk.

---

