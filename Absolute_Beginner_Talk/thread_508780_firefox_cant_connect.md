---
title: "firefox cant connect"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Fangus on 2007-07-24
hi i cant connect to the Internet via firefox, my network icon says data is being sent/recieved however it says page cant be displayed for every site i try. im running feisty fawn thanks  :)

---

### Post by Cypher on 2007-07-24
Open a terminal by going to Applications->Accessories->Terminal and type
```

ipconfig -a
cat /etc/resolv.conf
ping google.com

```
Show us the output..

---

### Post by Fangus on 2007-07-24
it says that ipconfig -a is an invalid code :confused: :(
edit: i mean command not found

---

### Post by coffeecat on 2007-07-24
ipconfig -a is a typo. Try 'ifconfig -a'. By the way, Cypher suggested three commands, so there will be three sets of output to post.

---

### Post by Fangus on 2007-07-24
packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet6 addr: fe80::218:deff:fe36:6d0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212 errors:307 dropped:334 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54938 (53.6 KiB)  TX bytes:18368 (17.9 KiB)
          Interrupt:17 Base address:0x6000 Memory:64100000-64100fff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet addr:169.254.4.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x6000 Memory:64100000-64100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5912 (5.7 KiB)  TX bytes:5912 (5.7 KiB)


bash: /usr/share/ubuntu-docs/ubuntu/sample/resolv.conf: Permission denied

ping: unknown host [http://www.google.com](http://www.google.com)



i dont know why permission is denied as i am the administrator

---

### Post by coffeecat on 2007-07-24
> **Fangus said:**
> bash: /usr/share/ubuntu-docs/ubuntu/sample/resolv.conf: Permission denied

ping: unknown host [http://www.google.com](http://www.google.com)

i dont know why permission is denied as i am the administrator


Try:

```
sudo cat /etc/resolv.conf
```You will be prompted for your password.

Now that you've discovered that pinging [www.google.com]("http://www.google.com") fails, try:

```
ping 64.233.183.103
```That's the IP address of Google - or it was when I tried it. :wink:

If that works, search the forum for how to disable IPv6 in firefox. A long shot, but it's worth a try.

It's late here in the UK so I'm going to bed now - I won't be able to respond again for some hours. In the meantime, post some details of how you connect to the internet. Dial-up, adsl or cable or something else? Type of modem? Do you have an ethernet router? That sort of thing. It might be relevant.

---

### Post by Fangus on 2007-07-24
> **coffeecat said:**
> Try:

```
sudo cat /etc/resolv.conf
```You will be prompted for your password.

Now that you've discovered that pinging [www.google.com]("http://www.google.com") fails, try:

```
ping 64.233.183.103
```That's the IP address of Google - or it was when I tried it. :wink:

If that works, search the forum for how to disable IPv6 in firefox. A long shot, but it's worth a try.

It's late here in the UK so I'm going to bed now - I won't be able to respond again for some hours. In the meantime, post some details of how you connect to the internet. Dial-up, adsl or cable or something else? Type of modem? Do you have an ethernet router? That sort of thing. It might be relevant.

is it to late for a 14 year old geek to fix his internetz i think not!
edit:i dont understand this ```
sudo cat /etc/resolv.conf
``` udo cat? im connecting via a netgear wireless router

---

### Post by coffeecat on 2007-07-25
> **Fangus said:**
> is it to late for a 14 year old geek to fix his internetz i think not!

The impatience of youth these days! With his whole life before him, he wants everything fixed yesterday, if not before. :roll: :wink:

**Fangus**, I just stopped by originally to help out briefly because an earlier poster had already made some good suggestions but had made a typing error. I was hoping that other members might help as well - they usually do. That they haven't may be because of your impatience, or it may be because you haven't tried a couple of things I suggested - or at least you haven't mentioned this.

In case you are still following this thread, let me respond again.

> **Fangus said:**
> i dont understand this ```
sudo cat /etc/resolv.conf
``` udo cat?

What don't you understand? Just open a terminal, type:

```
sudo cat /etc/resolv.conf
``` and post the output. It's sudo, not udo, by the way.

Explanation: /etc/resolv.conf contains details of your nameservers. If there's something wrong in this file it will explain your problem. This is why Cypher suggested this. The command cat simply outputs the contents of a file to the terminal, but since /etc/resolv.conf is owned by root you need root privileges to be able to 'cat' it. The command 'sudo' gives you temporary root privileges. [Read this]("https://help.ubuntu.com/community/RootSudo") to understand what I mean. No - I really do mean **read** it. You're going to need to understand sudo and the root account if you want to use Linux. Consider it your homework for this evening. :wink:

Did you:

```
ping 64.233.183.103
```as I suggested? If you can ping an IP 4-number address you have internet connectivity, but if you can't ping a human-readable IP address (which you have established you can't) then you have a nameserver resolving problem.

Did you look up how to disable IPv6 in Firefox? I could have told you how to do it but you will learn more if you search for yourself. :wink: IPv6 issues can lead to precisely what you are experiencing which is why it's worth trying. However,

> **Fangus said:**
>  im connecting via a netgear wireless router

IPv6 problems are usually down to old/badly-written firmware in the router. I believe Netgear is one of the good guys here, but it's still worth checking.

---

### Post by Cypher on 2007-07-25
Sorry for the typo..that's what happens when I switch between Windows and Linux..:) 

Now as far as IP addresses go, 169.254.4.103 is usually not a good one. That class of addresses is used in, Windows atleast, when you've setup for DHCP and the DHCP server can't give you a real IP address. Instead of reverting to an invalid IP address that might cause issues, a 169.254.x.x address is used.

If you have the GUI running, then go to System->Adminstration->Network, it will prompt you for your password. You should now have a "Wired Connection" and maybe a "Modem Connection". Click on the "Wired Connection" and then choose Properties. What info is in there???

---

### Post by coffeecat on 2007-07-25
> **Cypher said:**
> Sorry for the typo..that's what happens when I switch between Windows and Linux..:) 

I thought I recognised where that ipconfig came from. :D

> **Cypher said:**
>  Now as far as IP addresses go, 169.254.4.103 is usually not a good one. That class of addresses is used in, Windows atleast, when you've setup for DHCP and the DHCP server can't give you a real IP address. Instead of reverting to an invalid IP address that might cause issues, a 169.254.x.x address is used.

**Cypher**, a question. I noticed the 169.254.4.103 IP address and found it odd but let it pass until the OP had given some more information. Thanks for the explanation, by the way. However - the OP got that IP address from ifconfig in Linux. He says he's using a Netgear router. I've just had a quick look on the UK Netgear webpage and for the latest wireless modem-router, the router takes the address 192.168.0.1, so I would have thought it would allocate addresses in the 192.168.0.x range. And if not, I thought home routers used only the 192.168.x.x. and 10.0.0.x ranges.

If his Ubuntu box hasn't connected to the router and been allocated an IP address by it, ifconfig should have shown no address. Or am I missing something? Any thoughts? :?

---

### Post by Cypher on 2007-07-25
Most routers are configured for the 192.168.x.x address range. My linksys defaults to 192.168.1.x. So you're right that as long as the Router is functioning, it should have given an IP address in that range. I don't know if the DHCP client software in Linux has followed the same scheme of Windows and now uses the bogus 169.254.x.x address range when the DHCP server is misbehaving.

If a particular Ethernet interface is set to DHCP, then the dhclient software runs constantly to, first, get the IP address and then to continually renew it once it figures out what the expiration period of that IP address is. So since it's always running, it can't use a value of 0.0.0.0 or something which is a bad address..

Anyway..we need more info from the OP before we can provide any help..

---

### Post by Fangus on 2007-07-26
> **coffeecat said:**
> The impatience of youth these days! With his whole life before him, he wants everything fixed yesterday, if not before. :roll: :wink:

**Fangus**, I just stopped by originally to help out briefly because an earlier poster had already made some good suggestions but had made a typing error. I was hoping that other members might help as well - they usually do. That they haven't may be because of your impatience, or it may be because you haven't tried a couple of things I suggested - or at least you haven't mentioned this.

In case you are still following this thread, let me respond again.



What don't you understand? Just open a terminal, type:

```
sudo cat /etc/resolv.conf
``` and post the output. It's sudo, not udo, by the way.

Explanation: /etc/resolv.conf contains details of your nameservers. If there's something wrong in this file it will explain your problem. This is why Cypher suggested this. The command cat simply outputs the contents of a file to the terminal, but since /etc/resolv.conf is owned by root you need root privileges to be able to 'cat' it. The command 'sudo' gives you temporary root privileges. [Read this]("https://help.ubuntu.com/community/RootSudo") to understand what I mean. No - I really do mean **read** it. You're going to need to understand sudo and the root account if you want to use Linux. Consider it your homework for this evening. :wink:

Did you:

```
ping 64.233.183.103
```as I suggested? If you can ping an IP 4-number address you have internet connectivity, but if you can't ping a human-readable IP address (which you have established you can't) then you have a nameserver resolving problem.

Did you look up how to disable IPv6 in Firefox? I could have told you how to do it but you will learn more if you search for yourself. :wink: IPv6 issues can lead to precisely what you are experiencing which is why it's worth trying. However,



IPv6 problems are usually down to old/badly-written firmware in the router. I believe Netgear is one of the good guys here, but it's still worth checking.

yeah i had already disabled ipv6 a while ago before this thread, i shouldve mention. ipv6 should work as it was working when i had vista *shudders* I thought sudo cat was a location not a command! Silly me!


search com
nameserver 204.11.126.131
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 208.185.179.218
 

PING 64.223.183.103 (64.223.183.103) 56(84) bytes of data.
From 169.254.4.103 icmp_seq=1 Destination Host Unreachable
and it did that^ until i stopped the terminal  ](*,)

---

### Post by coffeecat on 2007-07-26
> **Fangus said:**
> 
PING 64.223.183.103 (64.223.183.103) 56(84) bytes of data.
From 169.254.4.103 icmp_seq=1 Destination Host Unreachable
and it did that^ until i stopped the terminal  ](*,)

I'm afraid we can put that down to google being awkward. I've just tried that myself and got no response. 64.223.183.103 is the address that was returned the other day when I did a 'ping www.google.com'. So I pinged google.com just now and this time got:

> $ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (66.249.93.104): 56 data bytes
64 bytes from 66.249.93.104: icmp_seq=0 ttl=247 time=39.940 ms
64 bytes from 66.249.93.104: icmp_seq=1 ttl=247 time=40.275 ms
64 bytes from 66.249.93.104: icmp_seq=2 ttl=247 time=39.202 ms
64 bytes from 66.249.93.104: icmp_seq=3 ttl=247 time=39.093 ms
64 bytes from 66.249.93.104: icmp_seq=4 ttl=247 time=39.250 ms
64 bytes from 66.249.93.104: icmp_seq=5 ttl=247 time=39.634 ms
^C
--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
6 packets transmitted, 6 packets received, 0% packet lossHo hum. :( Seems like the IP address changes from day to day. You'll have to ping Google (or whatever site you like) in Windows (you can use the same command at a command prompt) or from an Apple Mac, write down the IP address and then try that.

But first - we need to see if Ubuntu and your Netgear router are talking to each other properly. Have you read the chat between Cypher and myself? We're puzzled by the host IP address you've got.

Try pinging your router. That'll be either 192.168.1.1 or 192.168.0.1. And have you checked the GUI networking configuration as Cypher suggested in an earlier post?

---

### Post by Fangus on 2007-07-26
there not working  :( it still says Destination Host Unreachable
my wired connection is disabled and on dhcp, my wireless data is correct, roaming mode isnt enabled (i tried enabling that) and the connection settings are on automatic configuration dhcp

---

### Post by coffeecat on 2007-07-27
Now he tells us he's using wireless. ](*,) :( :wink:

OK, I know you said you had a wireless router but most posters with internet connection problems who use wireless usually say they are up front. It wasn't clear. :)

**Fangus**, we're dealing with a lot of variables here and it's difficult to see where your problem lies. Depending on your wireless chipset, the problem may lie with your wireless connection to the router. Can you connect your box to the router with an ethernet cable temporarily just to see if you can get internet connection? If you can connect to the internet with a wired connection, then the problem does lie with the wireless connection and you need to post much more information about your wireless hardware, and whether or not you are using encryption and, if so, which type.

---

### Post by Fangus on 2007-07-27
no that didnt work

---

### Post by Fangus on 2007-07-28
still not working. any more ideas? thanks

---

### Post by Fangus on 2007-08-02
has everyone given up on this thread? should i just ask a mod?

---

### Post by RomeReactor on 2007-08-02
Hi. Please post the output of the following commands, so people here can take a look at them and help you diagnose the problem, as your wireless card may need appropriate drivers:
```
lspci | grep Ethernet
```
```
sudo lshw -class network
```
In the output of this last command, look for "description: Wireless interface" and see what its "logical name" is; it may be **eth0, eth1, wlan0, ra0**, etc., depending of your card's chipset. Then use that name in the following command:
```
iwlist **logical name** scan
```
and post the output. Let's say the logical name it gave you was **wlan0**; then you would enter:
```
iwlist wlan0 scan
```

---

### Post by asmoore82 on 2007-08-02
wow, this line of thinking is getting too complex

we can see from the output of your 'ifconfig' that your computer has
been unable to get a DHCP address from your router.

unplug/re-plug the POWER to your router and make sure the lights come on
to indicate that the ethernet cord is plugged in right, then ...

```
~ $ sudo ifconfig eth1 down
~ $ sudo ifconfig eth1 up
```

wait a few minutes and check ifconfig -a again for the existance of a plain IPv4 address ...
```
~ $ ifconfig | grep inet | head -n 1
```
until this shows a simple address like 192.168. ... 
it is pointless to attempt to ping anything

---

### Post by Fangus on 2007-08-02
> **RomeReactor said:**
> Hi. Please post the output of the following commands, so people here can take a look at them and help you diagnose the problem, as your wireless card may need appropriate drivers:
```
lspci | grep Ethernet
```
```
sudo lshw -class network
```
In the output of this last command, look for "description: Wireless interface" and see what its "logical name" is; it may be **eth0, eth1, wlan0, ra0**, etc., depending of your card's chipset. Then use that name in the following command:
```
iwlist **logical name** scan
```
and post the output. Let's say the logical name it gave you was **wlan0**; then you would enter:
```
iwlist wlan0 scan
```
04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:36:6d:0c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:64100000-64100fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@04:04.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:9f:0d:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:2000-20ff iomemory:63000000-630000ff irq:21


eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:B5:EC:50
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-49 dBm  Noise level=-49 dBm
                    Extra: Last beacon: 12ms ago

i'm currently waiting that few minutes till re-entering ifconfig-a

---

### Post by Fangus on 2007-08-02
when i entered this ```
  ifconfig | grep inet | head -n 1 
``` it said invalid number of lines.

---

### Post by Raineer on 2007-08-02
Try without the space between the 'n' and the 1, I believe proper syntax has no space there.

---

### Post by asmoore82 on 2007-08-02
the space is either/or on modern systems;

but that is a <number 1> not a <lowercase L>

---

### Post by Fangus on 2007-08-02
that gave me a stupid addresss, what should i do?

---

### Post by asmoore82 on 2007-08-02
Check to see if the problem is fixed
if not; post the output of
```
ifconfig -a
```
again

---

### Post by Fangus on 2007-08-02
net out? I dont follow

---

### Post by asmoore82 on 2007-08-02
bump ^edited

---

### Post by Fangus on 2007-08-02
eth0      Link encap:Ethernet  HWaddr 00:40:D0:9F:0D:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet6 addr: fe80::218:deff:fe36:6d0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:2 dropped:2 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44 (44.0 b)  TX bytes:6493 (6.3 KiB)
          Interrupt:17 Base address:0xe000 Memory:64100000-64100fff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet addr:169.254.4.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 Memory:64100000-64100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

---

### Post by asmoore82 on 2007-08-02
ahh, you have two network cards?

now bring #0 down and back up

```
~ $ sudo ifconfig eth0 down
~ $ sudo ifconfig eth0 up
```

---

### Post by Fangus on 2007-08-03
> **asmoore82 said:**
> ahh, you have two network cards?

now bring #0 down and back up

```
~ $ sudo ifconfig eth0 down
~ $ sudo ifconfig eth0 up
```

I do? wow! :biggrin:

---

### Post by Fangus on 2007-08-03
what now?

---

### Post by Fangus on 2007-08-03
bump

---

### Post by asmoore82 on 2007-08-03
is it working => if not; ifconfig -a again

---

### Post by Fangus on 2007-08-04
didnt work tried it 3 times should i keep trying?

---

### Post by Fangus on 2007-08-05
bump

---

### Post by Jenda on 2007-08-05
> **Fangus said:**
> has everyone given up on this thread? should i just ask a mod?

Don't ask mods. It makes them grumpy. See? I'm now grumpy.
Mods are here to ensure that the forums run smoothly, not to know everything. I, for one, have absolutely no clue about wireless, and prefer my good old ethernet cable.

Everyone else in the thread has been very patient - you should try some of that too :)

---

### Post by Fangus on 2007-08-08
re-bump

---

### Post by nichipet on 2007-08-08
I'll need to reread the thread, which I won't have time for until this afternoon when I'm home. Maybe you could add a new post on here (besides "re-bump") that catches us up on where it stands now so we don't have to read all four pages.

---

### Post by Fangus on 2007-08-08
> **Cypher said:**
> Open a terminal by going to Applications->Accessories->Terminal and type
```

ifconfig -a
cat /etc/resolv.conf
ping google.com

```
Show us the output..

the output was

> **Fangus said:**
> packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet6 addr: fe80::218:deff:fe36:6d0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212 errors:307 dropped:334 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54938 (53.6 KiB)  TX bytes:18368 (17.9 KiB)
          Interrupt:17 Base address:0x6000 Memory:64100000-64100fff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet addr:169.254.4.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x6000 Memory:64100000-64100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5912 (5.7 KiB)  TX bytes:5912 (5.7 KiB)


bash: /usr/share/ubuntu-docs/ubuntu/sample/resolv.conf: Permission denied

ping: unknown host [http://www.google.com](http://www.google.com)



i dont know why permission is denied as i am the administrator


> **coffeecat said:**
> Try:

```
sudo cat /etc/resolv.conf
```You will be prompted for your password.

Now that you've discovered that pinging [www.google.com]("http://www.google.com") fails, try:

```
ping 64.233.183.103
```That's the IP address of Google - or it was when I tried it. :wink: 

> **Fangus said:**
> 
search com
nameserver 204.11.126.131
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 208.185.179.218
 

PING 64.223.183.103 (64.223.183.103) 56(84) bytes of data.
From 169.254.4.103 icmp_seq=1 Destination Host Unreachable
and it did that^ until i stopped the terminal  ](*,)

then

> **RomeReactor said:**
> Hi. Please post the output of the following commands, so people here can take a look at them and help you diagnose the problem, as your wireless card may need appropriate drivers:
```
lspci | grep Ethernet
```
```
sudo lshw -class network
```
In the output of this last command, look for "description: Wireless interface" and see what its "logical name" is; it may be **eth0, eth1, wlan0, ra0**, etc., depending of your card's chipset. Then use that name in the following command:
```
iwlist **logical name** scan
```
and post the output. Let's say the logical name it gave you was **wlan0**; then you would enter:
```
iwlist wlan0 scan
```

then

then

> **Fangus said:**
> 04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:36:6d:0c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:64100000-64100fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@04:04.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:9f:0d:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:2000-20ff iomemory:63000000-630000ff irq:21


eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:B5:EC:50
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-49 dBm  Noise level=-49 dBm
                    Extra: Last beacon: 12ms ago





> **asmoore82 said:**
> wow, this line of thinking is getting too complex

we can see from the output of your 'ifconfig' that your computer has
been unable to get a DHCP address from your router.

unplug/re-plug the POWER to your router and make sure the lights come on
to indicate that the ethernet cord is plugged in right, then ...

```
~ $ sudo ifconfig eth1 down
~ $ sudo ifconfig eth1 up
```

wait a few minutes and check ifconfig -a again for the existance of a plain IPv4 address ...
```
~ $ ifconfig | grep inet | head -n 1
```
until this shows a simple address like 192.168. ... 
it is pointless to attempt to ping anything

> **Fangus said:**
> that gave me a stupid addresss, what should i do?


then

OTE=asmoore82;3122471]Check to see if the problem is fixed
if not; post the output of
```
ifconfig -a
```
again[/QUOTE]

> **Fangus said:**
> eth0      Link encap:Ethernet  HWaddr 00:40:D0:9F:0D:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet6 addr: fe80::218:deff:fe36:6d0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:2 dropped:2 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44 (44.0 b)  TX bytes:6493 (6.3 KiB)
          Interrupt:17 Base address:0xe000 Memory:64100000-64100fff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:36:6D:0C  
          inet addr:169.254.4.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 Memory:64100000-64100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)


then

> **asmoore82 said:**
> ahh, you have two network cards?

now bring #0 down and back up

```
~ $ sudo ifconfig eth0 down
~ $ sudo ifconfig eth0 up
```

i re-tried that a few times. any moar ideas

---

### Post by Fangus on 2007-08-13
re-bump

---

### Post by RomeReactor on 2007-08-13
Try this:
```
sudo dhclient eth1
```
and see if you can use Firefox now. If that doesn't work, try taking off the encryption on your router--at least while you sort this out--and use the command above again. Also, I think your eth1 card should be set to **managed** mode instead of **master** by entering this in the terminal:
```
sudo iwconfig eth1 mode Managed
```
or by editing the /etc/network/nterfaces file:
```
gksudo gedit /etc/network/interfaces
```
then look for the **eth1** entry and add:
```
wireless-mode managed
```
below **auto eth1** and **iface eth1 inet dhcp**.

---

### Post by Fangus on 2007-08-14
how do i set it so it doesnt ask for a password in ubuntu?

---

### Post by Fangus on 2007-08-14
didnt work :(

---

### Post by RomeReactor on 2007-08-14
> **Fangus said:**
> how do i set it so it doesnt ask for a password in ubuntu?

It's a security feature. I would advise you to **not** disable it.

---

### Post by RomeReactor on 2007-08-14
Seeing as you've been very patient with this thread, I really feel bad about not being able to help you further; I have no practical experience with your wireless card, so I can't assure you it's working correctly. Since this thread is going very slow, I suggest you also post on the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=136") section; try a title like, "Intel PRO Wireless 3945ABG can't connect to the internet" or something similar. Keep an eye out for this thread also, as someone might be able to help you further.

---

### Post by Fangus on 2007-08-15
> **RomeReactor said:**
> It's a security feature. I would advise you to **not** disable it.

i mean in the networking panel thing.

---

