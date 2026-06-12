---
title: "[dsl] SIOCSIFADDR: No such device"
date: 2013-03-14
forum: Any Other OS
---

### Post by FoodEat on 2013-03-14
Hello!

I'm having a problem with the interfaces on my damnsmalllinux VM.
I'm trying to do ifconfig to eth1, but I get the error message saying I have no such device.

Can anyone help me figuring out what's wrong?
[http://i.imgur.com/u4JUlXo.png](http://i.imgur.com/u4JUlXo.png)

---

### Post by chili555 on 2013-03-14
When you run this, do you have an eth1?```
ifconfig
```I don't know much about darnsmallinux, but you will probably get much better support at their forums.

---

### Post by FoodEat on 2013-03-14
No, an eth1 doesn't show up :|
[http://i.imgur.com/S5FvTHj.png](http://i.imgur.com/S5FvTHj.png)

---

### Post by FoodEat on 2013-03-14
Another screenshot
[http://i.imgur.com/3y2w9Vz.png](http://i.imgur.com/3y2w9Vz.png)

Does this mean I only have 1 ethernet interface on my computer? :s

I'm sorry, but I don't really know a lot about networks and interfaces


Edit:
What shows on my windows Device Manager
[IMG]http://i.imgur.com/4G6AyBd.png[/IMG]

---

### Post by chili555 on 2013-03-14
A virtual machine, you say? Networking is handled quite a bit differently. Please see: [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)> Network Address Translation (NAT) is the simplest way of accessing an external network from a virtual machine. Usually, it does not require any configuration on the host network and guest system. For this reason, it is the default networking mode in VirtualBox.

A virtual machine with NAT enabled acts much like a real computer that connects to the Internet through a router. The "router", in this case, is the VirtualBox networking engine, which maps traffic from and to the virtual machine transparently. In VirtualBox this router is placed between each virtual machine and the host. This separation maximizes security since by default virtual machines cannot talk to each other.

The disadvantage of NAT mode is that, much like a private network behind a router, the virtual machine is invisible and unreachable from the outside internet; you cannot run a server this way unless you set up port forwarding (described below).

The network frames sent out by the guest operating system are received by VirtualBox's NAT engine, which extracts the TCP/IP data and resends it using the host operating system. To an application on the host, or to another computer on the same network as the host, it looks like the data was sent by the VirtualBox application on the host, using an IP address belonging to the host. VirtualBox listens for replies to the packages sent, and repacks and resends them to the guest machine on its private network.

The virtual machine receives its network address and configuration on the private network from a DHCP server integrated into VirtualBox. The IP address thus assigned to the virtual machine is usually on a completely different network than the host. As more than one card of a virtual machine can be set up to use NAT, the first card is connected to the private network 10.0.2.0, the second card to the network 10.0.3.0 and so on. If you need to change the guest-assigned IP range for some reason, please refer to the section called “Fine-tuning the VirtualBox NAT engine”.

---

### Post by FoodEat on 2013-03-14
Thanks, that actually helped. I figured out that I just had to turn on another Adapter on the Network tab of VirtualBox --,

---

### Post by chili555 on 2013-03-14
Awesome. That's what I was shooting for, to actually help.

---

