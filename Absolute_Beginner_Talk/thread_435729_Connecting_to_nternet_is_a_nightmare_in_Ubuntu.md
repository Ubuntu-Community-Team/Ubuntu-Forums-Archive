---
title: "Connecting to nternet is a nightmare in Ubuntu"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-07
Installed Ubuntu Feisty this weekend in two computers.  After two days, i still don´t have internet in any of them.

I need help with this, i would really appreciate the help from the Ubuntu community.
So, one thing at a time. The Desktop Computer:


 - Adsl internet connection
 - Computer connected to wireless modem ADSL with a network cable
 - network card recognized in eth0, and communicating. I can ping the modem ip. But when i open firefox or synaptic, it says it can´t connect. Something is missing and i have no ideia off what it is.

Anyone?

---

### Post by Solicitous on 2007-05-07
Well if your adsl modem does all the connecting and authenticating to the internet, to me then sounds like either an issue of your desktop computer is not getting DNS information or gateway address.

I assume the desktop computer is a dual boot with Windows?  If so I'd grab the networking details from your Windows installation eg; ip address, gateway and dns, and then put them into your Ubuntu install and see how you go from there.

Cheers,

---

### Post by sailor2001 on 2007-05-07
did you put in a wireless manager?  kwifi or wifi-radar

---

### Post by omns on 2007-05-07
My d-link adsl router never picks up the correct DNS server details with Ubuntu. You may have a similar problem and just need to enter your connection manually instead of using dhcp

---

### Post by rich.bradshaw on 2007-05-07
Yeah, sounds like your router isn't set up to do DHCP properly. Check your router settings and manually add your DNS servers to it if you need to. Getting ethernet to work should be as simple as plugging the cable in...

---

### Post by Pulka on 2007-05-07
checked windows configurations, and in ubuntu it all seems like it´s ok, or at least in the network tools, the ip is right, the DNS also. It also says that there are bytes transmitted. What the hell is missing?

One thing i notice is that on the network settings, the network device that always shows first is the loopback (lo). I wonder if that is the problem.

Another thing i realized now. U are saying to set manually in ubuntu, right? not in the router configuration

---

### Post by fastpakr on 2007-05-07
So you have a valid IP, gateway, subnet, and DNS info?  What happens if you run a tracert (or whatever the linux equivalent is, I'm not really sure yet) of the next hop (i.e. the gateway the AP shows in the info it leased from the ISP)?

---

### Post by justleen on 2007-05-07
the loopback device is perfecty normal. Thats your localhost, 127.0.0.1.. all network traffic goes through the loopback

---

### Post by tgalati4 on 2007-05-07
On the desktop machine, post the output of:

ifconfig

ping 192.168.1.1

or

ping 192.168.0.1

---

### Post by Pulka on 2007-05-07
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:2F:5C:F4:A7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe5c:f4a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3389 (3.3 KiB)  TX bytes:4086 (3.9 KiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)


ping 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.675 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.669 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.687 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.660 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.664 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.570 ms

---

### Post by fastpakr on 2007-05-07
Click on the network icon in the taskbar, go to Connection Information, and post the information you see in the window that pops up.

---

### Post by Pulka on 2007-05-07
> **fastpakr said:**
> So you have a valid IP, gateway, subnet, and DNS info?  What happens if you run a tracert (or whatever the linux equivalent is, I'm not really sure yet) of the next hop (i.e. the gateway the AP shows in the info it leased from the ISP)?


sorry, i have no ideia of what you just hasked me

---

### Post by Pulka on 2007-05-07
> **fastpakr said:**
> Click on the network icon in the taskbar, go to Connection Information, and post the information you see in the window that pops up.


adress: 192.168.1.2
broadcast: 192.168.1.255
subnet mask: 255.255.255.0

connection name: eth0
status: idle

received: 662 packets
sent: 540 packets

---

### Post by fastpakr on 2007-05-07
Interesting - do you not see any information regarding Default Route or DNS?

---

### Post by Pulka on 2007-05-07
the only thing that i didn´t posted was the network device:

tipe: ethernet
adress: 00:11:2F:5C...

there´s nothing else

---

### Post by bukwirm on 2007-05-07
[Disable IPv6]("http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6").

---

### Post by Pulka on 2007-05-07
WORKED!!!

thank you all. It was just turning off IPv6

---

### Post by Pulka on 2007-05-07
have another problem now. I can browse the internet just fine, but i can´t use synaptic neither apt-get. It doesn´t connect to the servers. I checked the repositories. They´re ok. They simply can´t connect to the intenret

---

### Post by z0phi3l on 2007-05-07
Have you rebooted your PC?


I would just to make sure all the changes have taken.


I know it's a very Windows type solution but it never hurts

---

### Post by Pulka on 2007-05-07
yes. twice

---

### Post by tgalati4 on 2007-05-07
Post the output of:

more /etc/resolv.conf

It should be something like:
nameserver 192.168.0.1
or
nameserver 192.168.1.1

depending on how your network is set up.

Post the output of:

route

It should look something like:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Normally a computer reboot is not required, but a modem reboot usually is!

---

### Post by Pulka on 2007-05-08
thank you all, but my problem is solved. Removed ipv6 and gave new dns

---

