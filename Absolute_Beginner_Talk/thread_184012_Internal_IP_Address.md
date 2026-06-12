---
title: "Internal IP Address"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-05-29
How do I figure out what my internal IP address is? I ran ```
ifconfig -a
``` but all I got was my mac address

---

### Post by linuchsan on 2006-05-29
So you properly don't have an ip address assigned.

---

### Post by Randomskk on 2006-05-29
If ifconfig doesn't show an IP, the interface doesn't have one assigned.
If your network uses DHCP, assign one like this:
sudo dhclient eth0
(I'm assuming eth0 is your network interface)

If it's manaully configured:
sudo ifconfig eth0 192.168.x.x
(where 192.168.x.x is your desired IP)

If manually configuring, make sure to set a default route:
sudo route add default gw 192.168.x.1
(where 192.168.x.1 is your default gateway)

Also, if you need to set up a DNS server, change /etc/resolv.conf so that at least one line looks like:
nameserver 192.168.x.1
Where 192.168.x.1 is a valid name server (many modems / routers have a name server built in, or your ISP may give you a name server address).

---

### Post by eentonig on 2006-05-29
If you have a TCP/IP stack installed on your machine, you normally should have at a bare minimum a loopback If with ip address 127.0.0.1 which you should be able to ping.

If you don't have this, you're in deep shit.

---

