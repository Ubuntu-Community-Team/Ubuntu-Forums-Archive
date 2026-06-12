---
title: "Adsl Pain!!"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-21
Hello

After many hours of messing around with ndiswrapper and the like, it occured to me to plug the ADSL router directly into the back of my computer using an ethernet cable (since the computer is only 2ft away from the router!) and dump the wireless bit for now.  

Anyway, after more playing about I can now view the stuff on my ADSL router (set-up stuff and WEP stuff) and I can see my tiscali account details are already in place.  In fact, I'm using it right now to construct this letter through XP.  My problem is... what do I need to do in Ubuntu to get onto the internet?  All those DNS, IP thingys and other abreviations are very much confusing? :confused:

Thank you, in advance, for all your advice.

---

### Post by TrendyDark on 2006-03-21
I'm not very familiar with ADSL connections, but I'm quite sure that you're given a set of IPs and a DNS Gateway to use. Thus, if you open up System> Administration> Networking and enter your IP Address, Subnet Mask, and Gateway address, you should be connected. You can find this information in Windows, just look at your connection properties.

---

### Post by gnu2tux on 2006-03-21
hi

you don't need to know any of those details as long as your router is set up for automatic configuration (DHCP).

Set your network card on your PC (in the Ubuntu networking options) to DHCP and the DNS, Route/gateway and IP information will be set on your PC by the router instead. It is likely this is already the case if you can connect to your router though. What happens when you try and ping an IP address, for example, the IP for google.com is 64.233.167.99. Go to your terminal and type:

ping 64.233.167.99

paste back what you see, ctrl +C stops the output.

if you don't get a ping, then there may be a problem somewhere with the DHCP settings. If you get a ping, then there is likely only a problem with the name server (DNS) settings, which translate names like google.com into IP addresses (eg 64.233.167.99).

Regards,

Ali.

---

### Post by Norfolk 'n' Good on 2006-03-21
Hello Ali

Thank you for your help with this issue and may I apologies for the delay... I'm having to switch between operating systems.  I did as you suggested and here is a copied extract from the ping test...

64 bytes from 64.233.167.99: icmp_seq=18 ttl=239 time=120 ms
64 bytes from 64.233.167.99: icmp_seq=19 ttl=239 time=120 ms
64 bytes from 64.233.167.99: icmp_seq=20 ttl=239 time=121 ms
64 bytes from 64.233.167.99: icmp_seq=21 ttl=239 time=119 ms
64 bytes from 64.233.167.99: icmp_seq=22 ttl=239 time=119 ms
64 bytes from 64.233.167.99: icmp_seq=23 ttl=239 time=120 ms

--- 64.233.167.99 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22020ms
rtt min/avg/max/mdev = 118.780/120.700/131.647/2.491 ms

I'm no expert, does this suggests that there is communication to the outside world?

---

### Post by Titus A Duxass on 2006-03-21
Yes, you are connected if you pinged the google IP.
Normally I type ping [www.google.com](www.google.com) to get confirmation.

You should be online now.

---

### Post by Norfolk 'n' Good on 2006-03-21
Thank you for being patient with me guys.  

I went back into the terminal and pinged [www.google.com](www.google.com) and got the following result…

64 bytes from 64.233.167.99: icmp_seq=18 ttl=239 time=120 ms
64 bytes from 64.233.167.99: icmp_seq=19 ttl=239 time=120 ms
64 bytes from 64.233.167.99: icmp_seq=20 ttl=239 time=121 ms
64 bytes from 64.233.167.99: icmp_seq=21 ttl=239 time=119 ms
64 bytes from 64.233.167.99: icmp_seq=22 ttl=239 time=119 ms
64 bytes from 64.233.167.99: icmp_seq=23 ttl=239 time=120 ms

--- 64.233.167.99 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22020ms
rtt min/avg/max/mdev = 118.780/120.700/131.647/2.491 ms

However, when I tried pinging eBay ([www.ebay.com](www.ebay.com)) and got X packets transmitted, 0 packets received?  This was also the case for other www. sites I know of.

I then opened my Mozilla browser and typed in [www.google.com](www.google.com).  It just hangs there without ever connecting.  I have also tried several other addresses, but it doesn’t appear to want to connect.  If I type in ‘192.168.1.1’ I can see the stuff on my router.  I know it works because I’m back here on the forums.  Logic dictates there is a problem between my browser and the router.  I’m nearly there, I can see the light, but I just can’t get over the last hurdle  :confused:

---

