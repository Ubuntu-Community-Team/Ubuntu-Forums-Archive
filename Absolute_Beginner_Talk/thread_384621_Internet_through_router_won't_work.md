---
title: "Internet through router won't work"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by dofkex on 2007-03-14
Hi everyone,

I've just installed ubuntu and i'm completely new to linux

the problem is that although the message in the taskbar says connected to the internet, the browser can't connect to any sites except my router administration page.
(i'm connected to ADSL through router D-Link DSL-G604T). Another thing i noticed is that in the router page it shows that i'm connected and my ip but doesn't show my host name.

any clues what is the problem here?

---

### Post by dofkex on 2007-03-14
please help me...

---

### Post by annda on 2007-03-14
can you ping any hosts?

in the terminal, type:

ping -c 4 [www.google.com](www.google.com)

if not, try one of google's IPs

ping -c 4 209.85.135.99

if pinging is fine and you are using firefox, it might be a problem that your router has with IPv6 (i've had this with a d-link router once). in that case, type about:config in the address bar, search for ipv6 and double-click to change it to "false". you may need to restart firefox after that.

---

### Post by astrolabio on 2007-03-14
You probably either need to set your gateway or your and/or dns.

---

### Post by cate on 2007-03-17
I'm having the same problem with the same router. Pinging is fine and IPv6 is set to false. My DNS is set up. I don't know what's wrong.

---

### Post by belvoir on 2008-03-09
Hi
 i have the same problem with my router.

I can connect through it no problems with xp and 98se but it has recently stopped working with kubuntu.

I've also tried ubuntu and puppy with no joy.

I'm no expert but i think it may be a dns problem, i can connect to my routers http server for configuration with no problems  but i can get nothing on the WAN.

My theory is that my isp has upgraded the dns servers to IPv6 and the router/ linux can not cope, microsoft must have found a way around it.

I'm stumped but their must be an answer, i use firefox on all os's except puppy.

Cheers
 Neil

---

