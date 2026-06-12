---
title: "cannot connect to the internet with seemingly correct settings"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by zenix on 2007-07-08
I can not connect to the internet. Simple as that, but what I don't understand is my settings seem to be completely correct. I use DHCP to determine the IP. I tried to disable IPv6 by doing [FONT=Courier New]alias net-pf-10[/FONT] off but that doesn't seem to work :(

The gateway is 192.168.1.254

Output of [FONT=Courier New]ifconfig -a[/FONT]
```
eth1      Link encap:Ethernet  HWaddr 00:12:17:5B:84:21  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386471 (377.4 KiB)  TX bytes:4251 (4.1 KiB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```Output of [FONT=Courier New]iwconfig[/FONT]
```
lo        no wireless extensions.

eth1      no wireless extensions.
```Output of [FONT=Courier New]lspci[/FONT]
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:10.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
``` A run of [FONT=Courier New]sudo ps -ef | grep -i dhcp[/FONT] just a bit before this post
```
dhcp      7153  4835  0 21:41 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1
colin     8303  5758  0 22:35 pts/0    00:00:00 grep -i dhcp
```Contents /etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp
address 192.168.1.21
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.1.121
netmask 255.255.255.0
gateway 192.168.1.254

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```I hope this is enough information to help you help me :)

---

### Post by Computer-Slave on 2007-07-09
> **zenix said:**
> I can not connect to the internet. Simple as that, but what I don't understand is my settings seem to be completely correct. I use DHCP to determine the IP. I tried to disable IPv6 by doing [FONT=Courier New]alias net-pf-10[/FONT] off but that doesn't seem to work :(

The gateway is 192.168.1.254

Output of [FONT=Courier New]ifconfig -a[/FONT]
```
eth1      Link encap:Ethernet  HWaddr 00:12:17:5B:84:21  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386471 (377.4 KiB)  TX bytes:4251 (4.1 KiB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```Output of [FONT=Courier New]iwconfig[/FONT]
```
lo        no wireless extensions.

eth1      no wireless extensions.
```Output of [FONT=Courier New]lspci[/FONT]
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:10.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
``` A run of [FONT=Courier New]sudo ps -ef | grep -i dhcp[/FONT] just a bit before this post
```
dhcp      7153  4835  0 21:41 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1
colin     8303  5758  0 22:35 pts/0    00:00:00 grep -i dhcp
```Contents /etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp
address 192.168.1.21
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.1.121
netmask 255.255.255.0
gateway 192.168.1.254

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```I hope this is enough information to help you help me :)
How r u Using Internet LAN or Direct?

---

### Post by Amplidude on 2007-07-09
Hi 

I'm a newbie, so keep the salt handy! It seems to me that there is a configuration problem.  Your  Output of ifconfig -a shows one Network Interface Card (eth1), but your Contents /etc/network/interfaces shows three:

> auto eth0
iface eth0 inet dhcp
address 192.168.1.21
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.1.121
netmask 255.255.255.0
gateway 192.168.1.254

auto eth2
iface eth2 inet dhcp

How many NIC do you have?

Ciao

---

### Post by Computer-Slave on 2007-07-09
> **Amplidude said:**
> Hi 

I'm a newbie, so keep the salt handy! It seems to me that there is a configuration problem.  Your  Output of ifconfig -a shows one Network Interface Card (eth1), but your Contents /etc/network/interfaces shows three:



How many NIC do you have?

Ciao
Actually there are no problems in the configurations > ifconfig -a only shows alive Networks but the /etc/network/interfaces shows Online and Offline both. i hope i increased your knowledge for more info on linux visit site mentioned in my Signature and please become a registered member.

Thanks!

---

### Post by zenix on 2007-07-09
I connect through a lan via DHCP. (redundant?) About 9 days ago I had gone on vacation and connected directly to another computer via a cross-over cable. I had done a static address with the gateway set to itself (effectivley creating a loopback, I think) and had worked for about 2-3 days but then the 2 computers just stopped seeing each other. Just like that. Thankfully, our (I had gone with family) ideas of a "fun" game had changed then and I switched OS and continued on my merry way. Also, I only started seeing eth1 listed in ifconfig instead of eth0 after about 2 days before the vacation (so 11 days total) when I had gotten a new NIC card. I only have 1 NIC, the new one replacing the old.
 
[quote=Amplidude]
How many NIC do you have?[/quote]
Only 1, as I stated above
 
[quote=Computer-Slave]
How r u Using Internet LAN or Direct?
[/quote]
DHCP, but directly before hand, again as stated above. These troubles only started after I tried to switch back from a direct connection over the cross-over cable to the family DHCP.
[quote=Computer-Slave]
Actually there are no problems in the configurations 
[/quote]
Whew! I had thought that but wasn't sure wether or not that was the origin of the error as well as not knowing how to properly modifing the file. Seems easy enough but you never know ;)

---

### Post by zenix on 2007-07-10
*BUMP*

With the bump comes some more debugging information:
I have openSUSE 10.2 installed and running successfully. Network works, as well as a bit more device detection. (It sees my Nintendo USB Wi-Fi adapter, wether or not it works is still unknown, while Ubuntu has yet to do so automaggiclly but I have gotten detected manually) Also, a run of Knoppix is ok as well as Ubuntu 6.06, 6.10, and 7.04 live CDs. This all seems to point to a local configuration issue. In hopes to fix everything, I had tried to do a simple copy/paste of the configuration file, but to no avail as the configuration file is all openSUSE-ish and not Ubuntu-ish! :P

---

### Post by Rui Pais on 2007-07-10
Hi
i read some posts in this forum where net fail when several interfaces are listed (and don't exist) on /etc/network/interfaces.

Another thing is that your ifconfig shows a nic with address 192.168.1.11 but is assigned to device eth1, not eth0, the one referenced by your interfaces as dhcp. Don't know if that discrepancies are the cause, but can' t believe they help.

Try edit yout /etc/network/interfaces to simply:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp
``` 

Another thing is reduce the number of variable on your config till you find whats wrong. 
I suggest remove dhcp for now till you got connected and then try again with dhcp. 
In that case clean /etc/network/interfaces to:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
address 192.168.1.21  # or 192.168.1.11 if 1.21 already exists
netmask 255.255.255.0
gateway 192.168.1.254
```

About the ipv6, that method, changing alias in not a good method and don't even work on Feisty anymore.
You just need to add it to modules blacklist. 
Do:
```
sudo sh -c "echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist"
```
and restart your computer, a simple network restart is not enough because kernel needs to boot without that module  (an "unloadable" one...)

hth

---

### Post by zenix on 2007-07-11
Ah, thank you Rui Pais! I will go ahead and try them (obviously not immediately, as I can go online and post ;) ) and report back. Thank you very much!

> 
About the ipv6, that method, changing alias in not a good method and don't even work on Feisty anymore.
Ah, well. Think there should have been some notification that doesn't work. Thank you again for the information. Fingers crossed and hope things work out!

**EDIT**
Ah, crud. Everything works, to a point. No internet at all, but I am now back online with the family LAN. Now, I could just use a HTTP proxy but alas, no luck. I was trying to make one on my own system for use of the other's but then my NIC card failed. Wonderful. Anyways, thank you for your time and answer. While you have helped me get things in working order to a point, I still can not connect through to the internet :(

Oh, nice avatar Rui :P

---

### Post by Rui Pais on 2007-07-11
> **zenix said:**
> 
**EDIT**
Ah, crud. Everything works, to a point. No internet at all, but I am now back online with the family LAN. Now, I could just use a HTTP proxy but alas, no luck. I was trying to make one on my own system for use of the other's but then my NIC card failed. Wonderful. Anyways, thank you for your time and answer. While you have helped me get things in working order to a point, I still can not connect through to the internet :(

Oh, nice avatar Rui :P

Oh... you know if you just edit your post, instead of make a new one, the forum will not notify users subscribed to that thread... 
I find your edit just because i keep thread tab open and restarted the browser (it's configured to restart with opened tabs from last session) :) 

So if you are on LAN, then the net card is now correctly configured. 

What do you use static or dynamic IPs?

Are you sure your gateway is 192.168.1.254?

Do you mind to check the output of:
```
cat /etc/resolv.conf
```
please?

Thanks in the name of the pingat (or is a cinguin?) i like both animals an get that one somewhere from the net... 
Later i discover the original site of it's author:
[http://www.humandescent.com/VersionNew/index3.shtml](http://www.humandescent.com/VersionNew/index3.shtml)
Not all images are that nice, but some are very funny
[ATTACH]37881[/ATTACH]

---

### Post by zenix on 2007-07-11
Ah! I got it to work!!! WHOO-HOO!

How? Well, if I could connect to my LAN, what could be blocking/preventing me from connecting to the world outside? Oh! Now I remember! I installed a firewall! So, shut it down, and hey! Look at that! I'm not unable to access the internet!

Ah, thank you Rui Pais, thank you so much!

P.S. I think that was the source of the problem then I just screwed it up in my attempts to "fix" the network before coming here. ](*,) :lolflag: 

P.S.S. Do you know of any good firewall configuration utilities for KDE? I'd love to hear them!

---

### Post by Rui Pais on 2007-07-12
Glad its working :)

Well i don't know much of firewalls... my only try to use one was disastrous. And now i got internet with a ADSL router that come with its own firewall already configured and running. 

But if i understand correctly your computer is in a local network and connect trough some gateway. 
So, i think - i may be wrong here, the only point that may need a firewall is the gateway that should be the only contact with outside. 
Ubuntu come with all ports close for security so there should be safe without extra effort from the user...

Anyway, usually people i read that use firewalls, use firestarter. It's one of most mentioned apps for manage firewalls, but it's gtk. 
There is a kde equivalent, called guarddog, but i don't read much about it, don't if it's good or easy to use. 

Maybe searching at synaptic or ask in kubuntu forum...

Best of luck :)

---

