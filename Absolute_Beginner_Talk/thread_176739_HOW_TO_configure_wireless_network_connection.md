---
title: "HOW TO: configure wireless network connection"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-15
My Ubuntu box has a NetGear wireless PCI adapter and I have a NetGear wireless network router in the house using DHCP.

When starting FireFox, it cannot connect to the internet. I tried pinging other IPs on the local network, which didn't work. I only can ping my own IP.

I read a post about automatic network configuration using 'whereami'.

I tried to install it using code: 'sudo apt-get install whereami' and got the following error code:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package whereami

What do I do from here? How can I configure my network connection?

Thanks in advance!

Cheers, Anders

---

### Post by tkjacobsen on 2006-05-15
Check if the wireless device is set up correctly and enabled in system -> administration -> networking

---

### Post by ahlandberg on 2006-05-15
In 'Network Settings' -> 'Connections' there are two connections:

'Ethernet connection' and 'Modem connection'.

For the 'Ethernet connection' there are the following settings:

Connections: 'The interface eth0 is active'
General: Hostname: ubuntu, Domain name: <n/a>
DNS: DNS Servers: 192.168.0.1 (my gateway), Search Domains: <n/a>
Hosts:
ff00::0 ip6-mcastprefix
127.0.0.1 localhost.localdomain localhost
fe00::0 ip6-localnet
ff02::2 ip6-allrouters
ff02::1 ip6-allnodes
::1 ip6-localhost ip6-loopback
192.168.0.4 ubuntu
ff02::3 ip6-allhosts

I went to eth0 Interface properties and changed the Configuration to DHCP and ticked 'Enable this connection'.

Although the settings look okay, it still cannot connect to the internet.

When I try to ping another address on the network, it says: 'Network unreachable'

What now?

Thanks in advance!

Cheers, Anders

---

### Post by tkjacobsen on 2006-05-15
Is eth0 your wireless device.. Wireless devices are usually named ra0...  Try to dmesg your device and see if it is the wireless one:
```
dmesg | grap eth0 
```
See witch driver it uses

also try to:
```
ifconfig eth0
iwconfig eth0 
```

---

### Post by ahlandberg on 2006-05-15
Alright, now the problem is here:

I tried iwconfig and it said that there are no wireless extenstions.

Weird - my wireless PCI adapter is plugged in!

What's wrong?

Thanks in advance!

Cheers, Anders

---

### Post by tkjacobsen on 2006-05-15
maybe your wireless device is not detected at all.. eth0 could very well be your wired ethernet interface

---

### Post by ahlandberg on 2006-05-15
Indeed. eth0 is a wired ethernet connection. In fact, when trying the commands you suggested, I found that there are no wireless extensions.

Before installing Ubuntu, I had WinXP running on that machine and the wireless PCI adapter worked fine.

What could be the problem now that it is not recognized?

How could I possibly fix this problem?

Thanks in advance!

Cheers, Anders

---

### Post by tkjacobsen on 2006-05-15
Not all wireless devices have working drivers for linux. With the program ndiswrapper, you can use the windows drivers for your wireless device under linux.

---

