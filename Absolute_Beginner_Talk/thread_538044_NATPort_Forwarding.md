---
title: "NAT/Port Forwarding"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mrgrapefruit on 2007-08-29
I've set up masquerading and DHCP to allow computers connected to a switch which is in turn connected to the ubuntu box to access the internet connection through the network interface ppp0. The computers are connected to eth0.

I've got webmin up and running, but I cant figure out what settings I need to enter to get some port forwarding on the go, and also whether it should go in filter, mangle or NAT...

Anyone have any ideas?

Thanks in advance.

---

### Post by guardsman85 on 2007-09-01
OK, I'm assuming your setup is something like this (if not, please explain):
```

[Computer] o----o [switch] o----o [eth0_Ubuntu_ppp0] o----o [wan]
```First, this is how I setup NAT.  This was modified from a script I built to configure a Fedora system at school, but I think it should work for Ubuntu as well (I modified it to match the setup above):
```
# Turn off IP forwarding
echo 0 > /proc/sys/net/ipv4/ip_forward
# -F Flush any rules
iptables -F
# -P Policy (accept everything)
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
# Flush NAT rule
iptables -t nat -F
# Append destination NAT rule to chain
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
# Turn IP forwarding back on
echo 1 > /proc/sys/net/ipv4/ip_forward
```The easiest thing to do is save it to a script so you can run it using sudo.

You'll also want to make sure your client computers have their default gateway set to the address of eth0 (or your equivalent) on the Ubuntu machine.  Now your Ubuntu machine should be effectively serving as a NAT gateway/router, but you specifically mentioned port forwarding...

Let's say you have these IP addresses:  
Ubuntu ppp0 - 10.0.0.1   
Ubuntu eth0 - 192.168.0.1   
Computer eth0 - 192.168.0.200

Here's how you could forward web traffic to your Ubuntu ppp0 interface (10.0.0.1:80) to Computer eth0 (192.168.0.200:80):
```
sudo iptables -t nat -A PREROUTING -p tcp -i ppp0 10.0.0.1 --dport 80 -j DNAT 192.168.0.200:80
```
I think that should do it.  Someone please correct me if I'm wrong.

---

