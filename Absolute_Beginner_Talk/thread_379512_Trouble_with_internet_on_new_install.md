---
title: "Trouble with internet on new install"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by ld50 on 2007-03-08
Ok, I have been searching for some help on this topic and have come to the conclusion that I will just try to start my own thread.

I have just installed Ubuntu 6.10 and have been unable to access the internet through a wired connection. I am using the built in ethernet on a Dell Dimension 8250.  What info do you guys need to help me with this? I am currently re-installing the OS to undo any changes i have made...
Thank you in advance for any help...

only somewhat familiar with Linux so as detailed of explanations as possible would be helpful, sorry.

---

### Post by Bachstelze on 2007-03-08
The first thing we need it the output of :

```
lspci
```

If you're really unlucky, your card isn't detected/supported and will need additional work. Most of the time, though, it's just a configuration problem, please also paste the output of

```
sudo ifconfig -a
```

---

### Post by ld50 on 2007-03-08
I believe this is the info you are asking for...

02:0c.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 10)


eth0      Link encap:Ethernet  HWaddr 00:07:E9:C6:52:ED  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fec6:52ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2735 (2.6 KiB)  TX bytes:12672 (12.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:18:39:06:A6:D5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7813 (7.6 KiB)  TX bytes:7813 (7.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Bachstelze on 2007-03-08
All right, so your card is detected, it should be very simple. Could you describe a bit how your internet connection is set up (cable or DSL ? router ?)

---

### Post by ld50 on 2007-03-09
I'm connecting to a cable modem through a linksys router

---

### Post by Bachstelze on 2007-03-09
Then just

```
sudo dhclient eth1
```

should do the trick.

---

### Post by igknighted on 2007-03-09
Assuming your router is set up to use DHCP, try "sudo dhclient3 eth0"... I **think** thats the command.  Also you could try "sudo ifdown eth0" then "sudo ifup eth0".  I use those two commands when my internet quits on me and it almost always comes right back.

---

### Post by ld50 on 2007-03-09
i tried "sudo dhclient eth1" and it returns 

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
listening on LPF/eth1/00:18:39:06:a6:d5
sending on LPF/eth1/00:18:39:06:a6:d5
sending on socket/fallback
recieve_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 255.255.255.255 port 67 interval 8
send_packet: Network is down
.
.
.
No DHCPOFFERS received.
No working leases in persistent database - sleeping

---

### Post by Bachstelze on 2007-03-09
And with eth0 ?

---

### Post by ld50 on 2007-03-09
with eth0 i get,

Listening on LPF/eth0/00:07:e9:c6:52:ed
Sending on   LPF/eth0/00:07:e9:c6:52:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.103 -- renewal in 32464 seconds.

so this means the computer has been assigned an ip right? but there is still no internet

---

### Post by honns on 2007-03-09
It looks to me like your router is refusing the connection to your computer.  You may want to make sure that your router is set up correctly and that your settings in Networking match up to the router

---

### Post by ld50 on 2007-03-09
i dont think the router is set up incorrectly, i can connect with two other windows pc's, an ipaq, a printer and a psp... unless there is other settings for wired connections as all of those are wireless devices, what setting in Networking should be set to match the router?

---

### Post by ld50 on 2007-03-09
i dont know if this means anything but under the DNS tab in Network Settings two DNS servers are showing up as well as ma.dl.cox.net in the box labled Search Domains.  Cox is my service provider so there must be some communication going on.

---

### Post by honns on 2007-03-09
go to system -> networking tools and do a traceroute, put in any web site and see if the packets leave the router?  im guessing here...

o and before I didnt realize you were going through a wired connection, so there probably isnt anything wrong with your router

---

### Post by ld50 on 2007-03-09
traceroute only replies that the address cannot be found

---

### Post by honns on 2007-03-09
that means that the router is not sending your packets to the ISP.  When I plug into my Linksys router, my DNS is shows my router IP and there is no Domain.

---

### Post by ld50 on 2007-03-09
ok so when I log into the router and check the DHCP Clients the computer is not listed so I'm guessing that its still not getting an assigned ip? I'm totally lost here

---

### Post by honns on 2007-03-09
have you changed any settings in the router or are they all standard?

---

### Post by ld50 on 2007-03-09
no all the settings on the router are standard only the wireless security and a couple of port settings for p2p software have been changed

---

### Post by honns on 2007-03-09
i know this may sound stupid, but have you tried different ports on the routher (where the other computers are plugged in) or resetting the router (unplugging and plugging back in)?

---

### Post by ld50 on 2007-03-09
I've tried other ports, as well as resetting the router and the modem.

---

### Post by honns on 2007-03-09
jeez man, i dont know what to tell you.  Whenever I have plugged a computer into the router, it worked right away.  Sorry that I havent been much help, hopefully someone else will have some idea what the problem is.  good luck

---

### Post by Sarge50 on 2007-03-09
I am a real amateur compared to all these experts - but - it sounds to me like your Network Adapter is not compatible with the Linux Operating System. Check this site out and even the adapter manufacturers (Intel) site - there are a lot of Network Adapters around that will not work with Linux and/or need new drivers.

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

---

### Post by honns on 2007-03-09
[http://www.ubuntuforums.org/showthread.php?t=378984&highlight=router](http://www.ubuntuforums.org/showthread.php?t=378984&highlight=router)

that thread gave me an idea, you could try and force the DNS.  U know the dns of your router, so if u just add it in maybe it will connect

---

### Post by ld50 on 2007-03-09
well, thanks a lot.... hopefully someone will figure this out, I may have to go back to trying to get the wireless to work.  I tried the wireless but it needs ndiswrapper for the drivers, thinking that a wired connection would be simple I hooked it up and here I am stuck again... Would it be possible that having the wireless card is interfering with the settings somehow?

---

### Post by honns on 2007-03-09
i dunno, but you could just uncheck the wireless in System -> Networking.  Also, double click on the icon of two computers near the date and time and make sure that eth0 is selected.  lo is a loop back and wlan0 is wireless, neither of which you want

---

### Post by ld50 on 2007-03-09
I tried adding the DNS server but that hasn't solved anything.  I'm thinking this is something between my computer and router.  oh and I dont have two computers by the time and date, only the speaker icon. Is there a command I can use to see if my computer is connected to the router properly?  Also, if i type the routers address into firefox it cannot be found. I'm thinking that would still work if it were a DNS proplem right?

---

### Post by honns on 2007-03-09
to your last comment, i dont want to say because im not sure.

there is only one more suggestion i can make, unplug your modem from your router, plug the modem into the computer, reset the laptop and the modem.  If you can connect to the internet you know its your router, if not then you most likely have defective or unsupported hardware.

---

