---
title: "linksys 354g"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-31
in need of some help with getting out onto the web,i have got this linksys / modem/router/ adsl/
wag354g/2.4ghz/wierless-g homegateway.now i uesd to have usb voyager but now i still use the voyager 
with btbroadband to get to this forum and tell you whats going on, the first thing i did was to set it all up 
which went ok, then connect to the gateway to configure the adsl gateway and selected,rfc2156, pppoe
because i pays one monthly amout to btbroadband,now this is what i get,

ip address 192.168.238.238
subnetmask 255.255.255.0

every time i click onto the tv thing in the phone line connection apart in windows, i mean erthnet thing
called lacal eara connection click on that and two tv screens come up and all the light on the modem come on and it makes you think its out on the web, but every time i click onto somthing nothing happens, 
and i have tried to make new connection but nothing goes right, any help thank you richard

---

### Post by richard willacy on 2005-12-31
just been into ubuntu breezy and went into a terminal and typed somthing and this is what comes up,

port8080
ip address 127.0.0.1
netmask 255.0.0.0
protocol ipv4
ip address 86.129.38.161
now im compleatly confuesd about all this :confused:

---

### Post by thekiller on 2005-12-31
[QUOTE=richard willacy]just been into ubuntu breezy and went into a terminal and typed somthing and this is what comes up,

port8080
ip address 127.0.0.1
netmask 255.0.0.0
protocol ipv4
ip address 86.129.38.161
now im compleatly confuesd about all this :confused:[/QUOTE]

On ubuntu, please open a terminal and post the output of[COLOR="Red"] ifconfig[/COLOR]

---

### Post by richard willacy on 2005-12-31
this what it says,gtho/link encap:erthnet hwaddr/00:20:ed:bf:70:fo:
internet address 86.129.38.161
bcast 86.129.38.255/mask 255.255.255.0
internet 6 address fe80/220/edff/fsbs/7dfk/64/scooplink
upboard cast running multicast.mtu:1500

io
    linkencap local loopback
internet address 127.0.0.1
mask 255.0.0.0
internet 16 address /1/128 scope host
loopback running mtu 16436 metric 1

and when i type pppoeconf, and this thing comes up and starts to look for my modem but it found nothing

---

