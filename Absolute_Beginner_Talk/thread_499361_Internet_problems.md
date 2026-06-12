---
title: "Internet problems"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Mano_vardas_Tomas on 2007-07-12
Hi,

so I have this problem with internet. Not much understand about PC, but here's what I got:
I use D-Link ADSL router. I configured internet in pppoeconf and Network Settings. Everything seems to work, but sometime I can't connect to internet, sometime I can. When I cannot connect, I restart PC till I am connected.  Also when I am connected, internet stops every 15-30 min. and with commands poff dsl-provider and pon dsl-provider, I can connect again. 

Here's what I get when internet doesn't work:

laisvas@nepriklausomas:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:95:07:47:71
          inet addr:169.254.252.151  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::240:95ff:fe07:4771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12992 (12.6 KiB)  TX bytes:12992 (12.6 KiB)

laisvas@nepriklausomas:~$ plog
Jul 12 20:42:13 localhost pppd[5273]: Timeout waiting for PADO packets
Jul 12 20:42:13 localhost pppd[5273]: Unable to complete PPPoE Discovery

laisvas@nepriklausomas:~$ sudo /etc/init.d/networking restart
Reconfiguring network interfaces...There is already a pid file /var/run/dhclient.eth0.pid with pid 2802
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:95:07:47:71
Sending on   LPF/eth0/00:40:95:07:47:71
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Plugin rp-pppoe.so loaded.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:95:07:47:71
Sending on   LPF/eth0/00:40:95:07:47:71
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done.


Here's what I get when internet does work:

laisvas@nepriklausomas:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:95:07:47:71
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:95ff:fe07:4771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2149861 (2.0 MiB)  TX bytes:392016 (382.8 KiB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:78.62.15.196  P-t-P:213.190.60.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:569236 (555.8 KiB)  TX bytes:49263 (48.1 KiB)

laisvas@nepriklausomas:~$ plog
Jul 12 23:33:40 localhost pppd[3793]: PAP authentication succeeded
Jul 12 23:33:40 localhost pppd[3793]: peer from calling number 00:90:1A:42:1B:5D authorized
Jul 12 23:33:40 localhost pppd[3793]: Cannot determine ethernet address for proxy ARP
Jul 12 23:33:40 localhost pppd[3793]: local  IP address 78.62.15.196
Jul 12 23:33:40 localhost pppd[3793]: remote IP address 213.190.60.229
Jul 12 23:33:40 localhost pppd[3793]: primary   DNS address 212.59.1.1
Jul 12 23:33:40 localhost pppd[3793]: secondary DNS address 212.59.2.2

Hope someone understand what I am talking about, and will help me.

---

### Post by phr0ze on 2007-07-13
I thought the Dlink would take care of all the DSL pppoe connection issues and all your PC has to do is talk to the dlink. Did you change the dlink configurations?

---

### Post by Austin_KW on 2007-07-13
Yes why are you tunneling a ppp connection through your router?

Setup the ppp connection on the modem side of the router, and use the router to share your connection to all PCs  on your network.

---

### Post by Mano_vardas_Tomas on 2007-07-15
> **Austin_KW said:**
> Yes why are you tunneling a ppp connection through your router?

Setup the ppp connection on the modem side of the router, and use the router to share your connection to all PCs  on your network.

I am doing that because I don't understand much :)

Could someone help me explain step by step how I could  fix that problem?

---

### Post by mendingo84 on 2007-07-15
yeah. log into your router ( type 192.168.1.1 in any browser and you'll get the router interface) and find where it has listed how it connects to the internet. configure it to pppoe in that place.

---

### Post by Mano_vardas_Tomas on 2007-07-15
Well I tried several times to connect to router, but I always get "192.168.1.1 not respond".
I called internet provider and they send a man. He pluged his laptop with win and he could connect to router. The man couldn't explain, what's wrong, 'cause he doesn't know linux.

Is there is any way to deal with this?

---

### Post by Austin_KW on 2007-07-16
Do not bring up the ppp link, your eth0 connection will allow you to connect to the router.

If you bring up ppp it will replace your default route to send everything through the ppp tunnel (to the internet) and of course it cannot find your router on the other side of the ppp tunnel.

---

### Post by Mano_vardas_Tomas on 2007-07-16
> **Austin_KW said:**
> Do not bring up the ppp link, your eth0 connection will allow you to connect to the router.

If you bring up ppp it will replace your default route to send everything through the ppp tunnel (to the internet) and of course it cannot find your router on the other side of the ppp tunnel.

So what I am doing wrong? Thing is that now when I boot there is no internet, but sometime after booting there is internet though I don't change anything.

---

### Post by Austin_KW on 2007-07-16
> **Mano_vardas_Tomas said:**
> So what I am doing wrong? Thing is that now when I boot there is no internet, but sometime after booting there is internet though I don't change anything.

Not sure, I don't use the ppp tools on linux, I use the modem side of my router.

But, you must have at some stage done a pppconfig and created a configuration for your ppp connection. And something is bringing up this connection after boot, is there an "auto ppp0" line in /etc/network/interfaces

---

### Post by Mano_vardas_Tomas on 2007-07-17
I'am completely lost.
I reinstalled ubuntu. Could someone tell me step by step how to make internet work with D-link?
More I read more I get lost.
Now there is no internet. Fresh install. What should I do. I followed this tutorial [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html), but I don't get where I have to enter my connection user name and password. As much as I understand I have to connect into my router, but how can I do that if I don't have internet? Previuosly I used pppoeconf and there enterd username and password, but know "sorry acces concentrator of your provider did not respond".

---

### Post by CrazyCanuck on 2007-07-17
Some food for thought.  I recently was able to get back online using cable instead of ADSL.  There is a signal issue that can cause intermittent problems like you describe.  Perhaps your signal is too weak or too strong?  Is there a diagnostic page through your browser that you can look at?  For me to look at POST settings on my modem, i enter within my Internet browser the following:

192.168.100.1

What my cable provider had to do was use a filter to reduce the signal coming to my house, as it was too strong.  Perhaps you have an opposite issue with a weak signal?  See if you can check out your modem settings to verify that your signal is within limits of your modem.  Maybe a call to your ISP is worth being done as well.

Good luck.  :)

CC

---

### Post by Rui Pais on 2007-07-17
> **Mano_vardas_Tomas said:**
> I'am completely lost.
I reinstalled ubuntu. Could someone tell me step by step how to make internet work with D-link?
More I read more I get lost.
Now there is no internet. Fresh install. What should I do. I followed this tutorial [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html), but I don't get where I have to enter my connection user name and password. As much as I understand I have to connect into my router, but how can I do that if I don't have internet? Previuosly I used pppoeconf and there enterd username and password, but know "sorry acces concentrator of your provider did not respond".

hi,
is your D-Link a router that connect to you computer through a net cable/card? Can describe a little more your network setup? And model of router (is just the router and a net card or do you have some ADSL modem?

An advice. You shouldn't, for your security, post the output of plog on a public place like this.

---

### Post by Austin_KW on 2007-07-17
> **Mano_vardas_Tomas said:**
> I'am completely lost.
I reinstalled ubuntu. Could someone tell me step by step how to make internet work with D-link?
More I read more I get lost.
Now there is no internet. Fresh install. What should I do. I followed this tutorial [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html), but I don't get where I have to enter my connection user name and password. As much as I understand I have to connect into my router, but how can I do that if I don't have internet? Previuosly I used pppoeconf and there enterd username and password, but know "sorry acces concentrator of your provider did not respond".

First you have to get your local network (connection to your router) up. This will be up when you have a ip address assigned by your router to your PC.

In a terminal enter the command "ifconfig" and verify that you have a 192.168.1.x address for eth0.

Once you have an ip address you should be able to connect to your router at [http://192.168.1.1](http://192.168.1.1) You then need to configure the modem side of your router with your ISP login information. This configuration page will be called internet/WAN/DSL or some such name. 
When you connect to your router you may need to enter the router username/password before setting configurations. A quick google of your router model number and "password" will usually find the default username/password

---

### Post by Mano_vardas_Tomas on 2007-07-18
> **Rui Pais said:**
> hi,
is your D-Link a router that connect to you computer through a net cable/card? Can describe a little more your network setup? And model of router (is just the router and a net card or do you have some ADSL modem?

An advice. You shouldn't, for your security, post the output of plog on a public place like this.

My D-Link router connect through net card. Model of the router DSL-G604T.
That's all I understand :)

Thanks for advice.

---

### Post by Rui Pais on 2007-07-18
Ok, so there is no need for pppoeconfs. You got the simple and better way to connect to internet.

You just need to ensure, 1st, that your net card is properly configured and working, and 2nd, your router and internet settings are ok.

For network configuration please post the output of:
```
ifconfig 
```
and
```
cat /etc/network/interfaces
```

For the 2nd part (maybe better check if network config is ok first)
you must do what Austin_KW suggested 2 posts above.

---

### Post by Mano_vardas_Tomas on 2007-07-18
the result of cat /etc/network/interfaces is:
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

The result of ifconfig
eth0 Link encap:Ethernet HWaddr 00:19:21:5c:52:96
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0,0 b) TX bytes:0 (0,0 b)
Interrupt: 22 Base address:0x4000

eth0:avah
Link encap:Ethernet HWaddr 00:19:21:5c:52:96
inet addr:169.254.5.166 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:22 Base address:0x4000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:754 errors:0 dropped:0 overruns:0 frame:0
TX packets:754 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 tqueuelen:0
RX bytes:60372 (58.9 KiB) TX bytes:60372 (58.9 KiB)

What this eth0: avah means.

---

### Post by Rui Pais on 2007-07-18
> **Mano_vardas_Tomas said:**
> the result of cat /etc/network/interfaces is:
...
inet addr:169.254.5.166 Bcast:169.254.255.255 Mask:255.255.0.0
...
What this eth0: avah means.

This seems to be a dhcp problem. For some reason when the dynamic IP is set it's not on the same network that your router (and you couldn't navigate of course).

avah is some that came from the MAC world (as far as i know) as is been implemented since Feisty (or edgy?).
Frankly i don't see either the purpose or the necessity (maybe if one had a mist net with macs...) 
I had a minimal install that don't have that and on my 2nd computer a removed that packages and services.

About you dhcp. Try a static ip to see if that work:
```
sudo mv /etc/network/interfaces /etc/network/interfaces_BAKUP
gksudo gedit /etc/network/interfaces
```
and past this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```
save and do:
```
sudo invoke-rc.d networking restart
```
after that you should be able to see your router.

Good luck.

---

### Post by Austin_KW on 2007-07-18
Do you have a cable connected to eth0, you are not transmitting/receiving any packets

---

### Post by Mano_vardas_Tomas on 2007-07-18
Yes, the cable is connected to net card.

I tried what Rui Pais said, but still I can't see my router.

When I first time made sudo invoke-rc.d networking restart command it showed:

 * Reconfiguring network interfaces...     
RTNETLINK answers: No such process 
SIOCDELRT: No such process 

Second time it seems worked:

 * Reconfiguring network interfaces...                                   [ OK ] 

Code cat /etc/network/interfaces shows:

# The loopback network interface 
auto lo 
iface lo inet loopback 

# The primary network interface 
auto eth0 
iface eth0 inet static 
address 192.168.1.2 
netmask 255.255.255.0 
gateway 192.168.1.1

Code  sudo ifconfig shows:

eth0      Link encap:Ethernet  HWaddr 00:40:95:07:47:71  
          inet6 addr: fe80::240:95ff:fe07:4771/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:5 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:95:07:47:71  
          inet addr:169.254.4.209  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:375 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:32130 (31.3 KiB)  TX bytes:32130 (31.3 KiB) 

I know that ISP provides dynamic IP.

So, what's wrong? Maybe my drivers for net card are bad? For me it seemes that my net card and router are not communicating, 'cause earlier when I had internet at connection info it showed speed 100 Mbps, now it shows 10 Mbps.

---

### Post by Rui Pais on 2007-07-18
sorry, Austin_KW is right in asking. I assumed, maybe incorrectly, that you were using a wire to connect net card to router. 
Is that the case? 

It still says your eth0 is 169.254.4.209. So dhcp should still give that IP address to the card (Your Internet provider is assign you an **external** IP, the one i said you should avoid post, your internel IP should be set by you or by the DHCP server).

i would suggest that you turned off ipv6 too to make things simpler and a reboot of machine instead of just restart the network... 
To turn off ipv6:
```
sudo sh -c "echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist"
```
then reboot and check if eth0 have the address of 192.168.1.2

good luck

---

### Post by Austin_KW on 2007-07-18
I still dont see any traffic on that eth interface, hence no dhcp assigned address just the auto allocated avhi (useless). 
Try a different port on your router, and maybe restarting the router.

---

### Post by Mano_vardas_Tomas on 2007-07-19
> **Rui Pais said:**
> sorry, Austin_KW is right in asking. I assumed, maybe incorrectly, that you were using a wire to connect net card to router. 
Is that the case? 

It still says your eth0 is 169.254.4.209. So dhcp should still give that IP address to the card (Your Internet provider is assign you an **external** IP, the one i said you should avoid post, your internel IP should be set by you or by the DHCP server).

i would suggest that you turned off ipv6 too to make things simpler and a reboot of machine instead of just restart the network... 
To turn off ipv6:
```
sudo sh -c "echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist"
```
then reboot and check if eth0 have the address of 192.168.1.2

good luck

Actually I tried to reboot and after that there wasn't wired network at all. When I changed back to dhcp wired network was established.

I've tried different ports on my router, although I've reset it, but it didn't help.

---

### Post by Austin_KW on 2007-07-19
I dont see why you are having these problems, can you try a different pc/OS/cable/router

---

### Post by Mano_vardas_Tomas on 2007-07-19
Now code ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:40:95:07:47:71  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10626 (10.3 KiB)  TX bytes:10626 (10.3 KiB)

But still I can't connect  nor to my router nor to any website (browser searches longer website than router).  I disabled ipv6 using about:config at browser. Although I used Rui Pais code.  I also tried changing DNS servers from ISP's to router's IP.

I think router is OK, because man from ISP could connect using his laptop connected to my router.

---

### Post by Austin_KW on 2007-07-19
This is from setting a static address not allocated from the router?

The RX and TX counters are still 0, So the connection is not up.
Is the link light on on the router when you connect the cable?

The most obvious thing to try is to change the cable, or try a different PC

---

### Post by Rui Pais on 2007-07-19
thats so weird...

everything looks correct, you don't even have ipv6 on the way...

can you ping the router?
```
ping -c2 192.168.1.1
```?

Just to be check everything, whats the output of:
```
lshw -C net
```


i haven't no idea what could be wrong, i confess...

---

### Post by Mano_vardas_Tomas on 2007-07-20
Thats what I get with those codes:

kame@kampas:~$ ping -c2 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1008ms
, pipe 2
kame@kampas:~$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 10
       serial: 00:40:95:07:47:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=32 mingnt=32 multicast=yes
       resources: ioport:dc00-dcff iomemory:e3050000-e30500ff irq:5

Also, when I started computer code ifconfig showed that eth0:avah and that ip starting 169, then I ran code sudo invoke-rc.d networking restart and code ifconfig this time showed info of my last post.

I wonder if man's of IPS configuration on D-Link could have some influence? When he connected to router with his laltop he made pppoe configuration and exiting I think he turned it to bridge.

By the way with previuos ubuntu (same Feisty) installations I had internet, but configured with pppoeconf (which now doesn't work). It was that after shuting down PC and starting it again there wasn't internet and I had to restart PC lot's of time to have internet again.

---

### Post by Austin_KW on 2007-07-20
There should be a way to restore factory defaults on the router. But I really don't know where the problem is at.

---

### Post by Rui Pais on 2007-07-20
Yes your linux configuration seems to be correct. 
You got card recognized, modules loaded. And a minimal and simple configuration, nothing seems to be raising a problem.

The issue is that Linux can't communicate to router.
So something should be incorrect on that part. 
There things that can be done alternatively on Linux size (like different module/driver for your net card, or turn avah off) but seems quite unuseful cause all indicates that the problem is on the router.

About pppoe settings. That should be done all on router side, too. Pppoeconf are for ADSL modems. 
If the person that config your router set it to bridge mode, instead of  setting plain PPPoE, that should be the reason to why it fail, (i think, never used that...)

Do you have other machine or laptop that you can use with router? Or other OS on the same machine?
Did run with liveCD (or old livecds) make router accessible?

---

### Post by Austin_KW on 2007-07-20
Bridge mode often just means turning dhcp off, but it is still not responding when you set static IP?

I dont understand why the eth0 tx counter in not incrementing, it does not appear to attempt to send. Is the ethernet link light on at the router?  What is the output of "route -n" from a terminal?

---

### Post by Mano_vardas_Tomas on 2007-07-21
Well, on the router ADSL, WLAN, Power, port lights are on and status is blinking.

I tried running and configuring network using live CD, but nothing changes.

I think I restored factory defaults by reseting router.

---

### Post by Mano_vardas_Tomas on 2007-07-22
That's what route -n shows.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Unfortunatelly, I don't have other PC or other OS.

---

### Post by Rui Pais on 2007-07-22
what i still don't get it is why it stll insist on assign IPs from 169.254.x.x... 
i don't know if that cause for problems, but i wonder if eth0 get both IPs some how assigned (or at least they appear on route command) its preventing router on the 192.168.x.x being visible...

Are you sure your interfaces only have one iface eth0 section with a static 192.168.1.2 (or other number from 2 to 255)? 

Maybe try to remove avahi daemon from boot process should give only one IP (the correct static from interfaces). 
To do that run:
```
sudo update-rc.d -f avahi-daemon remove
```
and then reboot.

Just another thing. 
If you don't have another way to access the router, maybe it's not a good idea reset it to factory settings. This should delete your username and  password and without knowing for sure that you can connect to it after the reset.

---

### Post by Mano_vardas_Tomas on 2007-07-23
At laaaassstttt!!!!!! 

I have internet on ubuntu. Thank you Rui Pais and others who tried to help.

I think that last code with removing avahi did something and after rebooting I just swithched to dhcp and connected into router.

Thank's a lot! :)

---

### Post by Rui Pais on 2007-07-23
> **Mano_vardas_Tomas said:**
> At laaaassstttt!!!!!! 

I have internet on ubuntu. Thank you Rui Pais and others who tried to help.

I think that last code with removing avahi did something and after rebooting I just swithched to dhcp and connected into router.

Thank's a lot! :)

Ah! it was avahi the bad guy... 
it probably needed to be configured to go for a 192.168.x.x instead of 169.254.x.x...

Anyway you have, this way, less things to config and less services running. The simpler solutions are always the better.

Glad you have internet.
Have fun :)

---

### Post by Lek130 on 2007-07-26
just came across this thread while searching for something different ... i also had an avahi problem. it killed me, that i had a 16x. address with ifconfig and ipconfig within my vm. was wondering where this is comming from. took me a long time to figure that out :)

---

### Post by lisati on 2007-07-26
If your D-link ADSL router is anything like the one hooked up to my system, you might want to try the ip address 10.1.1.1 

The factory default user name is ADMIN and has a default password of PASSWORD

---

