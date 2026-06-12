---
title: "Internet Problems"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by JavaBeans2007123 on 2007-12-24
I can't seem to access the internet on my new Ubuntu installation. Do I need special drivers of some sort? 

TIA,
JavaBeans2007123

---

### Post by benrboone on 2007-12-24
Please let us know a little bit more about your problem.  Are you using DSL, Cable, or a Modem.  Wireless or wire and so on

---

### Post by JavaBeans2007123 on 2007-12-24
I am using cable, 1 meg on wire. The wire from the modem connects to the router (Linksys WRT54G) and from there, a ethernet wire connects to the computer. A windows laptop also connects (wirelessly) to the router

---

### Post by benrboone on 2007-12-24
please open up a terminal window (It is found under application, accessories, terminal) and type "ifconfig" enter

---

### Post by JavaBeans2007123 on 2007-12-24
> **benrboone said:**
> please open up a terminal window (It is found under application, accessories, terminal) and type "ifconfig" enter
Then what should I do?

---

### Post by benrboone on 2007-12-24
post that information or at least see if you can see an IP address in the section under eth0

---

### Post by JavaBeans2007123 on 2007-12-24
Ok.

---

### Post by JavaBeans2007123 on 2007-12-24
Here you go:
vinh@vinh-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:D3:B7:FE:25  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:d3ff:feb7:fe25/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6000 (5.8 KB)  TX bytes:6000 (5.8 KB) 

vinh@vinh-desktop:~$

---

### Post by benrboone on 2007-12-24
it appears that you have and address of 192.168.1.1 
in this same terminal can you type "route -n" and post the line of the default gateway this will most likly be the last entry (at least on mine it always has been) anyways it will have all zero in the destination (0.0.0.0) and then in the gatway colunm it will have the gatway

---

### Post by dnvikram on 2007-12-24
Will be needing some more info regarding your internet setup.You said,windows connects wirelessly to the router to access the internet.There are 2 possible setups for what you mentioned:

1)If its a DSL, your ISP is using PPPoE.If its that ,then you have to make sure that the login credentials are setup properly in the router and the internet link on the router will always be on,until router is on and your ubuntu will be assigned an ip using DHCP.If modem is directly connected to your ubuntu machine then use the ,"sudo pppoeconf" command to setup the dial up connection.

2)If its a cable ,then your setup will be using internal ip behind nat and wil directly connect to the internet using dhcp.

---

### Post by bumanie on 2007-12-24
I fear you are suffering from the ipv6 stack issue. Many have had this happen under gutsy. The only way around it is to disable/blacklist ipv6 in either firefox on by modifying a gedit list.
The problem is that everything to do with connections looks OK, but you still can't hook up until you blaclist ipv6.
To disable ipv6 
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Another way is to diable ipv6 in firefox
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
You can try one of these methods if you wish. If they don't work either can be reversed by 
a) removing the blacklist ipv6 from the gedit list and saving or
b) changing the "network.dns.disableIPv6" back to false

---

### Post by Zero Prime on 2007-12-24
You are having the same problem that I had a few weeks ago.  What fixed mine was unplugging the routers for 10 seconds to reset them then plugged them all back in.  You may have a slightly different situation, but try that and see what happens.

---

### Post by JavaBeans2007123 on 2007-12-24
> **dnvikram said:**
> Will be needing some more info regarding your internet setup.You said,windows connects wirelessly to the router to access the internet.There are 2 possible setups for what you mentioned:

1)If its a DSL, your ISP is using PPPoE.If its that ,then you have to make sure that the login credentials are setup properly in the router and the internet link on the router will always be on,until router is on and your ubuntu will be assigned an ip using DHCP.If modem is directly connected to your ubuntu machine then use the ,"sudo pppoeconf" command to setup the dial up connection.

2)If its a cable ,then your setup will be using internal ip behind nat and wil directly connect to the internet using dhcp.

My desktop, the one with Ubuntu, connects to the internet via an enternet cable. The type of internet is cable; the ISP is Virgin Media/NTL

---

### Post by bumanie on 2007-12-24
As you can hook up via ethernet cable, please disregard ipv6 being a problem.

---

### Post by JavaBeans2007123 on 2007-12-24
So is it drivers?

---

### Post by benrboone on 2007-12-24
did you ever check your gateway? Because once we have this information we can start tring to ping, first your computer then your router and then finally a website.  But we need the gateway just type route -n into a terminal window (It is found under application, accessories, terminal) and post the results or at least the gateway

also I don't think it is driver due to eth0 having an IP address

---

### Post by JavaBeans2007123 on 2007-12-25
Here you go:
vinh@vinh-desktop:~$ route -n 
Kernel IP routeing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
vinh@vinh-desktop:~$

---

### Post by benrboone on 2007-12-25
I looked at your post which should show your gateway but I certenly don't see your gateway.  my system at work and home this looks like this:


ben@ben-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 ath0

ben@ben-laptop:~$ 


Line two shows the default gateway of 192.168.2.1 notice it begins with 0.0.0.0
on your post I can not see a valid gateway

also how is your computer obtain it ip address?  is it DHCP or is it static
If you know your router address you could try pinging it.
also you might try pinging this address 64.233.167.104 and see if you get a reply from both of these.

---

### Post by benrboone on 2007-12-25
I looked at your post which should show your gateway but I certenly don't see your gateway.  my system at work and home this looks like this:


ben@ben-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 ath0

ben@ben-laptop:~$ 


Line two shows the default gateway of 192.168.2.1 notice it begins with 0.0.0.0
on your post I can not see a valid gateway

also how is your computer obtain it ip address?  is it DHCP or is it static
If you know your router address you could try pinging it.

---

### Post by JavaBeans2007123 on 2007-12-26
I think my IP address is set by the router.

---

### Post by guitronics on 2007-12-26
> **JavaBeans2007123 said:**
> I think my IP address is set by the router.
I'm having the same problem. I will try this stuff, and be booting back and forth between ubuntu and microsuck. I connect to the internet only via windoze.

On a Dual Boot, shouldn't the M$ section tell the correct IP protocols?

Will be back, and thanks for being there to help.

---

### Post by benrboone on 2007-12-26
Yes you could grab your gateway from your windows computer,  I assume that your Ubuntu Computer is currently set for DHCP, so it should be pulling the gateway from the router.  If you have been configuring it manually then of course you would need to put that in as well as the address and the DNS setting before it would work

Also have you tried pinging the address 64.233.167.104 ?
First try in a terminal "ping www.google.com"
Second, also in a terminal try: "ping 64.233.167.104"

If the Second one works but not the first one we could be have DNS problems, maybe regarding ipv6
there are several solution to this error 

If both don't work then I think you have a problem relating to  your gateway or router
So please get the gateway of the router this can be acomplished by getting it from your window computer: get a command prompt and type ipconfig

---

### Post by JavaBeans2007123 on 2007-12-31
This is what my router configuration pages says:
[IMG]http://img208.imageshack.us/img208/8855/routerio8.png[/IMG]
Edit:
This is what the ping says:
vinh@vinh-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
vinh@vinh-desktop:~$ ping 64.233.167.104
PING 64.233.167.104 (64.233.167.104) 56(84) bytes of data.
From 169.254.8.144 icmp_seq=2 Destination Host Unreachable
From 169.254.8.144 icmp_seq=3 Destination Host Unreachable
From 169.254.8.144 icmp_seq=4 Destination Host Unreachable
From 169.254.8.144 icmp_seq=6 Destination Host Unreachable
From 169.254.8.144 icmp_seq=7 Destination Host Unreachable
From 169.254.8.144 icmp_seq=8 Destination Host Unreachable
From 169.254.8.144 icmp_seq=10 Destination Host Unreachable
From 169.254.8.144 icmp_seq=11 Destination Host Unreachable
From 169.254.8.144 icmp_seq=12 Destination Host Unreachable

--- 64.233.167.104 ping statistics ---
15 packets transmitted, 0 received, +9 errors, 100% packet loss, time 14008ms
, pipe 3
vinh@vinh-desktop:~$

---

