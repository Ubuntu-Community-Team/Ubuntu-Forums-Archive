---
title: "Problems with Railink wireless network"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-04-03
This is a continuation of an earlier thread that was hijacked. It contains additional diagnostic material, all copy/pasted from my (still offline) laptop.

I am trying to add a Dell Latitude laptop equipped with a Belkin F5D7010 wireless card to an existing ad-hoc wireless network (ESSID = Hoffnet) WEP-encrypted, which consists of two XP machines both equipped with D-Link DWL-520 wireless PCI adapters. I have activated the rao device, but no lights appear on the card and no internet connection can be made.

The relevant diagnostics so far are:
```

steve@laptop:~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"Hoffnet"  Nickname:"Hoffnet"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-69 dBm  Noise level:-209 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
steve@laptop:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:11:50:90:55:3C
          inet6 addr: fe80::211:50ff:fe90:553c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:21483935 (20.4 MiB)
          Interrupt:11 Base address:0x4000
```

```
steve@laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
steve@laptop:~$
```

Any suggestions on what I should do to get this laptop onto my wireless network would be greatly appreciated.

---

### Post by htinn on 2006-04-03
It looks to me like you just need to set the key. Maybe you have entered wrong. Check the /etc/network/interfaces file and make sure your key looks right. (i.e. something like this: iwconfig ra0 key 1234567812

---

### Post by SteveHoffmanUK on 2006-04-03
Thanks for the reply.

I have rechecked the key (26 char) in /etc/network/interfaces as you suggest and it is correct.

Any more suggestions?

I have set up the network myself in Windows XP, but some of the terminology here isn't the same, or at least I don't recognise it. For example, in activating ra0, I had to chose between DHCP or Static IP address. I chose DHCP without really knowing whether that's correct or not. Is there anything I can check in XP to confirm that?

---

### Post by NetworkNed on 2006-04-03
[QUOTE=SteveHoffmanUK]
```
steve@laptop:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:11:50:90:55:3C
          inet6 addr: fe80::211:50ff:fe90:553c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:21483935 (20.4 MiB)
          Interrupt:11 Base address:0x4000
```

```
steve@laptop:~$ sudo dhclient eth0
....sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

```
[/QUOTE]
Sorry if my posting in your previous thread misled you. Have you tried (with rootlike powers) `dhclient ra0`?

Ned.

---

### Post by SteveHoffmanUK on 2006-04-04
NetworkNed wrote:
> Sorry if my posting in your previous thread misled you. Have you tried (with rootlike powers) `dhclient ra0`?

```
steve@laptop:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:11:50:90:55:3c
Sending on   LPF/ra0/00:11:50:90:55:3c
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
steve@laptop:~$

```

---

### Post by tuxinvader on 2006-04-04
I setup a ralink on my parents ubuntu box, but it was a while ago.

Why aren't you using the gui config tool? It's in the ra2400/ra2500 packages. And it will be called RaConfig2400/Raconfig2500. More importantly why aren't you using WPA? WEP is about as secure as my grandmothers dentures when she's using a jackhammer!

---

### Post by SteveHoffmanUK on 2006-04-04
tuxinvader wrote:
> Why aren't you using the gui config tool? It's in the ra2400/ra2500 packages. And it will be called RaConfig2400/Raconfig2500.

Because the advice so far is coming from people who prefer to use Terminal commands, so I try to cooperate with them. I have nothing against GUI (indeed, would prefer it) but, remember, you're in Absolute Beginner Talk forum. How do I find these packages? I went to Applications, Add Application and searched for RAconfig but found nothing. I'm sure that's not the way to do it, but maybe you could spell out the steps for me (BEGINNER remember) to follow?

As for using grandma's-dentures-like WEP instead of WPA, until a few weeks ago my wireless was completely unencrypted, so I'm at least trying! At this point I prefer not to mess about with my XP-based network, which has the virtue of actually working. When I get my Ubuntu laptop wireless working, then I can consider changing to WPA, but first things first and let's just change one variable at a time.
 
Thanks for responding; I do appreciate it.

---

### Post by htinn on 2006-04-04
Another problem with the GUI is that they *assume* you are in a managed network, which is not the case here. You need to edit your interfaces directly if you want to get an ad-hoc mode network going. First, you need to make sure you can get the auth working. :)

---

### Post by SteveHoffmanUK on 2006-04-04
The Auth? Don't understand, or is that just a Linux joke?:confused:

---

### Post by SteveHoffmanUK on 2006-04-04
The Belkin wireless network card is supposed to run in Linux "out of the box", yet I don't seem to have made much progress in getting it to work, in spite of help from forum members. I have to conclude that it may be a problem with my particular laptop.

When I first installed Breezy, it hung at "Starting hotplug subsystem" and wouldn't get beyond that point. Searching the forums I found a suggestion that when I reached that point I should key Ctl+C, which effectively cancels this particular load. This did indeed work for me, in that I got to load Breezy, but from then on, whenever I booted, the hotplug subsystem was never loaded. Reading elsewhere, I conclude that this would affect the system's networking functions. 

In another thread, someone commented that he also had this problem but found that it didn't happen with Dapper, so that is my next move -- am downloading Dapper now. If I succeed in booting Dapper without this hang, then I will see whether this also will allow me to get the wireless network working.

---

### Post by htinn on 2006-04-04
The reason your network isn't working "out of the box" is because you are setting up in ad-hoc mode. The user interfaces in Ubuntu are not that thorough. I think you'll likely have the exact same issues in Dapper.

Please bear in mind that ad-hoc mode requires some interaction on both sides of the network (server and client).

---

### Post by SteveHoffmanUK on 2006-04-04
[QUOTE=htinn]The reason your network isn't working "out of the box" is because you are setting up in ad-hoc mode. The user interfaces in Ubuntu are not that thorough. I think you'll likely have the exact same issues in Dapper.

Please bear in mind that ad-hoc mode requires some interaction on both sides of the network (server and client).[/QUOTE]
Are you saying, therefore, that I need to change my network to a managed one?

---

### Post by htinn on 2006-04-04
It's your choice, really. Managed mode is a bit more expensive, but it's a lot easier to set up.

---

### Post by SteveHoffmanUK on 2006-04-05
[QUOTE=htinn]It's your choice, really. Managed mode is a bit more expensive, but it's a lot easier to set up.[/QUOTE]

"Time is money"-- Benjamin Franklin
My cost benefit analysis says that if I buy a wireless broadband router I will be "quids in" as they say in these parts (dollars ahead?). 

Question: Presumably the router setup means that I will have a managed network? 

It will also bring other gains, for example, it will mean that I won't have to have my main PC switched on in order for the other machine(s) on the network to share the internet connection. Also I can move it around the house to maximise signal strength.

---

### Post by NetworkNed on 2006-04-06
Ok... sorry I haven't been keeping up with this thread - I just realised I forgot to tick the "subscribe" box when I last posted.

[QUOTE=SteveHoffmanUK]```
steve@laptop:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:11:50:90:55:3c
Sending on   LPF/ra0/00:11:50:90:55:3c
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
steve@laptop:~$

```[/QUOTE]
Ok... so you're not getting an IP address issued to you. This could be because the other PC is not issuing one or because you're not connected to the network at the wireless level (SSID, WEP &c).

Can you try:
```
# iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet enc aaaaaaaaaa
# ifconfig ra0 192.168.0.42
# ifconfig ra0 up
# ifconfig ra0
# ping 192.168.0.1

```

---

### Post by NetworkNed on 2006-04-06
[QUOTE=SteveHoffmanUK]...I have set up the network myself in Windows XP, but some of the terminology here isn't the same, or at least I don't recognise it. For example, in activating ra0, I had to chose between DHCP or Static IP address. I chose DHCP without really knowing whether that's correct or not. Is there anything I can check in XP to confirm that?[/QUOTE]
DHCP means "make a network request to see if there's a DHCP server out there which can give you an IP address".

In Windows XP if you have your TCP/IP properties set up to "assign IP address automatically" then it will try DHCP first; if it doesn't receive an IP address then it will use an address in the zeroconf reserved range (169.254.x.y). So if a Windows XP client connecting to this network receives an address in the 192.168.x.y range (you can check using `ipconfig` at a DOS prompt) then DHCP is the correct setting.

I believe that when you set-up connections like this with Windows' Internet Connection Sharing Wizard it enables a DHCP server on the machine that shares the internet and that if you run `ipconfig` on your gateway machine you'll find it has an address of 192.168.0.1

Ned.

---

### Post by NetworkNed on 2006-04-06
[QUOTE=SteveHoffmanUK]The Auth? Don't understand, or is that just a Linux joke?:confused:[/QUOTE]
Authentication. The most obvious interpretation of the problems you're demonstrating is that you're not managing the SSID or WEP authentication part of connecting to the network.

I think that it might be worth temporarily disabling encryption on this network just to prove the point that you haven't been unfortunate enough to get a card with a manufacturing fault.

I can't remember if `iwscan` works on this card (my bad), but it might be worth trying that. If you see your network as being detected then it would tend to indicate that your card is receiving network packets.

Ned.

---

### Post by NetworkNed on 2006-04-06
[QUOTE=SteveHoffmanUK]Question: Presumably the router setup means that I will have a managed network?[/QUOTE]
Yes. Assuming you're on ADSL then I recommend that DG834G. It's particularly easy to configure and does about everything a router should. I doubt if you'd get it cheaper than at [http://Broadbandbuyer.co.uk](http://Broadbandbuyer.co.uk)
[QUOTE=SteveHoffmanUK]It will also bring other gains, for example, it will mean that I won't have to have my main PC switched on in order for the other machine(s) on the network to share the internet connection.[/QUOTE]
Indeed.
[QUOTE=SteveHoffmanUK]Also I can move it around the house to maximise signal strength.[/QUOTE]
As long as you have phone sockets around the house into which you can plug it in. If you have a micro-filter in each phone socket then you should be able to use any one of them.

Ned.

---

### Post by SteveHoffmanUK on 2006-04-06
Ned wrote:
> Assuming you're on ADSL then I recommend that DG834G. It's particularly easy to configure and does about everything a router should. 


Too late! I have taken the plunge and ordered a Netgear DG834GT Integrated ADSL Modem and 108Mbps 802.11g Wireless Firewall Router from Ebuyer. I assume that this is what you are referring to? What's the "T" signify? This was recommended to me by my local PC engineer. The price seemed pretty good to me, and the device should be with me by next Tuesday.

In the light of that, I suggest we suspend any further attempts to get my ad-hoc WLAN working -- it's now no longer relevant.

I have four phone points scattered around the house, so I should be able to find some place where everyone can receive a good signal. It's a 150 year old building with some thick brick walls, some of which are now internal, and I have been having low-signal problems with my current setup. I hope the new router will improve the situation.

So I'll probably be back, but with a new set of problems.

BTW, I've had problems booting my Breezy on my laptop and have to cancel the loading hotplug services option (or something like that) during boot-up. Is this likely to screw up my network functions? There are threads here that cover this problem, and the easiest workaround is to cancel it, otherwise Breezy won't load. 

Thanks for all your help so far. I really appreciate it.

---

### Post by SteveHoffmanUK on 2006-04-11
I am pleased to report that I am sending this from my laptop, linked by wireless Belkin Railink card to my new Netgear DWHG834GT Integrated ADSL Modem and 108Mbps 802.11g Wireless Firewall Router. WHEE!:cool: 

Thanks especially to Ned and others who helped me. I feel like Samuel F B Morse and his first telegram ("What hath God wrought").  Lessons learned:
1. Don't try to implement ad-hoc wireless networks in Ubuntu, or only do so if you want some real challenges. I didn't, thanks.
2. When buying new kit, make sure it's Linux-friendly (but that's so obvious it's not worth saying, really).

I have now also implemented dual-boot Ubuntu on my PC. It's not been without its problems, and there are several aspects of it that still seem pretty dodgy to me, but now that I've got it loaded, I have been impressed by its trouble-free, "out-of-the-box' handling of:
1. My Epson Perfection 1260 scanner
2. My Canon S750 inkjet printer
3. My USB Olympus digital camera downloading.

Well done, Ubuntu team! Keep up the good work.

---

