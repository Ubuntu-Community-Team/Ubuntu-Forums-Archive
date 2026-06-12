---
title: "trying to get ubuntu configured to work on the web"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by BBlight on 2007-06-20
hello all,

(please see my earlier post right at the bottom)

no the command.......sudo dhclient....... seams to have had no effect on helping me get web connected...

here is the ouput the command made:

------------------------------------------------------------------
Internet Systems COnsortium DHCP client V3/04
Copyright 2004-2006 internet systems consortium
all rights reserved

For info please visit  [http://www.isc.org/sw/dchp](http://www.isc.org/sw/dchp)

Listening on LPF/eth0/00:40:f489:2e:F3
sending on LOF/eth0/00:40:f4:89:2e:f3
sending on Socket/Fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2--renewal in 20075 seconds

-----------------------------------------------------------------------------


what should my network settings actually be set to?

for example DNS?
and account etc

there are about 4 tabs on the network window....what should the settings be in these tabs...

also this ROUTER is not recognised via USB either.....(just thought it was worth a try)

can you help?

Ian

----------------------------------------------------

eirleir post:

Hello,

i installed ubuntu the other day and it does not connect to the internet through my ethernet socket and router..

i have searched this forum and read the advice

i see the main information here...

ifconfig -a
-------------------------------------------------------------------------------------------------

eth0 Link encap: Ethernet HWaddr 00:40:F4:89:2e:F3
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask 255.255.255.0
inet6 addr :Fe80::240:f4ff:fe89:2ef 3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:41 errors 0 dropped 0 overurns:0 carrier 0
collisions:0 txqueuelen:1000
RX bytes:1044 (1.0KiB) TX bytes :6644
interrupt:11 Base address:0x4000 (6.4KiB)

lo Link encap: Local Loopback
inet addr : 127.0.0.1 Mask 255.0.0.0
inet6 addr ::1/128 scope:Host
UP LOOPBACK RUNNING MTO :16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame=0
TX packets:0 errors:0 dropped:0 overruns:0 carrier=0
collisions:0 txqueelen:0 carrier:0
RX byets:0 (0.0b) TX byets (0.0b)

-------------------------------------------------------------------------------------

as far as i know my ips is very standard...PLUSNET.....i think it uses DCHP....

i have a hunch the ubuntu network needs configuring and the router...

my ISP has emailed all the setting values they say any ethernet ROUTER needs...but hey have not included the DNS in this list...

my router has a book with it....and i first tried getting it working under winXP but had ZERO luck on both ethernet or USB.....even after doing the configuring and saving it to flash etc.....the web just would not work....(it installed all the correct USB drivers in winXP..... and still did not work)

this is disconcerting...the fact that the router did not work in winXP with USB drivers installed.......... and the configuration done exactly by the book...

i can post all the settings required for my router....in this forum....

as for ubuntu...i have never touched any settings to do with the internet....apart from the command listed above...

can you help

thanks

Ian

---

### Post by phr0ze on 2007-06-20
Does your router get DNS settings? You can usually find this under WAN settings or Status on the router. If DNS is there I have heard some people need to disable the IPv6 to get internet to work. I don't know how to do this, but I've seen it around.

---

### Post by BBlight on 2007-06-20
Hello there

well i can't look at the ROUTER configuring under linux.....only in windows can i look at what the flash inside the router contains...and change it's settings...

i believe it DOES get DNS settings...

but does this mean i must stick the router back onto winXP and try to configure it again?

the WAN settings and stuff....these are not linux things you are referring to ....are they...

V

---

### Post by DSn0wMan on 2007-06-20
If you can get to the internet on your windows box, then your router probably is not the problem.

---

### Post by BBlight on 2007-06-20
Well, that is jus the problem

i can't the router to work on the windows box neither....

i wil try it again...doing that iv6 DNS thing...and see if the windows box works...

my isp never gave me the DNS address...or details

i emailed them twice...and they only ever sent me 4 settings that apply to ANY router across the board.......and this is a large ISP aswell....dealing with many router enquiries per day)

DNS was not included

anyhow

V

---

### Post by lazyart on 2007-06-20
you shouldn't need to fill out settings for the router-- it should pull them directly from the modem.

It looks like you are getting an ip address-- it's 192.168.1.2.  If you punch 192.168.1.1 into firefox it should give you the router config page.

I think you'll find the router is unhappy communicating to the modem.  Power cycling both the modem and the router may resolve it.

---

