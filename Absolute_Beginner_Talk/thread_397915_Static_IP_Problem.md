---
title: "Static IP Problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-31
I am trying to make a DNS server in my house, I have set /etc/network/interfaces to 
"# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1" 
and when I type "/etc/init.d/networking restart" to restart the network it says "Network is unreachable, failed to bring up eth0" Any suggestions?

---

### Post by HellSpawn on 2007-03-31
Why do it the hard way??

Just use gnome-neworkt-manager or KDE's... and set the IP address there, but before, restore the default settings of the /etc/network/interfaces, and then check the changes.

Yo can use a script to set your IP address with ifconfig...
ifconfig eth0 192.168.0.100 ..etc...etc...

Hope this helps

---

### Post by Peter1234123 on 2007-03-31
Ahh, this helps, but I still have a problem, I changed /etc/hosts to 
"127.0.0.1       localhost.localdomain localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts" 

I want the network to have the domain name server1.example.com, and when I type hostname -f, it says "Hostname unknown" :o

---

### Post by K.Mandla on 2007-03-31
Not 100 percent sure on this, but I rarely use *broadcast* or *network* when I set static IPs. Mine usually look like this

```
auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid XXXXXX
wireless-key XXXXXXXXXX
```
Is that any help?

---

