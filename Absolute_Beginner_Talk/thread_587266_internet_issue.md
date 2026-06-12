---
title: "internet issue"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by lalek on 2007-10-22
well after installing ubuntu 7.10 i made the pppoeconf and my ADSL connection was flying. but then just after opening few pages with firefox it just stopped. In the first 30 mins i thought that the connection keeps dropping and i was doing the "sudu pon dsl-provider" thing over and over but again firefox opens pages just briefly and then again stops. but after installing Skype i noticed that disconnection is probably not the case, since skype is running  without any problems while at the same time firefox can't open pages,Synaptic PM cannot upgrade software..any help on this?

i forgot to mention: sometimes i need to do poff dsl-provider in order with the next pon dsl-provider to get connection the connection active.

---

### Post by HermanAB on 2007-10-22
Some debugging required: tcpdump, dig, telnet, traceroute, ping...

---

### Post by lalek on 2007-10-23
sorry mate,can you be more specific?

---

### Post by realvz on 2007-10-23
try using opendns

[B]OpenDNS | Providing A Safer And Faster Internet 
OpenDNS is a better DNS service. We make your Internet safer, faster, smarter and more reliable. It's free, and there's nothing to download.
[www.opendns.com/](www.opendns.com/) [/B]

---

### Post by lalek on 2007-10-24
ok i found some manual on my ISP webpage for older versions of windows.

it says in Internet Protocol (TCP/IP) Properties check Obtain an IP address automaticly,
then choose Use the following DNS server addresses and in preferred DNS server enter 62.162.32.5 and in Alternate DNS server enter 62.162.32.6. 

so can anyone please tell me where shoud i enter these DNS addresses?

And here is a copy of my dsl-provider file. I have no idea if it will help but anyway.

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
user "xxxxxxx@mt.net.mk"
usepeerdns

---

### Post by lalek on 2007-10-24
anybody?? please?? i'm kinda desperate here!!

---

### Post by dstath on 2008-01-08
I have a similar problem. Internet works for a while and then stops. I am 
using a USB modem. My interface is ppp0 (not eth0).

see [here ]("http://ubuntuforums.org/showpost.php?p=4093248&postcount=32")for a complete description.

---

### Post by lalek on 2008-01-09
openDNS guide solved the issue! hope it will help you too. just go to the OpenDNS website and follow the instructions. you dont even have to register!gl

---

### Post by dstath on 2008-01-09
openDNS did not solve my problem. I already tried.

---

