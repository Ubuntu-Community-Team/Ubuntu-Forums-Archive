---
title: "[SOLVED] wireless problems with ubuntu 7.04"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-02-12
hello i looked at some of the threds above and i could not find a problem simaler to mine. i am using ubuntu 7.04 on a IBM t-22 notebook. i have a RAlink wireless card and i am unable to join a network i can see what networks are open but not join them. i dont have a password on my rougher and for my rougher i have a linksys WRT54G. i am a noob at linux so can you please be very easy on me.



David D.

---

### Post by OffAxis on 2008-02-12
you might want to start here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by divindavid on 2008-02-12
yeah my wireless card is not on the list but when i plug it into my laptop i get the like activity on and the activity LED is blinking do you guys have any suggestions.



David D.

---

### Post by divindavid on 2008-02-12
i have been dinkering around with it and i can not make it connect

---

### Post by OffAxis on 2008-02-12
more information is needed...
What card (or chipset) do you specifically have?
Is it a usb card?

Did anything from that Troubleshooting guide help?
For instance, is the driver installed?

what does 
```
iwconfig
```
show?

How about 
```
iwlist <your network card from above> ap
```

---

### Post by divindavid on 2008-02-12
i did not install the driver. how do i do that
my card is a intellinet wireless G 54 mbps PC card

---

### Post by OffAxis on 2008-02-12
and what about the **iwconfig **and the **iwlist **commands?
what'd they come back with?

---

### Post by divindavid on 2008-02-12
i got this from iwconfig




lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

ra0       RT61 Wireless  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:17:27:A6:F4   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=78/100  Signal level:-61 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i dont know what it meens
and for the iwlist i got 

Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
 still i dont know what it meens 


David D.

---

### Post by OffAxis on 2008-02-12
**lo **is the loopback address (127.0.0.1)
**eth0 **is your wired ethernet connection
**irda0 **is your infrared connection
**ra0 **is your wireless card (the only one we care about right now)

```
iwlist ra0 ap
``` 
should list all detected access points (your router, your neighbor's router, etc)

Currently you're set up to use 'linksys' as your connection point (is this your router's name?)

try this command
```
sudo dhclient ra0
```

then
```
ifconfig
```

what did ifconfig come back with?

---

### Post by divindavid on 2008-02-12
ok i problem is for the sudo dhclient ra0 code it is asking for a password i dont have a password for my rougher. so i went and did the ifconfig and i got 

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:A3:73:8A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:700 errors:4 dropped:4 overruns:0 carrier:0
          collisions:22 txqueuelen:1000 
          RX bytes:2560932 (2.4 MiB)  TX bytes:7776 (7.5 KiB)
          Interrupt:11

---

### Post by OffAxis on 2008-02-12
when running
```
sudo dhclient ra0
```

the password requested isn't for the router, it's for ubuntu install.
You can try the password that you used to log on to the system.
If that doesn't work you can reboot.

After that run 
**ifconfig **again, and post the results.

---

### Post by divindavid on 2008-02-12
wow i feel dumb so i did the sudo dhclient ra0 again and added my ubuntu password and i got
david@david:~$ sudo dhclient ra0
Password:
There is already a pid file /var/run/dhclient.pid with pid 12716
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:0e:2e:a3:73:8a
Sending on   LPF/ra0/00:0e:2e:a3:73:8a
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 34758 seconds.

dont know what that meens

then i went for the ifconfig and got


ra0       Link encap:Ethernet  HWaddr 00:0E:2E:A3:73:8A  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fea3:738a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1435 errors:7 dropped:7 overruns:0 carrier:0
          collisions:24 txqueuelen:1000 
          RX bytes:4473560 (4.2 MiB)  TX bytes:21968 (21.4 KiB)
          Interrupt:11 

i still cannot connect to my rougher
thank you for you help

---

### Post by OffAxis on 2008-02-12
> 
i still cannot connect to my rougher
Not quite...

The command dhclient requests a new ip from the dhcp server. At the tail end of that command (right before you got your command prompt back) you can see it get assigned here
> DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 34758 seconds.

right after that you ran the ifconfig command and you saw this:

> ra0 Link encap:Ethernet HWaddr 00:0E:2E:A3:73:8A
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0

which confirms that your ip (which was requested from your router - the dhcp server)
is good.

So, are you sure that you don't have internet access still?
Usually if you can get an ip off the router (which you did) you're done.

You can access the router's configuration at
192.168.1.1 (by putting that as the url in firefox). The router default name/password is probably:
name: admin
password: (none)
or
name: admin
password: password

There's an 'Attached Devices' section in the router setup that should list all the connected machines (including your wireless one).
If you still can't reach the internet, that's a different problem;
so the question is 

can you reach the router's configuration page?

---

### Post by divindavid on 2008-02-12
well i can get to the rougher config when i am pluged into my rougher by a ethernet port.
but still no wireless. i dont see a attached devices section.

---

### Post by divindavid on 2008-02-12
my wii can connect to the internet

---

### Post by OffAxis on 2008-02-12
what does 
```
route
```

give ya?

---

### Post by divindavid on 2008-02-12
i get

david@david:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
david@david:~$ 

i really hope this will help

---

### Post by divindavid on 2008-02-12
david@david:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
david@david:~$

---

### Post by divindavid on 2008-02-12
i dont know how to make it look right\

[IMG]file:///home/david/Desktop/Screenshot-david%40david%3A%20~.png[/IMG]

---

### Post by divindavid on 2008-02-12
[IMG]http://file:///home/david/Desktop/Screenshot-david%40david%3A%20~.png[/IMG]

---

### Post by divindavid on 2008-02-12
[/URL]http://www.flickr.com/photos/23744128@N06/2260952789/[/URL]

---

### Post by divindavid on 2008-02-12
you get the point

---

### Post by OffAxis on 2008-02-12
yes; got it.

---

### Post by zozobra on 2008-02-12
I personally didn't have much luck using the gui for setting up wireless. It may be best for you to uninstall those utilities and use iwconfig to manually configure your connections then run ```
sudo /etc/init.d/networking restart
```

---

### Post by OffAxis on 2008-02-12
judging by your route table it looks like you've got a few things going on.

1. You connected to your router with a wire, got an ip, unplugged it, possibly rebooted, and then ran **route**.

2. By doing that, your wireless ip (the one attached to ra0) went away as your eth0 connection became the default.

No big deal. Unplug your wire and request a new ip on the wireless connection.

you can use 
```
sudo dhclient ra0
```
to get a new one.

After this, run 
```
ifconfig
```

again. It should show you ra0 with an ip assigned to it (probably 192.168.1.101)

once you've got your wireless ip back try pinging the router.

```
ping -c 4 192.168.1.1
```

If that works check the **route **command again.
The default gateway of 192.168.1.1 should show up bound to the ra0 interface.
If it's not bound then you need to bind it.
Check the man page
```
man route
```
or that troubleshooting guide for the command (I've gotta go)
it's something along the lines of
```
sudo route add default gw 192.168.1.1 dev ra0
```

---

### Post by divindavid on 2008-02-12
i did not have any luck with the sudo /etc/init.d/networking restart and for the iwconfig



ra0       RT61 Wireless  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:17:27:A6:F4   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level:-59 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by divindavid on 2008-02-12
ok i did all of that, and i got nothing nothing at all.  so i did the        
sudo route add default gw 192.168.1.1 dev ra0
and i got

david@david:~$ sudo route add default gw 192.168.1.1 dev ra0
SIOCADDRT: Network is unreachable
david@david:~$ 



please help

david d

---

### Post by divindavid on 2008-02-13
i have tried everything and i can not connect to wireless 
do u think it is the wifi card if so i could get a new one. i know it is not my rougher because everything else can connect

---

### Post by OffAxis on 2008-02-13
try scanning for your router again to see that it's still reachable with your card
```

iwlist ra0 scan
```

if it's still there then check to see that your card is still tied to it.

```
iwconfig
```

If it's NOT there you can add it with 
```
sudo iwconfig ra0 essid "linksys"
```

(substituting your router's real ESSID for *linksys *if you've changed it)

check it again
```
iwconfig
```

if it's all good, then request another ip

```
sudo dhclient ra0
```



Incidentally, 
```
sudo /etc/init.d/networking restart
```

is virtually the same command as **dhclient**. 
What it does is restart the networking as a whole, so your system will re-examine the */etc/network/interfaces* file and apply whatever changes or specifications are there to your interfaces, be it a static ip or a dhcp request.
**dhclient **is a little more directed, and only requests a new ip for the specified interface.
the **ifup **and **ifdown **commands yield similar results, too.

---

### Post by divindavid on 2008-02-13
i did not have to do any of that i just upgraded to 7.10 and i am good i am amazed
but you still helped me sooooo much

---

