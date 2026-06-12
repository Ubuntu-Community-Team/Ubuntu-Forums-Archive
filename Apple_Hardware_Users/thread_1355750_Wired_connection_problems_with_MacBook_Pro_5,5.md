---
title: "Wired connection problems with MacBook Pro 5,5"
date: 2009-12-15
forum: Apple Hardware Users
---

### Post by Imlad on 2009-12-15
I got a new 13" MacBook Pro (5,5) and installed Karmic on it (dual boot along side Snow Leopard).  While I got the wireless to work fine, I am having problems with my wired connection.  Here is the info on the Ehternet card:

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)

For whatever reason, the system does not see the wired connection - I know it's not a pure hardware issue because the same wired connection works fine for OSX.  Are there any drivers I need to download?

Thanks!

---

### Post by dennis123123 on 2009-12-15
> **Imlad said:**
> I got a new 13" MacBook Pro (5,5) and installed Karmic on it (dual boot along side Snow Leopard).  
....
Are there any drivers I need to download?


Nope, it just works!

The *system* does not see the connection? I.e. an "ifup eth0" then an "ifconfig eth0" shows nothing, or an error? Try a live CD or something to make sure its not your configuration. Also maybe try a different network to connect to? eg if you have tried on a home router, try it on a friends.

I have a 5,5; and I can confirm it just works with every recent linux distro Ive thrown at it, Parted Magic is always a good test

---

