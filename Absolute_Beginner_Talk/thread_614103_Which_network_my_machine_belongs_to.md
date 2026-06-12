---
title: "Which network my machine belongs to?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-11-15
Okay, could be some stupid questions. My machine in the office getting the ip addres 192.168.0.211via DHCP. I want to get a static IP instead. 
How do I know which network my machine belongs too? 
Most of the other machine in this area of my office must be on the same network, correct? (they all have static ip starting with 172.17.x.x
How can I go about setting a static IP? Should the administrator assign me one or it's something I can find out on my own.
Thanks a lot.

---

### Post by Nano Geek on 2007-11-15
> **aspen_dv said:**
> Okay, could be some stupid questions. My machine in the office getting the ip addres 192.168.0.211via DHCP. I want to get a static IP instead. 
How do I know which network my machine belongs too? 
Most of the other machine in this area of my office must be on the same network, correct? (they all have static ip starting with 172.17.x.x
How can I go about setting a static IP? Should the administrator assign me one or it's something I can find out on my own.
Thanks a lot.If it's a work computer, it would probably be best to ask before you did that. But why do you want a static IP? Is there a specific reason?

---

### Post by Skefflock on 2007-11-15
That's not not exactly true. All the computers on the same LAN must be in the same IP address space, usually in the same subnet. You address, the one you've got through DHCP, is the local address. You've got something like a proxy server or NAT between your machine and the Internet. But the address 172.17.xxx.xxx - is a real IP that belongs to the global network. In any case they couldn't be withing the same LAN.
Usually DHCP server will allow you to keep the IP assigned by hands if it is correct at all for this LAN, If it's not - ask the administrator. So check it out.

---

