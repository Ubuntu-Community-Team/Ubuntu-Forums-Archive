---
title: "NEW INSTALL  can't connect to the internet"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by 7Aaron7 on 2007-05-13
:mad: 
OK, I would really like to get into ubuntu, but at this rate........
Simply put, I can't connec to the net.  Firefox tells me server can't be found.

My config:
AMD 1.4 ghz

ethernet card connected with a cable to a B-focus 270 pr router (this is my ADSL modem)

After hunting around the forums tried several things:

I am using dhcp. Doesn't work
I also tried statically addressing the tcpip addresses according to my ISP, that ddin't work

under script line "aaron@local:~$"   ping ubuntuforums.org     yields      unknown host 
                                       "                 ping  192.68.80.0              yields      from 169.254.8.148  destination      host unreachable.

I changed the firefox network.dns.kisableIPv6 to true   didn't help.


If anybody wants, I'll manually type in the ifconfig output, but I'd rather you ask me for specifics, rather than me having to type in the 30+ lines of info.  

Much more than grateful to anyone who can help out.  I'm really trying to get away from the OTHER OS, but this is hard!!


Aaron

---

### Post by beorn! on 2007-05-13
please post your distro (6.06, 6.10, or 7.04?) Also go into Start> System> Administration> Network, and let me know what connections show up. This is the part that will be a little different depending on your distro.... but the idea is to see that your network device has been initialized... sometime it can be as easy as just activating the device, or putting it in roaming mode, and if not, reply back.

PS- don't give up on Ubuntu. We're all here for you.

---

### Post by 7Aaron7 on 2007-05-13
thanks!!

feisty fawn 7.04

In order of display:

wired connection (eth1)  it's checked, and the adress is dhcp
wired connection (eth0)  it's checked, and the adress is dhcp
Modem connection   It's not checked. "This network interface is not configured"

BTW, I don't have roaming mode enabled since I don't know what it is.

thanks again, and, BTW, what in the world is that dog lcking in your avatar?

---

