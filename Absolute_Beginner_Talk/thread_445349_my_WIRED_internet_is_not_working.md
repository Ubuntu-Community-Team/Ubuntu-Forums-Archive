---
title: "my WIRED internet is not working"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zomw on 2007-05-15
I am currently running a multi-boot setup with vista, xp, and edgy ubuntu.  My wired internet connection refuses to work in ubuntu, yet works absolutely fine in vista and xp.  I think it is some kind of problem with DHCP, but I am not sure.  I have browsed through several threads relating to this issue, but with no luck.

Can anyone please help me resolve this?

---

### Post by wormser on 2007-05-15
Here are some things to try.

See if you have an ip address.
**ifconfig**  

Ping your router, a domain name and an ip address.
**ping yahoo.com**

Try running this command to get an ip address.
**dhclient**  

Post results if it still is not working.  BTW, double check your cable.

---

### Post by zomw on 2007-05-15
Here are the results:

Output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:04:4B:00:D4:CD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 

eth1      Link encap:Ethernet  HWaddr 00:04:4B:00:D4:CB  
          inet6 addr: fe80::204:4bff:fe00:d4cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92600 (90.4 KiB)  TX bytes:92600 (90.4 KiB)

```

Output of ping yahoo.com:
```
ping: unknown host yahoo.com
```

Output of dhclient:
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:4b:00:d4:cb
Sending on   LPF/eth1/00:04:4b:00:d4:cb
Listening on LPF/eth0/00:04:4b:00:d4:cd
Sending on   LPF/eth0/00:04:4b:00:d4:cd
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

How do I figure out the address of my router to ping it?

---

### Post by zomw on 2007-05-15
bump

---

### Post by n8bounds on 2007-05-15
you don't have an IP address, so you won't be able to ping your router.

Boot into XP and do an ```
 ipconfig /all 
``` and either print it or write it down or something

Your windows default gatway is usually your router.  Anyway, thats not going to help you because you don't have a route to it with no DHCP lease.  

Something looks off about your eth0 device.  Anyway, back to your printout, try saying this in a terminal: 
```

sudo ifconfig eth1 192.168.1.42 netmask 255.255.255.0

```
substituting the ip address with whatever it was when you were in windows
if you can THEN run ifconfig (alone) you should see something like this
```

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:23:4F:0D
          inet addr:66.233.126.169  Bcast:66.233.127.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:73ff:fe23:4f0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:198000729 (188.8 MiB)  TX bytes:13553486 (12.9 MiB)
          Interrupt:17 Memory:d6000000-d6004000

```
Also, when you say ```
 route -n 
``` you should see a line resembling:
```

0.0.0.0         66.233.124.1    0.0.0.0         UG    0      0        0 wlan0

```
replacing the 66.233..etc with your router's IP address (and the wlan bit with eth1)
your /etc/resolv.conf file defines your DNS servers, if you don't have anything in there, do a 
```
 gksudo gedit /etc/resolv.conf 
``` and add ```
 nameserver 208.67.220.220 
``` to it
after all that try to ping yahoo.com or something

your router might be flaky or only handing out a limited number of dhcp offers, it might be configurable

---

### Post by zomw on 2007-05-16
Big thanks for all the info, but it is still not working.

Exactly what address am I supposed to replace the address in the sudo ifconfig netmask command with?  The default gateway that windows displayed, or the ip address it gave me?

When I enter the default gateway or the ip address into the sudo ifconfig netmask command, the route -n command always gives me the "destination" as the number I entered and the "gateway" as 0.0.0.0.  The "genmask" is 255.255.255.0.  The "inet addr" from the plain sudo ifconfig command is the same number I entered into the last sudo ifconfig netmask command.  The only flag for the route -n command is U.

Also, am I supposed to enter the same dns addresses into ubuntu that I got from windows?

Output of regular ifconfig command:
```
eth1      Link encap:Ethernet  HWaddr 00:04:4B:00:D4:CB  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe00:d4cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x4000

```

Output of route -n command:
```
 Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

---

### Post by zomw on 2007-05-16
bump

---

### Post by medad on 2007-05-16
Do you have two ethernet cards on your system?  The eth0 looks almost exactly how mine looks.  Was your edgy version the live disk and if it is did you try to get on the internet prior to installing it?

---

### Post by zomw on 2007-05-16
I have dual ethernet ports, if that is what you are asking.  The internet did work on the live disk, but it also worked on the installed version until one day I booted up and it wasn't working anymore...

---

### Post by zomw on 2007-05-16
bump

---

### Post by annda on 2007-05-16
what does your  /etc/network/interfaces look like?

---

### Post by Ocxic on 2007-05-16
is it possible that an new upgrad caused the identifiers of your 2 ethernet ports to change, try switching your ethernet cable to the other port, and rebooting, or running "sudo /etc/init.d/networking restart", and see what happens i know it''s kinba out in left field idea, but give it a shot.. I've known strager things to happen.

---

### Post by steve.horsley on 2007-05-16
I can see that the cable is plugged into eth1 because that is the interface that has RUNNING in the status.
However, it shows 0 bytes transmitted and 0 bytes received - it is not passing traffic. Running the command
**sudo dhclient**
would normally transmit some packets (DHCP requests), so there is some kind of internal problem.
You could try:
[B]sudo ifdown eht1
sudo ifup eth1[/B]
but beyond that, I don't know. And I'm not sure I like those interrupt numbers.

You could try turning the machine off and on again - I once had a machine with hardware that Windows left in a state that Linux couldn't recover from and I had to power reset rather than soft restart when switching from Win to Linuix. And you might try moving the cable to eth0, just to see.

---

### Post by obrient on 2007-05-16
Looking at you information are you running a router between your computer and internet modem? 

If so if you entered the network ip for the machine as 192.168.1.1 then you have most likely confused the router which usually has that address. 

If you want to have a static IP address for the machine and only use one interface you might want to make your /etc/networks/interfaces file so that it look something like this.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.80
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

```

This gives my machine a single internet interface with an address of 192.168.1.80 my gateway is my routers ip.

If you simply want to use DHCP on a single interface you might want your /etc/network/interfaces file to look like this.

```

iface eth1 inet dhcp
gateway 192.168.1.1

```

To edit your interfaces file you will want to 

```
sudo gedit /etc/network/interfaces
```

One big note **don't** delete the lines
```

auto lo
iface lo inet loopback

```

Hope this helps.

---

### Post by zomw on 2007-05-16
Thanks for all the help guys.  I've learned some things I didn't know before.
Unfortunately, though, none of the solutions have worked.

I've decided to just go ahead and uninstall edgy and install feisty and see how that works out.  If that doesn't work, I'll come back to this thread for more help:)

---

### Post by zomw on 2007-05-17
I installed ubuntu 7.04 and the internet is working like a charm now.  In fact, I am typing this in ubuntu right now :)

Thanks for all the help guys.

---

### Post by n8bounds on 2007-05-18
Glad it all sorted out in the end! :)

---

