---
title: "New to Ubuntu, ipw2200 trouble"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by MEHEndrics on 2007-01-12
Hey guys, I migrated over to Ubuntu from Fedora. I put FC6 on my laptop and I didn't really like it, so I figured it was time to give ubuntu a go.

I downloaded the iso for 6.10 and it turned out to be a live cd, but I installed from that anyway. Is there a real installation disc that would be better or was this ok?

My wireless card does not work and I can't find information on installing it. I have a Gateway laptop with the Centrino chipset and the ipw2200 wireless card. 

If anyone can point me in the right direction, I'd appreciate it.

Thanks, Matt

---

### Post by ejjenkins on 2007-01-12
6.10 should have included the ipw2200 drivers.  Is the wireless card enabled in BIOS...or tuned off with a keyboard combo (mine is FN F11)?

---

### Post by MEHEndrics on 2007-01-12
It appears to be working. I put in the WEP key and it connected but it doesn't see the internet

---

### Post by ejjenkins on 2007-01-12
When it connected, did it get an IP address?  Does your router see it?

---

### Post by MEHEndrics on 2007-01-12
Unfortunately I don't have access to the router, but how do I know if it got an IP address?

I'm kind of a n00b

---

### Post by ejjenkins on 2007-01-12
from a terminal run the ifconfig command:

ifconfig and press enter

---

### Post by MEHEndrics on 2007-01-12
I don't see anything about IP address in there.

would it be inet addr: ?

---

### Post by ejjenkins on 2007-01-12
Yes...tht is it.

---

### Post by MEHEndrics on 2007-01-12
Alright well then I guess I do have an IP address. The internet just won't work.

---

### Post by ejjenkins on 2007-01-12
How ar you trying to access the internet, Firefox?

---

### Post by MEHEndrics on 2007-01-12
yes, firefox.

When I go to the connection properties, it says I'm connected to lo and the status is idle. What does this mean?

---

### Post by ejjenkins on 2007-01-12
When you ran ifconfig...what connections did it show?

eth0
eth1
lo

---

### Post by MEHEndrics on 2007-01-12
eth1 and lo. eth1 is my wireless card. What is lo?

---

### Post by ejjenkins on 2007-01-12
Here is what mine shows when I run ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:90:F5:3F:14:2E  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe3f:142e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1067872 (1.0 MiB)  TX bytes:1833469 (1.7 MiB)
          Interrupt:50 Base address:0x6800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:29:54:28  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe29:5428/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3895 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3391106 (3.2 MiB)  TX bytes:662422 (646.8 KiB)
          Interrupt:217 Base address:0xc000 Memory:b0207000-b0207fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2210 (2.1 KiB)  TX bytes:2210 (2.1 KiB)

which shows eth0, my wired connection
eth1 my ipw2200 wireless connection 
and lo---which will always show 127.0.0.0 as the ip address, that is not a connection you can use for the internet...

---

### Post by ejjenkins on 2007-01-12
What wireless manager are you using in Ubuntu?  That should point at your eth1 connection not your lo connection.

I am using NetworkManager Applet 0.6.3.  Pretty sure it was installed when I installed Ubuntu.

---

### Post by MEHEndrics on 2007-01-12
my eth1 does not have an ip address. I'm using Network Monitor 2.12.0.

---

### Post by ejjenkins on 2007-01-12
look at your network interface config file it is located at:

/etc/network/interfaces

what does it say for eth1?

Mine has the following:

auto eth1
iface eth1 inet dhcp

---

### Post by MEHEndrics on 2007-01-12
it says:

iface eth1 inet dhcp
wireless-essid VerizonFIOS
wireless-key (my WEP key here)

auto eth1

---

### Post by ejjenkins on 2007-01-12
It appears to be right...the only thing I can think is that the router may be set for a static IP or is blocking your hardware ID (mac address).  Have you ever connected through this router?

---

### Post by MEHEndrics on 2007-01-12
Yes, I connected with Fedora just fine.

---

### Post by ejjenkins on 2007-01-12
You are using Network Monitor?  Have you right clicked on the Icon and configured it?

---

### Post by ejjenkins on 2007-01-12
Are you good now?

---

### Post by annda on 2007-01-12
i got a little confused with different people posting different problems but if you have an IP and still can't browse with Firefox, try disabling the IPv6 protocol, which some (or maybe most) routers handle badly.

in Firefox open the page about:config

go down to line that says:
network.dns.disableIPv6

and double-click it to change to true

that should help some people.

---

### Post by MEHEndrics on 2007-01-13
I got it working. Turns out they changed the WEP key and forgot to tell anyone.

Sorry guys.

---

