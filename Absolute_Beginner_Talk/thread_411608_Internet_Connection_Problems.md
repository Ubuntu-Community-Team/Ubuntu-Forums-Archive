---
title: "Internet Connection Problems"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by aka50 on 2007-04-17
Just installed Ubuntu on a partition and I have been loving it; however, I am having internet problems at my home connection. I also have WinXP on another partition (dual-boot) and have not had trouble connecting to the internet there.

I originally installed Ubuntu at my University and the internet worked well over the network. At home my cable modem->router however is not allowing me to connect.

I have read posts on this forum and elsewhere. I even tried: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

and I have had no success!

When I run ifconfig my eth0 shows addresses,masks, etc. I can even connect to my router (admin panel) which is a Netgear. I am also not using wireless.

 Anyone?

Thanks,
-aka50

---

### Post by zvacet on 2007-04-17
system>administration>network settings>highlight your modem>properties>select your type of connection(dhcp,static),chek upper left box>close.DNS tab>delete address you find there and put your nameserver instead>close.
```
pppoeconf
```

---

### Post by aberry5555 on 2007-04-17
Are you connecting using DHCP (automatic configuration) or using a static IP address? if it's the latter you'll need to copy exactly what the settings are from Windows. 

From the sounds of it, though it is a DNS problem (dynamic name serving). DNS, if you didn't know, is the system on the net net that takes the text address you type in, then asks a main DNS server on the web what it's IP address is. (which it knows by the IP address you put in the settings).
 Since you seem to be able to connect to your routers IP address I assume most of your settings are correct and this is the problem. 

To double-check this try typing in to firefox the following IP address: 212.58.224.131. If it takes you to the BBC website then you know that you're connected to the net but have the wrong DNS settings.

---

### Post by aka50 on 2007-04-17
I am using DHCP not Static. When I tried static that too did not work. I used the same settings as shown in WinXP. I found those settings in WinXP using the command window and using "ipconfig /all" When I tried going to the BBC website via the ip address as detailed above my Mozilla window said connecting to BBC in the bottom left but it still did not work. 

?

---

### Post by Seisen on 2007-04-17
What type of cable modem/router is it?

---

### Post by aka50 on 2007-04-17
> **Seisen said:**
> What type of cable modem/router is it?
Netgear WGR614 v5, speedstream cable modem behind that from cable company.

---

### Post by aka50 on 2007-04-17
> **Seisen said:**
> What type of cable modem/router is it?
Netgear WGR614 v5, speed stream cable modem behind that from cable company.

---

### Post by Seisen on 2007-04-17
Have you upgraded the firmware for  the router? If you haven't see if that helps fix the problem.

---

### Post by Austin_KW on 2007-04-17
Open a terminal and post the output from the following commands
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
host google.com
ping -c 3 72.14.207.99

---

### Post by aka50 on 2007-04-17
Did the firmware upgrade but it did not work.

I am begining to think that the person who helped me install Ubuntu added a firewall feature. I am wondering if this could be the issue, since all others are not working. 

If a firewall could be the problem how would I turn if off? Or check to see if there is one even running?

---

### Post by stump138 on 2007-04-17
are you able to ping addresses outside of your network ? 

ping [www.google.com](www.google.com) (do a ctrl + c to stop it).  This will also make sure your DNS is resolving correctly.

---

### Post by annda on 2007-04-17
this should not be a firewall issue (although linux has one enabled by default).

you say you can connect to your router. this is good. there is some connectivity.

when you run ifconfig, does eth0 have an IP? it's inet addr, not inet6 addr.

---

### Post by annda on 2007-04-17
> **stump138 said:**
> are you able to ping addresses outside of your network ? 

ping [www.google.com](www.google.com) (do a ctrl + c to stop it).  This will also make sure your DNS is resolving correctly.

if you can't, try Austin_KW's advice and ping an IP:

```
ping -c 3 72.14.207.99
```

---

### Post by aka50 on 2007-04-17
okay... we are getting close. In short here's what I think the problem relates to, and below are what was requested.

ping [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

also

host google.com
;; connection timed out; no servers could be reached


BUT!!!

ping 72.14.207.99      

worked!!! 
example of what returned:

64 bytes from 72.14.207.99 icmp_seq=1 ttl=241 time=92.3ms

---------------------------------------------------------------------
HERE ARE SOME OTHER REQUESTED TESTS:
---------------------------------------------------------------------

ifconfig -a
eth0 (which is what I am using) returned:  

inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
and everything else looked good.

----------------------------------------------------------------------
cat /etc/network/interfaces

returned: (I only wrote what I think is related to this)

auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.4
netmask 255.255.255.0
gateway 75.15.121.135

iface dsl-provider inet ppp
provider dsl-provider

auto eth0
-------------------------------------------------------
cat /etc/resolv.conf

returned:

namerserver 192.168.1.1

--------------------------------------

---

### Post by annda on 2007-04-17
so you get an IP and everything looks fine except DNS (despite the right entry in /etc/resolv.conf)

i'd suggest restarting the connection:

```
sudo ifdown eth0
sudo ifup eth0
```

and pinging [www.google.com](www.google.com) again.

if it doesn't work, try this guide to disable ipv6 (it helped me bypass my father's router's inability to handle IPv6)
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

### Post by Austin_KW on 2007-04-17
> 
iface eth0 inet dhcp
address 192.168.1.4
netmask 255.255.255.0
gateway 75.15.121.135

This looks like a mashup of 2 different networks configs
It should just be dhcp without address/mask/gateway or static with (address/gateway...)

---

### Post by aka50 on 2007-04-17
I do not have much knowledge with networking; however, I think I am seeing how some things might work.

I can open Mozilla (in Ubuntu) and enter the ip address for google and it works! I can even search; however, I can not view the page results, probably due to the same reason I can not view google.com. 

Can someone briefly explain this to me, or give me a link or search term so I can learn/research about this more?

Also, **annda's ** recommendation: ([http://ubuntuforums.org/showthread.php?t=6841)](http://ubuntuforums.org/showthread.php?t=6841)), did not work!

Thanks again!

---

### Post by Austin_KW on 2007-04-17
Something is slightly wrong with your configuration. You did not give me all the configuration but it looks like you are connected on two networks (a link to 75.15.121.135?  and an ethernet link on your local subnet).  Either that or you have left some configuration from a previous network connection. 

I really can not tell because you only gave me part of the output. 

iface eth0 inet dhcp <- this says get eth0's IP address from the (local) network
But the following lines
address 192.168.1.4 netmask 255.255.255.0 <- these say to use ip address 192.168.1.4/24 for eth0
gateway 75.15.121.135 <- this says your default route(internet) is via this address

namerserver 192.168.1.1 <- this says dhcp is setting you dnsnameserver to some device (probably your router)

You have a proble resolving addresses (ie you cannot find google.com by name)  so there is probably a problem with your nameserver config. But I can not be sure why.

My first guess would be to edit /etc/network/interfaces and comment out the 3 lines (add '#' as first character)
address 192.168.1.4
netmask 255.255.255.0
gateway 75.15.121.135
save the changes.

Then 
sudo ifdown eth0
sudo ifup eth0 

and check your internet access with 
ping -c 3 google.com
ping -c 3 72.14.207.99
tracepath 72.14.207.99


If that does not work we need to see the full output from the following commands
ifconfig -a
route
grep -v \# /etc/dhcp3/dhclient.conf

---

### Post by n3tfury on 2007-04-18
> **Austin_KW said:**
> This looks like a mashup of 2 different networks configs
It should just be dhcp without address/mask/gateway or static with (address/gateway...)

yep, that gateway is not correct.  you can see that it is getting dhcp address.

---

### Post by aka50 on 2007-04-18
As requested...
--------------------------------------------------------------------------
jjwillia@aka50:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:18:EA:8E:E9  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:feea:8ee9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11831 (11.5 KiB)  TX bytes:16055 (15.6 KiB)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr 00:0C:41:65:FC:B8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:d9000000-d9002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jjwillia@aka50:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
grep -v default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
jjwillia@aka50:~$ grep -v \# /etc/dhcp3/dhclient.conf

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;


jjwillia@aka50:~$

---

### Post by Austin_KW on 2007-04-18
Now that looks ok, Is DNS still not working
Verify the you can use the dns in your router with
host google.com 192.168.1.1

If that does not work, see if you can access the opendns server with
host google.com 208.67.222.222 

If only opendns works add the following lines to the start of  /etc/dhcp3/dhclient.conf (And reboot)
prepend domain-name-servers 208.67.222.222
prepend domain-name-servers 208.67.220.220

---

### Post by aka50 on 2007-04-18
Man.... still nothing!

Both

host google.com 192.168.1.1
host google.com 208.67.222.222 

came back with:
;; connection timed out; no servers could be reached

this sounds like my problem but I have no clue on how to attack it:
[http://doc.gwos.org/index.php/Router_DNS_Problems](http://doc.gwos.org/index.php/Router_DNS_Problems)

---

### Post by aka50 on 2007-04-18
OKAY I am ON!

I had a friend (who I have been trying to get a hold of) help me. It had to do with ports not being opened in Ubuntu?

Thanks again for all your help. Ill know I can come back here when I have other questions and recieve good sugguestions from a warm community!

Thanks again,
-a

---

### Post by Austin_KW on 2007-04-18
Well done, But just for people following this thread and looking for a solution; What ports and how did you open them?

---

### Post by n3tfury on 2007-04-18
> **aka50 said:**
> OKAY I am ON!

I had a friend (who I have been trying to get a hold of) help me. It had to do with ports not being opened in Ubuntu?

Thanks again for all your help. Ill know I can come back here when I have other questions and recieve good sugguestions from a warm community!

Thanks again,
-a

from what i know, by default that's not correct that you would have to open up ports.  you mentioned a buddy installing a firewall previously, i gather this is the same buddy who had to open these ports.

---

### Post by aka50 on 2007-04-22
Well I am not sure what exact ports. A simple "sudo iptables -F" worked. I have no idea what it does/ did. And NO this not the same person you installed the firewall.

---

### Post by n3tfury on 2007-04-22
yep, your previous buddy's rule(s) hosed your connection.  -f flushes all the rules in all chains if one isn't specified.

---

