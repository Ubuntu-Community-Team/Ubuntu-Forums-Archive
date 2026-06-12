---
title: "Cable internet!!!???"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2007-06-13
Um this is pretty confusing...

I plug in my cable modem into the ethernet port and my computer says that I'm connected but then my browser won't connect to anything. I tried using pppoeconf but it didn't work....

Does anybody know what to do to get my Time Warner  Cable modem working????

---

### Post by violin on 2007-06-13
hi 
try system>administration>networking from there select wired connections select proporties fill the information and dont forget the fill dns. I managed to go net like that

hope this helps

---

### Post by Mazehero55 on 2007-06-13
I don't know what info to put in... or DNS stuff how do I?

Before I had dial-up that worked with wvdial, so I know nothing on how to do this...

---

### Post by violin on 2007-06-13
are using just ubuntu in your box or do you have windows. if you do then easy go to windows then select run then write cmd. in cmd write ipconfig you will get the information from there. Also on the terminal write ifconfig what is say?

---

### Post by Mazehero55 on 2007-06-13
I only have Ubuntu on my box, but I have a windows laptop from a friend that I've tested with the modem. 

I see if I can do that on it.

---

### Post by oilchangeguy on 2007-06-13
> **Mazehero55 said:**
> Um this is pretty confusing...

I plug in my cable modem into the ethernet port and my computer says that I'm connected but then my browser won't connect to anything. I tried using pppoeconf but it didn't work....

Does anybody know what to do to get my Time Warner  Cable modem working????

uh, have you reset the modem (unpluged it)? turn it off for about a minute, plug it back in and you should be able to get on line. and it won't hurt to reboot the computer when you restart the modem.

---

### Post by Mazehero55 on 2007-06-13
I put in ipconfig on this laptop and it gave me many addresses like the subnet mask and gateway I put them in but nothing happens, even worse now it says there is no connection at all. When before it said there was.

Also the DNS Suffix it gives is tx.rr.com  but the dns server thing only lets me put in ip addresses not text...

Also I tried to restart everything but it still does nothing

---

### Post by steveneddy on 2007-06-13
This may help.

I use wireless at home all the time on my laptop. When I went to my LUG meeting this last weekend, I plugged in to the LAN with a hard wire, but did this while the lappie was already on.

I wondered why it wouldn't hook up. I got home and tried the same thing. Same deal. wireless worked fine but no wired ethernet connection.

THEN - I restarted. I left the ethernet cable plugged in and lo and behold, I knew there was a cable plugged in and I could use the wired connection. If the cable is plugged in while booting, ethernet works like a charm.

Try plugging the cable in and restarting. That may help. Maybe not.

Good luck.

---

### Post by Mazehero55 on 2007-06-13
I tried restarting with the cable in, it's still a dud....

---

### Post by Mazehero55 on 2007-06-13
has anybody have any ideas

---

### Post by rscott5 on 2007-06-13
Try just setting the Ubuntu network settings to DHCP so it gets the IP, DNS, etc from the modem. Otherwise...dead modem?

---

### Post by kingfoot on 2007-06-13
i have the same problem, (i revived an old thread i started a while ago, should see it on front page where this one is.) i tried what everyone has said here, and it wont work. only difference is mine is a dsl modem not cable.

---

### Post by Mazehero55 on 2007-06-13
Well it's not a dead modem i'm using it right now on a windows laptop.  Also pppoeconf fails to find annything which is wierd.

Gosh I hope someone figures out what's wrong with our modems....

---

### Post by scotthershall on 2007-06-13
I had something similar happen once, although it wasn't while using Ubuntu.  I plugged the modem into my laptop directly, then tried to plug it into a router.  The laptop worked fine, but the router wouldn't connect.  What a friend told me to do was leave the modem unplugged (can't remember if it was from just the computer or from the coaxial too... you may want to just disconnect everything) for at least 15 minutes.  It's something about the way the cable service works... it only wants to communicate with whatever it communicated with last, if that makes sense.  It didn't make sense to me, but it worked.



Scott

---

### Post by information_entropy on 2007-06-13
**scotthershall** said
> t's something about the way the cable service works... it only wants to communicate with whatever it communicated with last, if that makes sense. It didn't make sense to me, but it worked.


This is because some cable companies are tracking the MAC addresses of the computer connected to the internet.  In my neck of the woods there are three different cable systems.  On one of them if you change the MAC address (for example a different computer or a new network card in the same computer) you have to actually call the cable company to get them to reset the MAC address to allow the new computer to connect.  On the other two you have to wait a while  like **scotthershall **described.

This is why you see cable modems with MAC address spoofing for sale at all of the local computer stores.

This is also why I use DSL even though it costs a few dollars more.

---

### Post by fdrake on 2007-06-13
what's the output of your ifconfig command? can you also connect through your browser to your modem Registration Status page?? did you try to reset you modem with the Ethernet cable plugged in the computer?it will take ~ 30 sec 
for example i have an arris cable modem with comcast and my Registration Status page is on this url: [http://192.168.100.1/](http://192.168.100.1/)  .

---

### Post by nymphaeles on 2007-06-13
Let me try to understand the situation...
So you use a CAT5 cable, plug one end to the cable modem, and the other end directly to the LAN port in the back of your PC?

Some cable modem would support auto-sensing, but typically you need a cross-over cable for this type of connection.  Check your cable modem manual to see if it support auto-sensing or if it requires a cross-over cable.  If you don't have the manual, try to locate the model number of the cable modem, and search for its manual online.

If the modem requires a cross-over cable, use a router or a switch in between your modem and PC.  That should fix the issue.

Note:  Your cable company has your cable modem MAC address recorded as an authorized device, not your PC.

---

### Post by jimrz on 2007-06-13
i agree, get yourself a router. most current (and a lot of not so current) models will automatically detect and hookup with your cable modem + will handle DHCP / NAT / address reservation, etc for you and are quite easy to setup. you can get a 4 port + wlan wired model really cheap anymore and, if you want/need wireless the 802.11g ones a reasonably affordable, as well. i have had very good results using both wired and wireless routers from Netgear.

---

### Post by Mazehero55 on 2007-06-14
Okay I tried it with a Linksys router. It says that I'm connected to a wired connection but still no internet.

Also theres a neat thread [here ]("http://http://www.geekzone.co.nz/forums.asp?ForumId=46&TopicId=13359") that might help

---

### Post by Chayak on 2007-06-14
*  208.67.222.222
    * 208.67.220.220
Put those two IP addresses into your DNS settings.  They are for OpenDNS and should give you DNS info if your DHCP doesn't give it to you.

---

### Post by deadlikeoscar on 2007-06-14
What happens when you open a terminal and type: **sudo dhclient eth0** ?

Also if you ever need to restart networking for any reason (this is second nature to me because I had to do this every class for Network Security) typing **sudo /etc/init.d/networking restart** is a good thing to know. Sometimes stupid things like these will get the ball moving. Are you using Ubuntu 7.04 or an earlier version? As a side note, I've never had any problems with my Time Warner service except for when my cable modem got fried during a storm.

---

### Post by Mazehero55 on 2007-06-14
I typed sudo dhclient and I got:

> Listening on LPF/eth0/00:00:00:00:00:00
Sending on LPF/eth0/00:00:00:00:00:00
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

I think it might be bad

---

### Post by louieb on 2007-06-14
I've got several computers running Linux and usually the only thing I've had to do is plug in the Ethernet cable and it works.         

The only time I've had trouble connecting with a wired Ethernet connection was just after my cat  urinated on my laptop's keyboard. After that I could connect to the net wireless,  but when I I tried pugging into a wire the computer could not get an a valid IP address. Fixed it by getting a PCMCIA Ethernet card. I guess the inboard card got fried. 

I'm not saying my cat peed on your computer also but you might try another NIC and see if that fixes your connection problem.

---

### Post by Fuzzygnome on 2007-06-14
It might be too simple, but my cable modem has a button on it to turn the internet on and off.

---

### Post by sandeep108 on 2007-06-14
> **information_entropy said:**
> **scotthershall** said


This is because some cable companies are tracking the MAC addresses of the computer connected to the internet.  In my neck of the woods there are three different cable systems.  On one of them if you change the MAC address (for example a different computer or a new network card in the same computer) you have to actually call the cable company to get them to reset the MAC address to allow the new computer to connect.  On the other two you have to wait a while  like **scotthershall **described.

This is why you see cable modems with MAC address spoofing for sale at all of the local computer stores.

This is also why I use DSL even though it costs a few dollars more.
QFT. Also usually they reset them every 24 hours. I went bonkers when I set up my new PC in windows and it simply would not connect and the old one would. Then next day the new one did and old one did not. I finally called their help line and they reset the ip. 

I am now using DSL and had no issues with ubuntu connecting.

---

### Post by deadlikeoscar on 2007-06-14
Well, to try to get some more information...when you go to System-->Administration-->Network:

-Is there a check mark in the box to the left of Wired Connection? I doubt this is the problem.

-Under the DNS tab what do you have listed for DNS Servers and Search Domains? 
(Mine says 65.24.7.3 and 65.24.7.6 with neo.rr.com under Search Domains. Since you don't live in Ohio you will have to find Road Runner's DNS Servers for yourself but Search Domain should be whatever the tail end of  your email from Road Runner is supposed to be)

-Under Modem Connection's properties, is this enabled? It shouldn't be.

You said that you used to connect with a stardard modem before. I wonder if there is something left over from that preventing you from connecting.

---

### Post by nymphaeles on 2007-06-14
When you plug in a Linksys router, I assume that the WAN port is connected to you modem, and your PC connects to one of those switch ports, as in this diagram:

Coaxial Cable ---- Cable Modem ---- WAN--LinksysRouter--Port# ---- PC

Your Linksys router would get an IP from your ISP.  Your PC would get an IP from your Linksys router from its built-in DHCP server.  If the router works OK, your PC will get an IP from it even if it doesn't connect to the modem.
I suggest that you
1)  reset the router to the default manufacture settings,
2)  plug your PC in one of the router switch ports,
3)  turn on or restart the PC,
4)  do an ifconfig and see if you have a valid private IP in the range 192.168.0. x,
5)  if you don't have an IP, try to use a known good PC and repeat the steps 1-4,
6)  if the good PC still don't get an IP, the router broke,
7)  if the good PC gets an IP, your PC network card is having a hardware or a driver issue,
8)  if the router is good, further testing is recommended by signing in to its web-base administration, check to see if it obtains an IP from your ISP,
9)  call your ISP if your router doesn't get an IP,
10) post your tests here for more assistance

---

### Post by dannyboy79 on 2007-06-14
sounds to me like a classic DNS issue. I thought I read that the author said he could put in an IP and get to the website. open firefox and type in this:
[http://64.233.167.104/](http://64.233.167.104/)

if that works it's a DNS issue and do what's listed on page 2 of this thread, put the OpenDNS servers within your DNS tab.

---

### Post by Mazehero55 on 2007-06-14
here's the output from ifconfig. First though, I know that the cable modem and the router work fiine; I've tested it on other computers with windows and it works, I should probably pop in a livecd in one of them and see what happens.

eth0    Link encap:Ethernet HWaddr 00:00:00:00:00:00
           inet6 addr: fe80::200::ff::fe00::0/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:573905 errors:0 dropped:0 overruns:0 frame:0
           TX packets:7356 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX  bytes:35428322 (33.7 MiB) TX bytes:461378 (450.5 KiB)
           Interrupt:11 Base address:0xdc00


eth0:avah    Link encap:Ethernet Hwaddr 00:00:00:00:00:00
                     inet addr:169.254.0.1 Bcast:169.254.255.255 Mask:255.255.0.0
                     UP BROADCAST RUNNING MULTICASR MTU:1500 Metric:1
                     Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
           inet addr:127.0.0.1 Mask 255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:17444 errors:0 dropped:0 overruns:0 frame:0
           TX packets:17444 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:999572 (976.1 KiB) TX bytes:999572 (976.1 KiB)



Does anybody know what this means

I have put in openDNS ip and still nothing

---

### Post by godd4242 on 2007-06-14
eh woops didn't see the other pages, and said something that everyone else had already said

;_;

---

### Post by kingfoot on 2007-06-14
this is similar to what my ifconfig gives me.

---

### Post by nymphaeles on 2007-06-14
I don't even see your MAC address.  Your network card may be bad.

---

### Post by Mazehero55 on 2007-06-15
That's what I'm thinking... Well I think I get paid soon so... I might be able to get a new one.

Also I have trouble connecting to other computers. It says theres a connection but it doesn't show any other computers anywhere.

---

### Post by dannyboy79 on 2007-06-15
IP addresses in the 169.254.0.0/16 range are used as defaults by a dhcp client when it can't get a lease from a dhcp server. If you have hosts on your network that use an IP address in that range after they ask for DHCP, then they never got a response from a DHCP server.

Not to mention, you have 2 eth0 results
The second one has the weird 169.... address which I think may be confusing everything. I believe that avah.... kicks in when dhcp isn't working. 

My best bet is that your NIC is bad. You could always try to set a new MAC address and see if that works but I doubt it. [http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

---

### Post by Mazehero55 on 2007-06-15
okay when I change the mac address and I restart the network, it wont bring up the device.

When I plug in the cord into my computer it shows it connecting and then says it has connected to a wired network. And then when I bring up firefox I try an address and it just sits there loading for a while and then comes up with server not found.

This is pretty confusing...

---

### Post by scotthershall on 2007-06-17
Do you have a place to which you can drag your computer and test it.  A friend or family member's house with a router for instance?  If you could test it with a known-good connection then you could rule out your computer's hardware.  It still sounds like everything is working but you just can get to the internet.  It still sounds like the cable service/MAC address problem.

Scott

---

### Post by dannyboy79 on 2007-06-18
i would say that if you CAN ping the IP address or even enter this into Firefox and it goes there  (64.233.167.104) then it's a DNS issue, if you can't, then I would say you have a bad Ethernet Card.

---

### Post by gbutler288 on 2007-06-20
If you figure this out let me know.  I'm on Time Warner and I am having the same issue.  I reloaded Windows and it works fine.  I have 5 other pc's (Dell's mind you) all are within 2 years old and none of them will connect with 7.04 but work just fine in a windows environment.  I've been working on this for 4 weeks now.  Any help is great appreciated.

Thanks,

Gary

---

### Post by nymphaeles on 2007-06-20
An ISP has very little to do with your computer equipment, especially for what OS you use behind the gateway (which is your cable/router).  In fact, none of the routers available on the market has a Windows OS on it.  It's hard for me to comprehend your issue.
You may want to post your test results here for more info?

---

