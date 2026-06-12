---
title: "programs using wrong NIC"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by madcap_magician on 2006-01-29
I've got a dumb DSL modem that only allows me to have 1 computer online at a time.  I thought I'd set up a server with IP Masquarading to get my collection of computers online at the same time.

My set up is something like this:
DSL modem connects to eth0 on the server
eth1 on the server connects to my hub
my hub connects to all my other computers.

I have dhcp working on eth1 so all  my networked machines have 192.168... IPs.  I also get a dhcp address assigned to me from my DSL modem on eth0.  The problem is that I can't get my server to see the internet.  Anytime I try to do something like Ping or load a webpage the server uses eth1 instead of eth0.

How can i change which NIC I use for programs?

---

### Post by madcap_magician on 2006-01-29
Additional information:


madcap@revolution:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0    *                     255.255.255.0 U       0         0       0 eth1
172.16.0.0      *                     255.255.0.0     U       0         0       0 eth0
default            192.168.0.1    0.0.0.0             UG    0         0       0 eth1
default            172.16.0.254  0.0.0.0             UG    0         0       0 eth0

I'm not totally sure about this but I think that is saying to use the 192.168 route first, is there a way I can change that?

---

### Post by BenTyreman on 2006-01-29
You shouldn't have two default entries. Remove one with
```
sudo route del -net 0.0.0.0 eth1
```

If it kicks up an error message, you may need to use the full
```
sudo route del -net 0.0.0.0 gw 192.168.0.1 eth1
```

---

### Post by madcap_magician on 2006-01-29
Perfect, thanks for the help, that was exactly what I was looking for.  Got everything working now!
Thanks.

---

### Post by madcap_magician on 2006-01-29
Ok, if I reboot it undoes my route info.  Is there a way to have that happen at boot time?  Preferably before IPMasq starts (have to restart it once I remove the route).

---

### Post by BenTyreman on 2006-01-29
It probably an error in your /etc/network/interfaces file. Could you post what's in there? You want to be on the look out for duplicate gateway lines.

---

### Post by madcap_magician on 2006-01-29
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        gateway 192.168.0.1
```

---

### Post by BenTyreman on 2006-01-30
It looks like eth0 is not using the dhcp messages from the modem, it is using the dhcp messages from the server. Hence, it is being automatically assigned the info that the rest of the machines get. I presume you are using dnsmasq (that's what I use). In there, there should be options to ignore the server's hostname. Alternatively, bring eth0 off dhcp, and assign it's IP address manually.

Adding this
```
dhcp-host=<servers hostname>,ignore
```
to dnsmasq.conf should do the trick.

---

### Post by madcap_magician on 2006-01-30
No, I'm not using dnsmasq.  I'm not sure if statically assigning the ip will work either, I've been watching the IPs the dsl modem is giving me, it's not always the same.

Here is my dhcpd.conf, I think the problem is in here somewhere but I haven't figured out what this all means yet.

```


#option subnet-mask 255.255.255.224;
default-lease-time 600000000;
max-lease-time 720000000;

authoritative;
subnet 192.168.0.0 netmask 255.255.255.0
{
        range dynamic-bootp 192.168.0.20 192.168.0.39;
        option subnet-mask 255.255.255.0;
        option netbios-name-servers 192.168.0.1;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.1;
}


```

There is a lot more to it but it's all commented out.

---

### Post by BenTyreman on 2006-01-30
Remove the gateway 192.168.0.1 from /etc/network/interfaces. This is causing the extra line to be added to the routing table. If manually removing it from the routing table worked temporarily, this should fix you up permanently.

---

### Post by madcap_magician on 2006-02-01
Woot, everything seems to work fine now.  Thanks for the continual help.

---

