---
title: "I can't connect to my server"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by uantuzri on 2006-10-17
Hi, 

I've been using ubuntu for some time and I though it was time to try to install a LAMP server on an old box. I followed several guides to install it and now, I'm trying to access my web server from outside my network and I configured my router with a dyndns service. So far everything ok, unless I had to make any changes on the LAMP concerning the localhost and new_dyndns_address. I forwarded the port 80 to my server's static ip but what all I get is a connection to my **router** (it appears the web interface). 

I can connect to the web server inside the network, but not outside. I tryed changing the ports both on Apache and the ip forwarding, as I read in the forums, but it didn't work (my isp doesn't block any port).

Maybe I've done something wrong with the port forwarding, but I don't have a clue. This might be helpful:

```
cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
 address 192.168.1.34
 netmask 255.255.0.0
 gateway 192.168.1.1
```
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:49:0A:85:B3
          inet addr:192.168.1.34  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::213:49ff:fe0a:85b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6448249 (6.1 MiB)  TX bytes:1471687 (1.4 MiB)
          Interrupt:5 Base address:0x6000
```

Thanks in advance

---

### Post by grim918 on 2006-10-17
When I configured my LAMP server I don't remember ever messing around with the router other than to forward my ports. I configured my LAMP server to work with no-ip. You can check if everything is working correctly by going to the site canyouseeme.org and putting in port 80. It will tell you if the port is being blocked.

Heres a How-To for no-ip
[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)

---

### Post by thornomad on 2006-10-17
What router are you using ? 

I have done a [LAMP Installation]("http://www.damontimm.com/blog/how-to-install-a-lamp-server-linux-apache-mysql-php-on-older-laptop-with-ubuntu/") and simply forwarded the ports to the IP address ... didn't have to do anything silly on the Ubuntu side ... just had to get my router working correctly.

---

### Post by Daremo on 2006-10-17
double-check the port forwarding on your router. if you can access your web server from within your network the server is functioning. it is the router blocking the external requests for that port.

---

### Post by uantuzri on 2006-10-18
> You can check if everything is working correctly by going to the site canyouseeme.org and putting in port 80. It will tell you if the port is being blocked.
I've checked it, canyouseeme tells that the port is accessible.
> What router are you using ? 
It is a ZyXel Prestige 660. I've read the user guide, and it says to use the NAT > Edit SUA/NAT server options to do this (SUA if my isp provides a single IP, or NAT server if it provides more than one; I'm almost sure that it gives me a single dynamic ip, but I tryed both methods).

> double-check the port forwarding on your router. if you can access your web server from within your network the server is functioning. it is the router blocking the external requests for that port.
I can access my server inside my network if I tipe 168.192.1.34 on the browser, and I can access with a ssh connection.

I think it is the router the one that is blocking the connection, because it is the config web interface what appears. In a very first moment, my network was unreachable because there was an option on the router's firewall to not to respond any ping signal, but once deleted that rule, it's the router the one that awnsers all the connections, not letting anything come inside my network... :(

If I disconnect the dyndns service on my router and use a dyndns client would it change anything? Do you know any guide to install a dyndns client?

---

### Post by uantuzri on 2006-10-18
> **grim918 said:**
> 
Heres a How-To for no-ip
[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)

Well, I followed it, but my router still "blocks" the connection. Any ideas?

---

### Post by uantuzri on 2006-10-18
I fixed it. It had to do with the router's config. A command was needed to make the server visible. Thankyou anyway

---

