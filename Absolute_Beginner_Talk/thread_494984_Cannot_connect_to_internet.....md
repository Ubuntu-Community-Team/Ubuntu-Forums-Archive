---
title: "Cannot connect to internet...."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by surm00 on 2007-07-07
I'm a complete noob to this so:

Installed Umbuntu 7.04 today. I have wired connection selected. When I plug in the net line usb active stays powered, as does dsl sync but the dsl traffic light only flashes once or twice. Nothing. Nada. No connection to the net at all. I tried reduced the mtu but I haven't got a clue how to. I did my best in the terminal to no avale. I could really do with a step by step guide here if anyone is willing. Thanks in advance.

---

### Post by ronocdh on 2007-07-07
> **surm00 said:**
> I'm a complete noob to this so:

Installed Umbuntu 7.04 today. I have wired connection selected. When I plug in the net line usb active stays powered, as does dsl sync but the dsl traffic light only flashes once or twice. Nothing. Nada. No connection to the net at all. I tried reduced the mtu but I haven't got a clue how to. I did my best in the terminal to no avale. I could really do with a step by step guide here if anyone is willing. Thanks in advance.
DHCP-enabled ethernet works out of the box in Linux. I recommend you try placing a router between your DSL modem and your computer. This would allow you to connect many computers to the same access point, and should work reliably with DHCP.

---

### Post by xpod on 2007-07-07
> Installed Umbuntu 7.04 today. I have wired connection selected. When I plug in the net line usb active stays powered, as does dsl sync but the dsl traffic light only flashes once or twice. Nothing. Nada. No connection to the net at all. I tried reduced the mtu but I haven't got a clue how to. I did my best in the terminal to no avale. I could really do with a step by step guide here if anyone is willing. Thanks in advance.

What kind of modem do you have??
Does it not not have an ethernet connection you can use rather than a usb one??
I know a lot of folks have had trouble with speedtouch usb modems although mines works fine with either usb or ethernet.

Have you been in to System>administration>network to make sure dhcp is enabled on your network connection?This would normally be setup automatically during installation though as long as you were connected at the time??

```
ifconfig
```
That command will show you your network interfaces and wether your getting an ip address or not.
I`ve never had trouble with feisty myself although with gutsy i have to sometimes left click the network icon and disable the connection to then enable it again before it establishes a connection.

Of course you will have tried just rebooting everything too eh:D

---

