---
title: "download speeds"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-30
ok I hava a 29mb per sec internet connection
I know prove it 
I have many times at PRO Networks
Im not sure how in ubuntu Ive only been using linux for 1 day

My speed is acurate and works in Vista

However current download is 376k/s
Im downloading upgrades

why so slow and can I tweak it

---

### Post by jualin on 2007-12-30
maybe you can try disabling IPV6, sometimes when you have IPV6 enable the internet speed is slow. In Vista IPV6 is disabled by default but in Ubuntu is enabled by default. Search in the forum for disabling IPV6 and try it. Hope it helps

---

### Post by Dr Small on 2007-12-30
Try going to speedtest and checking your speeds, and then do as jualin suggested:
[http://speedtest.net/](http://speedtest.net/)

---

### Post by spiderbatdad on 2007-12-30
you've  probably seen this tweak:[http://ubuntuforums.org/showthread.php?t=202838&highlight=ipv6+tweak](http://ubuntuforums.org/showthread.php?t=202838&highlight=ipv6+tweak)

IDK if it will help you at all.[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

---

### Post by frenchsquared on 2007-12-30
speed test wont work from linux yet no flash
and as I said I have posted speed test results many times
**It is 29mbps**

i tried the ipv6+tweak link but when it typed in 
gksudo gedit /etc/modprobe.d/aliases
i got nothing like what it said
mostly a bunch of errors
fail to load icon a memory map, type, numeris time and lots of other stuff

---

### Post by frenchsquared on 2007-12-30
strange

I just finished upgrade to 6.10 and started 7.4
download speed is know ranging from 1400kbps to 400kbps

---

### Post by reacocard on 2007-12-30
> **frenchsquared said:**
> ok I hava a 29mb per sec internet connection
I know prove it 
I have many times at PRO Networks
Im not sure how in ubuntu Ive only been using linux for 1 day

My speed is acurate and works in Vista

However current download is 376k/s
Im downloading upgrades

why so slow and can I tweak it

that's normal. the problem isn't your connection, its that the update mirror simply doesn't have enough bandwidth to give you any more than what you're getting. you can try using a different mirror, but if you're already getting over 300KB/s there probably won't be much improvement. this is a common issue with such fast connections as yours: the server, rather than the connection, is often the limiting point.

you could try running a download speed test in ubuntu, if that number is significantly different from what you got under vista, there my be an issue, btu if not, the problem is almost certainly what I outlined above.  I have experienced this phenomenon myself: my college has a 1000mbps connection. On bittorrent downloads I've seen speeds above 8MB/s, but the ubuntu servers max out at around 350KB/s even after choosing the best mirror I could find. (mirrors.kernel.org)

---

### Post by reacocard on 2007-12-30
> **frenchsquared said:**
> strange

I just finished upgrade to 6.10 and started 7.4
download speed is know ranging from 1400kbps to 400kbps

wow really? what mirror are you using? (you can find out in system->administration->software sources)

---

### Post by frenchsquared on 2007-12-30
??

I guess you are asking about download from
Server for United states

It didnt stay at 1400 for long
was mostly between 3-600 kb/s

Upgrading seemed to fix it.
I understand the change and you are correct It changes in Vista and XP

below 300 just seemed really slow

Thanks

---

### Post by frenchsquared on 2007-12-30
1000mbps?
I thought the record was just over 100mb/s

---

### Post by reacocard on 2007-12-30
> **frenchsquared said:**
> 1000mbps?
I thought the record was just over 100mb/s

it's a college line, idk what they put into it but given that it serves thousands of people and still manages to be as fast as it is for individuals I don't doubt that that figure they gave is correct. teh US server was never that fast for me. oh well, i'm happy enough with 300KB/s given that my home connection can't even reach 40KB/s. :(

---

