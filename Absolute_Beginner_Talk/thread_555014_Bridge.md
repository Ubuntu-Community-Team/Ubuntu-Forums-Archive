---
title: "Bridge"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by leonegron on 2007-09-19
I recently started messing around with Linux and I'm getting most of it, but still hang at some places.  I am trying to make a bridge that connects two totally DIFFERENT Internet connections and my Internal network all together.  I'm running Ubuntu Server, the most recent one.

Now I'm a little confused because I did these steps:

1. Made my y /etc/network/interfaces look like this:
auto br0 inet static
address 192.168.23.200
netmask 255.255.255.0
bridge_ports eth0 eth1 eth2

auto eth0 inet manual

auto eth1 inet manual

auto eth2 inet manual

2. Added my DNS settings for both Internet networks into my resolv.conf

I have no idea what to do next.  I looked online but no one seems to have more than one interface bound to the bridge.

The idea is to make the network look like this:

Internet 1 --- Bridge --- Internet 2

Then the internal network is connected to the bridge on a third Interface.

Any ideas?

---

