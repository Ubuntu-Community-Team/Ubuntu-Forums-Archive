---
title: "Network masking ( using Ubuntu as a router )"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by antubis on 2005-12-23
Hello to all!

I want to use my ubuntu linux as a router. Till now I was using Slackware but now the slack is gone and I really need my router back again. The only linux distribution I have is Ubuntu. But I don`t know a bit of working with Ubuntu couse its a little bit strange for me. Can u tell me how to configure my Ubuntu:

First: Ubuntu router use my real ip - XX.XX.XXX.XX on the first NIC and on the second NIC: 192.168.1.1

Second: My windows XP comp. will use the route by having the IP: 192.168.1.2

This is very popular way to configure the network so I don`t think it should be a problem for any who used to work with Ubuntu.

Thanks to all!

---

### Post by Koybe on 2005-12-23
i'm not used to the graphical interface. But the best way is to edit your configurations files. **You did not tell if your internet ip is static or dynamic, so choose one or another below.**

/etc/network/interfaces ```

#Internet NIC
#static
auto eth0 
iface eth0 inet static 
  address ???.???.???.???
  netmask ???.???.???.???
  gateway ???.???.???.??? 

#dynamic
auto eth0
iface eth0 inet dhcp

#LAN NIC
auto eth1 
iface eth1 inet static 
  address 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
```

Put ip_forward on in your /etc/network/options
```
ip_forward = yes
```

Restart your network service and check it with ifconfig
```
/etc/init.d/networking restart
ifconfig
```

Put on NAT masquerading to get reply from outside and save it.
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables-save
```


Hopes this work and help ;-)

---

### Post by Biased turkey on 2005-12-23
Welcome Antubis.
Ubuntu allows you to install some routing-firewall programs.
My situation is very similar to yours: I have an firewall-router with 2 ethernet cards running Ubuntu and 1 LAN client doublebooting ( Ubuntu and windows 2000 ).
I highly suggest to use Synaptic to install "Firestarter" It's a very popular firewall-router-Network adress translation program.
It is easy to configure.
I think you have to enable universe and multiverse repositories in Synaptic in order to download Firestarter.

---

