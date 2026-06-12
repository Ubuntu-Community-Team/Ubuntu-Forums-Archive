---
title: "failing to fix my ip"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by John Stoner on 2006-08-17
I have a fairly new install of 6.06, and I'm trying to set the IP as fixed. The rest of the addresses on my network are DHCP, but this will be the server. 

My /etc/network/interfaces looks like this:

auto eth0
iface eth0 inet static
     address 192.168.1.3
     netmask 255.255.255.0
     gateway 64.17.24.1

my router has a static IP, subnet mask 255.255.255.0, gateway same as above, static dns of 64.81.159.2 and 216.231.41.2, both of which are configured in /etc/resolv.conf on this box.

when I 'ifup eth0', I get 

SIOCADDRT: Network is unreachable
Failed to bring up eth0.

When I switch this box to dhcp, I can connect to the network.

Oh, and I can't ping any machine from any other machine on this network.

---

### Post by wieman01 on 2006-08-17
You either have DHCP **_OR_** use static IPs. Both your router and your PCs need to have an identical configuration. If your router is set to DHCP (the router itself will always have a fixed IP), then you network adapter will have to use DHCP as well. Don't mix it up. :-)

This is an example for static IP ("/etc/network/interfaces"):
> auto eth0
iface eth0 inet static
    address 192.168.168.40
    netmask 255.255.255.0
    network 192.168.168.0
    broadcast 192.168.168.255
    gateway 192.168.168.230
    dns-nameservers 192.168.168.230

"192.168.168.230" is your router's IP address and "192.168.168.40" your computer's.

---

### Post by IYY on 2006-08-17
If you want to use DHCP but don't want your server's IP to change, you'll need to configure *static DHCP* in your router. The configuration for this varies from one router to another.

---

