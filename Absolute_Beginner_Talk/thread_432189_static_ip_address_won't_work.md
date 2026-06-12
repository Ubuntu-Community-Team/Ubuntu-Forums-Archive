---
title: "static ip address won't work"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by noob12345 on 2007-05-03
I'm trying to set up static ip address so I use port forwarding with my Netgear MR314 router

I used Networking to configure my usb adapter to set it up, but when I try to set it from DHCP to static, it just won't work (no internet connection)

I tried 
Ip address: 192.168.0.136;  subnet mask: 255.255.255.0; and gateway address: 192.168.0.1 

those are what i got from portfoward.com
i also tried different ip addresses

here is the ifconfig information:

owner@owner-desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4235218 (4.0 MiB)  TX bytes:4235218 (4.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:90:A1:A8
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe90:a1a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:469110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:329422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:561604169 (535.5 MiB)  TX bytes:30670833 (29.2 MiB)



thanks for any help

by the way, has anyone heard of a bug in Azureus that displays the router/firewall warning, and just doesn't go away, blocking workspace switching?

---

### Post by louieb on 2007-05-03
I setup  my Netgear router to look at the mac address and assign it the same ip every time. Works for wired connections. Results are the same. But it doesn't seem to work for wireless connections.

---

### Post by e_james on 2007-05-03
I have found that when you use static IP addresses you sometimes need to provide DNS addresses as well as the gateway. Try pinging a suitable IP address. If that works and web pages don't then it looks like dns is the problem. I usually include the gateway address as one of the dns addresses.

---

### Post by wirelessmonkey on 2007-05-03
You probably have the wrong gateway set... your gateway should be the IP address of your router. You should also probably set DNS as your router as well, unless you use an outside DNS server.

---

### Post by noob12345 on 2007-05-04
how do I provide a DNS address?
I'm pretty sure my gateway address is that of my router address (when typed in to address bar on firefox, it will bring me to the configurations page)
how do I ping an ip address?
the settings worked when I was using windows (but I can't be certain about that)

---

### Post by zvacet on 2007-05-04
If you don´t know yours you can use this 208.67.222 & 208.67.220.220 .They are from

[http://www.opendns.com/start/]("http://www.opendns.com/start/")

After you put nameservers in DNS tab and close it type in terminal

```
pppoeconf
```

---

### Post by e_james on 2007-05-04
noob12345

If your Netgear router works in a similar way to mine, it logs on automatically to your ISP. Assuming this works correctly, the router status page should list the DNS addresses it has obtained from the ISP.

If you can connect to the router configuration using static ip, it would seem that the ethernet is functioning as required.

One way to ping an IP address is via System / Administration / Network tools. There is a "ping" tab. Conveniently it will remember the address you type for repeated tests.

zvacet

Thanks for the "pppoeconf". I didn't know that.

---

### Post by noob12345 on 2007-05-05
i tried adding 208.67.220.220 (zvacet), and added 192.198.0.1 (router address) to DNS (my question earlier about DNS acually meant how do i set it, since i didn't see the tab there)

then set to static ip address, it didn't work

then i closed Networking and typed "pppoeconf" in terminal (zvacet)
it told me i may have serious connection issues

was i suppose to add DNS, close, type pppoeconf in terminal, open Networking, then set static ip?
i didn't get to try that because, for apparently no reason, my keyboard stop responding. Is that just a bug that should be fixed in later releases of Ubuntu? (I'm still using Dapper because of the long install time)

---

### Post by e_james on 2007-05-05
My expertise is very limited here. In the past few weeks I have attempted internet connections from linux about 6 times and been successful with 3 of them. I haven't given up on the others yet.

What version of ubuntu are you using? The network setup changes a little with the versions.
Did the ping test work? (i.e. did you get several responses?)
I think you said earlier that you can access the router configuration using linux. Is that correct?

---

### Post by noob12345 on 2007-05-07
I am using Dapper
I pinged 192.168.0.1 with DHCP settings, and got back all five requests
then went into network settings, set it to static. ping results look pretty much the same
I read somewhere this means it's a DNS problem
then i added 192.168.0.1 (gateway) to DNS, pressed ok, my connection was gone and when i opened Networking again, the DNS I added was still there, but my network connection wasn't. 
the led on my adapter was off too. when i start up my computer, i have to activate that through terminal, so i did that. I tried setting to static ip address, pinged, exact same results

Help? Do i have to put another DNS, or something? 
And what does pppoeconf do? Was that necessary after DNS changes?

---

### Post by jimrz on 2007-05-07
> **noob12345 said:**
> I am using Dapper
I pinged 192.168.0.1 with DHCP settings, and got back all five requests
then went into network settings, set it to static. ping results look pretty much the same
I read somewhere this means it's a DNS problem
then i added 192.168.0.1 (gateway) to DNS, pressed ok, my connection was gone and when i opened Networking again, the DNS I added was still there, but my network connection wasn't. 
the led on my adapter was off too. when i start up my computer, i have to activate that through terminal, so i did that. I tried setting to static ip address, pinged, exact same results

Help? Do i have to put another DNS, or something? 
And what does pppoeconf do? Was that necessary after DNS changes?

if you are using network-manager the static ip is not going to work. i use the method suggested above, and have the router "reserve" specific ip addresses for specific machines by name/mac address and it works quite well. mine is also a netgear. i even have 2 laptops set up in the router with 2 reserved addresses each (1 for wifi + 1 for wired) with no problem at all, even though those computer names are listed twice eachh has a unique mac for it to go by.

---

### Post by e_james on 2007-05-07
I spent 3 to 4 hours earlier today replacing Dapper with Feisty on the laptop I am now using. At this moment I am using Windows XP because I have work to do which I can't yet do with Ubuntu. The most immediate result of the Feisty install is that my built in Intel wireless adaptor now connects to my ADDON router where it wouldn't earlier today with Dapper. I have reason to believe that somehow this is partly to do with the behaviour of the router because I didn't have the same difficulty with a Netgear wireless adsl router. I did try pppoeconf on another laptop with Feisty and it seems to do nothing useful because it perceives some other software interfering with it. I think this may be the Network Manager (nm-applet) which seems to be new in Edgy and Feisty.

I asked if you can access your router configuration pages even though you can't get to the internet. What I am trying to do is to guess where the problem is and then maybe figure out a solution. If ping works then it appears that the hardware and the drivers are functioning, but ping is just one protocol. In order to configure the router I assume you do what I do and use your browser (Firefox?) to open a web page like [http://192.168.0.1](http://192.168.0.1). The significant point here is that no DNS is involved (in principle). To open a page like [http://ubuntuforums.org](http://ubuntuforums.org) your pc has to request a translation of the text into an IP address and that's what the DNS machine does. When you use DHCP your pc isn't just allocated an IP address, it's also told the gateway address and in some way I don't understand it's connected to the DNS service. I noticed a comment somewhere that the router does DNS forwarding which is what mine now seems to be doing with Feisty because the primary DNS listed is my router IP. In Windows at this moment I am using a static IP and the router is listed as the gateway but my ISP's DNS addresses are used for the DNS settings. 

I had a problem with Dapper. I was setting DNS addresses and it was "forgetting" them at the first opportunity. I got a tip from spd106 which helped. 

[http://ubuntuforums.org/showthread.php?t=388723](http://ubuntuforums.org/showthread.php?t=388723)

While I've been writing this, I see jimrz has made some useful comments.

---

