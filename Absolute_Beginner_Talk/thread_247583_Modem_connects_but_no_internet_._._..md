---
title: "Modem connects but no internet . . ."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2006-08-30
I followed the modem howto in the Ubuntu help section.  I can dial in to my ISP, connect, and even get an IP address.  But, what do I do next to get the internet working?  Do I need to inform the browser that I am using the modem and not the network card?  Do I need to disable the network card while using dialup internet?

Thanks for the help.  Dapper works great on my T30!
(except for the modem :)

---

### Post by cwaldbieser on 2006-08-30
> **braddcadd said:**
> I followed the modem howto in the Ubuntu help section.  I can dial in to my ISP, connect, and even get an IP address.  But, what do I do next to get the internet working?  Do I need to inform the browser that I am using the modem and not the network card?  Do I need to disable the network card while using dialup internet?

Thanks for the help.  Dapper works great on my T30!
(except for the modem :)

After you connect, do you see the modem in your network settings (maybe as something like ppp)?  The following commands in the terminal will help you figure out what is going on:

```

$ ifconfig
$ route

```
The first shows you your network interfaces (network cards, dial-up connections, etc).  The modem is usually something like ppp0.
The second shows your routing table.  It should show that your default route is to the Internet through your modem (ppp) connection.  If it isn't, then that is probably your trouble.  You can set the default route using the GUI or with the route command.

---

### Post by braddcadd on 2006-08-30
ifconfig yeilds the following

```

eth0      Link encap:Ethernet  HWaddr 00:09:6B:86:8E:65
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:90861 (88.7 KiB)  TX bytes:90861 (88.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:216.77.208.248  P-t-P:216.77.208.1       Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:58 (58.0 b)  TX bytes:128 (128.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:B6:A5:35:E2
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fea5:35e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3572966 (3.4 MiB)  TX bytes:587649 (573.8 KiB)
          Interrupt:11 Memory:d2000000-d2002000

```

---

### Post by scxtt on 2006-08-30
what's the output of /etc/resolv.conf? -- maybe your nameserver address(es) aren't being set ...

---

### Post by braddcadd on 2006-08-30
I have to dial-in and disconnect each time so the ip address may be different (if that helps diagnose).

Before modem connects:
```

nameserver 205.152.37.23
nameserver 205.152.144.23

```

After modem connects:
```

nameserver 139.76.169.99

```


Thansk for the troubleshooting.

---

### Post by cwaldbieser on 2006-08-30
> **braddcadd said:**
> ifconfig yeilds the following

```

eth0      Link encap:Ethernet  HWaddr 00:09:6B:86:8E:65
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:90861 (88.7 KiB)  TX bytes:90861 (88.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:216.77.208.248  P-t-P:216.77.208.1       Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:58 (58.0 b)  TX bytes:128 (128.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:B6:A5:35:E2
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fea5:35e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3572966 (3.4 MiB)  TX bytes:587649 (573.8 KiB)
          Interrupt:11 Memory:d2000000-d2002000

```

What about your routing table?

---

### Post by braddcadd on 2006-08-31
Do you mean the output of route -n?  If so, here it is:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
216.77.209.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by cwaldbieser on 2006-08-31
> **braddcadd said:**
> Do you mean the output of route -n?  If so, here it is:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
216.77.209.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

Try typing:
```

$ sudo route del 0.0.0.0
$ sudo route add default gw dev ppp0

```
Your default route (0.0.0.0) is sending traffic to your your wireless adapter.  The above lines remove that route and replace it with a route to the ppp0 device.

You should also be able to configure this through the network GUI, if I am not mistaken.

I am not sure what program you are using for dialup, but there is probably an option to configure a new default route on connecting from that program as well.

---

### Post by braddcadd on 2006-08-31
Thanks but we are not quite there yet.

First problem
```

braddcadd@UbuntuTop:~$ sudo route del 0.0.0.0
Password:
SIOCDELRT: No such process

```

Second problem
```

braddcadd@UbuntuTop:~$ sudo route add default gw dev ppp0
dev: Host name lookup failure

```

---

### Post by MaximB on 2006-08-31
try in the terminal :
sudo pppoeconf
then configure your network connection
and see if it works

---

### Post by 1969Benz on 2006-08-31
I had the same problem with my newly installed 6.0.6 server.  I finally figured out that the default route was pointing at my eth0 interface instead of my ppp0 interface.  I double-checked the settings in pppconfig and they definitely say that the ppp0 int should become the default route after a successful dialup connection.

I didn't have this problem on 5.10.  Any suggestions?

Cheers,
Ben.

---

### Post by cwaldbieser on 2006-08-31
> **braddcadd said:**
> Thanks but we are not quite there yet.

First problem
```

braddcadd@UbuntuTop:~$ sudo route del 0.0.0.0
Password:
SIOCDELRT: No such process

```

Second problem
```

braddcadd@UbuntuTop:~$ sudo route add default gw dev ppp0
dev: Host name lookup failure

```

OK, my syntax must be a little off.  Try
```

$ sudo route add default gw <ip-address-of-ppp0>

```
You need to fill in the IP address of the ppp0 device (after you have connected).

---

### Post by 1969Benz on 2006-08-31
I had the same problem with my newly installed 6.0.6 server.  After a bit of searching I found that the default route points to eth0 instead of ppp0.  I think that means I made a mistake somewhere in my config during setup.  If I manually add a default route to ppp0 then all is well (I'm using the server as a dialout router among other things).

pppconfig seems to be fine, it says that when my connection is dialled then ppp0 should become the default route.  Any ideas how I can fix this?  [Edit:  I mean, fix it so that I don't have to manually re-add the default route every time I dial out to my ISP :) ]

I used to Linux a bit some years ago, but my skills have atrophied considerably.  All help appreciated.

Cheers,
Ben.

---

### Post by braddcadd on 2006-09-01
Thanks.  It now works!

To use dialup:
```

sudo wvdial
sudo ip link set wlan0 down
route -n
sudo route add default gw <ip from dialup>

```

To go back to network card (first disconnect the modem connection):
```

sudo ip link set wlan0 up
route -n
sudo route add default gw <ip from network card>

```

---

