---
title: "Dns Issue : Kindly Help!!!!"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by pulldogg on 2007-11-25
hi
my default dns shows up as 192.168.1.1
and everytime i log on i have to chnage my nameserver ip
i have done sudo gedit etc/resolv.conf
n edited it there n saved it, but stilll when i restart its abck to 192.168.1.1
it is kinda irritating typing ur dns everytime u start ur computer.
kindly advise.
thx in advance

---

### Post by MrFSL on 2007-11-25
I would bet that you have a small home type router that is setup with dhcp.

When you computer loads and goes the get the internet settings dynamically (DHCP) the router is telling it to use it's address as the name server address. 

You can either 
1) Log into the router and look for a setting that stops this behavior

or 
2) Accept it. The router might or might not cache dns records. Either way it will probably be faster since there probably isn't an extra packet inspection when dns requests are sent to an address on the intra-network.

---

