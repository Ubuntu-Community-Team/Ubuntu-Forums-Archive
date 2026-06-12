---
title: "Internet connection works &quot;halfway&quot;"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Seseli on 2007-01-16
Hi, 

I recently installed Ubuntu 6.10 on my parents' computer, everything worked fine except for the internet connection. They connect via an ADSL modem which is works as a router using PPPoE (hope I got that right). There's nothing wrong with the modem, since when you plug in a Windows or Mac computer it works without doing anything except sticking the wire in. 

I set Ubuntu to use DHCP. And it sort of works halfway: I can ping a server out there and it replies fast. On the other hand, Firefox is glacially slow; mostly it doesn't find a site at all, and sometimes it finds it after a long time. I thought the problem might be the DNS servers, so I asked the ISP for them and entered them in under Networking, but it's still not working. 

I think there's some sort of configuration file for DHCP, does that need to be edited in some way? Or is there something else I'm doing wrong?

---

### Post by xyz on 2007-01-16
Try this for a start - Originally posted by **richbarna**
Open a terminal and:
```
gksudo gedit /etc/modprobe.d/aliases
```
> # These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
alias net-pf-10 ipv6 off --
alias net-pf-10 off **-- add these three lines here.**
alias ipv6 off --
#alias net-pf-10 ipv6 **=========comment (put #) the original line**
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet

You can see it here as well:
[by Slowjet]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=speed+firefox")

Also:
[SWIFTFOx is faster]("http://www.ubuntuforums.org/showthread.php?t=142798")

---

### Post by Seseli on 2007-01-17
Hmm, I tried writing the following in a terminal, which one of your links recommended:

host [www.google.com](www.google.com)

and then it said that the connection timed out. So, according to the link, it would appear that I have some more general problem and IPV6 is not to blame?

---

