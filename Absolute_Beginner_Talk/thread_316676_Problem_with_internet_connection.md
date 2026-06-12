---
title: "Problem with internet connection"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by cyberbuff on 2006-12-11
Dear friends, 
I have an NIC ethernet connection. i tried with rp-pppoe-3.5 and it sed the installation is complete. but whenever I try to access the net (after running adsl-start) it's not working. adsl-stop gives:
```
killing pid 
```
adsl-start says a connection is on. I tried lowering 1412. but of no use. 
adsl-status gives:
```
cant' read pppoe PID file /var/run/pppoe.conf-adsl.pppoe.pid.pppoe
```
as a matter of fact there is no file as such. 
Please help
Regards

---

### Post by Patrick-Ruff on 2006-12-11
I don't understand why you're using that software to use the internet . . . ubuntu should have all NIC networking services built in so long as your NIC drivers are working in the first place.

could you be more specific?

---

### Post by cyberbuff on 2006-12-11
Well, now i am having some other problem. it is similar to [http://www.ubuntuforums.org/showthread.php?t=314876]("http://www.ubuntuforums.org/showthread.php?t=314876").
route -n gives me:
```

Destination         Gateway      Genmask       Flags    Metric ref   
59.93.192.1        0.0.0.0   255.255.255.255  UH        0 0 
0.0.0.0            0.0.0.0   255.255.255.255  U         0 0

Use Iface
0   ppp0
0   ppp0

```
What to do now?

---

### Post by cyberbuff on 2006-12-12
is nt there someone to help me?

---

### Post by dbott67 on 2006-12-12
Hi Cyberbuff,

If your NIC is directly connected to the modem (no router or NAT firewall) and you use PPPoE to connect, then your routing table (route -n) appears to be missing the default gateway.

PPPoE generally uses the same destination & gateway, so you could try the following command:
```
route add -net default gw 59.93.192.1 dev ppp0
```
Note: you may need to preface the command with 'sudo'
```
sudo route add -net default gw 59.93.192.1 dev ppp0
```

If this doesn't work, can you please describe your setup?  Do you have a cable/DSL router or are your connected directly to your DSL modem?

Please post a diagram, as well as make & model of modem, router and any other pertinent details.

Thanks.

-Dave

---

### Post by cyberbuff on 2006-12-12
well, the IP you posted is nt static. Since I am using broadband it changes everytime I log on. So will that really work. Beside I found my problem similar to [this one]("http://www.ubuntuforums.org/showthread.php?t=314876&highlight=pppoe"). But I cant find any file as .ete/resolv.conf

---

### Post by cyberbuff on 2006-12-12
oh, it didn't work for me.:-?  I think it's becoz it's nt the default gateway. should I add 192.168.1.1?

---

### Post by dbott67 on 2006-12-12
> **cyberbuff said:**
> oh, it didn't work for me.:-?  I think it's becoz it's nt the default gateway. should I add 192.168.1.1?

The default gateway of 192.168.1.1 would be valid *if* you have a home cable/DSL router (such as D-Link, Linksys, or other similar NAT firewall) that has an IP address of 192.168.1.1.

Can you please provide details of your network:
- make & model of modem
- make & model of cable/DSL router
- ISP
- if possible, draw up a little diagram

Also, what is the output of the following commands:
```
ifconfig -a
```

```
dbott@dapper:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

```
dbott@dapper:~$ **cat /etc/network/interfaces **
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```


Thanks,
Dave

---

### Post by cyberbuff on 2006-12-13
outputs 
```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```
and ```

~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
I use a Quidway W1000 Series Wireless
Access Device WA1003A Wireless
ADSL Access Point
My ISP is BSNL.
Pictures attached[ATTACH]20975[/ATTACH]

[ATTACH]20976[/ATTACH]
Thanks

---

### Post by dbott67 on 2006-12-13
It appears as though your Quidway router acts as a NAT firewall.

Typically, these devices need to be configured with the settings for your ISP.  It handles all of the communication between your computers & the internet, meaning that you do not need any special software on your computers (the router typically has a PPPoE client embedded that connects to the ISP).

The gateway is normally the IP address of the router (which could be 192.168.1.1 --- check your documentation).

My suggestion is this:

1. Try connecting the computer to the router using a cable (not wireless, as wireless adds another layer of complexity).

2. You do not need any PPPoE software on your computer.  The router handles it.

3. Try logging in to the router using a web browser:
[http://192.168.1.1/](http://192.168.1.1/) (again, check the documentation for correct IP and username/password)

4. Make sure your ADSL settings are correctly programmed in to the router.  Your ISP should have provided you with a username & password (I've attached a screenshot of mine).

5. Once you are able to connect to the internet over the cable, you can try wireless.

I've attached a network diagram that indicates a typical setup.  Note: the 'INTERNET PORT' in the diagram gets it's IP address from the ISP (on your router it's the ADSL port).  The other difference is that your Quidway router has an integrated ADSL modem, where as my diagram shows a separate modem.

-Dave

---

### Post by cyberbuff on 2006-12-13
[http://192.168.1.1/](http://192.168.1.1/) didn't open in the browser. :(  I use a NIC cable to connect with the modem. Pls suggest some other method.

---

### Post by cyberbuff on 2006-12-14
Oh I did it!:)  I really dont know how. But i just reformatted and did 
```
 pppoeconf
```
And it's working now. Can you please tell what would have been the problem?
Anyway, thanks for your time and help.
Regards

---

### Post by dbott67 on 2006-12-14
Well PPPoE is the 'point-to-point over Ethenet Protocol' used for connecting via ADSL and **pppoeconf** is a user-friendly tool for initial configuration of a DSL (PPPoE) connection.

I'm not familiar with the Quidway router/AP; perhaps it does not have manage PPPoE settings and that each computer requires it... I don't really know, to be honest.  Every cable/DSL router that I've seen has a built-in NAT firewall, DHCP server and a web interface to manage ISP settings, so the Quidway seems like it's lacking some features.

Your best bet (if you really want to know) is to contact your ISP and ask them what functions the Quidway provides (NAT firewall, DHCP, PPPoE connection, etc.).  Also, you might want to ask if there's a web management interface, etc.

-Dave

---

### Post by cyberbuff on 2006-12-14
thanks dave. Well, as I told you earlier that  I use a NIC cable. Now it seems that it is not detected by Ubuntu, and it connects through wireless accesss point. Can tell me how to configure the NIC?
Regards

---

### Post by dbott67 on 2006-12-15
I'll preface this by saying that I've never used the pppoe configuration client, as my router handles it for me.  This will be a learning experience for me as well.

Here are the main commands when dealing with networking:

This command shows each network interface and it's config settings (whether it is  automatically enabled, uses static or dhcp, etc.)

```
cat/etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```



This command tries to detect wireless access points using each NIC:

```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

This command prints out your routing table:

```
route -n
```

```
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```


So, what we need to know is:

a) whether or not the interface is automatically enabled
b) is the PPPoE interface enabled

I need you to do a few things:

1. Post the output of the above commands **before** running pppoeconf.
2. Post the output of the above commands **after** running pppoeconf.

We'll then modify your existing **/etc/network/interfaces** file to match.

-Dave

---

