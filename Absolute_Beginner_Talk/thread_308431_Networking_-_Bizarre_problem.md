---
title: "Networking - Bizarre problem"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-11-28
I boot my laptop.  I can ssh into my laptop. Sometimes I can ping google, other times I get 

marx2k@UbuLappy:~$ ping google.com
connect: Network is unreachable

If I CAN ping google, I wont be able to after a few minutes.

During the time that the network is reachable, my network looks fine in route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    *               255.255.255.0   U     0      0        0 eth1
default         192.168.11.1    0.0.0.0         UG    0      0        0 eth1

```

Once it goes down, I can still ping the router without any problem.  I just cant seem to go beyond the router.

At that point, route -n looks like this:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    *               255.255.255.0   U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     0      0        0 eth0

```

Im not sure where it's picking up 169.254.0.0 from, Im also not sure why eth0 is even in there at all since it's commented out in /etc/network/interfaces

```

auto lo
iface lo inet loopback

#auto eth1
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid 000740B6F60A
netmask 255.255.255.0
gateway 192.168.11.1

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

iftab looks like: (the only thing I can think of...)
eth0 mac 00:02:a5:bb:25:dd arp 1
```

/etc/hosts: 
127.0.0.1       localhost
127.0.1.1       UbuLappy
192.168.11.4    BluScreen #another linux box on the system

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

this is ifconfig AFTER I restart the network:
```

eth0      Link encap:Ethernet  HWaddr 00:02:A5:BB:25:DD
          inet addr:169.254.17.111  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::202:a5ff:febb:25dd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:30:BD:D2:02:35
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fed2:235/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3415 errors:71 dropped:0 overruns:0 frame:0
          TX packets:2838 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:323979 (316.3 KiB)  TX bytes:758434 (740.6 KiB)
          Interrupt:3 Base address:0x2100

```

Where is ETH0 picking up that IP address from?!?!  Theres no ethernet connected into it. Truly bizarre.

---

### Post by marx2k on 2006-11-28
Slight update...

in System -> Administration -> Networking for some reason had eth0 as being active.  Not sure why.  I deactivated that, rebooted and so far everything seems ok.

Im unsure as to why the Networking app would all of a sudden enable it.

I will try a reboot and see if it still works after rebooting...

While reading up on the web, looks like the 169.254 address is an automatically assigned address when the client can't find the DHCP server - so that would make sense for eth0 (ethernet port)

Hmm... looks like everything is fine after a reboot also.  I will continue to test this out.  

Now eth0 looks like:
```

eth0      Link encap:Ethernet  HWaddr 00:02:A5:BB:25:DD
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Which is about right since it's disconnected.

eth1 (wireless) looks like:
```

eth1      Link encap:Ethernet  HWaddr 00:30:BD:D2:02:35
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fed2:235/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200 errors:12 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27961 (27.3 KiB)  TX bytes:49580 (48.4 KiB)
          Interrupt:3 Base address:0x2100

```

---

