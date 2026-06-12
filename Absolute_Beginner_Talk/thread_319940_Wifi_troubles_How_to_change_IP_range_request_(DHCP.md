---
title: "Wifi troubles: How to change IP range request (DHCP)"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-16
Hi,

I have a dualboot Ubuntu/XP and despite everything works fine in XP I've never been able to make wireless work with Ubuntu. Basically I can connect to my wifi network, I can ping my router (192.168.0.1) but that's about it: I cannot ping any website either with IP address or with name. 

In a last attempt to make things work, I checked the DHCP configuration of my wireless router and saw that the range of IP address it provides is from 192.168.0.100 to 192.168.0.199 for LAN. Since this is written to be related to LAN, I thought this was only related to the Ethernet ports on the router. 

To make sure I booted in XP, connected to my wireless network and checked my IP address (that was given by DHCP following the above rules) and my IP was 192.168.0.101.....so apparently **[COLOR="Red"]my router gives IP from 192.168.0.100 and 192.168.0.199[/COLOR]** for wireless as well!

OK now comes the Ubuntu part: I rebooted in Ubuntu, launched my wireless connection and typed **sudo dhclient eth1** in the terminal. Here is what I got:

Listening on LPF/eth1/00:12:f0:14:84:86
Sending on   LPF/eth1/00:12:f0:14:84:86
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
[COLOR="Red"][B]DHCPACK from 192.168.0.1
bound to 192.168.0.100[/B][/COLOR] -- renewal in 299628 seconds.

Just for fun I tried **ifconfig up eth1** and got:

eth1: Host name lookup failure

I don't really understand what means the output of the last command but at least the first is interesting: it seems that Ubuntu request an IP between ***.***.*.1 and ***.***.*.100 while my wireless router only gives addresses between ***.***.*.100 and ***.***.*.199 !!! Is this the cause of all my wireless troubles???? If it is how can I tell the wireless DHCP of Ubuntu to request IP in the same range that my router can give???

Thanks

PS: My wireless card is Intel 2200BG, I'm running Edgy Eft with Gnome Network manager (also tried Wifi-radar but same problem). Wired connection works perfectly with DHCP.

---

### Post by steve.horsley on 2006-12-16
A DHCP request simply asks to be assigned an address - it doesn't suggest a range. [COLOR="Red"]DHCPACK from 192.168.0.1[/COLOR] means that your request has been acknowleged by 192.168.0.1 - the DHCP server. [COLOR="Red"]bound to 192.168.0.100[/COLOR] means ths is the address you have been allocated. I see no problems here.

I think it should be **ifconfig eth1 up** rather than **ifconfig up eth1**, but it is already up so this will do nothing.

It sounds as though perhaps your default route isn't being set. Can you bring the wireless up, prove it's working by pinging the router, and then use the command route and post the output here?

---

### Post by kilou on 2006-12-16
Thanks for your help. So I connected to my wireless network and did the following commands:
[B]
iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Kilou"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A7:AE:50   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=-42 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3

**ping -c 2 192.168.0.1**
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=2.49 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=1.89 ms

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 1.895/2.193/2.491/0.298 ms


**route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

Anything could explain my issues??

---

### Post by Wall86 on 2006-12-16
could you by any chance look into your router to see if you can moddify the dhcp ip range? if so, just change it into the limits that your computer is trying to acces in,   

that might work.

---

### Post by steve.horsley on 2006-12-16
I don't think there's anything wrong with the DHCP allocation range. 

You can ping the router, and you have a default route that points to the router. Everything looks good. I know not all web sites respond to ping, but [www.ubuntuforums.org](www.ubuntuforums.org) does. I would thing that everything should work. Can you post the output of these two commands?
**ping 82.211.81.186**
and 
**ping [www.ubuntuforums.org](www.ubuntuforums.org)**
The second is to see if dns is working.

---

### Post by kilou on 2006-12-17
OK here are the outputs when connected to wireless network (I had to add -c 2 to the ping command otherwise it takes too long):

------------------------------------------------------------------------------------------------
**ping -c 2 82.211.81.186**
PING 82.211.81.186 (82.211.81.186) 56(84) bytes of data.

--- 82.211.81.186 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1000ms

**ping -c 2 [www.ubuntuforums.org](www.ubuntuforums.org)**
ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)
------------------------------------------------------------------------------------------------

So as you can see I cannot ping the IP or the name of the website :(

---

### Post by kilou on 2006-12-17
I am sooooo stupid ](*,)  I just checked the connection at the back of my wireless router and guess what: nothing was plugged in the WAN port!!!!! I just plugged the cable back in and oh miracle wireless works in Edgy :p 

However I can't understand how I could connect with XP, probably my Ethernet cable was also plugged in so I thought I was on wireless....when I was on the wired network actually.

Hey it's a newbie forum but you can move this thread to the "stupid" section anytime:rolleyes: 

Thanks again for all your help and sorry for the hassle....I'm writing this message on my wireless network :D

---

### Post by steve.horsley on 2006-12-17
Haha, haha! The old ones are the best ones. It's been a while since I did that. Thanks for a laugh.

Have fun with Linux. It's what it's for.

---

