---
title: "Ubuntu 6.06 Dial up and Static LAN IP DNS"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by FRAMBO on 2006-09-16
Howdy,

I have been having some issues with getting my new install of Ubuntu to connect to the internet via my dialup connection when required.  

I have done plenty of searching here.  It seems most of the issues posted here discuss DCHP of the LAN.  

I have install automatrix (if that maters) and I can connect to my dialup ISP.  My LAN IP is manually configured with dns.  

I can connect to the internet with no problems with the LAN connection but as soon as I try to use the dial up connection (which connects and has DCHP ip) firefox and the email client is not connecting.  (I usually disable the LAN or unplug the rj45 cable before connecting)

What am I missing here?  I'm a newbie and this type of setup usually works with out thought in winxp when switching between dialup and LAN to connect to the internet.

---

### Post by towsonu2003 on 2006-09-16
couple of things that come to my mind: 
. use wvdial to dial up your isp (I find it much more helpful) -available from the repos using synaptic (package manager)
. before dialing out, make sure no other interface is active: 
```
ifconfig
``` should list only "lo" (if you are not using vmware). 

-> so before dialing out, if you see that you have, for example, eth0 listed under ```
ifconfig
```, take it down with ```
sudo ifconfig eth0 down
```

also, are you sure you can connect to your isp via dial up? it is usually very hard to set up the dial up modem if it's a winmodem. if you're talking about DSL dial up, the above post is obsolete though...

---

### Post by FRAMBO on 2006-09-16
Thanks for the response. I'm referring to Standard dial up (not DSL) 

I've been using Gnome PPP to connect.  I've also been able to connect via wvdial too.  I get IP etc but I do get these warning codes I'm not familiar with:

```

 Starting pppd at Sat Sep 16 16:28:07 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
```

This is what I get when run : ipconfig with Dial up connected  (I'm behind a router/firewall

```
eth0      Link encap:Ethernet  HWaddr 00:01:6C:30:71:77
          inet addr:192.168.16.10  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fe30:7177/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50048449 (47.7 MiB)  TX bytes:2108612 (2.0 MiB)
          Interrupt:193 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7232 (7.0 KiB)  TX bytes:7232 (7.0 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:209.52.XXX.XX  P-t-P:209.52.XXX.XXX  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:95 (95.0 b)  TX bytes:101 (101.0 b)

```


I'm going to run the next command but I'm going to post this first before taking my ethernet down :)

---

### Post by FRAMBO on 2006-09-16
OK that command is the same as what I have been doing through System-> Adminstration -> Networking


I'm back on the ethernet.  No dice on taking down eth0.  

This is the typical error message I receive in Firefox:

```
Server not found        
Firefox can't find the server at [www.google.ca](www.google.ca).

    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
```

---

### Post by spur on 2006-09-16
Could this be a firewall issue? Clue is 'permission denied'  error message.Its been a while since I configured a dial up on linux but I do recall a heap of firewall probs.

---

### Post by FRAMBO on 2006-09-16
I have installed firestarter firewall but turned it off.

---

### Post by FRAMBO on 2006-09-16
I'm on dialup now.  I removed the manual DNS servers I listed for eth0.  After awhile the dns listed the automatically assigned ones after a few mintues.  

It's a pain in the *** if I need to manualy add and remove the static DNS for eth0 each time I switch between eth0 and ppp0

 It this as good as it gets?

---

### Post by FRAMBO on 2006-09-16
Well I just realized firestarter actually got my connection switched over to dialup when I restarted it.  I had to do the same when I returned to eth0.

Now is there some way for this to swtich back and forth automatically?

---

### Post by towsonu2003 on 2006-09-16
> **FRAMBO said:**
> I'm on dialup now.  I removed the manual DNS servers I listed for eth0.  After awhile the dns listed the automatically assigned ones after a few mintues.  

It's a pain in the *** if I need to manualy add and remove the static DNS for eth0 each time I switch between eth0 and ppp0

 It this as good as it gets?
I don't use your setup (read: I don't know anything about static ip usage), and I'm relatively new so, maybe? I'm sure there is a work-around. 

In the meantime (while you're looking for a workaround), you could write a script that: 
1. takes down eth0
2. interchanges a blank DNS server list with the hand-written one
3. dial wvdial

it is possible (but please wait for someone else's confirmation!) that the script could look like below after initial setup. iniial setup being:
```
sudo cp /etc/resolv.conf /etc/manual.resolv
sudo touch /etc/dialup.resolve
```
manual.resolv has your LAN DNS servers.
and the script (switching from LAN to dialup) possibly would look like: 
```

#!/bin/bash
ifconfig eth0 down
sleep 2
cp /etc/dialup.resolve /etc/resolv.conf
sleep 2
wvdial

```
save this as dialup under /home/username and do ```
chmod +x /home/username/dialup
```to make it executable
and the next time you wanna dial, do ```
sudo ./dialup
```

but again _please_ _wait_ for someone to confirm this. 

also to switch from dial up to LAN, you could do something like:
```

#!/bin/bash
cp /etc/manual.resolv /etc/resolv.conf
sleep 2
ifconfig eth0 up

```
save this as lan under /home/username and make it executable (command above). when you want to switch from dialup tp LAN, first kill wvdial (ctrl + c) and then start this script with ```
sudo ./lan
```

for anyone who reads this: would this work?


as for firestarter, I think no... I do the same myself everytime I switch interfaces.

---

### Post by FRAMBO on 2006-09-16
> **towsonu2003 said:**
> it is possible (but please wait for someone else's confirmation!) that the script could look like below after initial setup. iniial setup being:



for anyone who reads this: would this work?


as for firestarter, I think no... I do the same myself everytime I switch interfaces.

Great thanks.  I will wait offical confirmation :biggrin:

---

