---
title: "internet connection probs"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by dantastik on 2006-07-15
my first post ever so i hope i wont break any important rules. if i do please accept my apologies in advance.

my prob:

i can ping and log on to my router - ethernet or wireless - but thats pretty much it.

i did try leaving the i.p. assigned by the dhcp, so that it came with the gateway and all.

i chose an i.p. address myself, making sure it wouldnt clash with other at home. gateway was set as 192.168.1.1, which is the router address. as dns i chose that that my router is using. no luck so i tried same address as the router. no luck.

i am positive that the router' s connection ok cause one of the few things my flatmate does in his life is checking his emails on his comp.

whats left to try?

also, anybody living in london uk? seeing a person in the flesh would be greatly appreciated. got the impression that l.u.g.'s tend to avoid communicating with the external world, or at least with me! if anybody can give a hand and able to produce a receipt for that, my employer's willing to refund whatever it costs... within certain limits :)

cheers, dan

dan.arbo(a)gmail.com

---

### Post by bigken on 2006-07-15
take look at this reply 3 
[http://www.ubuntuforums.org/showthread.php?t=215461](http://www.ubuntuforums.org/showthread.php?t=215461)
hope this helps ;)

---

### Post by HereInOz on 2006-07-15
You can first try pinging an outside IP address if you haven't already done it.  Try pinging 203.87.88.1 and see what you get.  That is provided you have not configured your firewall to block outgoing pings or incoming replies.

If you get a response from that, then you have internet connectivity, but you have a DNS problem.  If you do not get a response from that ping, you have a little more difficulty.

Is this a Netcomm router/modem?  If so, they are very dodgey as far as assigning IP addresses by DHCP with some linux installations.

I would certainly try setting the IP address of the Ubuntu machine to 192.168.1.3, and then setting your gateway as 192.168.1.1 and the DNS servers set as appropriate from your ISP, and see how you go.

Cheers,

Alan

---

### Post by philippe_carlo on 2006-07-15
Make sure your DNS servers are listed in /etc/resolv.conf
```
nameserver <ip-address>
```

Make sure that your gateway is set to the router's IP:
```
route
```
should give (among others)
```

default   <router ip>     0.0.0.0       UG    0      0        0 eth0

```
If no such line exists, try adding it with
```

sudo route add default gw <router ip> eth0

```

---

### Post by HereInOz on 2006-07-15
Sorry, I re-read your post and it looks like you have already tried a static IP and static DNS addresses.  My apologies.  

Alan

---

### Post by dantastik on 2006-07-15
sorted!

thank you very much to you all :)

---

### Post by bigken on 2006-07-16
what did you do to get it working ?

---

### Post by drtvasudevan on 2006-07-16
> **bigken said:**
> what did you do to get it working ?

oh yeah!
that is important.
usually some other guy comes along searches for his problem...bingo here is one... and finds it is solved with no details.
a bit frustrating what?
:-?

---

### Post by dantastik on 2006-07-17
> **drtvasudevan said:**
> oh yeah!
that is important.
usually some other guy comes along searches for his problem...bingo here is one... and finds it is solved with no details.
a bit frustrating what?
:-?


Sooooooooorry, did warn i was a newby tho... promise i wont do it anymore...

i got myself a static i.p. address, set the router as gateway, primary dns 4.2.2.1 and secondary dns 4.2.2.1 i believe thats what did the trick.

before that i was using my provider's dns's which were no help

---

